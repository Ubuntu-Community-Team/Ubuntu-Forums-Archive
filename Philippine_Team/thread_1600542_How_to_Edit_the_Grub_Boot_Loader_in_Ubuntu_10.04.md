---
title: "How to Edit the Grub Boot Loader in Ubuntu 10.04"
date: 2010-10-19
forum: Philippine Team
---

### Post by JCyberinux on 2010-10-19
How to Edit the Grub Boot Loader in Ubuntu 10.04

Step 1
On Ubuntu click on Places >  Computer 
(see step 1 picture)
_[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step1-1.jpg[/IMG]_

Step 2
At Computer, Double Click on File System

Step 3
Double Click on boot Folder
(see step 3 picture)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step3-1.jpg[/IMG]

Step 4
Double Click on grub folder

Step 5
Find and Copy the grub.cfg to make a backup copy
Simply right click and copy
(see step 5 picture)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step5-1.jpg[/IMG]

Step 6 
On Ubuntu click on Places >  Windows File System or Windows HDD (whatever name it is) mine was SYSTEM2
(see step7 picture)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step7.png[/IMG]

Step 7
Paste it in C: Drive or create a folder and paste the copy grub.cfg backup or even anywhere.

Step 8
On Ubuntu click on Applications > Accessories > Terminal

Step 9 
At Terminal, type the following

sudo gedit /boot/grub/grub.cfg

(then it will ask for a password) then ENTER.

(see step 10 picture)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step10-1.jpg[/IMG]


Step 10
You will see the gedit with opened file (grub.cfg)
Go to line 54, and locate and set timeout=10
you can change this value if you want to boot it faster,
or more time to choose what to do on your boot loader.

(see step 11 picture)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step11-1.jpg[/IMG]


Step 11
Go to line 117, see the picture to see my action regarding this.
As on the picture, i higlighted the ### BEGIN.... until the END ...###,
this is for the Windows Boot  Option, in order to make it on the first choice on the boot loader.
CUT (by simple  CTRL-X) or Edit > Cut the whole highlighted lines.

(see step 12 picture)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step12-1.jpg[/IMG]


Step 12
Go to line 63, or betwen middle of the ### END /etc/grub.d/05_debian_theme ###......
and the ............ ### BEGIN /etc/grub.d/10_linux ###
this is were to be the first choice on the boot loader.
Paste it, and save it. Just like the picture i have shown.

(see step 13 picture)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/Step13-1.jpg[/IMG]


I tested it, and works like it should be... Enjoy and share it to others!!!
rjdreyes 2010-10-19 a.k.a JCyberinux on ubuntu pilipinas

---

### Post by Lawand on 2010-10-19
Thanks for this tutorial.

BTW, you can also install the package "StartUp-Manager" and edit GRUB options through the GUI...

---

### Post by _duncan_ on 2010-10-19
It is not advisable to edit the grub.cfg manually since any changes will be overwritten by subsequent processes invoking the 'update-grub' command (e.g. installing/upgrading to a newer kernel, removing old kernels, etc.)

There are marked differences between grub(legacy) and grub2. grub.cfg should not be considered as just a replacement for menu.lst. [[COLOR="Blue"]_This_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275") link provides details on the inner workings of GRUB2 and how permanent changes/customizations can be made.

---

### Post by JCyberinux on 2010-10-19
> **_duncan_ said:**
> It is not advisable to edit the grub.cfg manually since any changes will be overwritten by subsequent processes invoking the 'update-grub' command (e.g. installing/upgrading to a newer kernel, removing old kernels, etc.)

There are marked differences between grub(legacy) and grub2. grub.cfg should not be considered as just a replacement for menu.lst. [[COLOR=Blue]_This_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275") link provides details on the inner workings of GRUB2 and how permanent changes/customizations can be made.

yeah i know that, because as i can see the notice on the grub.cfg, but it seems that the menu.lst tutorial doesn't work for me, and i've been using this for a week now, so nothing happened badly so far... (in between i've also check that grub2 but i don't like the workarounds on grub2) anyway that's only my opinion mates! so any process can do... cheers!!! :guitar:

---

### Post by JCyberinux on 2010-10-20
> **Lawand said:**
> Thanks for this tutorial.

BTW, you can also install the package "StartUp-Manager" and edit GRUB options through the GUI...

Now you mentioned it, it also works... nice!

**For StartUp-Manager (Editing the Grub Boot Loader)**

This will make your choice be the first highlighted option NOT technically first on the boot loader choice.

for example: (in my case)

before:

    Ubuntu 10.04 <--- this is the first highlighted option 
    Memory Test  
    Windows XP 

after making changes:
     
    Ubuntu 10.04 
    Memory Test  
    Windows XP <--- this is the first highlighted option (changes here)

Get it? :)

Step 1
At the top of the Ubuntu logo, you will see the word "System" click on it. then go forth to the "StartUp-Manager".
and click it. It will ask for the password, so type in your password (if any)
[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/01-start1.jpg[/IMG]


Step 2
In StartUp-Manager, you will see the "Default operating system", in there you can change the first highlighted option. 

You will also see the "Timeout" in seconds, in which you can change it, the lower its value the faster it loads. 

The "Display" is for the resolution of you boot loader, and i made it changes same as on the Bootloader menu resolution(in my case 1024x76)

Then go to "Advanced Tab", you will see the "Bootloader menu resolution" - again for the bootloader menu resolution same as Display resolution (in my case 1024x76)

"Misc" Create rescue floppy. > I didn't try this one, especially i don't used floppy drive anymore. :P

[IMG]http://i744.photobucket.com/albums/xx83/rjdreyes1317/grububuntu/02-start2.jpg[/IMG]

Step 3
After making changes, Close it and reboot to see the changes. 

Enjoy! and very thanks to **Lawand**, share it to others! Cheers!

---

### Post by zeroseven0183 on 2010-10-20
I suggest you post this HowTo in [Tutorials and Tips forums]("http://ubuntuforums.org/forumdisplay.php?f=100")
Or you can, if you are already running, update it as Ubuntu 10.10.

---

### Post by JCyberinux on 2010-10-20
> **zeroseven0183 said:**
> I suggest you post this HowTo in [Tutorials and Tips forums]("http://ubuntuforums.org/forumdisplay.php?f=100")
Or you can, if you are already running, update it as Ubuntu 10.10.

How i can transfer this post to the tutorials and tips.? or do i have to post new again to that forum? thanks!!!!

---

### Post by Laibcoms on 2010-10-21
It will work fine until the next time update-grub runs.  But if it still works, then you're probably using grub-legacy? I'm not sure but it is weird that it is still working after an update-grub command.  :)

Try this one, this is what I do:

1) Set your GRUB_DEFAULT and GRUB_TIMEOUT here.
gksu gedit /etc/default/grub
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda3)"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=13
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
* above was truncated

2) gksu gedit /boot/grub/grub.cfg
And look for 30_os-prober portion, copy and paste that section, example:
```

menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 828c35428c353251
    chainloader +1
}

```

3) sudo chmod -x /etc/grub.d/30_os-prober
4) sudo chmod +x /etc/grub.d/40_custom

5) gksu gedit /etc/grub.d/40_custom
- Copy and paste what you copied in Step 2 into this file then save

6) sudo update-grub

Take note of:
* GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda3)"
* menuentry "Windows 7 (loader) (on /dev/sda3)" {

It is better to do it that way, by "name" than by "position".  That way, if the position of your default OS moves in position in the grub menu, you don't have to re-edit your grub.
-- That is, if you have a different default OS than what comes with Ubuntu.

You can try it and see if it works now.  Or you can go the GUI way as was posted above ^_^

---

### Post by JCyberinux on 2010-10-21
> **Laibcoms said:**
> It will work fine until the next time update-grub runs.  But if it still works, then you're probably using grub-legacy? I'm not sure but it is weird that it is still working after an update-grub command.  :)

Try this one, this is what I do:

1) Set your GRUB_DEFAULT and GRUB_TIMEOUT here.
gksu gedit /etc/default/grub
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda3)"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=13
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```* above was truncated

2) gksu gedit /boot/grub/grub.cfg
And look for 30_os-prober portion, copy and paste that section, example:
```

menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 828c35428c353251
    chainloader +1
}

```3) sudo chmod -x /etc/grub.d/30_os-prober
4) sudo chmod +x /etc/grub.d/40_custom

5) gksu gedit /etc/grub.d/40_custom
- Copy and paste what you copied in Step 2 into this file then save

6) sudo update-grub

Take note of:
* GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda3)"
* menuentry "Windows 7 (loader) (on /dev/sda3)" {

It is better to do it that way, by "name" than by "position".  That way, if the position of your default OS moves in position in the grub menu, you don't have to re-edit your grub.
-- That is, if you have a different default OS than what comes with Ubuntu.

You can try it and see if it works now.  Or you can go the GUI way as was posted above ^_^

nicely done.. thanks man! i'll try that too....

---

