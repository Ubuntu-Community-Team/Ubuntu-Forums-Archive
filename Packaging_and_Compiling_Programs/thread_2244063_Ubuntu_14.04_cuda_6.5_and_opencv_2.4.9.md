---
title: "Ubuntu 14.04 cuda 6.5 and opencv 2.4.9"
date: 2014-09-13
forum: Packaging and Compiling Programs
---

### Post by erotavlas on 2014-09-13
Hi,

I have a trouble on installing opencv 2.4.9 on a system with Ubuntu 14.04 64 bit and cuda 6.5. I installed the cuda package by downloading it from cuda zone [https://developer.nvidia.com/cuda-downloads#linux](https://developer.nvidia.com/cuda-downloads#linux) and by adding package as dpkg -i cuda-repo-ubuntu1404_6.5-14_amd64.deb. Then I installed cuda as normal package. After this, I continued by installing opencv as specified here [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV) with same modifications on configuration parameters.
```

version="$(wget -q -O - http://sourceforge.net/projects/opencvlibrary/files/opencv-unix | egrep -m1 -o '\"[0-9](\.[0-9])+' | cut -c2-)"
downloadfilelist="opencv-$version.tar.gz opencv-$version.zip"
downloadfile=
for file in $downloadfilelist;
do
        wget --spider http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$version/$file/download
        if [ $? -eq 0 ]; then
                downloadfile=$file
        fi
done
if [ -z "$downloadfile" ]; then
        echo "Could not find download file on sourceforge page. Please find the download file for version $version at"
        echo "http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$version/ and update this script"
        exit 1
fi
echo "Installing OpenCV ${version}, ffmpeg and zlib"
mkdir OpenCV
cd OpenCV
echo "Removing any pre-installed ffmpeg and x264"
sudo apt-get remove ffmpeg x264 libx264-dev
echo "Installing Dependenices ffmpeg, codecs and zlib"

if [ $(cat /etc/*-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f2) == 'trusty' ]; then
sudo add-apt-repository 'deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main' && sudo add-apt-repository 'deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu saucy main' && sudo apt-get update
fi

sudo apt-get install libopencv-dev build-essential checkinstall cmake pkg-config yasm libtiff4-dev libjpeg-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev libxine-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libv4l-dev python-dev python-numpy libtbb-dev libqt4-dev libgtk2.0-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils ffmpeg unzip zlib1g-dev
echo "Downloading OpenCV" $version
wget -O $downloadfile http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$version/$downloadfile/download
echo "Installing OpenCV" $version
echo $downloadfile | grep ".zip"
if [ $? -eq 0 ]; then
        unzip $downloadfile
else
        tar -xvf $downloadfile
fi
cd opencv-$version
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_SHARED_LIBS=ON -D WITH_TBB=ON -D WITH_OPENMP=ON -D WITH_OPENCL=ON -D WITH_CUDA=ON -D WITH_GTK=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D BUILD_EXAMPLES=OFF -D WITH_QT=ON -D WITH_OPENGL=ON -D BUILD_JPEG=ON -D BUILD_PNG=ON -D BUILD_JASPER=ON -D BUILD_ZLIB=ON -D WITH_JPEG=ON -D WITH_PNG=ON -D WITH_JASPER=ON -D WITH_ZLIB=ON -D WITH_OPENEXR=OFF ..
make -j 2
sudo make install
sudo sh -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf'
sudo ldconfig
echo "OpenCV" $version "ready to be used"

```
During compilation I receive the following errors. I cannot figure out where is the source of the problems. Indeed, the same configuration with cuda 6.0 works perfectly.
```

Linking CXX executable ../../bin/opencv_test_photo
[ 75%] Building NVCC (Device) object modules/gpu/CMakeFiles/cuda_compile.dir/src/nvidia/core/./cuda_compile_generated_NCVPyramid.cu.o
nvcc warning : The 'compute_11', 'compute_12', 'compute_13', 'sm_11', 'sm_12', and 'sm_13' architectures are deprecated, and may be removed in a future release.
[ 75%] Built target opencv_test_photo
[ 75%] Building NVCC (Device) object modules/gpu/CMakeFiles/cuda_compile.dir/src/nvidia/NPP_staging/./cuda_compile_generated_NPP_staging.cu.o
nvcc warning : The 'compute_11', 'compute_12', 'compute_13', 'sm_11', 'sm_12', and 'sm_13' architectures are deprecated, and may be removed in a future release.
nvcc warning : The 'compute_11', 'compute_12', 'compute_13', 'sm_11', 'sm_12', and 'sm_13' architectures are deprecated, and may be removed in a future release.
nvcc warning : The 'compute_11', 'compute_12', 'compute_13', 'sm_11', 'sm_12', and 'sm_13' architectures are deprecated, and may be removed in a future release.
/home/userOpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(51): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(52): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(53): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(54): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(55): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(56): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(57): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(58): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(61): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(62): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(63): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(64): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(65): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(66): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(67): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(68): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(119): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(120): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(121): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(122): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(123): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(124): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(125): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(126): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(127): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(128): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(129): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(130): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(131): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(132): error: a storage class is not allowed in an explicit specialization

/home/user/OpenCV/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(133): error: a storage class is not allowed in an explicit specialization

31 errors detected in the compilation of "/tmp/tmpxft_0000069a_00000000-21_NCVPyramid.compute_35.cpp1.ii".
CMake Error at cuda_compile_generated_NCVPyramid.cu.o.cmake:266 (message):
  Error generating file
  /home/user/OpenCV/opencv-2.4.9/build/modules/gpu/CMakeFiles/cuda_compile.dir/src/nvidia/core/./cuda_compile_generated_NCVPyramid.cu.o


make[2]: *** [modules/gpu/CMakeFiles/cuda_compile.dir/src/nvidia/core/./cuda_compile_generated_NCVPyramid.cu.o] Error 1
make[2]: *** Waiting for unfinished jobs....
Linking CXX shared library ../../lib/libopencv_ocl.so
[ 78%] Built target opencv_ocl
[ 78%] Built target opencv_haartraining_engine
Linking CXX executable ../../bin/opencv_test_legacy
[ 78%] Built target opencv_test_legacy
Linking CXX executable ../../bin/opencv_perf_ocl
[ 78%] Built target opencv_perf_ocl
Linking CXX executable ../../bin/opencv_test_ocl
[ 82%] Built target opencv_test_ocl
Linking CXX executable ../../bin/opencv_createsamples
[ 82%] Built target opencv_createsamples
Linking CXX executable ../../bin/opencv_haartraining
[ 82%] Built target opencv_haartraining
Linking CXX executable ../../bin/opencv_performance
[ 82%] Built target opencv_performance
Linking CXX executable ../../bin/opencv_traincascade
[ 82%] Built target opencv_traincascade
make[1]: *** [modules/gpu/CMakeFiles/opencv_gpu.dir/all] Error 2

```
It seems that opencv has some problem with cuda 6.5. The only way to compile opencv is to disable cuda support or to come back to previous cuda 6.0
Any suggestions?
Thank you in advance

P.S.

I found that it is a bug [http://code.opencv.org/issues/3814](http://code.opencv.org/issues/3814). So what can I do?

---

### Post by erotavlas on 2014-09-14
I solved by modifying the source code of the file NCVPixelOperations.hpp In particular, I removed the static keyword from each template function declaration.

```

/*M///////////////////////////////////////////////////////////////////////////////////////
//
//  IMPORTANT: READ BEFORE DOWNLOADING, COPYING, INSTALLING OR USING.
//
//  By downloading, copying, installing or using the software you agree to this license.
//  If you do not agree to this license, do not download, install,
//  copy or use the software.
//
//
//                           License Agreement
//                For Open Source Computer Vision Library
//
// Copyright (C) 2000-2008, Intel Corporation, all rights reserved.
// Copyright (C) 2009, Willow Garage Inc., all rights reserved.
// Third party copyrights are property of their respective owners.
//
// Redistribution and use in source and binary forms, with or without modification,
// are permitted provided that the following conditions are met:
//
//   * Redistribution's of source code must retain the above copyright notice,
//     this list of conditions and the following disclaimer.
//
//   * Redistribution's in binary form must reproduce the above copyright notice,
//     this list of conditions and the following disclaimer in the documentation
//     and/or other materials provided with the distribution.
//
//   * The name of the copyright holders may not be used to endorse or promote products
//     derived from this software without specific prior written permission.
//
// This software is provided by the copyright holders and contributors "as is" and
// any express or implied warranties, including, but not limited to, the implied
// warranties of merchantability and fitness for a particular purpose are disclaimed.
// In no event shall the Intel Corporation or contributors be liable for any direct,
// indirect, incidental, special, exemplary, or consequential damages
// (including, but not limited to, procurement of substitute goods or services;
// loss of use, data, or profits; or business interruption) however caused
// and on any theory of liability, whether in contract, strict liability,
// or tort (including negligence or otherwise) arising in any way out of
// the use of this software, even if advised of the possibility of such damage.
//
//M*/

#ifndef _ncv_pixel_operations_hpp_
#define _ncv_pixel_operations_hpp_

#include <limits.h>
#include <float.h>
#include "NCV.hpp"

template<typename TBase> inline __host__ __device__ TBase _pixMaxVal();
template<> {static} inline __host__ __device__ Ncv8u  _pixMaxVal<Ncv8u>()  {return UCHAR_MAX;}
template<> {static} inline __host__ __device__ Ncv16u _pixMaxVal<Ncv16u>() {return USHRT_MAX;}
template<> {static} inline __host__ __device__ Ncv32u _pixMaxVal<Ncv32u>() {return  UINT_MAX;}
template<> {static} inline __host__ __device__ Ncv8s  _pixMaxVal<Ncv8s>()  {return  SCHAR_MAX;}
template<> {static} inline __host__ __device__ Ncv16s _pixMaxVal<Ncv16s>() {return  SHRT_MAX;}
template<> {static} inline __host__ __device__ Ncv32s _pixMaxVal<Ncv32s>() {return   INT_MAX;}
template<> {static} inline __host__ __device__ Ncv32f _pixMaxVal<Ncv32f>() {return   FLT_MAX;}
template<> {static} inline __host__ __device__ Ncv64f _pixMaxVal<Ncv64f>() {return   DBL_MAX;}

template<typename TBase> inline __host__ __device__ TBase _pixMinVal();
template<>  {static} inline __host__ __device__ Ncv8u  _pixMinVal<Ncv8u>()  {return 0;}
template<>  {static} inline __host__ __device__ Ncv16u _pixMinVal<Ncv16u>() {return 0;}
template<>  {static} inline __host__ __device__ Ncv32u _pixMinVal<Ncv32u>() {return 0;}
template<>  {static} inline __host__ __device__ Ncv8s  _pixMinVal<Ncv8s>()  {return SCHAR_MIN;}
template<>  {static} inline __host__ __device__ Ncv16s _pixMinVal<Ncv16s>() {return SHRT_MIN;}
template<>  {static} inline __host__ __device__ Ncv32s _pixMinVal<Ncv32s>() {return INT_MIN;}
template<>  {static} inline __host__ __device__ Ncv32f _pixMinVal<Ncv32f>() {return FLT_MIN;}
template<>  {static} inline __host__ __device__ Ncv64f _pixMinVal<Ncv64f>() {return DBL_MIN;}

template<typename Tvec> struct TConvVec2Base;
template<> struct TConvVec2Base<uchar1>  {typedef Ncv8u TBase;};
template<> struct TConvVec2Base<uchar3>  {typedef Ncv8u TBase;};
template<> struct TConvVec2Base<uchar4>  {typedef Ncv8u TBase;};
template<> struct TConvVec2Base<ushort1> {typedef Ncv16u TBase;};
template<> struct TConvVec2Base<ushort3> {typedef Ncv16u TBase;};
template<> struct TConvVec2Base<ushort4> {typedef Ncv16u TBase;};
template<> struct TConvVec2Base<uint1>   {typedef Ncv32u TBase;};
template<> struct TConvVec2Base<uint3>   {typedef Ncv32u TBase;};
template<> struct TConvVec2Base<uint4>   {typedef Ncv32u TBase;};
template<> struct TConvVec2Base<float1>  {typedef Ncv32f TBase;};
template<> struct TConvVec2Base<float3>  {typedef Ncv32f TBase;};
template<> struct TConvVec2Base<float4>  {typedef Ncv32f TBase;};
template<> struct TConvVec2Base<double1> {typedef Ncv64f TBase;};
template<> struct TConvVec2Base<double3> {typedef Ncv64f TBase;};
template<> struct TConvVec2Base<double4> {typedef Ncv64f TBase;};

#define NC(T)       (sizeof(T) / sizeof(TConvVec2Base<T>::TBase))

template<typename TBase, Ncv32u NC> struct TConvBase2Vec;
template<> struct TConvBase2Vec<Ncv8u, 1>  {typedef uchar1 TVec;};
template<> struct TConvBase2Vec<Ncv8u, 3>  {typedef uchar3 TVec;};
template<> struct TConvBase2Vec<Ncv8u, 4>  {typedef uchar4 TVec;};
template<> struct TConvBase2Vec<Ncv16u, 1> {typedef ushort1 TVec;};
template<> struct TConvBase2Vec<Ncv16u, 3> {typedef ushort3 TVec;};
template<> struct TConvBase2Vec<Ncv16u, 4> {typedef ushort4 TVec;};
template<> struct TConvBase2Vec<Ncv32u, 1> {typedef uint1 TVec;};
template<> struct TConvBase2Vec<Ncv32u, 3> {typedef uint3 TVec;};
template<> struct TConvBase2Vec<Ncv32u, 4> {typedef uint4 TVec;};
template<> struct TConvBase2Vec<Ncv32f, 1> {typedef float1 TVec;};
template<> struct TConvBase2Vec<Ncv32f, 3> {typedef float3 TVec;};
template<> struct TConvBase2Vec<Ncv32f, 4> {typedef float4 TVec;};
template<> struct TConvBase2Vec<Ncv64f, 1> {typedef double1 TVec;};
template<> struct TConvBase2Vec<Ncv64f, 3> {typedef double3 TVec;};
template<> struct TConvBase2Vec<Ncv64f, 4> {typedef double4 TVec;};

//TODO: consider using CUDA intrinsics to avoid branching
template<typename Tin> static inline __host__ __device__ void _TDemoteClampZ(Tin &a, Ncv8u &out) {out = (Ncv8u)CLAMP_0_255(a);};
template<typename Tin> static inline __host__ __device__ void _TDemoteClampZ(Tin &a, Ncv16u &out) {out = (Ncv16u)CLAMP(a, 0, USHRT_MAX);}
template<typename Tin> static inline __host__ __device__ void _TDemoteClampZ(Tin &a, Ncv32u &out) {out = (Ncv32u)CLAMP(a, 0, UINT_MAX);}
template<typename Tin> static inline __host__ __device__ void _TDemoteClampZ(Tin &a, Ncv32f &out) {out = (Ncv32f)a;}

//TODO: consider using CUDA intrinsics to avoid branching
template<typename Tin> static inline __host__ __device__ void _TDemoteClampNN(Tin &a, Ncv8u &out) {out = (Ncv8u)CLAMP_0_255(a+0.5f);}
template<typename Tin> static inline __host__ __device__ void _TDemoteClampNN(Tin &a, Ncv16u &out) {out = (Ncv16u)CLAMP(a+0.5f, 0, USHRT_MAX);}
template<typename Tin> static inline __host__ __device__ void _TDemoteClampNN(Tin &a, Ncv32u &out) {out = (Ncv32u)CLAMP(a+0.5f, 0, UINT_MAX);}
template<typename Tin> static inline __host__ __device__ void _TDemoteClampNN(Tin &a, Ncv32f &out) {out = (Ncv32f)a;}

template<typename Tout> inline Tout _pixMakeZero();
template<>  {static} inline __host__ __device__ uchar1 _pixMakeZero<uchar1>() {return make_uchar1(0);}
template<>  {static} inline __host__ __device__ uchar3 _pixMakeZero<uchar3>() {return make_uchar3(0,0,0);}
template<>  {static} inline __host__ __device__ uchar4 _pixMakeZero<uchar4>() {return make_uchar4(0,0,0,0);}
template<>  {static} inline __host__ __device__ ushort1 _pixMakeZero<ushort1>() {return make_ushort1(0);}
template<>  {static} inline __host__ __device__ ushort3 _pixMakeZero<ushort3>() {return make_ushort3(0,0,0);}
template<>  {static} inline __host__ __device__ ushort4 _pixMakeZero<ushort4>() {return make_ushort4(0,0,0,0);}
template<>  {static} inline __host__ __device__ uint1 _pixMakeZero<uint1>() {return make_uint1(0);}
template<>  {static} inline __host__ __device__ uint3 _pixMakeZero<uint3>() {return make_uint3(0,0,0);}
template<>  {static} inline __host__ __device__ uint4 _pixMakeZero<uint4>() {return make_uint4(0,0,0,0);}
template<>  {static} inline __host__ __device__ float1 _pixMakeZero<float1>() {return make_float1(0.f);}
template<>  {static} inline __host__ __device__ float3 _pixMakeZero<float3>() {return make_float3(0.f,0.f,0.f);}
template<>  {static} inline __host__ __device__ float4 _pixMakeZero<float4>() {return make_float4(0.f,0.f,0.f,0.f);}
template<>  {static} inline __host__ __device__ double1 _pixMakeZero<double1>() {return make_double1(0.);}
template<>  {static} inline __host__ __device__ double3 _pixMakeZero<double3>() {return make_double3(0.,0.,0.);}
template<>  {static} inline __host__ __device__ double4 _pixMakeZero<double4>() {return make_double4(0.,0.,0.,0.);}

static inline __host__ __device__ uchar1 _pixMake(Ncv8u x) {return make_uchar1(x);}
static inline __host__ __device__ uchar3 _pixMake(Ncv8u x, Ncv8u y, Ncv8u z) {return make_uchar3(x,y,z);}
static inline __host__ __device__ uchar4 _pixMake(Ncv8u x, Ncv8u y, Ncv8u z, Ncv8u w) {return make_uchar4(x,y,z,w);}
static inline __host__ __device__ ushort1 _pixMake(Ncv16u x) {return make_ushort1(x);}
static inline __host__ __device__ ushort3 _pixMake(Ncv16u x, Ncv16u y, Ncv16u z) {return make_ushort3(x,y,z);}
static inline __host__ __device__ ushort4 _pixMake(Ncv16u x, Ncv16u y, Ncv16u z, Ncv16u w) {return make_ushort4(x,y,z,w);}
static inline __host__ __device__ uint1 _pixMake(Ncv32u x) {return make_uint1(x);}
static inline __host__ __device__ uint3 _pixMake(Ncv32u x, Ncv32u y, Ncv32u z) {return make_uint3(x,y,z);}
static inline __host__ __device__ uint4 _pixMake(Ncv32u x, Ncv32u y, Ncv32u z, Ncv32u w) {return make_uint4(x,y,z,w);}
static inline __host__ __device__ float1 _pixMake(Ncv32f x) {return make_float1(x);}
static inline __host__ __device__ float3 _pixMake(Ncv32f x, Ncv32f y, Ncv32f z) {return make_float3(x,y,z);}
static inline __host__ __device__ float4 _pixMake(Ncv32f x, Ncv32f y, Ncv32f z, Ncv32f w) {return make_float4(x,y,z,w);}
static inline __host__ __device__ double1 _pixMake(Ncv64f x) {return make_double1(x);}
static inline __host__ __device__ double3 _pixMake(Ncv64f x, Ncv64f y, Ncv64f z) {return make_double3(x,y,z);}
static inline __host__ __device__ double4 _pixMake(Ncv64f x, Ncv64f y, Ncv64f z, Ncv64f w) {return make_double4(x,y,z,w);}


template<typename Tin, typename Tout, Ncv32u CN> struct __pixDemoteClampZ_CN {static __host__ __device__ Tout _pixDemoteClampZ_CN(Tin &pix);};

template<typename Tin, typename Tout> struct __pixDemoteClampZ_CN<Tin, Tout, 1> {
static __host__ __device__ Tout _pixDemoteClampZ_CN(Tin &pix)
{
    Tout out;
    _TDemoteClampZ(pix.x, out.x);
    return out;
}};

template<typename Tin, typename Tout> struct __pixDemoteClampZ_CN<Tin, Tout, 3> {
static __host__ __device__ Tout _pixDemoteClampZ_CN(Tin &pix)
{
    Tout out;
    _TDemoteClampZ(pix.x, out.x);
    _TDemoteClampZ(pix.y, out.y);
    _TDemoteClampZ(pix.z, out.z);
    return out;
}};

template<typename Tin, typename Tout> struct __pixDemoteClampZ_CN<Tin, Tout, 4> {
static __host__ __device__ Tout _pixDemoteClampZ_CN(Tin &pix)
{
    Tout out;
    _TDemoteClampZ(pix.x, out.x);
    _TDemoteClampZ(pix.y, out.y);
    _TDemoteClampZ(pix.z, out.z);
    _TDemoteClampZ(pix.w, out.w);
    return out;
}};

template<typename Tin, typename Tout> static inline __host__ __device__ Tout _pixDemoteClampZ(Tin &pix)
{
    return __pixDemoteClampZ_CN<Tin, Tout, NC(Tin)>::_pixDemoteClampZ_CN(pix);
}


template<typename Tin, typename Tout, Ncv32u CN> struct __pixDemoteClampNN_CN {static __host__ __device__ Tout _pixDemoteClampNN_CN(Tin &pix);};

template<typename Tin, typename Tout> struct __pixDemoteClampNN_CN<Tin, Tout, 1> {
static __host__ __device__ Tout _pixDemoteClampNN_CN(Tin &pix)
{
    Tout out;
    _TDemoteClampNN(pix.x, out.x);
    return out;
}};

template<typename Tin, typename Tout> struct __pixDemoteClampNN_CN<Tin, Tout, 3> {
static __host__ __device__ Tout _pixDemoteClampNN_CN(Tin &pix)
{
    Tout out;
    _TDemoteClampNN(pix.x, out.x);
    _TDemoteClampNN(pix.y, out.y);
    _TDemoteClampNN(pix.z, out.z);
    return out;
}};

template<typename Tin, typename Tout> struct __pixDemoteClampNN_CN<Tin, Tout, 4> {
static __host__ __device__ Tout _pixDemoteClampNN_CN(Tin &pix)
{
    Tout out;
    _TDemoteClampNN(pix.x, out.x);
    _TDemoteClampNN(pix.y, out.y);
    _TDemoteClampNN(pix.z, out.z);
    _TDemoteClampNN(pix.w, out.w);
    return out;
}};

template<typename Tin, typename Tout> static inline __host__ __device__ Tout _pixDemoteClampNN(Tin &pix)
{
    return __pixDemoteClampNN_CN<Tin, Tout, NC(Tin)>::_pixDemoteClampNN_CN(pix);
}


template<typename Tin, typename Tout, typename Tw, Ncv32u CN> struct __pixScale_CN {static __host__ __device__ Tout _pixScale_CN(Tin &pix, Tw w);};

template<typename Tin, typename Tout, typename Tw> struct __pixScale_CN<Tin, Tout, Tw, 1> {
static __host__ __device__ Tout _pixScale_CN(Tin &pix, Tw w)
{
    Tout out;
    typedef typename TConvVec2Base<Tout>::TBase TBout;
    out.x = (TBout)(pix.x * w);
    return out;
}};

template<typename Tin, typename Tout, typename Tw> struct __pixScale_CN<Tin, Tout, Tw, 3> {
static __host__ __device__ Tout _pixScale_CN(Tin &pix, Tw w)
{
    Tout out;
    typedef typename TConvVec2Base<Tout>::TBase TBout;
    out.x = (TBout)(pix.x * w);
    out.y = (TBout)(pix.y * w);
    out.z = (TBout)(pix.z * w);
    return out;
}};

template<typename Tin, typename Tout, typename Tw> struct __pixScale_CN<Tin, Tout, Tw, 4> {
static __host__ __device__ Tout _pixScale_CN(Tin &pix, Tw w)
{
    Tout out;
    typedef typename TConvVec2Base<Tout>::TBase TBout;
    out.x = (TBout)(pix.x * w);
    out.y = (TBout)(pix.y * w);
    out.z = (TBout)(pix.z * w);
    out.w = (TBout)(pix.w * w);
    return out;
}};

template<typename Tin, typename Tout, typename Tw> static __host__ __device__ Tout _pixScale(Tin &pix, Tw w)
{
    return __pixScale_CN<Tin, Tout, Tw, NC(Tin)>::_pixScale_CN(pix, w);
}


template<typename Tin, typename Tout, Ncv32u CN> struct __pixAdd_CN {static __host__ __device__ Tout _pixAdd_CN(Tout &pix1, Tin &pix2);};

template<typename Tin, typename Tout> struct __pixAdd_CN<Tin, Tout, 1> {
static __host__ __device__ Tout _pixAdd_CN(Tout &pix1, Tin &pix2)
{
    Tout out;
    out.x = pix1.x + pix2.x;
    return out;
}};

template<typename Tin, typename Tout> struct __pixAdd_CN<Tin, Tout, 3> {
static __host__ __device__ Tout _pixAdd_CN(Tout &pix1, Tin &pix2)
{
    Tout out;
    out.x = pix1.x + pix2.x;
    out.y = pix1.y + pix2.y;
    out.z = pix1.z + pix2.z;
    return out;
}};

template<typename Tin, typename Tout> struct __pixAdd_CN<Tin, Tout, 4> {
static __host__ __device__ Tout _pixAdd_CN(Tout &pix1, Tin &pix2)
{
    Tout out;
    out.x = pix1.x + pix2.x;
    out.y = pix1.y + pix2.y;
    out.z = pix1.z + pix2.z;
    out.w = pix1.w + pix2.w;
    return out;
}};

template<typename Tin, typename Tout> static __host__ __device__ Tout _pixAdd(Tout &pix1, Tin &pix2)
{
    return __pixAdd_CN<Tin, Tout, NC(Tin)>::_pixAdd_CN(pix1, pix2);
}


template<typename Tin, typename Tout, Ncv32u CN> struct __pixDist_CN {static __host__ __device__ Tout _pixDist_CN(Tin &pix1, Tin &pix2);};

template<typename Tin, typename Tout> struct __pixDist_CN<Tin, Tout, 1> {
static __host__ __device__ Tout _pixDist_CN(Tin &pix1, Tin &pix2)
{
    return Tout(SQR(pix1.x - pix2.x));
}};

template<typename Tin, typename Tout> struct __pixDist_CN<Tin, Tout, 3> {
static __host__ __device__ Tout _pixDist_CN(Tin &pix1, Tin &pix2)
{
    return Tout(SQR(pix1.x - pix2.x) + SQR(pix1.y - pix2.y) + SQR(pix1.z - pix2.z));
}};

template<typename Tin, typename Tout> struct __pixDist_CN<Tin, Tout, 4> {
static __host__ __device__ Tout _pixDist_CN(Tin &pix1, Tin &pix2)
{
    return Tout(SQR(pix1.x - pix2.x) + SQR(pix1.y - pix2.y) + SQR(pix1.z - pix2.z) + SQR(pix1.w - pix2.w));
}};

template<typename Tin, typename Tout> static __host__ __device__ Tout _pixDist(Tin &pix1, Tin &pix2)
{
    return __pixDist_CN<Tin, Tout, NC(Tin)>::_pixDist_CN(pix1, pix2);
}


template <typename T> struct TAccPixWeighted;
template<> struct TAccPixWeighted<uchar1> {typedef double1 type;};
template<> struct TAccPixWeighted<uchar3> {typedef double3 type;};
template<> struct TAccPixWeighted<uchar4> {typedef double4 type;};
template<> struct TAccPixWeighted<ushort1> {typedef double1 type;};
template<> struct TAccPixWeighted<ushort3> {typedef double3 type;};
template<> struct TAccPixWeighted<ushort4> {typedef double4 type;};
template<> struct TAccPixWeighted<float1> {typedef double1 type;};
template<> struct TAccPixWeighted<float3> {typedef double3 type;};
template<> struct TAccPixWeighted<float4> {typedef double4 type;};

template<typename Tfrom> struct TAccPixDist {};
template<> struct TAccPixDist<uchar1> {typedef Ncv32u type;};
template<> struct TAccPixDist<uchar3> {typedef Ncv32u type;};
template<> struct TAccPixDist<uchar4> {typedef Ncv32u type;};
template<> struct TAccPixDist<ushort1> {typedef Ncv32u type;};
template<> struct TAccPixDist<ushort3> {typedef Ncv32u type;};
template<> struct TAccPixDist<ushort4> {typedef Ncv32u type;};
template<> struct TAccPixDist<float1> {typedef Ncv32f type;};
template<> struct TAccPixDist<float3> {typedef Ncv32f type;};
template<> struct TAccPixDist<float4> {typedef Ncv32f type;};

#endif //_ncv_pixel_operations_hpp_

```

---

