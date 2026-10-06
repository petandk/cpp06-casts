*This project has been created as part of the 42 curriculum by rmanzana*

# C++ Module 06 — C++ casts

## Description

Seventh module of the 42 C++ piscine. It is about the four **C++ cast operators** and when to use each one, instead of the C-style `(type)value` cast that hides what kind of conversion is happening.

| Cast | Use |
|---|---|
| `static_cast` | Well-defined conversions checked at compile time (e.g. `double` → `int`) |
| `dynamic_cast` | Safe downcasting in a polymorphic hierarchy, checked at runtime |
| `reinterpret_cast` | Reinterpreting the bits of a value as another type (e.g. pointer → integer) |
| `const_cast` | Adding or removing `const` |

All the code follows the **C++98** standard and compiles with `c++ -Wall -Wextra -Werror -std=c++98`.

## Exercises

| Exercise | Program | Description |
|---|---|---|
| `ex00` — Conversion of scalar types | `convert` | A non-instantiable `ScalarConverter` class with a static `convert()` method. It detects whether the input is a `char`, `int`, `float` or `double` literal (including the pseudo-literals `nan`, `+inf`, `-inf`, `nanf`, `+inff`, `-inff`), converts it to its real type, and then **explicitly casts** it to the other three types with `static_cast`, printing `impossible` or `Non displayable` when a conversion makes no sense. |
| `ex01` — Serialization | `serialize` | A `Serialize` class with two static methods that turn a pointer into a `uintptr_t` and back with `reinterpret_cast`. The deserialized pointer must compare equal to the original one. |
| `ex02` — Identify real type | `identify` | A `Base` class and three empty derived classes `A`, `B` and `C`. `generate()` returns a random one, and `identify()` finds its real type in two ways: from a **pointer** (`dynamic_cast` returns `NULL` on failure) and from a **reference** (`dynamic_cast` throws `std::bad_cast` on failure, since a reference cannot be null). |

## Key concepts

- **Type detection and conversion** of literals, and the limits of each type (overflow, precision, non-printable characters).
- **`static_cast`** for explicit, safe conversions between numeric types.
- **`reinterpret_cast`** and `uintptr_t` for low-level pointer manipulation.
- **`dynamic_cast`** and RTTI (Run-Time Type Information), which needs at least one virtual function in the base class.
- **Static classes:** a class whose constructors are private so it cannot be instantiated.

## Instructions

Each exercise has its own `Makefile`:

```bash
cd ex00
make
./convert 42
./convert 4.2f
./convert nan
./convert a
```

`make clean`, `make fclean` and `make re` are available in every exercise.

## Resources

- [cplusplus.com — Type casting](https://cplusplus.com/doc/tutorial/typecasting/)
- [cppreference — `static_cast`](https://en.cppreference.com/w/cpp/language/static_cast), [`dynamic_cast`](https://en.cppreference.com/w/cpp/language/dynamic_cast), [`reinterpret_cast`](https://en.cppreference.com/w/cpp/language/reinterpret_cast)
- [IEEE 754 — special values (NaN, infinity)](https://en.wikipedia.org/wiki/IEEE_754#Special_values)
- [Serialization — Wikipedia](https://en.wikipedia.org/wiki/Serialization)
