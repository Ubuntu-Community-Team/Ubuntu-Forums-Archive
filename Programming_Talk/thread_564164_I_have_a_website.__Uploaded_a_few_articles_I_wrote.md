---
title: "I have a website.  Uploaded a few articles I wrote about X11 programming"
date: 2007-09-30
forum: Programming Talk
---

### Post by Sp4cedOut on 2007-09-30
[http://www.space-out.net](http://www.space-out.net)

a few articles on X11 programming, and later I'll upload some projects I've been working on.

---

### Post by mssever on 2007-09-30
Nice website design. I do have two comments, though. First, your logo--which is really nice--is a little dark. It's a bit hard to read text that's over it. If you lightened it a bit, it would be awesome. Second, sans serif fonts are easier to read on-screen than serif fonts.

---

### Post by BuffaloX on 2007-10-01
Great. :popcorn:

I've just started looking into X11, and am currently looking for sites such as yours.
I'm very surprised about how hard it is to find current information on X11 programming.
I found only one really good beginners guide, but it's a bit old.

Most are very old, and doesn't compile without "updating" the source code.
And 99% of all examples shows just how to make a window with an rectangle, and exit on some event.

I think X11 is really cool, because it gives more direct control, and (in theory) less overhead, it works equally well with all window managers. ( I think ).

Your examples seem very good, I especially like that you include a shaped window example for both X11 and SDL with X11L.

But unfortunately the links to download the code result in 404 error.

If you would like to help beginners like me even more. 
An example with pixmap (buffered)  muti-color RGB-based drawing would be cool.
All The examples I can find use some weird ?? palette ?? system,
With 3 or 4 calls just to define a simple color.
Is anybody seriously programming for palette based systems anymore?

Thanx for a great initiative making an X11 guide. :guitar:

---

### Post by Sp4cedOut on 2007-10-01
BuffaloX, thanks for telling me about the 404 Error, this is my first attempt at creating a website and I put the examples in the wrong directory.  I fixed it now.

I'll take your other suggestion into consideration, as stated on my page, I don't really know all that much about X11 programming.

---

### Post by BuffaloX on 2007-10-01
Hi again,
Links are now working. :)

I tried your shaped window example.
It compiles fine, but when I try to run it afterwards I get this error:

> X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  15


---

### Post by BuffaloX on 2007-10-01
Tried the other examples, all have the same error, except the SDL example which seems to work.
x11properties works with compiz, but is only white with metacity.

---

### Post by Sp4cedOut on 2007-10-02
> **BuffaloX said:**
> Tried the other examples, all have the same error, except the SDL example which seems to work.
x11properties works with compiz, but is only white with metacity.

That's because Compiz is a compositing window manager, and metacity isn't.  In my article it says:

> Note, you need to be using a compositing window manager such as Beryl or Compiz for this to work.

It should still appear on all desktops and be above all other windows.


As for your other one, it's probably a library issue, my  you likely don't have the development libraries for GLX to work.  On the manual page for XCreateWindow it defines the errors it throws, but "BadMatch" is a bit ambiguous:

> BadMatch 	Some argument or pair of arguments has the correct type and range but fails to match in some other way required by the request.

[http://tronche.com/gui/x/xlib/window/XCreateWindow.html](http://tronche.com/gui/x/xlib/window/XCreateWindow.html)

I checked again, it does compile fine on my computer but I've done a lot of apt-getting over my ubuntu career, so I'll try to track down this error.  Again, it's likely a dependency issue.

EDIT: Try checking what vInfo->visual and vInfo->depth are set to, that may help.

---

### Post by BuffaloX on 2007-10-02
Yes it's probably a dependency issue.
They all compile fine on my system, I get the error when i try to run them adter compilation.
That would mean I have the dev part of a library, but not the runtime part I suppose.

---

### Post by ThomasAdam on 2007-10-02
Few interesting bits and pieces, although, your article about window properties is flawed and makes one too many assumptions about the EWMH extensions than they do about existing XAtoms (in that they're non-standard).  You don't mention once about how xprop can be used to change XAtom values on the fly, nor do you mention xlsatoms or XGetAtomName{,S}.  The latter functions are important.

Keep up the good work though.  :)

-- Thomas Adam

---

### Post by Sp4cedOut on 2007-10-03
First off, BuffaloX, try compiling this file I attached, it's an X Shape example without glx.  I'd really like to find out what's causing this problem because I'm certain someone else will have it too.

Second, ThomasAdam.  I admit I don't know much about X11 programming.  These articles were based off of my very limited experience, as I said, they're about things I had trouble with.  What I say is based off my understanding, which isn't very good, that's why I tried to do little talking focus on giving working examples.

My intention with the X11 properties article was to show how to use X11 functions in C to change the properties of a window one is programming.  From my understanding xlsatoms and xprop is used by the window manager or the user to change the properties of windows that have already been created; honestly, I don't know a lot about it though.

You're probably right that I should include XGetAtomName along with XGetWindowProperty and some of the other Atom manipulating functions, I might do an updated article with those included.

Finally, I tried to avoid extrapolating too far, but if I made a statement or assumption that with incorrect, please tell me, because the last thing I want is to be a source of inaccurate information.

Thanks for the feedback.

EDIT: BTW, I added my website onto google's list of websites to look at a few days ago and it's still not showing up on searches, is that normal?  I don't know how long this thing is supposed to take.

---

### Post by BuffaloX on 2007-10-03
Works like a charm. :)
Compile and execute without problems.
With compiz enabled, both mask and alpha works.
Without compiz it still works, only without the alpha-blending effect.

This could actually be considered a feature, because it avoids alpha blending weirdness for window managers that doesn't support alpha blending properly.

---

### Post by ThomasAdam on 2007-10-03
> **Sp4cedOut said:**
> From my understanding xlsatoms and xprop is used by the window manager or the user to change the properties of windows that have already been created; honestly, I don't know a lot about it though.

xlsatoms(1) lists those atoms which have been Interned -- whilst they appear to belong to a specific window, they're stored and defined on the XServer remember.  The whole point of this is so that other applications can make use of them.

As for xprop, it's important to realise this point from its use:  *most* Xatoms simply _are not static_!

> **Sp4cedOut said:**
> 
You're probably right that I should include XGetAtomName along with XGetWindowProperty and some of the other Atom manipulating functions, I might do an updated article with those included.

Yes, you should, since you can't really use XAtoms without those functions.  Note also that in xlib, there are numerous ancillary functions which go together to define window properties, above and beyond the ones I've listed.  XSetWMProperties() and their related widget ones (of which XmbSetWMProperties() is one such example) also helps.  As does XWMHints() (see -- the WM_HINTS struct for more information).  

A basic xlib application, when you get down to it (even if it just maps a window with no content) will use all of this to set XAtoms -- they're essential to most WMs to define their behaviour (even if some of the widget-related functions hide the underlying Xlib calls).

> **Sp4cedOut said:**
> 
Finally, I tried to avoid extrapolating too far, but if I made a statement or assumption that with incorrect, please tell me, because the last thing I want is to be a source of inaccurate information.

No, what you've done is generally OK, but it will need expansion if you want to explain what's going on, rather than just telling someone what needs doing.  I don't mind helping you.


> **Sp4cedOut said:**
> 
EDIT: BTW, I added my website onto google's list of websites to look at a few days ago and it's still not showing up on searches, is that normal?  I don't know how long this thing is supposed to take.

Patience is a virtue.

-- Thomas Adam

---

