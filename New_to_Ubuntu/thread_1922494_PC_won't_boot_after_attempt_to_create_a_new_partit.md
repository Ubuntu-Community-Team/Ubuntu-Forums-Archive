---
title: "PC won't boot after attempt to create a new partition for /home"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by mameshiba on 2012-02-08
Hello all,

I:m sorry for posting this here... I:m not really a beginner at all, I:ve been using Ubuntu a while, but there:s a lot of terminology I don:t know in relation to this issue and I don;t know where else to post this. I also apologise for using colons in place of apostrophes; I:m using a Japanese keyboard on a Windows machine and can:t find the inverted comma key.

In the last few days I attempted an upgrade from 10.10 to 11.04. At first, it wouldn:t boot up at all on restarting to complete the upgrade. However using the advice in [http://ubuntuforums.org/showthread.php?t=1921344]("http://ubuntuforums.org/showthread.php?t=1921344") this post I was able to boot up from the GRUB menu and fix the login so I wouldn;t have to do that every time.

That obviously shook me up a bit as I momentarily thought I:d have lost all my files so I decided to try creating a separate partition for my /home directory to ensure their safety in the event of anything like that happening again. I was referring to the walk-through tutorial on how to do this in the community help pages.

However, when I installed GPart and looked at my hard drive it wasn:t set up how the guide anticipated, so I wasn:t sure what to do. (My laptop has only ever had Ubuntu on it; I bought it without an operating system and loaded 10.04 onto it as soon as I got it.) Furthermore, most of the options in the menus on GPart were "greyed out", and when I tried "Create new partition table" (...I think) I got an error message telling me I would have to Unmount or Swapoff the existing partitions before I could make any changes. So I tried "swapoff" on the only partition that gave me the option, but it didn:t change anything. I didn:t want to risk messing anything up, so I changed it back to "swapon" and opened Chrome to post on this forum asking for advice.

The damning irony was what happened next. I was mid-way through writing a new post, when my whole system froze. I waited and it didn:t come unstuck so I rebooted, only then it wouldn:t boot up at all. Trying to boot up from the kernel I:d set it to resulted in a blank screen and the two LEDs on my laptop marked with a padlock and the letter "A" and a padlock with an arrow pointing downwards flashing simultaneously. I tried rebooting again and booting from different kernels; each time it resulted in the system hanging, sometimes on "Checking battery state...", but a common error that came up as text was scrolling down the screen was "Starting load failback graphics devices [FAIL]". I couldn:t get it to start in recovery mode, either.

I:m at the mercy of other people letting me use their computers in trying to get this fixed, and I really do need my laptop to be working as not having access to it prevents me from studying at home and cuts me off from having any contact with my friends and family in the UK. 

Can anyone suggest a way I might get it started again without losing all my files, or is it well and truly broken and my only option to start again with a fresh install from a CD?

:(

Thanks in advance for any and all help, I:m sorry I can:t be more specific than this and that I can:t provide any screenshots.

---

### Post by WthIteh on 2012-02-09
As the first step, you can use a live CD to boot up.
Then you can mount and backup important files, for example on a flash disk, to be safe.

Then you can continue with gparted to check partitions.
NOTE: Never use "Create new partition table" since it will destroy all of your partitions and files!!!
If you can not use some options in gparted, make sure 1. all partitions are unmounted and 2. gparted is ran as root (i.e. running "sudo gparted" in terminal).
Unmounting all partitions from live CD is easy since live environment is not dependent on them. First run "mount" in terminal and see all mounted partitions. Then run "sudo umount /dev/sdaX" to unmount them individually (close all applications first). Also use "swapoff" to disable swap partition usage too.

Then you must be able to change partitions as you want. If you need advice on that step, post output of "sudo fdisk -l" command.

At last you can reinstall the grub and MBR to resolve probable boot up issues ([http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099))

---

### Post by mameshiba on 2012-02-09
Ok, thanks for getting back to me. Now I have tried to boot from a disk I burned from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) - but the following error has come up:

> EDD: Error 8000 reading sector 353246
No default or UI configuration directive found!
boot_

Um, what now? :(

---

### Post by WthIteh on 2012-02-09
Are you using a CD or a USB for booting live?
Take a look at <http://ubuntuforums.org/showthread.php?p=11109202>.

---

### Post by mameshiba on 2012-02-09
Using a CD. I have two pen drives, one is 2GB and the other is 512MB... would I be better off using one of those?

I am afraid I didn"t get the relevance of that other thread :confused:

---

### Post by yashiez on 2012-02-09
which storage Device you use to boot the PC doesnt really matter.
You must make the Pendrive bootable before you actually try to boot it..
there are number of Opensource Softwares that Can help you make the pendrive bootable and load the OS binaries into that..
 
Happy re Formatting..

---

### Post by mameshiba on 2012-02-09
Okay, using my flatmates PC - which is all in Czech, which I do not understand - I have created a bootable USB stick using the instructions here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download).

I checked the files were all named correctly, as explained in this thread: [http://ubuntuforums.org/showthread.php?t=1487937&highlight=default+ui+configuration&page=2](http://ubuntuforums.org/showthread.php?t=1487937&highlight=default+ui+configuration&page=2)

However, nothing is happening when I use the USB stick. It just goes straight to the GRUB menu. ](*,)

---

### Post by WthIteh on 2012-02-09
> **mameshiba said:**
> Using a CD. I have two pen drives, one is 2GB and the other is 512MB... would I be better off using one of those?

I am afraid I didn"t get the relevance of that other thread :confused:
No, using CD is better (easier).
That thread was about resolving "No default or UI configuration directive found" problem while using USB.

Booting from CD, first select the disk check option to be sure CD is burned correctly. If it was OK, go with "Try ubuntu witohut any change" option. If it can not boot, then try "Rescue system" option which should give you a command line for correcting previous system (this option always works since it does not require any graphic card to be detected correctly but it's a little harder since recovery must be done in pure command line).

---

### Post by mameshiba on 2012-02-09
Disk check option? I"m not getting any options at all when I try to boot from the disk... Just this:

> ISOLINUX 4.04 20110518 ETCD Copyright C 1994-2011 H. Peter Abvin et al

... followed by the error message I quoted in my previous post.

Is there something else I should be doing, like pressing "Shift" like you would to load the GRUB menu, or something like that?

---

### Post by mastablasta on 2012-02-09
your dwonloaded image could be corrupted. after download you need to perform md5sum check to see if the image is exactly the same as on the server and no data was lost during transmision. here is how you do it: 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

after you manage to boot form it you do the CD integrity test (nero does this for you as well as some other free image burning software i believe) or you can just try and boot into live session using try it from the menu

---

### Post by WthIteh on 2012-02-09
> **mameshiba said:**
> Disk check option? I"m not getting any options at all when I try to boot from the disk...
So probably disc image is not OK. Using another system you can verify burned CD using manual method described at <[https://help.ubuntu.com/community/HowToMD5SUM#Manual_method-1](https://help.ubuntu.com/community/HowToMD5SUM#Manual_method-1)>.
The calculated md5sum must match values at <[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)>.

---

### Post by mameshiba on 2012-02-09
New development: I:ve managed to get a 10.04 installer disk to start up on my machine. However, it didn:t give me a "Check disk" option, only "Try Ubuntu 10.04.3" and "Install Ubuntu 10.04.3". I went with the former, only it:s just loaded the screen you get in 10.04 before you log in and nothing else. I tried rebooting and loading from the CD again, but it:s just done the same thing again without giving me any options this time :(

> **mastablasta said:**
> your dwonloaded image could be corrupted. after download you need to perform md5sum check to see if the image is exactly the same as on the server and no data was lost during transmision. here is how you do it: 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

after you manage to boot form it you do the CD integrity test (nero does this for you as well as some other free image burning software i believe) or you can just try and boot into live session using try it from the menu

The problem with this is that I:m using a machine that:s set up in a language I don:t understand. I tried following the instructions for performing the md5sum check in Windows, but the icon that was shown in the guide wasn:t next to any of the options... I:m sorry, I know this is making this whole affair into a right ballache.

I:m starting to think that I might just be better off ordering a pack of installer CDs from the shop on the Ubuntu homepage and waiting until they arrive before I try fixing this.

I have to say though, guys, thank you **so much** for all your helpful suggestions and patience with me this far, I:m extremely grateful to all of you for trying to help!

---

### Post by WthIteh on 2012-02-09
> **mameshiba said:**
> New development: I:ve managed to get a 10.04 installer disk to start up on my machine. However, it didn:t give me a "Check disk" option, only "Try Ubuntu 10.04.3" and "Install Ubuntu 10.04.3". I went with the former, only it:s just loaded the screen you get in 10.04 before you log in and nothing else. I tried rebooting and loading from the CD again, but it:s just done the same thing again without giving me any options this time :(
In 10.04 it should looks like <[http://www.debianadmin.com/ubuntu-10-04-lucid-alpha-3-screenshots-gallery.html](http://www.debianadmin.com/ubuntu-10-04-lucid-alpha-3-screenshots-gallery.html)> and third item "Check disk for defects" should do the job.
You may also try downloading iso again (hoping this time it goes right).

---

