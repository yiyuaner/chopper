KLEE/Slicing Project
=============================
An extension of KLEE (http://klee.github.io).

## Build
Build the Slicing Library:
* https://github.com/davidtr1037/se-slicing

Build KLEE:
```
mkdir klee_build
cd klee_build
cmake \
    -DCMAKE_C_FLAGS="-m32 -g" \
    -DCMAKE_CXX_FLAGS="-m32 -g" \
    -DENABLE_SOLVER_STP=ON \
    -DENABLE_POSIX_RUNTIME=ON \
    -DENABLE_KLEE_UCLIBC=ON \
    -DKLEE_UCLIBC_PATH=<KLEE_UCLIBC_DIR> \
    -DLLVM_CONFIG_BINARY=<LLVM_CONFIG_PATH> \
    -DENABLE_UNIT_TESTS=OFF \
    -DKLEE_RUNTIME_BUILD_TYPE=Release+Asserts \
    -DENABLE_SYSTEM_TESTS=ON \
    -DSLICING_ROOT_DIR=<SLICING_PROJECT_DIR> \
    <KLEE_ROOT_DIR>
```

## Usage Example
Let's look at the following program:
```

```

Compile the program:
```
clang -m32 main.c -o main.bc
opt -mem2reg main.bc -o main.bc (required for better pointer analysis)
```

Run KLEE:
```
klee -libc=klee -search=dfs -slice=<function_name> main.bc
```
