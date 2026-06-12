---
title: "[SOLVED] Blue splashscreen after login - what causes it?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Norsefire on 2008-11-27
Whenever I login there is a blue splashscreen that comes up (see attached image). What package is causing this? Or is there a way to see what packages I have installed in the order I installed them, as I would be able to work it out that way.

Thanks.

---

### Post by drs305 on 2008-11-27
I can at least tell you where it is in Intrepid (or at least one of the places):
/usr/share/pixmaps/splash/gnome-splash.png

**Added:**
Whether or not to display the splash image is controlled by settings you can change in gconf-editor. The section you want to deal with is /apps/gnome-session/options
You can turn off the splash image in that section.
Run it with:
```

gconf-editor /apps/gnome-session/options

```

If you want to replace it with another image, here is a good explanation of how to do it. It's from a year ago but from an initial reading it appears to still be correct :
[http://taufanlubis.wordpress.com/2007/08/22/how-to-change-splash-screen-in-ubuntu/]("http://taufanlubis.wordpress.com/2007/08/22/how-to-change-splash-screen-in-ubuntu/")

---

### Post by kd420 on 2008-11-27
I think you meant /usr/share/pixmaps/splash/  (usr not user). I'm assuming you want to disable or change it. If so, open up gconf-editor (eiher type it in terminal or the run dialog using Alt+F2).

navigate to apps>gnome-session>options and uncheck the "show_splash_screen" box. If you just want to change the screen, make another image in the /usr/share/pixmaps/splash/ and change the entry under "splash_image" (or just overwrite the original)

---

### Post by drs305 on 2008-11-27
> **kd420 said:**
> I think you meant /usr/share/pixmaps/splash/  (usr not user). I'm assuming you want to disable or change it. If so, open up gconf-editor (eiher type it in terminal or the run dialog using Alt+F2).

navigate to apps>gnome-session>options and uncheck the "show_splash_screen" box. If you just want to change the screen, make another image in the /usr/share/pixmaps/splash/ and change the entry under "splash_image" (or just overwrite the original)


Yes, you are correct and I edited the typo. I pronounce it 'user' but of course it has nothing to do with 'user' but 'unix system resources'. As I was editing my post it appears we both came up with the same solution.

---

