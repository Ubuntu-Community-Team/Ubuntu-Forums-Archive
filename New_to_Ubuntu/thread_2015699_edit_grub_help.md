---
title: "edit grub help"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-07-03
ran into a problem when trying to change grub background
here is output

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="-1"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/ray/linux wallpapers/linuxPenguinOnCloud.jpg"
when i run update grub i get this

ray@ray-GC660AA-ABA-SR5123WM:~$ sudo update-grub
[sudo] password for ray: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.5.0-3-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

does not pick up my grub background image

how should i fix sure i am overlooking something simple

---

### Post by msammels on 2012-07-03
Hey rb,

Yeah it is so simple, but not to worry, I spent a good few hours stumped. Simply see [this post](http://ubuntuforums.org/showthread.php?t=30341) for a complete know how.

---

### Post by oldfred on 2012-07-03
LInk above is to old grub legacy.

Your path is not correct. Ubuntu has not booted so /home does not yet exist. If you have not booted yet where is the file. That would then be the correct path for grub to find it. Often easier just to put in /boot/grub which I think is now all you have to do.

Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by rburkartjo on 2012-07-04
tried that putting the image in boot/grub does not fix problem
goes back to old boot image.

---

### Post by raja.genupula on 2012-07-04
This is the approach  i have tried and got success . 

* Take a image and save that image into **PNG** format and rename it as **desktop-grub.png** . 
* Lets assume you have placed that image in the home folder . 
* now open your terminal and do as 
```
sudo mv desktop-grub.png /usr/share/images/desktop-base/desktop-grub.png
```
* then ```
sudo update-grub
```

Now you can see it by restarting your PC .I am sure this thing gonna work for you because i have tried my self and got success . 

all the best .

---

### Post by rburkartjo on 2012-07-04
didnt work did as you said twice 


THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo mv desktop-grub.png /usr/share/images/desktop-base/desktop-grub.png
[sudo] password for ray: 
mv: cannot stat `desktop-grub.png': No such file or directory
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.5.0-3-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by oldfred on 2012-07-04
You are showing Ubuntu 12.04 but menu.lst? menu.lst is from grub legacy and then you may have to go back to the very old instructions on images. Why not grub2 as that has many updates and most users here know grub2 now.

---

### Post by rburkartjo on 2012-07-04
and how would i do that dont want to break grub.
get this from spm

GRand Unified Bootloader (common files for version 2) 
 
This package contains common files shared by the distinct flavours of GRUB.
The files in this package are specific to GRUB 2, and would break GRUB
Legacy if installed on the same system.

---

### Post by rburkartjo on 2012-07-04
should i just remove grub and then install grub2? what would be the proper commands?

---

### Post by DogMatix on 2012-07-04
Could you not just use grub2-splashimages [link]("https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images")

Although, I haven't installed it myself.

---

### Post by oldfred on 2012-07-04
If you can boot, you can skip the chroot and run this from your install. Just be sure you have Internet connection as it downloads the new grub2 (grub-pc).

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
> 
[LIST]
[*]Complete only steps 2 through 5.
[*]Include "sudo" at the start of each command.  Example: *sudo apt-get purge grub grub-pc grub-common *
[/LIST]


---

### Post by ENigma885 on 2012-07-04
**Grub Customizer** is good gui tool to configure grub including changing the background with few clicks.
Unfortunately, it's not available using the official repositories provided by Ubuntu. So, you'll have to add its ppa to be able to install it.

**1-** Open a terminal window and paste 

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
```

**2-** Hit enter to accept adding the new ppa

**3-** Update the repositories' lists and install Grub Customizer
```
sudo apt-get update && sudo apt-get install grub-customizer
```

**4-** Launch the program normally by searching for it using the Dash Home menu

**5-** The program will scan your grub entries once launched in few seconds. Then you can go to Preferences>>Appearance tab>>Background Image
[U]
*Note to the original poster of the thread:*[/U] It seems that you are somehow knowledgeable and prefer the command line way. Surely, we won't go into the usual debate of gui vs cli, but my post might be useful to beginners (especially that you've posted in Absolute Beginner Talk) or those who prefer a simple gui to do simple stuff.

---

### Post by rburkartjo on 2012-07-04
tks ya'll for all your advise here is how i fixed
somehow i must have deleted grub and when i re-installed i ran

 sudo apt-get install grub
thats when i started having problems

 so i took a chance and ran
sudo apt-get install grub2

that fixed the problem now if i edit this line in grub
GRUB_BACKGROUND="/home/ray/980735-1920x1080-1.jpg"

i can change the background image to anything i want as long as the path to the image is correct

---

