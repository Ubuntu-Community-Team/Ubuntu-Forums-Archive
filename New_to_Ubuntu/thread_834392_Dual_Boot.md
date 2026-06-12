---
title: "Dual Boot"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by jogui on 2008-06-19
Hi, Im very new to linux, I recently installed winxp first on my laptop then ubuntu 8.04 then I encounter this error message "error 24: attempt to access block outside partition"
when Im trying to boot to winxp, ubuntu boots up fine, Im trying to make a dual boot, Ive tried doing dual boot in microsoft before, I know its different in linux, since Im new here I really dont have any idea how to do this, I would really appreciate if someone can help me figure this out, thanks alot.

---

### Post by DGortze380 on 2008-06-19
how did you partition your drive?

---

### Post by jogui on 2008-06-19
when I installed xp i take half of it, then when i install ubuntu i assign the remaining half, thus that answer your question :confused:

---

### Post by housam on 2008-06-19
Boot from ubuntu or its live CD and type the following code in the terminal ( applications >> accessories >> terminal ) : 
```
sudo fdisk -l
```
where -l is the lower case of L and post the results .

---

### Post by barney385 on 2008-06-19
You need a root=/, ext3=home and swap.

So, if you have 80gb to play with, /=10gb; home=68gb and swap=2gb.

---

### Post by jogui on 2008-06-19
> **housam said:**
> Boot from ubuntu or its live CD and type the following code in the terminal ( applications >> accessories >> terminal ) : 
```
sudo fdisk -l
```
where -l is the lower case of L and post the results .

heres what it looks like
```

device boot	boot	start	end	Blocks		ID	System
/dev/sda1	*	1	3570	28675993+	7	HPFS/NTS
/dev/sda2		3571	7296	29929095	5	Extended
/dev/sda5		3571	7137	28651896	83	linux
/dev/sda6		7138	7296	1277136		82	linuz swap / solaris

```

---

### Post by gnrathon on 2008-06-19
looks like to me that you dont have an ext3 partition

just taking a crack at it

---

### Post by housam on 2008-06-19
> **gnrathon said:**
> looks like to me that you dont have an ext3 partition

just taking a crack at it

No , he has ext3 partition ( partition ID 83 linux )

---

### Post by housam on 2008-06-19
> **jogui said:**
> heres what it looks like
```

device boot	boot	start	end	Blocks		ID	System
/dev/sda1	*	1	3570	28675993+	7	HPFS/NTS
/dev/sda2		3571	7296	29929095	5	Extended
/dev/sda5		3571	7137	28651896	83	linux
/dev/sda6		7138	7296	1277136		82	linuz swap / solaris

```

Your partition table is just ok , nothing wrong with it. try to [[COLOR="Red"]_reinstall grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3")

---

### Post by jogui on 2008-06-19
> **housam said:**
> No , he has ext3 partition ( partition ID 83 linux )

what should i do, i really want to try ubuntu and learn a different os, can you show me how to setup the dual boot right

---

### Post by jogui on 2008-06-19
> **housam said:**
> Your partition table is just ok , nothing wrong with it. try to [[COLOR="Red"]_reinstall grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3")

alright!!! ill try this now, thanks alot:)

---

### Post by jogui on 2008-06-19
> **housam said:**
> Your partition table is just ok , nothing wrong with it. try to [[COLOR="Red"]_reinstall grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3")

one question, when i tried the command

```
mount /dev/hda4 /mnt/work 
```

it gives an error message 

```
mount: special device /dev/hda does not exist
```

am i gonna change that value to /dev/sda5 ? is the right

---

### Post by bumanie on 2008-06-19
To reinstall grub boot into ubuntu or use live cd. in terminal > sudo grub
> root (hd0,4) > setup (hd0) > quit reboot and if grub is the problem, it should now work. If not, please post the output of > cat /boot/grub/menu.lst

---

### Post by Duck2006 on 2008-06-19
From the terminal on the live cd.

sudo grub

find /boot/grub/stage 1
root (hd0,4)
setup (hd0)
quit

then reboot and you should have grub menu.

Edit: As "bumanie" posted.

---

### Post by jogui on 2008-06-19
error message "error 24: attempt to access block outside partition"

still the same error message

---

### Post by bumanie on 2008-06-19
Post output of > cat /boot/grub/menu.lst If this is a new install, I would consider reinstalling and doing manual partitioning at the partitioning stage. It seems that ubuntu my not have installed properly.  If you reinstall, prior to doing that, defrag windows twice and do a chkdisk.

---

### Post by jogui on 2008-06-19
> **bumanie said:**
> Post output of  If this is a new install, I would consider reinstalling and doing manual partitioning at the partitioning stage. It seems that ubuntu my not have installed properly.  If you reinstall, prior to doing that, defrag windows twice and do a chkdisk.

in reinstalling the os, is it advisable to install ubuntu 1st then xp or the other way around, which is easier? ive tried installing x p 1st then ubuntu twice with no luck

---

### Post by Duck2006 on 2008-06-19
It can be done with win first or linux first.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by bumanie on 2008-06-19
Although it can be done either way, it is easier and simpler to install xp first. This is mainly due to windows in that it will not recognise grub and will overwrite grubs entry, whereas grub will happily  sit beside and boot other OSes.

---

### Post by jogui on 2008-06-19
> **Duck2006 said:**
> It can be done with win first or linux first.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

thats what i exactly did, xp first then ubuntu twice to be exact, but i cant seem to boot to xp, im not really that sure but i think reinstalling the os will not do the trick, any other suggestions please again the error message is error 24: attempt to access block outside

---

### Post by bumanie on 2008-06-19
This comes from Herman's grub page re grub error 24
> Quoted from the GNU/GRUB manual
24 : Attempt to access block outside partition
This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool).  

Try a file system check.

If you have a GParted -- LiveCD you can boot that and right-click on the filesystem you need to check and select 'check' from the right-click menu. That will fix a lot of filesystem problems. A GParted LiveCD is free and only a small download (45 MB or so), and it is almost indispensable.

If that doesn't work or you would rather use your own commands for filesystem checking, see this website's File Systems and Mounting Page. Type 'man fsck', 'man e2fsck', or 'man reiserfsck' into an terminal and make up a command with the right options to fix your specific filesystem problems.

At this address [http://users.bigpond.net.au/hermanzone/p15.htm#24_](http://users.bigpond.net.au/hermanzone/p15.htm#24_)

---

### Post by Duck2006 on 2008-06-19
From the grub manual Error 24.

> Attempt to access block outside partition
    This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool). 

In your menu,lst find the line that has,

savedefault=true

and change it to,

savedefault=false

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by jogui on 2008-06-20
its all ok now, ive change the root hd(0,0) to rootnoverify hd(0,0) and it works fine, thank you all for the support :guitar:

---

