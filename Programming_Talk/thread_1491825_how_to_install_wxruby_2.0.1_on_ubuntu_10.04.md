---
title: "how to install wxruby 2.0.1 on ubuntu 10.04?"
date: 2010-05-24
forum: Programming Talk
---

### Post by c2h2 on 2010-05-24
anyone has successfully installed wxruby 2.0.1 on ubuntu 10.04?

i have tried this whole afternoon, but it keeps complaining about  


/var/lib/gems/1.9.1/gems/wxruby-ruby19-2.0.0-x86-linux/lib/wx.rb:12:in `require': /var/lib/gems/1.9.1/gems/wxruby-ruby19-2.0.0-x86-linux/lib/wxruby2.so: wrong ELF class: ELFCLASS32 - /var/lib/gems/1.9.1/gems/wxruby-ruby19-2.0.0-x86-linux/lib/wxruby2.so (LoadError)
        from /var/lib/gems/1.9.1/gems/wxruby-ruby19-2.0.0-x86-linux/lib/wx.rb:12:in `<top (required)>'
        from ./h.rb:3:in `require'
        from ./h.rb:3:in `<main>'


thanks in advance.

---

### Post by bildr on 2010-05-27
100% working

uninstall (purge) : ubuntu ruby packages, gems,  rubygem, and rake
(i didn't want to deal with split up packages and even ruby-full doesn't give me the within ruby gem and rake)
 
then make sure you are current
apt-get update

apt-get upgrade

then install dependencies
apt-get -y install libgtk2.0-0 libgtk2.0-dev libgconf2-dev libgl1-mesa-dev libgl1-mesa-glx libglu1-mesa-dev build-essential swig libgtkgl2.0-1 libgtkgl2.0-dev swig

then install options
apt-get -y install 
libiodbc2 libiodbc2-dev
(for odbc option, if you need database consider this required, builtin crashed on me)
libsdl1.2-dev libsdl1.2debian libsdl1.2debian-all
(for sdl sound)
libexpat1 libexpat1-dev libtiff4 libtiff4-dev libjpeg62 libjpeg62-dev libpng12-0 libpng12-dev zlib1g zlib1g-dev
(for expat tiff jpeg png and zlib)
libgnomeprintui2.2-0  libgnomeprintui2.2-dev
(for Print DC options note: print DC not available when using wxGTK, I am assuming because printing support is handled by GTK)
freeglut3 freeglut3-dev
(for opengl rubygem)
libmagickwand2 libmagickcore2 libmagickwand-dev libmagickcore2-extra libmagickcore-dev
(for rmagick rubygem)
gstreamermm gstreamermm-dev these are required of the following libs some are required many are not.

I will thin it out when I get time.  If it doesn't have -dev it probably isn't required

bluez-gstreamer gir1.0-gstreamer-0.10 gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-plugins-mp3-partner gstreamer0.10-gnomevfs gstreamer0.10-nice gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-pulseaudio gstreamer0.10-sdl gstreamer0.10-tools gstreamer0.10-x libgstfarsight0.10-0 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base0.10-dev libgstreamer0.10-0 libgstreamer0.10-0-dbg libgstreamer0.10-dev libgstreamermm-0.10-2 libgstreamermm-0.10-dbg libgstreamermm-0.10-dev libgstrtspserver-0.10-0 libgstrtspserver-0.10-dev

updated ldconfig(probably overkill but I would rather be complete than missing something)

added /etc/ld.so.conf.d/mylibs.conf with contents
# my libs config
/usr/lib
/usr/lib32
/usr/lib64
/usr/local/lib
/usr/local/lib32
/usr/local/lib64

then update cache
rm /etc/ld.so.cache
ldconfig

Installing from original vendor source in this order ruby 1.9.1(latest stable)
(my testing suggests that swig 1.3.40 works but you have to change MAX_VERSION in the rakefile for wxruby)
(the wxruby website says you need rake and gem, but that is included in ruby 2.0.1 out of the box)
(CFLAGS=-fPIC CXXFLAGS=-fPIC LDFLAGS=-fPIC is required on the configure  line for ruby and wxWidgets if on x86_64)
(alternately:
 export CFLAGS=-fPIC CXXFLAGS=-fPIC LDFLAGS=-fPIC
 in a terminal and you don't have to add it to each configure line while in a single shell)

./configure --enable-shared
make
sudo make install

(the enable-shared flag is for ruby-opengl gem, it doesn't compile or install properly unless shared)

gem install ruby-opengl rmagick

wxWidgets latest stable from source

in project root
./configure --enable-shared --with-gtk --enable-monolithic --enable-unicode --disable-debug --enable-catch_segvs --enable-graphics_ctx --enable-mediactrl --with-opengl --enable-gui --enable-xrc --enable-mdi --enable-gif --enable-pcx --enable-iff --enable-pnm --enable-xpm --with-libjpeg=builtin --with-libpng=builtin --with-libtiff=builtin --with-zlib=builtin --with-expat=builtin --with-odbc  --with-sdl
(this was the exact configure line I used, NOT the one recommended by the wxruby devs)

(these flags enable external options remove any =builtin or =no options that you replace --enable-odbc=sys --with-libjpeg=sys --with-libpng=sys --with-libtiff=sys  --with-zlib=sys --with-expat=sys)

(CFLAGS=-fPIC CXXFLAGS=-fPIC LDFLAGS=-fPIC is required on the configure line if on x86_64)

in project root
make
sudo make install
ldconfig

in contrib
make
make install


install from source latest wxruby with modified linux rakefile

# rakelinux.rb
#   Copyright 2004-2005 by Kevin Smith
#   released under the MIT-style wxruby2 license
# I modified and released this to the public so...

#############################
# platform-dependent settings

require './rake/rakeunixish'
$extra_cppflags = '-Wno-unused-function '

# create a .so binary
$extra_ldflags = '-shared -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2'

# This class is not available on WXGTK
$excluded_classes << 'PrinterDC'

# Extra libraries that are required on Linux
$extra_libs = "-Wl,-Bdynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 " + 
  "-lgdk_pixbuf-2.0 -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 " + 
  "-lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lglib-2.0 " +
  "-lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lxml2 " +
  "-lgobject-2.0 -lxml2 -lgthread-2.0 -lrt -lglib-2.0"
libs = $wx_libs.split(' ')
libs.collect! do | lib |
  if $static_build and lib =~ /lwx_/
    lib = "-Wl,-Bstatic #{lib} -Wl,-Bdynamic"
  end
  lib
end

$wx_libs = libs.join(' ')


sudo su
rake clean
rake recompile
rake install

test with the samples
ruby -rubygems ./samples/minimal/minimal.rb
ruby -rubygems ./samples/mediactrl/mediactrl.rb

working for me with this method on both x86_64 and i386 10.04 clean install and upgrade 100%.

ok, so I am comfortable using wxWidgets and ruby from source.  dependencies from ubuntu working.

hope it all works for you

P.S. - Sorry if my syntax or methods were excessive of technically incorrect but functional.  I have no formal training in programming or linux usage.  My goal was a working solution.

requesting solved

please let me know if there are still any problems

note: i just had to do all this again for maverick...to follow these directions properly in maverick you must modify
libmagickwand2 libmagickcore2 libmagickwand-dev libmagickcore2-extra libmagickcore-dev
to be 3 instead of 2
gstreamermm needs:
apt-get install libgstreamermm-0.10-2 libgstreamermm-0.10-dev
fluendo needs to chop off the partner at end of package resulting in:
gstreamer0.10-fluendo-mp3 in the huge package list instead of the other fluendo package
evidently autoconf was taken out of build-essential as well ... install it separately - gosh this is a pain

ubuntu install process is so fscked. i install vm's to support ruby and RoR on ubuntu because builtin packages are woefully broken

i think they change package names just to make my life difficult - switching to lfs systems across the board soon

---

### Post by unter on 2010-07-01
wow. why does it have to be that hard? :(

---

### Post by bildr on 2010-07-03
because I am lazy and haven't built packages to do this, at least i did the hard part and gave you all the compilation options and dependencies...

---

