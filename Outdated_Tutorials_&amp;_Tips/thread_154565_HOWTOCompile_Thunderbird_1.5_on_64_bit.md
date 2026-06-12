---
title: "HOWTO:Compile Thunderbird 1.5 on 64 bit"
date: 2006-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by art on 2006-04-03
Looking for ways to get my favorite mail client on 64 bit platform I found that there is no place on this forums where I can get instructions on how to build it from source, so I decided to write one. Here it goes:
1: Download the source for 1.5 [http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/1.5/source/thunderbird-1.5-source.tar.bz2]("http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/1.5/source/thunderbird-1.5-source.tar.bz2")
2: Open up the terminal and untar the file 
tar jxf thunderbird-1.5-source.tar.bz2
3: cd mozilla
4: Create the .mozconfig in your $HOME
gedit $HOME/.mozconfig&
and paste this into it

export BUILD_OFFICIAL=1
export MOZILLA_OFFICIAL=1
mk_add_options MOZ_THUNDERBIRD=1
mk_add_options MOZ_OBJDIR=/usr/lib/thunderbird_build/
mk_add_options BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
ac_add_options --enable-application=mail
ac_add_options --enable-optimize=-O2
ac_add_options --disable-debug
ac_add_options --enable-xft
ac_add_options --enable-default-toolkit=gtk2
ac_cv_visibility_pragma=no

5: Create the MOZ_OBJDIR
sudo mkdir /usr/lib/thunderbird_build/

6: If like me you have a dual CPU system you can speed up the build process by adding 
mk_add_options MOZ_MAKE_FLAGS=-j2
to the end of .mozconfig
7: Start the build process
make -f client.mk build_all 
This will take some time. 
8: After it finishes 
sudo ln -s /usr/lib/thunderbird_build/dist/bin/thunderbird /usr/bin/thunderbird15
Now you can run it with thunderbird15.
Enjoy!

---

