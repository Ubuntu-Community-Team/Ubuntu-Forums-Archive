---
title: "Super Key Shortcuts"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by abgemacht on 2008-08-11
Hello,

I would like to set Super+L to lock my screen.  I've set "Super is mapped to Windows Key" in Preferences-->Keyboard and set <mod4>+L to Lock Screen in Preference-->Keyboard Shortcuts.  

If I set Super to "Default" in Preferences-->Keyboard, I can map Lock to Super L, but that means I only can press the Left Super Key to lock the screen.

I've seen a lot of posts about this, but none seem to solve the problem for me.

Thanks

---

### Post by abgemacht on 2008-08-12
Some additional info:

I'm running on a T60p with keyboard model set to "IBM ThinkPad 560Z/600/600E/A22E" and USA Layout.  I've tried this on a couple settings with no luck.

Thanks

---

### Post by colon247 on 2008-09-02
Hey just came across your question.  I know it been three weeks but I may have a solution.  go to "add/remove" may sure it is set to all applications. Search for "compizconfig".  you will see a program called "Advanced Desktop Effects Settings" check it off and hit apply.  

After you install go to system>preferences>Advanced Desktop Effects Settings

DETAILED INSTRUCTIONS:
1. then just click on the "general options" icon

2. in the menu you will see a commands tab. click it

3. click on the arrow for commands

4. choose a command line # to write in (does not matter which one)

5. type in this: /usr/bin/gnome-screensaver-command --lock
--that command will turn on your screensaver and lock your computer at the same time

6. click on the the arrow(not the tab on top) for keybindings

7. look for the command line # you just wrote the code on in this list

8. click the disabled button for that line #

9. check off enabled (it will open up a new menu)

10.Click grab key combination

11.Type whatever combination you want (in you case "super+L")

12.Click okay and your done

Hope this helped  :D

---

### Post by bcooperb on 2009-11-06
These instructions were a little off. But I figured it out from these instructions anyway! Thanks!!! I've been wanting to do that for a while now. I have Windows 7 64bit dual booting with Ubuntu 9.10 64bit. Now I can lock both the same way...

As nice as the new Windows 7 is...I only use it for outlook exchange and all my After Effects and other video Adobe CS4 needs!

---

