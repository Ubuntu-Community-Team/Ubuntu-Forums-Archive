---
title: "wxAui and BadDrawable error"
date: 2008-10-26
forum: Programming Talk
---

### Post by bbillade on 2008-10-26
I am writing a media application that acts as a frontend for mplayer using wxWidgets2.8.7. My application uses wxAui for docking the media window and other windows.

It is working great under windows but under linux, specifically Ubuntu 7.10 and Ubuntu 8.04, when I attempt to dock/undock the media window mplayer crashes with the error "X11 error: BadDrawable (invalid Pixmap or Window parameter)"
It does this for every video output driver tried with mplayer.
It also does it with and without compiz and on several computers with different video cards and drivers.

It only happens when docking or undocking the window. It does not happen any other time. However, the wxWidgets application itself is not crashing or giving an error, only mplayer.

Does anyone have any idea what may be causing this error or what I might do to prevent it?

Here is the full mplayer error in case it helps.

ID_SIGNAL=6
X11 error: BadDrawable (invalid Pixmap or Window parameter)


MPlayer interrupted by signal 6 in module: flip_page
- MPlayer crashed. This shouldn't happen.
It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
gcc version. If you think it's MPlayer's fault, please read
DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
won't help unless you provide this information when reporting a possible bug.
Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a59767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a5981e]
#2 /usr/lib/libX11.so.6 [0xb7cf2518]
#3 /usr/lib/libSDL-1.2.so.0 [0xb7c59a20]
#4 /usr/lib/libSDL-1.2.so.0 [0xb7c51766]
#5 /usr/lib/libSDL-1.2.so.0(SDL_FreeYUVOverlay+0x37) [0xb7c3dd37]
#6 ./wmiplayer [0x80be400]
#7 ./wmiplayer [0x80be464]
#8 ./wmiplayer(vfprintf+0x3251) [0x807e2f9]
#9 ./wmiplayer(vfprintf+0x331f) [0x807e3c7]
#10 [0xb7f0a420]
#11 /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7ac4a01]
#12 ./wmiplayer [0x80af60f]
#13 /usr/lib/libX11.so.6(_XError+0xfe) [0xb7ceb73e]
#14 /usr/lib/libX11.so.6 [0xb7cf2e5c]
#15 /usr/lib/libX11.so.6(_XReply+0x15a) [0xb7cf321a]
#16 /usr/lib/libX11.so.6(XSync+0x6a) [0xb7ce724a]
#17 /usr/lib/libSDL-1.2.so.0 [0xb7c451d5]
#18 /usr/lib/libSDL-1.2.so.0 [0xb7c518bc]
#19 /usr/lib/libSDL-1.2.so.0(SDL_DisplayYUVOverlay+0x190) [0xb7c3dee0]

---

### Post by cmat on 2008-10-27
Is it an MDI interface like frames contained in a parent window? X11 doesn't like those.

---

