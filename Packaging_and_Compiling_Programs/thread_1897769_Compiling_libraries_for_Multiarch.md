---
title: "Compiling libraries for Multiarch?"
date: 2011-12-19
forum: Packaging and Compiling Programs
---

### Post by nerdopolis on 2011-12-19
Hi. 

I am trying to compile Wayland and its dependencies on Ubuntu Precise. I install all the dependent build packages that the software requires. 

 The problem I am having is that I seem to be running into problems with Multiarch, where the libraries are being built to /usr/lib, but seem to be trying to compile it against the version in /usr/lib/i386-linux-gnu.

```
apt-get install build-essential libtool libxi-dev libxmu-dev libxt-dev bison flex libgl1-mesa-dev xutils-dev libtalloc-dev libdrm-dev autoconf x11proto-kb-dev libegl1-mesa-dev libgles2-mesa-dev libgdk-pixbuf2.0-dev libudev-dev libxcb-dri2-0-dev libxcb-xfixes0-dev shtool libffi-dev libpoppler-glib-dev libgtk2.0-dev git diffstat libx11-xcb-dev quilt autopoint dh-autoreconf xkb-data gtk-doc-tools gobject-introspection gperf librsvg2-bin libpciaccess-dev kubuntu-desktop python-libxml2 libjpeg-dev   libgbm-dev libjpeg-turbo62     libjpeg-turbo-progs    
export WLD=/usr
LD_LIBRARY_PATH=$WLD/lib
PKG_CONFIG_PATH=$WLD/lib/pkgconfig/:$WLD/share/pkgconfig/
ACLOCAL="aclocal -I $WLD/share/aclocal"
C_INCLUDE_PATH=$WLD/include
LIBRARY_PATH=$WLD/lib
PKG_CONFIG_ALLOW_SYSTEM_CFLAGS=1

export WLD LD_LIBRARY_PATH PKG_CONFIG_PATH ACLOCAL C_INCLUDE_PATH \
       LIBRARY_PATH PKG_CONFIG_ALLOW_SYSTEM_CFLAGS

git clone git://anongit.freedesktop.org/wayland/wayland
cd wayland
./autogen.sh --prefix=$WLD
make
make install
cd ..


git clone git://anongit.freedesktop.org/git/mesa/drm
cd drm
./autogen.sh --prefix=$WLD --enable-nouveau-experimental-api
make
make install
cd ..

git clone git://anongit.freedesktop.org/git/xorg/util/macros
cd macros
./autogen.sh --prefix=$WLD
make
make install
cd ..

git clone git://anongit.freedesktop.org/xorg/proto/glproto
cd glproto
./autogen.sh --prefix=$WLD
make
make install
cd ..

git clone git://anongit.freedesktop.org/xorg/proto/dri2proto
cd dri2proto
./autogen.sh --prefix=$WLD
make
make install
cd ..


git clone git://anongit.freedesktop.org/mesa/mesa
cd mesa
./autogen.sh --prefix=$WLD --enable-gles2  --enable-shared-glapi --enable-gbm --with-gallium-drivers=  --with-egl-platforms=wayland,drm
make
make install
cd ..

git clone git://anongit.freedesktop.org/xorg/proto/xproto
cd xproto
./autogen.sh --prefix=$WLD
make 
make install
cd ..

git clone git://anongit.freedesktop.org/xorg/proto/kbproto
cd kbproto
./autogen.sh --prefix=$WLD
make 
make install
cd ..

git clone git://anongit.freedesktop.org/xorg/lib/libX11
cd libX11
./autogen.sh --prefix=$WLD
make 
make install
cd ..

git clone git://people.freedesktop.org/xorg/lib/libxkbcommon.git
cd libxkbcommon/
./autogen.sh --prefix=$WLD --with-xkb-config-root=/usr/share/X11/xkb
make
make install
cd ..

git clone git://anongit.freedesktop.org/pixman
cd pixman
./autogen.sh --prefix=$WLD
make 
make install
cd ..

git clone git://anongit.freedesktop.org/cairo
cd cairo
./autogen.sh --prefix=$WLD --enable-gl --enable-xcb
make 
make install
cd ..


git clone git://anongit.freedesktop.org/wayland/wayland-demos
cd wayland-demos
./autogen.sh --prefix=$WLD
make
make install
cd ..

```Is there an extra argument or flag or variable I need to provide for Ubuntu's multiarch? 

Thanks.

---

### Post by MadCow108 on 2011-12-20
adding --libdir=$PREFIX/lib/$(dpkg-architecture -qDEB_HOST_MULTIARCH) to the configure/autogen lines should place the packages in the multarch path.

Its probably not a good idea to place the results in /usr it might break your system.
you should put them in a different prefix and set LD_RUN_PATH for the compiler and LD_LIBRARY_PATH or ld.so.conf appropriatly.

---

### Post by nerdopolis on 2011-12-23
Thanks! That actually seems to have got me MUCH further! Except now its not running because everything OpenGL related returns ```
undefined symbol: _glapi_tls_Dispatch
```, but I don't think thats related to multiarch anymore.

And as for breaking my system, I am experimenting on a debootstrap/chroot...

---

