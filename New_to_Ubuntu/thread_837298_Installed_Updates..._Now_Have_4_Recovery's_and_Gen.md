---
title: "Installed Updates... Now Have 4 Recovery's and Generic's"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-06-22
Hmm. Installed updates via update manager last night, and now when i booted up this morning i have 4 recovery entries in grub as well as 4 generic kernel entries. i know the top one is my ubuntu as i know it, but what are the rest for?! obviously recovery is 'safe mode', but the rest? Annoyingly it means Vista is no longer my default boot either and I've totally forgotten how i got it to be...

i think i edited a grub.inf or something..

So two questions - why the populous of grub entries, and how do edit/what do i edit to get Vista as my default boot? 

( on a side note, Ubuntu would be primary OS if my wifi worked - i've tried nsdi wrapper etc and no one seems to be able to help :(

Also, my emerald themes don't load up on start up and i have to manually change windows to the emerald theme via terminal.

i have got iTunes however so :)

---

### Post by perlluver on 2008-06-22
> Also, my emerald themes don't load up on start up and i have to manually change windows to the emerald theme via terminal.

For this one, go to System>Preferences>Sessions and add emerald --replace as one of them.

---

### Post by _sphinx_ on 2008-06-22
These are your older kernel images just in case the new kernel doesnot works for you.
If you haven't edited anything like > /boot/grub/menu.lst
 then the entry for you vista partition would be the grub you just have to press the down arrow, since it may be hidden.
if you do not want to see all the kernel in the grub you can remove them from > /boot/grub/menu.lst

by
```
gksu gedit /boot/grub/menu.lst

```
any remove the old kernel images

---

### Post by _sphinx_ on 2008-06-22
Do not forget to make backup for >  /boot/grub/menu.lst
by
```
sudo cp /boot/grub/menu.lst /boot/grub/menu_bak.lst
```
Since some mistake can harm your system.

---

### Post by Kevbert on 2008-06-22
If everything works fine with the latest version of Ubuntu just delete the old kernels in the /boot/grub/menu.lst file.  
Regarding default boot OS.  Find the line that says 
```
default 0
```
Now count from O (the top menu item) to your Vista OS, including the line Other OS, and change the number after 'default' to the line corresponding to Vista (this will probably be 4) if you have no other OS installed and change the line to
```
default 4
```
Save and exit.

---

### Post by Paqman on 2008-06-22
Easiest thing to do is simply remove the old kernels through synaptic. Look for them starting "linux-image..." This will automatically tidy up your menu.lst, so you don't need to faff about editting it by hand.

Make sure you leave your current kernel installed, of course! ;)

---

### Post by joey-elijah on 2008-06-22
thanks guys, i'll be sure to give it a try later.

i remember before that i had to count lines to get Vista as default, so that sounds like what i did before. Awesome! 

Good news re: gnome too! :D it's silly things like that that make me meh. i suppose it doesn't help i'm using 64 bit lol - strange flash etc all work no problem in firefox 32 etc just simple thing don't!

---

