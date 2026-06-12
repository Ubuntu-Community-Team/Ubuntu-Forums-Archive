---
title: "16-bit SDL blitting"
date: 2009-12-29
forum: Programming Talk
---

### Post by Emill on 2009-12-29
Hello!
If I set up a 16-bit video mode in SDL, the SDL_Flip(screen) is very very slow. 32-bit video mode is much faster, because that is the default Xorg setting.
When using 16-bit mode, SDL creates a "shadow" 16-bit surface, and when calling SDL_Flip, it blits that shadow surface onto the real 32-bit surface.

Now to my question: If you look in the [_SDL_blit_N.c_]("http://wesnoth.repositoryhosting.com/trac/wesnoth_wesnoth/browser/trunk/Classes/SDL/src/video/SDL_blit_N.c") file, you see the blit_table normal_blit_2[] array, which contains a
```
{0x0000F800, 0x000007E0, 0x0000001F, 4, 0x00FF0000, 0x0000FF00,
     0x000000FF,
     0, Blit_RGB565_ARGB8888, SET_ALPHA}
```
but the expected blitting function is something with NO_ALPHA, because the shadow surface has the Amask set to 0. So it falls back to the slow BlitNtoN-function.
But, try to add this line into the blit-table:
```
{0x0000F800, 0x000007E0, 0x0000001F, 4, 0x00FF0000, 0x0000FF00,
     0x000000FF,
     0, Blit_RGB565_ARGB8888, NO_ALPHA}
```
The alpha, though, is set to 0xff on the 32-bit surface because of the RGB565_ARGB8888_LUT lookup-table, but that doesn't seem to matter...
Then everything seems to work properly and the blitting is now 3 times faster!

Why isn't something like this in the current version of SDL?

---

