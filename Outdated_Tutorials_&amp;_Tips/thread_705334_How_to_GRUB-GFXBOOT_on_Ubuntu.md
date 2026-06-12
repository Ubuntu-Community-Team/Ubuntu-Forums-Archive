---
title: "How to GRUB-GFXBOOT on Ubuntu"
date: 2008-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by criskat777 on 2008-02-23
Hello, This is my first how to so please fell free to add what you think is fit. this how to will add the animated grub splash screen like the one on Suse and Mint to your Ubuntu Distro.

REMOVE OLD GRUB
Code:

sudo apt-get remove grub

DOWNLOAD & INSTALL GRUB-GFXBOOT
Code:

wget [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

Code:

sudo dpkg -i grub-gfxboot_0.97-5_i386.deb

GET THE ANIMATED IMAGE & COPY IT TO YOUR GRUB DIRECTORY
(You can also get some from gnome-look.org or from the bottom of post #1 in this thread)
Code:

here are some themes

Dark Brown (Dapper look) generic theme [message.new] | Link |     [http://ubuntuforums.org/showpost.php?p=1239724&postcount=55](http://ubuntuforums.org/showpost.php?p=1239724&postcount=55)
Medium blue kubuntu theme [message.kubuntu] | Link |     [http://ubuntuforums.org/showpost.php?p=1234300&postcount=54](http://ubuntuforums.org/showpost.php?p=1234300&postcount=54)
Dark grey ubuntu theme [message.ubugrey] | Link |    [http://ubuntuforums.org/showpost.php?p=1251236&postcount=61](http://ubuntuforums.org/showpost.php?p=1251236&postcount=61)
Medium brown ubuntu theme [message.ububrown] | Link |    [http://ubuntuforums.org/showpost.php?p=1252317&postcount=63](http://ubuntuforums.org/showpost.php?p=1252317&postcount=63)
Light orange ubuntu theme [message.ubu] | Link |    [http://ubuntuforums.org/showpost.php?p=1254642&postcount=64](http://ubuntuforums.org/showpost.php?p=1254642&postcount=64)
Red ubuntu theme [message.new] | Link |     [http://ubuntuforums.org/showpost.php?p=1265601&postcount=65](http://ubuntuforums.org/showpost.php?p=1265601&postcount=65)
Fuzzy blue and black ubuntu theme [message.bluspash] | Link |   thttp://ubuntuforums.org/showpost.php?p=1272301&postcount=71
White / Grey Snowish generic theme [message.snow] | Link |     [http://ubuntuforums.org/showpost.php?p=1292317&postcount=84](http://ubuntuforums.org/showpost.php?p=1292317&postcount=84)
Linspire-style blue kubuntu theme [message.kubu] | Link |      [http://ubuntuforums.org/showpost.php?p=1294120&postcount=86](http://ubuntuforums.org/showpost.php?p=1294120&postcount=86)
Light blue / grey Xubuntu theme [message.xubu] | Link |      [http://ubuntuforums.org/showpost.php?p=1297486&postcount=97](http://ubuntuforums.org/showpost.php?p=1297486&postcount=97) 


once you dowload the theme you want Extract it to your desktop
then open a terminal

Code: 

cd Desktop 

Code:

sudo cp message.blusplash /boot/grub/   (where it says message.blusplash write the name of whatever splash you choose) then

EDIT YOUR GRUB MENU TO USE THE ANIMATED IMAGE
(good practice to backup the file first and then edit)
Code:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

Code:

sudo gedit /boot/grub/menu.lst

ADD THE FOLLOWING LINE  TO THE TOP OF THE FILE SO IT LOOKS LIKE THIS...
Code:

gfxmenu /boot/grub/message.blusplash      (write here what ever splash name you chose in this case it's  message.blusplash )
                                            


# menu.lst - See: grub(), info grub, update-grub
#            grub-install(), grub-floppy,
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

THEN, INSTALL THE BOOT-LOADER           (This step is in case something changed in grub when it was reinstalled so take a look at grub in a terminal before you start

Code :

sudo gedit /boot/grub/menu.lst       

At the end it will look something like this   Look at were it says root    (hd0,0)    look at all your root settings and make sure there the same after the mode
if all is the same you should not have any problems if something changed just edit it like it was before the mode.


title		Ubuntu Studio, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1ee4114a-f382-43f0-bdc9-a5d6ed9e13c4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu Studio, kernel 2.6.22-14 recovery 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1ee4114a-f382-43f0-bdc9-a5d6ed9e13c4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu Studio, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		MicroVirus WinBlows XP Pro
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1 




(this may vary based on your computer)

Code:
sudo grub-install hd0

that is it. enjoy 

Just in case some one completes this how to and can not boot back to Ubuntu download Super Grub Disk   From tihs Web Page first [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml) and burn it to a cd it's the easiest way to reinstall Grub in case of a fatal error (just to be safe) 

i have done this numeris times and it works great but like in all mods there is always a probability of something my go wrong. But if you fell Lucky go for it you won't regret it.      

i hope this helps some get there grub screen look better:popcorn:
Credits go to this wep page: 
[http://abhay-techzone.blogspot.com/2007/10/howto-have-grub-like-suse-on-ubuntu.html](http://abhay-techzone.blogspot.com/2007/10/howto-have-grub-like-suse-on-ubuntu.html)

i just mode it to better fit a noobs needs

if you have any ??????? just PM me and i will try to help.

---

### Post by blacksm1th on 2008-02-28
Nice. This is one well written working tutorial. Thanks :guitar:

---

### Post by criskat777 on 2008-03-06
if anyone knows were there are more themes please post links. Thank you
and those who have been successful please leave a comment :)

---

### Post by obsrv on 2008-06-20
Where do I find grub-gfxboot 64bit package?

---

### Post by blaxnux on 2009-04-03
[http://kanotix.com/debian/pool/main/g/grub-gfxboot/](http://kanotix.com/debian/pool/main/g/grub-gfxboot/)

---

### Post by petrofang on 2009-07-07
this worked for me when other how-to's did not. Thank you! 

Oh, one minor thing I did change from your directions. Since my /boot is mounted from a different partition than my root directory, line 1 of my menu.lst reads:
```
gfxmenu /grub/*message *#graphical menu file
```as well as all the kernels and such, which do not have the **/boot** prefix

Up Next - how do custom design a theme?  I'll start looking around for the answer to that one; maybe: [http://en.opensuse.org/Gfxboot](http://en.opensuse.org/Gfxboot)

---

### Post by blackhawkover on 2009-07-11
> **criskat777 said:**
> 

Code:
sudo grub-install hd0

that is it. enjoy 


So, I got to this point and terminal says

blackhawkover@blackhawkover-desktop:~$ sudo grub-install hd0
The file /boot/grub/stage1 not read correctly.
blackhawkover@blackhawkover-desktop:~$ 

and so I come to your wisdom. I just want it to look good. 
thanks. It's great up to this point.

---

### Post by nCounTr on 2009-07-11
Ok i've completed the install of the grub-gfxbooot file version 0.97_42 and it worked great.
I downloaded gfxboot-theme-nld from synaptic and changed the back.jpg image file with my own and i encountered little problem.
The text with the boot options (windows, linux, leopard) is shown almost on the center of the screen, and i like it to be on the right center side of the screen and i don't know how to do that.
And another thing, i want to remove the boot options line on the bottom of the screen.
If some knows how to do that i would be grateful if he/she could help me with this.

When i'll finish my theme i'll post the message file and the source for it here.

Thanks in advance,
nCounTr

---

### Post by zoogTHOMzoog on 2009-08-30
Thanks, worked like a charm for me!

---

### Post by Ezure on 2009-10-12
> **blackhawkover said:**
> So, I got to this point and terminal says

blackhawkover@blackhawkover-desktop:~$ sudo grub-install hd0
The file /boot/grub/stage1 not read correctly.
blackhawkover@blackhawkover-desktop:~$ 

and so I come to your wisdom. I just want it to look good. 
thanks. It's great up to this point.

I have the same issue - found nothing on it yet.

---

