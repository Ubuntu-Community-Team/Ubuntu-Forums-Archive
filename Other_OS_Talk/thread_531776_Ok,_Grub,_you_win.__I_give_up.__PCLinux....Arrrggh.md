---
title: "Ok, Grub, you win.  I give up.  PCLinux....Arrrgghhh!!!"
date: 2007-08-21
forum: Other OS Talk
---

### Post by ArtF10 on 2007-08-21
I am trying to install three distros on the same HD.  I have 

/dev/sda5 Xubuntu /home
/dev/sda6 Swap
/dev/sda7 Xubuntu /

I want:
/dev/sda8 Ubuntu /home
/dev/sda9 Ubuntu /

/dev/sda10 PcLinux /home  <-----this might have to change
/dev/sda11 PcLinux /  <-----this might have to change

I sepnt the last 4 hours going through the PcLinux install without any luck.  Here's what I did and my questions:

I selected /home for /dev/sda 10 and / for /dev/sda11 as planned above.  The next screen in the installation asks me for mount points and Grub options: Grub Text, Grub Graphic or LILO so I said Grub text so that I could select from the same Grub boot loader.  It is the mount points that are confusing to me.  IT gives me a drop down menu for selecting the mount point.  NOW, the PC Linux Wiki gives the following as instructions for this procedure:
[http://docs.pclinuxos.com/Adding_PCLinuxOS_to_an_existing_GRUB](http://docs.pclinuxos.com/Adding_PCLinuxOS_to_an_existing_GRUB)

Essentially I would be adding PCLinux to the existing Grub by what they say "You have installed the bootloader, of the PCLinuxOS you want to boot, to the partitions bootsector" and then edit the file /boot/grub/grub.conf of the linux that "owns" the "master" bootloader in the MBR by adding the following at the end of the file: 

title PCLinuxOS
rootnoverify (hd0,2) 
chainloader +1  

1.  By this do they mean that I need to select /boot instead of / for dev/sda10?

2.  Do I need to select /dev/sda10 as the mount point and not use / as the mount point from the Grub selection screen?

I tried this earlier and it failed.  I must have selected a wrong mount point(not sure) because the bootloader did nto work as XUbuntu did not show up.  I had to reset Grub and then it automatically boots into Xubuntu with no mention of PcLinux.  I have spent much time on google searching for this and need some guidance here.

3.  If I install Ubuntu, would I just use / for /dev/sda9 and /home for /dev/sda8 or will that also be more complicated to get it TOO to show up in the same Grub bootloader as Xubuntu...separate from Xubuntu ofcourse?

---

### Post by logos34 on 2007-08-22
> **ArtF10 said:**
> 
1.  By this do they mean that I need to select /boot instead of / for dev/sda10?

2.  Do I need to select /dev/sda10 as the mount point and not use / as the mount point from the Grub selection screen?

I tried this earlier and it failed.  I must have selected a wrong mount point(not sure) because the bootloader did nto work as XUbuntu did not show up.  I had to reset Grub and then it automatically boots into Xubuntu with no mention of PcLinux.  I have spent much time on google searching for this and need some guidance here.

The easier method is to chainload PCLinuxOS rather than do the full configuration (the latter isn't all that difficult except it means you will have to manually edit the master grub menu after any kernel updates in the PCLinuxOS grub.conf file).  

You want to install  'Grub Text' to the PCLinuxOS **root partition bootsector**. so choose '**[COLOR="Red"]/[/COLOR]**' (sda11).  

Then you simply need to add an entry for PCLinuxOS to the Xubuntu grub menu.lst, pointing to the root (/) partition sda11 (where the /boot folder is containing the kernels and images), not sda10 which is your /home.  (If you had made a separate /boot partition, then you would point it there)

In Xubuntu open up menu.lst:

**gksudo gedit /boot/grub/menu.lst**

Add this to bottom:

> title PCLinuxOS
rootnoverify (hd0,[COLOR="Red"]**10**[/COLOR])
chainloader +1

(hd0,10) = /dev/sda11

---

### Post by dptxp on 2007-08-22
Why not install the ubuntu-desktop on top of xubuntu instead of separate install ? You can always remove unwanted menu items or programs.

---

### Post by logos34 on 2007-08-22
> **dptxp said:**
> Why not install the ubuntu-desktop on top of xubuntu instead of separate install ? You can always remove unwanted menu items or programs.

Good question.  Maybe he's running 32- and 64-bit (that's what I have), or just wants to experiment a little without fear of borking his main Xubuntu install.

---

### Post by ArtF10 on 2007-08-22
> **dptxp said:**
> Why not install the ubuntu-desktop on top of xubuntu instead of separate install ? You can always remove unwanted menu items or programs.

Well, that's interesting.  I just did that and it seems to work.  Now, how would I remove the unwanted menu items?  Do you have a link to the procedure to remove these?

Thnaks for the replies.

---

### Post by dptxp on 2007-08-22
In Ubuntu (gnome) - System>Preferences>Main Menu
OR right click on 'Applications' at top left and click on 'Edit Menu'.

You will find some items to add too. Something you should know.
The programs do not get added or removed from disk. Only from menu.

Do not know about Xubuntu, explore there.

---

### Post by ArtF10 on 2007-08-22
> **dptxp said:**
> In Ubuntu (gnome) - System>Preferences>Main Menu
OR right click on 'Applications' at top left and click on 'Edit Menu'.

You will find some items to add too. Something you should know.
The programs do not get added or removed from disk. Only from menu.

Do not know about Xubuntu, explore there.

IS there a way to remove them from the disk or are they there to stay?

---

### Post by logos34 on 2007-08-22
You can uninstall them through Synaptic or just do

**sudo apt-get --purge remove <program>**

---

### Post by ArtF10 on 2007-08-22
BTW, thank you for the reply about the PCLinux post..I will try it in a few hourse and post back.  You clarified a lot for me in that post.

---

### Post by ArtF10 on 2007-08-22
Xubuntu has nano so I replaced gedit with nano but it won't let me scroll down.

---

### Post by logos34 on 2007-08-22
> **ArtF10 said:**
> Xubuntu has nano so I replaced gedit with nano but it won't let me scroll down.

you used 

**sudo nano** ...

and you can't scroll down?

---

### Post by ArtF10 on 2007-08-22
Thanks, changed it to sudo,....previously used gksudo...will restart and post.

---

### Post by ArtF10 on 2007-08-22
Didn't do it.  No menu...just brought me right back into XUbuntu.

I  set / for /dev/sda11 and /home for /dev/sda10 as I said earlier and put the grub mount point on /dev/sda11 (text Grub menu).

Now, on the website I posted earlier, they say after the configuration, to do the following:

After editing the configuration file, you have to install updates again. Make sure you are either booted from the Linux that comes with the file you've just edited. (or that you are correctly chrooted - experienced users) If that is the case, then install the bootloader using: %%grub-install /dev/hda%% Replace /dev/hda with the device you want to install to.

Do I need to do this?  If so, would it be grub-install /dev/hda11?  And do I need those %% signs?

---

