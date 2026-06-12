---
title: "Pretty new install taking up 14gb, what's safe to delete?"
date: 2022-03-19
forum: New to Ubuntu
---

### Post by bscruggs99 on 2022-03-19
Ok, here's what I did. I bought a used chromebook and formatted it and installed Ubuntu 20.04 on it, I've installed a few programs, vscode, gitkraken etc. nothing extravagent. I kept getting an error that I was down to 760ish mb free space so I started investivating and my 16gb drive, with basically just ubuntu and a few programs installed was taking up just over 15gb. I googled a bit and ran apt-get clean and apt-get autoremove and now I've got 2gb free space but it feels like 14gb for what's installed is insanely massive.  /usr is taking up 3.3gb but I'm not sure why. I've been using ubuntu for a while but I don't know anything about the inner workings of it so I'm a complete noob here.

What files/folders are safe to delete? I ran sudo du -k /usr  | sort -n|tail -222 and usr/lib/x86_64-linux-gnu is taking up 1gb. I'll try to include a ss of the biggest folders. 

[IMG]http://www.davidscruggs.tech/files.png[/IMG]

but I'm not sure what's in these folders and what's safe to remove. Any help is greatly appreciated. Thanks!

---

### Post by ActionParsnip on 2022-03-19
what is the output of
```

dpkg -l | grep linux-image

```
Thanks

---

### Post by bscruggs99 on 2022-03-19
I ran that and this is the output

```
rc  linux-image-4.15.0-167-generic             4.15.0-167.175                        amd64        Signed kernel image generic
rc  linux-image-4.15.0-29-generic              4.15.0-29.31                          amd64        Signed kernel image generic
ii  linux-image-5.4.0-100-generic              5.4.0-100.113                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-104-generic              5.4.0-104.118                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-97-generic               5.4.0-97.110                          amd64        Signed kernel image generic
ii  linux-image-5.4.0-99-generic               5.4.0-99.112                          amd64        Signed kernel image generic
ii  linux-image-generic                        5.4.0.104.108                         amd64        Generic Linux kernel image
```

---

### Post by ActionParsnip on 2022-03-19
A forum is a text based system. The output is text. So... Why a screenshot of text....? Paste the output of the command as an update, not a screenshot.

---

### Post by bscruggs99 on 2022-03-19
updated

---

### Post by Impavidus on 2022-03-19
On the screenshot you posted I can see some old kernel headers installed. You can remove those: linux-headers-[some version]. Use your favourite package management tools to remove them. That will save a few hundred megabytes, so it's not much of a difference. In fact, your /usr is quite small.

I'm not sure where snaps are stored, but those are big packages, so avoid them. And maybe you've got a large swap file. You may be able to get away with a smaller one.

---

### Post by GhX6GZMB on 2022-03-19
Could also be the logs in /var getting out of hand.

---

### Post by bscruggs99 on 2022-03-19
> **ml9104 said:**
> Could also be the logs in /var getting out of hand.



how do I know what in /var can be deleted?

Edit:

I just looked and /var does take up 4.9gb

---

### Post by GhX6GZMB on 2022-03-19
This will help:
[https://askubuntu.com/questions/1238214/big-var-log-journal](https://askubuntu.com/questions/1238214/big-var-log-journal)

---

### Post by TheFu on 2022-03-19
Don't run the default "Ubuntu Desktop".  That is quite a bloated DE and comes with lots and lots of extra programs.  
You don't need vscode!  The OS is the IDE. [https://blog.sanctum.geek.nz/unix-as-ide-introduction/](https://blog.sanctum.geek.nz/unix-as-ide-introduction/)
You don't need libreoffice either. There are light solutions for a word processor and spreadsheet.
You don't need any snaps.  Remove all of those and put a better DE on the box.  BTW, you don't NEED any DE either. A good window manager does all that you need. It is possible to get a usable desktop OS in under 5G, but not really using Ubuntu. Canonical doesn't care about the low-end market all that much.  They pre-install all sorts of 'convenience' packages which is both good and bad, depending on your needs.

These days, if you want to run the default Ubuntu Desktop, expect at least 4G of RAM and 40G of disk to be needed. If you want a comfortable desktop, then 8G+ of RAM and 80G of storage.

Rather than deal with trying to squeeze a development environment into a chromebook 16G, why not spend $30 and replace the SSD for a $60-$240G SSD?  That's what I did with all my chromebooks that became Ubuntu laptops. Should take 5 minutes to swap an SSD, provided the chromebook isn't used that soldiered in storage. Ewwww.

I would ask that rather than describing what you see, please run the command and post both the command + options + output here, wrapped in forum _code tags._  We are used to seeing the commands and the output. There is 10x more information than the single piece of data being posted in most of that output.

For example, 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
are extremely helpful for all storage issues.  I have aliases for those commands - they are that useful. Mainly, they only show the important stuff and hide the non-storage aspects in the outputs. They specifically remove all the snap-crap. Snaps are stored under /var/snap/, but each gets mounted separately and appears like a separate mount and storage location. They are not. You can read up on the bloat in snap packages.

Text is always preferred here.

---

### Post by MAFoElffen on 2022-03-20
16GB is a tight space for Ubuntu Desktop and Developer tools. There is a lot of bloat that you will probably never use...

Snap's (mentioned by TheFu)

LibreOffice (mentioned by TheFu)

Other app's that I do not use on my lightweight VM's:
AisleRiot Solitaire
Cheese
Livepatch
Mahjongg
Mines
Rythmbox
Shotwell
Snap Store
Sudoku
TeXInfo
Transmission
Thunderbird Mail
Videos

---

### Post by bscruggs99 on 2022-03-20
> **TheFu said:**
> Don't run the default "Ubuntu Desktop".  That is quite a bloated DE and comes with lots and lots of extra programs.  
You don't need vscode!  The OS is the IDE. [https://blog.sanctum.geek.nz/unix-as-ide-introduction/](https://blog.sanctum.geek.nz/unix-as-ide-introduction/)
You don't need libreoffice either. There are light solutions for a word processor and spreadsheet.
You don't need any snaps.  Remove all of those and put a better DE on the box.  BTW, you don't NEED any DE either. A good window manager does all that you need. It is possible to get a usable desktop OS in under 5G, but not really using Ubuntu. Canonical doesn't care about the low-end market all that much.  They pre-install all sorts of 'convenience' packages which is both good and bad, depending on your needs.

These days, if you want to run the default Ubuntu Desktop, expect at least 4G of RAM and 40G of disk to be needed. If you want a comfortable desktop, then 8G+ of RAM and 80G of storage.

Rather than deal with trying to squeeze a development environment into a chromebook 16G, why not spend $30 and replace the SSD for a $60-$240G SSD?  That's what I did with all my chromebooks that became Ubuntu laptops. Should take 5 minutes to swap an SSD, provided the chromebook isn't used that soldiered in storage. Ewwww.

I would ask that rather than describing what you see, please run the command and post both the command + options + output here, wrapped in forum _code tags._  We are used to seeing the commands and the output. There is 10x more information than the single piece of data being posted in most of that output.

For example, 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
are extremely helpful for all storage issues.  I have aliases for those commands - they are that useful. Mainly, they only show the important stuff and hide the non-storage aspects in the outputs. They specifically remove all the snap-crap. Snaps are stored under /var/snap/, but each gets mounted separately and appears like a separate mount and storage location. They are not. You can read up on the bloat in snap packages.

Text is always preferred here.


I don't mind replacing the hdd if i need to, and apparently mine is  glued in not soldered, I just didn't realize Ubuntu installs were so  massive. Ok so i ran those two commands and got the following results, for 

```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

I got 

```

Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/mmcblk0p2 ext4   14G   12G  1.6G  89% /
/dev/mmcblk0p1 vfat  511M  5.3M  506M   2% /boot/efi
/dev/mmcblk1p1 ext4  115G  140M  109G   1% /media/david/external hd

```

and for 

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

I got 

```

NAME           SIZE TYPE FSTYPE MOUNTPOINT
mmcblk0       14.7G disk        
&#9500;&#9472;mmcblk0p1    512M part vfat   /boot/efi
&#9492;&#9472;mmcblk0p2   14.2G part ext4   /
mmcblk0boot0     4M disk        
mmcblk0boot1     4M disk        
mmcblk1      116.5G disk        
&#9492;&#9472;mmcblk1p1  116.5G part ext4   /media/david/external hd


```


All I really get from that is that mmcblk0p2 is taking up basically the whole hdd. I did add an sd card that I can use as a hdd if I could figure out how to make that my default space for installs and such. But 16gb should be enough space for what I do so I'd rather just sort out my hdd. If it ends up I need to replace the hdd, I'll add more ram too as I only have 4gb i think.

---

### Post by bscruggs99 on 2022-03-20
> **ml9104 said:**
> This will help:
[https://askubuntu.com/questions/1238214/big-var-log-journal](https://askubuntu.com/questions/1238214/big-var-log-journal)



very cool, thanks. After a vacuum I freed 1.3gb. :KS

---

### Post by Impavidus on 2022-03-20
I remember that 15 years ago, when I first installed Ubuntu, it fitted in just 2GB. But in those days your typical hard drive was about 50GB. Nowadays your typical hard drive is over 1TB, so there's not much pressure to keep disk usage down. Chromebooks have very small drives to encourage you to store your data on Googles servers.

How much swap space have you got? Making that a bit less may free some more disk space.```
swapon --show
```

---

### Post by bscruggs99 on 2022-03-20
> **Impavidus said:**
> I remember that 15 years ago, when I first installed Ubuntu, it fitted in just 2GB. But in those days your typical hard drive was about 50GB. Nowadays your typical hard drive is over 1TB, so there's not much pressure to keep disk usage down. Chromebooks have very small drives to encourage you to store your data on Googles servers.

How much swap space have you got? Making that a bit less may free some more disk space.```
swapon --show
```

672mb apparently haha

```

NAME      TYPE   SIZE USED PRIO
/swapfile file 672.2M 512K   -2



```

---

### Post by grahammechanical on 2022-03-20
I am surprised that you are able to use Ubuntu. The official guide says this is what you need.

> A laptop or PC (obviously!) with at least 25GB of storage space.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

You also say this:

> I did add an sd card that I can use as a hdd if I could figure out how to make that my default space for installs

Linux is not Windows. We do not install applications/programs in their own directories. Libraries go into the OS part of Linux. Data and configuration files go into the User's part of Linux.

Why not install Ubuntu to the SSD and use the hard disk as a store for backups. Ubuntu used to have a minimum install image that installed the basic operating system with a minimal desktop environment with enough utilities to work with. The user could chose what applications to install either during the installation or after. This minimum install image is no longer supported by Ubuntu developers.

Debian still offers a minimum install image. 

[https://www.debian.org/CD/netinst/](https://www.debian.org/CD/netinst/)

[https://www.debian.org/releases/stable/amd64/](https://www.debian.org/releases/stable/amd64/)

Regards

---

### Post by bscruggs99 on 2022-03-20
> **grahammechanical said:**
> I am surprised that you are able to use Ubuntu. The official guide says this is what you need.



[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

You also say this:



Linux is not Windows. We do not install applications/programs in their own directories. Libraries go into the OS part of Linux. Data and configuration files go into the User's part of Linux.

Why not install Ubuntu to the SSD and use the hard disk as a store for backups. Ubuntu used to have a minimum install image that installed the basic operating system with a minimal desktop environment with enough utilities to work with. The user could chose what applications to install either during the installation or after. This minimum install image is no longer supported by Ubuntu developers.

Debian still offers a minimum install image. 

[https://www.debian.org/CD/netinst/](https://www.debian.org/CD/netinst/)

[https://www.debian.org/releases/stable/amd64/](https://www.debian.org/releases/stable/amd64/)

Regards



I thought I had the minimum install option when I installed Ubuntu. There was some choice, basically install everything or only install what's needed, I chose the smaller install.

---

### Post by VMC on 2022-03-20
install the small "ncdu", then from terminal ```
ncdu /
```. Then you can investigate who's using the most storage. Its a menu driven program.

---

### Post by TheFu on 2022-03-20
Based on the drive device names, it appears you cannot swap the SSD. It is using soldiered on storage.  I bet the RAM is soldiered on too, so don't expect to upgrade it either. Few Chromebooks are like normal laptops and can be upgraded.  

I think it would be better getting a 64G-256G USB3 flash storage device and running Ubuntu from that. The cheap ones are $15 now.  Expect the external storage to fail every year due to write counts - flash storage that isn't SSD doesn't allow for huge write counts.  Definitely try to get the fastest USB3 you can. Heck, they sell SSD-based external USB3 devices, if you want to get better performance and don't want to worry about write counts too much, but those are usually overpriced. You can get an m.2 SATA SSD for $40, then an external enclosure for $10-$20 for it and come out cheaper. The assembly is 3 minutes and perhaps 3 screws.  I have one of these. Works great. Sized for a 2242 SSD, about the size of a zippo lighter. While they sell the NVMe versions (instead of SATA), those are 2x the price and not really necessary unless you have a USB 3.2 10Gbps port on the chromebook.  Any USB3.1 or 3.0 will be more than blazing fast already.

Using an SDHC or MicroSD card will be slower since those slots connect to USB2 ports.  They are fine for emergency use, but definitely plan to use the USB3 port for normal stuff.  A number of friends run MX Linux this way on their laptops and have for years.  

I've run Ubuntu-Mate in this way on a media server after the OS HDD crashed and it took about a week for the replacement to arrive.

---

### Post by Tadaen_Sylvermane on 2022-03-20
If that thing has a usb slot you can plug an external in you would have space to compile some stuff. I'm using Debian right now and my root volume is using 19g, 12g of that is my home directory. 7g installed.

My list of packages minus the libraries. It's quite full featured for my use for it's small size. Because I piped out the lib packages the list is missing the full LibreOffice. I also have Google's chrome, and Kodi installed in /opt.

[https://paste.ubuntu.com/p/T4ZvvNGWFB/](https://paste.ubuntu.com/p/T4ZvvNGWFB/)

I love Ubuntu but the dependencies are a nightmare if space is your concern.

---

### Post by SeijiSensei on 2022-03-20
> **Tadaen_Sylvermane said:**
> If that thing has a usb slot you can plug an external in you would have space to compile some stuff.
With thumb drives now hitting 2 TB, you'd have a lot of space to work with.

[https://www.newegg.com/p/0BD-07B6-00009?item=9SIAVWGHB53013](https://www.newegg.com/p/0BD-07B6-00009?item=9SIAVWGHB53013)

---

### Post by bscruggs99 on 2022-03-20
> **Tadaen_Sylvermane said:**
> If that thing has a usb slot you can plug an external in you would have space to compile some stuff. I'm using Debian right now and my root volume is using 19g, 12g of that is my home directory. 7g installed.

My list of packages minus the libraries. It's quite full featured for my use for it's small size. Because I piped out the lib packages the list is missing the full LibreOffice. I also have Google's chrome, and Kodi installed in /opt.

[https://paste.ubuntu.com/p/T4ZvvNGWFB/](https://paste.ubuntu.com/p/T4ZvvNGWFB/)

I love Ubuntu but the dependencies are a nightmare if space is your concern.

I have a 128gb sd card in there now if i can use that, or i can probably find an external drive. I don't really need that much space. If I could just get about 5gb free on this ssd, I would be fine proably. It's up to around 3gb free now which is probably enough but I'd like a little wiggle room too

---

### Post by MAFoElffen on 2022-03-20
> **TheFu said:**
> Based on the drive device names, it appears you cannot swap the SSD. It is using soldiered on storage.  I bet the RAM is soldiered on too, so don't expect to upgrade it either. Few Chromebooks are like normal laptops and can be upgraded.  

I think it would be better getting a 64G-256G USB3 flash storage device and running Ubuntu from that. The cheap ones are $15 now.  Expect the external storage to fail every year due to write counts - flash storage that isn't SSD doesn't allow for huge write counts.  Definitely try to get the fastest USB3 you can. Heck, they sell SSD-based external USB3 devices, if you want to get better performance and don't want to worry about write counts too much, but those are usually overpriced. You can get an m.2 SATA SSD for $40, then an external enclosure for $10-$20 for it and come out cheaper. The assembly is 3 minutes and perhaps 3 screws.  I have one of these. Works great. Sized for a 2242 SSD, about the size of a zippo lighter. While they sell the NVMe versions (instead of SATA), those are 2x the price and not really necessary unless you have a USB 3.2 10Gbps port on the chromebook.  Any USB3.1 or 3.0 will be more than blazing fast already.

Using an SDHC or MicroSD card will be slower since those slots connect to USB2 ports.  They are fine for emergency use, but definitely plan to use the USB3 port for normal stuff.  A number of friends run MX Linux this way on their laptops and have for years.  

I've run Ubuntu-Mate in this way on a media server after the OS HDD crashed and it took about a week for the replacement to arrive.
Agreed. Storage names that start with "mmcblk", denotes Flash Storage. This naming convention denotes both SD Cards (removable) and soldered in Flash storage. That is why both your storage devices have the same naming convention...

If it where me, I would make another plan. SD cards are notoriously slow on read/write. It's not just the transfer interface, but the media read/write speed itself... Even if you had and were using a standard, cheap, external USB 2.0 HDD, it would be faster. SD type cards are not very reliable for data your care about. their original intent of existence was for for temporary storage, that is transferred to something else.  If you want to concentrate on development and learning in that arena... To be honest, you would be better off backing up your data, and starting fresh (as TheFu has hinted).

TheFu and I have some experience using XServer and other, very light DE's... I will let TheFu explain what he uses. I would start out with a minimal Ubuntu Server install, and then install minimal XServer, with i3 as my main Desktop Environment. Then install app's as you need them, or want to experiment with... Removing which one's you find you do not use or like... 

With i3, I setup 10 Workspaces, with applications that I installed, pinned to certain, specific Workspaces. Such as a graphical terminal, and Terminator pinned to Workspace 2, with Program Editors, pinned to Workspace 3, with Web Browsers pinned to Workspace 4, etc, etc... That is how I setup my own 'cooked' development platform IDE. That way I can switch between Workspaces very quickly with just a hot-key. Editing code, running it, seeing the results of... I can build and run this in less than 5 GB persistent storage, and 1 GB RAM. In testing, 2 GB storage for the core system, with 640 MB RAM... The RAM overhead is very minimal, and it is very fast. Compiling code takes a bit more RAM.

You have some very "fixed" internal storage space (and RAM) boundaries of what can be there 'internally'. I would suggest that you install your core system on the internal soldered-in flash storage (mmcblk0). Then your code and data on an external drive...

If that is too rustic for your skill level, then I would recommend starting out with a minimal Lubuntu Install base.

---

