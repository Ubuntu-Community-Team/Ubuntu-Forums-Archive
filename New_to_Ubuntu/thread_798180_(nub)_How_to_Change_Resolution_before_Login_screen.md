---
title: "(nub) How to Change Resolution before Login screen"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by joshfulgencio on 2008-05-17
I accidently set the resolution to 620. and now everytime i start it i Literally cant see anything its all Stretched out way too much and i cant see nothing. Is there any way, To change the Resolution Before Login screen? because when i start the Comp it just goes to the Ubuntu Bar that loads then goes to startup i think. Running on Ubuntu 8.04 btw. Thank you

---

### Post by joshfulgencio on 2008-05-18
Um Bump..

---

### Post by joshfulgencio on 2008-05-18
help ...

---

### Post by gnomikos on 2008-05-18
open a terminal and type
```
sudo gedit /boot/grub/menu.lst
```
at the end of the kernel line add:

> vga=791

for 1024x768 resolution.

the kernel line should look something like this:

> kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7egff-6eg vga=791

for other resolutions, look [here]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10")(the values are in hexadecimal)

---

### Post by joshfulgencio on 2008-05-18
I cant open the terminal though i cant see anything after the login screen, and i dont know how to open a terminal before it starts?

---

### Post by gnomikos on 2008-05-18
When the grub menu comes up, choose the recovery mode. It should then boot to console.From there type
> sudo nano /boot/grub/menu.lst

and change the line.

At first, you changed the value to 620 in menu.lst, right?

---

### Post by jordanmthomas on 2008-05-18
> **gnomikos said:**
> open a terminal and type
```
sudo gedit /boot/grub/menu.lst
```
at the end of the kernel line add:



for 1024x768 resolution.

the kernel line should look something like this:



for other resolutions, look [here]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10")(the values are in hexadecimal)

I think he means he set the resolution to 640x480, not that he changed anything in grub's menu.  (Offtopic:  do you know where to find the modes for widescreen terminals?  I found them once and remember that mine is 869, but most sites just list 4:3 resolutions)


joshfulgencio, if you DID change your menu.lst, you can edit the grub command line by pressing e before selecting which kernel to boot and edit it there, or press ctrl-alt-f1 when gdm comes up.  I  really do think you've changed X's configuration since you're having trouble finding a terminal.

---

### Post by joshfulgencio on 2008-05-18
I just finished installing UBUNTU Hardy Full system partion. and it asked me to set resolution I Put it to 800x600 on accident. So i was like "oops" so i better go to settings then screen resolution to change it and i ACCIDENTLY hit the 620 x something, and now i cant see anything. So i cant get to the Terminal after login Nor see the login screen its all Stretched out to the point of no view. So i wanted to know what to do before it logs in. ill try some of these methods

---

### Post by joshfulgencio on 2008-05-18
okay i tried CTRL+ALT+F1 during that Ubuntu Bar loading screen. And it just loads a bunch of stuff in a text format and just brings me to my impossible to see Login screen again any way to get to terminal or something

---

### Post by jordanmthomas on 2008-05-18
> **joshfulgencio said:**
> I just finished installing UBUNTU Hardy Full system partion. and it asked me to set resolution I Put it to 800x600 on accident. So i was like "oops" so i better go to settings then screen resolution to change it and i ACCIDENTLY hit the 620 x something, and now i cant see anything. So i cant get to the Terminal after login Nor see the login screen its all Stretched out to the point of no view. So i wanted to know what to do before it logs in. ill try some of these methods

I don't think what's listed in this thread will help to be honest.
If you've JUST installed it and haven't done much customizing, try pressing ctrl-alt-f2 and logging there.
Then, run these commands:
```
rm -r ~/.gconf ~/.gconfd ~/.gnome2
```
This will get rid of the settings you made in gnome and when you log in again will start back with the defaults.  Your login screen still has normal resolution, right?

---

### Post by gnomikos on 2008-05-18
Ok, I misunderstood cause he only wrote 620.

You'll have to get to console to change your /etc/X11/xorg.conf, try the recovery mode.

---

### Post by joshfulgencio on 2008-05-18
Im so sorry for making you guys type so much but your such big helps >_<. And no my Login screen's Resolution is messed up. I cant do anything. And how many i go about Geting into Recovery mode?
- On a side note i tried CTRL+ALT+F1 and 2 and it just starts up a bunch of text loads then goes back to my unreadable login screen

---

### Post by jordanmthomas on 2008-05-18
Hmm, it shouldn't send you back to the gdm screen.  
Try going into the recovery mode from the grub (right when your computer is starting) screen.

Once it boots, you should have a terminal.  Run this in it:
[code]sudo dpkg-reconfigure -phigh xserver-xorg[/cpde]
This will remake your xorg.conf and should fix your resolution problems (hopefully)
After running this, reboot and boot normally.

---

### Post by joshfulgencio on 2008-05-18
a recovery menu pops up, should i choose RESUME? ROOT? or XFIX?

---

### Post by gnomikos on 2008-05-18
> **joshfulgencio said:**
> a recovery menu pops up, should i choose RESUME? ROOT? or XFIX?

root should get you to the console

---

### Post by jordanmthomas on 2008-05-18
I'd personally try XFIX; sounds like it fixes X which is what you're wanting to do.
I could be wrong as I haven't used Ubuntu in over a year and a half, but I remember reading that hardy was coming out with something like that.

---

### Post by joshfulgencio on 2008-05-18
okay i got into the console from Root and i tried xserver-orgx yata yata. But it gave me a bunch of Keyboard layouts..nothing to do with my resolution.. any other codes that may help me?

---

### Post by jordanmthomas on 2008-05-18
It should still fix the resolution I think.
If not, you can go in and manually edit xorg.conf
```
nano /etc/X11/xorg.conf
```
and make sure the resolutions you need are in there.  There's piles and piles of documentation for this out on the web.

Also, have you tried the xfix thing you mentioned?

---

### Post by gnomikos on 2008-05-18
After the keyboard selection, it should ask about the resolution.Try

```
sudo dpkg-reconfigure -plow xserver-xorg
```

---

### Post by gnomikos on 2008-05-18
To do it manually 
```
sudo nano /etc/X11/xorg.conf
```

and at the screen section add your resolution.It should look something like this:
> 
Section "Screen"
  Identifier  "Default Screen"
  Device    "ati[device]"
  Monitor   "Generic Monitor"
  DefaultDepth  24
  SubSection "Display"
    Depth   24
    Modes   **"1024x768"**
  EndSubSection
EndSection


---

### Post by joshfulgencio on 2008-05-18
Alright guys! it worked thank you so much! im in! ^__^ thank yous o much for your help :D i owe u guys thank u thank u

---

