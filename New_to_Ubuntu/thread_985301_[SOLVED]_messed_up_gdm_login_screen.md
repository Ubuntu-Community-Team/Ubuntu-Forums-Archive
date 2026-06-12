---
title: "[SOLVED] messed up gdm login screen"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Haluci on 2008-11-17
I've recently added a GDM theme from gnome-looks.com for my login screen.  Upon rebooting, I get the gnome circly-loading-thing, but the login screen is never loaded.  Obviously something got corrupted, so I'm wondering how I can change the login screen back to the default one.  I've tried booting in recovery mode, dropping into a root shell, and logging from there... I get my desktop just fine when I run startx but my mouse and keyboard don't work.

So, is there a way to login in text mode (maybe with some kind of boot option?), start my gnome desktop from there (maybe with something other than startx?), then revert my login screen to the one I had before?

Thanks!

---

### Post by jbrown96 on 2008-11-17
What do you see after the black screen? Is it just black, cursor blinking, etc? I'm not sure how you installed it but if you just set it in Preferences then it shouldn't be too hard to undo. (just a side note: when you use recovery mode, you are logged in as the root user. You should not run a X server as root because if there are any bugs or nefarious stuff in any of the programs that are launched it could compromise your system). 
When you boot up the computer, try pressing Crtl+Alt+F1 while its booting. This will show you the boot messages. Once they stop, you should be presented with a login. Login and they use ```
startx
``` hopefully you will be able to undo the damage then. Please post back if you have problems or mark this as solved. 

If that doesn't work, you could always try a graphical login. I can't think of a better method right now, but you need to disable gdm. You can do it with ```
sudo apt-get install sysv-rc-conf
``` then run ```
sudo sysv-rc-conf
``` and uncheck all the boxes for gdm. This will give you a simple text login and you can start x with ```
startx
```

---

### Post by Haluci on 2008-11-17
Oh man I got ninja'd.  Thanks for your suggestions, I'll reboot into ubuntu again and see how things work.

During the black screen I see my cursor, but doing the circly-loading-thing, which is what usually happens when it's loading the login screen... except the login screen never loads.  I set the login screen through preferences -> login window or something like that, I forget what exactly it was called.

---

### Post by Haluci on 2008-11-17
Ah-ha!  That worked - back to normal.  Thanks! :)

---

