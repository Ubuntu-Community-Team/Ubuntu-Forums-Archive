---
title: "No matching function error in stl_error.h"
date: 2012-04-24
forum: Programming Talk
---

### Post by johnpamar on 2012-04-24
Hello,

I am very new to ubuntu and to this forum. I have Ubuntu 10.04 (lucid) and I am trying to build/make a 3rd party software (CRKit). I build and make it using:

/usr/bin/cmake -DBUILD_EXAMPLES:BOOL=OFF -DBUILD_TESTING:BOOL=OFF -DCMAKE_BUILD_TYPE:STRING=Release '-DCMAKE_CXX_FLAGS_RELEASE:STRING=-O3 -DNDEBUG' -DUSE_ITK:BOOL=ON -DUSE_VTK:BOOL=ON -DUSE_QT:BOOL=ON -DDESIRED_QT_VERSION:STRING=4 -DQT_QMAKE_EXECUTABLE:PATH=~/CRKit/crkit_build/install/qt-4.7.4/bin/qmake -DITK_DIR:PATH=~/CRKit/crkit_build/install/itk/lib/InsightToolkit -DVTK_DIR:PATH=~/CRKit/crkit_build/install/vtk/lib/vtk-5.6 -DCRKIT_INSTALL_PREFIX:PATH=~/CRKit/crkit_build/install -DCMAKE_INSTALL_PREFIX:PATH=~/CRKit/crkit_build/install ~/CRKit/crkit_build/crkit/release-1.5.2

make

During make, I receive the following error:
In file included from /usr/include/c++/4.4/vector:65,
                 from ~/CRKit/crkit_build/crkit/release-1.5.2/common/external/tclap/SwitchArg.h:28,
                 from ~/CRKit/crkit_build/crkit/release-1.5.2/common/external/tclap/CmdLine.h:26,
                 from ~/CRKit/crkit_build/crkit/release-1.5.2/tools/code/crlIdentityMeasurementFrameFullProcessing.cxx:1:
/usr/include/c++/4.4/bits/stl_vector.h: In member function ‘void std::vector<_Tp, _Alloc>::_M_initialize_dispatch(_Integer, _Integer, std::__true_type) [with _Integer = int, _Tp = std::vector<double, std::allocator<double> >, _Alloc = std::allocator<std::vector<double, std::allocator<double> > >]’:
/usr/include/c++/4.4/bits/stl_vector.h:303:   instantiated from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const _Alloc&) [with _InputIterator = int, _Tp = std::vector<double, std::allocator<double> >, _Alloc = std::allocator<std::vector<double, std::allocator<double> > >]’
~/CRKit/crkit_build/crkit/release-1.5.2/tools/code/crlIdentityMeasurementFrameFullProcessing.cxx:121:   instantiated from here
**/usr/include/c++/4.4/bits/stl_vector.h:991: error: no matching function for call to **‘std::vector<std::vector<double, std::allocator<double> >, std::allocator<std::vector<double, std::allocator<double> > > >::_M_fill_initialize(size_t, int&)’
/usr/include/c++/4.4/bits/stl_vector.h:1033: note: candidates are: void std::vector<_Tp, _Alloc>::_M_fill_initialize(size_t, const _Tp&) [with _Tp = std::vector<double, std::allocator<double> >, _Alloc = std::allocator<std::vector<double, std::allocator<double> > >]
make[2]: *** [tools/code/CMakeFiles/crlIdentityMeasurementFrameFullProcessing.dir/crlIdentityMeasurementFrameFullProcessing.cxx.o] Error 1
make[1]: *** [tools/code/CMakeFiles/crlIdentityMeasurementFrameFullProcessing.dir/all] Error 2
make[1]: *** Waiting for unfinished jobs....
Linking CXX executable crlImageAddMpyAdd
[ 57%] Built target crlImageAddMpyAdd
make: *** [all] Error 2

Looking over past threads, it seems like it might be because I have gcc-4.4 and this issue might resolve with the installation of gcc-4.1. I am not sure though. Please let me know what other information you need and what suggestions you can provide to fix this problem.

Thanks
JP

---

### Post by Zugzwang on 2012-04-24
You can try to fix the code. In "~/CRKit/crkit_build/crkit/release-1.5.2/tools/code/crlIdentityMeasurementFrameFullProcessing.cxx", line 121, there is some "int" used a parameter to some vector<double> function or its constructor that should be of type "double". Try to cast the integer to double explicitly. If this doesn't work, try to store this integer value into a new double variable and use this as replacement parameter.

---

### Post by johnpamar on 2012-04-24
Thank you for the quick reply! The line 121 in crlIdentityMeasurementFrameFullProcessing.cxx was:

std::vector<std::vector<double> > idFrame(3,3);

and I changed it to:

std::vector<std::vector<double> > idFrame((double)3,(double)3);

I, unfortunately, now get the following error:
In file included from /usr/include/c++/4.4/bits/stl_algobase.h:67,
                 from /usr/include/c++/4.4/bits/char_traits.h:41,
                 from /usr/include/c++/4.4/string:42,
                 from ~/CRKit/crkit_build/crkit/release-1.5.2/common/external/tclap/SwitchArg.h:27,
                 from ~/CRKit/crkit_build/crkit/release-1.5.2/common/external/tclap/CmdLine.h:26,
                 from ~/CRKit/crkit_build/crkit/release-1.5.2/tools/code/crlIdentityMeasurementFrameFullProcessing.cxx:1:
/usr/include/c++/4.4/bits/stl_iterator_base_types.h: In instantiation of ‘std::iterator_traits<double>’:
/usr/include/c++/4.4/bits/stl_vector.h:1001:   instantiated from ‘void std::vector<_Tp, _Alloc>::_M_initialize_dispatch(_InputIterator, _InputIterator, std::__false_type) [with _InputIterator = double, _Tp = std::vector<double, std::allocator<double> >, _Alloc = std::allocator<std::vector<double, std::allocator<double> > >]’
/usr/include/c++/4.4/bits/stl_vector.h:303:   instantiated from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const _Alloc&) [with _InputIterator = double, _Tp = std::vector<double, std::allocator<double> >, _Alloc = std::allocator<std::vector<double, std::allocator<double> > >]’
~/CRKit/crkit_build/crkit/release-1.5.2/tools/code/crlIdentityMeasurementFrameFullProcessing.cxx:122:   instantiated from here
[B]/usr/include/c++/4.4/bits/stl_iterator_base_types.h:127: error: ‘double’ is not a class, struct, or union type
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:128: error: ‘double’ is not a class, struct, or union type
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:129: error: ‘double’ is not a class, struct, or union type
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:130: error: ‘double’ is not a class, struct, or union type
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:131: error: ‘double’ is not a class, struct, or union type
[/B]make[2]: *** [tools/code/CMakeFiles/crlIdentityMeasurementFrameFullProcessing.dir/crlIdentityMeasurementFrameFullProcessing.cxx.o] Error 1
make[1]: *** [tools/code/CMakeFiles/crlIdentityMeasurementFrameFullProcessing.dir/all] Error 2
make: *** [all] Error 2

Any help would be greatly appreciated.

Sincerely,
JP

> **Zugzwang said:**
> You can try to fix the code. In "~/CRKit/crkit_build/crkit/release-1.5.2/tools/code/crlIdentityMeasurementFrameFullProcessing.cxx", line 121, there is some "int" used a parameter to some vector<double> function or its constructor that should be of type "double". Try to cast the integer to double explicitly. If this doesn't work, try to store this integer value into a new double variable and use this as replacement parameter.

---

### Post by Zugzwang on 2012-04-24
I don't know how the code "std::vector<std::vector<double> > idFrame(3,3);" was ever working. I can only guess what it was intended to do. A possible fix would be:
```
std::vector<std::vector<double> > idFrame(3,std::vector<double>(3,0.0));

``` This one compiles at least and creates a 3x3 matrix with "0.0" elements. Note that only the last initialization element is of type double, the others are sizes.

---

