
# Create Shared Libraries

## Preprocessor Library

Preprocessor needs path to included header files so that it can replace its contents

```sh
gcc -E -IshlibFirst/include shlibFirst/src/mylib.cpp -v
```

```sh
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 6.3.0-18+deb9u1' --with-bugurl=file:///usr/share/doc/gcc-6/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-6 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --enable-default-pie --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-6-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-6-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-6-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --with-target-system-zlib --enable-objc-gc=auto --enable-multiarch --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 6.3.0 20170516 (Debian 6.3.0-18+deb9u1) 
COLLECT_GCC_OPTIONS='-E' '-I' 'shlibFirst/include' '-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/6/cc1plus -E -quiet -v -I shlibFirst/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE shlibFirst/src/mylib.cpp -mtune=generic -march=x86-64
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/6"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/6/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 shlibFirst/include
 /usr/include/c++/6
 /usr/include/x86_64-linux-gnu/c++/6
 /usr/include/c++/6/backward
 /usr/lib/gcc/x86_64-linux-gnu/6/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/6/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
# 1 "shlibFirst/src/mylib.cpp"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 1 "<command-line>" 2
# 1 "shlibFirst/src/mylib.cpp"

# 1 "shlibFirst/include/mylib.h" 1

int add(int x, int y);
# 3 "shlibFirst/src/mylib.cpp" 2

int add(int x, int y){
    return x+y;
}
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-E' '-I' 'shlibFirst/include' '-v' '-mtune=generic' '-march=x86-64'
```
If path is not given then preprocessing (and ultimate compilation) stops

```sh
gcc -E shlibFirst/src/mylib.cpp -v
```

```sh
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 6.3.0-18+deb9u1' --with-bugurl=file:///usr/share/doc/gcc-6/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-6 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --enable-default-pie --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-6-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-6-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-6-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --with-target-system-zlib --enable-objc-gc=auto --enable-multiarch --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 6.3.0 20170516 (Debian 6.3.0-18+deb9u1) 
COLLECT_GCC_OPTIONS='-E' '-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/6/cc1plus -E -quiet -v -imultiarch x86_64-linux-gnu -D_GNU_SOURCE shlibFirst/src/mylib.cpp -mtune=generic -march=x86-64
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/6"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/6/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/6
 /usr/include/x86_64-linux-gnu/c++/6
 /usr/include/c++/6/backward
 /usr/lib/gcc/x86_64-linux-gnu/6/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/6/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
# 1 "shlibFirst/src/mylib.cpp"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 1 "<command-line>" 2
# 1 "shlibFirst/src/mylib.cpp"
shlibFirst/src/mylib.cpp:2:19: fatal error: mylib.h: No such file or directory
 #include "mylib.h"
                   ^
compilation terminated.
```


## Compile Library as ObjectFile

Compiler called with `-fPIC` flag to prepare it with glp sections

```sh
g++ -fPIC -IshlibFirst/include  -c shlibFirst/src/mylib.cpp -o mylib.o -v
```

```sh
Using built-in specs.
COLLECT_GCC=g++
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 6.3.0-18+deb9u1' --with-bugurl=file:///usr/share/doc/gcc-6/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-6 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --enable-default-pie --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-6-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-6-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-6-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --with-target-system-zlib --enable-objc-gc=auto --enable-multiarch --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 6.3.0 20170516 (Debian 6.3.0-18+deb9u1) 
COLLECT_GCC_OPTIONS='-fPIC' '-I' 'shlibFirst/include' '-c' '-o' 'mylib.o' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/6/cc1plus -quiet -v -I shlibFirst/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE shlibFirst/src/mylib.cpp -quiet -dumpbase mylib.cpp -mtune=generic -march=x86-64 -auxbase-strip mylib.o -version -fPIC -o /tmp/ccRRGEFn.s
GNU C++14 (Debian 6.3.0-18+deb9u1) version 6.3.0 20170516 (x86_64-linux-gnu)
        compiled by GNU C version 6.3.0 20170516, GMP version 6.1.2, MPFR version 3.1.5, MPC version 1.0.3, isl version 0.15
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/6"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/6/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 shlibFirst/include
 /usr/include/c++/6
 /usr/include/x86_64-linux-gnu/c++/6
 /usr/include/c++/6/backward
 /usr/lib/gcc/x86_64-linux-gnu/6/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/6/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++14 (Debian 6.3.0-18+deb9u1) version 6.3.0 20170516 (x86_64-linux-gnu)
        compiled by GNU C version 6.3.0 20170516, GMP version 6.1.2, MPFR version 3.1.5, MPC version 1.0.3, isl version 0.15
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9d922bffefb5a33c8f2905f4ce829a36
COLLECT_GCC_OPTIONS='-fPIC' '-I' 'shlibFirst/include' '-c' '-o' 'mylib.o' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 as -v -I shlibFirst/include --64 -o mylib.o /tmp/ccRRGEFn.s
GNU assembler version 2.28 (x86_64-linux-gnu) using BFD version (GNU Binutils for Debian) 2.28
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-fPIC' '-I' 'shlibFirst/include' '-c' '-o' 'mylib.o' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
```

```sh
objdump -D shlibFirst/mylib.o
```

## Link ObjectFile into a SharedLibrary

Linker called with `-shared` flag

```sh
g++ -shared shlibFirst/mylib.o -o shlibFirst/libmylib.so -v
```

```sh
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/6/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 6.3.0-18+deb9u1' --with-bugurl=file:///usr/share/doc/gcc-6/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-6 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --enable-default-pie --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-6-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-6-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-6-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --with-target-system-zlib --enable-objc-gc=auto --enable-multiarch --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 6.3.0 20170516 (Debian 6.3.0-18+deb9u1) 
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-shared' '-o' 'shlibFirst/libmylib.so' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/6/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/6/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/6/lto-wrapper -plugin-opt=-fresolution=/tmp/ccdw0px7.res -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc_s --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu -shared -o shlibFirst/libmylib.so /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/6/crtbeginS.o -L/usr/lib/gcc/x86_64-linux-gnu/6 -L/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/6/../../.. shlibFirst/mylib.o -lstdc++ -lm -lgcc_s -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/6/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crtn.o
COLLECT_GCC_OPTIONS='-shared' '-o' 'shlibFirst/libmylib.so' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
```

----------------------------

# Create Client Binary via Linking


## 

Build time search for shared library is done via `L`.

```sh
g++                                               clientApp/main.cpp -o main
```
```sh
g++ -IshlibFirst/include                          clientApp/main.cpp -o main
```

```sh
g++ -IshlibFirst/include                  -lmylib clientApp/main.cpp -o main
```

```sh
g++ -IshlibFirst/include -Wl,-LshlibFirst -lmylib clientApp/main.cpp -o main
```

```sh
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/6/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 6.3.0-18+deb9u1' --with-bugurl=file:///usr/share/doc/gcc-6/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-6 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --enable-default-pie --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-6-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-6-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-6-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --with-target-system-zlib --enable-objc-gc=auto --enable-multiarch --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 6.3.0 20170516 (Debian 6.3.0-18+deb9u1) 
COLLECT_GCC_OPTIONS='-I' 'shlibFirst/include' '-LshlibFirst' '-o' 'main' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/6/cc1plus -quiet -v -I shlibFirst/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE clientApp/main.cpp -quiet -dumpbase main.cpp -mtune=generic -march=x86-64 -auxbase main -version -o /tmp/ccK1Aw6j.s
GNU C++14 (Debian 6.3.0-18+deb9u1) version 6.3.0 20170516 (x86_64-linux-gnu)
        compiled by GNU C version 6.3.0 20170516, GMP version 6.1.2, MPFR version 3.1.5, MPC version 1.0.3, isl version 0.15
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/6"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/6/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 shlibFirst/include
 /usr/include/c++/6
 /usr/include/x86_64-linux-gnu/c++/6
 /usr/include/c++/6/backward
 /usr/lib/gcc/x86_64-linux-gnu/6/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/6/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++14 (Debian 6.3.0-18+deb9u1) version 6.3.0 20170516 (x86_64-linux-gnu)
        compiled by GNU C version 6.3.0 20170516, GMP version 6.1.2, MPFR version 3.1.5, MPC version 1.0.3, isl version 0.15
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9d922bffefb5a33c8f2905f4ce829a36
COLLECT_GCC_OPTIONS='-I' 'shlibFirst/include' '-LshlibFirst' '-o' 'main' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 as -v -I shlibFirst/include --64 -o /tmp/ccSiC9ML.o /tmp/ccK1Aw6j.s
GNU assembler version 2.28 (x86_64-linux-gnu) using BFD version (GNU Binutils for Debian) 2.28
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/6/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/6/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-I' 'shlibFirst/include' '-LshlibFirst' '-o' 'main' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/6/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/6/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/6/lto-wrapper -plugin-opt=-fresolution=/tmp/ccjl7Hud.res -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu -dynamic-linker /lib64/ld-linux-x86-64.so.2 -pie -o main /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/Scrt1.o /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/6/crtbeginS.o -LshlibFirst -L/usr/lib/gcc/x86_64-linux-gnu/6 -L/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/6/../../.. -lmylib /tmp/ccSiC9ML.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/x86_64-linux-gnu/6/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crtn.o
COLLECT_GCC_OPTIONS='-I' 'shlibFirst/include' '-LshlibFirst' '-o' 'main' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
```


RPATH or DT_PATH

-rpath or -R 

RUNPATH or DT_RUNPATH

Whenever RUNPATH is specified, linker sets both rpath and runpath to same value
Whenever RUNPATH is not empty, DT_RPATH is ignored so that LD_LIBRARY_PATH gets chance of being respected

-rpath,--enable-new-dtags  or -R,--enable-new-dtags

```sh
objdump -x main | grep PATH
or
readelf -d main | head -20
readelf -d main | grep PATH
or
objdump -x main | grep PATH

chrpath -l main
```

```sh
g++ -Wall -fPIC -IshlibFirst/include -L./shlibFirst  -lmylib -Wl,-rpath,./shlibFirst clientApp/main.cpp -o main -v

g++ -c -IshlibFirst/include clientApp/main.cpp -o main.o
nasm -f elf64 -o $1.o $1.asm


/usr/lib/gcc/x86_64-linux-gnu/6/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/6/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/6/lto-wrapper -plugin-opt=-fresolution=/tmp/ccjl7Hud.res -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu -dynamic-linker /lib64/ld-linux-x86-64.so.2 -pie -o main /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/Scrt1.o /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/6/crtbeginS.o -LshlibFirst -L/usr/lib/gcc/x86_64-linux-gnu/6 -L/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/6/../../.. -lmylib main.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/x86_64-linux-gnu/6/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crtn.o -rpath=./shlibFirst --enable-new-dtags

ld 
-plugin /usr/lib/gcc/x86_64-linux-gnu/6/liblto_plugin.so
-plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/6/lto-wrapper 
-plugin-opt=-fresolution=/tmp/ccjl7Hud.res 
-plugin-opt=-pass-through=-lgcc_s 
-plugin-opt=-pass-through=-lgcc 
-plugin-opt=-pass-through=-lc 
-plugin-opt=-pass-through=-lgcc_s 
-plugin-opt=-pass-through=-lgcc 
--sysroot=/ 
--build-id 
--eh-frame-hdr 
-m elf_x86_64 
--hash-style=gnu 
-dynamic-linker /lib64/ld-linux-x86-64.so.2 
-pie 
-o main 
/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/Scrt1.o /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crti.o 
/usr/lib/gcc/x86_64-linux-gnu/6/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu/crtn.o
/usr/lib/gcc/x86_64-linux-gnu/6/crtbeginS.o 
-LshlibFirst 
-L/usr/lib/gcc/x86_64-linux-gnu/6 -L/usr/lib/gcc/x86_64-linux-gnu/6/../../../x86_64-linux-gnu 
-L/usr/lib/gcc/x86_64-linux-gnu/6/../../../../lib 
-L/lib/x86_64-linux-gnu 
-L/lib/../lib 
-L/usr/lib/x86_64-linux-gnu 
-L/usr/lib/../lib 
-L/usr/lib/gcc/x86_64-linux-gnu/6/../../.. 
-lmylib 
main.o 
-lstdc++ 
-lm 
-lc 
-lgcc_s 
-lgcc
 


LD_DEBUG=libs ./main                             => ShouldRun
LD_LIBRARY_PATH=WrongPath ./main   => ShouldRun

```

```sh
g++ -IshlibFirst/include -Wl,-LshlibFirst -Wl,-rpath=shlibFirst,--enable-new-dtags -lmylib clientApp/main.cpp -o main

./main                             => ShouldRun
LD_LIBRARY_PATH=WrongPath ./main   => ShouldRun
```



# Running Client Binary via Dynamic Loading & Linking

* For running the client binary

        there is no need to search for header files
        if it is linked to shared library then that library needs to known for loader
* Loader loads the shared library and dynamic linking occurs

```sh
./main
```

```sh
LD_LIBRARY_PATH=shlibFirst ./main
```

## Links

* https://gcc.gnu.org/onlinedocs/gcc/Preprocessor-Options.html
