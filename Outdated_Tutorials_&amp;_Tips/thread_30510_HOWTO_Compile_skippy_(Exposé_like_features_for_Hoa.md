---
title: "HOWTO: Compile skippy (Exposé like features for Hoary)"
date: 2005-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by pjack76 on 2005-04-29
1. Download skippy from:

[http://thegraveyard.org/files/skippy-0.5.0.tar.bz2](http://thegraveyard.org/files/skippy-0.5.0.tar.bz2)

This HOWTO was written for skippy version 0.5.0, hopefully it will work for future versions too.

2. Untar the skippy source code into a directory:

$ tar -xjf skippy-0.5.0.tar.bz2

3. Switch to the untarred directory

$ cd skippy-0.5.0.tar.bz2

4. Install imlib2-dev, libxft-dev and libxmu-dev, since skippy needs them to compile:

$ sudo apt-get install libimlib2-dev libxmu-dev libxft-dev

5. Edit the Makefile so that it won't try to bind to Xinerama. 

$ nano Makefile

You want to insert a # at the beginning of lines 10 and 11, so that they look like this:

    #CFLAGS += -DXINERAMA
    #LDFLAGS += -lXext -lXinerama

6. Compile the software:

$ make

7. Install the executable:

$ sudo make install

8. Copy the default config file to your home directory:

$ cp skippyrc-default ~/.skippyrc

9. Edit the default config file so that it uses Scroll Lock instead of F11 as the hotkey. I recommend this, because many Ubuntu applications use F11 (for instance, OpenOffice Writer uses F11 to display the Stylist, which is a very useful feature). On the other hand, I don't think the Scroll Lock EVER had a use. :)

$ nano ~/.skippyrc

Change line 24 to read:

     keysym=Scroll_Lock

10. Launch skippy:

$ skippy

11. Press Scroll Lock to see scaled-down versions of all of your windows. Some people have complained about skippy's performance, but it works very quickly on my ancient laptop. 

Note that this version of skippy does not update the scaled-down windows in real-time.

Hope this helps,

-Paul

[Edited to add extra dependency.]

---

### Post by TravisNewman on 2005-04-29
note-- for skippy-xd (NOT regular skippy), you have to be running xcompmgr for this to work, and you also have to have the -dev libs for xdamage, xfixes, xrender, and xcomposite installed. At least I did. ;)

This thing is SLOW. But I'm hoping it works out the kinks later on.

EDIT: My post probably came off wrong-- the original instructions work fine, but if you want the version that renders in real time, you have to do the above.

---

### Post by vnbuddy2002 on 2005-04-29
For me, I really doubt that skippy would be usable if it depends on xcompmgr. With xcompmgr alone, my computer (PIV 2.4ghz) could barely handle it. With skippy, I am wonder how slow it would be.

However, if you hadn't brought it up, I wouldn't know that there is an Exposé-like utility. :) thank u!

---

### Post by Insanely on 2005-04-29
I love expose in Mac OS X but makes things easier on Linux.

---

### Post by didit on 2005-04-29
for me i am fine with kompose. Though, it is not as eye candy as expose and friends but it is usable.

-dyt

---

### Post by Jeconais on 2005-04-29
If you get make errors, you will also need to:

sudo apt-get install libxmu-dev

---

### Post by TravisNewman on 2005-04-29
Skippy doesn't depend on xcompmgr, skippy-xd does. Two different releases :)

---

### Post by pjack76 on 2005-04-29
[QUOTE=Jeconais]If you get make errors, you will also need to:

sudo apt-get install libxmu-dev[/QUOTE]

Whoops!  Thanks for catching that. I should have triple-checked the dependencies... I've edited the original post to include this. Thanks!

-Paul

---

### Post by bored2k on 2005-04-29
Ok Skippy performance is not bad on my P4. Actually not bad at all, but I get compile errors on skippy-xd. Last errors were:
> /usr/X11R6/include/X11/Xft/Xft.h:468: error: syntax error before '*' token
/usr/X11R6/include/X11/Xft/Xft.h:479: warning: type defaults to `int' in declaration of `XftGlyphSpec'
/usr/X11R6/include/X11/Xft/Xft.h:479: error: syntax error before '*' token
/usr/X11R6/include/X11/Xft/Xft.h:500: warning: type defaults to `int' in declaration of `XftGlyphFontSpec'
/usr/X11R6/include/X11/Xft/Xft.h:500: error: syntax error before '*' token
In file included from tooltip.c:20:
skippy.h:31:39: X11/extensions/Xcomposite.h: No such file or directory
skippy.h:32:36: X11/extensions/Xdamage.h: No such file or directory
skippy.h:33:35: X11/extensions/Xfixes.h: No such file or directory
In file included from skippy.h:63,
                 from tooltip.c:20:
clientwin.h:41: error: syntax error before "Damage"
clientwin.h:41: warning: no semicolon at end of struct or union
clientwin.h:50: error: conflicting types for `x'
/usr/X11R6/include/X11/Xft/Xft.h:101: error: previous declaration of `x'
clientwin.h:50: error: conflicting types for `y'
/usr/X11R6/include/X11/Xft/Xft.h:102: error: previous declaration of `y'
clientwin.h:51: error: syntax error before '}' token
clientwin.h:51: warning: ISO C does not allow extra `;' outside of a function
make: *** [skippy-xd] Error 1 
reb@noir:~/Files/skippy-0.5.0$[/QUOTE]

---

### Post by bored2k on 2005-04-29
[QUOTE=panickedthumb]Skippy doesn't depend on xcompmgr, skippy-xd does. Two different releases :)[/QUOTE]
 If I run skippy without xcompmgr, no matter what I have opened, i always get 3 terminals:
[[IMG]http://img182.echo.cx/img182/7654/why7bs.th.png[/IMG]](http://img182.echo.cx/my.php?image=why7bs.png)

**Edit** : This is not the case in XFCE. Here it runs w/o the xcompmgr turned on. *XFCE with the ball ... three pointer!*

---

### Post by deepbluepixel on 2005-04-29
hi 

I get a BIG error and I dont know why, im new to linux but I did follow your steps.
I know "xtf" is missing or something but not how to fix it...
can someone help me??

root@########:/home/pete/Downloads/skippy-0.5.0 # make
gcc -I/usr/X11R6/include `imlib2-config --cflags` `pkg-config xft --cflags` -g -pedantic -Wall -o skippy skippy.c wm.c dlist.c mainwin.c clientwin.c layout.c focus.c config.c tooltip.c -L/usr/X11R6/lib -lX11 -lm `imlib2-config --libs` `pkg-config xft --libs`
Package xft was not found in the pkg-config search path.
Perhaps you should add the directory containing `xft.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xft' found
Package xft was not found in the pkg-config search path.
Perhaps you should add the directory containing `xft.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xft' found
In file included from skippy.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from skippy.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from skippy.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
skippy.c: In function `skippy_run':
skippy.c:166: error: dereferencing pointer to incomplete type
In file included from wm.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from wm.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from wm.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
wm.c:318: error: syntax error before '*' token
wm.c:320: warning: return type defaults to `int'
wm.c: In function `wm_get_window_title':
wm.c:322: error: `FcChar8' undeclared (first use in this function)
wm.c:322: error: (Each undeclared identifier is reported only once
wm.c:322: error: for each function it appears in.)
wm.c:322: error: `ret' undeclared (first use in this function)
wm.c:323: warning: ISO C89 forbids mixed declarations and code
wm.c:353: error: syntax error before ')' token
In file included from dlist.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from dlist.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from dlist.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
In file included from mainwin.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from mainwin.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from mainwin.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
In file included from clientwin.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from clientwin.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from clientwin.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
clientwin.c: In function `clientwin_handle':
clientwin.c:285: error: `FcChar8' undeclared (first use in this function)
clientwin.c:285: error: (Each undeclared identifier is reported only once
clientwin.c:285: error: for each function it appears in.)
clientwin.c:285: error: `win_title' undeclared (first use in this function)
In file included from layout.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from layout.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from layout.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
In file included from focus.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from focus.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from focus.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
In file included from config.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from config.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from config.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
In file included from tooltip.c:20:
skippy.h:28:25: X11/Xft/Xft.h: No such file or directory
In file included from skippy.h:64,
                 from tooltip.c:20:
wm.h:70: error: syntax error before '*' token
wm.h:70: warning: type defaults to `int' in declaration of `wm_get_window_title'wm.h:70: error: ISO C forbids data definition with no type or storage class
In file included from skippy.h:70,
                 from tooltip.c:20:
tooltip.h:27: error: syntax error before "XftFont"
tooltip.h:27: warning: no semicolon at end of struct or union
tooltip.h:28: warning: type defaults to `int' in declaration of `draw'
tooltip.h:28: error: ISO C forbids data definition with no type or storage classtooltip.h:29: error: syntax error before "color"
tooltip.h:29: warning: type defaults to `int' in declaration of `color'
tooltip.h:29: error: ISO C forbids data definition with no type or storage classtooltip.h:31: error: syntax error before "extents"
tooltip.h:31: warning: type defaults to `int' in declaration of `extents'
tooltip.h:31: error: ISO C forbids data definition with no type or storage classtooltip.h:37: error: syntax error before '*' token
tooltip.h:37: warning: type defaults to `int' in declaration of `text'
tooltip.h:37: error: ISO C forbids data definition with no type or storage classtooltip.h:39: error: syntax error before '}' token
tooltip.h:39: warning: ISO C does not allow extra `;' outside of a function
tooltip.h:44: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.h:44: error: syntax error before '*' token
tooltip.c: In function `tooltip_destroy':
tooltip.c:28: error: dereferencing pointer to incomplete type
tooltip.c:29: error: dereferencing pointer to incomplete type
tooltip.c:30: error: dereferencing pointer to incomplete type
tooltip.c:31: warning: implicit declaration of function `XftFontClose'
tooltip.c:31: error: dereferencing pointer to incomplete type
tooltip.c:31: error: dereferencing pointer to incomplete type
tooltip.c:32: error: dereferencing pointer to incomplete type
tooltip.c:33: warning: implicit declaration of function `XftDrawDestroy'
tooltip.c:33: error: dereferencing pointer to incomplete type
tooltip.c:34: error: dereferencing pointer to incomplete type
tooltip.c:35: warning: implicit declaration of function `XftColorFree'
tooltip.c:35: error: dereferencing pointer to incomplete type
tooltip.c:36: error: dereferencing pointer to incomplete type
tooltip.c:37: error: dereferencing pointer to incomplete type
tooltip.c:38: error: dereferencing pointer to incomplete type
tooltip.c:39: error: dereferencing pointer to incomplete type
tooltip.c:40: error: dereferencing pointer to incomplete type
tooltip.c:40: error: dereferencing pointer to incomplete type
tooltip.c:42: error: dereferencing pointer to incomplete type
tooltip.c:43: error: dereferencing pointer to incomplete type
tooltip.c:43: error: dereferencing pointer to incomplete type
tooltip.c:43: error: dereferencing pointer to incomplete type
tooltip.c:45: error: dereferencing pointer to incomplete type
tooltip.c:46: error: dereferencing pointer to incomplete type
tooltip.c:46: error: dereferencing pointer to incomplete type
tooltip.c:46: error: dereferencing pointer to incomplete type
tooltip.c:47: error: dereferencing pointer to incomplete type
tooltip.c:48: error: dereferencing pointer to incomplete type
tooltip.c:48: error: dereferencing pointer to incomplete type
tooltip.c:48: error: dereferencing pointer to incomplete type
tooltip.c: In function `tooltip_create':
tooltip.c:62: error: invalid application of `sizeof' to an incomplete type
tooltip.c:66: error: dereferencing pointer to incomplete type
tooltip.c:67: error: dereferencing pointer to incomplete type
tooltip.c:68: error: dereferencing pointer to incomplete type
tooltip.c:69: error: dereferencing pointer to incomplete type
tooltip.c:70: error: dereferencing pointer to incomplete type
tooltip.c:71: error: dereferencing pointer to incomplete type
tooltip.c:72: error: dereferencing pointer to incomplete type
tooltip.c:78: error: dereferencing pointer to incomplete type
tooltip.c:79: error: dereferencing pointer to incomplete type
tooltip.c:81: error: dereferencing pointer to incomplete type
tooltip.c:87: error: dereferencing pointer to incomplete type
tooltip.c:88: error: dereferencing pointer to incomplete type
tooltip.c:90: error: dereferencing pointer to incomplete type
tooltip.c:95: error: dereferencing pointer to incomplete type
tooltip.c:96: error: dereferencing pointer to incomplete type
tooltip.c:99: error: dereferencing pointer to incomplete type
tooltip.c:105: error: dereferencing pointer to incomplete type
tooltip.c:112: warning: implicit declaration of function `XftColorAllocName'
tooltip.c:112: error: dereferencing pointer to incomplete type
tooltip.c:118: error: dereferencing pointer to incomplete type
tooltip.c:120: error: dereferencing pointer to incomplete type
tooltip.c:120: warning: implicit declaration of function `XftDrawCreate'
tooltip.c:120: error: dereferencing pointer to incomplete type
tooltip.c:121: error: dereferencing pointer to incomplete type
tooltip.c:128: error: dereferencing pointer to incomplete type
tooltip.c:128: warning: implicit declaration of function `XftFontOpenName'
tooltip.c:129: error: dereferencing pointer to incomplete type
tooltip.c:136: error: dereferencing pointer to incomplete type
tooltip.c:136: error: dereferencing pointer to incomplete type
tooltip.c:136: error: dereferencing pointer to incomplete type
tooltip.c: At top level:
tooltip.c:142: warning: type defaults to `int' in declaration of `FcChar8'
tooltip.c:142: error: syntax error before '*' token
tooltip.c: In function `tooltip_map':
tooltip.c:144: error: `tt' undeclared (first use in this function)
tooltip.c:144: error: (Each undeclared identifier is reported only once
tooltip.c:144: error: for each function it appears in.)
tooltip.c:146: warning: implicit declaration of function `XftTextExtents8'
tooltip.c:146: error: `len' undeclared (first use in this function)
tooltip.c:149: error: `x' undeclared (first use in this function)
tooltip.c:149: error: `y' undeclared (first use in this function)
tooltip.c:154: error: `FcChar8' undeclared (first use in this function)
tooltip.c:154: error: syntax error before ')' token
tooltip.c: In function `tooltip_move':
tooltip.c:166: error: dereferencing pointer to incomplete type
tooltip.c:166: error: dereferencing pointer to incomplete type
tooltip.c:166: error: dereferencing pointer to incomplete type
tooltip.c:167: error: dereferencing pointer to incomplete type
tooltip.c:167: error: dereferencing pointer to incomplete type
tooltip.c:167: error: dereferencing pointer to incomplete type
tooltip.c:170: error: dereferencing pointer to incomplete type
tooltip.c:170: error: dereferencing pointer to incomplete type
tooltip.c:170: error: dereferencing pointer to incomplete type
tooltip.c:171: error: dereferencing pointer to incomplete type
tooltip.c:171: error: dereferencing pointer to incomplete type
tooltip.c:171: error: dereferencing pointer to incomplete type
tooltip.c:174: error: dereferencing pointer to incomplete type
tooltip.c:174: error: dereferencing pointer to incomplete type
tooltip.c: In function `tooltip_unmap':
tooltip.c:180: error: dereferencing pointer to incomplete type
tooltip.c:180: error: dereferencing pointer to incomplete type
tooltip.c:181: error: dereferencing pointer to incomplete type
tooltip.c:182: error: dereferencing pointer to incomplete type
tooltip.c:183: error: dereferencing pointer to incomplete type
tooltip.c:184: error: dereferencing pointer to incomplete type
tooltip.c: In function `tooltip_handle':
tooltip.c:190: error: dereferencing pointer to incomplete type
tooltip.c:195: error: dereferencing pointer to incomplete type
tooltip.c:195: error: dereferencing pointer to incomplete type
tooltip.c:196: warning: implicit declaration of function `XftDrawString8'
tooltip.c:196: error: dereferencing pointer to incomplete type
tooltip.c:196: error: dereferencing pointer to incomplete type
tooltip.c:196: error: dereferencing pointer to incomplete type
tooltip.c:196: error: dereferencing pointer to incomplete type
tooltip.c:196: error: dereferencing pointer to incomplete type
tooltip.c:196: error: dereferencing pointer to incomplete type
tooltip.c:196: error: dereferencing pointer to incomplete type
tooltip.c:196: error: dereferencing pointer to incomplete type
make: *** [skippy] Error 1

---

### Post by pjack76 on 2005-04-29
[QUOTE=deepbluepixel]hi 

I get a BIG error and I dont know why, im new to linux but I did follow your steps.
I know "xtf" is missing or something but not how to fix it...
can someone help me??

[/QUOTE]

Argh! I'm so sorry. My instructions don't list the dependencies correctly. What you need to do, in addition to installing xmu and imlib2 libraries headers, is you also need to install the xft library headers.

Some quick background since you're new: The source code for a program almost always requires libraries to be installed. The source code "links" to those libraries by including something called a header file. By default, Ubuntu won't install header files for you, because Ubuntu assumes that you're not a developer, you're an end user. This seems like a reasonable assumption to me, but it's a pain when an end user really does have to compile something. 

The header files are usually stored in packages named "*-dev". Once you install the dev package, you should be able to compile against the library. Also, libraries (like imlib2 or xft) have package names that start with "lib", to distinguish them from runnable programs (like skippy).

So, since we need to compile against xft, we want to install the libxft-dev package:

$ sudo apt-get install libxft-dev

Sorry about that. :( This is why .deb packages were invented, to keep track of source code AND dependencies at the same time. The good news is, there will be a package for skippy in Breezy, so you won't have to compile from scratch anymore...

-Paul

---

### Post by bored2k on 2005-04-29
[QUOTE=pjack76]Argh! I'm so sorry. My instructions don't list the dependencies correctly. What you need to do, in addition to installing xmu and imlib2 libraries headers, is you also need to install the xft library headers.

Some quick background since you're new: The source code for a program almost always requires libraries to be installed. The source code "links" to those libraries by including something called a header file. By default, Ubuntu won't install header files for you, because Ubuntu assumes that you're not a developer, you're an end user. This seems like a reasonable assumption to me, but it's a pain when an end user really does have to compile something. 

The header files are usually stored in packages named "*-dev". Once you install the dev package, you should be able to compile against the library. Also, libraries (like imlib2 or xft) have package names that start with "lib", to distinguish them from runnable programs (like skippy).

So, since we need to compile against xft, we want to install the libxft-dev package:

$ sudo apt-get install libxft-dev

Sorry about that. :( This is why .deb packages were invented, to keep track of source code AND dependencies at the same time. The good news is, there will be a package for skippy in Breezy, so you won't have to compile from scratch anymore...

-Paul[/QUOTE]
 I get more or less the same errors when I try skippy-xd. And I do have it installed.
libxft-dev is already the newest version.

Skippy still owns though :D. XFCE+Skippy = Bliss

---

### Post by deepbluepixel on 2005-04-29
IT WORKS!!!

thx..

---

### Post by pjack76 on 2005-04-29
[QUOTE=bored2k]I get more or less the same errors when I try skippy-xd. And I do have it installed.
libxft-dev is already the newest version.

Skippy still owns though :D. XFCE+Skippy = Bliss[/QUOTE]

Well, the instructions are only for skippy, not for skippy-xd. I don't know how to compile skippy-xd, and I think it requires reconfiguring your X Server too... Plus everyone says it's slow. So, I'm not motivated to figure it all out, since skippy works, and works quickly, and is (relatively) simple to install...

It would be nice for the windows to update in real-time, but honestly, when I use skippy I just want to select a new window quickly, so it's okay if the window display is a few seconds out-of-date.

-Paul

---

### Post by bored2k on 2005-04-30
[http://thegraveyard.org/skippy.php](http://thegraveyard.org/skippy.php)
> 
There are also two or three modifiers you can use with the hotkey: hold Control and Skippy (not used in Skippy-XD) will update the snapshots of all the windows. Hold Mod1 (aka the alt key) and skippy will only show the windows of the currently focused window's window group (like, all of gimp's windows, or all of kopete's windows), and if Skippy or Skippy-XD is compiled with Xinerama support and you have several heads, hold shift while pressing the hotkey to make it show the windows on all heads.

These modifiers are not working here :-(
Anyone got this working? os the skippy-xd? I'm really ditching the panel for good here.

---

### Post by bored2k on 2005-04-30
Ok I e-mailed the developer and he told me how it's done:
> You have to hold the modifiers when you press the hotkey. Like Alt+F11.

Hyriand

No need for skippy-xd now :D

---

### Post by oars on 2005-04-30
Skippy won't run  :-? 

This is the error I get:

```
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  89
  Current serial number in output stream:  89
```

---

### Post by Dromio on 2005-04-30
I can't get skippy-xd to compile.  I've made sure I have all the dependencies that panickedthumb listed, but I get the following when I make:

```

gcc -I/usr/X11R6/include `pkg-config xft xrender xcomposite xdamage xfixes --cflags` -g -pedantic -Wall -o skippy-xd skippy.c wm.c dlist.c mainwin.c clientwin.c layout.c focus.c config.c tooltip.c -L/usr/X11R6/lib -lX11 -lm `pkg-config xft xrender xcomposite xdamage xfixes --libs`
mainwin.c: In function `mainwin_create':
mainwin.c:170: error: `event_base' undeclared (first use in this function)
mainwin.c:170: error: (Each undeclared identifier is reported only once
mainwin.c:170: error: for each function it appears in.)
make: *** [skippy-xd] Error 1

```

I'm probably missing something stupid, but I can't figure it out.  Regular skippy compiles fine.  Any suggestions?

---

### Post by pjack76 on 2005-05-01
[QUOTE=Dromio]I can't get skippy-xd to compile.  I've made sure I have all the dependencies that panickedthumb listed, but I get the following when I make:

```

gcc -I/usr/X11R6/include `pkg-config xft xrender xcomposite xdamage xfixes --cflags` -g -pedantic -Wall -o skippy-xd skippy.c wm.c dlist.c mainwin.c clientwin.c layout.c focus.c config.c tooltip.c -L/usr/X11R6/lib -lX11 -lm `pkg-config xft xrender xcomposite xdamage xfixes --libs`
mainwin.c: In function `mainwin_create':
mainwin.c:170: error: `event_base' undeclared (first use in this function)
mainwin.c:170: error: (Each undeclared identifier is reported only once
mainwin.c:170: error: for each function it appears in.)
make: *** [skippy-xd] Error 1

```

I'm probably missing something stupid, but I can't figure it out.  Regular skippy compiles fine.  Any suggestions?[/QUOTE]

Well, yes. Re-enable Xinerama support in the Makefile, and install xinerama-dev, then try to recompile.

There is a bug in skippy-xd code, it's defining that event_base variable in a #ifdef XINERMA section -- so if Xinerama support isn't enabled, that variable never gets declared.

I'll send an email to the maker of skippy with a patch, but until then, re-enable Xinerma and try again...

-Paul

---

### Post by optimistic on 2005-05-01
1.- $ wget [http://www.debian.org.hk/~glee/deb/skippy/skippy_0.5.0-1_i386.deb](http://www.debian.org.hk/~glee/deb/skippy/skippy_0.5.0-1_i386.deb)

2.- $ sudo dpkg -i skippy_0.5.0-1_i386.deb

3.- run skippy 

4.- F11

5.- :P

---

### Post by sidetrak on 2005-05-02
Well, I've been able to compile skippy and it seems to work fine.  It takes about 2-3 seconds for it to work.  The only problem is that firefox seems to cover up all the windows, even if firefox is in the background.  I'm a moron with linux so I can only blame voodoo magic for this effect, does anyone here have an idea whats the deal?  Thanks for a great tutorial.  In this screenshot firefox is open, as well as a terminal, a nautilus folder and mplayer.  Thanks again!

[[IMG]http://img32.echo.cx/img32/7580/screenshot6yw.th.png[/IMG]](http://img32.echo.cx/my.php?image=screenshot6yw.png)

---

### Post by Dromio on 2005-05-02
Thank you pjack, that worked.

Looks neat.  Too bad it crashed my xserver :(

---

### Post by Dali on 2005-05-02
I had difficulty compiling, but was able to install the .deb that was provided recently...works as advertised!

I'd love to see skippy able to show windows from all workspaces, and to eliminate the overlapping window issue...but other than that it's pretty good!

Cheers,

Dali

---

### Post by Kazuhiro on 2005-05-08
Any one able to provide some help with this error?

Thanks.


X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Resource id in failed request:  0x0
  Serial number of failed request:  111
  Current serial number in output stream:  113

---

### Post by krusbjorn on 2005-05-08
[QUOTE=sidetrak]Well, I've been able to compile skippy and it seems to work fine.  It takes about 2-3 seconds for it to work.  The only problem is that firefox seems to cover up all the windows, even if firefox is in the background.  I'm a moron with linux so I can only blame voodoo magic for this effect, does anyone here have an idea whats the deal?  Thanks for a great tutorial.  In this screenshot firefox is open, as well as a terminal, a nautilus folder and mplayer.  Thanks again!

[[IMG]http://img32.echo.cx/img32/7580/screenshot6yw.th.png[/IMG]](http://img32.echo.cx/my.php?image=screenshot6yw.png)[/QUOTE]

i have that problem too. anyone know how to solve this?

---

### Post by stubby on 2005-05-15
[QUOTE=optimistic]1.- $ wget [http://www.debian.org.hk/~glee/deb/skippy/skippy_0.5.0-1_i386.deb](http://www.debian.org.hk/~glee/deb/skippy/skippy_0.5.0-1_i386.deb)

2.- $ sudo dpkg -i skippy_0.5.0-1_i386.deb

3.- run skippy 

4.- F11

5.- :P[/QUOTE]

When I try to run skippy, i get the error
```
WARNING: Couldn't load config file '/home/stubby/.skippyrc'
``` 
I used the deb file to install

---

### Post by kvidell on 2005-05-17
Just to get this thing moving again;
Anyone find a fix for the latency issue?
When I hit F11 it cycles through all the windows (about 2 or 3 seconds on each, very slow in my terminals workspace as I have many terminals there) in my current workspace, then pops them in to the Expose` layout.

Any ideas yet?
- Kev

---

### Post by jonrkc on 2005-05-20
I switched over to Ubuntu a few days ago from Mandriva (Mandrake) 10.1, and kept all my Mandriva stuff just in case.  I'd been enjoying skippy on Mandriva, and missed it, at least playing with it, in Ubuntu.  

I thought I'd take a chance and see if I could just copy what looked like the essential stuff for skippy over from the Mandriva setup to Ubuntu.  After adding a couple of libraries that it wanted, which I also just copied over from Mandriva, skippy works just fine, in fact noticeably better than with Mandriva, I think because Ubuntu is faster.  It gets windows mixed up less, so far, than with Mandriva.

Sidetrack commented on the Firefox window having problems.  I suspect it's because it's the same class as Thunderbird--Gecko rendering--and skippy can't always sort those out very well.  But it's doing OK so far here, and I'm highly pleased that I was able to save it!

I've posted a screenshot at [www.jonrkc.com/my_images/skippy_at_work_in_Ubuntu.png](www.jonrkc.com/my_images/skippy_at_work_in_Ubuntu.png)

---

### Post by sethmahoney on 2005-05-20
[QUOTE=stubby]When I try to run skippy, i get the error
```
WARNING: Couldn't load config file '/home/stubby/.skippyrc'
``` 
I used the deb file to install[/QUOTE]

I'm getting the same error, followed by:
```
X Error of failed request:  BadAccess (attempt to access private resource denied)
```

---

### Post by jonrkc on 2005-05-21
[QUOTE=sethmahoney]I'm getting the same error, followed by:
```
X Error of failed request:  BadAccess (attempt to access private resource denied)
```[/QUOTE]
I got both the messages, too, after transfering most of the files I could find from my other system.  I then was able to find my old skippyrc file and copy it and that fixed it.  I suspect that if you just do 
```

touch ~/.skippyrc

```
it will satisfy skippy.  I haven't verified this yet, though.
EDIT: A few minutes later.  Nope, that won't work.  Still get the same message with an empty .skippyrc.file.  So here's a good one you can cut and paste and name .skippyrc; it came with the program as I got it, and I only modified the hotkey from F12 to scroll, the degree of translucency, and the color of the borders.  You can use any key within reason as hotkey.

```

# Copy this to ~/.skippyrc and edit it to your liking
#
# Notes:
#
# - keysym can be anything XStringToKeysym can handle
#   (like F11, KP_Enter or implementation specific keysyms)
#
# - colors can be anything XAllocNamedColor can handle
#   (like "black" or "#000000")
#
# - distance is a relative number, and is scaled according to the scale
#   factor applied to windows
#
# - fonts are Xft font descriptions
#
# - booleans are "true" or anything but "true" (-> false)
#
# - opacity is an integer in the range of 0-255
#
# - brighness is a floating point number (with 0.0 as neutral)
#

[general]
keysym = Scroll_Lock
distance = 50
useNETWMFullscreen = true
ignoreSkipTaskbar = false

[xinerama]
showAll = false

[normal]
brightness = 0.0
tint = white
opacity = 100
border = gray33

[highlight]
brightness = 0.05
tint = #d0d0ff
opacity = 255
border = #d0d0ff

[tooltip]
show = false
border = black
background = #e0e0ff
text = yellow
font = fixed-11:weight=bold

```

Use that file and you should be in business!

---

### Post by sethmahoney on 2005-05-22
Blaaaaaargh!  I'm still gettin the same error.  Thanks for the help attempt, though!

---

### Post by jonrkc on 2005-05-22
[QUOTE=sethmahoney]Blaaaaaargh!  I'm still gettin the same error.  Thanks for the help attempt, though![/QUOTE]
Did you set ownership and permission OK on the file?  

```

cd ~
sudo chown [username]:[username] ./.skippyrc
sudo chmod u+rxw ./.skippyrc

```

That's about all I can think of right now...

Hope you will get it to work.  I really like using skippy.

---

### Post by sethmahoney on 2005-05-22
[QUOTE=jonrkc]Did you set ownership and permission OK on the file? [/QUOTE]

I shouldn't need to, should I?  I used my own username to create the file, no sudo or anything.  I'll try, though.

---

### Post by sethmahoney on 2005-05-30
Okay, finally got a chance to try setting ownership/permission on .skippyrc, and no luck.  Still doesn't want to run, same error.  : /

---

### Post by jonrkc on 2005-05-30
[QUOTE=sethmahoney]Okay, finally got a chance to try setting ownership/permission on .skippyrc, and no luck.  Still doesn't want to run, same error.  : /[/QUOTE]
 I'm sorry it's taking so long to get Skippy domesticated.  You might want to go to the homepage for Skippy at [http://thegraveyard.org/skippy.php](http://thegraveyard.org/skippy.php) and download the tar'd version and compile it...  Or go to some of the other links at the bottom of that page and see if you can pick up any clues.  I'm mystified that it works for me and not for some other people who installed it basically the same way.  The only thing I can think of is that the .deb package is different in contents from the .rpm (as I recall) that I used when I was still using Mandrake/Mandriva.  I just copied everything that seemed related to Skippy over from my Mandriva installation when I switched to Ubuntu, and it worked and still does (unlike my CD burner, which worked and now DOESN'T).  

You could get one of the rpm packages and convert it with alien to a deb package and then try installing that and see if it works.  I'm hesitant to experiment with that for fear of breaking what I already have.

Good luck...  Please let us know if you find out the trouble.

---

### Post by sethmahoney on 2005-05-30
[QUOTE=jonrkc]Good luck...  Please let us know if you find out the trouble.[/QUOTE]

Thanks for trying to help, anyway!  I'm not gonna have much time until finals are over, but I'll take a look then.  If I figure anything out, I'll post it here

---

### Post by kejace on 2005-06-22
As a laptop user, the Scroll_Lock key isn't very useful to me.
I found Super_L , the windows key better (similar to what my girlfriend uses on ibook so..)

all the possible keys are listed in <X11/keysymdef.h> which can be seen [http://www.liafa.jussieu.fr/~carton/Enseignement/InterfacesGraphiques/LicenceInfo/Cours/X/keysymdef.h](http://www.liafa.jussieu.fr/~carton/Enseignement/InterfacesGraphiques/LicenceInfo/Cours/X/keysymdef.h)  if you don't have it.

Be sure to not have any spaces **after** the key in the ~/.skippyrc as it won't parse then.

---

### Post by kiddo on 2005-07-19
Hi guys, just wanted to let you know that:
- I used the deb, same problems here
- I aliened a mandrake rpm, and here's what I get

 ```
root@kitsune:~/Desktop# alien --to-deb skippy-0.5.0-2mdk.i386.rpm
skippy_0.5.0-3_i386.deb generated
root@kitsune:~/Desktop# dpkg -i skippy_0.5.0-3_i386.deb
Selecting previously deselected package skippy.
(Reading database ... 102303 files and directories currently installed.)
Unpacking skippy (from skippy_0.5.0-3_i386.deb) ...
Setting up skippy (0.5.0-3) ...
root@kitsune:~/Desktop# skippy
skippy: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by skippy)
```

---

### Post by bored2k on 2005-07-19
[QUOTE=kiddo]Hi guys, just wanted to let you know that:
- I used the deb, same problems here
- I aliened a mandrake rpm, and here's what I get

 ```
root@kitsune:~/Desktop# alien --to-deb skippy-0.5.0-2mdk.i386.rpm
skippy_0.5.0-3_i386.deb generated
root@kitsune:~/Desktop# dpkg -i skippy_0.5.0-3_i386.deb
Selecting previously deselected package skippy.
(Reading database ... 102303 files and directories currently installed.)
Unpacking skippy (from skippy_0.5.0-3_i386.deb) ...
Setting up skippy (0.5.0-3) ...
root@kitsune:~/Desktop# skippy
skippy: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by skippy)
```[/QUOTE]
 Do you have the glibc dev packages installed ?

---

### Post by rwabel on 2005-07-30
The deb file and the posted .skippyrc are working! But when pressing scroll_lock I don't get my different tasks, I get only 5 instead of much more and they are all looking the same. Furthermore there is no tooltip. Anyone else have that problem?

---

### Post by Sparkster on 2005-07-30
Hey guys! I've read all your work trying to adapt skippy from source to Ubuntu, you did a phenomenal work and detailed every step of the way, so I'm guessing everything there is to know to get Skippy up 'n running is right here.

However, there's one point I couldn't find in this thread. I'm really into MacOS' Exposé, and it'd be nice to have it on my Ubuntu, but...

...what kind of performance can I expect? I mean, if it's gonna turn my Ubuntu box into a snail race, I'll pass... I'm running Ubuntu on a REALLY old system: a PIII Coppermine@800Mhz with 256MB RAM PC100, and no OpenGL in my graphics card...

...is it really worth it to install Skippy? Honest!

Peace out! :)

---

### Post by bored2k on 2005-07-30
[QUOTE=Sparkster]...what kind of performance can I expect? I mean, if it's gonna turn my Ubuntu box into a snail race, I'll pass... I'm running Ubuntu on a REALLY old system: a PIII Coppermine@800Mhz with 256MB RAM PC100, and no OpenGL in my graphics card...

...is it really worth it to install Skippy? Honest![/QUOTE]
Skippy is sluggish on a Pentium IV 2.4GHZ. I wouldn't recommend it. Instead, I'd go for Kompose wich is a KDE native. I've used it on the same box with KDE and it renders almost instantly (faster than any other software that aims to do the same). I've heard of people using it on GNOME on this forums (search for kompose here;).

---

### Post by caeserjk on 2005-07-30
I recieve the following error when hitting the key to activate skippy.

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Resource id in failed request:  0x0
  Serial number of failed request:  111
  Current serial number in output stream:  113


Please note I am running 64bit.

---

### Post by kiddo on 2005-08-24
You know, I tried again today (I just found out I posted on this thread before.. I didn't even remember that!), and by following the very nice instructions in the first post, it worked within two minutes, added it to my gnome session startup, and happy I go!

So yeah, worksforme. The only issue is that it has a 2-3 seconds delay to capture window screenshots. Boy, I want something as neat as Exposé. Patience I guess...

My verdict is: don't use a .deb. Just follow the instructions.

---

### Post by bored2k on 2005-08-24
[QUOTE=kiddo]You know, I tried again today (I just found out I posted on this thread before.. I didn't even remember that!), and by following the very nice instructions in the first post, it worked within two minutes, added it to my gnome session startup, and happy I go!

So yeah, worksforme. The only issue is that it has a 2-3 seconds delay to capture window screenshots. Boy, I want something as neat as Exposé. Patience I guess...

My verdict is: don't use a .deb. Just follow the instructions.[/QUOTE]
 Try Kompose. It works (even on gnome) faster than skipp-E.

---

### Post by poofyhairguy on 2005-08-24
[QUOTE=bored2k]Try Kompose. It works (even on gnome) faster than skipp-E.[/QUOTE]

Kompose works OK in Gnome. I just wish I could get it to use a backround.

---

### Post by yyyc514 on 2005-09-01
Ok, I've read the notes... and got Skippy working great... but it's kind of sluggish having to "look" at each of the windows before entering expose mode... anyway to speed this up... or is skippy-xd relaly not any faster?

---

### Post by chaok on 2005-10-16
[QUOTE=caeserjk]I recieve the following error when hitting the key to activate skippy.

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Resource id in failed request:  0x0
  Serial number of failed request:  111
  Current serial number in output stream:  113


Please note I am running 64bit.[/QUOTE]

I have the same problem and I too am using 64bit.
Also When I try to install from source I get 
~/downlaod/skippy-0.5.0$ make
gcc -I/usr/X11R6/include `imlib2-config --cflags` `pkg-config xft --cflags` -g -pedantic -Wall -o skippy skippy.c wm.c dlist.c mainwin.c clientwin.c layout.c focus.c config.c tooltip.c -L/usr/X11R6/lib -lX11 -lm `imlib2-config --libs` `pkg-config xft --libs`
wm.c: In function ‘wm_get_stack’:
wm.c:261: warning: cast to pointer from integer of different size


Any ideas?

---

### Post by pickarooney on 2005-11-04
*snip*

---

### Post by dbbolton on 2008-06-28
I just followed this guide to compile Skippy in Ubuntu Hardy (8.04) and everything worked fine. Thanks!

---

### Post by macduy on 2008-06-28
Hi,

I followed the instructions precisely but every time I press Scroll Lock, I get the following error in terminal:

```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Resource id in failed request:  0x0
  Serial number of failed request:  111
  Current serial number in output stream:  113

```

Not sure if this is relevant, but after running skippy in terminal, I get:

```

WARNING: Ignoring invalid line: ssageBoq

```

Is there any fix to this?

Thanks.

---

### Post by macduy on 2008-07-01
Hehe, I managed to fix this without really understanding what I did :D.

If you have an amd64 system and get a warning during compilation, try opening wm.c and change "CARD32" to "CARD64" on line 261. It worked for me.

---

### Post by Railsbuntu on 2008-07-06
Thanks for the tutorial. Why is skippy no longer maintained? This app is great and brings Exposé to Linux!

---

### Post by el_diablo on 2010-12-18
HI..
while reading linux,i read about skippy.
Can you plz tell what is skippy??

---

