---
title: "Dual Boot Can not see option"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by yeehi on 2008-06-15
I had vista installed. 
Hardy Heron LTS detected it during installation and said grub would be ok.

When the machine boots, I get no option to go to Vista. Why? How do I change it?

In the grub folder, I see that vista is in there in one file...

---

### Post by Eisenwinter on 2008-06-15
Post the contents of /boot/grub/menu.lst in here.

---

### Post by Biggy on 2008-06-15
in [Startup-Manager]("http://web.telia.com/~u88005282/sum/installation.html") set as Default perating ystem Vista.

---

### Post by ibuclaw on 2008-06-15
On bootup, you press the **Escape** key to view the GRUB boot menu.

By default, the boot menu is hidden. To turn off, open the menu.lst file and comment out the command "hiddenmenu"
This one-line command does it for you.
```
sudo awk '{if ($1 == "hiddenmenu") print "#hiddenmenu"; else print}' /boot/grub/menu.lst
```
And to turn it back on.
```
sudo awk '{if ($1 == "#hiddenmenu") print "hiddenmenu"; else print}' /boot/grub/menu.lst
```

Regards
Iain

---

### Post by yeehi on 2008-06-16
:lolflag:Thanks for the replies!

One problem I have is not being able to see anything on the display during the bootup, due to using a TV as the display. It reports "PC out of range" meaning the refresh rate is too high...

Anyway, by guessing the keys to hit, (Blindfolded Linux guru kung fu!) I got it to boot into Vista! :)

One of the problems was that it hadn't shut down properly and i had to guess the options for the supplementary menu too - wild, heh? :)

Now, if I could only get my e220 modem working on linux...

:confused:

---

