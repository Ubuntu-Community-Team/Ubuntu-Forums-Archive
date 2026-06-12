---
title: "[SOLVED] Fullscreen not working? (SDL)"
date: 2008-06-06
forum: Programming Talk
---

### Post by EpsilonDelta on 2008-06-06
Hello everybody, I'm new! Ubuntu is great, and I regret not having made the switch earlier.  
I'm making a small application with SDL for a school (a fractal explorer), and I'm trying to get fullscreen toggling to work. First it only enlarged the window, then I added the NOFRAME flag (which should have been be set automatically by the FULLSCREEN flag), and now it works, except that the desktop panels are still on top. If I minimize and then maximize the app, the panels stay hidden for about one second before returning on top.

```
void Set_fullscreen() {
    video_flags |= SDL_FULLSCREEN;
    video_flags |= SDL_NOFRAME;
    scr_w = max_scr_w;
    scr_h = max_scr_h;
    screen = SDL_SetVideoMode(scr_w, scr_h, color_depth, video_flags);
}
```

---

### Post by geirha on 2008-06-06
why are you using xor operator? that will toggle the fullscreen and noframe flags, so either you should call your function toggle_fullscreen or use "or".

---

### Post by EpsilonDelta on 2008-06-06
> **geirha said:**
> why are you using xor operator? that will toggle the fullscreen and noframe flags, so either you should call your function toggle_fullscreen or use "or".
True, I forgot to change the xors when simplifying it. But that's not the problem.
Also, I noticed some flickering when minimizing/maximizing. It's really odd, and I wonder what I'm doing wrong and why it isn't just fullscreen like you'd expect.

---

### Post by imachine on 2008-09-20
Same issues here, with Compal EL80 (GF7600) compiz and ubuntu 8.04.1, whenever I launch apps like wormux or openttd, which use SDL, they only go full screen after minimising and maximising them, and only for a second - then they get covered by the panels again.

any news on that ? 

any bug reports?:mad:

---

### Post by Zugzwang on 2008-09-20
> **imachine said:**
> Same issues here, with Compal EL80 (GF7600) compiz and ubuntu 8.04.1, whenever I launch apps like wormux or openttd, which use SDL, they only go full screen after minimising and maximising them, and only for a second - then they get covered by the panels again.


As fas as I know that's a problem with compiz. Switch it off and it should work.

---

### Post by imachine on 2008-09-20
so, it's upstream? no patches for compiz from ubuntu?

here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg902025.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg902025.html)

you can read that if you disable some compiz option for auto-redirect, this ought to work..

I will check it and if so, perhaphs a bug report ought to be filed mentioning how ubuntu should have that turned on by now by default, since otherwise problems arise?

EDIT:

ok, you go into gconf-editor, go to apps/compiz/general/screen0/options/unredirect_fullscreen_windows and unclick it.

this way sdl fullscreen works. I do not know of any downside yet.

cheers!

---

### Post by EpsilonDelta on 2008-09-20
> **imachine said:**
> 
ok, you go into gconf-editor, go to apps/compiz/general/screen0/options/unredirect_fullscreen_windows and unclick it.

this way sdl fullscreen works. I do not know of any downside yet.

cheers!

Yes, I recently discovered that fix too. But it I did discover a downside. All gnome hotkeys are disabled in fullscreen for me. So no alt-tab or prntscrn.

---

### Post by imachine on 2008-09-20
Yes, ofcourse, that is what one'd expect from a "true" fullscreen tho - all the input device activity is directed at the fullscreened application :) In my opinion, that is absolutely correct, even if it may seem as a downside to some ;)

There is one other issue, which however most certainly seems a downside - whenever I resume my laptop, the screen remains plain white, with nothing on it, just a moving cursor - that is certainly not correct :(

---

