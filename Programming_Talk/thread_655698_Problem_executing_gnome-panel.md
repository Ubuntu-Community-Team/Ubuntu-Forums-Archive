---
title: "Problem executing gnome-panel"
date: 2007-11-27
forum: Programming Talk
---

### Post by caclratm on 2007-11-27
I'm trying to build the gnome-panel package from source 'cuz I'll try to build my first bug (I know some C and I want to make myself useful), but when I want to build the package the next message comes up:

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.8...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.8
checking for gnome-doc-utils >= 0.4.2...
  testing gnome-doc-prepare... found 0.12.0
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.20.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running gtkdocize...
Running gnome-doc-common...
Running gnome-doc-prepare...
You should update your 'aclocal.m4' by running aclocal.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.9...
aclocal:configure.in:248: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:248: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
christian@christian-laptop:~/Documents/Bug-gnome/gnome-panel$ ./autogen.sh --prefix=usr/local
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.8...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.8
checking for gnome-doc-utils >= 0.4.2...
  testing gnome-doc-prepare... found 0.12.0
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.20.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running gtkdocize...
Running gnome-doc-common...
Running gnome-doc-prepare...
You should update your 'aclocal.m4' by running aclocal.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.9...
aclocal:configure.in:248: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:248: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.


Any help would be greatly appreciated

---

### Post by caclratm on 2007-11-27
I don't know if this counts as a newbie question, so I'll post it here too...

I'm trying to build the gnome-panel package from source 'cuz I'll try to build my first bug (I know some C and I want to make myself useful), but when I want to build the package the next message comes up:

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
testing autoconf2.50... not found.
testing autoconf... found 2.61
checking for automake >= 1.8...
testing automake-1.10... not found.
testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
testing gtkdocize... found 1.8
checking for gnome-doc-utils >= 0.4.2...
testing gnome-doc-prepare... found 0.12.0
checking for gnome-common >= 2.3.0...
testing gnome-doc-common... found 2.20.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running gtkdocize...
Running gnome-doc-common...
Running gnome-doc-prepare...
You should update your 'aclocal.m4' by running aclocal.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.9...
aclocal:configure.in:248: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:248: error: possibly undefined macro: AM_GCONF_SOURCE_2
If this token and others are legitimate, please use m4_pattern_allow.
See the Autoconf documentation.
christian@christian-laptop:~/Documents/Bug-gnome/gnome-panel$ ./autogen.sh --prefix=usr/local
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
testing autoconf2.50... not found.
testing autoconf... found 2.61
checking for automake >= 1.8...
testing automake-1.10... not found.
testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
testing gtkdocize... found 1.8
checking for gnome-doc-utils >= 0.4.2...
testing gnome-doc-prepare... found 0.12.0
checking for gnome-common >= 2.3.0...
testing gnome-doc-common... found 2.20.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running gtkdocize...
Running gnome-doc-common...
Running gnome-doc-prepare...
You should update your 'aclocal.m4' by running aclocal.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.9...
aclocal:configure.in:248: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:248: error: possibly undefined macro: AM_GCONF_SOURCE_2
If this token and others are legitimate, please use m4_pattern_allow.
See the Autoconf documentation.


Any help would be greatly appreciated

---

### Post by master_kernel on 2007-11-27
I think you need to install autoconf. I hate these configure messages; they drive me crazy trying to find out what dependency(s) isn't satisfied.

---

### Post by caclratm on 2007-11-27
I've already installed it. In fact I installed autotools-dev and it came inside...

---

### Post by dholbach on 2007-11-28
sudo apt-get install libgconf2-dev

---

### Post by caclratm on 2007-11-28
Thanks a lot. After that I had to install some more packages but now I'm good to go

---

### Post by caclratm on 2007-12-26
Hi,

I was asked by a teacher to add a functionality to gnome-panel. I have already downloaded the source code from svn and all the tools and all, but I think I don't quite understand the problem I was asked to solve. Here's the link to the Bugzilla page:

[http://bugzilla.gnome.org/show_bug.cgi?id=127940](http://bugzilla.gnome.org/show_bug.cgi?id=127940)

I think I followed the instructions he gives to emulate the environment he wants but contrary to him I was able to do what he wanted. It might be that this is an old feature request and that it has already been added. Does anybody know anything about this?, it would be really appreciated.

---

### Post by adam.tropics on 2007-12-26
Autohide is already in the panel options (that bug was from 2003), and is directional in the sense that if your panel is on the side it will slide to the side, if on the top, will slid up, etc etc. Not sure I understand your question to be honest.

---

### Post by caclratm on 2007-12-26
The thing is I'm not sure I understand what's being asked for by the person that made the post. Is this a problem that's already been addressed?, what was the problem exactly?, why was this a problem?.

---

### Post by adam.tropics on 2007-12-26
Ok, now you have lost me....confused. As far as I can see you are being guided towards adding a feature that was added a while ago already. Maybe you could get him to clarify what it is he is expecting of you? I don't think you're gonna get very far trying to fix an issue until you're sure of what that issue is. Sorry if that's not all that helpful!

---

### Post by caclratm on 2007-12-26
Actually, that's exactly the problem. It seems to me that what the guy that requested the feature wanted has already been added, but I wanted to corroborate this with someone because maybe I wasn't understanding exactly what the feature was.

---

### Post by adam.tropics on 2007-12-26
lol sounds like he doesn't understand either!

---

### Post by caclratm on 2008-01-01
Hi,

I'm  trying to modify some of the code in gnome-panel so I downloaded the code from the svn repository and installed it all right. To be able to test it I do 'sudo gnome-panel'. This was all done on a fresh install. After I downloaded and installed it, I started installing apps I like on the machine (amarok, Eclipse, miro, codecs, etc.). Now, though I'm able to compile and install without any problems, whenever I do 'sudo gnome-panel' I get this:

christian@christian-laptop:~/Documents/workspace/FeatureGnomePanel$ sudo gnome-panel

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowInfo" verb="" label="Get Help Online..." hidden="0" pixtype="pixbuf" pixname="0000001000000010A00000000dfbf6008e9b86e8de9b96eeae9b96ee1b57053bba41f1eeca60a09fea40202ffa60a09fea51f1eecb46e51bce9b96ee1e9b96eeae9b86e8ddfbf600800000000e9b96f8af0ce9afff2eee6ffa4a6a2ffbc9693ffedb8b7fffcececfffef9f9fffcebebffedb7b6ffbb9894ffa4a6a2fff2eee6fff0ce9affe9b96f8a00000000e9b96eecf2eee5ff9b9b93ffe9eae9fffefefefffce3e3fff9bbbbfff7ababfff9bbbbfffce3e3fffefefeffe8e9e8ff9b9b93fff2eee5ffe9b86eeb00000000e9b96ee7abaca9ffe8e8e7fffefefdfffcfcfcfff5e3e2fff16867fff16565fff16968fff5e3e2fffcfcfcfffdfdfdffe7e7e6ffabaca9ffe9b96ee600000000b5583ec0b89590fffdfdfdfffcfcfcfff3f4f2fff0f0efffe16d6cffd74343ffe17170fff1f1f0fff3f4f2fffcfcfcfffdfdfdffb88e8affb66c4db600000000a51f1eebe7a0a0fffbe0e0fff5e3e2fff0f1efffb6b8b4f49f3735ed9f2827cc9e3836edb8bab6f4f1f2f1fff5e3e2fffbdfdfffe69999ffa51f1eeb00000000a60909fef8cecefff9b9b9fff26e6dffdf7373ff9e3836eaffffff0100000000ffffff019f3534eae48281fff27373fff9b9b9fff6c6c6ffa60909fe00000000a40202fffad5d5fff7aaaafff27474ffda5353ff9f2928cc0000000000000000000000009f2928ccdc5e5efff37d7dfff7aaaafff9ceceffa40202ff00000000a60909fef5bfbffff8b8b8fff27473ffe58786ff9f3534eaffffff0100000000ffffff019e3836eae58f8efff37978fff8b8b8fff4b8b8ffa60909fe00000000a51f1eebe18888fffbddddfff5e3e2fff4f5f4ffbcbebbf59e3836eda02927cb9f3735edbec1bdf5f5f6f5fff5e3e2fffbdcdcffdf8181ffa51f1eeb00000000b86d4cb8b48984fffcfcfcfffcfcfcfff3f4f2fff6f6f5ffea9d9dffe06f6fffeca2a1fff7f7f6fff4f4f3fffcfcfcfffcfcfbffb38d87ffb5583ec000000000e9b96ee1abaca9ffdedfddfffcfcfcfffcfcfcfff5e4e3ffa07070ffdbababffa57170fff5e4e3fffcfcfcfffcfcfcffdddedbffabaca9ffe9b96ee700000000e9b96fe9f3eee6ff9a9a92ffdbdcdaffcacac9ffa48f8fff605b5bffa7a0a0ff625d5dffa58f8fffcacac9ffdadbd9ff9a9a92fff2eee5ffe9b96eec55555590716859dc6e6960ff5e5d5dff555555ff555555ff555555ffe2e1e1ffe2e1e1ffc7c6c6ff555555ff555555ff555555ff595958ff65615cff6e6659dfc8c8c874c8c7c69eccc5bbe5cac6c1fdc8c7c6ffa0a0a0ff808080ffe2e2e2ffc8c8c8ffa0a0a0ff666666ff808080ffa0a09fffc9c7c5fecbc6bfeec8c7c6a4555555765555559c555555c9555555eb555555fc555555ff555555ffc0c0c0ff9c9c9cff868686ff555555ff555555ff555555fe555555f7555555de555555ad"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowTranslations" verb="" label="Translate This Application..." hidden="0" pixtype="pixbuf" pixname="0000001000000010Abcbcb841bdc0baebbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbdc0baebbcbcb841000000000000000000000000bec0b9e7fafafafffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffafafaffbec0b9e7000000000000000000000000babdb6ffffffffff7ba5d2ff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff7ba5d2ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffff4371acff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff4371acffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5ffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffd5dde4ff7495c1ff3e6da7ff3969a7ea3768a68c2e68a216babdb6ffffffffffebedeaffebedeaffebedeaff3465a4ff7f9ec1ffd5dde1ffe5e9e8ffa0b5ceff4572abffa0bad9ffcfdeeeffbfd3e8ff80a2cbf93465a4ffbabdb6ffffffffffe8eae6ffe8eae6ffe8eae6ff3465a4ff97b2d3ff5680b3ff4975adff799ac4ffcedcedffc8daecff9dbcdeff9bbbddffcfdfefff3465a4ffbabdb6ffffffffffe4e7e2ffe4e7e2ffe4e7e2ff3465a4ffc6d8ebffd1dfefffe3ebf5ffd7e4f1ffbcd2e8ffa1bfdfff95b7dbff89afd7ffcfdfefff3465a4ffbabdb6ffffffffffe1e3deffe1e3deffe1e3deff3465a4ffc0d4e9ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc8daedff3465a4ffbdbfb8e7f3f4f2ffffffffffffffffffffffffff3465a4ffbbd1e7ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc2d6eaff3465a4ffbcbcb841bbbeb7ebbabdb6ffbabdb6ffbabdb6ff3465a4ffb5cde5ffa9c4e2ffc5d7ebffb9cfe7ffb8cee7ffc1d5eaffc1d5eaffb9cfe7ffbcd1e8ff3465a4ff00000000000000000000000000000000000000003465a4ffafc8e3ffafc8e4ffc7d8ecffc9daecffbacee5ff668dbdf43f6ea9f44876aef37a9dc8fa3465a4ff00000000000000000000000000000000000000003465a4ff6b92c0f8b2c9e2ffd0dfeeff97b3d4fd3c6ca7f43767a56f2b6aaa0c3868a7203868a69b3465a4ff00000000000000000000000000000000000000003764a6173768a5913a6aa7ec3b6ba7f13d6ca9bb3665a1260000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowBugs" verb="" label="Report a Problem" hidden="0" pixtype="pixbuf" pixname="0000001000000010A0000000000000000000000000000000000000000c4a10093c5a100f9c49d002700000000000000000000000000000000c2a30019c4a10098c4a000ffbfaa000c0000000000000000000000000000000000000000c6a300e8ecde8bfecaab15f5c7a20076aaaa0003c59e0042c6a400b8caaa16f7cdaf29ffc5a200be0000000000000000000000000000000000000000c5a10039d4b835f5fffffffffdfae4ffdec856f7c4a000ffd7be3ff4f3e9a9ffffffffffd0b42df6c39d002f0000000000000000000000000000000000000000c8a2009deee191fef7ea84fff2df3ffffcf8d6fffdfae8fffcf7d1fffaf3b7fff9f4d0ffc5a200d70000000000000000c4a000e2c5a205ffc9a811f8c5a201f6c7a50dfffdfbe8fff2de35ff0e0d01ff131104fff1dc26fff0d811fffaf3b9ffe1cc60f7c4a000630000000000000000c69f0028c9a912f6fffffffffffffffffefcedfff8ed90fff2db1dff2b2705ff332f07fff2db1dfff1da1afffffffdffc7a50dffc5a10039000000000000000000000000c6a30075ddc64ef6fdfadffff3dd27fff3dd22fff4de26ff48410cff554d0efff4de26fff3dd22fffaf2acfff7efbaffc9a912f5c4a100570000000000000000ff800002c6a301cef3e7a4fefaf09dfff5df2afff6e02fff655d15ff786d18fff6e02ffff5df2afff3dd26fffaf1a8ffffffffffd0b32bf8c5a200a40000000000000000c49f004accad24fffefbe7fff6e131fff7e237fff8e33cfff8e33cfff7e237fff6e131fff8eb7ffffefcecfff3e9aefecdae20fcc5a100d900000000b6920007c6a301daf5ebaffefaf1a0fff7e235fff8e43eff3a3510ff3a3510fff8e43efff7e235fffffefbffcaaa1affc8a401abc19f00250000000000000000c7a3009ce8d67afafffffffffefce9fffaef8dfff9e540ff3a3511ff3a3511fff9e540fff7e237fffdf8d0ffdfc858f7c5a200650000000000000000c4a2005ac7a40bffeada7efdddc653f4caaa1cfffefdf3fff8e546fff9e64afffdf4b2fffefdf1fffdf8cdfffcf7c8fffbf8dcffc7a401e2ff80000200000000c4a000ffc5a000f6c7a20283c49f003dc6a402d3f9f3c8fffaee8cfffefaddfff4eaacfec7a60fffddc650f4f3e9aaffffffffffd7bd3ef5c5a1004f00000000c6aa0009000000000000000000000000c6a10087f0e399fdffffffffe4d16cf9c7a302d6c6a30024c6a20047c7a403a9c9a508f4ccac21ffc4a000ff0000000000000000000000000000000000000000c5a00046d1b534fcd2b42df6c7a3029bb6920007000000000000000000000000b6920007c5a00053c5a000cdc39d002f00000000000000000000000000000000c49d000dc4a000ffc3a10051000000000000000000000000000000000000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowInfo" verb="" label="Get Help Online..." hidden="0" pixtype="pixbuf" pixname="0000001000000010A00000000dfbf6008e9b86e8de9b96eeae9b96ee1b57053bba41f1eeca60a09fea40202ffa60a09fea51f1eecb46e51bce9b96ee1e9b96eeae9b86e8ddfbf600800000000e9b96f8af0ce9afff2eee6ffa4a6a2ffbc9693ffedb8b7fffcececfffef9f9fffcebebffedb7b6ffbb9894ffa4a6a2fff2eee6fff0ce9affe9b96f8a00000000e9b96eecf2eee5ff9b9b93ffe9eae9fffefefefffce3e3fff9bbbbfff7ababfff9bbbbfffce3e3fffefefeffe8e9e8ff9b9b93fff2eee5ffe9b86eeb00000000e9b96ee7abaca9ffe8e8e7fffefefdfffcfcfcfff5e3e2fff16867fff16565fff16968fff5e3e2fffcfcfcfffdfdfdffe7e7e6ffabaca9ffe9b96ee600000000b5583ec0b89590fffdfdfdfffcfcfcfff3f4f2fff0f0efffe16d6cffd74343ffe17170fff1f1f0fff3f4f2fffcfcfcfffdfdfdffb88e8affb66c4db600000000a51f1eebe7a0a0fffbe0e0fff5e3e2fff0f1efffb6b8b4f49f3735ed9f2827cc9e3836edb8bab6f4f1f2f1fff5e3e2fffbdfdfffe69999ffa51f1eeb00000000a60909fef8cecefff9b9b9fff26e6dffdf7373ff9e3836eaffffff0100000000ffffff019f3534eae48281fff27373fff9b9b9fff6c6c6ffa60909fe00000000a40202fffad5d5fff7aaaafff27474ffda5353ff9f2928cc0000000000000000000000009f2928ccdc5e5efff37d7dfff7aaaafff9ceceffa40202ff00000000a60909fef5bfbffff8b8b8fff27473ffe58786ff9f3534eaffffff0100000000ffffff019e3836eae58f8efff37978fff8b8b8fff4b8b8ffa60909fe00000000a51f1eebe18888fffbddddfff5e3e2fff4f5f4ffbcbebbf59e3836eda02927cb9f3735edbec1bdf5f5f6f5fff5e3e2fffbdcdcffdf8181ffa51f1eeb00000000b86d4cb8b48984fffcfcfcfffcfcfcfff3f4f2fff6f6f5ffea9d9dffe06f6fffeca2a1fff7f7f6fff4f4f3fffcfcfcfffcfcfbffb38d87ffb5583ec000000000e9b96ee1abaca9ffdedfddfffcfcfcfffcfcfcfff5e4e3ffa07070ffdbababffa57170fff5e4e3fffcfcfcfffcfcfcffdddedbffabaca9ffe9b96ee700000000e9b96fe9f3eee6ff9a9a92ffdbdcdaffcacac9ffa48f8fff605b5bffa7a0a0ff625d5dffa58f8fffcacac9ffdadbd9ff9a9a92fff2eee5ffe9b96eec55555590716859dc6e6960ff5e5d5dff555555ff555555ff555555ffe2e1e1ffe2e1e1ffc7c6c6ff555555ff555555ff555555ff595958ff65615cff6e6659dfc8c8c874c8c7c69eccc5bbe5cac6c1fdc8c7c6ffa0a0a0ff808080ffe2e2e2ffc8c8c8ffa0a0a0ff666666ff808080ffa0a09fffc9c7c5fecbc6bfeec8c7c6a4555555765555559c555555c9555555eb555555fc555555ff555555ffc0c0c0ff9c9c9cff868686ff555555ff555555ff555555fe555555f7555555de555555ad"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowTranslations" verb="" label="Translate This Application..." hidden="0" pixtype="pixbuf" pixname="0000001000000010Abcbcb841bdc0baebbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbdc0baebbcbcb841000000000000000000000000bec0b9e7fafafafffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffafafaffbec0b9e7000000000000000000000000babdb6ffffffffff7ba5d2ff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff7ba5d2ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffff4371acff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff4371acffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5ffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffd5dde4ff7495c1ff3e6da7ff3969a7ea3768a68c2e68a216babdb6ffffffffffebedeaffebedeaffebedeaff3465a4ff7f9ec1ffd5dde1ffe5e9e8ffa0b5ceff4572abffa0bad9ffcfdeeeffbfd3e8ff80a2cbf93465a4ffbabdb6ffffffffffe8eae6ffe8eae6ffe8eae6ff3465a4ff97b2d3ff5680b3ff4975adff799ac4ffcedcedffc8daecff9dbcdeff9bbbddffcfdfefff3465a4ffbabdb6ffffffffffe4e7e2ffe4e7e2ffe4e7e2ff3465a4ffc6d8ebffd1dfefffe3ebf5ffd7e4f1ffbcd2e8ffa1bfdfff95b7dbff89afd7ffcfdfefff3465a4ffbabdb6ffffffffffe1e3deffe1e3deffe1e3deff3465a4ffc0d4e9ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc8daedff3465a4ffbdbfb8e7f3f4f2ffffffffffffffffffffffffff3465a4ffbbd1e7ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc2d6eaff3465a4ffbcbcb841bbbeb7ebbabdb6ffbabdb6ffbabdb6ff3465a4ffb5cde5ffa9c4e2ffc5d7ebffb9cfe7ffb8cee7ffc1d5eaffc1d5eaffb9cfe7ffbcd1e8ff3465a4ff00000000000000000000000000000000000000003465a4ffafc8e3ffafc8e4ffc7d8ecffc9daecffbacee5ff668dbdf43f6ea9f44876aef37a9dc8fa3465a4ff00000000000000000000000000000000000000003465a4ff6b92c0f8b2c9e2ffd0dfeeff97b3d4fd3c6ca7f43767a56f2b6aaa0c3868a7203868a69b3465a4ff00000000000000000000000000000000000000003764a6173768a5913a6aa7ec3b6ba7f13d6ca9bb3665a1260000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowBugs" verb="" label="Report a Problem" hidden="0" pixtype="pixbuf" pixname="0000001000000010A0000000000000000000000000000000000000000c4a10093c5a100f9c49d002700000000000000000000000000000000c2a30019c4a10098c4a000ffbfaa000c0000000000000000000000000000000000000000c6a300e8ecde8bfecaab15f5c7a20076aaaa0003c59e0042c6a400b8caaa16f7cdaf29ffc5a200be0000000000000000000000000000000000000000c5a10039d4b835f5fffffffffdfae4ffdec856f7c4a000ffd7be3ff4f3e9a9ffffffffffd0b42df6c39d002f0000000000000000000000000000000000000000c8a2009deee191fef7ea84fff2df3ffffcf8d6fffdfae8fffcf7d1fffaf3b7fff9f4d0ffc5a200d70000000000000000c4a000e2c5a205ffc9a811f8c5a201f6c7a50dfffdfbe8fff2de35ff0e0d01ff131104fff1dc26fff0d811fffaf3b9ffe1cc60f7c4a000630000000000000000c69f0028c9a912f6fffffffffffffffffefcedfff8ed90fff2db1dff2b2705ff332f07fff2db1dfff1da1afffffffdffc7a50dffc5a10039000000000000000000000000c6a30075ddc64ef6fdfadffff3dd27fff3dd22fff4de26ff48410cff554d0efff4de26fff3dd22fffaf2acfff7efbaffc9a912f5c4a100570000000000000000ff800002c6a301cef3e7a4fefaf09dfff5df2afff6e02fff655d15ff786d18fff6e02ffff5df2afff3dd26fffaf1a8ffffffffffd0b32bf8c5a200a40000000000000000c49f004accad24fffefbe7fff6e131fff7e237fff8e33cfff8e33cfff7e237fff6e131fff8eb7ffffefcecfff3e9aefecdae20fcc5a100d900000000b6920007c6a301daf5ebaffefaf1a0fff7e235fff8e43eff3a3510ff3a3510fff8e43efff7e235fffffefbffcaaa1affc8a401abc19f00250000000000000000c7a3009ce8d67afafffffffffefce9fffaef8dfff9e540ff3a3511ff3a3511fff9e540fff7e237fffdf8d0ffdfc858f7c5a200650000000000000000c4a2005ac7a40bffeada7efdddc653f4caaa1cfffefdf3fff8e546fff9e64afffdf4b2fffefdf1fffdf8cdfffcf7c8fffbf8dcffc7a401e2ff80000200000000c4a000ffc5a000f6c7a20283c49f003dc6a402d3f9f3c8fffaee8cfffefaddfff4eaacfec7a60fffddc650f4f3e9aaffffffffffd7bd3ef5c5a1004f00000000c6aa0009000000000000000000000000c6a10087f0e399fdffffffffe4d16cf9c7a302d6c6a30024c6a20047c7a403a9c9a508f4ccac21ffc4a000ff0000000000000000000000000000000000000000c5a00046d1b534fcd2b42df6c7a3029bb6920007000000000000000000000000b6920007c5a00053c5a000cdc39d002f00000000000000000000000000000000c49d000dc4a000ffc3a10051000000000000000000000000000000000000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowInfo" verb="" label="Get Help Online..." hidden="0" pixtype="pixbuf" pixname="0000001000000010A00000000dfbf6008e9b86e8de9b96eeae9b96ee1b57053bba41f1eeca60a09fea40202ffa60a09fea51f1eecb46e51bce9b96ee1e9b96eeae9b86e8ddfbf600800000000e9b96f8af0ce9afff2eee6ffa4a6a2ffbc9693ffedb8b7fffcececfffef9f9fffcebebffedb7b6ffbb9894ffa4a6a2fff2eee6fff0ce9affe9b96f8a00000000e9b96eecf2eee5ff9b9b93ffe9eae9fffefefefffce3e3fff9bbbbfff7ababfff9bbbbfffce3e3fffefefeffe8e9e8ff9b9b93fff2eee5ffe9b86eeb00000000e9b96ee7abaca9ffe8e8e7fffefefdfffcfcfcfff5e3e2fff16867fff16565fff16968fff5e3e2fffcfcfcfffdfdfdffe7e7e6ffabaca9ffe9b96ee600000000b5583ec0b89590fffdfdfdfffcfcfcfff3f4f2fff0f0efffe16d6cffd74343ffe17170fff1f1f0fff3f4f2fffcfcfcfffdfdfdffb88e8affb66c4db600000000a51f1eebe7a0a0fffbe0e0fff5e3e2fff0f1efffb6b8b4f49f3735ed9f2827cc9e3836edb8bab6f4f1f2f1fff5e3e2fffbdfdfffe69999ffa51f1eeb00000000a60909fef8cecefff9b9b9fff26e6dffdf7373ff9e3836eaffffff0100000000ffffff019f3534eae48281fff27373fff9b9b9fff6c6c6ffa60909fe00000000a40202fffad5d5fff7aaaafff27474ffda5353ff9f2928cc0000000000000000000000009f2928ccdc5e5efff37d7dfff7aaaafff9ceceffa40202ff00000000a60909fef5bfbffff8b8b8fff27473ffe58786ff9f3534eaffffff0100000000ffffff019e3836eae58f8efff37978fff8b8b8fff4b8b8ffa60909fe00000000a51f1eebe18888fffbddddfff5e3e2fff4f5f4ffbcbebbf59e3836eda02927cb9f3735edbec1bdf5f5f6f5fff5e3e2fffbdcdcffdf8181ffa51f1eeb00000000b86d4cb8b48984fffcfcfcfffcfcfcfff3f4f2fff6f6f5ffea9d9dffe06f6fffeca2a1fff7f7f6fff4f4f3fffcfcfcfffcfcfbffb38d87ffb5583ec000000000e9b96ee1abaca9ffdedfddfffcfcfcfffcfcfcfff5e4e3ffa07070ffdbababffa57170fff5e4e3fffcfcfcfffcfcfcffdddedbffabaca9ffe9b96ee700000000e9b96fe9f3eee6ff9a9a92ffdbdcdaffcacac9ffa48f8fff605b5bffa7a0a0ff625d5dffa58f8fffcacac9ffdadbd9ff9a9a92fff2eee5ffe9b96eec55555590716859dc6e6960ff5e5d5dff555555ff555555ff555555ffe2e1e1ffe2e1e1ffc7c6c6ff555555ff555555ff555555ff595958ff65615cff6e6659dfc8c8c874c8c7c69eccc5bbe5cac6c1fdc8c7c6ffa0a0a0ff808080ffe2e2e2ffc8c8c8ffa0a0a0ff666666ff808080ffa0a09fffc9c7c5fecbc6bfeec8c7c6a4555555765555559c555555c9555555eb555555fc555555ff555555ffc0c0c0ff9c9c9cff868686ff555555ff555555ff555555fe555555f7555555de555555ad"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowTranslations" verb="" label="Translate This Application..." hidden="0" pixtype="pixbuf" pixname="0000001000000010Abcbcb841bdc0baebbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbdc0baebbcbcb841000000000000000000000000bec0b9e7fafafafffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffafafaffbec0b9e7000000000000000000000000babdb6ffffffffff7ba5d2ff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff7ba5d2ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffff4371acff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff4371acffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5ffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffd5dde4ff7495c1ff3e6da7ff3969a7ea3768a68c2e68a216babdb6ffffffffffebedeaffebedeaffebedeaff3465a4ff7f9ec1ffd5dde1ffe5e9e8ffa0b5ceff4572abffa0bad9ffcfdeeeffbfd3e8ff80a2cbf93465a4ffbabdb6ffffffffffe8eae6ffe8eae6ffe8eae6ff3465a4ff97b2d3ff5680b3ff4975adff799ac4ffcedcedffc8daecff9dbcdeff9bbbddffcfdfefff3465a4ffbabdb6ffffffffffe4e7e2ffe4e7e2ffe4e7e2ff3465a4ffc6d8ebffd1dfefffe3ebf5ffd7e4f1ffbcd2e8ffa1bfdfff95b7dbff89afd7ffcfdfefff3465a4ffbabdb6ffffffffffe1e3deffe1e3deffe1e3deff3465a4ffc0d4e9ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc8daedff3465a4ffbdbfb8e7f3f4f2ffffffffffffffffffffffffff3465a4ffbbd1e7ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc2d6eaff3465a4ffbcbcb841bbbeb7ebbabdb6ffbabdb6ffbabdb6ff3465a4ffb5cde5ffa9c4e2ffc5d7ebffb9cfe7ffb8cee7ffc1d5eaffc1d5eaffb9cfe7ffbcd1e8ff3465a4ff00000000000000000000000000000000000000003465a4ffafc8e3ffafc8e4ffc7d8ecffc9daecffbacee5ff668dbdf43f6ea9f44876aef37a9dc8fa3465a4ff00000000000000000000000000000000000000003465a4ff6b92c0f8b2c9e2ffd0dfeeff97b3d4fd3c6ca7f43767a56f2b6aaa0c3868a7203868a69b3465a4ff00000000000000000000000000000000000000003764a6173768a5913a6aa7ec3b6ba7f13d6ca9bb3665a1260000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowBugs" verb="" label="Report a Problem" hidden="0" pixtype="pixbuf" pixname="0000001000000010A0000000000000000000000000000000000000000c4a10093c5a100f9c49d002700000000000000000000000000000000c2a30019c4a10098c4a000ffbfaa000c0000000000000000000000000000000000000000c6a300e8ecde8bfecaab15f5c7a20076aaaa0003c59e0042c6a400b8caaa16f7cdaf29ffc5a200be0000000000000000000000000000000000000000c5a10039d4b835f5fffffffffdfae4ffdec856f7c4a000ffd7be3ff4f3e9a9ffffffffffd0b42df6c39d002f0000000000000000000000000000000000000000c8a2009deee191fef7ea84fff2df3ffffcf8d6fffdfae8fffcf7d1fffaf3b7fff9f4d0ffc5a200d70000000000000000c4a000e2c5a205ffc9a811f8c5a201f6c7a50dfffdfbe8fff2de35ff0e0d01ff131104fff1dc26fff0d811fffaf3b9ffe1cc60f7c4a000630000000000000000c69f0028c9a912f6fffffffffffffffffefcedfff8ed90fff2db1dff2b2705ff332f07fff2db1dfff1da1afffffffdffc7a50dffc5a10039000000000000000000000000c6a30075ddc64ef6fdfadffff3dd27fff3dd22fff4de26ff48410cff554d0efff4de26fff3dd22fffaf2acfff7efbaffc9a912f5c4a100570000000000000000ff800002c6a301cef3e7a4fefaf09dfff5df2afff6e02fff655d15ff786d18fff6e02ffff5df2afff3dd26fffaf1a8ffffffffffd0b32bf8c5a200a40000000000000000c49f004accad24fffefbe7fff6e131fff7e237fff8e33cfff8e33cfff7e237fff6e131fff8eb7ffffefcecfff3e9aefecdae20fcc5a100d900000000b6920007c6a301daf5ebaffefaf1a0fff7e235fff8e43eff3a3510ff3a3510fff8e43efff7e235fffffefbffcaaa1affc8a401abc19f00250000000000000000c7a3009ce8d67afafffffffffefce9fffaef8dfff9e540ff3a3511ff3a3511fff9e540fff7e237fffdf8d0ffdfc858f7c5a200650000000000000000c4a2005ac7a40bffeada7efdddc653f4caaa1cfffefdf3fff8e546fff9e64afffdf4b2fffefdf1fffdf8cdfffcf7c8fffbf8dcffc7a401e2ff80000200000000c4a000ffc5a000f6c7a20283c49f003dc6a402d3f9f3c8fffaee8cfffefaddfff4eaacfec7a60fffddc650f4f3e9aaffffffffffd7bd3ef5c5a1004f00000000c6aa0009000000000000000000000000c6a10087f0e399fdffffffffe4d16cf9c7a302d6c6a30024c6a20047c7a403a9c9a508f4ccac21ffc4a000ff0000000000000000000000000000000000000000c5a00046d1b534fcd2b42df6c7a3029bb6920007000000000000000000000000b6920007c5a00053c5a000cdc39d002f00000000000000000000000000000000c49d000dc4a000ffc3a10051000000000000000000000000000000000000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'


I didn't use to have this problem. Any idea as to why is this and how to solve it?, is it important or can I still go on with my stuff without worrying about it too much?

---

### Post by caclratm on 2008-01-01
Hi,

I'm  trying to modify some of the code in gnome-panel so I downloaded the code from the svn repository and installed it all right. To be able to test it I do 'sudo gnome-panel'. This was all done on a fresh install. After I downloaded and installed it, I started installing apps I like on the machine (amarok, Eclipse, miro, codecs, etc.). Now, though I'm able to compile and install without any problems, whenever I do 'sudo gnome-panel' I get this:

christian@christian-laptop:~/Documents/workspace/FeatureGnomePanel$ sudo gnome-panel

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowInfo" verb="" label="Get Help Online..." hidden="0" pixtype="pixbuf" pixname="0000001000000010A00000000dfbf6008e9b86e8de9b96eeae9b96ee1b57053bba41f1eeca60a09fea40202ffa60a09fea51f1eecb46e51bce9b96ee1e9b96eeae9b86e8ddfbf600800000000e9b96f8af0ce9afff2eee6ffa4a6a2ffbc9693ffedb8b7fffcececfffef9f9fffcebebffedb7b6ffbb9894ffa4a6a2fff2eee6fff0ce9affe9b96f8a00000000e9b96eecf2eee5ff9b9b93ffe9eae9fffefefefffce3e3fff9bbbbfff7ababfff9bbbbfffce3e3fffefefeffe8e9e8ff9b9b93fff2eee5ffe9b86eeb00000000e9b96ee7abaca9ffe8e8e7fffefefdfffcfcfcfff5e3e2fff16867fff16565fff16968fff5e3e2fffcfcfcfffdfdfdffe7e7e6ffabaca9ffe9b96ee600000000b5583ec0b89590fffdfdfdfffcfcfcfff3f4f2fff0f0efffe16d6cffd74343ffe17170fff1f1f0fff3f4f2fffcfcfcfffdfdfdffb88e8affb66c4db600000000a51f1eebe7a0a0fffbe0e0fff5e3e2fff0f1efffb6b8b4f49f3735ed9f2827cc9e3836edb8bab6f4f1f2f1fff5e3e2fffbdfdfffe69999ffa51f1eeb00000000a60909fef8cecefff9b9b9fff26e6dffdf7373ff9e3836eaffffff0100000000ffffff019f3534eae48281fff27373fff9b9b9fff6c6c6ffa60909fe00000000a40202fffad5d5fff7aaaafff27474ffda5353ff9f2928cc0000000000000000000000009f2928ccdc5e5efff37d7dfff7aaaafff9ceceffa40202ff00000000a60909fef5bfbffff8b8b8fff27473ffe58786ff9f3534eaffffff0100000000ffffff019e3836eae58f8efff37978fff8b8b8fff4b8b8ffa60909fe00000000a51f1eebe18888fffbddddfff5e3e2fff4f5f4ffbcbebbf59e3836eda02927cb9f3735edbec1bdf5f5f6f5fff5e3e2fffbdcdcffdf8181ffa51f1eeb00000000b86d4cb8b48984fffcfcfcfffcfcfcfff3f4f2fff6f6f5ffea9d9dffe06f6fffeca2a1fff7f7f6fff4f4f3fffcfcfcfffcfcfbffb38d87ffb5583ec000000000e9b96ee1abaca9ffdedfddfffcfcfcfffcfcfcfff5e4e3ffa07070ffdbababffa57170fff5e4e3fffcfcfcfffcfcfcffdddedbffabaca9ffe9b96ee700000000e9b96fe9f3eee6ff9a9a92ffdbdcdaffcacac9ffa48f8fff605b5bffa7a0a0ff625d5dffa58f8fffcacac9ffdadbd9ff9a9a92fff2eee5ffe9b96eec55555590716859dc6e6960ff5e5d5dff555555ff555555ff555555ffe2e1e1ffe2e1e1ffc7c6c6ff555555ff555555ff555555ff595958ff65615cff6e6659dfc8c8c874c8c7c69eccc5bbe5cac6c1fdc8c7c6ffa0a0a0ff808080ffe2e2e2ffc8c8c8ffa0a0a0ff666666ff808080ffa0a09fffc9c7c5fecbc6bfeec8c7c6a4555555765555559c555555c9555555eb555555fc555555ff555555ffc0c0c0ff9c9c9cff868686ff555555ff555555ff555555fe555555f7555555de555555ad"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowTranslations" verb="" label="Translate This Application..." hidden="0" pixtype="pixbuf" pixname="0000001000000010Abcbcb841bdc0baebbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbdc0baebbcbcb841000000000000000000000000bec0b9e7fafafafffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffafafaffbec0b9e7000000000000000000000000babdb6ffffffffff7ba5d2ff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff7ba5d2ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffff4371acff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff4371acffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5ffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffd5dde4ff7495c1ff3e6da7ff3969a7ea3768a68c2e68a216babdb6ffffffffffebedeaffebedeaffebedeaff3465a4ff7f9ec1ffd5dde1ffe5e9e8ffa0b5ceff4572abffa0bad9ffcfdeeeffbfd3e8ff80a2cbf93465a4ffbabdb6ffffffffffe8eae6ffe8eae6ffe8eae6ff3465a4ff97b2d3ff5680b3ff4975adff799ac4ffcedcedffc8daecff9dbcdeff9bbbddffcfdfefff3465a4ffbabdb6ffffffffffe4e7e2ffe4e7e2ffe4e7e2ff3465a4ffc6d8ebffd1dfefffe3ebf5ffd7e4f1ffbcd2e8ffa1bfdfff95b7dbff89afd7ffcfdfefff3465a4ffbabdb6ffffffffffe1e3deffe1e3deffe1e3deff3465a4ffc0d4e9ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc8daedff3465a4ffbdbfb8e7f3f4f2ffffffffffffffffffffffffff3465a4ffbbd1e7ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc2d6eaff3465a4ffbcbcb841bbbeb7ebbabdb6ffbabdb6ffbabdb6ff3465a4ffb5cde5ffa9c4e2ffc5d7ebffb9cfe7ffb8cee7ffc1d5eaffc1d5eaffb9cfe7ffbcd1e8ff3465a4ff00000000000000000000000000000000000000003465a4ffafc8e3ffafc8e4ffc7d8ecffc9daecffbacee5ff668dbdf43f6ea9f44876aef37a9dc8fa3465a4ff00000000000000000000000000000000000000003465a4ff6b92c0f8b2c9e2ffd0dfeeff97b3d4fd3c6ca7f43767a56f2b6aaa0c3868a7203868a69b3465a4ff00000000000000000000000000000000000000003764a6173768a5913a6aa7ec3b6ba7f13d6ca9bb3665a1260000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowBugs" verb="" label="Report a Problem" hidden="0" pixtype="pixbuf" pixname="0000001000000010A0000000000000000000000000000000000000000c4a10093c5a100f9c49d002700000000000000000000000000000000c2a30019c4a10098c4a000ffbfaa000c0000000000000000000000000000000000000000c6a300e8ecde8bfecaab15f5c7a20076aaaa0003c59e0042c6a400b8caaa16f7cdaf29ffc5a200be0000000000000000000000000000000000000000c5a10039d4b835f5fffffffffdfae4ffdec856f7c4a000ffd7be3ff4f3e9a9ffffffffffd0b42df6c39d002f0000000000000000000000000000000000000000c8a2009deee191fef7ea84fff2df3ffffcf8d6fffdfae8fffcf7d1fffaf3b7fff9f4d0ffc5a200d70000000000000000c4a000e2c5a205ffc9a811f8c5a201f6c7a50dfffdfbe8fff2de35ff0e0d01ff131104fff1dc26fff0d811fffaf3b9ffe1cc60f7c4a000630000000000000000c69f0028c9a912f6fffffffffffffffffefcedfff8ed90fff2db1dff2b2705ff332f07fff2db1dfff1da1afffffffdffc7a50dffc5a10039000000000000000000000000c6a30075ddc64ef6fdfadffff3dd27fff3dd22fff4de26ff48410cff554d0efff4de26fff3dd22fffaf2acfff7efbaffc9a912f5c4a100570000000000000000ff800002c6a301cef3e7a4fefaf09dfff5df2afff6e02fff655d15ff786d18fff6e02ffff5df2afff3dd26fffaf1a8ffffffffffd0b32bf8c5a200a40000000000000000c49f004accad24fffefbe7fff6e131fff7e237fff8e33cfff8e33cfff7e237fff6e131fff8eb7ffffefcecfff3e9aefecdae20fcc5a100d900000000b6920007c6a301daf5ebaffefaf1a0fff7e235fff8e43eff3a3510ff3a3510fff8e43efff7e235fffffefbffcaaa1affc8a401abc19f00250000000000000000c7a3009ce8d67afafffffffffefce9fffaef8dfff9e540ff3a3511ff3a3511fff9e540fff7e237fffdf8d0ffdfc858f7c5a200650000000000000000c4a2005ac7a40bffeada7efdddc653f4caaa1cfffefdf3fff8e546fff9e64afffdf4b2fffefdf1fffdf8cdfffcf7c8fffbf8dcffc7a401e2ff80000200000000c4a000ffc5a000f6c7a20283c49f003dc6a402d3f9f3c8fffaee8cfffefaddfff4eaacfec7a60fffddc650f4f3e9aaffffffffffd7bd3ef5c5a1004f00000000c6aa0009000000000000000000000000c6a10087f0e399fdffffffffe4d16cf9c7a302d6c6a30024c6a20047c7a403a9c9a508f4ccac21ffc4a000ff0000000000000000000000000000000000000000c5a00046d1b534fcd2b42df6c7a3029bb6920007000000000000000000000000b6920007c5a00053c5a000cdc39d002f00000000000000000000000000000000c49d000dc4a000ffc3a10051000000000000000000000000000000000000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowInfo" verb="" label="Get Help Online..." hidden="0" pixtype="pixbuf" pixname="0000001000000010A00000000dfbf6008e9b86e8de9b96eeae9b96ee1b57053bba41f1eeca60a09fea40202ffa60a09fea51f1eecb46e51bce9b96ee1e9b96eeae9b86e8ddfbf600800000000e9b96f8af0ce9afff2eee6ffa4a6a2ffbc9693ffedb8b7fffcececfffef9f9fffcebebffedb7b6ffbb9894ffa4a6a2fff2eee6fff0ce9affe9b96f8a00000000e9b96eecf2eee5ff9b9b93ffe9eae9fffefefefffce3e3fff9bbbbfff7ababfff9bbbbfffce3e3fffefefeffe8e9e8ff9b9b93fff2eee5ffe9b86eeb00000000e9b96ee7abaca9ffe8e8e7fffefefdfffcfcfcfff5e3e2fff16867fff16565fff16968fff5e3e2fffcfcfcfffdfdfdffe7e7e6ffabaca9ffe9b96ee600000000b5583ec0b89590fffdfdfdfffcfcfcfff3f4f2fff0f0efffe16d6cffd74343ffe17170fff1f1f0fff3f4f2fffcfcfcfffdfdfdffb88e8affb66c4db600000000a51f1eebe7a0a0fffbe0e0fff5e3e2fff0f1efffb6b8b4f49f3735ed9f2827cc9e3836edb8bab6f4f1f2f1fff5e3e2fffbdfdfffe69999ffa51f1eeb00000000a60909fef8cecefff9b9b9fff26e6dffdf7373ff9e3836eaffffff0100000000ffffff019f3534eae48281fff27373fff9b9b9fff6c6c6ffa60909fe00000000a40202fffad5d5fff7aaaafff27474ffda5353ff9f2928cc0000000000000000000000009f2928ccdc5e5efff37d7dfff7aaaafff9ceceffa40202ff00000000a60909fef5bfbffff8b8b8fff27473ffe58786ff9f3534eaffffff0100000000ffffff019e3836eae58f8efff37978fff8b8b8fff4b8b8ffa60909fe00000000a51f1eebe18888fffbddddfff5e3e2fff4f5f4ffbcbebbf59e3836eda02927cb9f3735edbec1bdf5f5f6f5fff5e3e2fffbdcdcffdf8181ffa51f1eeb00000000b86d4cb8b48984fffcfcfcfffcfcfcfff3f4f2fff6f6f5ffea9d9dffe06f6fffeca2a1fff7f7f6fff4f4f3fffcfcfcfffcfcfbffb38d87ffb5583ec000000000e9b96ee1abaca9ffdedfddfffcfcfcfffcfcfcfff5e4e3ffa07070ffdbababffa57170fff5e4e3fffcfcfcfffcfcfcffdddedbffabaca9ffe9b96ee700000000e9b96fe9f3eee6ff9a9a92ffdbdcdaffcacac9ffa48f8fff605b5bffa7a0a0ff625d5dffa58f8fffcacac9ffdadbd9ff9a9a92fff2eee5ffe9b96eec55555590716859dc6e6960ff5e5d5dff555555ff555555ff555555ffe2e1e1ffe2e1e1ffc7c6c6ff555555ff555555ff555555ff595958ff65615cff6e6659dfc8c8c874c8c7c69eccc5bbe5cac6c1fdc8c7c6ffa0a0a0ff808080ffe2e2e2ffc8c8c8ffa0a0a0ff666666ff808080ffa0a09fffc9c7c5fecbc6bfeec8c7c6a4555555765555559c555555c9555555eb555555fc555555ff555555ffc0c0c0ff9c9c9cff868686ff555555ff555555ff555555fe555555f7555555de555555ad"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowTranslations" verb="" label="Translate This Application..." hidden="0" pixtype="pixbuf" pixname="0000001000000010Abcbcb841bdc0baebbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbdc0baebbcbcb841000000000000000000000000bec0b9e7fafafafffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffafafaffbec0b9e7000000000000000000000000babdb6ffffffffff7ba5d2ff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff7ba5d2ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffff4371acff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff4371acffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5ffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffd5dde4ff7495c1ff3e6da7ff3969a7ea3768a68c2e68a216babdb6ffffffffffebedeaffebedeaffebedeaff3465a4ff7f9ec1ffd5dde1ffe5e9e8ffa0b5ceff4572abffa0bad9ffcfdeeeffbfd3e8ff80a2cbf93465a4ffbabdb6ffffffffffe8eae6ffe8eae6ffe8eae6ff3465a4ff97b2d3ff5680b3ff4975adff799ac4ffcedcedffc8daecff9dbcdeff9bbbddffcfdfefff3465a4ffbabdb6ffffffffffe4e7e2ffe4e7e2ffe4e7e2ff3465a4ffc6d8ebffd1dfefffe3ebf5ffd7e4f1ffbcd2e8ffa1bfdfff95b7dbff89afd7ffcfdfefff3465a4ffbabdb6ffffffffffe1e3deffe1e3deffe1e3deff3465a4ffc0d4e9ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc8daedff3465a4ffbdbfb8e7f3f4f2ffffffffffffffffffffffffff3465a4ffbbd1e7ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc2d6eaff3465a4ffbcbcb841bbbeb7ebbabdb6ffbabdb6ffbabdb6ff3465a4ffb5cde5ffa9c4e2ffc5d7ebffb9cfe7ffb8cee7ffc1d5eaffc1d5eaffb9cfe7ffbcd1e8ff3465a4ff00000000000000000000000000000000000000003465a4ffafc8e3ffafc8e4ffc7d8ecffc9daecffbacee5ff668dbdf43f6ea9f44876aef37a9dc8fa3465a4ff00000000000000000000000000000000000000003465a4ff6b92c0f8b2c9e2ffd0dfeeff97b3d4fd3c6ca7f43767a56f2b6aaa0c3868a7203868a69b3465a4ff00000000000000000000000000000000000000003764a6173768a5913a6aa7ec3b6ba7f13d6ca9bb3665a1260000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowBugs" verb="" label="Report a Problem" hidden="0" pixtype="pixbuf" pixname="0000001000000010A0000000000000000000000000000000000000000c4a10093c5a100f9c49d002700000000000000000000000000000000c2a30019c4a10098c4a000ffbfaa000c0000000000000000000000000000000000000000c6a300e8ecde8bfecaab15f5c7a20076aaaa0003c59e0042c6a400b8caaa16f7cdaf29ffc5a200be0000000000000000000000000000000000000000c5a10039d4b835f5fffffffffdfae4ffdec856f7c4a000ffd7be3ff4f3e9a9ffffffffffd0b42df6c39d002f0000000000000000000000000000000000000000c8a2009deee191fef7ea84fff2df3ffffcf8d6fffdfae8fffcf7d1fffaf3b7fff9f4d0ffc5a200d70000000000000000c4a000e2c5a205ffc9a811f8c5a201f6c7a50dfffdfbe8fff2de35ff0e0d01ff131104fff1dc26fff0d811fffaf3b9ffe1cc60f7c4a000630000000000000000c69f0028c9a912f6fffffffffffffffffefcedfff8ed90fff2db1dff2b2705ff332f07fff2db1dfff1da1afffffffdffc7a50dffc5a10039000000000000000000000000c6a30075ddc64ef6fdfadffff3dd27fff3dd22fff4de26ff48410cff554d0efff4de26fff3dd22fffaf2acfff7efbaffc9a912f5c4a100570000000000000000ff800002c6a301cef3e7a4fefaf09dfff5df2afff6e02fff655d15ff786d18fff6e02ffff5df2afff3dd26fffaf1a8ffffffffffd0b32bf8c5a200a40000000000000000c49f004accad24fffefbe7fff6e131fff7e237fff8e33cfff8e33cfff7e237fff6e131fff8eb7ffffefcecfff3e9aefecdae20fcc5a100d900000000b6920007c6a301daf5ebaffefaf1a0fff7e235fff8e43eff3a3510ff3a3510fff8e43efff7e235fffffefbffcaaa1affc8a401abc19f00250000000000000000c7a3009ce8d67afafffffffffefce9fffaef8dfff9e540ff3a3511ff3a3511fff9e540fff7e237fffdf8d0ffdfc858f7c5a200650000000000000000c4a2005ac7a40bffeada7efdddc653f4caaa1cfffefdf3fff8e546fff9e64afffdf4b2fffefdf1fffdf8cdfffcf7c8fffbf8dcffc7a401e2ff80000200000000c4a000ffc5a000f6c7a20283c49f003dc6a402d3f9f3c8fffaee8cfffefaddfff4eaacfec7a60fffddc650f4f3e9aaffffffffffd7bd3ef5c5a1004f00000000c6aa0009000000000000000000000000c6a10087f0e399fdffffffffe4d16cf9c7a302d6c6a30024c6a20047c7a403a9c9a508f4ccac21ffc4a000ff0000000000000000000000000000000000000000c5a00046d1b534fcd2b42df6c7a3029bb6920007000000000000000000000000b6920007c5a00053c5a000cdc39d002f00000000000000000000000000000000c49d000dc4a000ffc3a10051000000000000000000000000000000000000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowInfo" verb="" label="Get Help Online..." hidden="0" pixtype="pixbuf" pixname="0000001000000010A00000000dfbf6008e9b86e8de9b96eeae9b96ee1b57053bba41f1eeca60a09fea40202ffa60a09fea51f1eecb46e51bce9b96ee1e9b96eeae9b86e8ddfbf600800000000e9b96f8af0ce9afff2eee6ffa4a6a2ffbc9693ffedb8b7fffcececfffef9f9fffcebebffedb7b6ffbb9894ffa4a6a2fff2eee6fff0ce9affe9b96f8a00000000e9b96eecf2eee5ff9b9b93ffe9eae9fffefefefffce3e3fff9bbbbfff7ababfff9bbbbfffce3e3fffefefeffe8e9e8ff9b9b93fff2eee5ffe9b86eeb00000000e9b96ee7abaca9ffe8e8e7fffefefdfffcfcfcfff5e3e2fff16867fff16565fff16968fff5e3e2fffcfcfcfffdfdfdffe7e7e6ffabaca9ffe9b96ee600000000b5583ec0b89590fffdfdfdfffcfcfcfff3f4f2fff0f0efffe16d6cffd74343ffe17170fff1f1f0fff3f4f2fffcfcfcfffdfdfdffb88e8affb66c4db600000000a51f1eebe7a0a0fffbe0e0fff5e3e2fff0f1efffb6b8b4f49f3735ed9f2827cc9e3836edb8bab6f4f1f2f1fff5e3e2fffbdfdfffe69999ffa51f1eeb00000000a60909fef8cecefff9b9b9fff26e6dffdf7373ff9e3836eaffffff0100000000ffffff019f3534eae48281fff27373fff9b9b9fff6c6c6ffa60909fe00000000a40202fffad5d5fff7aaaafff27474ffda5353ff9f2928cc0000000000000000000000009f2928ccdc5e5efff37d7dfff7aaaafff9ceceffa40202ff00000000a60909fef5bfbffff8b8b8fff27473ffe58786ff9f3534eaffffff0100000000ffffff019e3836eae58f8efff37978fff8b8b8fff4b8b8ffa60909fe00000000a51f1eebe18888fffbddddfff5e3e2fff4f5f4ffbcbebbf59e3836eda02927cb9f3735edbec1bdf5f5f6f5fff5e3e2fffbdcdcffdf8181ffa51f1eeb00000000b86d4cb8b48984fffcfcfcfffcfcfcfff3f4f2fff6f6f5ffea9d9dffe06f6fffeca2a1fff7f7f6fff4f4f3fffcfcfcfffcfcfbffb38d87ffb5583ec000000000e9b96ee1abaca9ffdedfddfffcfcfcfffcfcfcfff5e4e3ffa07070ffdbababffa57170fff5e4e3fffcfcfcfffcfcfcffdddedbffabaca9ffe9b96ee700000000e9b96fe9f3eee6ff9a9a92ffdbdcdaffcacac9ffa48f8fff605b5bffa7a0a0ff625d5dffa58f8fffcacac9ffdadbd9ff9a9a92fff2eee5ffe9b96eec55555590716859dc6e6960ff5e5d5dff555555ff555555ff555555ffe2e1e1ffe2e1e1ffc7c6c6ff555555ff555555ff555555ff595958ff65615cff6e6659dfc8c8c874c8c7c69eccc5bbe5cac6c1fdc8c7c6ffa0a0a0ff808080ffe2e2e2ffc8c8c8ffa0a0a0ff666666ff808080ffa0a09fffc9c7c5fecbc6bfeec8c7c6a4555555765555559c555555c9555555eb555555fc555555ff555555ffc0c0c0ff9c9c9cff868686ff555555ff555555ff555555fe555555f7555555de555555ad"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowTranslations" verb="" label="Translate This Application..." hidden="0" pixtype="pixbuf" pixname="0000001000000010Abcbcb841bdc0baebbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbabdb6ffbdc0baebbcbcb841000000000000000000000000bec0b9e7fafafafffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffafafaffbec0b9e7000000000000000000000000babdb6ffffffffff7ba5d2ff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff729fcfff7ba5d2ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffff4371acff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff3667a6ff4371acffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5fff6f7f5ffffffffffbabdb6ff000000000000000000000000babdb6fffffffffff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1fff2f4f1ffffffffffbabdb6ff000000000000000000000000babdb6ffffffffffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffeff0eeffd5dde4ff7495c1ff3e6da7ff3969a7ea3768a68c2e68a216babdb6ffffffffffebedeaffebedeaffebedeaff3465a4ff7f9ec1ffd5dde1ffe5e9e8ffa0b5ceff4572abffa0bad9ffcfdeeeffbfd3e8ff80a2cbf93465a4ffbabdb6ffffffffffe8eae6ffe8eae6ffe8eae6ff3465a4ff97b2d3ff5680b3ff4975adff799ac4ffcedcedffc8daecff9dbcdeff9bbbddffcfdfefff3465a4ffbabdb6ffffffffffe4e7e2ffe4e7e2ffe4e7e2ff3465a4ffc6d8ebffd1dfefffe3ebf5ffd7e4f1ffbcd2e8ffa1bfdfff95b7dbff89afd7ffcfdfefff3465a4ffbabdb6ffffffffffe1e3deffe1e3deffe1e3deff3465a4ffc0d4e9ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc8daedff3465a4ffbdbfb8e7f3f4f2ffffffffffffffffffffffffff3465a4ffbbd1e7ffa9c4e2ffc5d7ebffb9cfe7ffadc7e3ffa1bfdfff95b7dbff89afd7ffc2d6eaff3465a4ffbcbcb841bbbeb7ebbabdb6ffbabdb6ffbabdb6ff3465a4ffb5cde5ffa9c4e2ffc5d7ebffb9cfe7ffb8cee7ffc1d5eaffc1d5eaffb9cfe7ffbcd1e8ff3465a4ff00000000000000000000000000000000000000003465a4ffafc8e3ffafc8e4ffc7d8ecffc9daecffbacee5ff668dbdf43f6ea9f44876aef37a9dc8fa3465a4ff00000000000000000000000000000000000000003465a4ff6b92c0f8b2c9e2ffd0dfeeff97b3d4fd3c6ca7f43767a56f2b6aaa0c3868a7203868a69b3465a4ff00000000000000000000000000000000000000003764a6173768a5913a6aa7ec3b6ba7f13d6ca9bb3665a1260000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'

(gnome-panel:30963): Bonobo-WARNING **: Serious exception on node_set '$invalid path to XML user interface element' of '<menuitem name="LpShowBugs" verb="" label="Report a Problem" hidden="0" pixtype="pixbuf" pixname="0000001000000010A0000000000000000000000000000000000000000c4a10093c5a100f9c49d002700000000000000000000000000000000c2a30019c4a10098c4a000ffbfaa000c0000000000000000000000000000000000000000c6a300e8ecde8bfecaab15f5c7a20076aaaa0003c59e0042c6a400b8caaa16f7cdaf29ffc5a200be0000000000000000000000000000000000000000c5a10039d4b835f5fffffffffdfae4ffdec856f7c4a000ffd7be3ff4f3e9a9ffffffffffd0b42df6c39d002f0000000000000000000000000000000000000000c8a2009deee191fef7ea84fff2df3ffffcf8d6fffdfae8fffcf7d1fffaf3b7fff9f4d0ffc5a200d70000000000000000c4a000e2c5a205ffc9a811f8c5a201f6c7a50dfffdfbe8fff2de35ff0e0d01ff131104fff1dc26fff0d811fffaf3b9ffe1cc60f7c4a000630000000000000000c69f0028c9a912f6fffffffffffffffffefcedfff8ed90fff2db1dff2b2705ff332f07fff2db1dfff1da1afffffffdffc7a50dffc5a10039000000000000000000000000c6a30075ddc64ef6fdfadffff3dd27fff3dd22fff4de26ff48410cff554d0efff4de26fff3dd22fffaf2acfff7efbaffc9a912f5c4a100570000000000000000ff800002c6a301cef3e7a4fefaf09dfff5df2afff6e02fff655d15ff786d18fff6e02ffff5df2afff3dd26fffaf1a8ffffffffffd0b32bf8c5a200a40000000000000000c49f004accad24fffefbe7fff6e131fff7e237fff8e33cfff8e33cfff7e237fff6e131fff8eb7ffffefcecfff3e9aefecdae20fcc5a100d900000000b6920007c6a301daf5ebaffefaf1a0fff7e235fff8e43eff3a3510ff3a3510fff8e43efff7e235fffffefbffcaaa1affc8a401abc19f00250000000000000000c7a3009ce8d67afafffffffffefce9fffaef8dfff9e540ff3a3511ff3a3511fff9e540fff7e237fffdf8d0ffdfc858f7c5a200650000000000000000c4a2005ac7a40bffeada7efdddc653f4caaa1cfffefdf3fff8e546fff9e64afffdf4b2fffefdf1fffdf8cdfffcf7c8fffbf8dcffc7a401e2ff80000200000000c4a000ffc5a000f6c7a20283c49f003dc6a402d3f9f3c8fffaee8cfffefaddfff4eaacfec7a60fffddc650f4f3e9aaffffffffffd7bd3ef5c5a1004f00000000c6aa0009000000000000000000000000c6a10087f0e399fdffffffffe4d16cf9c7a302d6c6a30024c6a20047c7a403a9c9a508f4ccac21ffc4a000ff0000000000000000000000000000000000000000c5a00046d1b534fcd2b42df6c7a3029bb6920007000000000000000000000000b6920007c5a00053c5a000cdc39d002f00000000000000000000000000000000c49d000dc4a000ffc3a10051000000000000000000000000000000000000000000000000000000000000000000000000"/>
' to '/popups/button3/LaunchpadItems'


I didn't use to have this problem. Any idea as to why is this and how to solve it?, is it important or can I still go on with my stuff without worrying about it too much?

---

