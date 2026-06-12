---
title: "screen resolution stuck at 800x600 in hardy heron"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by kaston on 2008-11-13
i somehow inadvertently upgraded to hardy heron and as was the case when i upgraded to gutsy, my screen res is stuck at 800x600.  previously, i used envy to fix the problem but that doesn't seem to be working now.  in system->admin->hardware drivers it says my nvidia accelerated graphics driver is enabled and in use.  when i run nvidia-settings in a terminal, it says that i don't appear to be using the nvidia x driver and to run nvidia-xconfig and restart.  i have done this and then tried to rerun nvidia-settings but it's still screwed.  how can i get my screen res back?

this problem is pretty annoying and is seriously making me contemplate a mac

---

### Post by Tamlynmac on 2008-11-13
Have you tried this:

[http://albertomilone.com/wordpress/?p=294](http://albertomilone.com/wordpress/?p=294)

---

### Post by icanfly0307 on 2008-11-13
Hey there...
                     Open up Nautilus or your Home Folder and browse to /usr/share/applications. You'll see an application that's called "Screens and Graphics". Configure your graphics driver and WALLA! It should work... :)

---

### Post by Ryadt on 2008-11-13
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Dave Otter on 2008-11-13
alt + F2 >> displayconfig-gtk 
click on Model then chose your screan model >> ok
then you will find all resolution available for your screen
choose what you want then >> ok

---

### Post by mapes12 on 2008-11-13
I had a similar problem with 800x600 in 8.04 stuck on my machine. This solved it for me: 

Terminal

```
gksudo displayconfig-gtk
```

then select your monitor and driver from the easy to use GUI that pops up.

---

### Post by Dave Otter on 2008-11-14
Sorry-should read

   alt + F2 >> sudo displayconfig-gtk

---

### Post by kaston on 2008-11-14
> **mapes12 said:**
> I had a similar problem with 800x600 in 8.04 stuck on my machine. This solved it for me: 

Terminal

```
gksudo displayconfig-gtk
```

then select your monitor and driver from the easy to use GUI that pops up.

i used envy to uninstall the nvidia driver (my plan was to uninstall and then reinstall) but after the uninstall it was fine for some reason.

i will keep that command in mind though.  for future reference can someone explain to me the difference between gksudo displayconfig-gtk and nvidia-xconfig or nvidia-settings?

---

