---
title: "Error 13: Invalid or unsupported executable format"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by phoenix_verma on 2008-11-28
can anyone help me out??

I had ubuntu and WinXP on my Acer Aspire 5920 laptop...
I wanted to try out Fedora...

now when I have installed Fedora a serious problem came in..
I am now not able to use Ubuntu...

The following screen appears when I use Ubuntu...

"
Booting 'Ubuntu'

rootnoverify (hd0,9)
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue...
"

Whwn I press any key, the Menu showing the operating System opens..
Please help me out...

---

### Post by gnuvistawouldbecool on 2008-11-28
well, when I had this issue, I used this guide [here](http://ubuntuforums.org/showthread.php?t=224351).

The only problem is because of the way I did it, I no longer have a bootable Fedora install.  But that can be changed with an edit of /boot/grub/menu.lst, I expect.

---

### Post by jimreynold2nd on 2008-11-28
Lemme guess... You installed Ubuntu first, let it install GrUB into the MBR, then installed Fedora, also let it install GrUB into the MBR right?

Chainloader tried to load the Ubuntu's GrUB from its partition's boot sector, which is not where it is; the Ubuntu version of GrUB in the MBR is overwritten now...

My solution is a little bit involving: modifying the GrUB entry for ubuntu so that it loads Ubuntu directly, not chainloading.
1) Mount the Ubuntu partition from Fedora(it should be in the menu Places -> )
2) find the file boot/grub/menu.lst or boot/grub/grub.conf **in the Ubuntu partition**.
3) Scroll down until you see the first section like this
```
title Ubuntu 8.04.1 -blah-blah-blah
	root (hdx,y)
	kernel /boot/vmlinuz-blah-generic root=/dev/sda(y+1) ro quiet splash
	initrd /boot/initrd.img-blah-generic
```
	quiet
4) Copy that whole section over to the end of your /boot/grub/grub.conf in Fedora (NOTE: this is the /boot/grub/ directory from your root, not from your mounted Ubuntu partition). If able, delete theUbuntu entry in that file (if you get a hang of what makes up that entry).
5) Reboot and choose the new Ubuntu entry.

Goodluck! :)

---

### Post by caljohnsmith on 2008-11-28
How about in your Fedora menu.lst, just link to the Ubuntu menu.lst:
```
title Ubuntu Grub Menu
root (hd0,9)
configfile /boot/grub/menu.lst
```
Give that a shot and let me know how it goes. :)

---

### Post by phoenix_verma on 2008-12-20
Thanks dudes....

Nw lemme tell the weired way I used to fix d problem...

I reinstalled ubuntu (really crazy thin to do)..
But this time I didn't installed its boot loader....

I installed the boot loader of Fedora and gave a link for Ubuntu's drive in it..


:KS

---

