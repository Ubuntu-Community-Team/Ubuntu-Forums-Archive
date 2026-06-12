---
title: "[SOLVED] Logout Icon Causes Panel to Disappear!"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by mochiko on 2008-07-25
Hi everyone, 

Well here's my problem:

I press the logout icon (the little green running man) and usually it brought up a little window with some options - Logout, Restart, Shut Down, etc...

Then, something went wrong and now, whenever I press the green dude, the panel just disappears. Everything stays the same otherwise, the wallpaper, the windows... I can even move the windows around and type stuff so it's not getting stuck, but yeah..

I really don't know whether this is a problem on it's own or not. Some other problems that started around this same time - 

-Every time i log in, a window says my deskbar applet is not working and it gives me an option to delete it.

- When I go to the Menu Bar and click on some applications, it does not open. Sometimes, the window comes on the panel, but then disappears. 

-The wallpaper - i need to set it everytime i log in.. 


does anyone have any idea or similar problems?
any insight would be greatly appreciated!

thanks for reaching the end of this if you're reading this..=)

---

### Post by gerbalblaste on 2008-07-25
Alright, it looks like gnome or xorg (the stuff that draws the desktop) may be messed up. Hopefully this will be easy to fix. 

reboot, you should see a boot menu with several options. (if you don't press esc several times until you do.

the options should be some thing along the lines of 
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+

Choose recovery mode option. When your system has booted you should see a blue screen with several options. Choose the option that says 'Fix Xorg' or something along those lines. then choose continue booting and report back the results.

---

### Post by mochiko on 2008-07-26
Hey gerbalblaste!!

I tried rebooting and pressing Esc many many times when it said "Press Esc for Menus", but it didn't really do anything and it just ignored me!
I've tried that before and it worked then.. should i change it from a hidden menu to a non hidden menu thingy on the menu.lst file??

Well, other than that, the icons on my panels disappear every time i reboot and i have to add them back each time.

---

### Post by RiceMonster on 2008-07-26
Maybe there's a permission problem with the configuration files.

try this:

```
mv ~/.gnome2 ~/.gnome2.bak
```

That will rename your gnome configurations folder to .gnome.bak. If that doesn't work and you want your old configuration back, simply delete the new .gnome2 folder and rename .gnome2.bak .gnome2.

---

### Post by mochiko on 2008-07-27
Hey thanks for the reply!


It's just that I tried that in the terminal and it didn't work. Said there was no such file, and I tried searching for it in the file browser but nothing showed up. I went to some folders, which said gnome and gconf or something and i couldn't find it.. but in any case, it's okay because when i rebooted, it doesn't lemme get into ubuntu anymore. 

but that's a different story and it's a new thread now hahah, so thanks for the reply in any case!

=D

---

