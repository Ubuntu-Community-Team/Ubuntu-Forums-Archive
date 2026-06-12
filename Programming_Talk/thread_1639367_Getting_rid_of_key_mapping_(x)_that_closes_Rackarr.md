---
title: "Getting rid of key mapping (x) that closes Rackarrack"
date: 2010-12-06
forum: Programming Talk
---

### Post by GraysonPeddie on 2010-12-06
Hi. Call me lazy, but when I am working with [Rakarrack](http://rakarrack.sourceforge.net/) (Ubuntu 10.10) while playing musical notes in ZynAddSubFX's Virtual Keyboard using my QWERTY, when I press the "x" key, I forgot to switch back to ZynAddSubFX to play the key. Instead, pressing "x" in my QWERTY keyboard closes the program and this gets extremely annoying and I'm used to doing Alt+F4.

So, is there a place to start looking at a source code for keyboard mappings? I know this is a lot to ask, though.

---

### Post by transmogrifox on 2010-12-06
If you build it yourself from source and would like to do your own customization, you can make a very simple modification:

In my current build from git, line 1016 of rakarrack.cxx:
```
 {"Exit", 0x78,  (Fl_Callback*)RKRGUI::cb_salir, 0, 0, FL_NORMAL_LABEL, 0, 14, 7},
```

Change the 0x78 to NULL, like this:
```
 {"Exit", NULL,  (Fl_Callback*)RKRGUI::cb_salir, 0, 0, FL_NORMAL_LABEL, 0, 14, 7},
```

then make, sudo make install, and the keyboard shortcut is out of your hair.

As far as the line number goes you are better to use your text editor's find function to locate that line of code, because the line number will change every time even a minor modification is made to the GUI...so the line number is probably not helpful for locating that line.  It only took a couple iterations for me to find this line by searching "salir".

This an FLTK option. If you install FLUID, then you can open the rakarrack.fl, browse to the menu object in the GUI, find the Exit entry and delete shortcut "X", save, write code...

I'm not sure what will happen upstream.  I guess it depends whether there are other people who use that shortcut and want it to stay. It's really easy for us to make the keybinding do anything you want...but for now it's probably best if you compile yourself and do a one-off to suit your own preferences.  That's one way a person can leverage the freedom of free open source software ;)  

As a final note, you can extend the same concept to customize your keybindings if you want.  It's probably easiest to use FLUID to do that.

---

### Post by GraysonPeddie on 2010-12-07
> **transmogrifox said:**
> This an FLTK option. If you install FLUID, then you can open the rakarrack.fl, browse to the menu object in the GUI, find the Exit entry and delete shortcut "X", save, write code...

I'm not sure what will happen upstream.  I guess it depends whether there are other people who use that shortcut and want it to stay. It's really easy for us to make the keybinding do anything you want...but for now it's probably best if you compile yourself and do a one-off to suit your own preferences.  That's one way a person can leverage the freedom of free open source software ;)

I used locate in the command line to find rakarrack.fl but the file is not in my computer.

---

### Post by transmogrifox on 2010-12-07
> **GraysonPeddie said:**
> I used locate in the command line to find rakarrack.fl but the file is not in my computer.

It won't be on your computer unless you have downloaded the source code:
[http://rakarrack.sourceforge.net/dl.html](http://rakarrack.sourceforge.net/dl.html)

I think I too quickly assumed you are experienced building software from source code since you were asking how to modify the source.  If you use a binary distributed with Ubuntu, you're stuck with this behavior. There is no easy way to modify the binary to remove this shortcut.  I'm one of the Rakarrack developers, so I could easily make the change upstream, but it would take probably 6 months for it to trickle down to you.  In addition, I'm not yet certain whether it's a good change to spring on the entire community.  Either way, the easiest route for you is to download the source code and compile your own custom build.

Your best way to approach this is to uninstall the Ubuntu version of Rakarrack, download the source code, edit rakarrack.cxx as I explained above, then compile the program yourself.  Other perks you get if you track with current development include fast access to bug fixes, new features, etc.  For example, I'm working on a Risset filter and sidechain compressor.  Debian/Ubuntu probably won't get those for several months, but people who compile from git can try it in the same minute we add it to the source code :) 

If you haven't compiled anything from source code before, you will have some things to install to prepare your computer for this at first, but the process is pretty easy once you have all the tools installed for compiling programs.

Here is some help for compiling rakarrack from source:
Link to part I of a three part video tutorial.
[http://www.youtube.com/watch?v=ZfdqjReVD_s](http://www.youtube.com/watch?v=ZfdqjReVD_s)
It demonstrates how to prepare your machine and compile from source code on Debian Lenny.  Ubuntu will be very similar, and the differences will be minor enough that the video will be relevant.
Make sure you follow the links to parts II and III.

What the video doesn't show is what you need to set up your development environment.  You will need g++, make, and possibly linux-headers-2.6-686 (likely it's already installed...but search in Synaptic to make sure), autotools-dev and maybe something else that doesn't come to mind at the moment.  I think everything else is covered in the videos.

When you get to the ./configure part, anything missing will be reported, so look for errors before attempting the make command.  Configure will tell you if you don't have something Rakarrack needs to be able to compile on your system.  Search for key words in Synaptic and install anything that looks related, try to configure again, and keep doing that until configure passes successfully.

If you're going through the trouble of compiling from source, I highly recommend using the git repository (this is what the instructions on the videos show you how to do).

Once you have it from git, you can check for updates by going into the rakarrack directory and:
```
$git pull 
```
Then make the modifications I explained above to rakarrack.cxx and compile and install again:
```

$./autogen.sh
$./configure
$make
$sudo make install
(honestly you can do sudo make install and the make utility will automatically invoke everything before that if needed).
```

If you aren't familiar with programming and only want to make the change, I recommend modifying the **rakarrack.cxx** file.  This is the actual code that is compiled, so there are no more steps than editing that file for yourself, compile the program, and install.

---

### Post by Vox754 on 2010-12-07
> **transmogrifox said:**
> ... I'm one of the Rakarrack developers, ...

I like Rakarrack... well, at least it works, unlike Creox.

I don't want to be an *** but, I think Rakarrack is freaking ugly! Oh, you are using FLTK!

Being serious, I like things that work, so props to you guys. Nevertheless, I hope somebody in the future can put the huge effort to design the interface in GTK+ or Qt. It would have support from the whole GNOME and KDE desktops, and it would look more professional.

Given that the internal code that does the effects processing should be shared libraries, I would assume that it shouldn't be to much problem to design an interface. But I don't really know.

Keep up the good work.

---

### Post by transmogrifox on 2010-12-07
> **Vox754 said:**
>  Nevertheless, I hope somebody in the future can put the huge effort to design the interface in GTK+ or Qt. It would have support from the whole GNOME and KDE desktops, and it would look more professional.

:D  Yes, us too.  At the moment the active Rakarrack team is two people.  Neither of us are very skilled at GUI design, so we definitely have an unfilled need.  On the up side, FLTK is very fast and light, so it's great from the perspective of somebody who uses it but doesn't spend much time looking at it.  FLTK doesn't eat much of the processing power for animating pretty knobs and contour/depth rendering on refresh.

However, the program design does completely separate GUI from effects engine (actually there is a mode to run rakarrack headless...you don't even need to start the X server to use it if you have a MIDI controller).  If somebody made the GUI's, you could theoretically choose the GUI you want at program start time without any change to how rakarrack processes effects.  It is relatively trivial to interface all the internal parameters.

All we need is an awesome GUI designer to volunteer the time and effort to make a killer GUI ;)  There's the rub...

---

### Post by GraysonPeddie on 2010-12-08
I'm familiar with C# and the basics of C/C++, but not when it comes to API of Linux and I'm used to compiling MythTV and Asterisk PBX in my Ubuntu Server with no need to modifying the source code.

I will give it a try when I boot over to Ubuntu desktop. Thanks.

Update: Okay, I don't seem to have problems with rakarrack that I got from Ubuntu repository (I'm running Ubuntu 10.10), but when downloaded from git and compiled from source, I get a "Cannot open this bank file" upon launching rakarrack. Plus, have a look at this:

```
rakarrack 0.6.2 - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
Enhanced3DNow! detected
SSE2 detected
zombified - calling shutdown handler
X I/O errorX I/O error


```

I was scrolling through presets in the bank while playing the sound and when I chose "Goin through a phase" or "Surf's Up," Rakarrack disappears in a whim. For one time, I get this:

```
grayson@htpc:~$ /usr/local/bin/rakarrack 

rakarrack 0.6.2 - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
Enhanced3DNow! detected
SSE2 detected
zombified - calling shutdown handler
X_SetModifierMapping: BadLength (poly request too large or internal Xlib length error) 0x4400004
XRequest.163: BadRequest (invalid request code or no such operation) 0x4400004
X_SetModifierMapping: BadLength (poly request too large or internal Xlib length error) 0x4400004
^C

```

Even without the error message, I had to kill it in the gnome-terminal.

Rakarrack seems to be less buggy when downloaded from the Ubuntu's repository compared to building Rakarrack from source.

I know I should start a new thread, but I thought I should add something here about the errors I've been encountering.

---

### Post by transmogrifox on 2010-12-08
:D Ha! Then we're equals.  I don't know anything about Windows API's.

The errors you reported sounds much like problems stemming from conflicts between two versions (ubuntu versus compiled).  It is important to know this, because I'm sure we can add some checks when reading configurations and presets from other versions to prevent things like this.

On my system current development version from git is generally more stable, so don't be quick to throw in the towel.  The other nice thing about git is if we get the problem identified there will be a fix very soon.  Then for you is only "git pull", compile and install again.

Anyway, before getting too in-depth, let's try the obvious:

Rename ~/.fltk/rakarrack.sf.net/rakarrack.prefs to rakarrack.prefs.bak (if you decide to settle back on the version distributed with Ubuntu, then rename rakarrack.prefs.bak to rakarrack.prefs if you want to be able to restore your settings from before).  Upon first start of compiled rakarrack, it will create a new rakarrack.prefs file which will be relevant to that version (this user file is the most likely cause of problems--this we have seen reported elsewhere).

If renaming the rakarrack.prefs file doesn't help, then the best test is to sudo apt-get remove --purge rakarrack, then go to the source directory and do sudo make uninstall, then do sudo make install to make sure you have a truly clean install from source.

If you get the same errors after renaming the rakarrack.prefs and removing the Ubuntu version, then we can start looking for bugs elsewhere.

Normally you should be perfectly safe doing what you did, installing from source and issuing /usr/local/bin/rakarrack, so isn't anything fundamentally wrong with not removing the Ubuntu rakarrack.  However, if removing the Ubuntu rakarrack fixes the errors you had with the compiled version, it may point to something else for us to investigate if there is a conflict.

Finally, if you want a quick and less troublesome fix, you can download the source tarball from sourceforge with the same version you have in Ubuntu (I think it has version 0.5.1).  You can compile and install that and it will be exactly the same thing, only you can add your minor tweak to the source code before you compile it.  There will not be conflicts between the two config files nor presets/data files in that case.

---

### Post by GraysonPeddie on 2010-12-08
I renamed rakarrack.prefs and that makes the error message go away when I start rakarrack. Simply doing apt-get purge rakarrack does not seem to remove rakarrack.prefs, it seems.

I'll give rakarrack a test and see how it goes.

Update: Okay, I'm getting a memory dump:

```
grayson@htpc:~/Downloads/rakarrack$ /usr/local/bin/rakarrack

rakarrack 0.6.2 - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
Enhanced3DNow! detected
SSE2 detected
cannot read server event (Connection reset by peer)
zombified - calling shutdown handler
*** glibc detected *** /usr/local/bin/rakarrack: double free or corruption (fasttop): 0x00000000017e55e0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f2013e694b6]
/lib/libc.so.6(cfree+0x73)[0x7f2013e6fc83]
/usr/lib/libX11.so.6(+0x4a362)[0x7f2016757362]
/usr/lib/libX11.so.6(_XReply+0x140)[0x7f20167579b0]
/usr/lib/libX11.so.6(XInternAtom+0xa4)[0x7f2016739c84]
/usr/lib/libX11.so.6(+0x8548f)[0x7f201679248f]
/usr/lib/libX11.so.6(_XcmsInitScrnInfo+0x69)[0x7f201679bac9]
/usr/lib/libX11.so.6(XcmsDefaultCCC+0x75)[0x7f201678e075]
/usr/lib/libX11.so.6(XcmsCreateCCC+0x38)[0x7f201678e0e8]
/usr/lib/libX11.so.6(+0x8d71e)[0x7f201679a71e]
/usr/lib/libX11.so.6(XcmsCCCOfColormap+0x2d)[0x7f201679a77d]
/usr/lib/libX11.so.6(XParseColor+0x3e)[0x7f201673fb7e]
/usr/lib/libfltk.so.1.1(_Z14fl_parse_colorPKcRhS1_S1_+0x4d)[0x7f2016abbbad]
/usr/lib/libfltk.so.1.1(_Z14fl_draw_pixmapPKPKcii8Fl_Color+0x15c)[0x7f2016ac73cc]
/usr/lib/libfltk.so.1.1(_ZN9Fl_Pixmap4drawEiiiiii+0x29a)[0x7f2016a9feda]
/usr/lib/libfltk.so.1.1(_Z7fl_drawPKciiii8Fl_AlignPFvS0_iiiEP8Fl_Imagei+0x20d)[0x7f2016ac4f9d]
/usr/lib/libfltk.so.1.1(_Z7fl_drawPKciiii8Fl_AlignP8Fl_Imagei+0x7b)[0x7f2016ac567b]
/usr/lib/libfltk.so.1.1(_Z15fl_normal_labelPK8Fl_Labeliiii8Fl_Align+0x6c)[0x7f2016aca4dc]
/usr/lib/libfltk.so.1.1(_ZNK9Fl_Widget10draw_labelEiiii8Fl_Align+0x7f)[0x7f2016aca2af]
/usr/lib/libfltk.so.1.1(_ZNK8Fl_Group10draw_childER9Fl_Widget+0x3e)[0x7f2016a8a29e]
/usr/lib/libfltk.so.1.1(_ZN8Fl_Group13draw_childrenEv+0x52)[0x7f2016a8a362]
/usr/lib/libfltk.so.1.1(_ZN9Fl_Window4drawEv+0x53)[0x7f2016ab8d23]
/usr/lib/libfltk.so.1.1(_ZN2Fl5flushEv+0xb3)[0x7f2016a76e33]
/usr/lib/libfltk.so.1.1(_ZN2Fl4waitEd+0x10d)[0x7f2016a7707d]
/usr/lib/libfltk.so.1.1(_ZN2Fl4waitEv+0x1d)[0x7f2016a7719d]
/usr/lib/libfltk.so.1.1(+0x7e75b)[0x7f2016ac175b]
/usr/lib/libfltk.so.1.1(_Z10fl_messagePKcz+0xc4)[0x7f2016ac1ea4]
/usr/local/bin/rakarrack[0x46ba33]
/usr/lib/libjack.so.0(+0x7225)[0x7f2014eec225]
/usr/lib/libjack.so.0(+0x7f40)[0x7f2014eecf40]
/lib/libpthread.so.0(+0x7971)[0x7f2015807971]
/lib/libc.so.6(clone+0x6d)[0x7f2013ed894d]
======= Memory map: ========
00400000-004de000 r-xp 00000000 08:06 8622                               /usr/local/bin/rakarrack
006dd000-006de000 r--p 000dd000 08:06 8622                               /usr/local/bin/rakarrack
006de000-006e7000 rw-p 000de000 08:06 8622                               /usr/local/bin/rakarrack
006e7000-006e8000 rw-p 00000000 00:00 0 
011d9000-0195d000 rw-p 00000000 00:00 0                                  [heap]
7f2008000000-7f2008021000 rw-p 00000000 00:00 0 
7f2008021000-7f200c000000 ---p 00000000 00:00 0 
7f200e93c000-7f200e988000 r--p 00000000 08:06 271281                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
7f200e988000-7f200ea17000 r--p 00000000 08:06 271277                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f200ea17000-7f200ea18000 ---p 00000000 00:00 0 
7f200ea18000-7f200ea98000 rw-p 00000000 00:00 0 
7f200ea98000-7f200eb33000 r--p 00000000 08:06 271278                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f200eb33000-7f200eb5b000 rw-p 00000000 00:00 0 
7f200eb5b000-7f200eb60000 r-xp 00000000 08:06 396077                     /usr/lib/libXfixes.so.3.1.0
7f200eb60000-7f200ed5f000 ---p 00005000 08:06 396077                     /usr/lib/libXfixes.so.3.1.0
7f200ed5f000-7f200ed60000 r--p 00004000 08:06 396077                     /usr/lib/libXfixes.so.3.1.0
7f200ed60000-7f200ed61000 rw-p 00005000 08:06 396077                     /usr/lib/libXfixes.so.3.1.0
7f200ed61000-7f200ed78000 r-xp 00000000 08:06 279184                     /lib/libnsl-2.12.1.so
7f200ed78000-7f200ef77000 ---p 00017000 08:06 279184                     /lib/libnsl-2.12.1.so
7f200ef77000-7f200ef78000 r--p 00016000 08:06 279184                     /lib/libnsl-2.12.1.so
7f200ef78000-7f200ef79000 rw-p 00017000 08:06 279184                     /lib/libnsl-2.12.1.so
7f200ef79000-7f200ef7b000 rw-p 00000000 00:00 0 
7f200ef7b000-7f200efbb000 r-xp 00000000 08:06 263711                     /lib/libdbus-1.so.3.5.2
7f200efbb000-7f200f1bb000 ---p 00040000 08:06 263711                     /lib/libdbus-1.so.3.5.2
7f200f1bb000-7f200f1bc000 r--p 00040000 08:06 263711                     /lib/libdbus-1.so.3.5.2
7f200f1bc000-7f200f1bd000 rw-p 00041000 08:06 263711                     /lib/libdbus-1.so.3.5.2
7f200f1bd000-7f200f1c6000 r-xp 00000000 08:06 263843                     /lib/libwrap.so.0.7.6
7f200f1c6000-7f200f3c5000 ---p 00009000 08:06 263843                     /lib/libwrap.so.0.7.6
7f200f3c5000-7f200f3c6000 r--p 00008000 08:06 263843                     /lib/libwrap.so.0.7.6
7f200f3c6000-7f200f3c7000 rw-p 00009000 08:06 263843                     /lib/libwrap.so.0.7.6
7f200f3c7000-7f200f3c8000 rw-p 00000000 00:00 0 
7f200f3c8000-7f200f3d6000 r-xp 00000000 08:06 396083                     /usr/lib/libXi.so.6.1.0
7f200f3d6000-7f200f5d6000 ---p 0000e000 08:06 396083                     /usr/lib/libXi.so.6.1.0
7f200f5d6000-7f200f5d7000 r--p 0000e000 08:06 396083                     /usr/lib/libXi.so.6.1.0
7f200f5d7000-7f200f5d8000 rw-p 0000f000 08:06 396083                     /usr/lib/libXi.so.6.1.0
7f200f5d8000-7f200f5dc000 r-xp 00000000 08:06 263841                     /lib/libuuid.so.1.3.0
7f200f5dc000-7f200f7db000 ---p 00004000 08:06 263841                     /lib/libuuid.so.1.3.0
7f200f7db000-7f200f7dc000 r--p 00003000 08:06 263841                     /lib/libuuid.so.1.3.0
7f200f7dc000-7f200f7dd000 rw-p 00004000 08:06 263841                     /lib/libuuid.so.1.3.0
7f200f7dd000-7f200f827000 r-xp 00000000 08:06 392429                     /usr/lib/libpulsecommon-0.9.21.so
7f200f827000-7f200fa27000 ---p 0004a000 08:06 392429                     /usr/lib/libpulsecommon-0.9.21.so
7f200fa27000-7f200fa28000 r--p 0004a000 08:06 392429                     /usr/lib/libpulsecommon-0.9.21.so
7f200fa28000-7f200fa29000 rw-p 0004b000 08:06 392429                     /usr/lib/libpulsecommon-0.9.21.so
7f200fa29000-7f200fa2c000 r-xp 00000000 08:06 397011                     /usr/lib/libxcb-atom.so.1.0.0
7f200fa2c000-7f200fc2c000 ---p 00003000 08:06 397011                     /usr/lib/libxcb-atom.so.1.0.0
7f200fc2c000-7f200fc2d000 r--p 00003000 08:06 397011                     /usr/lib/libxcb-atom.so.1.0.0
7f200fc2d000-7f200fc2e000 rw-p 00004000 08:06 397011                     /usr/lib/libxcb-atom.so.1.0.0
7f200fc2e000-7f200fc33000 r-xp 00000000 08:06 396103                     /usr/lib/libXtst.so.6.1.0
7f200fc33000-7f200fe33000 ---p 00005000 08:06 396103                     /usr/lib/libXtst.so.6.1.0
7f200fe33000-7f200fe34000 r--p 00005000 08:06 396103                     /usr/lib/libXtst.so.6.1.0Aborted
grayson@htpc:~/Downloads/rakarrack$ 

```

---

### Post by transmogrifox on 2010-12-08
> **GraysonPeddie said:**
> I renamed rakarrack.prefs and that makes the error message go away when I start rakarrack. Simply doing apt-get purge rakarrack does not seem to remove rakarrack.prefs, it seems.

I'll give rakarrack a test and see how it goes.

Update: Okay, I'm getting a memory dump:


Yeah, rakarrack.prefs is a file created by the program, and aptitude does not remove user data.  You will notice this with almost all programs.

As for your memory dump, it's hard to tell what exactly is triggering this without doing more in-depth debugging.

Do you know how to do a backtrace in gdb?  This can give us a name of function calls, line numbers... basically a little more information than the memory dump. 

Strange thing to me is your output:
```
*** glibc detected *** /usr/local/bin/rakarrack: double free or corruption (fasttop):
```
Here's a thread that seems to show a similar error:
[http://ubuntuforums.org/showthread.php?t=175050](http://ubuntuforums.org/showthread.php?t=175050)

Try this in the terminal before you attempt to run rakarrack:
```
export MALLOC_CHECK_=0
```
If that allows you to run the program, then there will be some ideas of things I can look at.  From what I read online, this seems to be most often related to multithreading applications.  I may have to chat with Holborn and/or go plumbing parts of the code I haven't looked at very much.  Thanks for the info.

Unfortunately this simple question turned into a can of worms.

---

### Post by GraysonPeddie on 2010-12-09
I might have a bunch of questions as my knowledge of C++/Linux is my weakness and .net Framework, C#, and ASP.net are my strengths when it comes to debugging in Visual Studio 2005-2010.

I will try out export MALLOC_CHECK_=0 during the daytime.

---

### Post by transmogrifox on 2010-12-09
> **GraysonPeddie said:**
> I might have a bunch of questions as my knowledge of C++/Linux is my weakness and .net Framework, C#, and ASP.net are my strengths when it comes to debugging in Visual Studio 2005-2010.

I will try out export MALLOC_CHECK_=0 during the daytime.

Yeah, gdb is a different bear.  Takes some time reading the documentation to go really in depth (setting break points and all that).

Usually all we end up needing from users experiencing a crash is to run a backtrace.  There are various ways to do it, but what I have found the easiest is,
```
$cd path/to/rakarrack/src
$gdb rakarrack
>run
...wait until it crashes
>bt
```

then it will spit out a backtrace.  I honestly prefer to debug by inserting printf statements (or cout if using a more formal C++).
Usually that is enough to point me to possible causes.  Probably stems from the C & C++ classes I had in college.  For us it was vi text editor on Red Hat (not even syntax highlighting...was a real pain but it taught good programming habits).

---

