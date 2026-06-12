---
title: "Dual-boot GRUB Issues"
date: 2018-05-23
forum: New to Ubuntu
---

### Post by awightma on 2018-05-23
Hi,

I've been running a dual boot Ubuntu / Windows8 setup for the past ~2 years with minimal issues until recently. After a routine update+restart my laptop stopped going to the grub boot menu and would instead go straight to booting Windows. In my BIOS I am able to select a particular boot option, but when I tried to boot Ubuntu it went straight to the grub command line and I wasn't sure how to boot from there.

I next tried to boot from my old Live USB with Ubuntu 14.04 and then run the Boot-repair tool from there. After doing this, my laptop seemed to load the grub2 menu properly, however, when I tried to boot Ubuntu it would just go to a blank screen with the caps lock LED repeatedly blinking. I next tried to boot from one of the Advanced Ubuntu options in the grub menu (in order).

'Ubuntu, with Linux 4.4.0-127-generic'
This boot again gave me the same blank screen and blinking caps lock key as before.

'Ubuntu, with Linux 4.4.0-127-generic (recovery mode)'
This time I got a Kernal panic, below are a few of the last lines printed out:[INDENT]VFS: Cannot open root device "sda6" or unknown-block(0,0): error -6
Please append a correct "root=" boot option; here are the available partitions:
Kernal Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
CPU: 2 PID: 1 Comm: swapper/0 Not tainted 4.4.0-127-generic #153-ubuntu
[/INDENT]

'Ubuntu, with Linux 4.4.0-116-generic (recovery mode)'
This seemed to boot successfully and everything looked ok, however, after restarting my computer I now go directly to the grub command line again. If I exit, I get back to the UEFI bios screen where I can then select a boot option, but the Ubuntu options send me back to the grub command line. The Windows boot option seems to still work just fine.

I'm really at a loss as to what to do next, aside from trying to re-run the boot-repair tool.

OS: Ubuntu 16.04 / Windows 8
Laptop: Dell Inspiron15R
BIOS Mode: UEFI, secure boot off
Boot Info: [http://paste.ubuntu.com/p/j2nMpdCgm9/](http://paste.ubuntu.com/p/j2nMpdCgm9/)

Thanks for the help!

---

### Post by yancek on 2018-05-23
> After a routine update+restart

Of what?  Windows/Ubuntu?
Is your Ubuntu 14.04?

Some major windows updates will modify the partition table to exclude any non-windows systems.  Probably the best thing to do is to post the output of the boot repair run with the Create BootInfo Summary option rather than trying to make repairs.  Posting a link to that output here should give some members a clue as to what the problem might be.

---

### Post by oldfred on 2018-05-23
Report is not showing much, it looks normal.

Since issues seems to be something with sda6, I might try fsck on it.
Did you have an abnormal or forced shutdown?

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by andrewaporter on 2018-05-23
Total newbie here, with the same or siimilar problem.
A few weeks ago I Loaded Ubuntu (14.?.?) dual boot on a Win 10 laptop. Initially I could boot into Ubuntu or Windows via Grub. Now Grub lets me into Windows but not Ubuntu. I get a blank screen with the cursor in the upper left corner.

---

### Post by wildmanne39 on 2018-05-23
Hello and welcome to the forum andrewaporter,  please start your own thread so you can get the help you need and so can the OP of this thread.

Thanks

---

### Post by awightma on 2018-05-24
Thanks all for the information! I'm currently running Ubuntu 16.04 (my liveUSB still has the 14.04 release I used to install Ubuntu originally)

Shortly after my initial post I tried re-running the boot-repair tool ([Pastebin Link]("http://paste.ubuntu.com/p/Py8vrtcD7r/")) and this time trying to boot from the default Ubuntu option gave no kernal panic and seems to be running fine. I've still not tried restarting the laptop to try running the filesystem checks, but will make sure to do so as soon as I am able.

As for the update, it was on Ubuntu for misc. software none of which seemed out of the ordinary to me at least, can't recall if GRUB would have been included in the update or not. I wasn't paying to much attention during the update and just assumed that it rebooted after it finished installing the updates, but perhaps the update is what caused the crash and the ensuing problems with GRUB were just a result of that? I had initially thought the problem was related to my dual boot setup and something Windows related, as thats what a lot of other people with similar symptoms were reporting, but I guess that was probably just a red herring.

---

