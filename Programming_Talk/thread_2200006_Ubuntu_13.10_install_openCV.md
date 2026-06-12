---
title: "Ubuntu 13.10 install openCV"
date: 2014-01-17
forum: Programming Talk
---

### Post by erotavlas on 2014-01-17
Hi,

I have a trouble on installing openCV on Ubuntu 13.10 64 bit. I have followed this guide [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV). Even if it is little bit old, since that the maintainer of openCV has changed the name of the package, I'm able to use it to install openCV on Ubuntu 12.04 64 bit. The latest version of Ubuntu fails to install the part of dependencies echo "Installing Dependencies". Where is the problem?

This is the update script
```

version="$(wget -q -O - [http://sourceforge.net/projects/opencvlibrary/files/opencv-unix](http://sourceforge.net/projects/opencvlibrary/files/opencv-unix) | egrep -m1 -o '\"[0-9](\.[0-9])+' | cut -c2-)"
echo "Installing OpenCV" $version
mkdir OpenCV
cd OpenCV
echo "Removing any pre-installed ffmpeg and x264"
sudo apt-get -qq remove ffmpeg x264 libx264-dev
echo "Installing Dependencies"
sudo apt-get -qq install libopencv-dev build-essential checkinstall cmake pkg-config yasm libtiff4-dev libjpeg-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev libxine-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libv4l-dev python-dev python-numpy libtbb-dev libqt4-dev libgtk2.0-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils ffmpeg
echo "Downloading OpenCV" $version
wget -O OpenCV-$version.zip http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$version/opencv-"$version".zip/download
echo "Installing OpenCV" $version
unzip OpenCV-$version.zip
cd opencv-$version
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON -D INSTALL_C_EXAMPLES=ON -D INSTALL_PYTHON_EXAMPLES=ON -D BUILD_EXAMPLES=ON -D WITH_QT=ON -D WITH_OPENGL=ON ..
make -j2
sudo make install
sudo sh -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf'
sudo ldconfig
echo "OpenCV" $version "ready to be used"

```

Thank you

P.S.
By removing the options -bb I get this
```

The following packages have unmet dependencies:
 libopencv-dev : Depends: libopencv-objdetect-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libopencv-highgui-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libopencv-legacy-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libopencv-contrib-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libopencv-videostab-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libopencv-ocl-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libcv-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libhighgui-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
                 Depends: libcvaux-dev (= 2.4.5+dfsg-0ubuntu4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
What do I need to do? If I pass also the arguments libopencv-objdetect-dev and the others, it starts a chain of dependencies.

---

