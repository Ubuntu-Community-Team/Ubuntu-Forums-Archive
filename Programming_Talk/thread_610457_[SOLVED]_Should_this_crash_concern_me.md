---
title: "[SOLVED] Should this crash concern me?"
date: 2007-11-12
forum: Programming Talk
---

### Post by jordanmthomas on 2007-11-12
Hello, I am writing a java game and I get this when I start it.  It appears to be java itself crashing.  Oddly, though, my program loads up and works as expected.  Should this "crash" concern me or should I just ignore it?

```
[jordan@ttyfscker src]$ java Screen
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cca767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7cca8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xab708a8d]
#3 /opt/java/jre/lib/i386/xawt/libmawt.so [0xab81864e]
#4 /opt/java/jre/lib/i386/xawt/libmawt.so [0xab7f6f97]
#5 /opt/java/jre/lib/i386/xawt/libmawt.so [0xab7f7248]
#6 /opt/java/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xab7f754f]
#7 [0xb5c9366e]
#8 [0xb5c8bedd]
#9 [0xb5c8bedd]
#10 [0xb5c89243]
#11 /opt/java/jre/lib/i386/client/libjvm.so [0x620bc6d]
#12 /opt/java/jre/lib/i386/client/libjvm.so [0x630a828]
#13 /opt/java/jre/lib/i386/client/libjvm.so [0x620bb00]
#14 /opt/java/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x62619bb]
#15 /opt/java/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7ca496d]
#16 [0xb5c9366e]
#17 [0xb5c8bd77]
#18 [0xb5c89243]
#19 /opt/java/jre/lib/i386/client/libjvm.so [0x620bc6d]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cca767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7cca81e]
#2 /usr/lib/libX11.so.6 [0xab707e08]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xab6feb76]
#4 /opt/java/jre/lib/i386/xawt/libmawt.so [0xab7f6249]
#5 /opt/java/jre/lib/i386/xawt/libmawt.so [0xab7f6495]
#6 /opt/java/jre/lib/i386/xawt/libmawt.so [0xab7f72f9]
#7 /opt/java/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xab7f754f]
#8 [0xb5c9366e]
#9 [0xb5c8bedd]
#10 [0xb5c8bedd]
#11 [0xb5c89243]
#12 /opt/java/jre/lib/i386/client/libjvm.so [0x620bc6d]
#13 /opt/java/jre/lib/i386/client/libjvm.so [0x630a828]
#14 /opt/java/jre/lib/i386/client/libjvm.so [0x620bb00]
#15 /opt/java/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x62619bb]
#16 /opt/java/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7ca496d]
#17 [0xb5c9366e]
#18 [0xb5c8bd77]
#19 [0xb5c89243]

```

---

### Post by jordanmthomas on 2007-11-13
bump (sorry)
(well, kind of sorry...not sorry enough to not do it)  :)

---

### Post by jordanmthomas on 2007-11-14
Well, can someone tell me if you think this is a problem with xcb-xlib or a problem with java at least?

---

### Post by Sef on 2007-11-14
Moved to Programming Talk.

---

### Post by jordanmthomas on 2007-11-14
Thank you, I suppose this is a better place for it.

---

### Post by smartbei on 2007-11-15
I don't know much about/of Java, but if your program is relatively simple, you may want to back it up and then start cutting off parts and running it, until you see that the error disappears. When it does, the last part you cut off probably was the problem.

You may want to try a simple hello world program first, just to see if it happens in all programs. If it still "Locking assertion failure.  Backtrace: ..."['s], the problem probably isn't in your code.

---

### Post by jordanmthomas on 2007-11-15
Hmm, I will try that.  It's not really a very simple program, but I think I can cut parts out pretty easily.  Also, I didn't mention this, but I don't get any kind of crash if I run the program in Windows or in OSX.

Good idea, though, and I will give it a try in the morning.  When we demonstrate the program we'll be using an OSX box so it's not mission-critical or anything, just something that is bothering me.

---

### Post by jordanmthomas on 2007-11-26
This turned out to not be a problem with my code, but with libmawt.so and being statically linked to Xinerama.
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373)

I fixed it with a (probably not such a good idea) sed hack to remove the check (posting it here so if I need to undo it I'll be able to find what I did  :) ).
```
sed -i 's/XINERAMA/FAKEEXTN/g'  usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so
```

---

### Post by karrotcake on 2007-11-27
Thanks mate, your a lifesaver.
I had the same problem when running Netbeans after upgrading to hardy. The only difference was the location of my jre (as I have the sdk), but other than that it worked perfectly.

---

### Post by jordanmthomas on 2007-11-27
Woops, I actually posted the wrong thing.  I've got the sdk too, and the bug report had two things.  I just copied the wrong one I think (and I had to change some other things because the location was different for me too, I really just wanted to post what I did with sed so I'd remember).

Anyway, glad it helped.  This was really annoying.

---

### Post by arcanus on 2008-04-11
This bug actually just resurfaced in 1.6.0_05. Just to bumb the thread back up in the hierarchy (Firefox on-the-fly spell checking ftw!).

---

### Post by th3james on 2008-04-16
Yep, i'm having this problem in hardy with eclipse, anyone know if there is a bug report for this yet?

---

### Post by aaroncampbell on 2008-05-07
I'm getting a similar error, every time I try to install or run Zend Studio (a Java Application).  I'm actually running Kubuntu Hardy.
```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2841767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb28418b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xaa9481bd]
#3 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so [0xaaabcf8a]
#4 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so [0xaaa62706]
#5 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so [0xaaa6294d]
#6 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xaaa62b58]
#7 [0xb28ceb28]
#8 [0xb28c8aeb]
#9 [0xb28c8aeb]
#10 [0xb28c61b4]
#11 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so [0xb76d17ec]
#12 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so [0xb7894828]
#13 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so [0xb76d161f]
#14 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb772ed1d]
#15 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb73e02cd]
#16 [0xb28ce458]
#17 [0xb28c8a14]
#18 [0xb28c61b4]
#19 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so [0xb76d17ec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2841767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb284181e]
#2 /usr/lib/libX11.so.6 [0xaa947518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xaa93e0a6]
#4 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so [0xaaa61593]
#5 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so [0xaaa61824]
#6 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so [0xaaa62a94]
#7 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xaaa62b58]
#8 [0xb28ceb28]
#9 [0xb28c8aeb]
#10 [0xb28c8aeb]
#11 [0xb28c61b4]
#12 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so [0xb76d17ec]
#13 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so [0xb7894828]
#14 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so [0xb76d161f]
#15 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb772ed1d]
#16 /tmp/install.dir.13959/Linux/resource/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb73e02cd]
#17 [0xb28ce458]
#18 [0xb28c8a14]
#19 [0xb28c61b4]
Warning: Cannot convert string "-b&h-lucidasans-medium-r-normal-sans-*-140-*-*-p-*-iso8859-1" to type FontStruct

```

I'm including my xorg.conf, because maybe it's related to [this other thread](http://ubuntuforums.org/showthread.php?t=782607):
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1680x1050"
    EndSubSection
EndSection

```

I'm also using nVidia drivers like that thread says, and that box is checked in the hardware drivers box.

---

### Post by aaroncampbell on 2008-05-07
There is a problem with Eclipse as well, and it gives this log file.

---

### Post by aaroncampbell on 2008-05-08
By removing GCJ, and then removing the directories in my ~ that had settings for the two programs, I was able to get them working.  I still get the JAVA errors, but at least they work.

---

### Post by maddog39 on 2008-05-20
Im currently running ArchLinux and I do my Java development without an IDE per-say however my Java applications are showing these same exact errors for me too. Although they do not cause crashes I still see them.

---

### Post by rcastellow on 2008-06-13
I had a similar issue, and hopefully this helps someone.  First I made sure that I had Java 6 downloaded and installed on my 64 bit Ubuntu 8.04 OS. 

I noticed the install script scans my hardware for jvms as early as 1.5.  Here's the section of netbeans-6.1_m1-linux.sh that contains that information...

setJavaCompatibilityProperties_0() {
JAVA_COMP_VERSION_MIN="1.6.0_03"
JAVA_COMP_VERSION_MAX=""
JAVA_COMP_VENDOR=""
JAVA_COMP_OSNAME=""
JAVA_COMP_OSARCH=""
}

Notice I changed JAVA_COMP_VERSION_MIN to 1.6XXX.  With the default settings the NetBeans install was picking up 1.5.  I was getting Assertion errors and after using the sed option in this thread a blank welcome screen.  After changing JAVA_COMP_VERSION_MIN the installer picked up 1.6 and ran fine.  W00t! W00t!

---

### Post by vclark on 2008-08-08
Trying to run iReports and getting the same error. I ran the sed command and the error went away, but iReports still won't run. Just comes up blank.

---

