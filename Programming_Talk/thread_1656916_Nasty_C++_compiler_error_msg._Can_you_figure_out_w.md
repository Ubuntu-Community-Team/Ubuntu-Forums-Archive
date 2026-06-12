---
title: "Nasty C++ compiler error msg. Can you figure out why?"
date: 2010-12-31
forum: Programming Talk
---

### Post by nitro_n2o on 2010-12-31
Hello there all C++ gurus and g++ lovers

one day I was hacking away something and ended up with huge nasty pages of g++ compiler errors. I've eventually figured it out, but thought that some people will be able to look at these errors and figure out the problem right away! Can you figure out this mini challenge? 

g++ -o lib/features.os -c -O3 -Wall -fPIC -D_DEBUG_ -g -msse2 -msse3 -mfpmath=sse -mmmx -fPIC -DUSE_CV -I/usr/local/include/opencv -Ilib lib/features.cc
In file included from /usr/local/include/opencv/cxtypes.h:52:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/assert.h:39:42: error: missing binary operator before token "("
/usr/include/assert.h:108:42: error: missing binary operator before token "("
In file included from /usr/include/math.h:34:0,
                 from /usr/local/include/opencv/cxtypes.h:83,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/bits/huge_val.h:28:18: error: missing binary operator before token "("
/usr/include/bits/huge_val.h:30:20: error: missing binary operator before token "("
In file included from /usr/local/include/opencv/cxtypes.h:83:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/math.h:392:42: error: missing binary operator before token "("
In file included from /usr/include/libio.h:62:0,
                 from /usr/include/stdio.h:75,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdio:45,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/char_traits.h:46,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/ios:41,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/istream:40,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/sstream:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/complex:47,
                 from /usr/local/include/opencv/cxcore.hpp:53,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/sys/cdefs.h:46:44: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:50:44: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:135:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:148:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:206:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:215:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:224:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:233:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:245:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:255:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:264:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:272:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:286:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:294:43: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:312:19: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:321:20: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:326:20: error: missing binary operator before token "("
/usr/include/sys/cdefs.h:333:19: error: missing binary operator before token "("
In file included from /usr/local/include/opencv/cvtypes.h:46:0,
                 from /usr/local/include/opencv/cv.h:59,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/assert.h:39:42: error: missing binary operator before token "("
/usr/include/assert.h:108:42: error: missing binary operator before token "("
In file included from /usr/include/assert.h:37:0,
                 from /usr/local/include/opencv/cxtypes.h:52,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
lib/features.h:19:21: error: variable or field 'harris_buckets' declared void
lib/features.h:19:21: error: 'cv' has not been declared
lib/features.h:19:41: error: 'vector' is not a member of 'std'
lib/features.h:19:53: error: 'cv' has not been declared
lib/features.h:19:67: error: 'pts' was not declared in this scope
lib/features.h:19:72: error: expected primary-expression before 'int'
lib/features.h:19:79: error: expected primary-expression before 'int'
lib/features.h:20:21: error: expected primary-expression before 'int'
lib/features.h:20:42: error: expected primary-expression before 'int'
lib/features.h:20:57: error: expected primary-expression before 'double'
In file included from /usr/local/include/opencv/cxtypes.h:52:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/assert.h:68:1: error: '__BEGIN_DECLS' does not name a type
/usr/include/assert.h:79:6: error: expected initializer before '__THROW'
/usr/include/assert.h:85:6: error: expected initializer before '__THROW'
/usr/include/assert.h:88:1: error: '__END_DECLS' does not name a type
In file included from /usr/local/include/opencv/cxtypes.h:53:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/stdlib.h:35:1: error: '__BEGIN_DECLS' does not name a type
/usr/include/stdlib.h:102:5: error: 'div_t' does not name a type
/usr/include/stdlib.h:113:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:143:1: error: '__BEGIN_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:149:6: error: expected initializer before '__THROW'
/usr/include/stdlib.h:152:6: error: expected initializer before '__THROW'
/usr/include/stdlib.h:153:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:168:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:190:6: error: expected initializer before '__THROW'
/usr/include/stdlib.h:191:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:382:41: error: expected initializer before '__THROW'
/usr/include/stdlib.h:383:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:474:6: error: expected initializer before '__THROW'
/usr/include/stdlib.h:475:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:488:32: error: expected initializer before '__THROW'
/usr/include/stdlib.h:489:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:517:43: error: expected initializer before '__THROW'
/usr/include/stdlib.h:518:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:532:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:546:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:640:1: error: '__BEGIN_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:646:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:677:1: error: '__BEGIN_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:687:6: error: '__compar_fn_t' has not been declared
/usr/include/stdlib.h:687:30: error: expected initializer before '__nonnull'
/usr/include/stdlib.h:691:26: error: expected initializer before '__THROW'
/usr/include/stdlib.h:692:37: error: expected initializer before '__THROW'
/usr/include/stdlib.h:693:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:708:6: error: expected initializer before '__THROW'
/usr/include/stdlib.h:709:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/stdlib.h:783:48: error: expected initializer before '__THROW'
/usr/include/stdlib.h:786:48: error: expected initializer before '__THROW'
/usr/include/stdlib.h:791:46: error: expected initializer before '__THROW'
/usr/include/stdlib.h:795:6: error: expected initializer before '__THROW'
/usr/include/stdlib.h:796:1: error: '__END_NAMESPACE_STD' does not name a type
In file included from /usr/local/include/opencv/cxtypes.h:54:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/string.h:28:1: error: '__BEGIN_DECLS' does not name a type
In file included from /usr/local/include/opencv/cxtypes.h:54:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/string.h:44:6: error: expected initializer before '__THROW'
/usr/include/string.h:45:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/string.h:63:6: error: expected initializer before '__THROW'
/usr/include/string.h:67:7: error: expected initializer before '__THROW'
/usr/include/string.h:68:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/string.h:89:6: error: expected initializer before '__THROW'
/usr/include/string.h:93:6: error: expected initializer before '__THROW'
/usr/include/string.h:96:21: error: expected initializer before '__THROW'
/usr/include/string.h:100:6: error: expected initializer before '__THROW'
/usr/include/string.h:103:6: error: expected initializer before '__THROW'
/usr/include/string.h:107:6: error: expected initializer before '__THROW'
/usr/include/string.h:111:6: error: expected initializer before '__THROW'
/usr/include/string.h:112:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/string.h:171:6: error: expected initializer before '__THROW'
/usr/include/string.h:172:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/string.h:189:6: error: expected initializer before '__THROW'
/usr/include/string.h:192:6: error: expected initializer before '__THROW'
/usr/include/string.h:195:6: error: expected initializer before '__THROW'
/usr/include/string.h:200:6: error: expected initializer before '__THROW'
/usr/include/string.h:201:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/string.h:240:1: error: '__BEGIN_NAMESPACE_STD' does not name a type
/usr/include/string.h:244:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/string.h:257:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/string.h:432:1: error: '__END_DECLS' does not name a type
In file included from /usr/include/math.h:28:0,
                 from /usr/local/include/opencv/cxtypes.h:83,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
lib/features.h:19:21: error: variable or field 'harris_buckets' declared void
lib/features.h:19:21: error: 'cv' has not been declared
lib/features.h:19:41: error: 'vector' is not a member of 'std'
lib/features.h:19:53: error: 'cv' has not been declared
lib/features.h:19:67: error: 'pts' was not declared in this scope
lib/features.h:19:72: error: expected primary-expression before 'int'
lib/features.h:19:79: error: expected primary-expression before 'int'
lib/features.h:20:21: error: expected primary-expression before 'int'
lib/features.h:20:42: error: expected primary-expression before 'int'
lib/features.h:20:57: error: expected primary-expression before 'double'
In file included from /usr/local/include/opencv/cxtypes.h:83:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/math.h:30:1: error: '__BEGIN_DECLS' does not name a type
In file included from /usr/include/math.h:71:0,
                 from /usr/local/include/opencv/cxtypes.h:83,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/bits/mathcalls.h:55:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:55:1: error: 'acos' was not declared in this scope
/usr/include/bits/mathcalls.h:55:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:55:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:55:1: error: initializer expression list treated as compound expression
/usr/include/bits/mathcalls.h:55:1: error: expected ',' or ';' before '(' token
/usr/include/bits/mathcalls.h:57:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:57:1: error: 'asin' was not declared in this scope
/usr/include/bits/mathcalls.h:57:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:57:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:57:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:57:1: error: 'asin' was not declared in this scope
/usr/include/bits/mathcalls.h:57:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:57:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:59:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:59:1: error: 'atan' was not declared in this scope
/usr/include/bits/mathcalls.h:59:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:59:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:59:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:59:1: error: 'atan' was not declared in this scope
/usr/include/bits/mathcalls.h:59:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:59:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:61:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:61:1: error: 'atan2' was not declared in this scope
/usr/include/bits/mathcalls.h:61:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:61:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:61:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:61:1: error: 'atan2' was not declared in this scope
/usr/include/bits/mathcalls.h:61:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:61:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:64:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:64:1: error: 'cos' was not declared in this scope
/usr/include/bits/mathcalls.h:64:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:64:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:64:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:64:1: error: 'cos' was not declared in this scope
/usr/include/bits/mathcalls.h:64:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:64:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:66:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:66:1: error: 'sin' was not declared in this scope
/usr/include/bits/mathcalls.h:66:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:66:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:66:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:66:1: error: 'sin' was not declared in this scope
/usr/include/bits/mathcalls.h:66:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:66:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:68:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:68:1: error: 'tan' was not declared in this scope
/usr/include/bits/mathcalls.h:68:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:68:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:68:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:68:1: error: 'tan' was not declared in this scope
/usr/include/bits/mathcalls.h:68:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:68:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:73:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:73:1: error: 'cosh' was not declared in this scope
/usr/include/bits/mathcalls.h:73:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:73:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:73:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:73:1: error: 'cosh' was not declared in this scope
/usr/include/bits/mathcalls.h:73:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:73:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:75:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:75:1: error: 'sinh' was not declared in this scope
/usr/include/bits/mathcalls.h:75:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:75:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:75:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:75:1: error: 'sinh' was not declared in this scope
/usr/include/bits/mathcalls.h:75:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:75:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:77:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:77:1: error: 'tanh' was not declared in this scope
/usr/include/bits/mathcalls.h:77:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:77:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:77:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:77:1: error: 'tanh' was not declared in this scope
/usr/include/bits/mathcalls.h:77:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:77:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:78:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/bits/mathcalls.h:101:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:101:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:101:1: error: 'exp' was not declared in this scope
/usr/include/bits/mathcalls.h:101:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:101:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:104:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:104:1: error: 'frexp' was not declared in this scope
/usr/include/bits/mathcalls.h:104:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:104:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:104:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:104:1: error: 'frexp' was not declared in this scope
/usr/include/bits/mathcalls.h:104:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:104:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:107:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:107:1: error: 'ldexp' was not declared in this scope
/usr/include/bits/mathcalls.h:107:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:107:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:107:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:107:1: error: 'ldexp' was not declared in this scope
/usr/include/bits/mathcalls.h:107:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:107:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:110:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:110:1: error: 'log' was not declared in this scope
/usr/include/bits/mathcalls.h:110:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:110:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:110:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:110:1: error: 'log' was not declared in this scope
/usr/include/bits/mathcalls.h:110:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:110:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:113:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:113:1: error: 'log10' was not declared in this scope
/usr/include/bits/mathcalls.h:113:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:113:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:113:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:113:1: error: 'log10' was not declared in this scope
/usr/include/bits/mathcalls.h:113:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:113:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:116:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:116:1: error: 'modf' was not declared in this scope
/usr/include/bits/mathcalls.h:116:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:116:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:116:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:116:1: error: 'modf' was not declared in this scope
/usr/include/bits/mathcalls.h:116:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:116:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:117:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/bits/mathcalls.h:154:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:154:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:154:1: error: 'pow' was not declared in this scope
/usr/include/bits/mathcalls.h:154:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:154:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:157:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:157:1: error: 'sqrt' was not declared in this scope
/usr/include/bits/mathcalls.h:157:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:157:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:157:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:157:1: error: 'sqrt' was not declared in this scope
/usr/include/bits/mathcalls.h:157:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:157:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:158:1: error: '__END_NAMESPACE_STD' does not name a type
/usr/include/bits/mathcalls.h:179:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:179:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:179:1: error: 'ceil' was not declared in this scope
/usr/include/bits/mathcalls.h:179:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:179:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:182:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:182:1: error: 'fabs' was not declared in this scope
/usr/include/bits/mathcalls.h:182:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:182:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:182:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:182:1: error: 'fabs' was not declared in this scope
/usr/include/bits/mathcalls.h:182:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:182:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:185:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:185:1: error: 'floor' was not declared in this scope
/usr/include/bits/mathcalls.h:185:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:185:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:185:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:185:1: error: 'floor' was not declared in this scope
/usr/include/bits/mathcalls.h:185:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:185:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:188:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:188:1: error: 'fmod' was not declared in this scope
/usr/include/bits/mathcalls.h:188:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:188:1: error: redefinition of 'double __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: 'double __CONCAT' previously defined here
/usr/include/bits/mathcalls.h:188:1: error: '__' was not declared in this scope
/usr/include/bits/mathcalls.h:188:1: error: 'fmod' was not declared in this scope
/usr/include/bits/mathcalls.h:188:1: error: '__CONCAT' cannot be used as a function
/usr/include/bits/mathcalls.h:188:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:193:1: error: conflicting declaration 'int __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: '__CONCAT' has a previous declaration as 'double __CONCAT'
/usr/include/bits/mathcalls.h:193:1: error: '__isinf' was not declared in this scope
/usr/include/bits/mathcalls.h:193:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:196:1: error: conflicting declaration 'int __CONCAT'
/usr/include/bits/mathcalls.h:55:1: error: '__CONCAT' has a previous declaration as 'double __CONCAT'
/usr/include/bits/mathcalls.h:196:1: error: '__finite' was not declared in this scope
/usr/include/bits/mathcalls.h:196:1: error: expected primary-expression before ')' token
/usr/include/bits/mathcalls.h:197:1: error: '__END_NAMESPACE_STD' does not name a type
In file included from /usr/local/include/opencv/cxtypes.h:83:0,
                 from /usr/local/include/opencv/cxcore.h:70,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/math.h:465:1: error: '__END_DECLS' does not name a type
In file included from /usr/local/include/opencv/cxcore.h:70:0,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/include/opencv/cxtypes.h:177:5: error: 'int64' does not name a type
/usr/local/include/opencv/cxtypes.h: In function 'int cvRound(double)':
/usr/local/include/opencv/cxtypes.h:228:28: error: 'lrint' was not declared in this scope
/usr/local/include/opencv/cxtypes.h: At global scope:
/usr/local/include/opencv/cxtypes.h:308:24: error: 'cvRNG' declared as an 'inline' variable
/usr/local/include/opencv/cxtypes.h:308:24: error: 'int64' was not declared in this scope
/usr/local/include/opencv/cxtypes.h:309:1: error: expected ',' or ';' before '{' token
/usr/local/include/opencv/cxtypes.h: In function 'CvMat cvMat(int, int, int, void*)':
/usr/local/include/opencv/cxtypes.h:636:5: error: '__STRING' was not declared in this scope
/usr/local/include/opencv/cxtypes.h:636:5: error: '__assert_fail' was not declared in this scope
/usr/local/include/opencv/cxtypes.h: In function 'double cvmGet(const CvMat*, int, int)':
/usr/local/include/opencv/cxtypes.h:667:5: error: '__STRING' was not declared in this scope
/usr/local/include/opencv/cxtypes.h:667:5: error: '__assert_fail' was not declared in this scope
/usr/local/include/opencv/cxtypes.h: In function 'void cvmSet(CvMat*, int, int, double)':
/usr/local/include/opencv/cxtypes.h:684:5: error: '__STRING' was not declared in this scope
/usr/local/include/opencv/cxtypes.h:684:5: error: '__assert_fail' was not declared in this scope
In file included from /usr/local/include/opencv/cv.h:58:0,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/include/opencv/cxcore.h: In function 'void cvSetRemoveByPtr(CvSet*, void*)':
/usr/local/include/opencv/cxcore.h:1143:5: error: '__STRING' was not declared in this scope
/usr/local/include/opencv/cxcore.h:1143:5: error: '__assert_fail' was not declared in this scope
/usr/local/include/opencv/cxcore.h: At global scope:
/usr/local/include/opencv/cxcore.h:1770:1: error: 'int64' does not name a type
In file included from /usr/include/limits.h:27:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/include-fixed/limits.h:169,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/include-fixed/syslimits.h:7,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/include-fixed/limits.h:34,
                 from /usr/local/include/opencv/cxmisc.h:51,
                 from /usr/local/include/opencv/cxcore.hpp:46,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
lib/features.h:19:21: error: variable or field 'harris_buckets' declared void
lib/features.h:19:21: error: 'cv' has not been declared
lib/features.h:19:41: error: 'vector' is not a member of 'std'
lib/features.h:19:53: error: 'cv' has not been declared
lib/features.h:19:67: error: 'pts' was not declared in this scope
lib/features.h:19:72: error: expected primary-expression before 'int'
lib/features.h:19:79: error: expected primary-expression before 'int'
lib/features.h:20:21: error: expected primary-expression before 'int'
lib/features.h:20:42: error: expected primary-expression before 'int'
lib/features.h:20:57: error: expected primary-expression before 'double'
In file included from /usr/local/include/opencv/cxcore.hpp:46:0,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/include/opencv/cxmisc.h: In function 'void* cvAlignPtr(const void*, int)':
/usr/local/include/opencv/cxmisc.h:216:5: error: '__STRING' was not declared in this scope
/usr/local/include/opencv/cxmisc.h:216:5: error: '__assert_fail' was not declared in this scope
/usr/local/include/opencv/cxmisc.h: In function 'int cvAlign(int, int)':
/usr/local/include/opencv/cxmisc.h:222:5: error: '__STRING' was not declared in this scope
/usr/local/include/opencv/cxmisc.h:222:5: error: '__assert_fail' was not declared in this scope
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:60:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/algorithm:63,
                 from /usr/local/include/opencv/cxcore.hpp:51,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdlib: At global scope:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdlib:60:40: error: expected initializer before '_GLIBCXX_NORETURN'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdlib:62:38: error: expected initializer before '_GLIBCXX_NORETURN'
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:62:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/algorithm:63,
                 from /usr/local/include/opencv/cxcore.hpp:51,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_heap.h: In function 'bool std::__is_heap(_RandomAccessIterator, _RandomAccessIterator)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_heap.h:117:38: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_heap.h: In function 'bool std::__is_heap(_RandomAccessIterator, _RandomAccessIterator, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_heap.h:123:46: error: 'distance' is not a member of 'std'
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:62:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:63,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/algorithm:63,
                 from /usr/local/include/opencv/cxcore.hpp:51,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In static member function 'static _ForwardIterator std::__uninitialized_copy<<anonymous> >::uninitialized_copy(_InputIterator, _InputIterator, _ForwardIterator)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:71:4: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:72:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:77:12: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:77:15: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:77:15: note: (if you use '-fpermissive', G++ will accept your code, but allowing the use of an undeclared name is deprecated)
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:78:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In static member function 'static void std::__uninitialized_fill<<anonymous> >::uninitialized_fill(_ForwardIterator, _ForwardIterator, const _Tp&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:129:4: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:130:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:134:12: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:134:15: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:135:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In static member function 'static void std::__uninitialized_construct_range_dispatch<<anonymous> >::__ucr(_ForwardIterator, _ForwardIterator, _Tp&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:186:4: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:187:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:195:12: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:195:15: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:196:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In static member function 'static void std::__uninitialized_fill_n<<anonymous> >::uninitialized_fill_n(_ForwardIterator, _Size, const _Tp&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:245:4: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:246:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:250:12: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:250:15: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:251:6: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In function '_ForwardIterator std::__uninitialized_copy_a(_InputIterator, _InputIterator, _ForwardIterator, _Allocator&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:301:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:302:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:307:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:307:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:308:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In function 'void std::__uninitialized_fill_a(_ForwardIterator, _ForwardIterator, const _Tp&, _Allocator&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:337:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:338:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:342:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:342:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:343:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In function 'void std::__uninitialized_fill_n_a(_ForwardIterator, _Size, const _Tp&, _Allocator&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:362:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:363:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:367:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:367:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:368:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In function '_ForwardIterator std::__uninitialized_copy_move(_InputIterator1, _InputIterator1, _InputIterator2, _InputIterator2, _ForwardIterator, _Allocator&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:404:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:405:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:408:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:408:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:409:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In function '_ForwardIterator std::__uninitialized_move_copy(_InputIterator1, _InputIterator1, _InputIterator2, _InputIterator2, _ForwardIterator, _Allocator&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:432:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:433:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:436:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:436:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:437:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In function '_ForwardIterator std::__uninitialized_fill_move(_ForwardIterator, _ForwardIterator, const _Tp&, _InputIterator, _InputIterator, _Allocator&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:454:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:455:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:458:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:458:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:459:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h: In function 'void std::__uninitialized_move_fill(_InputIterator, _InputIterator, _ForwardIterator, _ForwardIterator, const _Tp&, _Allocator&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:479:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:480:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:483:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:483:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_uninitialized.h:484:2: error: expected ';' before '{' token
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:63:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/algorithm:63,
                 from /usr/local/include/opencv/cxcore.hpp:51,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h: In function 'std::pair<_Tp*, int> std::get_temporary_buffer(ptrdiff_t)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:88:2: error: '__numeric_traits' is not a member of '__gnu_cxx'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:88:39: error: expected primary-expression before '>' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:88:40: error: '::__max' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h: In constructor 'std::_Temporary_buffer<_ForwardIterator, _Tp>::_Temporary_buffer(_ForwardIterator, _ForwardIterator)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:182:23: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:185:7: error: '__try' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:186:2: error: expected ';' before '{' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:195:15: error: expected primary-expression before '...' token
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:195:18: error: there are no arguments to '__catch' that depend on a template parameter, so a declaration of '__catch' must be available
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_tempbuf.h:196:2: error: expected ';' before '{' token
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/algorithm:63:0,
                 from /usr/local/include/opencv/cxcore.hpp:51,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_BidirectionalIterator1 std::__find_end(_BidirectionalIterator1, _BidirectionalIterator1, _BidirectionalIterator2, _BidirectionalIterator2, std::bidirectional_iterator_tag, std::bidirectional_iterator_tag)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:565:15: error: 'reverse_iterator' does not name a type
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:566:15: error: 'reverse_iterator' does not name a type
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:568:7: error: '_RevIterator1' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:568:21: error: expected ';' before '__rlast1'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:569:7: error: '_RevIterator2' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:569:21: error: expected ';' before '__rlast2'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:570:21: error: expected ';' before '__rresult'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:575:11: error: '__rresult' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:575:24: error: '__rlast1' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:580:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:580:28: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_BidirectionalIterator1 std::__find_end(_BidirectionalIterator1, _BidirectionalIterator1, _BidirectionalIterator2, _BidirectionalIterator2, std::bidirectional_iterator_tag, std::bidirectional_iterator_tag, _BinaryPredicate)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:601:15: error: 'reverse_iterator' does not name a type
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:602:15: error: 'reverse_iterator' does not name a type
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:604:7: error: '_RevIterator1' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:604:21: error: expected ';' before '__rlast1'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:605:7: error: '_RevIterator2' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:605:21: error: expected ';' before '__rlast2'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:606:21: error: expected ';' before '__rresult'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:610:11: error: '__rresult' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:610:24: error: '__rlast1' was not declared in this scope
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:615:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:615:28: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_ForwardIterator std::__inplace_stable_partition(_ForwardIterator, _ForwardIterator, _Predicate, _Distance)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:1779:7: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:1789:7: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:1789:29: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_ForwardIterator std::__stable_partition_adaptive(_ForwardIterator, _ForwardIterator, _Predicate, _Distance, _Pointer, _Distance)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:1824:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:1834:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:1834:26: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_FIter std::lower_bound(_FIter, _FIter, const _Tp&, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2405:29: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2413:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_FIter std::upper_bound(_FIter, _FIter, const _Tp&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2452:29: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2460:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_FIter std::upper_bound(_FIter, _FIter, const _Tp&, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2505:29: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2513:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'std::pair<_FIter, _FIter> std::equal_range(_FIter, _FIter, const _Tp&)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2560:29: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2568:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2580:8: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'std::pair<_FIter, _FIter> std::equal_range(_FIter, _FIter, const _Tp&, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2627:29: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2635:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2647:8: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function '_BidirectionalIterator1 std::__rotate_adaptive(_BidirectionalIterator1, _BidirectionalIterator1, _BidirectionalIterator1, _Distance, _Distance, _BidirectionalIterator2, _Distance)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2820:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2820:26: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::__merge_adaptive(_BidirectionalIterator, _BidirectionalIterator, _BidirectionalIterator, _Distance, _Distance, _Pointer, _Distance)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2862:8: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2865:18: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2870:8: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2873:18: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::__merge_adaptive(_BidirectionalIterator, _BidirectionalIterator, _BidirectionalIterator, _Distance, _Distance, _Pointer, _Distance, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2925:8: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2928:18: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2933:8: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2936:18: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::__merge_without_buffer(_BidirectionalIterator, _BidirectionalIterator, _BidirectionalIterator, _Distance, _Distance)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2974:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2976:14: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2981:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2983:14: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2987:7: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:2987:34: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::__merge_without_buffer(_BidirectionalIterator, _BidirectionalIterator, _BidirectionalIterator, _Distance, _Distance, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3019:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3022:14: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3027:4: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3030:14: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3034:7: error: 'advance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3034:34: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::inplace_merge(_BIter, _BIter, _BIter)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3080:30: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3081:30: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::inplace_merge(_BIter, _BIter, _BIter, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3137:36: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:3138:36: error: 'distance' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::random_shuffle(_RAIter, _RAIter)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:4956:35: error: 'rand' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::nth_element(_RAIter, _RAIter, _RAIter)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:5139:5: error: '__lg' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::nth_element(_RAIter, _RAIter, _RAIter, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:5179:5: error: '__lg' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::sort(_RAIter, _RAIter)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:5213:5: error: '__lg' is not a member of 'std'
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h: In function 'void std::sort(_RAIter, _RAIter, _Compare)':
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algo.h:5251:5: error: '__lg' is not a member of 'std'
In file included from /usr/local/include/opencv/cxcore.hpp:52:0,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath: At global scope:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:111:11: error: '::acos' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:127:11: error: '::asin' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:143:11: error: '::atan' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:159:11: error: '::atan2' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:181:11: error: '::ceil' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:197:11: error: '::cos' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:213:11: error: '::cosh' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:229:11: error: '::exp' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:245:11: error: '::fabs' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:261:11: error: '::floor' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:277:11: error: '::fmod' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:287:11: error: '::frexp' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:303:11: error: '::ldexp' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:319:11: error: '::log' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:335:11: error: '::log10' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:351:11: error: '::modf' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:361:11: error: '::pow' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:399:11: error: '::sin' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:415:11: error: '::sinh' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:431:11: error: '::sqrt' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:447:11: error: '::tan' has not been declared
/usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cmath:463:11: error: '::tanh' has not been declared
In file included from /usr/include/stdio.h:28:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdio:45,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/char_traits.h:46,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/ios:41,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/istream:40,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/sstream:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/complex:47,
                 from /usr/local/include/opencv/cxcore.hpp:53,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
lib/features.h:19:21: error: variable or field 'harris_buckets' declared void
lib/features.h:19:21: error: 'cv' has not been declared
lib/features.h:19:41: error: 'vector' is not a member of 'std'
lib/features.h:19:53: error: 'cv' has not been declared
lib/features.h:19:67: error: 'pts' was not declared in this scope
lib/features.h:19:72: error: expected primary-expression before 'int'
lib/features.h:19:79: error: expected primary-expression before 'int'
lib/features.h:20:21: error: expected primary-expression before 'int'
lib/features.h:20:42: error: expected primary-expression before 'int'
lib/features.h:20:57: error: expected primary-expression before 'double'
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdio:45:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/char_traits.h:46,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/ios:41,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/istream:40,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/sstream:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/complex:47,
                 from /usr/local/include/opencv/cxcore.hpp:53,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/stdio.h:30:1: error: '__BEGIN_DECLS' does not name a type
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdio:45:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/char_traits.h:46,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/ios:41,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/istream:40,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/sstream:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/complex:47,
                 from /usr/local/include/opencv/cxcore.hpp:53,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/stdio.h:47:1: error: '__BEGIN_NAMESPACE_STD' does not name a type
/usr/include/stdio.h:50:1: error: '__END_NAMESPACE_STD' does not name a type
In file included from /usr/include/sys/cdefs.h:25:0,
                 from /usr/include/libio.h:62,
                 from /usr/include/stdio.h:75,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdio:45,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/char_traits.h:46,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/ios:41,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/istream:40,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/sstream:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/complex:47,
                 from /usr/local/include/opencv/cxcore.hpp:53,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
lib/features.h:19:21: error: variable or field 'harris_buckets' declared void
lib/features.h:19:21: error: 'cv' has not been declared
lib/features.h:19:41: error: 'vector' is not a member of 'std'
lib/features.h:19:53: error: 'cv' has not been declared
lib/features.h:19:67: error: 'pts' was not declared in this scope
lib/features.h:19:72: error: expected primary-expression before 'int'
lib/features.h:19:79: error: expected primary-expression before 'int'
lib/features.h:20:21: error: expected primary-expression before 'int'
lib/features.h:20:42: error: expected primary-expression before 'int'
lib/features.h:20:57: error: expected primary-expression before 'double'
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/cstdio:45:0,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/char_traits.h:46,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/ios:41,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/istream:40,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/sstream:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/complex:47,
                 from /usr/local/include/opencv/cxcore.hpp:53,
                 from /usr/local/include/opencv/cxcore.h:1826,
                 from /usr/local/include/opencv/cv.h:58,
                 from lib/features.h:5,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/os_defines.h:39,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/i686-pc-linux-gnu/bits/c++config.h:275,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/bits/stl_algobase.h:60,
                 from /usr/local/lib/gcc/i686-pc-linux-gnu/4.5.1/../../../../include/c++/4.5.1/vector:61,
                 from lib/features.cc:3:
/usr/include/stdio.h:172:8: error: 'FILE' does not name a type
/usr/include/stdio.h:214:20: error: &#3

---

### Post by MadCow108 on 2010-12-31
you already solved the problem?
makes it a kind of pointless challenge without the source

Anyhow the length of an error message does not say much, gcc continues compiling even after an error so you get ton's of resulting errors in certain cases. (This in my opinion stupid behavior can luckily be turned of in newer versions)
Rule of thumb when fixing these things:
always look at the **first** error message and ignore the rest until the first is fixed
> 
/usr/include/assert.h:39:42: error: missing binary operator before token "("
/usr/include/assert.h:108:42: error: missing binary operator before token "("


Aha an error in a system header.
My guess is a unclosed bracket/parentheses inside a header file which is included some time before assert.h

---

### Post by nitro_n2o on 2010-12-31
Nope! it is not an error with a system header. In fact, the syntax is 100% correct, the source is perfectly valid. There is one little tiny thing that in that huge message that gives you a hint. 

The problem is really interesting and so much to debug, if you believe me that the source is 100% correct :)

---

### Post by kevdog on 2010-12-31
I wasn't aware this was a game or contest.

---

### Post by GeneralZod on 2010-12-31
Your local features.h (lib/features.h) hides /usr/include/features.h?

---

### Post by dwhitney67 on 2010-12-31
> **nitro_n2o said:**
> Nope! it is not an error with a system header. In fact, the syntax is 100% correct, the source is perfectly valid. There is one little tiny thing that in that huge message that gives you a hint. 

The problem is really interesting and so much to debug, if you believe me that the source is 100% correct :)

The source code may be 100% correct; thus I also award you 100% for being stupid in opening this thread.  Who cares what the problem was; it will not help anyone posting over a hundred lines of error messages.

Personally I would pick at the "g++" statement, since it seems you are attempting to link object code together to form a shared library with an ".os" extension (should be .so).  However, when linking, the -c option is not required. So frankly, nobody is going to have a freaking clue what the issue is.  Go crawl back under a rock.

---

### Post by nitro_n2o on 2010-12-31
> **GeneralZod said:**
> Your local features.h (lib/features.h) hides /usr/include/features.h?

That is it :) the winner is GeneralZod

---

### Post by nitro_n2o on 2010-12-31
> **dwhitney67 said:**
> The source code may be 100% correct; thus I also award you 100% for being stupid in opening this thread.  Who cares what the problem was; it will not help anyone posting over a hundred lines of error messages.

Personally I would pick at the "g++" statement, since it seems you are attempting to link object code together to form a shared library with an ".os" extension (should be .so).  However, when linking, the -c option is not required. So frankly, nobody is going to have a freaking clue what the issue is.  Go crawl back under a rock.

That was very polite of you. Nobody forced to reply or contribute any opinion. A lot of people might find this very useful, it is very tricky to figure out the reason for this without knowing the names of the internal files. This generalizes to internal variable names used in libc as well.. after all you didn't figure it out, or even come to close to figure it out

---

### Post by nitro_n2o on 2010-12-31
> **dwhitney67 said:**
> The source code may be 100% correct; thus I also award you 100% for being stupid in opening this thread.  Who cares what the problem was; it will not help anyone posting over a hundred lines of error messages.

Personally I would pick at the "g++" statement, since it seems you are attempting to link object code together to form a shared library with an ".os" extension (should be .so).  However, when linking, the -c option is not required. So frankly, nobody is going to have a freaking clue what the issue is.  Go crawl back under a rock.

and by the way there was no linking involved. The *.os extension is just another extension instead of *.o, you can have any extension you like.. this is the default scons extension for binaries.. hopefully that will teach you something you didn't knw

---

### Post by Vox754 on 2010-12-31
> **nitro_n2o said:**
> and by the way there was no linking involved. The *.os extension is just another extension instead of *.o, you can have any extension you like.. this is the default scons extension for binaries.. hopefully that will teach you something you didn't knw

Here, I'll teach you something you didn't "knw".

```

Use "code" tags so your damn output doesn't span several screens pointlessly.

```

Why yes, of course you can go back and edit your posts!

---

