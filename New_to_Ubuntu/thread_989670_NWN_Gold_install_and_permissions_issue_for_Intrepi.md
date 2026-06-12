---
title: "NWN Gold install and permissions issue for Intrepid"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by trooperchix on 2008-11-21
Exclamation  NWN Gold install and permissions issue for Intrepid
I followed the instructions to install Neverwinter Nights Gold using the install script at:

[http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

I updated my repo for wine for intrepid.

I try and run the bugger, I get a quick flash of a black screen then it disappears and I'm back to looking at my desktop. I'm pretty noob, so be as detailed as possible. Grrr, love the game but can't get it running again. Please help!!

Thanks
Trooperchix

PS. I have gone through as many other postings in the forums I could find, non of the fixes proposed in them worked.

This is what I get when I try and launch the bugger:

eddie@kilimanjaro:~$ /home/eddie/nwn/nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e6553d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7e6078c]
#5 ./lib/libSDL-1.2.so.0 [0xb7e62457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7c18530]
#4 ./lib/libSDL-1.2.so.0 [0xb7e6051a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7e60a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7e62457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7e6bb1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7e60c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7e62457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7bf71d6]
#4 ./lib/libSDL-1.2.so.0 [0xb7e62584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7e6580e]
#4 ./lib/libSDL-1.2.so.0 [0xb7e5ea89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7e5eb3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7e6260f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7c18bc6]
#4 ./lib/libSDL-1.2.so.0 [0xb7e61ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7e62635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e6553d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7e658e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7e60368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7e61092]
#7 ./lib/libSDL-1.2.so.0 [0xb7e63375]
#8 ./lib/libSDL-1.2.so.0 [0xb7e6352b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e587df]
#10 ./nwmain [0x84a0e31]
#11 ./nwmain(strftime+0x1de9) [0x80508a1]
#12 ./nwmain [0x805c9f2]
#13 ./nwmain [0x805a218]
#14 ./nwmain [0x8058ff1]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7bf6435]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7e610f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7e63375]
#6 ./lib/libSDL-1.2.so.0 [0xb7e6352b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e587df]
#8 ./nwmain [0x84a0e31]
#9 ./nwmain(strftime+0x1de9) [0x80508a1]
#10 ./nwmain [0x805c9f2]
#11 ./nwmain [0x805a218]
#12 ./nwmain [0x8058ff1]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted



HELP!!!

---

### Post by shifty_powers on 2008-11-21
did you just try to run the game exectuable?

don't you need to use the wine command?

---

### Post by shifty_powers on 2008-11-21
[http://pgshopping.com/mdkxp/en/artcls/nwnfaq.php#ding](http://pgshopping.com/mdkxp/en/artcls/nwnfaq.php#ding)

any good?

---

### Post by trooperchix on 2008-11-21
I have a Dell 1420n, with an Intel video card (if I recall correctly).  So the link info doesn't apply.  I guess I don't know what the game executable would be...  I know nothing about wine..  sorry, I am a bit of a knucklehead.  The good thing is I've been running Ubuntu for a year now, and I can tell you with all certainty, Microsoft can go take a long walk of a short pier.  Heck, I just ordered another Dell Ubuntu laptop for my better half...  :)

---

### Post by trooperchix on 2008-11-21
bump

---

### Post by trooperchix on 2008-11-22
bump

---

### Post by Zzl1xndd on 2008-11-22
What are you using to run NWN? Wine, Cedega, CrossOver? Or have you installed any of these?

---

### Post by trooperchix on 2008-11-22
I simply followed the instructions at this site:  [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)
installing the NWN Gold edition.  I just try to launch it double clicking the nwn file.  Am I missing something?  I don't touch wine or anything.

---

