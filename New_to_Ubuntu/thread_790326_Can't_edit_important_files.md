---
title: "Can't edit important files"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by J|Burn on 2008-05-11
Slight problem. If I try editing/saving menu.lst or xorg.conf or any other important files I get this:

[B]"Could not save the file /boot/grub/menu.lst.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."[/B]

How do I get around this? I've tried logging in as root through the terminal before saving but no go.

Thanks for your help! <3

---

### Post by SunnyRabbiera on 2008-05-11
you need to go under sudo to do such things.
We have the system set up for a reason, the root account is disabled by default...
Now those files, do you need to edit your xorg or grub menu list?
do you know how to properly do these things?

---

### Post by Joeb454 on 2008-05-11
Open a terminal again, and do ```
gksudo gedit /boot/grub/menu.lst
```

Hopefully that should allow you to save it :)

---

### Post by kk0sse54 on 2008-05-11
Lets first assume you are using the default Ubuntu Text editor. Go into the terminal and type:
```
sudo gedit /boot/grub/menu.lst
```
make your changes and then save it.

---

### Post by goodmanbrown on 2008-05-11
I don't know why logging in as root didn't work.  But here's the normal way to do it:

```
gksu gedit [file]
```

You should be able to save any changes you make if you start gedit that way, and enter your password when prompted.

---

### Post by TeoBigusGeekus on 2008-05-11
1) 
```
gksudo nautilus
```
this will give you the right to use nautilus with root priviledges. When you open menu.lst for example saving any changes will be allowed.

2)
```
gksudo gedit /boot/grub/menu.lst
```
you will open the file with root priviledges and any changes can be saved. I prefer this way, as with the 1rst method you can misclick something and all hell will break loose, whereas with this method you know that the only file that can be affected is menu.lst.

---

### Post by J|Burn on 2008-05-11
gksudo gedit /boot/grub/menu.lst

This worked, thanks guys! I concur this is the best/safest way also. 

I was going to edit menu.lst to load windows xp by default. I may change it from time to time. As far as xorg.conf I wanted to enable my mouse wheel forward/back buttons on my Logitech G5.

---

### Post by oldos2er on 2008-05-11
Or install the package nautilus-gksu, then you can simply right-click on a file and 'Open as Administrator.'

---

