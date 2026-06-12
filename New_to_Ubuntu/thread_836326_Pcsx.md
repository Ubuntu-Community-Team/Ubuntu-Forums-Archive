---
title: "Pcsx"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-21
I installed PCSX on my 8.04, but it crashes whenever I try to load a game.
Here is the terminal output:
```
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
Loading memory card /home/ryan/.pcsx/memcards/card1.mcd
Loading memory card /home/ryan/.pcsx/memcards/card2.mcd
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
RGB not found.  Using YUV.
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 11 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Anyone know how to fix this?

---

### Post by RoseKnight on 2009-01-03
I just recently fixed that problem for myself, but I can't remember what I did.

It had something to do with XORG and updating the video driver.

If you still need it, I'll try to back track what I did to try to help you.

---

