---
title: "Vlc 1.2 fail to build  on ubuntu lucid &quot;10.04 LTS&quot;"
date: 2011-03-23
forum: Packaging and Compiling Programs
---

### Post by CMatomic on 2011-03-23
I'm trying to compile a new version of VLC but got an error
[http://launchpadlibrarian.net/67052027/buildlog_ubuntu-lucid-amd64.vlc_1.2%2Bgit20110322~ppa1_FAILEDTOBUILD.txt.gz](http://launchpadlibrarian.net/67052027/buildlog_ubuntu-lucid-amd64.vlc_1.2%2Bgit20110322~ppa1_FAILEDTOBUILD.txt.gz)
```
  debian/rules override_dh_install
make[1]: Entering directory `/tmp/buildd/vlc-1.2+git20110322~ppa1'
cp debian/vlc-nox.install debian/vlc-nox.install.bak
for dir in sse2 3dnow altivec arm_neon mmx mmxext ; do \
	        if test -d debian/tmp/usr/lib/vlc/plugins/${dir}; then \
	                echo usr/lib/vlc/plugins/${dir} >> debian/vlc-nox.install ; \
	        fi ; \
	done
# Remove some modules on non-linux arch
sed -e '/\(lib\|libaccess_\)\(alsa\|atmo\|dc1394\|dv\|dvb\|fb\|v4l\|v4l2\|pvr\|udev\)_/d' \
	 debian/vlc-nox.install > debian/vlc-nox.install.kfreebsd
sed -e '/\(lib\|libaccess_\)\(probe_hal\)_/d' \
	 debian/vlc-nox.install.kfreebsd > debian/vlc-nox.install.hurd
cp tmp/libvlc.a debian/tmp/usr/lib
cp tmp/libvlccore.a debian/tmp/usr/lib
# Clean up libtool crap
find debian/tmp -name '*.la' -exec rm '{}' ';'
# Remove useless stuff
ln -sf /usr/share/fonts/truetype/freefont/FreeSans.ttf debian/tmp/usr/share/vlc/skins2/fonts/FreeSans.ttf
ln -sf /usr/share/fonts/truetype/freefont/FreeMonoBold.ttf debian/tmp/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
rm -f debian/tmp/usr/share/man/man1/vlc-config.1
# Install stuff
dh_install --fail-missing
cp: cannot stat `debian/tmp/usr/lib/mozilla': No such file or directory
dh_install: cp -a debian/tmp/usr/lib/mozilla debian/mozilla-plugin-vlc//usr/lib/ returned exit code 1
make[1]: *** [override_dh_install] Error 2
make[1]: Leaving directory `/tmp/buildd/vlc-1.2+git20110322~ppa1'
make: *** [binary] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
E: Failed autobuilding of package
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//13963 and its subdirectories
codexlibre@tonignome-laptop:~/CodigosFonte/vlc$ 

```

I have to do to solve this problem?

---

### Post by MadCow108 on 2011-03-23
where did you obtain the source package from?

```
dh_install --fail-missing
cp: cannot stat `debian/tmp/usr/lib/mozilla': No such file or directory
```

it can find that folder/file
update the debian/package.install file.

---

### Post by CMatomic on 2011-03-23
> **MadCow108 said:**
> where did you obtain the source package from?

```
dh_install --fail-missing
cp: cannot stat `debian/tmp/usr/lib/mozilla': No such file or directory
```

it can find that folder/file
update the debian/package.install file.

For me it is easy to build, but in building packages. DEB is still a new thing for me.
So I ask how do I know add the correct links in the case of vlc?

**vlc.install**
```
usr/bin/qvlc
usr/bin/svlc
usr/lib/vlc/plugins/access/libxcb_screen_plugin.so
usr/lib/vlc/plugins/codec/libavcodec_plugin.so
usr/lib/vlc/plugins/codec/libsdl_image_plugin.so
usr/lib/vlc/plugins/control/libglobalhotkeys_plugin.so
usr/lib/vlc/plugins/gui/libqt4_plugin.so
usr/lib/vlc/plugins/gui/libskins2_plugin.so
usr/lib/vlc/plugins/misc/libxdg_screensaver_plugin.so
usr/lib/vlc/plugins/misc/libxscreensaver_plugin.so
usr/lib/vlc/plugins/services_discovery/libxcb_apps_plugin.so
usr/lib/vlc/plugins/video_filter/libpanoramix_plugin.so
usr/lib/vlc/plugins/video_output/libaa_plugin.so
usr/lib/vlc/plugins/video_output/libxcb_glx_plugin.so
usr/lib/vlc/plugins/video_output/libxcb_window_plugin.so
usr/lib/vlc/plugins/video_output/libxcb_x11_plugin.so
usr/lib/vlc/plugins/video_output/libxcb_xv_plugin.so
usr/lib/mozilla
usr/share/applications
usr/share/kde4
```

**Rules **
```
#!/usr/bin/make -f

DEB_HOST_GNU_TYPE   ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
DEB_HOST_ARCH       ?= $(shell dpkg-architecture -qDEB_BUILD_ARCH)
DEB_BUILD_GNU_TYPE  ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)
DEB_HOST_ARCH_OS    ?= $(shell dpkg-architecture -qDEB_HOST_ARCH_OS)
VERSION = $(shell  dpkg-parsechangelog|sed -n 's/^Version: //p')
DEBIAN_VERSION = $(shell echo $(VERSION)|sed -nr 's/[^:]+://; s/.*-([^-]+$$)/\1/p')

ifeq ($(DEB_BUILD_GNU_TYPE),$(DEB_HOST_GNU_TYPE))
confflags := --build=$(DEB_BUILD_GNU_TYPE)
else
confflags := --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE)
endif

ifneq (,$(filter noopt,$(DEB_BUILD_OPTIONS)))
confflags += --disable-optimizations --disable-mmx --disable-sse --disable-altivec
endif

LDFLAGS = -Wl,--as-needed

# configure flags
confflags += \
	--config-cache \
	--disable-maintainer-mode \
	--disable-silent-rules \
	--disable-update-check \
	--enable-fast-install \
	--prefix=/usr \
	--docdir=/usr/share/doc/vlc-nox \
	--sysconfdir=/etc \
	--with-binary-version=$(DEBIAN_VERSION) \
	$(NULL)
# configure features
confflags += \
	--enable-a52 \
	--enable-aa \
	--enable-bonjour \
	--enable-caca \
	--enable-dca \
	--enable-dirac \
	--enable-dvb \
	--enable-dvbpsi \
	--enable-dvdnav \
	--enable-faad \
	--enable-flac \
	--enable-fluidsynth \
	--enable-freetype \
	--enable-fribidi \
	--enable-ggi \
	--enable-gnutls \
	--enable-jack \
	--enable-kate \
	--enable-libass \
	--enable-libmpeg2 \
	--enable-libproxy \
	--enable-libxml2 \
	--enable-lirc \
	--enable-live555 \
	--enable-mad \
	--enable-mkv \
	--enable-mod \
	--enable-mozilla \
	--enable-mpc \
	--enable-mtp \
	--enable-mux_ogg \
	--enable-ncurses \
	--enable-notify \
	--enable-ogg \
	--enable-pulse \
	--enable-qt4 \
	--enable-realrtsp \
	--enable-schroedinger \
	--enable-sdl \
	--enable-bluray \
	--enable-shout \
	--enable-skins2 \
	--enable-smb \
	--enable-speex \
	--enable-svg \
	--enable-taglib \
	--enable-theora \
	--enable-twolame \
	--enable-upnp \
	--enable-vcd \
	--enable-vcdx \
	--enable-vorbis \
	--enable-x264 \
	--enable-zvbi \
	--with-kde-solid=/usr/share/kde4/apps/solid/actions/ \
	--with-mozilla-pkg=libxul \
	$(NULL)
# Reasons for disabling features:
# dxva2 -> Windows only
# gnomevfs -> poorly maintained
# goom -> not in Debian
# osso_screensaver -> not targetting maemo
# portaudio -> not needed
# projectm -> broken
# sqlite -> still in development
# telx -> incompatible with zvbi
confflags += \
	--disable-dxva2 \
	--disable-gnomevfs \
	--disable-goom \
	--disable-osso_screensaver \
	--disable-portaudio \
	--disable-projectm \
	--disable-sqlite \
	--disable-telx \
	$(NULL)

# Linux specific flags
ifeq ($(DEB_HOST_ARCH_OS),linux)
confflags += \
	--enable-alsa \
	--enable-atmo \
	--enable-dc1394 \
	--enable-dv \
	--enable-libva \
	--enable-pvr \
	--enable-udev \
	--enable-v4l2 \
	$(NULL)
endif

ifeq ($(DEB_HOST_ARCH_OS),kfreebsd)
confflags += \
	--disable-alsa \
	$(NULL)
endif

# svgalib is only for x86 and x86-64 on Linux
ifneq ($(filter $(DEB_HOST_ARCH), amd64 i386),)
confflags += --enable-svgalib
endif

%:
	dh $@ --parallel

override_dh_auto_clean:
	[ ! -f debian/vlc-nox.install.bak ] || mv -f debian/vlc-nox.install.bak \
		debian/vlc-nox.install
	rm -f debian/vlc-nox.install.kfreebsd
	rm -f debian/vlc-nox.install.hurd
	rm -rf tmp/
	dh_auto_clean

override_dh_auto_configure:
	# We need to build the static library apart
	# Else it's a mess when we build the modules
	./configure --enable-static $(confflags)
	$(MAKE) -C compat
	$(MAKE) -C src libvlccore.la libvlc.la
	mkdir -p tmp
	cp src/.libs/libvlccore.a tmp/libvlccore.a
	cp src/.libs/libvlc.a tmp/libvlc.a
	dh_auto_configure -- $(confflags)

override_dh_auto_test:
ifeq ($(filter nocheck,$(DEB_BUILD_OPTIONS)),)
ifeq ($(DEB_BUILD_GNU_TYPE), $(DEB_HOST_GNU_TYPE))
	# Check which plugins were built and whether they load properly.
	@if test $$( id -u ) -eq 0 ; then \
	   echo "Not runing the test as you are compiling as root"; \
	   echo "Use 'dpkg-buildpackage -rfakeroot' rather than 'fakeroot dpkg-buildpackage'"; \
	else \
	   command="./vlc -vvv --ignore-config --no-plugins-cache --list --no-color"; \
	   echo "$${command}"; $${command} ; \
	fi
endif
endif

override_dh_install:
	cp debian/vlc-nox.install debian/vlc-nox.install.bak
	for dir in sse2 3dnow altivec arm_neon mmx mmxext ; do \
	        if test -d debian/tmp/usr/lib/vlc/plugins/$${dir}; then \
	                echo usr/lib/vlc/plugins/$${dir} >> debian/vlc-nox.install ; \
	        fi ; \
	done
	# Remove some modules on non-linux arch
	sed -e '/\(lib\|libaccess_\)\(alsa\|atmo\|dc1394\|dv\|dvb\|fb\|v4l\|v4l2\|pvr\|udev\)_/d' \
	 debian/vlc-nox.install > debian/vlc-nox.install.kfreebsd
	sed -e '/\(lib\|libaccess_\)\(probe_hal\)_/d' \
	 debian/vlc-nox.install.kfreebsd > debian/vlc-nox.install.hurd
	cp tmp/libvlc.a debian/tmp/usr/lib
	cp tmp/libvlccore.a debian/tmp/usr/lib
	# Clean up libtool crap
	find debian/tmp -name '*.la' -exec rm '{}' ';'
	# Remove useless stuff
	ln -sf /usr/share/fonts/truetype/freefont/FreeSans.ttf debian/tmp/usr/share/vlc/skins2/fonts/FreeSans.ttf
	ln -sf /usr/share/fonts/truetype/freefont/FreeMonoBold.ttf debian/tmp/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
	rm -f debian/tmp/usr/share/man/man1/vlc-config.1
	# Install stuff
	dh_install --fail-missing
	# move .hosts
	if test -d debian/vlc-data; then \
		mkdir -p debian/vlc-data/etc/vlc/http; \
		mv debian/vlc-data/usr/share/vlc/http/.hosts debian/vlc-data/etc/vlc/http; \
		ln -s /etc/vlc/http/.hosts debian/vlc-data/usr/share/vlc/http/.hosts; \
		mkdir -p debian/vlc-data/etc/vlc/lua/http; \
		mv debian/vlc-data/usr/share/vlc/lua/http/.hosts debian/vlc-data/etc/vlc/lua/http; \
		ln -s /etc/vlc/http/.hosts debian/vlc-data/usr/share/vlc/lua/http/.hosts; \
                
	fi
ifeq ($(DEB_BUILD_GNU_TYPE), $(DEB_HOST_GNU_TYPE))
	# Check that we did not install a plugin linked with libX11 or 
	# libxcb in vlc-nox
	BORKED=no; \
	for file in $$(find debian/vlc-nox/usr/lib/vlc -name '*.so'); do \
	  if objdump -x $$file | egrep -q -e '^ +NEEDED +libX11\.so' \
	                                  -e '^ +NEEDED +libxcb\.so'; then \
	    BORKED=yes; \
	    echo $$file depends on libX11 or libxcb; \
	  fi; \
	done; \
	if test "$$BORKED" = yes; then exit 1; fi
endif
	$(if $(shell dpkg-vendor --is Ubuntu && echo true),dh_install -pvlc-nox debian/source_vlc.py usr/share/apport/package-hooks/)
	dh_buildinfo -p vlc-nox

override_dh_strip:
	dh_strip --dbg-package=vlc-dbg

override_dh_installdocs:
	dh_installdocs -p vlc-data
	dh_installdocs -p vlc-nox

override_dh_installchangelogs:
	dh_installchangelogs ChangeLog -p vlc-data
	dh_installchangelogs ChangeLog -p vlc-nox
```

**mozilla-plugin-vlc.install**

```
usr/lib/mozilla
```

---

### Post by MadCow108 on 2011-03-23
is that an official package by vlc? if yes then report a bug.
what is in debian/tmp/?
the package building fails because make install does not create a usr/lib/mozilla in debian/tmp
I am not familiar with what you need to get a running vlc.
This may be files which aren't needed anymore in in vlc 1.2 so you can just remove the line from the install files or drop the --fail-missing flag of dh_install.

but if its required something else is wrong.

brief summary of what a standard configure/make package build does:
- extract original source
- apply patches
- configure
- build (e.g. make)
- install into temporary directory (e.g. make install DESTDIR=debian/tmp)
- look at stuff in DESTDIR and install it into debian/packagename/ according to files in debian/ (see man dh_install*)
- build deb package from debian/packagename/

---

### Post by CMatomic on 2011-03-23
> **MadCow108 said:**
> is that an official package by vlc? if yes then report a bug.
what is in debian/tmp/?
the package building fails because make install does not create a usr/lib/mozilla in debian/tmp
I am not familiar with what you need to get a running vlc.
This may be files which aren't needed anymore in in vlc 1.2 so you can just remove the line from the install files or drop the --fail-missing flag of dh_install.

but if its required something else is wrong.

brief summary of what a standard configure/make package build does:
- extract original source
- apply patches
- configure
- build (e.g. make)
- install into temporary directory (e.g. make install DESTDIR=debian/tmp)
- look at stuff in DESTDIR and install it into debian/packagename/ according to files in debian/ (see man dh_install*)
- build deb package from debian/packagename/
Thanks for responding
I asked the same question in the vlc forum 
[http://forum.videolan.org/viewtopic.php?f=13&t=89143](http://forum.videolan.org/viewtopic.php?f=13&t=89143)
I got the following response
[quote="Rémi Denis-Courmont"]Update your Debian/Ubuntu packaging files to not refer to files that don't exist anymore.[/quote]
 
from response
  I think mozilla is no longer necessary

I goo test again

---

