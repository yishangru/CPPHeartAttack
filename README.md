# Useful Note When Programming In CPP

## Copy Constructor Issue

### std::move


### Unique Pointer with Container (Vector, Map ...)
`unique pointer` can only be copied by `std::move()`. When wrap class in `unique pointer` and container, the copy of container will try to call `const class&`. However, `Unique Pointer` only support `const class&&`. Thus, it is proper to delete all possible `const class&` copy constructor, including
1. `class(const class&) = delete;`
2. `class& operator=(const class&) = delete;`

And only leave the move copy constructor (`class(const class&&)`) to make it consistency with `unique pointer` usage. Ref: https://stackoverflow.com/questions/21943569/deleted-function-unique-ptr