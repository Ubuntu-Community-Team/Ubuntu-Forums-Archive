---
title: "HP DV6 Pavilion Laptop won't resume from suspend"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by hscriber on 2012-08-28
I have a HP Pavilion DV6 laptop, and I am running Ubuntu LTS 12.04.  I can not get it to resume after suspending the system.  I installed the additional driver for my ATI Graphics card, but it still doesn't work.  A post release update is also available, but it won't install, I get an error.  There seem to be quite a few with this problem, but no solution has worked for me.  Any ideas?  Thanks
Scribe

---

### Post by micahpage on 2012-08-28
I have the same exact problem.

My quick time solution was to never suspend it. I am now very careful to never suspend it as I will have to restart my pc just get back into it

I will also be interested in this thread for a fix it.

---

### Post by hscriber on 2012-08-30
Yeah, I have found multiple people with multiple different kinds of computers with this issue.  I now have specific graphics driver info though.
VESA: M92
I have an ATI/AMD FGLRX graphics card with a proprietary driver update.  There's one more update, a post release update, but it won't let me install the post release update for some reason.  It tells me to look at a file for more information, but when I type the location of said file into the terminal, it tells me access denied.

---

### Post by Mark Phelps on 2012-08-31
> **hscriber said:**
> Yeah, I have found multiple people with multiple different kinds of computers with this issue.  I now have specific graphics driver info though.
VESA: M92
I have an ATI/AMD FGLRX graphics card with a proprietary driver update.  There's one more update, a post release update ... 

Do NOT try to force this install.  If it completes it's likely it will trash your display, you'll have to remove the drivers, and reinstall the ones you have now -- all over again!

---

### Post by hscriber on 2012-09-01
Ok, I won't do that.  Any body have a solution to the suspend problem though?

---

### Post by hscriber on 2012-09-11
Anybody?

---

### Post by NikTh on 2012-09-11
Hi , 

take a look here : [http://ubuntuforums.org/showthread.php?p=11926504](http://ubuntuforums.org/showthread.php?p=11926504) , 4th post. 

Thanks

---

### Post by hscriber on 2012-09-11
Neither of those scripts worked for me.  It seems that suspend doesn't like certain HP, Asus, and Samsung computers.

---

### Post by NikTh on 2012-09-14
Hi , 

can you install the latest Kernel from mainline and test it ? 

You can find it here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.3-quantal/)

Download the appropriate packages i386=32bit , amd64=64bit . 
Also download the _linux-headers**.all.deb**_ regardless of your system architecture. 

Install them with ```
dpkg -i "package name".deb
``` beginning from headers and proceed with linux-image. 

Reboot and see if suspend works. 

Thanks

---

### Post by hscriber on 2012-09-14
I downloaded those files, but it wouldn't let me do the terminal command, something about only a superuser can do that.  So I double clicked on it in my download files and it took me to the ubuntu software center to a page that says dependency is not satisfiable.  So I searched linux kernal and downloaded the generic kernal.  Rebooted, suspended, and it still didn't work.  Any other ideas?  Thanks for trying.

---

### Post by NikTh on 2012-09-14
> **hscriber said:**
> I downloaded those files, but it wouldn't let me do the terminal command, **something about only a superuser can do that**.  So I double clicked on it in my download files and it took me to the ubuntu software center to a page that says dependency is not satisfiable.  So I searched linux kernal and downloaded the generic kernal.  Rebooted, suspended, and it still didn't work.  Any other ideas?  Thanks for trying.

Hi , 

you have right. The command is ```
**sudo** dpkg -i "packagename".deb
```Are you sure now that you have installed properly the latest mainline kernel ? 
Can you boot from this Kernel and open a terminal and give the result of this command 
```
uname -r
```Thanks

---

### Post by hscriber on 2012-09-15
3.2.0-30-generic

EDIT:
I installed using terminal too, it said everything was successful, but it still doesn't work.  Any other ideas?  Hopefully everything that's been said up to now has helped someone else with this issue.

---

### Post by NikTh on 2012-09-16
> **hscriber said:**
> 3.2.0-30-generic

EDIT:
I installed using terminal too, it said everything was successful, but it still doesn't work.  Any other ideas?  Hopefully everything that's been said up to now has helped someone else with this issue.

Yes , it seems that something went wrong. 

Lets try to install the newer mainline kernel with an automatic script . 

Follow the instructions. 

1. Open a terminal and copy-paste from here bellow commands one at time. 

```
sudo apt-get install -y python-bs4 
wget http://ubuntuone.com/1qb8yjmtSxdUIqmEAiMgwR -O ~/kmpd.py
chmod a+x kmpd.py 
./kmpd.py
```2. Press Enter to all of the questions 

3. When it asks for your password write it carefully . 

4. When the procedure  finish,  you will see a message like "all done" 

Reboot your system and the newer kernel 3.5.3 , will be listed First in grub menu. Boot from there and see if suspend works. 

**[SIZE=3]Credits:[/SIZE]  **The script kmpd.py is a creation of [_Savvas Radevic (aka medigeek)_]("https://launchpad.net/~medigeek") written in python and hosted in his git . [https://github.com/medigeek/kmp-downloader](https://github.com/medigeek/kmp-downloader)
Excellent work Savvas!
 
Thanks

---

### Post by kemtnbkr on 2012-09-16
It seems your suspend problem has something to do with your graphics card.  I have a Pavilion DV6 as well, and it works fine.  However, I only have Intel integrated graphics, but suspend works perfectly fine.  Better than Win 7, actually.  Hope that the newest kernel will fix your problem.

---

### Post by hscriber on 2012-09-17
> **NikTh said:**
> Yes , it seems that something went wrong. 

Lets try to install the newer mainline kernel with an automatic script . 

Follow the instructions. 

1. Open a terminal and copy-paste from here bellow commands one at time. 

```
sudo apt-get install -y python-bs4 
wget http://ubuntuone.com/1qb8yjmtSxdUIqmEAiMgwR -O ~/kmpd.py
chmod a+x kmpd.py 
./kmpd.py
```2. Press Enter to all of the questions 

3. When it asks for your password write it carefully . 

4. When the procedure  finish,  you will see a message like "all done" 

Reboot your system and the newer kernel 3.5.3 , will be listed First in grub menu. Boot from there and see if suspend works. 

**[SIZE=3]Credits:[/SIZE]  **The script kmpd.py is a creation of [_Savvas Radevic (aka medigeek)_]("https://launchpad.net/~medigeek") written in python and hosted in his git . [https://github.com/medigeek/kmp-downloader](https://github.com/medigeek/kmp-downloader)
Excellent work Savvas!
 
Thanks

did this, now all I get is a blank red screen

---

### Post by NikTh on 2012-09-19
Hi , 
if you cannot boot from the newer kernel , then switch to the old . Keep press (hold down) the SHIFT key during PC boot until grub menu show up , and choose an older kernel version. (previous linux versions). 

If you want to remove the kernel 3.5 , then open synaptic (install it if you don't have) and at the search box write :**linux-image** and then click **status => installed** you will find the kernel 3.5 , right click and remove. 
Do the same thing for **linux-headers**.

I thought to test a newer kernel , but seems not working either. Sorry

Thanks

---

### Post by hscriber on 2012-09-19
That got me back running, thanks. Thanks for spending so much time trying to help me.

EDIT:
I tried again, and I here are the errors I'm getting when downloading I didn't notice last time.

error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Generating grub.cfg ...
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found linux image: /boot/vmlinuz-3.5.4-030504-generic
Found initrd image: /boot/initrd.img-3.5.4-030504-generic
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found linux image: /boot/vmlinuz-3.5.3-030503-generic
Found initrd image: /boot/initrd.img-3.5.3-030503-generic
Found linux image: /boot/vmlinuz-3.5.0-030500-generic
Found initrd image: /boot/initrd.img-3.5.0-030500-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
umount: /var/lib/os-prober/mount: not mounted
rmdir: failed to remove `/var/lib/os-prober/mount': Device or resource busy
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
grub-probe: error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
grub-probe: error: cannot find a GRUB drive for /dev/sda4.  Check your device.map.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
grub-probe: error: cannot find a GRUB drive for /dev/sda5.  Check your device.map.
Found Windows Recovery Environment (loader) on /dev/sda2
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Skipping Windows Recovery Environment (loader) on Wubi system
done
Setting up linux-image-extra-3.5.4-030504-generic (3.5.4-030504.201209142010) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.4-030504-generic /boot/vmlinuz-3.5.4-030504-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.4-030504-generic /boot/vmlinuz-3.5.4-030504-generic
update-initramfs: Generating /boot/initrd.img-3.5.4-030504-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.4-030504-generic /boot/vmlinuz-3.5.4-030504-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.4-030504-generic /boot/vmlinuz-3.5.4-030504-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.4-030504-generic /boot/vmlinuz-3.5.4-030504-generic
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Generating grub.cfg ...
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found linux image: /boot/vmlinuz-3.5.4-030504-generic
Found initrd image: /boot/initrd.img-3.5.4-030504-generic
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found linux image: /boot/vmlinuz-3.5.3-030503-generic
Found initrd image: /boot/initrd.img-3.5.3-030503-generic
Found linux image: /boot/vmlinuz-3.5.0-030500-generic
Found initrd image: /boot/initrd.img-3.5.0-030500-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
umount: /var/lib/os-prober/mount: not mounted
rmdir: failed to remove `/var/lib/os-prober/mount': Device or resource busy
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
grub-probe: error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
grub-probe: error: cannot find a GRUB drive for /dev/sda4.  Check your device.map.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
grub-probe: error: cannot find a GRUB drive for /dev/sda5.  Check your device.map.
Found Windows Recovery Environment (loader) on /dev/sda2
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Skipping Windows Recovery Environment (loader) on Wubi system
done
Setting up linux-headers-3.5.4-030504-generic (3.5.4-030504.201209142010) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.4-030504-generic /boot/vmlinuz-3.5.4-030504-generic
All done! Press any key to exit.

---

### Post by NikTh on 2012-09-19
> **hscriber said:**
> 
I tried again, and I here are the errors I'm getting when downloading I didn't notice last time.

error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Generating grub.cfg ...
error: cannot seek `/dev/sda'

Hi , 
this seems like a grub problem. Do you have raid 0 setup or something like this ? 

You can test boot-info script or boor-repair (creates results .txt too) and see what happened. Provide the results here so other guys can see them. 

Boot info script here : [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
OR 
Boot-repair here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can **attach **the results by clicking on **[COLOR=DarkOrange]New Reply [/COLOR]**and then click the **[COLOR=DarkOrange]paper-clip icon [/COLOR]**at message toolbar
OR
you can put them **[noparse]```
between the brackets, here
```[/noparse] **so can be readable.

Thanks

---

### Post by hscriber on 2012-09-19
```

http://paste.ubuntu.com/1215599/

```

Here's the boot-repair link.  I couldn't get boot-info to work, the sudo command wouldn't work for some reason.  Thanks for your help.

---

### Post by NikTh on 2012-09-19
Hi , 
As I can see from the results , this is a wubi install. You should have mentioned this at your First Post. 

Wubi install is not the same as regular install . Wubi is a Virtual install ONLY to test the system from some time. 
I.M.O : It is sure (as that sun will rise) wubi will generate problems in near future. 

Also I saw that you attempted to repair the installation and boot-repair took some actions . What happened ? Is your boot repaired ? 

Thanks

---

### Post by hscriber on 2012-09-19
I didn't know it was.  I'm pretty new to linux, so I wasn't aware that there was such thing.  I just googled wubi install though, and I see some things that I have different.  I do have a separate partition for ubuntu.  But, since you say it's a wubi install and since I do remember seeing that within boot repair, I'll take your word for it.  What do I need to do to get it to not be a wubi install (if that makes sense)?  I'd like to not lose all my files I have since installing ubuntu (June of 2012), but I'd like it to have full functionality at the same time.  I saw (on wikipedia granted) that if one decides they like ubuntu via wubi install that they can move it to another disk/partition, so how do I go about doing that?  I found the how-to on this forum, but I don't quite follow.  Do I need to do all those commands?  Are the usr/home/boot commands solely for those pieces, or do I do those after the first command?  If I already have 4 partitions (Windows, HP Recovery, System (Ubuntu), and Linux Files (where I keep files for ubuntu because I stupidly only made System 200 MB)), can I move what's on my System partition to my Linux Files partition?  Also, all of the partitions are ntfs file format, which I've been told is window's format and linux uses ext3 or 4.  Am I just screwed in general, or is there hope to (easily) migrate everything?

EDIT:
Also, I'm not sure what it repaired and I don't know how to check to see if it's repaired.

---

### Post by NikTh on 2012-09-20
Hi , 

don't you remember if you installed Ubuntu from inside Windows ? This is a wubi install. wubi = **W**indows-based **Ub**untu **I**nstaller. So you can test-see how Ubuntu is , without to do a regular install. 

I never used this migration, from wubi to regular. Yes I have read the how-to here: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) , but never used it for real. 
For that , I cannot guide you or  guarantee that everything will go well. 

Boot-Repair , repairs boot problems. I saw that repaired some blocks ... etc . If you had any problems with boot , now must be gone. 

Thanks

---

### Post by hscriber on 2012-09-20
I know I installed from within windows, but until I googled wubi I had no idea it existed, let alone what it was.  I always thought that when I installed ubuntu that it put it on a separate partition because when I installed it it asked me for a size to make the partition it was going on.  I'm still confused as to how it's on a different partition and still a wubi install, but that explanation would clear up why I'm having issues with suspend.  Everything I've found says suspend/hibernate isn't compatible with wubi, I'm guessing because there's no swap partition.

---

### Post by NikTh on 2012-09-20
> **hscriber said:**
>   I always thought that when I installed ubuntu that it put it on a separate partition because when I installed it it asked me for a size to make the partition it was going on. Yes , this is just a Virtual partition under NTFS filesystem. For real , Ubuntu installed in Windows like any other Windows program. If you search in Windows the Control Panel you will see Ubuntu listed under programs.
> **hscriber said:**
>  but that explanation would clear up why I'm having issues with suspend.  Everything I've found says suspend/hibernate isn't compatible with wubi, I'm guessing because there's no swap partition. 
Correct !! 

Take a look here if you decide to proceed with a regular dual-boot . 

[http://www.youtube.com/watch?v=LokDqte3sA4&feature=related](http://www.youtube.com/watch?v=LokDqte3sA4&feature=related) 

Above video is just an example I found searching youtube. You can find other tutorials if you want. 

I suggest to save all your documents - files .. etc(backup)  and proceed with a regular dual-boot. 

Thanks

---

### Post by hscriber on 2012-10-03
Ok, so I started over.  I reformatted my hard drive, made a Ubuntu Live USB, and put Windows 7 and Ubuntu on different partitions.  Still no suspend.  I've tried those scripts again and installing the newest kernel, but neither work.  The new kernel doesn't even boot, it just shows a blank red/purple screen.

---

### Post by hscriber on 2012-10-08
No more options?

---

