---
title: "How to compile the 2.6.18 kernel from kernel.org"
date: 2006-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxnewbie946 on 2006-07-17
[SIZE="5"]This thread has been replaced by _[COLOR="Orange"][the master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158")[/COLOR]_.[/SIZE]
The master kernel thread was written by me, under my new name.

---

### Post by linuxnewbie946 on 2006-07-17
Feel free to ask any questions......

---

### Post by linuxnewbie946 on 2006-07-17
PS This will be updated for each 2.6.17 kernel release through July 31.

---

### Post by Brain Juice on 2006-07-17
Im following your guide now :)  Compling as I type.

I didn't see these options however:

> Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz

Hope it doesn't matter too much.  I have an AMD 3800 and 2 GB of RAM.

---

### Post by linuxnewbie946 on 2006-07-17
It shouldn't matter too much at all.... unless you're a freak who wants the fastest computer in the world;)

---

### Post by Brain Juice on 2006-07-17
Oh Noes!! I better start over.  ;)

---

### Post by Brain Juice on 2006-07-17
OK problem.

I cant get X to load.  Tried to use my xorg.conf.backup and apt-got the fglrx-kernel-source.

What next?

---

### Post by linuxnewbie946 on 2006-07-17
> **Brain Juice said:**
> OK problem.

I cant get X to load.  Tried to use my xorg.conf.backup and apt-got the fglrx-kernel-source.

What next?

Did you follow the steps exactly?

---

### Post by Brain Juice on 2006-07-17
Yes the new kernel shows in my grub loader and boots.  Just cant load into X.  Wher could I have messed up?


ps thanks for the help.

---

### Post by linuxnewbie946 on 2006-07-17
> **Brain Juice said:**
> OK problem.

I cant get X to load.  Tried to use my xorg.conf.backup and apt-got the fglrx-kernel-source.

What next?

If you have an Nvidia graphics card you have to reinstall the drivers for it.
Backup your xorg.conf and reinstall the drivers for you graphics card.

---

### Post by linuxnewbie946 on 2006-07-17
[COLOR="Red"]PS  Every time you install a new kernel you must reinstall the graphics drivers[/COLOR]

---

### Post by Brain Juice on 2006-07-17
hmm what does your 'uname -r' say?

Mine says only 2.6.17.  maybe thats my problem?

---

### Post by linuxnewbie946 on 2006-07-17
> **Brain Juice said:**
> hmm what does your 'uname -r' say?

Mine says only 2.6.17.  maybe thats my problem?

no, it should say that

---

### Post by Brain Juice on 2006-07-17
Going to do it all over.

Thx for the patience.

---

### Post by linuxnewbie946 on 2006-07-17
I found this article on your problem: [http://kerneltrap.org/node/2384]("http://kerneltrap.org/node/2384"). Good Luck!

---

### Post by Brain Juice on 2006-07-17
Exactly my issue.  Thanks again.  Ill try this.

---

### Post by linuxnewbie946 on 2006-07-18
[COLOR="Lime"]Updated![/COLOR]

---

### Post by sebz2005 on 2006-07-18
What's the apt-get command to reinstall the nVidia drivers?

---

### Post by linuxnewbie946 on 2006-07-18
Go to [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper), use method 1, [COLOR="Red"]skip steps 1 and 2[/COLOR] but follow the rest and thats it! Good luck!

---

### Post by linuxnewbie946 on 2006-07-18
Updated....... again

---

### Post by GQed76 on 2006-07-18
When I patch i get

root@gqubuntu:/home/gqed76/Desktop# bzcat /home/gqed76/Desktop/patch-2.6.17.6.bz2| patch -p1 can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Makefile b/Makefile
|index 1700d3f..5c568d3 100644
|--- a/Makefile
|+++ b/Makefile
--------------------------
File to patch:

---

### Post by Gamebeavis on 2006-07-18
Great tutorial - works great. But, I thought 2.6.17 has built in support for the Broadcom 1390 wifi cards (the 43xx family). Mine still isnt recognized in the KDE control panel (nothing but my wired connection is listed). Do I still have to compile/install ndiswrapper if this is suppost to be a built in driver now??

---

### Post by Brain Juice on 2006-07-18
Finally got my X problem figured out.

Added nVidia to my /etc/modules file as root.  :D

---

### Post by hanzomon4 on 2006-07-19
I followed method 1 for the nvidia install. but x still refuses to start.
Any idea what could be wrong

---

### Post by KingArthur10 on 2006-07-19
Well, I attempted my first kernal compile.  Got through the whole thing with only one major hitch: my IPW 2200 card isn't working right now.  Graphics wasn't right, either, but I hadn't reinstalled my graphics card, but w/o networking, there was no point.  I made sure to checkmark the 2200 and 2100 cards in the wireless section, but still no luck.  Any ideas?

---

### Post by givré on 2006-07-19
You will need also the firmwire. I don't know for ipw2200, but for ipw2100 it's in synaptic. Have a look. 
But don't ask me more, i never did it, i just know that you need it 8)

---

### Post by dcstar on 2006-07-19
> **linuxnewbie946 said:**
> *This guide is for the stable 2.6.17 kernel from kernel.org.*
.......
[B]Before you begin, download the [latest kernel]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.6.tar.bz2") and its [performance patch]("http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.17.6.bz2").
Don't apply the patch if you are compiling a kernel other then 2.6.17 otherwise the kernel _will not compile_.[/B]

[SIZE="2"][LIST=1]
[*][COLOR="Blue"]Install the utilities needed to configure the kernel[/COLOR]
```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev
```

[*][COLOR="Blue"]Now we are going to move the kernel and unpack it.[/COLOR]
```
sudo cp linux-2.6.17.6.tar.bz2 /usr/src
```
.......
[*][COLOR="Blue"]Apply the performance patch:[/COLOR]  **Don't use if you are not patching the 2.6.17 kernel !**
```
bzcat /home/$USER/patch-2.6.17.6.bz2| patch -p1
```
[COLOR="Green"]**NOTE:** If you get this message:[/COLOR]
```
Reversed (or previously applied) patch detected!  Assume -R? [n]
```
[COLOR="Green"]Don't worry. This is normal. Press y then hit enter for each time this message comes up.[/COLOR]
.......

I believe you are making a major error, AFAIK these patch files should only be applied to the original 2.6.XX kernel, not the 2.6.XX.n versions.

When you apply any of these patches to clean 2.6.XX kernel source, you get no error messages.

The 2.6.XX.n kernels there for download already have these patches applied, and I believe they are not "Performance" patches, but patches to take the base kernel up to that version (you will notice that the patches usually gradually grow in size as the version number increases - this should mean that more code is applied as each modification is made).

"Performance" patches are done by individuals who customise the code of these "Vanilla" kernels and release their own patch files.

---

### Post by givré on 2006-07-19
> **dcstar said:**
> I believe you are making a major error, AFAIK these patch files should only be applied to the original 2.6.XX kernel, not the 2.6.XX.n versions.

When you apply any of these patches to clean 2.6.XX kernel source, you get no error messages.

The 2.6.XX.n kernels there for download already have these patches applied, and I believe they are not "Performance" patches, but patches to take the base kernel up to that version (you will notice that the patches usually gradually grow in size as the version number increases - this should mean that more code is applied as each modification is made).

"Performance" patches are done by individuals who customise the code of these "Vanilla" kernels and release their own patch files.
Right, the ck patch already contain the patch between 2.6.XX and 2.6.XX.X version. You should change your HowTo.

EDIT: ho ho, after looking at the first page, it appears that you are not applying the ck patch (what could be call a 'performance patch' since it's the idea behind) but the normal patch. It means that you are applying modifications that are already there.
Anyway, that should work but that's quite stupid.

---

### Post by linuxnewbie946 on 2006-07-19
You are absolutely right. I edited the howto to match what you have said.

---

### Post by linuxnewbie946 on 2006-07-19
> **Gamebeavis said:**
> Great tutorial - works great. But, I thought 2.6.17 has built in support for the Broadcom 1390 wifi cards (the 43xx family). Mine still isnt recognized in the KDE control panel (nothing but my wired connection is listed). Do I still have to compile/install ndiswrapper if this is suppost to be a built in driver now??

Yes, you do.

---

### Post by linuxnewbie946 on 2006-07-19
> **GQed76 said:**
> When I patch i get

root@gqubuntu:/home/gqed76/Desktop# bzcat /home/gqed76/Desktop/patch-2.6.17.6.bz2| patch -p1 can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Makefile b/Makefile
|index 1700d3f..5c568d3 100644
|--- a/Makefile
|+++ b/Makefile
--------------------------
File to patch:

You get this message because you are not in /usr/src/linux. Anyway, it doesn't matter because as people have pointed out, you do not need to apply the patch because it is not a performance patch. I have edited the howto to match these instructions. If you still want to compile the kernel, make sure you are in /usr/src/linux when you import your kernel configuration.

---

### Post by linuxnewbie946 on 2006-07-19
> **hanzomon4 said:**
> I followed method 1 for the nvidia install. but x still refuses to start.
Any idea what could be wrong

[COLOR="Blue"]Did you follow method 1 exactly? If you did make sure you added nVidia to your /etc/modules file. Here is the code to do that.[/COLOR]

```
sudo nano /etc/modules
```
[COLOR="Blue"]
Just add nVidia to the end. Good Luck![/COLOR]
[COLOR="Red"]
Thanks Brain Juice![/COLOR]

---

### Post by linuxnewbie946 on 2006-07-19
I have updated the howto so that the kernel is not the same as the performance patch.

---

### Post by WishMaster on 2006-07-19
Just followed your whole how-to. Rebooted with "2.6.17" selected in GRUB.
Black background with white letters saying: "unpacking kernel"
Then a black screen and nothing happening.

[my laptop]("http://ubuntu.vdb-studios.be/")

edit: specs from the link:
[IMG]http://ubuntu.vdb-studios.be/sysinfo.gif[/IMG] _[SIZE=4]Specs[/SIZE]_
     Pentium-M 1,4 Ghz
     512 MB RAM (2 x 256)
     Toshiba 40GB 4200rpm HDD (replaced with a new HDD after mechanic failure) 
     Intel i855GM chipset 400 MHz FSB with integrated graphics
     15" TFT display designed for 1400x1050 with 1 ext. VGA port
     Broadcom 4401 10/100 Ethernet Card
     Smart Link v.92 internal modem
     Intel PRO/Wireless 2100 802.11b card
     O2 Micro smart card reader
     SmartMedia/MMC/SD/MemoryStick reader
     1 32bit type II PCMIA CardBus slot
     1 IR, 1 IEEE 1394 (FireWire), 4 USB 2.0
     1 S-VHS out, 1 Parallell, 1 RJ-11, 1 RJ-45
     1 Headphone/Line-Out, 1 Line-In, 1 Mic-In

edit2: My processor was selected as "Pentium Pro", I changed it to "Pentium M". Maybe that was the fault?
Whatever I do, I never seem to get a "686"deb, it always compiles as "386"deb :-k

---

### Post by linuxnewbie946 on 2006-07-19
Give me your system specs

---

### Post by linuxnewbie946 on 2006-07-19
I edited the howto just this morning so you might have missed a couple of steps....

---

### Post by linuxnewbie946 on 2006-07-19
Did you install both deb files?

---

### Post by hanzomon4 on 2006-07-19
> **linuxnewbie946 said:**
> [COLOR="Blue"]Did you follow method 1 exactly? If you did make sure you added nVidia to your /etc/modules file. Here is the code to do that.[/COLOR]

```
sudo nano /etc/modules
```
[COLOR="Blue"]
Just add nVidia to the end. Good Luck![/COLOR]
[COLOR="Red"]
Thanks Brain Juice![/COLOR]

This is what I'm doing and the output:

>  sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
 sudo nvidia-xconfig
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```
```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```
```
CTRL+ALT+BACKSPACE 
```
Add nvidia to /etc/modules
Going to see if it works: Didn't work
Here is the out from /var/log/xorg.93.log 
>  Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

I get this when I try to "modprobe nvidia"
> FATAL: module nvidia not found

---

### Post by hanzomon4 on 2006-07-19
I got it to :-D  work. 
This is what I did

First I got the nvidia-kernel-source:
```
apt-get install nvidia-kernel-source
```
Next I cd to /usr/src/:
```
cd /usr/src/
```
Then I untared the nvidia-kernel-source:
```
 sudo tar -zxvf nvidia-kernel-source.tar.gz
```
Next I rebooted into the new kernel (2.6.17) logged in via the CLI and cd:
```
 cd /usr/src/modules/nvidia-kernel/nv/
```
read the README (cat README)for the last instructions
```
sudo make module
```
and 
```
sudo make install
```
and last 
```
sudo /etc/init.d/gdm restart
```
X started and I lived happily ever after.  ;)

---

### Post by WishMaster on 2006-07-19
Yes, both deb's were installed (and removed via synaptic)

---

### Post by hanzomon4 on 2006-07-19
At boot I just get a black screen no words or anything. I installed splashy buy following the howto, but I still get just a black screen, so I ran splashy test and got this output. ```
 DirectFBError [DirectFBCreate (&video->dfb)]: Initialization error
```

---

### Post by mlind on 2006-07-19
Nice looking HOWTO, but please make your instructions to utilize the use of **src** group and **fakeroot** instead of doing stuff as root user.

Instructions to this @ [http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4)

---

### Post by WishMaster on 2006-07-19
Just found this:
[https://launchpad.net/distros/ubuntu/+source/linux-meta/2.6.17.2](https://launchpad.net/distros/ubuntu/+source/linux-meta/2.6.17.2)

is it safe to download and install those deb's?  (and which one(s) do we need?)

---

### Post by linuxnewbie946 on 2006-07-19
> **WishMaster said:**
> Just found this:
[https://launchpad.net/distros/ubuntu/+source/linux-meta/2.6.17.2](https://launchpad.net/distros/ubuntu/+source/linux-meta/2.6.17.2)

is it safe to download and install those deb's?  (and which one(s) do we need?)

I am not sure if it is safe or which ones to install but I have a good guess. After compiling the kernel, you end up with 2 deb files. An image and a header. When you reboot the module is created. You should probably use the image header and module if you are going to download from there.

---

### Post by daedalusman on 2006-07-19
So I was wondering if I were to choose the athlon64 compile option would the kernel compile in 64bit mode? I currently have a 32bit setup and dont wont to mess things way up, I wont to stay 32bit. So is it alright to choose that option or should I should the k7 option? Thanks for the response.

---

### Post by linuxnewbie946 on 2006-07-19
> **daedalusman said:**
> So I was wondering if I were to choose the athlon64 compile option would the kernel compile in 64bit mode? I currently have a 32bit setup and dont wont to mess things way up, I wont to stay 32bit. So is it alright to choose that option or should I should the k7 option? Thanks for the response.

What compile option? Please give an example.

---

### Post by linuxnewbie946 on 2006-07-19
> **mlind said:**
> Nice looking HOWTO, but please make your instructions to utilize the use of **src** group and **fakeroot** instead of doing stuff as root user.

Instructions to this @ [http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4)

I will do this in a new thread and post the link in the howto. Thanks!

---

### Post by daedalusman on 2006-07-19
Under "Processor type and feature -> Processor Family" theres a list of processor families I have an athlon 64 running in 32bit mode but I want to know if setting the option "Opteron/Athlon64/Hammer/k8" option will compile the kernel in 64bit mode thus recking my setup. Otherwise I will use the "Athlon/Duron/k7" option instead to keep my 32bit system working.

---

### Post by linuxnewbie946 on 2006-07-19
Yes, it will compile the kernel in 64bit mode but you should only use this option if you hav ubuntu x64 installed on your system.

---

### Post by linuxnewbie946 on 2006-07-19
> **mlind said:**
> Nice looking HOWTO, but please make your instructions to utilize the use of **src** group and **fakeroot** instead of doing stuff as root user.

Instructions to this @ [http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1242877&postcount=4)

I tried to do this but it did not work. fakeroot is not powerful enough.

---

### Post by mlind on 2006-07-19
> **linuxnewbie946 said:**
> I tried to do this but it did not work. fakeroot is not powerful enough.

What step failed?

When you add yourself to a group, you need relogin to make the changes apply.
Choices are either to restart X, or relogin on a interactive login terminal.
gnome-terminal is not a interactive login terminal, so the trick is to use su
to force relogin.

su $USER, or su *username* will relogin as the current user.

fakeroot is even suggested by make-kpkg manual, see *man make-kpkg*.

---

### Post by sebz2005 on 2006-07-20
I got an error saying:
```
install -p    -o root -g root -m 644 debian/changelog        debian/tmp-image/usr/share/doc/kernel-image-2.6.17.6/changelog.Debian
install: cannot stat `debian/changelog': No such file or directory
make[1]: *** [real_stamp_image] Error 1
make[1]: Leaving directory `/usr/src/linux'
make: *** [kernel-image-deb] Error 2

``` What am I doing wrong?
I typed this into the terminal:
```
make-kpkg -initrd --revision=_amd64_ kernel_image kernel_headers modules_install
```

Edit:
My bad... Never mind.
Do I install the nVidia drivers after updating the kernel or after a reboot?

---

### Post by linuxnewbie946 on 2006-07-20
Don't reboot w/o installing them!

---

### Post by linuxnewbie946 on 2006-07-20
> **mlind said:**
> What step failed?

When you add yourself to a group, you need relogin to make the changes apply.
Choices are either to restart X, or relogin on a interactive login terminal.
gnome-terminal is not a interactive login terminal, so the trick is to use su
to force relogin.

su $USER, or su *username* will relogin as the current user.

fakeroot is even suggested by make-kpkg manual, see *man make-kpkg*.
```

fakeroot make-kpkg clean
```

Does not work. It says you need root privliges.

---

### Post by adam.tropics on 2006-07-20
Ok, call me a sceptic, but there are quite a few kernel howto guides around, and as a rule, you will see 'runs much fatser'. Now whilst I am not meaning to suggest you're making that up, define faster.....boot up, start applications, just a general more snappy feel....?

---

### Post by linuxnewbie946 on 2006-07-20
Faster= Bootup,apps........(mostly bootup)

---

### Post by mlind on 2006-07-20
> **linuxnewbie946 said:**
> ```

fakeroot make-kpkg clean
```

Does not work. It says you need root privliges.

If you have prepared kernel tree as a root, it will fail... But I guess you know that. 
Did you do the _whole_ process without using root privileges?

---

### Post by linuxnewbie946 on 2006-07-20
> **mlind said:**
> If you have prepared kernel tree as a root, it will fail... But I guess you know that. 
Did you do the _whole_ process without using root privileges?

I made a mistake. I tested the whole fakeroot process. Right now it is compiling the kernel. Hopefully I won't get any more errors!

EDIT: I am writing a new howto as I compile.

---

### Post by linuxnewbie946 on 2006-07-20
I submitted the new howto so it should be out in a couple hours.

EDIT: HERE IT IS: [http://ubuntuforums.org/showthread.php?t=219669]("http://ubuntuforums.org/showthread.php?t=219669")

---

### Post by ErikTheRed on 2006-07-20
I highly recommend this patchset: [Beyond]("http://iphitus.loudas.com/beyond.html")

---

### Post by mlind on 2006-07-20
> **linuxnewbie946 said:**
> I submitted the new howto so it should be out in a couple hours.

EDIT: HERE IT IS: [http://ubuntuforums.org/showthread.php?t=219669]("http://ubuntuforums.org/showthread.php?t=219669")

Nice that you've the time and energy to contribute for the community. Here's what I would change
[LIST]
[*]No need to add **src** user, there's already existing group for that. Just add current *user* to src group, and force relogin using su *user*
[*]You don't need the xhost stuff, because current user already has permissions for X
[*]Only use fakeroot for make-kpkg commands, no need for anything else. So you don't need fakeroot for tarring, symlinking on copying.
```

ln -sf *target* *source*

```


[/LIST]

---

### Post by linuxnewbie946 on 2006-07-20
> **mlind said:**
> Nice that you've the time and energy to contribute for the community. Here's what I would change
[LIST]
[*]No need to add **src** user, there's already existing group for that. Just add current *user* to src group, and force relogin using su *user*
[*]You don't need the xhost stuff, because current user already has permissions for X
[*]Only use fakeroot for make-kpkg commands, no need for anything else. So you don't need fakeroot for tarring, symlinking on copying.
```

ln -sf *target* *source*

```


[/LIST]

Ok I'll edit it thanks!

EDIT: I fixed it

---

### Post by WishMaster on 2006-07-20
Just followed the tutorial *again.*
Still won't boot up. 
Booted with "2.6.17 (memory check)" and that gave:

> [4294687.273000] EIP: [<c029f6349>]qdisc_rest +0x4/0x20 SS: ESP 0068:c1467ef0
[4294687.273000] <0>Kernel panic - not syncing: Fatal exeption in interrupt

---

### Post by linuxnewbie946 on 2006-07-20
> **WishMaster said:**
> Just followed the tutorial *again.*
Still won't boot up. 
Booted with "2.6.17 (memory check)" and that gave:

It seems like there was a package break when you installed the kernel. Otherwise you probably have an extermely buggy version of Ubuntu installed.

---

### Post by linuxnewbie946 on 2006-07-20
I found this on google: If you said Y or M to ACPI video support you must apply the patches posted later." The result of this issue is a hard-freeze kernel panic.

---

### Post by linuxnewbie946 on 2006-07-20
I sent you a private message on what to do next wishmaster.

---

### Post by mlind on 2006-07-20
> **linuxnewbie946 said:**
> Ok I'll edit it thanks!

EDIT: I fixed it

Looks very good. You can remove "sudo adduser $USER src" from step 2, it's not needed at all.
For executing both *kernel_headers* and *kernel_image* targets, you can use **binary-arch**.

Thanks for your HOWTO, I'll use it later myself for reference.

---

### Post by linuxnewbie946 on 2006-07-20
thanks, I'll do that

---

### Post by WishMaster on 2006-07-20
Yeey, it works now

Although setting up aiglx isn't possible (no dri-modules for this kernel)

Guess I have to wait for Edgy then :P

---

### Post by linuxnewbie946 on 2006-07-20
Glad to help!

---

### Post by sebz2005 on 2006-07-21
> **linuxnewbie946 said:**
> Don't reboot w/o installing them!

What do I do if I lost power?

---

### Post by linuxnewbie946 on 2006-07-21
boot into an older kernel and install them

---

### Post by sebz2005 on 2006-07-21
YES!!!! I did it!

[CENTER][SIZE=3][COLOR=Black]**Note: Non-Legacy drivers!!**[/COLOR][/SIZE]
[/CENTER]

I still booted to X because I hadn't updated to the nVidia drivers, and I downloaded the *.run package off the nVidia website.
Moved to a console (Alt+Ctrl+Shift+F1) and shut down X using "sudo /etc/init.d/gdu stop"
Ran the package as root. It says it needs a package from nVidia.com. Select yes. Replys saying cant find one, will create one instead.
Go ahead with it.
Let it install.

Back at the console, get the glx by typing "sudo apt-get install nvidia-glx"
Enter "sudo nano /etc/modules"
Add at the end "nvidia <New line> glx"
Type "Sudo /etc/init.d/gdm start"

Should load.

---

### Post by linuxnewbie946 on 2006-07-21
The guide has been majorly updated for efficiency.

---

### Post by nismohasan on 2006-07-21
i used to run IDE drives and today i finally went and got myself a sata2 drive, i used my old kernel config file and that didnt let me boot up the kernel, i'm assuming because i removed something needed for the sata2 drive?

kernel craps out and mentions stuff about sata drives.. 

here is my kernel.config what have i disabled that is needed to sucesfully boot my kernel? (2.6.17 + beyond2.1 patch)

[http://members.westnet.com.au/husky87/kernelconfig.txt](http://members.westnet.com.au/husky87/kernelconfig.txt)

---

### Post by mrojas73 on 2006-07-21
Hi!  I have a very stable system right now, my kernel is 2.6.15.26-386. I have Dreamweaver running under wine.  Also, my video card is an ATI Radeon Xpress 200M on my compaq Presario V2000.  Will I have to reinstall my applications (I am more concerned with DW), and If I have to re-install the vido card drivers, can I do it after the upgrade?

Thanks in advance!

---

### Post by nismohasan on 2006-07-22
> **mrojas73 said:**
> Hi!  I have a very stable system right now, my kernel is 2.6.15.26-386. I have Dreamweaver running under wine.  Also, my video card is an ATI Radeon Xpress 200M on my compaq Presario V2000.  Will I have to reinstall my applications (I am more concerned with DW), and If I have to re-install the vido card drivers, can I do it after the upgrade?

Thanks in advance!

you wont need to reinstall your applications.

---

### Post by kinematic on 2006-07-22
> **nismohasan said:**
> i used my old kernel config file and that didnt let me boot up the kernel, i'm assuming because i removed something needed for the sata2 drive?
[http://members.westnet.com.au/husky87/kernelconfig.txt](http://members.westnet.com.au/husky87/kernelconfig.txt)

do you know what driver it needs?....it may simply not be supported yet.
and on another note...why are you leaving so much stuff in it?
take out everything for hardware that you don't have....why would you wanna compile drivers into the kernel or as modules if you don't need them?
you'll end up with a much leaner kernel that boots a lot faster.

---

### Post by PingunZ on 2006-07-22
Nice guide ;)
here is my sugestion: [add this]("http://ubuntuforums.org/showpost.php?p=1174954&postcount=507") 
btw :: wouldn't it be great if we had an app that made all this for us, so we didn't have to select it by ouselves :p

Grtz PingunZ

---

### Post by hard_i on 2006-07-22
so .. got it working.
Except fglrx. This happens when building fglrx.
```

 make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.6'             &#9618;
 &#9474; /usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile:38:                    &#9618;
 &#9474; /usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile.cpu: No such file or   &#9618;
 &#9474; directory                                                                  &#9618;
 &#9474; make[1]: *** No rule to make target                                        &#9618;
 &#9474; `/usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile.cpu'.  Stop.          &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.6'              &#9618;
 &#9474; make: *** [build] Error 2

```

---

### Post by mlind on 2006-07-22
> **hard_i said:**
> so .. got it working.
Except fglrx. This happens when building fglrx.
```

 make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.6'             
 &#9474; /usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile:38:                    
 &#9474; /usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile.cpu: No such file or   
 &#9474; directory                                                                  
 &#9474; make[1]: *** No rule to make target                                        
 &#9474; `/usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile.cpu'.  Stop.          
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.6'              
 &#9474; make: *** [build] Error 2

```

tseliot posted the fix on another thread. You need to copy Makefile.cpu from **kernel source** tree to /usr/src/kernel-headers-2.6.17.6/arch/i386/

```

sudo cp /usr/src/linux-2.6.17.6/arch/i386/Makefile.cpu /usr/src/kernel-headers-2.6.17.6/arch/i386/

```

---

### Post by hard_i on 2006-07-22
ok.. thanks.
now i'm getting this >
```
 WARNING: Symbol version dump                                             &#9618;
 &#9474; /usr/src/kernel-headers-2.6.17.6/Module.symvers                            &#9618;
 &#9474;            is missing; modules will have no dependencies and modversions.  &#9618;
 &#9474;                                                                            &#9618;
 &#9474; ln: creating symbolic link `./Makefile.lib.c' to                           &#9618;
 &#9474; `../scripts/Makefile.lib.c': File exists                                   &#9618;
 &#9474; make[2]: *** [scripts/Makefile.lib.c] Error 1                              &#9618;
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.6'              &#9618;
 &#9474; make: *** [build] Error 2

```

---

### Post by mlind on 2006-07-22
> **hard_i said:**
> ok.. thanks.
now i'm getting this >
```
 WARNING: Symbol version dump                                             
 &#9474; /usr/src/kernel-headers-2.6.17.6/Module.symvers                            
 &#9474;            is missing; modules will have no dependencies and modversions.  
 &#9474;                                                                            
 &#9474; ln: creating symbolic link `./Makefile.lib.c' to                           
 &#9474; `../scripts/Makefile.lib.c': File exists                                   
 &#9474; make[2]: *** [scripts/Makefile.lib.c] Error 1                              
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.6'              
 &#9474; make: *** [build] Error 2

```

Try deleting the symlink that causes error.

---

### Post by hard_i on 2006-07-22
ok
when i remove the symlink i get
```
 gcc: scripts/Makefile.lib.c: No such file or directory
```
and when i don't, then it won't compile because it _is_ there.
w t f

---

### Post by Ike_ on 2006-07-22
Great great great HOWTO, fixed my problem with the default kernels (all through 2.6.15-26-686) being very jerky (everything from awful mplayer performance and animations to jerky and slow key repeat rate regardless of the setting).

Customized kernel works flawlessly, very smooth and quick.  My only problem is if I build a kernel without SMP enabled, X won't load.  I use the kernel's i810 module (for my i915) and it modprobes fine, but X gives a "no screens found" message.

If anyone knows why that is, I would love know but it is only a minor inconvenience as all other configurations with SMP enabled seem to work great.  Thank you!

---

### Post by Slicedbread on 2006-07-22
> **hard_i said:**
> ok
when i remove the symlink i get
```
 gcc: scripts/Makefile.lib.c: No such file or directory
```
and when i don't, then it won't compile because it _is_ there.
w t f

Hey I noticed that it was giving me those errors a while back also, it seems to not copy those files at all. I never got it to compile, but if just use the installer from ati it works perfectly fine, installs the modules and all.

just do sudo sh <name of ati installer>

---

### Post by hard_i on 2006-07-22
> **Slicedbread said:**
> Hey I noticed that it was giving me those errors a while back also, it seems to not copy those files at all. I never got it to compile, but if just use the installer from ati it works perfectly fine, installs the modules and all.

just do sudo sh <name of ati installer>
Weee... thanks, it works now.

---

### Post by mrojas73 on 2006-07-23
Hello, I need some help here!  I compiled a kernel for an IBM laptop withount any problems.  Now I am trying to do my compaq laptop and I can't make it pass step 4.  When I issue the make xconfig command I get the following error message:

mrojas@Compaq-Ubuntu:/usr/src$ cd linux
mrojas@Compaq-Ubuntu:/usr/src/linux$ sudo cp /boot/config-`uname -r` .config
mrojas@Compaq-Ubuntu:/usr/src/linux$ sudo make xconfig
/usr/bin/make: /usr/bin/make: cannot execute binary file
mrojas@Compaq-Ubuntu:/usr/src/linux$

I have tried it several times, which could be part of the problem.  I am just a noob trying to learn, so any help would be appreciated!

---

### Post by xXx 0wn3d xXx on 2006-07-23
> **mrojas73 said:**
> Hello, I need some help here!  I compiled a kernel for an IBM laptop withount any problems.  Now I am trying to do my compaq laptop and I can't make it pass step 4.  When I issue the make xconfig command I get the following error message:

mrojas@Compaq-Ubuntu:/usr/src$ cd linux
mrojas@Compaq-Ubuntu:/usr/src/linux$ sudo cp /boot/config-`uname -r` .config
mrojas@Compaq-Ubuntu:/usr/src/linux$ sudo make xconfig
/usr/bin/make: /usr/bin/make: cannot execute binary file
mrojas@Compaq-Ubuntu:/usr/src/linux$

I have tried it several times, which could be part of the problem.  I am just a noob trying to learn, so any help would be appreciated!

Make sure you have build-essential installed.
> sudo apt-get install build-essential

---

### Post by nismohasan on 2006-07-23
> **kinematic said:**
> do you know what driver it needs?....it may simply not be supported yet.
and on another note...why are you leaving so much stuff in it?
take out everything for hardware that you don't have....why would you wanna compile drivers into the kernel or as modules if you don't need them?
you'll end up with a much leaner kernel that boots a lot faster.

[http://members.westnet.com.au/husky87/beyondkernel.config.txt](http://members.westnet.com.au/husky87/beyondkernel.config.txt)


how'd i do this time? i removed alot of crap that i don't need, made sure the chipset stuff i needed was there but kernel still won't boot; it gets up to something about sata 1.5gbps and stops

> 
hasan@nismo-oobuntoo:~$ sudo lspci
pcilib: Cannot open /sys/bus/pci/devices
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


---

### Post by mrojas73 on 2006-07-23
> **xXx 0wn3d xXx said:**
> Make sure you have build-essential installed.

It says that it is already installed.  I tried again and I came back to the same error.

One thing I have been doing is running the commands in root: sudo -s -H, otherwise I get errors. That could be part of the problem, but whatever I currupted I don't know what it is.

Here is the list of files inside my /usr/src/linux files.  I don't know it could help you help me, but here it is just in case.

drwxrwxrwx 19 root root  4096 2006-07-23 13:21 .
drwxrwsr-x  3 root src   4096 2006-07-23 13:20 ..
drwxrwxrwx 26 root root  4096 2006-07-15 12:00 arch
drwxrwxrwx  2 root root  4096 2006-07-15 12:00 block
-rw-r--r--  1 root root 69876 2006-07-23 13:21 .config
-rw-rw-rw-  1 root root 18693 2006-07-15 12:00 COPYING
-rw-rw-rw-  1 root root 89536 2006-07-15 12:00 CREDITS
drwxrwxrwx  2 root root  4096 2006-07-15 12:00 crypto
drwxrwxrwx 55 root root  4096 2006-07-15 12:00 Documentation
drwxrwxrwx 59 root root  4096 2006-07-15 12:00 drivers
drwxrwxrwx 59 root root  4096 2006-07-15 12:00 fs
-rw-rw-rw-  1 root root   462 2006-07-15 12:00 .gitignore
drwxrwxrwx 40 root root  4096 2006-07-15 12:00 include
drwxrwxrwx  2 root root  4096 2006-07-15 12:00 init
drwxrwxrwx  2 root root  4096 2006-07-15 12:00 ipc
-rw-rw-rw-  1 root root  1273 2006-07-15 12:00 Kbuild
drwxrwxrwx  4 root root  4096 2006-07-15 12:00 kernel
drwxrwxrwx  5 root root  4096 2006-07-15 12:00 lib
lrwxrwxrwx  1 root root    23 2006-07-23 13:21 linux -> /usr/src/linux-2.6.17.6
-rw-rw-rw-  1 root root 70564 2006-07-15 12:00 MAINTAINERS
-rw-rw-rw-  1 root root 44697 2006-07-15 12:00 Makefile
drwxrwxrwx  2 root root  4096 2006-07-15 12:00 mm
drwxrwxrwx 36 root root  4096 2006-07-15 12:00 net
-rw-rw-rw-  1 root root 16538 2006-07-15 12:00 README
-rw-rw-rw-  1 root root  3065 2006-07-15 12:00 REPORTING-BUGS
drwxrwxrwx  8 root root  4096 2006-07-15 12:00 scripts
drwxrwxrwx  4 root root  4096 2006-07-15 12:00 security
drwxrwxrwx 16 root root  4096 2006-07-15 12:00 sound
drwxrwxrwx  2 root root  4096 2006-07-15 12:00 usr

Thank you again!

---

### Post by tseliot on 2006-07-23
> **hard_i said:**
> so .. got it working.
Except fglrx. This happens when building fglrx.
```

 make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.6'             &#9618;
 &#9474; /usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile:38:                    &#9618;
 &#9474; /usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile.cpu: No such file or   &#9618;
 &#9474; directory                                                                  &#9618;
 &#9474; make[1]: *** No rule to make target                                        &#9618;
 &#9474; `/usr/src/kernel-headers-2.6.17.6/arch/i386/Makefile.cpu'.  Stop.          &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.6'              &#9618;
 &#9474; make: *** [build] Error 2

```

That's easy to fix. Type:

```
sudo cp /usr/src/name_of_your_source/arch/i386/Makefile.cpu /usr/src/kernel-headers-`uname -r`/arch/i386/
```


NOTE: you have to replace "name_of_your_source" with the name of your source, such as linux-2.6.16, etc.)
file.pngCode:

```
cd /usr/src/kernel-headers-`uname -r`/
```
```

sudo make prepare
```

```
sudo make prepare scripts

```

Then try ATI's installer again

---

### Post by hard_i on 2006-07-23
> **tseliot said:**
> That's easy to fix. Type:

```
sudo cp /usr/src/name_of_your_source/arch/i386/Makefile.cpu /usr/src/kernel-headers-`uname -r`/arch/i386/
```


NOTE: you have to replace "name_of_your_source" with the name of your source, such as linux-2.6.16, etc.)
file.pngCode:

```
cd /usr/src/kernel-headers-`uname -r`/
```
```

sudo make prepare
```

```
sudo make prepare scripts

```

Then try ATI's installer again
umm.. yeah. Thanks for the effort.
But i can't try it out anymore,cause i got it working with ati installer already.

---

### Post by hfdragon on 2006-07-23
I have another way for the fglrx drivers but I find it UGLY ;-)


I force the installation of the .deb file created when compiling thje kernel and configures the driver... and I now have no problems running Xgl/compiz ;-)

```
sudo dpkg -i --force-depends fglrx-*2.6.17*.deb

Sélection du paquet fglrx-kernel-2.6.17 précédemment désélectionné.
(Lecture de la base de données... 139160 fichiers et répertoires déjà installés.)
Dépaquetage de fglrx-kernel-2.6.17 (à partir de fglrx-kernel-2.6.17_8.25.18-1+686_i386.deb) ...
dpkg : fglrx-kernel-2.6.17 : problèmes de dépendances, mais configuration comme demandé :
 fglrx-kernel-2.6.17 dépend de xorg-driver-fglrx (= 8.25.18-1) ; cependant :
  La version de xorg-driver-fglrx sur le système est 7.0.0-8.25.18+2.6.15.11-3.
```

The big problem I have is that the package is marked as broken in synaptics, so each time I want to update another package, or install a new one, it gets uninstalled, so I need to reinstall it manually....

---

### Post by hfdragon on 2006-07-23
I also have two other problems with this kernel : 

- no iptable support (it's the message I get when starting firestarster)!
- no bootsplash (?!) : I have a beatiful black screen when starting ubuntu until I have the login screen....

Did I miss something when configuring the kernel ?

---

### Post by kinematic on 2006-07-23
no you didn't.
i compiled the 2.6.17.6 kernel on PCLinuxOS and i also don't have iptables support.
i asked about it on the kernel mailing list but i haven't gotten an answer yet.

---

### Post by galactus51 on 2006-07-23
Ok Guys, very good tutorial. Really great. The compilation works fine, the system is very fast. But I'm having two problems (untill now): I can't access my USB card and my other two HDs. Ubuntu says that they're already mounted or busy.

I'm sure that I have not changed anything about USB and file systems supports. Any ideas?

---

### Post by kinematic on 2006-07-23
btw...this is what the readme says that comes with the 2.6.17.6 sources:
Do NOT use the /usr/src/linux area! This area has a (usually
incomplete) set of kernel headers that are used by the library header
files.  They should match the library, and not get messed up by
whatever the kernel-du-jour happens to be.

am i missing something?

---

### Post by galactus51 on 2006-07-23
So, that's mean: do not use /urs/src/linux?

---

### Post by kinematic on 2006-07-23
well...the kernel devs wouldn't put it in there for nothing.
and personally i've never had a problem with building from /usr/src/linux-2.6.whatever.
a simple xconfig,make and make modules_install has always worked for me(haven't build a custom kernel on ubuntu yet tho).

---

### Post by moore.bryan on 2006-07-24
this is a great tutorial, except for some problems on my machine... but individual settings is what linux is all about, right?  one question, though... the arch is for i386; where's the i686?

---

### Post by Ike_ on 2006-07-25
The HOWTO is arch-agnostic.  The only reference to i386 is in the revision parameter passed to make-kpkg and that is basically only used as a version number to identify separate kernel builds, you can change it to whatever you like.

You set up the kernel for your arch mostly in the kernel configuration step by selecting the most appropriate options from the "Processor type and features" menu.

---

### Post by mlind on 2006-07-25
> **kinematic said:**
> no you didn't.
i compiled the 2.6.17.6 kernel on PCLinuxOS and i also don't have iptables support.
i asked about it on the kernel mailing list but i haven't gotten an answer yet.

This is common gotcha. You need include Netfilter Xtables support from Networking -> Networking options -> Network packet filtering ->  Core netfilter configuration.

/edit
you should probably build all iptables related features as modules.

---

### Post by moore.bryan on 2006-07-27
> **Ike_ said:**
> The HOWTO is arch-agnostic.  The only reference to i386 is in the revision parameter passed to make-kpkg and that is basically only used as a version number to identify separate kernel builds, you can change it to whatever you like.

You set up the kernel for your arch mostly in the kernel configuration step by selecting the most appropriate options from the "Processor type and features" menu.

thanks for the info; much appreciated!

---

### Post by menapole on 2006-07-27
**I got the following error when trying the compile.  I tried the whole process twice.  This is my first try at doing this so I have no clue how to tell what might be wrong.  Any help is appreciated.**

drivers/media/dvb/ttpci/budget-av.c: In function ‘frontend_init’:
drivers/media/dvb/ttpci/budget-av.c:1063: error: ‘struct budget_av’ has no member named ‘reinitialise_demod’
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member ‘tuner_ops’ in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: ‘philips_cu1216_tuner_set_params’ undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in.)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

---

### Post by ZoltanPatay on 2006-07-27
Doesn't compile if DVB_BUDGET_AV is set.

Accidently one of the kernel developers submitted the wrong patch appearently.

Simply unset the following (change from module to nothing)

Device Drivers -> Multimedia Devices -> Digital Broadcasting Devices -> 

Budget cards
Budget cards with onboard CI connector
Budget cards with Budget Patch
AV7110 cards with BudgetParch

after you resaved the new config check it by:

cat /usr/src/linux/.config | grep DVB_BUDGET

what should return:

# CONFIG_DVB_BUDGET is not set
# CONFIG_DVB_BUDGET_CI is not set
# CONFIG_DVB_BUDGET_AV is not set

;-)

---

### Post by operationsone on 2006-07-28
@ ZoltanPatay 

that did the trick for me. Could you share how you came to the conclusion that those specific drivers were causing the problem ?

Thank you.

---

### Post by mozE- on 2006-07-28
> **menapole said:**
> **I got the following error when trying the compile.  I tried the whole process twice.  This is my first try at doing this so I have no clue how to tell what might be wrong.  Any help is appreciated.**

drivers/media/dvb/ttpci/budget-av.c: In function &#8216;frontend_init&#8217;:
drivers/media/dvb/ttpci/budget-av.c:1063: error: &#8216;struct budget_av&#8217; has no member named &#8216;reinitialise_demod&#8217;
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member &#8216;tuner_ops&#8217; in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: &#8216;philips_cu1216_tuner_set_params&#8217; undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in.)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

Ya I got the same problem :-x

---

### Post by nismohasan on 2006-07-28
if anyone could help with my problem, i still am unable to get the kernel to boot succesfully since i added my new SATA drive to the system.

hasan@nismo-oobuntoo:~$ sudo lspci
pcilib: Cannot open /sys/bus/pci/devices
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

a link to my current config is here (im also using the latest beyond patch available at this time 2.2)

[http://www.members.westnet.com.au/husky87/latest.config](http://www.members.westnet.com.au/husky87/latest.config)

if i use the kernel config from the default ubuntu kernel it boots so i'm missing some option in xconfig plz assist :)

---

### Post by hype on 2006-07-29
Are there any known issues with latest ATI drivers?

I have compiled and installed the custom kernel but when booting i get a black screen for a few seconds and then reboot.

 I installed  fglrx-kernel-source and replace "fglrx" by "vesa" in my xorg.conf. After kernel loaded, Ubuntu starts , but with a black screen. I thought it was a crash but i saw hard-drive was working. After a few seconds, im at login screen.
 Seems like ive lost the graphical interface of the boot process.(you know where it says "mounting root file system..." etc).Anyway, i know have GDM working.

The thing is: i get no hardware acceleration when putting back "fglrx" into my xorg.conf.

 Do i need to reinstall ATI drivers? I actually have these drivers installed. Is a simple re-install of xorg-driver-fglrx via sinaptik and a reboot enough to solve the problem? (i remove xorg-driver-fglrx then reinstall it?)
 
The thing that bothers me is that at last kernel update (2.6.15.26), as far sa i remember, i did not have to reinstall ATI drivers.

 Is there a way to integrate ATI latest drivers into the kernel so that it works without the need of reinstaling drivers manually?

Cheers

EDIT: i was just wondering, maybe a sudo dpkg-reconfigure xserver-xorg wont hurt? Does this command only "resets" xorg.conf, or any other stuff?(need to know if i have to backup anything more than my xorg.conf)

---

### Post by kremso on 2006-07-29
Hi, I compiled the kernel and installed the packages, but it won't boot.

I'm getting theese messages:

```

modprobe FATAL Could not load /lib/modules/2.6.17.7/modules.dep

mount failed
   mounting none on /proc failed
   mounting udev on /dev failed

```

Next erorr messages are following and booting stops at Mounting root filesystem.

Any ideas how to fix this?

---

### Post by trafiq on 2006-07-30
Heh i have amd64 when i compile this kernel.
I restart PC and i have bad msg:

kernel direct mapping tables up to 100000000 @ 8000-8000

any idea?:(

---

### Post by hype on 2006-07-30
Ok so i ****** up my Ubuntu when trying to get these ATI driver to work with my new kernel. X server just crashes as i followed the steps to reinstall my drivers properly.
 I'll wait a bit and try to understand better kernel compilation then try again.
 If someone sees a guide to properly compile kernel 2.6.17 and have it work properly with a ATI card, let me know... ;)

---

### Post by shiver on 2006-07-30
I felt adventurous and had a try at a kernel compile. I have done it before with Suse and had nothing but problems. I used the beyond2.2 patchset. On the first try iptables wasn't working as mentioned above and I also had missed via-agp which I need for DRI. I recompiled and got them working. But I still have one problem: I can't mount my secondary hard drive (hdb1) at all. All partitions on hda work normally but the hdb disk (which has only one partition) won't mount no matter what. I get this error message:

mount: /dev/hdb1 already mounted or /media/hdb1 busy

I tried removing it from fstab and mounting it manually afterwards, but it didn't help. The disk isn't show up on mount, either. It's NTFS which I have recently been playing with full write access using ntfs-3g but I doubt that's the problem since it works normally on the standard Ubuntu kernel. Any ideas? I'd hoped I'd finally get a self-compiled kernel fully working. :(

Here's the dmesg output. Ignore the hda5 errors, it's a dummy partition I left to prevent partitions from renumbering when I merged them.


```
[    0.000000] Linux version 2.6.17-beyond2.2 (samppa@ameba) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Sun Jul 30 21:26:56 EEST 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
[    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 511MB LOWMEM available.
[    0.000000] On node 0 totalpages: 131052
[    0.000000]   DMA zone: 4096 pages, LIFO batch:0
[    0.000000]   Normal zone: 126956 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6e20
[    0.000000] ACPI: RSDT (v001 ASUS   A7V266-E 0x30303031 MSFT 0x31313031) @ 0x1ffec000
[    0.000000] ACPI: FADT (v001 ASUS   A7V266-E 0x30303031 MSFT 0x31313031) @ 0x1ffec080
[    0.000000] ACPI: BOOT (v001 ASUS   A7V266-E 0x30303031 MSFT 0x31313031) @ 0x1ffec040
[    0.000000] ACPI: DSDT (v001   ASUS A7V266-E 0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Detected 1544.570 MHz processor.
[   20.231114] Built 1 zonelists
[   20.231119] Kernel command line: root=/dev/hda7 ro quiet
[   20.231352] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   20.231364] mapped APIC to ffffd000 (0140a000)
[   20.231369] Enabling fast FPU save and restore... done.
[   20.231372] Enabling unmasked SIMD FPU exception support... done.
[   20.231376] Initializing CPU#0
[   20.231469] Event source pit configured with caps set: 07
[   20.231473] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   20.232295] Console: colour VGA+ 80x25
[   20.232813] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.233231] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.250934] Memory: 512040k/524208k available (1936k kernel code, 11584k reserved, 563k data, 228k init, 0k highmem)
[   20.250940] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.310346] Calibrating delay using timer specific routine.. 3090.74 BogoMIPS (lpj=1545373)
[   20.310396] Security Framework v1.0.0 initialized
[   20.310404] SELinux:  Disabled at boot.
[   20.310561] Mount-cache hash table entries: 512
[   20.310742] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[   20.310751] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[   20.310760] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.310763] CPU: L2 Cache: 256K (64 bytes/line)
[   20.310766] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[   20.310789] Checking 'hlt' instruction... OK.
[   20.314435] SMP alternatives: switching to UP code
[   20.314621] Freeing SMP alternatives: 16k freed
[   20.314822] checking if image is initramfs... it is
[   20.718519] Freeing initrd memory: 4009k freed
[   20.719458] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.720861] ACPI: setting ELCR to 0200 (from 0e00)
[   20.745633] CPU0: AMD Athlon(TM) XP1800+ stepping 02
[   20.745640] SMP motherboard not detected.
[   20.745643] Local APIC not detected. Using dummy APIC emulation.
[   20.745709] Brought up 1 CPUs
[   20.745733] migration_cost=0
[   20.746088] NET: Registered protocol family 16
[   20.746121] ACPI: bus type pci registered
[   20.746984] PCI: PCI BIOS revision 2.10 entry at 0xf0ed0, last bus=2
[   20.746988] Setting up standard PCI resources
[   20.756742] ACPI: Subsystem revision 20060127
[   20.760040] ACPI: Interpreter enabled
[   20.760044] ACPI: Using PIC for interrupt routing
[   20.760793] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   20.761076] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   20.761359] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.761653] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   20.761925] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.761931] PCI: Probing PCI hardware (bus 00)
[   20.762204] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   20.767293] Boot video device is 0000:01:00.0
[   20.768621] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.776727] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   20.781856] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.781880] pnp: PnP ACPI init
[   20.786312] pnp: PnP ACPI: found 13 devices
[   20.786364] PCI: Using ACPI for IRQ routing
[   20.786368] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.804818] pnp: 00:03: ioport range 0xe400-0xe47f could not be reserved
[   20.804824] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   20.804828] pnp: 00:03: ioport range 0x290-0x291 has been reserved
[   20.804831] pnp: 00:03: ioport range 0x370-0x373 has been reserved
[   20.804875] PCI: Bridge: 0000:00:01.0
[   20.804882]   IO window: d000-dfff
[   20.804899]   MEM window: be000000-beffffff
[   20.804911]   PREFETCH window: c0000000-efffffff
[   20.804926] PCI: Bridge: 0000:00:0e.0
[   20.804928]   IO window: disabled.
[   20.804944]   MEM window: bc000000-bd7fffff
[   20.804956]   PREFETCH window: bf000000-bfffffff
[   20.805017] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.805058] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   20.805103] NET: Registered protocol family 2
[   20.813639] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.813782] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   20.814043] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   20.814193] TCP: Hash tables configured (established 16384 bind 8192)
[   20.814197] TCP reno registered
[   20.814444] Simple Boot Flag at 0x3a set to 0x1
[   20.815006] audit: initializing netlink socket (disabled)
[   20.815020] audit(1154299622.854:1): initialized
[   20.815274] Initializing Cryptographic API
[   20.815281] io scheduler noop registered
[   20.815289] io scheduler anticipatory registered (default)
[   20.815295] io scheduler deadline registered
[   20.815310] io scheduler cfq registered
[   20.844061] Real Time Clock Driver v1.12ac
[   20.844168] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.844305] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.844503] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.845195] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.845598] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.846524] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.846661] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.846666] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.846820] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   20.846825] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   20.849149] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.849366] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.849555] mice: PS/2 mouse device common for all mice
[   20.849666] TCP bic registered
[   20.849675] NET: Registered protocol family 1
[   20.849683] NET: Registered protocol family 8
[   20.849685] NET: Registered protocol family 20
[   20.849716] Using IPI No-Shortcut mode
[   20.850218] ACPI wakeup devices:
[   20.850221] PCI0 PCI1 UAR1 UAR2 USB0 USB1 USB2
[   20.850228] ACPI: (supports S0 S1 S4 S5)
[   20.850451] Time: tsc clocksource has been installed.
[   20.850708] Freeing unused kernel memory: 228k freed
[   21.126440] input: AT Translated Set 2 keyboard as /class/input/input0
[   21.605308] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   21.605810] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   21.605815] PCI: setting IRQ 11 as level-triggered
[   21.605820] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   21.605831] PCI: VIA IRQ fixup for 0000:00:11.1, from 0 to 11
[   21.605867] VP_IDE: chipset revision 6
[   21.605870] VP_IDE: not 100% native mode: will probe irqs later
[   21.605897] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
[   21.605912]     ide0: BM-DMA at 0xa000-0xa007, BIOS settings: hda:DMA, hdb:DMA
[   21.605944]     ide1: BM-DMA at 0xa008-0xa00f, BIOS settings: hdc:DMA, hdd:DMA
[   21.605963] Probing IDE interface ide0...
[   21.997649] hda: MAXTOR 6L080J4, ATA DISK drive
[   22.257213] hdb: IC35L120AVVA07-0, ATA DISK drive
[   22.309778] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   22.310145] Probing IDE interface ide1...
[   23.117786] hdc: LG DVD-ROM DRD-8160B, ATAPI CD/DVD-ROM drive
[   23.844581] hdd: HL-DT-ST DVDRAM GSA-4040B, ATAPI CD/DVD-ROM drive
[   23.899115] ide1 at 0x170-0x177,0x376 on irq 15
[   23.919900] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   23.919915] Uniform CD-ROM driver Revision: 3.20
[   23.924566] hda: max request size: 128KiB
[   23.931848] hdd: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   23.932049] hda: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
[   23.932213] hda: cache flushes supported
[   23.932262]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 > hda3 hda4
[   23.998699] hdb: max request size: 128KiB
[   24.004738] hdb: 241254720 sectors (123522 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
[   24.004972] hdb: cache flushes supported
[   24.005014]  hdb: hdb1
[   24.571561] ieee1394: Initialized config rom entry `ip1394'
[   24.574315] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   24.574323] PCI: setting IRQ 10 as level-triggered
[   24.574328] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   24.574344] PCI: Setting latency timer of device 0000:02:0c.0 to 64
[   24.637150] usbcore: registered new driver usbfs
[   24.637801] usbcore: registered new driver hub
[   24.640120] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   24.666357] USB Universal Host Controller Interface driver v3.0
[   24.678966] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[bc800000-bc8007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.683150] PCI: Enabling device 0000:00:10.0 (0014 -> 0016)
[   24.683598] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   24.683603] PCI: setting IRQ 9 as level-triggered
[   24.683608] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   24.683633] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   24.683640] ohci_hcd 0000:00:10.0: OHCI Host Controller
[   24.684274] ohci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   24.684298] ohci_hcd 0000:00:10.0: irq 9, io mem 0xbb800000
[   24.765236] usb usb1: configuration #1 chosen from 1 choice
[   24.765381] hub 1-0:1.0: USB hub found
[   24.765399] hub 1-0:1.0: 3 ports detected
[   24.866999] PCI: Enabling device 0000:00:10.1 (0014 -> 0016)
[   24.867014] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   24.867043] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   24.867051] ohci_hcd 0000:00:10.1: OHCI Host Controller
[   24.867186] ohci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   24.867208] ohci_hcd 0000:00:10.1: irq 11, io mem 0xbb000000
[   24.948844] usb usb2: configuration #1 chosen from 1 choice
[   24.948994] hub 2-0:1.0: USB hub found
[   24.949008] hub 2-0:1.0: 2 ports detected
[   25.050961] PCI: Enabling device 0000:00:10.2 (0014 -> 0016)
[   25.050975] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   25.050997] PCI: Setting latency timer of device 0000:00:10.2 to 64
[   25.051004] ehci_hcd 0000:00:10.2: EHCI Host Controller
[   25.051160] ehci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   25.072469] ehci_hcd 0000:00:10.2: irq 10, io mem 0xba800000
[   25.072481] ehci_hcd 0000:00:10.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.072724] usb usb3: configuration #1 chosen from 1 choice
[   25.072863] hub 3-0:1.0: USB hub found
[   25.072880] hub 3-0:1.0: 5 ports detected
[   25.174627] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   25.174652] PCI: Setting latency timer of device 0000:00:11.2 to 64
[   25.174660] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   25.174802] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 4
[   25.174835] uhci_hcd 0000:00:11.2: irq 9, io base 0x00009800
[   25.175054] usb usb4: configuration #1 chosen from 1 choice
[   25.175193] hub 4-0:1.0: USB hub found
[   25.175208] hub 4-0:1.0: 2 ports detected
[   25.276437] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   25.276464] PCI: Setting latency timer of device 0000:00:11.3 to 64
[   25.276471] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   25.276611] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 5
[   25.276647] uhci_hcd 0000:00:11.3: irq 9, io base 0x00009400
[   25.276859] usb usb5: configuration #1 chosen from 1 choice
[   25.276991] hub 5-0:1.0: USB hub found
[   25.277005] hub 5-0:1.0: 2 ports detected
[   25.378125] ACPI: PCI Interrupt 0000:00:11.4[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   25.378144] PCI: Setting latency timer of device 0000:00:11.4 to 64
[   25.378151] uhci_hcd 0000:00:11.4: UHCI Host Controller
[   25.378287] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 6
[   25.378315] uhci_hcd 0000:00:11.4: irq 9, io base 0x00009000
[   25.378519] usb usb6: configuration #1 chosen from 1 choice
[   25.378653] hub 6-0:1.0: USB hub found
[   25.378666] hub 6-0:1.0: 2 ports detected
[   25.587625] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   25.666953] Attempting manual resume
[   25.694376] ReiserFS: hda7: found reiserfs format "3.6" with standard journal
[   25.757353] usb 4-2: configuration #1 chosen from 1 choice
[   25.841185] ReiserFS: hda7: using ordered data mode
[   25.847386] ReiserFS: hda7: journal params: device hda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   25.849667] ReiserFS: hda7: checking transaction log (hda7)
[   25.883066] ReiserFS: hda7: Using r5 hash to sort names
[   25.939273] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00308d0a01d4c052]
[   26.074796] usb 5-2: new full speed USB device using uhci_hcd and address 2
[   26.521728] usb 5-2: configuration #1 chosen from 1 choice
[   26.731751] usbcore: registered new driver hiddev
[   26.741360] input: Logitech USB Gaming Mouse as /class/input/input1
[   26.741391] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:11.2-2
[   26.750289] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:11.2-2
[   26.750304] usbcore: registered new driver usbhid
[   26.750308] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   32.763484] Linux agpgart interface v0.101 (c) Dave Jones
[   32.813631] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   32.825705] agpgart: AGP aperture is 128M @ 0xf0000000
[   32.955617] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   32.955672] 8139cp: pci dev 0000:00:0d.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   32.955717] 8139cp: Try the "8139too" driver instead.
[   32.982803] 8139too Fast Ethernet driver 0.9.27
[   32.982894] PCI: Enabling device 0000:00:0d.0 (0004 -> 0007)
[   32.982908] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   32.982931] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   32.983264] eth0: RealTek RTL8139 at 0xe0a68000, 00:10:a7:0d:b6:cf, IRQ 11
[   32.983267] eth0:  Identified 8139 chip type 'RTL-8139C'
[   33.179781] parport: PnPBIOS parport detected.
[   33.179875] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   33.435946] PCI: Enabling device 0000:00:0f.0 (0004 -> 0005)
[   33.436436] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   33.436441] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   33.436457] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   33.484990] Bluetooth: Core ver 2.8
[   33.484998] NET: Registered protocol family 31
[   33.485000] Bluetooth: HCI device and connection manager initialized
[   33.485022] Bluetooth: HCI socket layer initialized
[   33.491910] Bluetooth: HCI USB driver ver 2.9
[   33.492037] usbcore: registered new driver hci_usb
[   33.678349] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   33.909919] SCSI subsystem initialized
[   34.021529] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   34.021536] ieee1394: sbp2: Try serialize_io=0 for better performance
[   34.312877] fuse init (API version 7.6)
[   34.388374] Adding 506036k swap on /dev/hda3.  Priority:-1 extents:1 across:506036k
[   34.816899] NET: Registered protocol family 17
[   36.793782] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   36.793789] md: bitmap version 4.39
[   37.200134] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[   38.484362] device-mapper: dm-linear: Device lookup failed
[   38.484419] device-mapper: error adding target to table
[   38.486881] device-mapper: dm-linear: Device lookup failed
[   38.486933] device-mapper: error adding target to table
[   38.489431] device-mapper: dm-linear: Device lookup failed
[   38.489482] device-mapper: error adding target to table
[   38.491921] device-mapper: dm-linear: Device lookup failed
[   38.491973] device-mapper: error adding target to table
[   38.494448] device-mapper: dm-linear: Device lookup failed
[   38.494499] device-mapper: error adding target to table
[   38.496959] device-mapper: dm-linear: Device lookup failed
[   38.497011] device-mapper: error adding target to table
[   38.499490] device-mapper: dm-linear: Device lookup failed
[   38.499542] device-mapper: error adding target to table
[   38.503608] device-mapper: dm-linear: Device lookup failed
[   38.503660] device-mapper: error adding target to table
[   38.506275] device-mapper: dm-linear: Device lookup failed
[   38.506327] device-mapper: error adding target to table
[   38.508897] device-mapper: dm-linear: Device lookup failed
[   38.508949] device-mapper: error adding target to table
[   38.511584] device-mapper: dm-linear: Device lookup failed
[   38.511637] device-mapper: error adding target to table
[   38.514250] device-mapper: dm-linear: Device lookup failed
[   38.514302] device-mapper: error adding target to table
[   38.516945] device-mapper: dm-linear: Device lookup failed
[   38.516997] device-mapper: error adding target to table
[   38.519618] device-mapper: dm-linear: Device lookup failed
[   38.519670] device-mapper: error adding target to table
[   38.522325] device-mapper: dm-linear: Device lookup failed
[   38.522377] device-mapper: error adding target to table
[   38.524832] device-mapper: dm-linear: Device lookup failed
[   38.524884] device-mapper: error adding target to table
[   38.527383] device-mapper: dm-linear: Device lookup failed
[   38.527434] device-mapper: error adding target to table
[   38.529886] device-mapper: dm-linear: Device lookup failed
[   38.529938] device-mapper: error adding target to table
[   38.532429] device-mapper: dm-linear: Device lookup failed
[   38.532481] device-mapper: error adding target to table
[   38.534949] device-mapper: dm-linear: Device lookup failed
[   38.535001] device-mapper: error adding target to table
[   38.537479] device-mapper: dm-linear: Device lookup failed
[   38.537531] device-mapper: error adding target to table
[   38.540030] device-mapper: dm-linear: Device lookup failed
[   38.540082] device-mapper: error adding target to table
[   38.542704] device-mapper: dm-linear: Device lookup failed
[   38.542756] device-mapper: error adding target to table
[   38.545362] device-mapper: dm-linear: Device lookup failed
[   38.545414] device-mapper: error adding target to table
[   38.548002] device-mapper: dm-linear: Device lookup failed
[   38.548054] device-mapper: error adding target to table
[   38.550661] device-mapper: dm-linear: Device lookup failed
[   38.550714] device-mapper: error adding target to table
[   38.553315] device-mapper: dm-linear: Device lookup failed
[   38.553366] device-mapper: error adding target to table
[   38.555947] device-mapper: dm-linear: Device lookup failed
[   38.555999] device-mapper: error adding target to table
[   93.927762] NTFS driver 2.1.27 [Flags: R/W MODULE].
[   93.999740] NTFS volume version 3.1.
[   94.088717] ReiserFS: hda4: found reiserfs format "3.6" with standard journal
[   94.917350] ReiserFS: hda4: using ordered data mode
[   94.917767] ReiserFS: hda4: journal params: device hda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   94.919863] ReiserFS: hda4: checking transaction log (hda4)
[   94.957063] ReiserFS: hda4: Using r5 hash to sort names
[   94.986903] attempt to access beyond end of device
[   94.986911] hda5: rw=0, want=6291457, limit=32067
[   94.986916] NTFS-fs error (device hda5): ntfs_read_inode_mount(): Device read failed.
[   94.986972] NTFS-fs error (device hda5): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[   94.987025] NTFS-fs error (device hda5): ntfs_fill_super(): Failed to load essential metadata.
[   94.999198] ReiserFS: hda6: found reiserfs format "3.6" with standard journal
[   96.822515] ReiserFS: hda6: using ordered data mode
[   96.822953] ReiserFS: hda6: journal params: device hda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   96.824996] ReiserFS: hda6: checking transaction log (hda6)
[   96.854740] ReiserFS: hda6: Using r5 hash to sort names
[   96.967572] kjournald starting.  Commit interval 5 seconds
[   96.968491] EXT3 FS on hda8, internal journal
[   96.968499] EXT3-fs: mounted filesystem with ordered data mode.
[   98.297857] ip_tables: (C) 2000-2006 Netfilter Core Team
[   98.343170] Netfilter messages via NETLINK v0.30.
[   98.360635] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 236 bytes per conntrack
[   99.371102] Using specific hotkey driver
[   99.405561] ACPI: Power Button (FF) [PWRF]
[   99.405582] ACPI: Power Button (CM) [PWRB]
[   99.856586] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   99.856594] apm: overridden by ACPI.
[  102.716814] hci_cmd_task: hci0 command tx timeout
[  102.749905] Bluetooth: L2CAP ver 2.8
[  102.749912] Bluetooth: L2CAP socket layer initialized
[  102.782342] Bluetooth: RFCOMM socket layer initialized
[  102.782365] Bluetooth: RFCOMM TTY layer initialized
[  102.782368] Bluetooth: RFCOMM ver 1.7
[  105.210852] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  105.215820] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[  105.216706] [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[  105.465697] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  107.905230] [fglrx] Internal AGP support requested, but kernel AGP support active.
[  107.905243] [fglrx] Have to use kernel AGP support to avoid conflicts.
[  107.905249] [fglrx] AGP detected, AgpState   = 0x1f000207 (hardware caps of chipset)
[  107.907705] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  107.907748] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  107.907976] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  107.908056] [fglrx] AGP enabled,  AgpCommand = 0x1f000304 (selected caps)
[  107.922723] [fglrx] total      GART = 134217728
[  107.922735] [fglrx] free       GART = 118222848
[  107.922738] [fglrx] max single GART = 118222848
[  107.922741] [fglrx] total      LFB  = 119533568
[  107.922744] [fglrx] free       LFB  = 94367744
[  107.922746] [fglrx] max single LFB  = 94367744
[  107.922749] [fglrx] total      Inv  = 0
[  107.922751] [fglrx] free       Inv  = 0
[  107.922753] [fglrx] max single Inv  = 0
[  107.922755] [fglrx] total      TIM  = 0
```

---

### Post by LordRaiden on 2006-07-30
I keep getting this error... I don't know why.

I have a few CFLAGS ("-march=athlon-xp -pipe -O2") but they should be harmless.

```
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x5f8): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x8d8): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0xa71): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xd03): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x439b): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x51d1): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [debian/stamp-build-kernel] Error 2
```

---

### Post by hfdragon on 2006-07-30
> **hype said:**
>  If someone sees a guide to properly compile kernel 2.6.17 and have it work properly with a ATI card, let me know... ;)

I did it ;-)

Compiled kernel 2.6.17.6 and installed the ATI drivers using the infos in this thread :

[http://ubuntuforums.org/showthread.php?t=209894]("http://ubuntuforums.org/showthread.php?t=209894")

It worked fine with drivers 8.26.18-1 and my card is a M300 (dell inspiron 6000 laptop).

I still have to find out if it's working with kernel 2.6.17.7 and the new drivers 8.27.10

The only problem remainging with the dislpay is when booting : I have a black screen, but everything is loading properly. I just neet to wait with a black screen until I get the login screen.

Besides this, anyone managed to compile this kernel with iptables support ?

---

### Post by PingunZ on 2006-07-30
just copy paste this in console
```
# -- What you should do in console --

sudo -s -H
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget 
cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.7.tar.bz2  
tar -xvjf linux-2.6.17.7.tar.bz2 
rm -rf linux 
ln -s /usr/src/linux-2.6.17.7 linux  
cd /usr/src/linux
cp /boot/config-`uname -r` .config 
make xconfig
make-kpkg clean
make-kpkg -initrd --revision=686 kernel_image kernel_headers modules_image
cd ..
dpkg -i kernel-headers-2.6.17.7_686_i386.deb
dpkg -i kernel-image-2.6.17.7_686_i386.deb

```

for some tips of performance look at [this]("http://ubuntuforums.org/showpost.php?p=1174954&postcount=507")

---

### Post by mlind on 2006-07-30
> **hfdragon said:**
> 
Besides this, anyone managed to compile this kernel with iptables support ?

Yes. If you're making oldconfig, make sure you have at least
CONFIG_NETFILTER_XTABLES=m and CONFIG_IP_NF_IPTABLES=m. 

I marked all options to build as modules from "Core Netfilter Configuration" and "IP: Netfilter Configuration".

---

### Post by LordRaiden on 2006-07-31
> **LordRaiden said:**
> I keep getting this error... I don't know why.

I have a few CFLAGS ("-march=athlon-xp -pipe -O2") but they should be harmless.

```
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x5f8): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x8d8): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0xa71): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xd03): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x439b): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x51d1): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [debian/stamp-build-kernel] Error 2
```

I managed to fix this from this link [http://www.uwsg.iu.edu/hypermail/linux/kernel/0607.1/2123.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0607.1/2123.html)

The part to use as a patch is

```
 diff --git a/Makefile b/Makefile
index 7c010f3..b4a2a80 100644
--- a/Makefile
+++ b/Makefile
@@ -308,7 +308,7 @@ LINUXINCLUDE    := -Iinclude \
 CPPFLAGS        := -D__KERNEL__ $(LINUXINCLUDE)
 
 CFLAGS          := -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
-                   -fno-strict-aliasing -fno-common
+                   -fno-strict-aliasing -fno-common -fno-stack-protector
 # Force gcc to behave correct even for buggy distributions
 CFLAGS          += $(call cc-option, -fno-stack-protector-all \
                                      -fno-stack-protector)
``` I manually replaced edited the Makefile in the top-level directory (/usr/src/linux) since I could not get it working using patch.

[B]Please not that this patch is needed only by Ubuntu Edgy users.

UPDATE[/B] - I used this patch and I successfully compiled 2.6.17.7 - great instructions!

---

### Post by shiver on 2006-07-31
I found a fix for my second hard drive not mounting:

[http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10)

Apparently it concerns any system with more than one HDD. :\ Perhaps the evms-patch should be added to the howto?

---

### Post by archer75 on 2006-07-31
my problem is that I don't have a usr/src/linux directory! What's the deal?

---

### Post by xXx 0wn3d xXx on 2006-07-31
> **archer75 said:**
> my problem is that I don't have a usr/src/linux directory! What's the deal?

It's not a directoy...it's a symlink. Sometimes it's called a "short-cut." The /usr/src/linux file links to the kernel you are building.

---

### Post by Metacarpal on 2006-08-02
Went through the howto, and it boots up fine but I lost my wireless card (was working out of the box with the Dapper kernel).  I probably just unchecked something I shouldn't have. :???: 

The card has the Realtek RTL8185L chipset.  I've downloaded the driver (R818x) source from the Realtek website, so I have that handy.

Is this driver already in 2.6.17?  If so, what's it under, so I can make sure to check it when I try compiling again?  If not, how do I go about adding it?

Also, how does one go about adding the bootsplash patch (I have the .deb for that) to the kernel?

Thanks in advance for your help!

---

### Post by John.Michael.Kane on 2006-08-02
What does this kernel offer over the one already in ubuntu?

---

### Post by linuxnewbie946 on 2006-08-02
> **SD-Plissken said:**
> What does this kernel offer over the one already in ubuntu?

It just speeds Ubuntu up a little.

---

### Post by kremso on 2006-08-02
After recompiling the kernel, because I compiled ext3 as a module, than recompiling because I compiled ext2 as a module and recompiling once again because I compiled IDE driver as a module I managed to get "only" theese two errors:

```

mounting udev on /dev failed : invalid argument
mknod /dev/console : File exists
0 //this is zero

```

..and booting stops
In recovery mode, booting stops at Waiting for root filesystem..

Is there anything else, what must be compiled staticaly to get the kernel boot? Or am i missing something else?

**2linuxnewbie** : I think you should really update this howto and tell people to compile IDE, ext2, ane ext3 staticaly.

---

### Post by saracen on 2006-08-02
I compiled the kernel from source following this howto and got most things to work fine.  I have a couple of issues though.  One is that I am using ntfs-3g and fuse to mount my NTFS drives.  For some reason only one of the drives gets mounted.  For the rest it says

```
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Couldn't mount device '/dev/hdb1': Device or resource busy
Mount failed.
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Couldn't mount device '/dev/sdb1': Device or resource busy
Mount failed.
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Couldn't mount device '/dev/sda1': Device or resource busy
Mount failed.
```

With the stock Ubuntu kernel all the drives are mounted fine.  The other thing I noticed is that any of the apps that I run with gksudo - like the udpate manager - they don't take on my gtk theme for some reason.  They use the default GNOME one.

Any ideas on this stuff?

---

### Post by mlind on 2006-08-02
> **saracen said:**
> I compiled the kernel from source following this howto and got most things to work fine.  I have a couple of issues though.  One is that I am using ntfs-3g and fuse to mount my NTFS drives.  For some reason only one of the drives gets mounted.  For the rest it says

```
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Couldn't mount device '/dev/hdb1': Device or resource busy
Mount failed.
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Couldn't mount device '/dev/sdb1': Device or resource busy
Mount failed.
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Couldn't mount device '/dev/sda1': Device or resource busy
Mount failed.
```

With the stock Ubuntu kernel all the drives are mounted fine.  The other thing I noticed is that any of the apps that I run with gksudo - like the udpate manager - they don't take on my gtk theme for some reason.  They use the default GNOME one.

Any ideas on this stuff?

This could be releated to evms claiming your partitions and blocking kernel from doing mount operations. see [http://evms.sourceforge.net/install/kernel.html#bdclaim](http://evms.sourceforge.net/install/kernel.html#bdclaim)
Ubuntu kernels seem to used bd-claim.patch.

does **dmesg** output contain errors about device lookup or mouting?

---

### Post by saracen on 2006-08-02
> **mlind said:**
> 
does **dmesg** output contain errors about device lookup or mouting?

Here's the output of dmesg looking for device-mapper:

```
saracen@veritas:~$ dmesg | grep device-mapper
[4294701.515000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[4294702.106000] device-mapper: dm-linear: Device lookup failed
[4294702.106000] device-mapper: error adding target to table
[4294702.107000] device-mapper: dm-linear: Device lookup failed
[4294702.107000] device-mapper: error adding target to table
[4294702.108000] device-mapper: dm-linear: Device lookup failed
[4294702.109000] device-mapper: error adding target to table
[4294702.110000] device-mapper: dm-linear: Device lookup failed
[4294702.110000] device-mapper: error adding target to table
[4294702.113000] device-mapper: dm-linear: Device lookup failed
[4294702.113000] device-mapper: error adding target to table
[4294702.114000] device-mapper: dm-linear: Device lookup failed
[4294702.114000] device-mapper: error adding target to table
[4294702.115000] device-mapper: dm-linear: Device lookup failed
[4294702.115000] device-mapper: error adding target to table
[4294702.116000] device-mapper: dm-linear: Device lookup failed
[4294702.116000] device-mapper: error adding target to table
[4294702.118000] device-mapper: dm-linear: Device lookup failed
[4294702.118000] device-mapper: error adding target to table
[4294702.119000] device-mapper: dm-linear: Device lookup failed
[4294702.119000] device-mapper: error adding target to table
[4294702.120000] device-mapper: dm-linear: Device lookup failed
[4294702.120000] device-mapper: error adding target to table
[4294702.121000] device-mapper: dm-linear: Device lookup failed
[4294702.121000] device-mapper: error adding target to table
[4294702.122000] device-mapper: dm-linear: Device lookup failed
[4294702.123000] device-mapper: error adding target to table
[4294702.124000] device-mapper: dm-linear: Device lookup failed
[4294702.124000] device-mapper: error adding target to table
[4294702.125000] device-mapper: dm-linear: Device lookup failed
[4294702.125000] device-mapper: error adding target to table
[4294702.126000] device-mapper: dm-linear: Device lookup failed
[4294702.126000] device-mapper: error adding target to table

```

If i look for mount it just says:

```
saracen@veritas:~$ dmesg | grep mount
[4294692.509000] EXT3-fs: mounted filesystem with ordered data mode.
[4294702.277000] EXT3-fs: mounted filesystem with ordered data mode.
```

So do u think it is the patch?  Is there a comprehensive list of patches that Ubuntu makes to the stock kernel for Dapper?

---

### Post by mlind on 2006-08-02
> **saracen said:**
> Here's the output of dmesg looking for device-mapper:

```
saracen@veritas:~$ dmesg | grep device-mapper
[4294701.515000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[4294702.106000] device-mapper: dm-linear: Device lookup failed
.
.

```

If i look for mount it just says:

```
saracen@veritas:~$ dmesg | grep mount
[4294692.509000] EXT3-fs: mounted filesystem with ordered data mode.
[4294702.277000] EXT3-fs: mounted filesystem with ordered data mode.
```

So do u think it is the patch?  Is there a comprehensive list of patches that Ubuntu makes to the stock kernel for Dapper?

Yes, bd-claim.patch will fix that. This is [known issue]("http://evms.sourceforge.net/faq.html") and you have [three solutions]("http://evms.sourceforge.net/install/kernel.html#bdclaim") to fix it. I applied the bd-claim.patch and rebuilt my kernel.

---

### Post by saracen on 2006-08-02
> **mlind said:**
> Yes, bd-claim.patch will fix that. This is [known issue]("http://evms.sourceforge.net/faq.html") and you have [three solutions]("http://evms.sourceforge.net/install/kernel.html#bdclaim") to fix it. I applied the bd-claim.patch and rebuilt my kernel.

Cool, thanks.  Do u know of any other patches that I may need to apply?  Or if there is a pre-patched version of the latest kernel out there for Ubuntu?

---

### Post by saracen on 2006-08-02
how do i compile usplash into the kernel?

---

### Post by glennric on 2006-08-02
There are several patches you can try.  They have to be applied to the vanilla kernel source, i.e., [HTML]http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.tar.bz2[/HTML]

Some patches to try are the Con Kolivas patch:
[HTML]http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.17/2.6.17-ck1/patch-2.6.17-ck1.bz2[/HTML]
or one of the beyond patches:
[HTML]http://iphitus.loudas.com/archck.php[/HTML]

By the way linuxnewbie946, in your "Note: Non-Legacy drivers!!" section, the first code section should be
```
sudo /etc/init.d/gdm stop
``` not /etc/init.d/gdu.  A little typo I suspect!!

---

### Post by mlind on 2006-08-02
> **saracen said:**
> Cool, thanks.  Do u know of any other patches that I may need to apply?  Or if there is a pre-patched version of the latest kernel out there for Ubuntu?

You can download Edgy's kernel sources and compile those if you want Ubuntu pre-patched kernel.

I use -ck patchset, but you don't need to apply that. If you use iptables and  used *make oldconfig* target, you should know that iptables is not enabled because of the naming changes in kernel config..

---

### Post by metathran on 2006-08-03
I get this error when compiling
```

make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Erreur 1
make[4]: *** [drivers/media/dvb/ttpci] Erreur 2
make[3]: *** [drivers/media/dvb] Erreur 2
make[2]: *** [drivers/media] Erreur 2
make[1]: *** [drivers] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-2.6.17.7 »
make: *** [stamp-build] Erreur 2

```

And compiling stop...

Any idea ? Where can we find a compiled deb of this kernel ? I find this place [http://people.ubuntu.com/~bcollins/kernels-daily/2006-07-12/i386/](http://people.ubuntu.com/~bcollins/kernels-daily/2006-07-12/i386/) but modules-init-tools dependency is not satisfiable

---

### Post by mrweirdo on 2006-08-03
I'm having the same problem as well in english though ;)

for some reason it doesnt seem to work :(

---

### Post by metathran on 2006-08-03
In fact it has been previously answered :roll:  :-\" :mrgreen: [http://ubuntuforums.org/showpost.php?p=1308736&postcount=106](http://ubuntuforums.org/showpost.php?p=1308736&postcount=106)

---

### Post by canucks on 2006-08-03
new xubuntu user here and i must say i'm impressed :)

anyways onto my problem, when i recompiled my kernel and booted into the new kernel, xfce4.4 no longer automount my dvd anymore, did i miss an option in the kernel? if so which one?

instead of using "make xconfig" what other libs do i need to get the old "make menuconfig" (ncurses?)

other than that, things are pretty smooth :)

thanks guys

---

### Post by hfdragon on 2006-08-03
> **SD-Plissken said:**
> What does this kernel offer over the one already in ubuntu?

A lot more than only speeding up a litle bit ;-)

- I had problems with my UMTS (3G) modem :now it's working because ppp support has been corrected since kernel 2.6.16

- I had problems to sync my Palm : now sync is back and running perfectly :-)

- I've heard that suspend & hibernate are now working for laptops, but i've not tested that yet.

- I've also heard that there are a lot of improvements for wifi support.



> **Metacarpal said:**
> Went through the howto, and it boots up fine but I lost my wireless card (was working out of the box with the Dapper kernel).  I probably just unchecked something I shouldn't have. :???: 

The card has the Realtek RTL8185L chipset.  I've downloaded the driver (R818x) source from the Realtek website, so I have that handy.

Is this driver already in 2.6.17?  If so, what's it under, so I can make sure to check it when I try compiling again?  If not, how do I go about adding it?

Also, how does one go about adding the bootsplash patch (I have the .deb for that) to the kernel?

Thanks in advance for your help!

I had this problem too.... and found the answer somewhere in these forums :  you must have the firmware of you card in /lib/firmware/(number of your kernel).

I resolved this issue on my computer by doing :

```
sudo cp -R /lib/fimware/2.6.15-25-686 /lib/firmware/2.6.17.7
```

After a reboot, it's working !! :-)

For the bootsplash screen, I also found the answer somewhere in these forums. You need to select some options when configuring the kernel before compilation no need to use any patch !!

I'll try to find again that and post here..

---

### Post by metathran on 2006-08-04
> **hfdragon said:**
> 

For the bootsplash screen, I also found the answer somewhere in these forums. You need to select some options when configuring the kernel before compilation no need to use any patch !!

I'll try to find again that and post here..

I'm also interested if you can find how we can get a bootscreen back. There is just a little bug when i shutdown the computer, i can see somme ugly lines with horrible color during 2-3 seconds, but this is not a serious issue

However this kernel is very fast, i can easily feel the performance, and the IQ improvement with compiz/XGL ;)

---

### Post by hfdragon on 2006-08-04
> **metathran said:**
> I'm also interested if you can find how we can get a bootscreen back. There is just a little bug when i shutdown the computer, i can see somme ugly lines with horrible color during 2-3 seconds, but this is not a serious issue

Ok, I found it here :

[http://ubuntuforums.org/showpost.php?p=1296169&postcount=2]("http://ubuntuforums.org/showpost.php?p=1296169&postcount=2")

Here is what you need to do in the config :

```

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)
```

Worked perfectly here on my laptop :-)

---

### Post by metathran on 2006-08-04
> **hfdragon said:**
> Ok, I found it here :

[http://ubuntuforums.org/showpost.php?p=1296169&postcount=2]("http://ubuntuforums.org/showpost.php?p=1296169&postcount=2")

Here is what you need to do in the config :

```

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)
```

Worked perfectly here on my laptop :-)


Do you have an ATI card ? I thought vesa is for ati.

The fact is taht i followed this part of the howto
> In Graphics Support
-DISABLE NVIDIA RIVA IF YOU ARE USING 3RD PARTY NVIDIA DRIVERS. This has been known to cause problems

I though that my usplash disappear because of this setting. Can somebody confirm that ?

---

### Post by hfdragon on 2006-08-04
> **metathran said:**
> Do you have an ATI card ? I thought vesa is for ati.

The fact is taht i followed this part of the howto

I though that my usplash disappear because of this setting. Can somebody confirm that ?

I have an ATI card, working perfectly after installing the latest drivers from ATI.

I don't know why it is working... but it is working with tihese settings for me ;)

---

### Post by bastupungen on 2006-08-04
Hello!
I just compiled the kernel from kernel.org with this guide and the other similar guide that uses fakeroot. After several PPC related compile issues (it was so many i highly doubt i would call this an "stable" release :( ) i finally got it to compile correctly and i got the two .deb files. I install them and edit my yaboot.conf and do an "sudo ybin -v". Everything seems fine and i reboot and chose my "new" configuration. 

the kernel loads but the loading stops at "Mounting root file system" and "Waiting for root file system". Whats up with that?

I've read on several sites that there should be an shell that appears after a while. It does (and it does not) but i could not write anything there. Anyone who knows whats wrong?

I get the same result from both the root and fakeroot version of the guide

I have an ibook G4 1.2 Ghz

thanks in advance / Jonatan

---

### Post by Metacarpal on 2006-08-04
> **hfdragon said:**
> A lot more than only speeding up a litle bit ;-)

- I had problems with my UMTS (3G) modem :now it's working because ppp support has been corrected since kernel 2.6.16

- I had problems to sync my Palm : now sync is back and running perfectly :-)

- I've heard that suspend & hibernate are now working for laptops, but i've not tested that yet.

- I've also heard that there are a lot of improvements for wifi support.





I had this problem too.... and found the answer somewhere in these forums :  you must have the firmware of you card in /lib/firmware/(number of your kernel).

I resolved this issue on my computer by doing :

```
sudo cp -R /lib/fimware/2.6.15-25-686 /lib/firmware/2.6.17.7
```

After a reboot, it's working !! :-)

For the bootsplash screen, I also found the answer somewhere in these forums. You need to select some options when configuring the kernel before compilation no need to use any patch !!

I'll try to find again that and post here..

Sweeeeeeeeet - Thanks so much!  Can't wait 'til I get a few hours without the girlfriend home so I can try this out.  (Last time I compiled the kernel, she got a little moody 'cause I wasn't, er, compiling with her instead.)

---

### Post by Ryan H on 2006-08-04
I got this error while compiling:
> . . .
  CC [M]  drivers/media/dvb/ttpci/ttpci-eeprom.o
  CC [M]  drivers/media/dvb/ttpci/budget-av.o
drivers/media/dvb/ttpci/budget-av.c: In function &#8216;frontend_init&#8217;:
drivers/media/dvb/ttpci/budget-av.c:1063: error: &#8216;struct budget_av&#8217; has no member named &#8216;reinitialise_demod&#8217;
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member &#8216;tuner_ops&#8217; in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: &#8216;philips_cu1216_tuner_set_params&#8217; undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in.)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

I don't know how to fix it?

-Ryan H

---

### Post by Metacarpal on 2006-08-04
> **Ryan H said:**
> I got this error while compiling:

I don't know how to fix it?

-Ryan H

This is mentioned in the first post on this thread.

Check out [this post]("http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106") for what to do to prevent that error.

---

### Post by rasec on 2006-08-04
linuxnewbie946, can you make a note for the powerpc users that they need to use the pmac32_defconfig in arch/powerpc/configs as their base config because the stock ubuntu config doesn't work on the 2.6.17.x kernels for thir macs. This seems to be a recurring topic in the mac forums ever week or so. Thanks!

---

### Post by bastupungen on 2006-08-04
> **rasec said:**
> linuxnewbie946, can you make a note for the powerpc users that they need to use the pmac32_defconfig in arch/powerpc/configs as their base config because the stock ubuntu config doesn't work on the 2.6.17.x kernels for thir macs. This seems to be a recurring topic in the mac forums ever week or so. Thanks!

I did what you said and now the kernel boots and loads in to X/KDE nicely. Though what i noticed after i loaded the kernel was that for some reason the bcm43xx module was not loaded and when i check make xconfig for the kernel compiled i cannot find the bcm43xx option.(well i find it if i choose to "show all" but i cannot check it) And this was one of the reasons to try compiling kernels (and also too learn)

Why is this? do i have to install the bcm43xx from scratch? Why??? did the bcm43xx option just disappear like that?

/jonatan

---

### Post by Ryan H on 2006-08-04
> **Metacarpal said:**
> This is mentioned in the first post on this thread.

Check out [this post]("http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106") for what to do to prevent that error.

I can't find where > Budget cards with Budget Patch is on the list, it's not under Device Drivers -> Multimedia Devices -> Digital Broadcasting Devices -> so I'm still getting > make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1 A screen shot is attatched to this post

-Ryan H

---

### Post by Metacarpal on 2006-08-05
See those 4 or 5 entries with the word "budget" in them?  Those are the culprits.

---

### Post by gcsoares on 2006-08-05
i compiled my kernel following other tutorial and is runnig cool for some days, but i still have somethink to ask:

I have a Sempron 64 (MMX, Extended 3DNow!, SSE, SSE2, AMD64), ill use 32 bits system only, but to select my kind of processor in menuconfig i dunno if i put k8 or athlon64...      


PS: i put i686 last time i compile, but i wanna try to do somethink better now,...

---

### Post by Sidhy on 2006-08-05
iptables are not enabled by default for version 2.6.17.7 would be nice if you add how to enable them :)

---

### Post by mlind on 2006-08-05
> **Sidhy said:**
> iptables are not enabled by default for version 2.6.17.7 would be nice if you add how to enable them :)

If you search this thread you should find the answer. Config names of iptables modules have changed and that's why oldconfig target doesn't include these even if your old .config did.

---

### Post by rasec on 2006-08-05
> **bastupungen said:**
> I did what you said and now the kernel boots and loads in to X/KDE nicely. Though what i noticed after i loaded the kernel was that for some reason the bcm43xx module was not loaded and when i check make xconfig for the kernel compiled i cannot find the bcm43xx option.(well i find it if i choose to "show all" but i cannot check it) And this was one of the reasons to try compiling kernels (and also too learn)

Why is this? do i have to install the bcm43xx from scratch? Why??? did the bcm43xx option just disappear like that?

/jonatan

There are a couple of things you need to select to get the bcm43xx driver working. The gentoo guys seem to have a nice guide for setting up the driver here: [http://forums.gentoo.org/viewtopic-t-409194.html](http://forums.gentoo.org/viewtopic-t-409194.html)

Also, someone had a similar issue to yours in the powerpc forum. You may want to take a look at that thread over there: [http://www.ubuntuforums.org/showthread.php?t=219062](http://www.ubuntuforums.org/showthread.php?t=219062)

---

### Post by Jengist on 2006-08-06
> **linuxnewbie946 said:**
> [7][COLOR="Blue"]Install the .deb files in /usr/src. There should be 2. One should be an image .deb file and the other a header .deb file. In terminal do:[/COLOR]
```
dpkg -i <name of the file>
```
DO THIS FOR BOTH FILES.

I got to this step and couldn't find the .deb files in /usr/src

I have a link called 'linux', a folder called 'linux-2.6.17.7', a folder called 'RPM' and a tar archive called 'linux-2.6.17.tar.bz2'. But nothing with 'image' or header in any of those or their contents. What am I missing?

Edit: Problem solved. I started over and desected nearly every option in qconf as I don't really use the machine much for anything other than internet browsing. All the errors I got first time around were for modules and kernel parts I'd never use or inapplicable for my machine like Bluetooth and the like so I guess it just makes for a leaner kernel without superfluous modules and less margin for error during the compile. 

It's all worked pretty well so far but without any of the speed increases I've found with a number of other changes like selecting a more minimalist theme, using Swiftfox or ditching uneeded services with BUM.

---

### Post by tseliot on 2006-08-06
> **shiver said:**
> I found a fix for my second hard drive not mounting:

[http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10)

Apparently it concerns any system with more than one HDD. :\ Perhaps the evms-patch should be added to the howto?

I have the same problem. Thanks for the link to the patch

---

### Post by salamaza on 2006-08-06
hi after i enter this inn terminal
sudo cp /boot/config-`uname -r` .config && sudo make xconfig

i get 

Makefile:266: /usr/src/linux-2.6.17.7/scripts/Kbuild.include: No such file or directory
/bin/sh: line 0: [: -lt: unary operator expected
make: *** No rule to make target `/usr/src/linux-2.6.17.7/scripts/Kbuild.include'.  Stop.
salam@salam-desktop:/usr/src/linux$


Edit, i tryed serval times...still get same error.....

---

### Post by Ryan H on 2006-08-07
> **Metacarpal said:**
> See those 4 or 5 entries with the word "budget" in them?  Those are the culprits.
Everything compiled ok. But when I tried to boot it up X Server couldn't start. I couldn't see all of the error because my monitor was messed up but this is what I got > FATAL: MOUDLE NVIDIA NOT FOUND

Did I forget to uncheck something?

-Ryan H

---

### Post by originof on 2006-08-10
thanks for the tutorial, but i've 3 problem after i update kernel...

1 - i can't see the screen with steps after grub loading...
    Same thing when i close ubuntu...
2 - i can't install Ati driver from repository....fglrxinfo give me    always "mesa"

3 - Ubuntu doesn't load 2 partition in fstab with ext3 and vfat fylesystem..also manually it give me an error about hdb1 and hdb2 are already mounted...but when i umount them he says that aren't mounted...

Excuse for my english...

---

### Post by hfdragon on 2006-08-10
> **originof said:**
> thanks for the tutorial, but i've 3 problem after i update kernel...

1 - i can't see the screen with steps after grub loading...
    Same thing when i close ubuntu...

You need to enable a few more things in the config before compilation of the kernel. more infos here : [http://ubuntuforums.org/showthread.php?t=222326]("http://ubuntuforums.org/showthread.php?t=222326")

> 2 - i can't install Ati driver from repository....fglrxinfo give me    always "mesa"

Ati drivers in the repository are for the 2.6.15 kernels... 
You need to install drivers from ATI. Please read the [Using the drivers from ati.com]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") section.
More infos here : [http://ubuntuforums.org/showthread.php?t=209894]("http://ubuntuforums.org/showthread.php?t=209894")


I think all of this has already been written somewhere above in this thread... 

> 3 - Ubuntu doesn't load 2 partition in fstab with ext3 and vfat fylesystem..also manually it give me an error about hdb1 and hdb2 are already mounted...but when i umount them he says that aren't mounted...

I don't have this problem sorry i can't answer this one... ;)

---

### Post by mlind on 2006-08-10
> **originof said:**
> 
3 - Ubuntu doesn't load 2 partition in fstab with ext3 and vfat fylesystem..also manually it give me an error about hdb1 and hdb2 are already mounted...but when i umount them he says that aren't mounted...


```

[I]The 2.6 kernels now prevent multiple "owners" of a block-device. This
means that the stock kernel will not allow you to mount a filesystem on one
of the kernel's built-in disk-partitions as well as use EVMS to activate
volumes on that disk.
[/I]
```
Search for evms and bd-claim patch to solve this issue.

---

### Post by originof on 2006-08-11
ok, thanks to all....i resolved the problem....but i can't install Ati driver....

when i do in terminal ```
sudo module-assistant build,install fglrx-kernel
```

i get an error...this is the log file
> dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17-ck1.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/kernel-headers-2.6.17-ck1 SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/kernel-headers-2.6.17-ck1'
/usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile:38: /usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu: Nessun file o directory
make[1]: *** No rule to make target `/usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu'.  Stop.
make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17-ck1'
make: *** [build] Error 2

excuse me for bad english :-P

---

### Post by phenolholic on 2006-08-11
I get this error messages

In file included from drivers/usb/net/zd1211/zdusb.c:41:
drivers/usb/net/zd1211/zddevlist.h:7:2: error: #error "Error in source file, lin e 35"
make[5]: *** [drivers/usb/net/zd1211/zdusb.o] Error 1
make[4]: *** [drivers/usb/net/zd1211] Error 2
make[3]: *** [drivers/usb/net] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [stamp-build] Error 2

---

### Post by WishMaster on 2006-08-13
Compiled 2.6.17.7 and it works.

Standard Ubuntu kernel is 2.6.15. 
As I read [here]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#Intel_Cards") I need kernel >2.6.16 for XGL. That's why I compiled this kernel.

According to [this thread]("http://www.ubuntuforums.org/showthread.php?t=145068") I need DRI-modules for XGL.
But the only dri-modules I can find in Synaptic are those for the standard kernel (2.6.15).

The kernel how-to said this:
>  Q: How can I get fglrx and DRI working on my new kernel ?
A: Type this in terminal:

     Quote:
                                                 sudo apt-get install fglrx-kernel-source                         
  Reboot and if that does not work, make sure fglrx is in the Driver section. 
Still no dri-modules. And which "driver section" does it refer to??
Where can I find/compile these dri-modules?


[SIZE=4]_[IMG]http://ubuntu.vdb-studios.be/sysinfo.gif[/IMG] Specs_[/SIZE]
     Pentium-M 1,4 Ghz
     512 MB RAM (2 x 256)
     Toshiba 40GB 4200rpm HDD (replaced with a new HDD after mechanic failure) 
     Intel i855GM chipset 400 MHz FSB with integrated graphics
     15" TFT display designed for 1400x1050 with 1 ext. VGA port
     Broadcom 4401 10/100 Ethernet Card
     Smart Link v.92 internal modem
     Intel PRO/Wireless 2100 802.11b card
     O2 Micro smart card reader
     SmartMedia/MMC/SD/MemoryStick reader
     1 32bit type II PCMIA CardBus slot
     1 IR, 1 IEEE 1394 (FireWire), 4 USB 2.0
     1 S-VHS out, 1 Parallell, 1 RJ-11, 1 RJ-45
     1 Headphone/Line-Out, 1 Line-In, 1 Mic-In

---

### Post by zasf on 2006-08-14
Here is the full procedure for compiling and installing latest fglrx driver with your own kernel

```
# compile and install your own kernel
cd ~
mkdir ati
cd ati
# download the latest ati installer
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-i386.run
chmod +x ati-driver-installer-8.27.10-i386.run
LANG=C LC_ALL=C ./ati-driver-installer-8.23.7-i386.run --buildpkg Ubuntu/dapper
# install the source (tar.bz2 file will be placed in /usr/src)
sudo dpkg -i fglrx-kernel-source_8.23.7-1_i386.deb
cd /usr/src
# untar fglrx.tar.bz2 (will be unzipped in /usr/src/modules/fglrx)
sudo tar xvf fglrx.tar.bz2
# make sure that /usr/src/linux point to the right kernel
cd /usr/src/linux
# substitute '-z2' with your own, debs will be placed in /usr/src
sudo make-kpkg --append-to-version=-z2 modules_image
cd /usr/src
# install the kernel module and xorg driver
sudo dpkg -i fglrx-kernel-2.6.16-mm2-z2_8.27.10-1+10.00.Custom_i386.deb
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
# reboot and check with
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5946 (8.27.10)
```

Hope it helps, you may want to link from the first post.

---

### Post by peterthewolf on 2006-08-14
At step 4 I got this what am I doing wrong ?


peter@blackburn:/usr/src/linux$ sudo cp /boot/config-2.6.15-26-386 .config && sudo make xconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  CHECK   qt
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:53:warning: trying to assign nonexistent symbol CC_ALIGN_FUNCTIONS
.config:54:warning: trying to assign nonexistent symbol CC_ALIGN_LABELS
.config:55:warning: trying to assign nonexistent symbol CC_ALIGN_LOOPS
.config:56:warning: trying to assign nonexistent symbol CC_ALIGN_JUMPS
.config:66:warning: trying to assign nonexistent symbol OBSOLETE_MODPARM
.config:144:warning: trying to assign nonexistent symbol X86_UP_APIC_DEFAULT_OFF.config:166:warning: trying to assign nonexistent symbol 05GB
.config:167:warning: trying to assign nonexistent symbol 1GB
.config:168:warning: trying to assign nonexistent symbol 2GB
.config:169:warning: trying to assign nonexistent symbol 3GB
.config:210:warning: trying to assign nonexistent symbol ACPI_SBS
.config:220:warning: trying to assign nonexistent symbol ACPI_PCC
.config:221:warning: trying to assign nonexistent symbol ACPI_SONY
.config:229:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:230:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:231:warning: trying to assign nonexistent symbol ACPI_DEV
.config:303:warning: trying to assign nonexistent symbol PCI_LEGACY_PROC
.config:336:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:477:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:479:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:480:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:481:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:482:warning: trying to assign nonexistent symbol IP_NF_MATCH_MULTIPORT
.config:487:warning: trying to assign nonexistent symbol IP_NF_MATCH_AH_ESP
.config:488:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:490:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:491:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:492:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:493:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:495:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:497:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:498:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:499:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:500:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:501:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:502:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:504:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:510:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:527:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:528:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:530:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:533:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:543:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:544:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:549:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MULTIPORT
.config:551:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:553:warning: trying to assign nonexistent symbol IP6_NF_MATCH_AHESP
.config:554:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:556:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:560:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:562:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:611:warning: trying to assign nonexistent symbol IP_DCCP_UNLOAD_HACK
.config:830:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:831:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:832:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:833:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:896:warning: trying to assign nonexistent symbol MTD_CFI_AMDSTD_RETRY
.config:941:warning: trying to assign nonexistent symbol MTD_BLKMTD
.config:1045:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:1056:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:1077:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:1086:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1118:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1161:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1169:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1170:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1184:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1185:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1204:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1226:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1274:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1279:warning: trying to assign nonexistent symbol SCSI_QLA6312
.config:1382:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1536:warning: trying to assign nonexistent symbol R1000
.config:1559:warning: trying to assign nonexistent symbol NET_IPG
.config:1610:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1632:warning: trying to assign nonexistent symbol ADM8211
.config:1643:warning: trying to assign nonexistent symbol WLAN_NG
.config:1644:warning: trying to assign nonexistent symbol PRISM2
.config:1645:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1646:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1647:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1648:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1649:warning: trying to assign nonexistent symbol NET_ACX
.config:1650:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1651:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1659:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1660:warning: trying to assign nonexistent symbol NET_RT2600
.config:1661:warning: trying to assign nonexistent symbol NET_RT2500
.config:1662:warning: trying to assign nonexistent symbol NET_RT2400
.config:1663:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1664:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1665:warning: trying to assign nonexistent symbol IPW3945
.config:1666:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1667:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1668:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1717:warning: trying to assign nonexistent symbol VENDOR_SANGOMA
.config:1783:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1936:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1937:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1938:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1939:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1940:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1941:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1942:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1943:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1944:warning: trying to assign nonexistent symbol MISDN_DSP
.config:2023:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:2048:warning: trying to assign nonexistent symbol ECC
.config:2078:warning: trying to assign nonexistent symbol SERIAL_8250_ACPI
.config:2304:warning: trying to assign nonexistent symbol SENSORS_RTC8564
.config:2306:warning: trying to assign nonexistent symbol RTC_X1205_I2C
.config:2316:warning: trying to assign nonexistent symbol W1_MATROX
.config:2317:warning: trying to assign nonexistent symbol W1_DS9490
.config:2318:warning: trying to assign nonexistent symbol W1_DS9490_BRIDGE
.config:2319:warning: trying to assign nonexistent symbol W1_THERM
.config:2320:warning: trying to assign nonexistent symbol W1_SMEM
.config:2322:warning: trying to assign nonexistent symbol W1_DS2433_CRC
.config:2370:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2371:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2425:warning: trying to assign nonexistent symbol VIDEO_AUDIO_DECODER
.config:2426:warning: trying to assign nonexistent symbol VIDEO_DECODER
.config:2522:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2544:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2552:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2565:warning: trying to assign nonexistent symbol DXR3
.config:2566:warning: trying to assign nonexistent symbol EM8300
.config:2567:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2568:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2569:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2570:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2571:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2572:warning: trying to assign nonexistent symbol ADV717X
.config:2573:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2574:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2575:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2576:warning: trying to assign nonexistent symbol BT865
.config:2602:warning: symbol value 'm' invalid for FB_VESA
.config:2623:warning: trying to assign nonexistent symbol FB_RADEON_OLD
.config:2631:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2650:warning: trying to assign nonexistent symbol FB_IMAC
.config:2700:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2813:warning: trying to assign nonexistent symbol BT_ALSA
.config:2819:warning: trying to assign nonexistent symbol OBSOLETE_OSS_DRIVER
.config:2887:warning: trying to assign nonexistent symbol OBSOLETE_OSS_USB_DRIVER
.config:2928:warning: trying to assign nonexistent symbol USB_MTOUCH
.config:2929:warning: trying to assign nonexistent symbol USB_ITMTOUCH
.config:2930:warning: trying to assign nonexistent symbol USB_EGALAX
.config:2937:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2938:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2959:warning: trying to assign nonexistent symbol USB_QC
.config:2960:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2961:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2963:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2964:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2988:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2989:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2990:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2991:warning: trying to assign nonexistent symbol USB_RT2570
.config:3157:warning: trying to assign nonexistent symbol DAZUKO
.config:3200:warning: trying to assign nonexistent symbol RELAYFS_FS
.config:3209:warning: trying to assign nonexistent symbol ASFS_FS
.config:3210:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:3211:warning: trying to assign nonexistent symbol ASFS_RW
.config:3230:warning: trying to assign nonexistent symbol SQUASHFS
.config:3231:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:3232:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:3240:warning: trying to assign nonexistent symbol UNION_FS
.config:3287:warning: trying to assign nonexistent symbol GFS_FS
.config:3288:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:3409:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3474:warning: trying to assign nonexistent symbol CLUSTER
peter@blackburn:/usr/src/linux$

---

### Post by WishMaster on 2006-08-14
> **zasf said:**
> Here is the full procedure for compiling and installing latest fglrx driver with your own kernel

```
# compile and install your own kernel
cd ~
mkdir ati
cd ati
# download the latest ati installer
...
``` 
Hope it helps, you may want to link from the first post.

Do I have an ATI card then ??

---

### Post by zasf on 2006-08-15
> **WishMaster said:**
> Do I have an ATI card then ??

You should know what card you have, from your previous [post]("http://ubuntuforums.org/showpost.php?p=1375291&postcount=165") I read 'Intel i855GM chipset 400 MHz FSB with integrated graphics', but I have no idea wich drivers you should use.

---

### Post by voltagex on 2006-08-15
This guide works still for 2.6.17.8

Thanks

---

### Post by programgeek on 2006-08-15
Well done, linuxnewbie946. :)

---

### Post by Jengist on 2006-08-15
I recently reinstalled and changed from Ubuntu to Xubuntu after successfully compiling a newer kernel in Ubuntu. In Xubuntu though, I keep getting this;
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:54:warning: trying to assign nonexistent symbol CC_ALIGN_FUNCTIONS
.config:55:warning: trying to assign nonexistent symbol CC_ALIGN_LABELS
.config:56:warning: trying to assign nonexistent symbol CC_ALIGN_LOOPS
.config:57:warning: trying to assign nonexistent symbol CC_ALIGN_JUMPS
.config:67:warning: trying to assign nonexistent symbol OBSOLETE_MODPARM
.config:144:warning: trying to assign nonexistent symbol ENABLE_ALT_SMP
.config:170:warning: trying to assign nonexistent symbol 05GB
.config:171:warning: trying to assign nonexistent symbol 1GB
.config:172:warning: trying to assign nonexistent symbol 2GB
.config:173:warning: trying to assign nonexistent symbol 3GB
.config:216:warning: trying to assign nonexistent symbol ACPI_SBS
.config:227:warning: trying to assign nonexistent symbol ACPI_PCC
.config:228:warning: trying to assign nonexistent symbol ACPI_SONY
.config:236:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:237:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:238:warning: trying to assign nonexistent symbol ACPI_DEV
.config:310:warning: trying to assign nonexistent symbol PCI_LEGACY_PROC
.config:344:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:485:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:487:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:488:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:489:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:490:warning: trying to assign nonexistent symbol IP_NF_MATCH_MULTIPORT
.config:495:warning: trying to assign nonexistent symbol IP_NF_MATCH_AH_ESP
.config:496:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:498:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:499:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:500:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:501:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:503:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:505:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:506:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:507:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:508:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:509:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:510:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:512:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:518:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:535:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:536:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:538:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:541:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:551:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:552:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:557:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MULTIPORT
.config:559:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:561:warning: trying to assign nonexistent symbol IP6_NF_MATCH_AHESP
.config:562:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:564:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:568:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:570:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:619:warning: trying to assign nonexistent symbol IP_DCCP_UNLOAD_HACK
.config:838:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:839:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:840:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:841:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:904:warning: trying to assign nonexistent symbol MTD_CFI_AMDSTD_RETRY
.config:949:warning: trying to assign nonexistent symbol MTD_BLKMTD
.config:1053:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:1064:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:1085:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:1094:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1126:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1169:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1177:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1178:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1192:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1193:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1212:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1234:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1282:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1287:warning: trying to assign nonexistent symbol SCSI_QLA6312
.config:1390:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1544:warning: trying to assign nonexistent symbol R1000
.config:1567:warning: trying to assign nonexistent symbol NET_IPG
.config:1618:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1640:warning: trying to assign nonexistent symbol ADM8211
.config:1651:warning: trying to assign nonexistent symbol WLAN_NG
.config:1652:warning: trying to assign nonexistent symbol PRISM2
.config:1653:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1654:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1655:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1656:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1657:warning: trying to assign nonexistent symbol NET_ACX
.config:1658:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1659:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1667:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1668:warning: trying to assign nonexistent symbol NET_RT2600
.config:1669:warning: trying to assign nonexistent symbol NET_RT2500
.config:1670:warning: trying to assign nonexistent symbol NET_RT2400
.config:1671:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1672:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1673:warning: trying to assign nonexistent symbol IPW3945
.config:1674:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1675:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1676:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1725:warning: trying to assign nonexistent symbol VENDOR_SANGOMA
.config:1791:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1943:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1944:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1945:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1946:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1947:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1948:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1949:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1950:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1951:warning: trying to assign nonexistent symbol MISDN_DSP
.config:2030:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:2055:warning: trying to assign nonexistent symbol ECC
.config:2084:warning: trying to assign nonexistent symbol SERIAL_8250_ACPI
.config:2284:warning: trying to assign nonexistent symbol SENSORS_RTC8564
.config:2286:warning: trying to assign nonexistent symbol RTC_X1205_I2C
.config:2296:warning: trying to assign nonexistent symbol W1_MATROX
.config:2297:warning: trying to assign nonexistent symbol W1_DS9490
.config:2298:warning: trying to assign nonexistent symbol W1_DS9490_BRIDGE
.config:2299:warning: trying to assign nonexistent symbol W1_THERM
.config:2300:warning: trying to assign nonexistent symbol W1_SMEM
.config:2302:warning: trying to assign nonexistent symbol W1_DS2433_CRC
.config:2350:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2351:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2405:warning: trying to assign nonexistent symbol VIDEO_AUDIO_DECODER
.config:2406:warning: trying to assign nonexistent symbol VIDEO_DECODER
.config:2502:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2524:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2532:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2545:warning: trying to assign nonexistent symbol DXR3
.config:2546:warning: trying to assign nonexistent symbol EM8300
.config:2547:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2548:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2549:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2550:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2551:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2552:warning: trying to assign nonexistent symbol ADV717X
.config:2553:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2554:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2555:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2556:warning: trying to assign nonexistent symbol BT865
.config:2582:warning: symbol value 'm' invalid for FB_VESA
.config:2603:warning: trying to assign nonexistent symbol FB_RADEON_OLD
.config:2611:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2630:warning: trying to assign nonexistent symbol FB_IMAC
.config:2680:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2793:warning: trying to assign nonexistent symbol BT_ALSA
.config:2799:warning: trying to assign nonexistent symbol OBSOLETE_OSS_DRIVER
.config:2867:warning: trying to assign nonexistent symbol OBSOLETE_OSS_USB_DRIVER
.config:2908:warning: trying to assign nonexistent symbol USB_MTOUCH
.config:2909:warning: trying to assign nonexistent symbol USB_ITMTOUCH
.config:2910:warning: trying to assign nonexistent symbol USB_EGALAX
.config:2917:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2918:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2939:warning: trying to assign nonexistent symbol USB_QC
.config:2940:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2941:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2943:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2944:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2968:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2969:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2970:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2971:warning: trying to assign nonexistent symbol USB_RT2570
.config:3137:warning: trying to assign nonexistent symbol DAZUKO
.config:3180:warning: trying to assign nonexistent symbol RELAYFS_FS
.config:3189:warning: trying to assign nonexistent symbol ASFS_FS
.config:3190:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:3191:warning: trying to assign nonexistent symbol ASFS_RW
.config:3210:warning: trying to assign nonexistent symbol SQUASHFS
.config:3211:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:3212:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:3220:warning: trying to assign nonexistent symbol UNION_FS
.config:3267:warning: trying to assign nonexistent symbol GFS_FS
.config:3268:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:3389:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3454:warning: trying to assign nonexistent symbol CLUSTER
.config:3460:warning: trying to assign nonexistent symbol X86_HT_DISABLE

```
qconf opened OK the first time I tried it with Xubuntu but the resulting headers and image don't allow me to boot. Instead, I get half way through booting then it just chokes with a repeated message about a runaway module loop and binfmt 486c. I didn't see those earlier error messages in the terminal until I tried to compile again.

Why would it be so different to the first time when I successfully compiled a kernel in Ubuntu? I have an image and headers for 2.6.17.8 sitting in /src/linux so is there something I can do to get those working or should I just work out how to get it going from scratch?

---

### Post by krugman on 2006-08-15
Hello!
I just tried to install this kernel everything seemed to worked fine but then after awhile I got these errors:

```
drivers/media/dvb/ttpci/budget-av.c: In function ‘frontend_init’:
drivers/media/dvb/ttpci/budget-av.c:1063: error: ‘struct budget_av’ has no member named ‘reinitialise_demod’
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member ‘tuner_ops’ in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: ‘philips_cu1216_tuner_set_params’ undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in.)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

```

any ideas???

---

### Post by mlind on 2006-08-15
> **krugman said:**
> Hello!
I just tried to install this kernel everything seemed to worked fine but then after awhile I got these errors:

```
drivers/media/dvb/ttpci/budget-av.c: In function ‘frontend_init’:
drivers/media/dvb/ttpci/budget-av.c:1063: error: ‘struct budget_av’ has no member named ‘reinitialise_demod’
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member ‘tuner_ops’ in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: ‘philips_cu1216_tuner_set_params’ undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in.)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

```

any ideas???

scroll back few pages of this thread to find the answer. You need to either get 2.6.17.8 kernel or don't disable build of that module from kernel config.

---

### Post by mattme on 2006-08-15
Should you be compiling as root? You don't need the superuser until install. With the source in /usr/src/linux-X you can run make unpriveleged to output to your /home        

(from the README)
   cd /usr/src/linux-2.6.N
   make O=/home/name/build/kernel menuconfig
   make O=/home/name/build/kernel
   sudo make O=/home/name/build/kernel modules_install install

Best not to 'rm -rf /usr/src/linux' either, that directory is reserved for the original headers glibc was built against.

---

### Post by mlind on 2006-08-15
> **mattme said:**
> Why should you be building the kernel as root? You don't need the superuser until you install.

There's no point of using root privileges at all. Just add yourself to **src** group to get write permission to /usr/src and use fakeroot with make-kpkg.

---

### Post by mattme on 2006-08-15
That's the style =) I suspect one is added automatically to **src**, I find myself already a member.

---

### Post by krugman on 2006-08-16
Ok, thanks I have seen my mistake! So I just did this and it seems that everything went ok, but upon rebooting, he loads the new kernel in Grub but then, I got the following message: "Kernel panic -not syncing VFS: Unable to mount root fs on unknown-block(0,0)"
ant it stopped booting!

any ideas???

---

### Post by dim4ik on 2006-08-16
Compiled 2.6.17.8 :cool:

---

### Post by DiamondX on 2006-08-17
[Sorry, I only read the first post.]
Great guide, but where you said it takes 1-3 hours to compile, I typed in
```
time make-kpkg -initrd --revision=k8 kernel_image kernel_headers modules_image
```
and here is the [time] output:
```
real    22m59.022s
user    18m56.047s
sys     2m31.769s
```
Only 23 minutes! That is on an Athlon64, with the latest kernel (from repository, otherwise I wouldnt be installing this!). I havnt rebooted yet, but installing the debs went fine. If I have problems, Ill edit this post. I still gotta install the nVidia drivers.

Edit: I booted it, but the nvidia drivers wouldnt work. Atleast 'uname -r' gives 2.6.17.7! I guess it worked!
Edit2:I got the nvidia drivers working, it looks good! BTW, this is (going to be) a mythtv box...

---

### Post by WishMaster on 2006-08-17
So I need DRI-modules for xgl...
I also need kernel > 2.6.16 for my intel855GM card.

So I compiled 2.6.17.7.
According to [http://dri.sourceforge.net/doc/DRIcompile.html](http://dri.sourceforge.net/doc/DRIcompile.html) I need to enable some things in "make menuconfig"

>                                                  Configure your kernel. You might, for example, use make menuconfig and do the following:[LIST]
[*]Go to *Code maturity level options*
[*]Enable *Prompt for development and/or incomplete code/drivers*
[*]hit ESC to return to the top-level menu
[*]Go to *Processor type and features*
[*]Select your processor type from *Processor Family*
[*]hit ESC to return to the top-level menu
[*]Go to *Character devices*
[*]Disable *Direct Rendering Manager (XFree86 DRI support)* since we'll use the DRI code from the XFree86/DRI tree and will compile it there.
[*]Go to */dev/agpgart (AGP Support) (EXPERIMENTAL) (NEW)*
[*]Hit SPACE twice to build AGP support into the kernel
[*]Enable all chipsets' support for AGP
[*]It's recommended that you turn on MTRRs under *Processor type and Features*, but not required.[/LIST]Configure the rest of the kernel as required for your system (i.e. Ethernet, SCSI, etc)                      
          
 Did all of that. No dri-modules.... only the dri-modules from the standard Ubuntu kernel (2.6.15)

---

### Post by dim4ik on 2006-08-19
So, I try to compile 2.6.17.8 on another machine, but I have following Error's:

```

init/built-in.o: In function `try_name':do_mounts.c:(.text+0x651): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t': undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy': undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root': undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':initramfs.c:(.init.text+0x4507): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o: more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.8'
make: *** [stamp-build] Error 2

```
How can I solve it :confused:

P.S. I used my old .config from 2.6.17-5-k7 kernel without any changes.

---

### Post by mattme on 2006-08-19
dim4ik, You can't use a .config from an older kernel straight off as it will omit newer options introduced to the kernel. Run "make oldconfig" after you've copied it, and you'll be prompted only wherever the new kernel differs. It shouldn't take long.

That may not be your problem however.

---

### Post by LordRaiden on 2006-08-19
I managed to fix this from this link [http://www.uwsg.iu.edu/hypermail/lin...07.1/2123.html]("http://www.uwsg.iu.edu/hypermail/linux/kernel/0607.1/2123.html")

The part to use as a patch is

 	Code:
 	[LEFT] diff --git a/Makefile b/Makefile
index 7c010f3..b4a2a80 100644
--- a/Makefile
+++ b/Makefile
@@ -308,7 +308,7 @@ LINUXINCLUDE    := -Iinclude \
 CPPFLAGS        := -D__KERNEL__ $(LINUXINCLUDE)
 
 CFLAGS          := -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
-                   -fno-strict-aliasing -fno-common
+                   -fno-strict-aliasing -fno-common -fno-stack-protector
 # Force gcc to behave correct even for buggy distributions
 CFLAGS          += $(call cc-option, -fno-stack-protector-all \
                                      -fno-stack-protector)[/LEFT]
 
 I manually edited the Makefile in the top-level directory (/usr/src/linux) since I could not get it working using patch.

[B]Please not that this patch is needed only by Ubuntu Edgy users.

UPDATE[/B] - I used this patch and I successfully compiled 2.6.17.7 - great instructions! 		 	 		 		 		 		 			 				__________________

---

### Post by konan on 2006-08-20
Hello!

I followd the howto and sucessfuly compiled latest stable kernel, but at boot I always end up with error;
at boot time, kernel reports -> 
> WARNING: Could not open directory /lib/modules/2.6.17.9 No such file or directory
FATAL: Could not open /lib/modules/2.6.17.9/modules.dep.temp for writing: No such file or directory

System then boots up, but I cant modprobe any of the modules in /lib/modules
> 
modprobe /lib/modules/2.6.17.9/kernel/crypto/des.ko
FATAL: Module /lib/modules/2.6.17.9/kernel/crypto/des.ko not found

If I use modinfo /lib/modules/2.6.17.9/kernel/crypto/des.ko it prints info about module.

Don't know what else to do!!

Help appriciated... :)

---

### Post by gizmoog on 2006-08-20
thanks for your tuto

I am new in Linux and I just install Drapper and kernel 2.6.17 and it seems to work. But I do not have wifi anymore. In the previous kernel, ndiswrapper was not used (asus notebook with Intel Corporation PRO/Wireless 2200BG (rev 05)). Do I have to use ndiswrapper as written at the end of your tuto ?
Moreover, I tried to use ndiswrapper and everything seems to be ok untill i do
> sudo modprobe ndiswrapper

At that time, ubuntu freeze and I have to reboot (with power button...).

Does anybody has a solution for me ?

thanks
gizmoog

---

### Post by gizmoog on 2006-08-20
thanks for your tuto

I am new in Linux and I just install Drapper and kernel 2.6.17 and it seems to work. But I do not have wifi anymore. In the previous kernel, ndiswrapper was not used (asus notebook with Intel Corporation PRO/Wireless 2200BG (rev 05)). Do I have to use ndiswrapper as written at the end of your tuto ?
Moreover, I tried to use ndiswrapper and everything seems to be ok untill i do
> sudo modprobe ndiswrapper

At that time, ubuntu freeze and I have to reboot (with power button...).

Does anybody has a solution for me ?

thanks
gizmoog

---

### Post by StreetSmart on 2006-08-22
Hey I'm currently running the 2.6.15-26-386 kernel which was the default on ubuntu 6.06.1 install. I have also installed my ATI drivers using the tutorial [Here.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") 
And I was just wondering, am I going to have to install the drivers again if i install the 2.6.17 kernel? And if not why not?

Also, I've been compiling kernels for a while now and never really understood the make menuconfig command. How do I know exactly what I need to have checked on/off?

Thanks guys.

---

### Post by quik77 on 2006-08-22
I just compiled the 2.6.17.9 AMD64 kernel last night, and now everythign except my non root hd's works, tried all the usual methods to mount them and nothing, is there something special have to do when I compile when I have multiple hd's with different file systems?

---

### Post by mlind on 2006-08-22
> **quik77 said:**
> I just compiled the 2.6.17.9 AMD64 kernel last night, and now everythign except my non root hd's works, tried all the usual methods to mount them and nothing, is there something special have to do when I compile when I have multiple hd's with different file systems?

If you mean you can't seem to mount your other partitions, then you need to apply so called "bd-claim" patch. You should browse this thread few pages back or search the forums for how to do this.
[http://evms.sourceforge.net/install/kernel.html#bdclaim](http://evms.sourceforge.net/install/kernel.html#bdclaim)

---

### Post by lazyd2 on 2006-08-22
> **quik77 said:**
> I just compiled the 2.6.17.9 AMD64 kernel last night, and now everythign except my non root hd's works, tried all the usual methods to mount them and nothing, is there something special have to do when I compile when I have multiple hd's with different file systems?
[Read this]("http://www.ubuntuforums.org/showpost.php?p=1331175&postcount=130")

---

### Post by lazyd2 on 2006-08-22
...

---

### Post by pcolamar on 2006-08-23
I performed STEP-1 and I got the following msg: 
-------------
palmer@palmer-laptop:~$ sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget && cd /usr/src
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
wget is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libfreetype6-dev but it is not going to be installed
                 Depends: libxft-dev but it is not going to be installed
E: Broken packages
---------------------
Should I worry ?
Can I continue ?
I wasn't able to find a post that talks about that on this thread. eventually point me please to the right one.

Thanks

---

### Post by mlind on 2006-08-23
> **pcolamar said:**
> I performed STEP-1 and I got the following msg: 
-------------
palmer@palmer-laptop:~$ sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget && cd /usr/src
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
wget is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libfreetype6-dev but it is not going to be installed
                 Depends: libxft-dev but it is not going to be installed
E: Broken packages
---------------------
Should I worry ?
Can I continue ?
I wasn't able to find a post that talks about that on this thread. eventually point me please to the right one.

Thanks

You have installed 3rd party packages, probably compiz (or font rendering related?), you need to install Ubuntu originals back. Either use aptitude or explicitly specify version for apt-get.

Dapper's libfreetype6=2.1.10-1ubuntu2.2 and libxft=2.1.8.2-0ubuntu2

---

### Post by pcolamar on 2006-08-23
Mlind; you are right, I installed Compiz.

So, if I understand correctly:

1) I have to stop Compiz (deinstall maybe ?)
2) with apt-get or aptitute çor just Synaptic , I suppose) reinstall the two lib's 

Then I can go back to the HOWTO Kernel Compile , right ?

And correct me if I am wrong, afterword to compile again the ATI driver, Compiz/Xgl, etc etc. Right ? 
(Tnks )

---

### Post by mlind on 2006-08-23
> **pcolamar said:**
> Mlind; you are right, I installed Compiz.

So, if I understand correctly:

1) I have to stop Compiz (deinstall maybe ?)
2) with apt-get or aptitute çor just Synaptic , I suppose) reinstall the two lib's 

Then I can go back to the HOWTO Kernel Compile , right ?

And correct me if I am wrong, afterword to compile again the ATI driver, Compiz/Xgl, etc etc. Right ? 
(Tnks )

1) Yes. Installing other versions for these libraries will probably break compiz (or apt-get/aptitude want's to uninstall it to resolve conflict). I doesn't matter though, you can always install compiz stuff back after you've compiled your vanilla kernel

Optionally, you could check if the repository where you got these compiz dependencies (libcairo2, freetype and probably libxft) provides you -dev packages for these as well. Probably on a separate module or repository?

2) Yeah. I'd recommend aptitude, it's usually smarter of the three.
```

sudo aptitude install libcairo2=1.0.4-0ubuntu1
sudo aptitude install libfreetype6=2.1.10-1ubuntu2.2

```

---

### Post by Soul_Est on 2006-08-24
great how to linuxnewbie946! it is this kind of generosity that keeps ubuntu users coming back to the forums. i was about to try your tutorial when i decided to look up the kernel.org site for the latest kernel. when i got there i saw that there was a patch for the newest 2.6.17.11 kernel and i was wondering if this would give the kernel a performance boost (saw something about arch, maybe related to the linux somehow? ;) ). if anyone can help me with this i would greatly appreciate it. thanks again linuxnewbie946!

---

### Post by pcolamar on 2006-08-25
Ok, I succeded in compiling and using the new kernel.

Now, one more question:
How do I deinstall it ?  

I would like to play with some parameter in .config and I would like to remove/deinstall the test kernels I produce but in Synaptic I do not see the usual "linux-image-2.6.17.7" packge.

GRUB has the 2 line relate to my new kernel though.

So, how do I deinstall and clean up ?

Thanks

---

### Post by mlind on 2006-08-25
> **pcolamar said:**
> Ok, I succeded in compiling and using the new kernel.

Now, one more question:
How do I deinstall it ?  

I would like to play with some parameter in .config and I would like to remove/deinstall the test kernels I produce but in Synaptic I do not see the usual "linux-image-2.6.17.7" packge.

GRUB has the 2 line relate to my new kernel though.

So, how do I deinstall and clean up ?

Thanks

kernel-package creates package called **kernel-image-x.x.xx**

---

### Post by CorruptKode on 2006-08-26
> Install the .deb files in /usr/src. There should be 2. One should be an image .deb file and the other a header .deb file. In terminal do:
Code:

dpkg -i <name of the file>

DO THIS FOR BOTH FILES.


I have no *.deb files in there? what do i do now?

---

### Post by book36worm on 2006-08-27
this is my first experiance w/ ubuntu. i'm trying to get my MS Ergo Keyboard 4000 to work. they directed me to this how to to up date the kernel. i've downloaded and unpacked the 2.6.17.7 version from kernel.org. the third step in this how to is to type the command:

sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.17.7 linux && cd /usr/src/linux

when i do this i get the error:

bash: cd: /usr/src/linux: No such file or directory

please help! i'm new to linux, but good w/ winxp. btw, love this community. very helpful.

---

### Post by mlind on 2006-08-27
> **book36worm said:**
> this is my first experiance w/ ubuntu. i'm trying to get my MS Ergo Keyboard 4000 to work. they directed me to this how to to up date the kernel. i've downloaded and unpacked the 2.6.17.7 version from kernel.org. the third step in this how to is to type the command:

sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.17.7 linux && cd /usr/src/linux

when i do this i get the error:

bash: cd: /usr/src/linux: No such file or directory

please help! i'm new to linux, but good w/ winxp. btw, love this community. very helpful.

You need to perform those commands in /usr/src directory if you're using relative pathnames.. Otherwise you may have symlink called linux on your $HOME directory that root owns and that's not what you want...

With relative paths, you need to do it like this.
```

cd /usr/src
sudo rm -f linux
sudo ln -s linux-2.6.17.7 linux
cd linux

```

---

### Post by book36worm on 2006-08-27
> **mlind said:**
> You need to perform those commands in /usr/src directory if you're using relative pathnames.. Otherwise you may have symlink called linux on your $HOME directory that root owns and that's not what you want...

With relative paths, you need to do it like this.
```

cd /usr/src
sudo rm -f linux
sudo ln -s linux-2.6.17.7 linux
cd linux

```

well that then begs the question, what is a relative pathname and how do i no do that... i've been typing the commands in the preloaded temrinal editor. i've stopped at the third step in this HOW TO, waiting for a resposne. i don't want to crap out my system by stopping half way through something like this. in my home folder i do have a linux file which has an X and lock on it. is this the file that you are refering to?

---

### Post by mlind on 2006-08-27
> **book36worm said:**
> well that then begs the question, what is a relative pathname and how do i no do that... i've been typing the commands in the preloaded temrinal editor. i've stopped at the third step in this HOW TO, waiting for a resposne. i don't want to crap out my system by stopping half way through something like this. in my home folder i do have a linux file which has an X and lock on it. is this the file that you are refering to?

[http://en.wikipedia.org/wiki/Path_(computing](http://en.wikipedia.org/wiki/Path_(computing))
You shouldn't type command(s) which require root priviliges without knowing what does it actually do.

/usr/src is a absolute path, where src is a relative path when working directory is /usr

---

### Post by danderson3 on 2006-08-27
> **quik77 said:**
> I just compiled the 2.6.17.9 AMD64 kernel last night, and now everythign except my non root hd's works, tried all the usual methods to mount them and nothing, is there something special have to do when I compile when I have multiple hd's with different file systems?

There is an old post at [http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10)
which says evms-patch is required to fix this...

I would like to know if this is still true...

David

---

### Post by mlind on 2006-08-28
> **danderson3 said:**
> There is an old post at [http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10)
which says evms-patch is required to fix this...

I would like to know if this is still true...

David

I guess it will always be true for kernel >= 2.6 and evms, so yes.

---

### Post by Anonii on 2006-08-28
I got this error:
>   CC [M]  drivers/media/dvb/ttpci/budget-av.o
drivers/media/dvb/ttpci/budget-av.c: In function ‘frontend_init’:
drivers/media/dvb/ttpci/budget-av.c:1063: error: ‘struct budget_av’ has no member named ‘reinitialise_demod’
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member ‘tuner_ops’ in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: ‘philips_cu1216_tuner_set_params’ undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in.)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

while in the:
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
step...

Can I have some quick help, please? :P

---

### Post by nerdtank on 2006-08-28
of course you can, do a search for DVB_BUDGET_AV, in this thread even, and you're good to go !

---

### Post by hfdragon on 2006-08-28
> **Anonii said:**
> I got this error:

while in the:
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
step...

Can I have some quick help, please? :P

Read the poste earlier in this thread, I think there is a problem with the budget dbv drivers and you need to deselect it in the config part...

---

### Post by Anonii on 2006-08-28
> **hfdragon said:**
> Read the poste earlier in this thread, I think there is a problem with the budget dbv drivers and you need to deselect it in the config part...


Ye I've read it, but I couldnt find these:
Budget cards with Budget Patch
AV7110 cards with BudgetParch

and so I ended up disabling everything that had to do with Budget and AV, to make it work :3

---

### Post by hfdragon on 2006-08-28
I just rebooted on a 2.6.17.11 compiled kernel and it's still working perfectly... almost perfectly ;-)

I seems that I have a problem with my webcam :

It is recognised by the system (here is my dmesg):
```
usb 4-1: new full speed USB device using uhci_hcd and address 2
usb 4-1: configuration #1 chosen from 1 choice
Linux video capture interface: v1.00
pwc Philips webcam module version 9.0.2-unofficial loaded.
pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
pwc Philips PCVC740K (ToUCam Pro)/PCVC840 (ToUCam II) USB webcam detected.
pwc Registered as /dev/video0.
usbcore: registered new driver Philips webcam
usbcore: registered new driver snd-usb-audio

```

But the only picture I get is completly grey :confused: 

The webcam is working perfectly with the 2.6.15.x kernels and I have the same problem with the 2.6.17.7 kernel..

Anyone with an idea ?

Update :

Found the solution myself here :

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090")

---

### Post by Eazy© on 2006-08-29
> **danderson3 said:**
> There is an old post at [http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10)
which says evms-patch is required to fix this...

I would like to know if this is still true...

David

I can confirm this. I had to patch with the 2.6-bd-claim.patch to get my ntfs-disk working.

I have two questions also. I forgot to add support for some things I want, like bootup logo and some other things. 

[COLOR="Red"]1.)[/COLOR] Do I need to start from scratch to recompile my kernel or can I start from step .4 in this howto like this:
```
sudo make xconfig
```
Are the patches and the settings I applied still there? I have not deleted anything since I compiled and installed the "image .deb" and "header .deb".


[COLOR="Red"]2.)[/COLOR] Do I need to reinstall the Nvidia graphics driver when I recompile with the same version of the kernel with just a few changes like add support for the bootup logo?

I had much trouble to install the Nvidia drivers and I dont want to go through that again. Everything works just fine now, but I get I black screen when I boot as I forgot to add support for fbvesa in the kernel (splashy will not work without it). I will not recompile the kernel for this trivial problem if I have to reinstall the Nvidia drivers. I did however find a solution so I get white text when I boot. I added this to the end of the commandline in menu.list
```
kernel		/boot/vmlinuz-2.6.17.7 ro root=/dev/hdb1  [COLOR="Red"]video=nvidiafb[/COLOR]
```

---

### Post by danderson3 on 2006-08-29
I can't snswer #2, but #1 is yes and yes.  Unless you deleted your
source code, the patched versions are there.  Your configuration
was saved in .config, if I am not mistaken, so 'make oldconfig' 
will use it.

David

---

### Post by mlind on 2006-08-29
> **Eazy© said:**
> 
[COLOR="Red"]2.)[/COLOR] Do I need to reinstall the Nvidia graphics driver when I recompile with the same version of the kernel with just a few changes like add support for the bootup logo?

I had much trouble to install the Nvidia drivers and I dont want to go through that again. Everything works just fine now, but I get I black screen when I boot as I forgot to add support for fbvesa in the kernel (splashy will not work without it). I will not recompile the kernel for this trivial problem if I have to reinstall the Nvidia drivers. I did however find a solution so I get white text when I boot. I added this to the end of the commandline in menu.list
```
kernel		/boot/vmlinuz-2.6.17.7 ro root=/dev/hdb1  [COLOR="Red"]video=nvidiafb[/COLOR]
```

If kernel headers are the same then no. Basically you don't need to do that if kernel version is same, but it's better to be safe than sorry..

The easiest way to compile nvidia kernel module is to install package called **module-assistant** and execute **m-a a-i nvidia-kernel-source**.
Then just make sure you have nvidia-glx installed.

---

### Post by OzzOzzOzz on 2006-08-29
Hey

I tried to compile the new kernel, but I ran in to some early problems.

sudo apt-get install libqt3-mt  

returns the following error

libqt3-mt-dev: Depends: libqt3-mt (= 3:3.3.6-1ubuntu3) but 3:3.3.6-1ubuntu6 is to be installed

Anyone got any ideas?

sudo apt-get install libqt3-mt tells me that it is already installed.

Is there a noticable speed difference with the new kernel?

Thanks in advance.

Cheers
Ozz

---

### Post by Anonii on 2006-08-29
> **OzzOzzOzz said:**
> Hey

I tried to compile the new kernel, but I ran in to some early problems.

sudo apt-get install libqt3-mt  

returns the following error

libqt3-mt-dev: Depends: libqt3-mt (= 3:3.3.6-1ubuntu3) but 3:3.3.6-1ubuntu6 is to be installed

Anyone got any ideas?

sudo apt-get install libqt3-mt tells me that it is already installed.

Is there a noticable speed difference with the new kernel?

Thanks in advance.

Cheers
Ozz
[B]
sudo aptitude install libqt3-mt-dev[/B] should fix it, by downgrading 
libqt3-mt.
Else try
*sudo aptitude install libqt3-mt* and then *sudo aptitude install libqt3-mt-dev*

Report back here.

---

### Post by danderson3 on 2006-08-29
> **mlind said:**
> I guess it will always be true for kernel >= 2.6 and evms, so yes.



After further study, I find that:
1) the evms patches are for earlier versions of the kernel 
and the source file they modify **did** change in 2.6.17,
so watch out!

2) evms looks pretty powerful, so I am going to look more at
converting everything to evms management, which means I won't
run into the conflict with the vanilla kernel anyway...

later....
David

---

### Post by OzzOzzOzz on 2006-08-29
Great...thanks.

Trying it now. It seems to be working great.

With regard to the kernel source to be downloaded,
do I have to find the kernel source of the SMP kernel?

I am currently using the SMP kernel aquired by using apt-get.
Will the speed change be noticable?

I think I'll compile the kernel anyway, just to see it work.

Thanks for the help.

Cheers
Ozz

---

### Post by Eazy© on 2006-08-29
@ danderson3 and mlind
Thanx for your respond! I'm compiling write this, and will come back with the results :)

What I did was:

[COLOR="Red"]cd /usr/src/linux[/COLOR]

[COLOR="Red"]sudo make oldconfig[/COLOR]

[COLOR="Red"]sudo make xconfig[/COLOR] made my changes and saved it.

[COLOR="Red"]sudo -s -H[/COLOR]

[COLOR="Red"]make-kpkg clean[/COLOR]

[COLOR="Red"]make-kpkg -initrd --revision=486smp kernel_image kernel_headers modules_image[/COLOR] changed the revision from 486 to 486smp so to not name it exactly the same as my old kernel (thought it might make a conflict or something when I install the debs)

So now it is compiling, but I dont know yet if I dare to install the debs when its done compiling :P


This happen when I try to install the new kernel:

```
Förbereder att ersätta kernel-image-2.6.17.7 486 (med kernel-image-2.6.17.7_486smp_i386.deb) ...
You are attempting to install a kernel image (version 2.6.17.7)
However, the directory /lib/modules/2.6.17.7 still exists.  If this
directory belongs to a previous kernel-image-2.6.17.7 package, and if
you have deselected some modules, or installed standalone modules
packages, this could be bad. However, if this directory exists because
you are also installing some stand alone modules right now, and they
got unpacked before I did, then this is pretty benign.  Unfortunately,
I can not tell the difference.

If /lib/modules/2.6.17.7 belongs to a old install of
kernel-image-2.6.17.7, then this is your last chance to abort the
installation of this kernel image (nothing has been changed yet).

If this directory is because of stand alone modules being installed
right now, or if it does belong to an older kernel-image-2.6.17.7
package but you know what you are doing, and if you feel that this
image should be installed despite this anomaly, Please answer n to the
question.

Otherwise, I suggest you move /lib/modules/2.6.17.7 out of the way,
perhaps to /lib/modules/2.6.17.7.old or something, and then try
re-installing this image.
Do you want to stop now? [Y/n] 
```  

Is it safe to ignore this or should I not proceed.

Perhaps I should name it with the same name "486" instead of "486smp"?

Edit: I accidently pressed N and I had no choise than continue. But it all worked. When I rebooted, X started just fine so I didnt need to reinstall the Nvidia drivers. Now I got every thing working my way :)

---

### Post by OzzOzzOzz on 2006-08-29
Great guide, just finished and got my new kernel up and running.

Once question though:
On the grub boot menu, its says the kernel is myname_i386,
but
uname -m     prints i686

What version of the kernel is it? 386 or 686? 
(I previously had the i686smp kernel)

Thanks
Ozz

---

### Post by Eazy© on 2006-08-29
Write [COLOR="Red"]top[/COLOR] in a consol and press 1

If you see 2 cpu's, then you got 686-kernel.

---

### Post by danderson3 on 2006-08-30
> **linuxnewbie946 said:**
> Feel free to ask any questions......

I patched 2.6.17 with beyond3 and did
make xconfig
make-kpkg clean
make-kpkg -initrd --revision=686 kernel_image kernel_headers modules_image

now when I dpkg -i kernel-headers-2.6.17.7_686_i386.deb

I get the error:

dpkg: error processing kernel-headers-2.6.17.7_686_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-headers-2.6.17.7_686_i386.deb

How can I debug this?

thanks,
David

---

### Post by danderson3 on 2006-08-30
BTW, my source directory is linux-2.6.17.  Do I have to
rename this?

David

---

### Post by hfdragon on 2006-08-30
> **danderson3 said:**
> 
now when I dpkg -i kernel-headers-2.6.17.7_686_i386.deb

I get the error:

dpkg: error processing kernel-headers-2.6.17.7_686_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-headers-2.6.17.7_686_i386.deb

How can I debug this?


I remember having this problem... I just forgot to "cd .." befor "dprkg -i ..."

When we make the .deb files, we are in /usr/src/linux, but the .deb files are in /usr/src !!

Hope this helps. :)

---

### Post by danderson3 on 2006-08-30
thanks, but I get the same error.  I would like dpkg to be
more verbose...

David

---

### Post by mlind on 2006-08-30
> **danderson3 said:**
> thanks, but I get the same error.  I would like dpkg to be
more verbose...

David

> 
cannot access archive: No such file or directory

That's verbose to me.

You need to give the actual file as a parameter to *dpkg*. go in to /usr/src folder and list its contents. Then choose install correct kernel-headers .deb package.

```

cd /usr/src
ls
sudo dpkg -i *kernel-headers-x.x.x.deb*

```

---

### Post by danderson3 on 2006-08-30
thanks!  I've been too busy and missed the
obvious...

David

---

### Post by moore.bryan on 2006-08-31
> **kinematic said:**
> no you didn't.
i compiled the 2.6.17.6 kernel on PCLinuxOS and i also don't have iptables support.
i asked about it on the kernel mailing list but i haven't gotten an answer yet.


[I]kinematic...
check out [/I][http://forums.debian.net/viewtopic.php?t=7671&highlight=](http://forums.debian.net/viewtopic.php?t=7671&highlight=)
*found it after i read about the 2.6.17 kernel.*

---

### Post by danderson3 on 2006-09-01
I downloaded vanilla 2.6.17 and patched it
with beyond3.  I configured it to cut out a
lot of useless cruft, but now I have no ethernet.
ifup eth0 returns SIOCSIFADDR and there is no
/dev/eth0.  I know that often this is a sign
the ethernet driver is missing, so I added in
nearly all brands without any success.

Attached is my conf file.  I would appreciate
any suggestions as to how to debug this.

Thanks!
David

---

### Post by danderson3 on 2006-09-02
I started over with the config file and got it working...

-d

---

### Post by RyanR313 on 2006-09-02
I followed the tutorial and everything went ok. I went to dial up and it said the /dev/modem does not exist. if I boot to the 2.6.15-23-386 kernel it works fine. It is a winmodem I did an lspci and got this for the modem 
0000:08:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)
	Subsystem: Actiontec Electronics Inc LT WinModem 56k (MiniPCI Ethernet+Modem)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (63000ns min, 3500ns max)
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f8ffec00 (32-bit, non-prefetchable) [size=256]
	Region 1: I/O ports at ecb8 [size=8]
	Region 2: I/O ports at e800 [size=256]
	Capabilities: <available only to root>

Did I mess something up in the config?

---

### Post by Zmija on 2006-09-03
Yellow,

I've compiled my own kernel! It's really small ( Image + Headers 9.9 MB) but....


Boot time is still 50-55 sec? How come? Can you gave me some performance tips?

THNX

[.config]("http://www.speedyshare.com/320136822.html")

---

### Post by bartman on 2006-09-04
I found that if you really want significant boot/shutdown reduction you have to disable some daemons you don't need. See [HowTo: Speed up ubuntu boot process - the way you can feel it](http://www.ubuntuforums.org/showthread.php?t=89491).

---

### Post by Zmija on 2006-09-05
THNX, I'll try!

---

### Post by DrMilo on 2006-09-07
I'm a noob. Can I assume that Ubuntu will release kernel updates along with other ones? I'm all for speed but I'm also quite lazy!

---

### Post by lozenge on 2006-09-08
NTFS won't mount. Ideas?

---

### Post by tworkemon on 2006-09-08
**For those who have problems with NTFS and/or Secondary HDD mount problems.**

You might need to follow the instrunction from the original post then when you get to the "PATCHING" Section do whats bellow.

You need to patch your kernel.
```
sudo apt-get install kernel-patch-evms
```
```
sudo cp /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch.gz
```
```
/usr/src/your_kernel
```
```
sudo gzip -d 2.6-bd-claim.patch.gz
```
```
sudo cat 2.6-bd-claim.patch | patch -p1
```

After you do that rerun your kernel configuration.
```
sudo cp /boot/config-`uname -r` .config && sudo make xconfig
```

Make yourself root:
```
sudo -s -H
```

And do:
```
make-kpkg clean
```

Let her rip:
```
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
```

Install the .deb files in /usr/src. There should be 2. One should be an image .deb file and the other a header .deb file. In terminal
```
dpkg -i <name of the file>
```

Those last steps were taken from the original post.

Good Luck

---

### Post by Inhumane on 2006-09-08
Can someone please list some benefits of upgrading the current Ubuntu 6.06 Kernel to 2.6.18?

---

### Post by puppy on 2006-09-08
Hi everyone, I get the same problem as Peter does (back on about page 14 I think) but I don't see a reply - when completing Stage 4, CTRL-S and exiting the configuration tool, I find the following in the console:


HOSTCC scripts/basic/fixdep
HOSTCC scripts/basic/split-include
HOSTCC scripts/basic/docproc
CHECK qt
HOSTCC scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
HOSTCC scripts/kconfig/kconfig_load.o
HOSTCC scripts/kconfig/kxgettext.o
HOSTCC scripts/kconfig/mconf.o
SHIPPED scripts/kconfig/zconf.tab.c
SHIPPED scripts/kconfig/lex.zconf.c
SHIPPED scripts/kconfig/zconf.hash.c
HOSTCC scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
HOSTCXX scripts/kconfig/qconf.o
HOSTLD scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:53:warning: trying to assign nonexistent symbol CC_ALIGN_FUNCTIONS
.config:54:warning: trying to assign nonexistent symbol CC_ALIGN_LABELS
.config:55:warning: trying to assign nonexistent symbol CC_ALIGN_LOOPS
.config:56:warning: trying to assign nonexistent symbol CC_ALIGN_JUMPS
.config:66:warning: trying to assign nonexistent symbol OBSOLETE_MODPARM
.config:144:warning: trying to assign nonexistent symbol X86_UP_APIC_DEFAULT_OFF.config:166:warning: trying to assign nonexistent symbol 05GB
.config:167:warning: trying to assign nonexistent symbol 1GB
.config:168:warning: trying to assign nonexistent symbol 2GB
.config:169:warning: trying to assign nonexistent symbol 3GB
.config:210:warning: trying to assign nonexistent symbol ACPI_SBS
.config:220:warning: trying to assign nonexistent symbol ACPI_PCC
.config:221:warning: trying to assign nonexistent symbol ACPI_SONY
.config:229:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:230:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:231:warning: trying to assign nonexistent symbol ACPI_DEV
.config:303:warning: trying to assign nonexistent symbol PCI_LEGACY_PROC
.config:336:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:477:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:479:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:480:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:481:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:482:warning: trying to assign nonexistent symbol IP_NF_MATCH_MULTIPORT
.config:487:warning: trying to assign nonexistent symbol IP_NF_MATCH_AH_ESP
.config:488:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:490:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:491:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:492:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:493:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:495:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:497:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:498:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:499:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:500:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:501:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:502:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:504:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:510:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:527:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:528:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:530:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:533:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:543:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:544:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:549:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MULTIPORT
.config:551:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:553:warning: trying to assign nonexistent symbol IP6_NF_MATCH_AHESP
.config:554:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:556:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:560:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:562:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:611:warning: trying to assign nonexistent symbol IP_DCCP_UNLOAD_HACK
.config:830:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:831:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:832:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:833:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:896:warning: trying to assign nonexistent symbol MTD_CFI_AMDSTD_RETRY
.config:941:warning: trying to assign nonexistent symbol MTD_BLKMTD
.config:1045:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:1056:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:1077:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:1086:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1118:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1161:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1169:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1170:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1184:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1185:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1204:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1226:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1274:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1279:warning: trying to assign nonexistent symbol SCSI_QLA6312
.config:1382:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1536:warning: trying to assign nonexistent symbol R1000
.config:1559:warning: trying to assign nonexistent symbol NET_IPG
.config:1610:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1632:warning: trying to assign nonexistent symbol ADM8211
.config:1643:warning: trying to assign nonexistent symbol WLAN_NG
.config:1644:warning: trying to assign nonexistent symbol PRISM2
.config:1645:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1646:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1647:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1648:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1649:warning: trying to assign nonexistent symbol NET_ACX
.config:1650:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1651:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1659:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1660:warning: trying to assign nonexistent symbol NET_RT2600
.config:1661:warning: trying to assign nonexistent symbol NET_RT2500
.config:1662:warning: trying to assign nonexistent symbol NET_RT2400
.config:1663:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1664:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1665:warning: trying to assign nonexistent symbol IPW3945
.config:1666:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1667:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1668:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1717:warning: trying to assign nonexistent symbol VENDOR_SANGOMA
.config:1783:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1936:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1937:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1938:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1939:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1940:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1941:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1942:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1943:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1944:warning: trying to assign nonexistent symbol MISDN_DSP
.config:2023:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:2048:warning: trying to assign nonexistent symbol ECC
.config:2078:warning: trying to assign nonexistent symbol SERIAL_8250_ACPI
.config:2304:warning: trying to assign nonexistent symbol SENSORS_RTC8564
.config:2306:warning: trying to assign nonexistent symbol RTC_X1205_I2C
.config:2316:warning: trying to assign nonexistent symbol W1_MATROX
.config:2317:warning: trying to assign nonexistent symbol W1_DS9490
.config:2318:warning: trying to assign nonexistent symbol W1_DS9490_BRIDGE
.config:2319:warning: trying to assign nonexistent symbol W1_THERM
.config:2320:warning: trying to assign nonexistent symbol W1_SMEM
.config:2322:warning: trying to assign nonexistent symbol W1_DS2433_CRC
.config:2370:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2371:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2425:warning: trying to assign nonexistent symbol VIDEO_AUDIO_DECODER
.config:2426:warning: trying to assign nonexistent symbol VIDEO_DECODER
.config:2522:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2544:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2552:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2565:warning: trying to assign nonexistent symbol DXR3
.config:2566:warning: trying to assign nonexistent symbol EM8300
.config:2567:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2568:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2569:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2570:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2571:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2572:warning: trying to assign nonexistent symbol ADV717X
.config:2573:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2574:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2575:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2576:warning: trying to assign nonexistent symbol BT865
.config:2602:warning: symbol value 'm' invalid for FB_VESA
.config:2623:warning: trying to assign nonexistent symbol FB_RADEON_OLD
.config:2631:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2650:warning: trying to assign nonexistent symbol FB_IMAC
.config:2700:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2813:warning: trying to assign nonexistent symbol BT_ALSA
.config:2819:warning: trying to assign nonexistent symbol OBSOLETE_OSS_DRIVER
.config:2887:warning: trying to assign nonexistent symbol OBSOLETE_OSS_USB_DRIVER
.config:2928:warning: trying to assign nonexistent symbol USB_MTOUCH
.config:2929:warning: trying to assign nonexistent symbol USB_ITMTOUCH
.config:2930:warning: trying to assign nonexistent symbol USB_EGALAX
.config:2937:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2938:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2959:warning: trying to assign nonexistent symbol USB_QC
.config:2960:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2961:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2963:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2964:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2988:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2989:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2990:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2991:warning: trying to assign nonexistent symbol USB_RT2570
.config:3157:warning: trying to assign nonexistent symbol DAZUKO
.config:3200:warning: trying to assign nonexistent symbol RELAYFS_FS
.config:3209:warning: trying to assign nonexistent symbol ASFS_FS
.config:3210:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:3211:warning: trying to assign nonexistent symbol ASFS_RW
.config:3230:warning: trying to assign nonexistent symbol SQUASHFS
.config:3231:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:3232:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:3240:warning: trying to assign nonexistent symbol UNION_FS
.config:3287:warning: trying to assign nonexistent symbol GFS_FS
.config:3288:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:3409:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3474:warning: trying to assign nonexistent symbol CLUSTER

What have I forgotten to do :-k

---

### Post by pwlodarczak on 2006-09-08
Hi there,
I installed the latest kernel from kernel.org (2.6.17.11). Now I cannot access my ext3 partitions anymore on my 2 extra hard disks. They are both SATA disks. In disk manager clicking Enable has no effect. When I do 
sudo mount -a 
I get 
mount: /dev/sdb1 already mounted or /sdb busy
mount: /dev/sdc1 already mounted or /sdc busy
They are still in /cat/fstab but not in etc/mtab
Any ideas?
Peter

---

### Post by tworkemon on 2006-09-08
Peter, Follow this guide.. It should work for not just NTFS but for any seconday hdd mount.

> **tworkemon said:**
> **For those who have problems with NTFS and/or Secondary HDD mount problems.**

You might need to follow the instrunction from the original post then when you get to the "PATCHING" Section do whats bellow.

You need to patch your kernel.
```
sudo apt-get install kernel-patch-evms
```
```
sudo cp /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch.gz /usr/src/your_kernel
```
```
sudo gzip -d 2.6-bd-claim.patch.gz
```
```
sudo cat 2.6-bd-claim.patch | patch -p1
```

After you do that rerun your kernel configuration.
```
sudo cp /boot/config-`uname -r` .config && sudo make xconfig
```

Make yourself root:
```
sudo -s -H
```

And do:
```
make-kpkg clean
```

Let her rip:
```
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
```

Install the .deb files in /usr/src. There should be 2. One should be an image .deb file and the other a header .deb file. In terminal
```
dpkg -i <name of the file>
```

Those last steps were taken from the original post.

Good Luck

---

### Post by tworkemon on 2006-09-08
Also for those with problems with usplash. Im not sure which of the  two fixed my problems but this is what I did.

```
sudo nano /boot/grub/menu.lst
```

Edit this line.
```
kernel          /boot/vmlinuz-2.6.17.11 root=/dev/hda1 ro quiet splash 

```
Add vga=791 to the end so it looked like:
```
kernel          /boot/vmlinuz-2.6.17.11 root=/dev/hda1 ro quiet splash vga=791
```

I then did
```
sudo update-alternatives --config usplash-artwork.so

```
```
Selected 2 "/usr/lib/usplash/usplash-default.so"
```

I havent tried setting it back to 1 to see if it works or not.

Good Luck

---

### Post by thetravellor on 2006-09-09
I mostly followed your instructions, for various reasons I couldnt install qt3 and kernel-package.

Anyhow: On my Powerbook 12" (powerpc ubuntu) I have successfully compiled and installed 2.6.17.7 and too my great surprise, it works very very well.

The sound module is a bit bizarre, that the PowerMac sound module seems to have doubled the sound output.

My apple trackpad now works (almost) perfectly.

I will attach my .config (the bits that were not #'d out) and my xorg.conf

CONFIG_PPC32=y
CONFIG_PPC_MERGE=y
CONFIG_MMU=y
CONFIG_GENERIC_HARDIRQS=y
CONFIG_RWSEM_XCHGADD_ALGORITHM=y
CONFIG_GENERIC_HWEIGHT=y
CONFIG_GENERIC_CALIBRATE_DELAY=y
CONFIG_PPC=y
CONFIG_EARLY_PRINTK=y
CONFIG_GENERIC_NVRAM=y
CONFIG_SCHED_NO_NO_OMIT_FRAME_POINTER=y
CONFIG_ARCH_MAY_HAVE_PC_FDC=y
CONFIG_PPC_OF=y

CONFIG_CLASSIC32=y
CONFIG_6xx=y
CONFIG_PPC_FPU=y
CONFIG_ALTIVEC=y
CONFIG_PPC_STD_MMU=y
CONFIG_PPC_STD_MMU_32=y

CONFIG_EXPERIMENTAL=y
CONFIG_BROKEN_ON_SMP=y
CONFIG_INIT_ENV_ARG_LIMIT=32

CONFIG_LOCALVERSION=""
CONFIG_LOCALVERSION_AUTO=y
CONFIG_SWAP=y
CONFIG_SYSVIPC=y
CONFIG_POSIX_MQUEUE=y
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_SYSCTL=y
CONFIG_INITRAMFS_SOURCE=""
CONFIG_KALLSYMS=y
CONFIG_HOTPLUG=y
CONFIG_PRINTK=y
CONFIG_BUG=y
CONFIG_ELF_CORE=y
CONFIG_BASE_FULL=y
CONFIG_FUTEX=y
CONFIG_EPOLL=y
CONFIG_SHMEM=y
CONFIG_SLAB=y
CONFIG_BASE_SMALL=0

CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y
CONFIG_KMOD=y


CONFIG_IOSCHED_NOOP=y
CONFIG_IOSCHED_AS=y
CONFIG_IOSCHED_DEADLINE=y
CONFIG_IOSCHED_CFQ=y
CONFIG_DEFAULT_AS=y
CONFIG_DEFAULT_IOSCHED="anticipatory"

CONFIG_PPC_MULTIPLATFORM=y
CONFIG_PPC_PMAC=y
CONFIG_MPIC=y
CONFIG_PPC_MPC106=y
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=y
CONFIG_CPU_FREQ_STAT=y
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=y
CONFIG_CPU_FREQ_GOV_USERSPACE=y
CONFIG_CPU_FREQ_PMAC=y
CONFIG_TAU=y

CONFIG_HIGHMEM=y
CONFIG_HZ_250=y
CONFIG_HZ=250
CONFIG_PREEMPT_NONE=y
CONFIG_BINFMT_ELF=y
CONFIG_BINFMT_MISC=y
CONFIG_ARCH_ENABLE_MEMORY_HOTPLUG=y
CONFIG_ARCH_FLATMEM_ENABLE=y
CONFIG_SELECT_MEMORY_MODEL=y
CONFIG_FLATMEM_MANUAL=y
CONFIG_FLATMEM=y
CONFIG_FLAT_NODE_MEM_MAP=y
CONFIG_SPLIT_PTLOCK_CPUS=4
CONFIG_PROC_DEVICETREE=y
CONFIG_CMDLINE_BOOL=y
CONFIG_CMDLINE="console=ttyS0,9600 console=tty0 root=/dev/hda4"
CONFIG_PM=y
CONFIG_PM_LEGACY=y
CONFIG_SOFTWARE_SUSPEND=y
CONFIG_PM_STD_PARTITION=""
CONFIG_SWSUSP_ENCRYPT=y
CONFIG_SECCOMP=y
CONFIG_ISA_DMA_API=y

CONFIG_GENERIC_ISA_DMA=y
CONFIG_PPC_INDIRECT_PCI=y
CONFIG_PCI=y
CONFIG_PCI_DOMAINS=y

CONFIG_PCCARD=m
CONFIG_PCMCIA=m
CONFIG_PCMCIA_LOAD_CIS=y
CONFIG_PCMCIA_IOCTL=y
CONFIG_CARDBUS=y

CONFIG_YENTA=m
CONFIG_YENTA_O2=y
CONFIG_YENTA_RICOH=y
CONFIG_YENTA_TI=y
CONFIG_YENTA_ENE_TUNE=y
CONFIG_YENTA_TOSHIBA=y
CONFIG_PCCARD_NONSTATIC=m



CONFIG_HIGHMEM_START=0xfe000000
CONFIG_LOWMEM_SIZE=0x30000000
CONFIG_KERNEL_START=0xc0000000
CONFIG_TASK_SIZE=0x80000000
CONFIG_BOOT_LOAD=0x00800000

CONFIG_NET=y

CONFIG_PACKET=y
CONFIG_UNIX=y
CONFIG_XFRM=y
CONFIG_NET_KEY=m
CONFIG_INET=y
CONFIG_IP_MULTICAST=y
CONFIG_IP_ADVANCED_ROUTER=y
CONFIG_ASK_IP_FIB_HASH=y
CONFIG_IP_FIB_HASH=y
CONFIG_IP_MULTIPLE_TABLES=y
CONFIG_NET_IPIP=y
CONFIG_NET_IPGRE=y
CONFIG_NET_IPGRE_BROADCAST=y
CONFIG_INET_AH=m
CONFIG_INET_ESP=m
CONFIG_INET_IPCOMP=m
CONFIG_INET_XFRM_TUNNEL=m
CONFIG_INET_TUNNEL=y
CONFIG_INET_DIAG=y
CONFIG_INET_TCP_DIAG=y
CONFIG_TCP_CONG_BIC=y

CONFIG_IPV6=m
CONFIG_INET6_AH=m
CONFIG_INET6_ESP=m
CONFIG_INET6_IPCOMP=m
CONFIG_INET6_XFRM_TUNNEL=m
CONFIG_INET6_TUNNEL=m
CONFIG_IPV6_TUNNEL=m
CONFIG_NETFILTER=y

CONFIG_NETFILTER_NETLINK=m
CONFIG_NETFILTER_NETLINK_QUEUE=m
CONFIG_NETFILTER_NETLINK_LOG=m
CONFIG_NETFILTER_XTABLES=m
CONFIG_NETFILTER_XT_TARGET_CLASSIFY=m
CONFIG_NETFILTER_XT_TARGET_CONNMARK=m
CONFIG_NETFILTER_XT_TARGET_MARK=m
CONFIG_NETFILTER_XT_TARGET_NFQUEUE=m
CONFIG_NETFILTER_XT_TARGET_NOTRACK=m
CONFIG_NETFILTER_XT_MATCH_COMMENT=m
CONFIG_NETFILTER_XT_MATCH_CONNBYTES=m
CONFIG_NETFILTER_XT_MATCH_CONNMARK=m
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
CONFIG_NETFILTER_XT_MATCH_DCCP=m
CONFIG_NETFILTER_XT_MATCH_HELPER=m
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
CONFIG_NETFILTER_XT_MATCH_PKTTYPE=m
CONFIG_NETFILTER_XT_MATCH_REALM=m
CONFIG_NETFILTER_XT_MATCH_SCTP=m
CONFIG_NETFILTER_XT_MATCH_STATE=m
CONFIG_NETFILTER_XT_MATCH_STRING=m
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m

CONFIG_IP_NF_CONNTRACK=m
CONFIG_IP_NF_CT_ACCT=y
CONFIG_IP_NF_CONNTRACK_MARK=y
CONFIG_IP_NF_CONNTRACK_EVENTS=y
CONFIG_IP_NF_FTP=m
CONFIG_IP_NF_IRC=m
CONFIG_IP_NF_TFTP=m
CONFIG_IP_NF_AMANDA=m
CONFIG_IP_NF_PPTP=m
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_IPRANGE=m
CONFIG_IP_NF_MATCH_TOS=m
CONFIG_IP_NF_MATCH_RECENT=m
CONFIG_IP_NF_MATCH_ECN=m
CONFIG_IP_NF_MATCH_DSCP=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_OWNER=m
CONFIG_IP_NF_MATCH_ADDRTYPE=m
CONFIG_IP_NF_MATCH_HASHLIMIT=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_TCPMSS=m
CONFIG_IP_NF_NAT=m
CONFIG_IP_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
CONFIG_IP_NF_TARGET_NETMAP=m
CONFIG_IP_NF_TARGET_SAME=m
CONFIG_IP_NF_NAT_IRC=m
CONFIG_IP_NF_NAT_FTP=m
CONFIG_IP_NF_NAT_TFTP=m
CONFIG_IP_NF_NAT_AMANDA=m
CONFIG_IP_NF_NAT_PPTP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_TOS=m
CONFIG_IP_NF_TARGET_ECN=m
CONFIG_IP_NF_TARGET_DSCP=m
CONFIG_IP_NF_TARGET_TTL=m
CONFIG_IP_NF_RAW=m
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
CONFIG_IP_NF_ARP_MANGLE=m

CONFIG_IP6_NF_IPTABLES=m
CONFIG_IP6_NF_MATCH_RT=m
CONFIG_IP6_NF_MATCH_OPTS=m
CONFIG_IP6_NF_MATCH_FRAG=m
CONFIG_IP6_NF_MATCH_HL=m
CONFIG_IP6_NF_MATCH_OWNER=m
CONFIG_IP6_NF_MATCH_IPV6HEADER=m
CONFIG_IP6_NF_MATCH_EUI64=m
CONFIG_IP6_NF_FILTER=m
CONFIG_IP6_NF_TARGET_LOG=m
CONFIG_IP6_NF_TARGET_REJECT=m
CONFIG_IP6_NF_MANGLE=m
CONFIG_IP6_NF_TARGET_HL=m
CONFIG_IP6_NF_RAW=m




CONFIG_NET_CLS_ROUTE=y

CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT_WEP=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IEEE80211_SOFTMAC=m
CONFIG_WIRELESS_EXT=y


CONFIG_FW_LOADER=y





CONFIG_BLK_DEV_LOOP=y
CONFIG_BLK_DEV_CRYPTOLOOP=y
CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=4096
CONFIG_BLK_DEV_INITRD=y

CONFIG_IDE=y
CONFIG_BLK_DEV_IDE=y

CONFIG_BLK_DEV_IDEDISK=y
CONFIG_BLK_DEV_IDECD=y

CONFIG_IDE_GENERIC=y
CONFIG_BLK_DEV_IDEPCI=y
CONFIG_BLK_DEV_GENERIC=y
CONFIG_BLK_DEV_IDEDMA_PCI=y
CONFIG_IDEDMA_PCI_AUTO=y
CONFIG_BLK_DEV_IDE_PMAC=y
CONFIG_BLK_DEV_IDE_PMAC_ATA100FIRST=y
CONFIG_BLK_DEV_IDEDMA_PMAC=y
CONFIG_BLK_DEV_IDE_PMAC_BLINK=y
CONFIG_BLK_DEV_IDEDMA=y
CONFIG_IDEDMA_AUTO=y

CONFIG_SCSI=y
CONFIG_SCSI_PROC_FS=y

CONFIG_BLK_DEV_SD=y
CONFIG_BLK_DEV_SR=y
CONFIG_CHR_DEV_SG=y







CONFIG_IEEE1394=m

CONFIG_IEEE1394_EXTRA_CONFIG_ROMS=y

CONFIG_IEEE1394_PCILYNX=m
CONFIG_IEEE1394_OHCI1394=m

CONFIG_IEEE1394_VIDEO1394=m
CONFIG_IEEE1394_SBP2=m
CONFIG_IEEE1394_DV1394=m
CONFIG_IEEE1394_RAWIO=m


CONFIG_ADB=y
CONFIG_ADB_CUDA=y
CONFIG_ADB_PMU=y
CONFIG_PMAC_APM_EMU=y
CONFIG_PMAC_MEDIABAY=y
CONFIG_PMAC_BACKLIGHT=y
CONFIG_INPUT_ADBHID=y
CONFIG_MAC_EMUMOUSEBTN=y
CONFIG_THERM_ADT746X=y
CONFIG_WINDFARM=y
CONFIG_ANSLCD=y

CONFIG_NETDEVICES=y
CONFIG_DUMMY=y


CONFIG_PHYLIB=y


CONFIG_NET_ETHERNET=y
CONFIG_BMAC=y
CONFIG_SUNGEM=y





CONFIG_NET_RADIO=y





CONFIG_PRISM54=m
CONFIG_HOSTAP=m
CONFIG_HOSTAP_FIRMWARE=y
CONFIG_HOSTAP_CS=m
CONFIG_BCM43XX=m
CONFIG_BCM43XX_DEBUG=y
CONFIG_BCM43XX_DMA=y
CONFIG_BCM43XX_PIO=y
CONFIG_BCM43XX_DMA_AND_PIO_MODE=y
CONFIG_NET_WIRELESS=y

CONFIG_NET_PCMCIA=y
CONFIG_PCMCIA_XIRC2PS=m

CONFIG_PPP=y
CONFIG_PPP_FILTER=y
CONFIG_PPP_ASYNC=y
CONFIG_PPP_SYNC_TTY=y
CONFIG_PPP_DEFLATE=y
CONFIG_PPP_BSDCOMP=y
CONFIG_SLIP=y
CONFIG_SLIP_COMPRESSED=y
CONFIG_SLIP_SMART=y
CONFIG_SLIP_MODE_SLIP6=y



CONFIG_INPUT=y

CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
CONFIG_INPUT_EVDEV=y

CONFIG_INPUT_KEYBOARD=y
CONFIG_KEYBOARD_ATKBD=y
CONFIG_INPUT_MOUSE=y
CONFIG_MOUSE_PS2=y

CONFIG_SERIO=y
CONFIG_SERIO_I8042=y
CONFIG_SERIO_SERPORT=y
CONFIG_SERIO_LIBPS2=y

CONFIG_VT=y
CONFIG_VT_CONSOLE=y
CONFIG_HW_CONSOLE=y


CONFIG_UNIX98_PTYS=y
CONFIG_LEGACY_PTYS=y
CONFIG_LEGACY_PTY_COUNT=256


CONFIG_NVRAM=y
CONFIG_GEN_RTC=y

CONFIG_AGP=y
CONFIG_AGP_UNINORTH=y
CONFIG_DRM=y
CONFIG_DRM_RADEON=y



CONFIG_I2C=y
CONFIG_I2C_CHARDEV=y

CONFIG_I2C_ALGOBIT=y

CONFIG_I2C_POWERMAC=y




CONFIG_HWMON=y


CONFIG_VIDEO_V4L2=y


CONFIG_FB=y
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
CONFIG_FB_MACMODES=y
CONFIG_FB_FIRMWARE_EDID=y
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_OF=y
CONFIG_FB_CONTROL=y
CONFIG_FB_PLATINUM=y
CONFIG_FB_VALKYRIE=y
CONFIG_FB_VGA16=y
CONFIG_FB_NVIDIA=y
CONFIG_FB_RADEON=y
CONFIG_FB_RADEON_I2C=y

CONFIG_VGA_CONSOLE=y
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=y
CONFIG_FONTS=y
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y
CONFIG_FONT_6x11=y
CONFIG_FONT_7x14=y
CONFIG_FONT_PEARL_8x8=y
CONFIG_FONT_ACORN_8x8=y
CONFIG_FONT_MINI_4x6=y
CONFIG_FONT_SUN8x16=y
CONFIG_FONT_10x18=y

CONFIG_LOGO=y
CONFIG_LOGO_LINUX_MONO=y
CONFIG_LOGO_LINUX_VGA16=y
CONFIG_LOGO_LINUX_CLUT224=y
CONFIG_BACKLIGHT_LCD_SUPPORT=y
CONFIG_BACKLIGHT_CLASS_DEVICE=y
CONFIG_BACKLIGHT_DEVICE=y
CONFIG_LCD_CLASS_DEVICE=y
CONFIG_LCD_DEVICE=y

CONFIG_SOUND=m

CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=m
CONFIG_SND_PCM_OSS=m
CONFIG_SND_PCM_OSS_PLUGINS=y
CONFIG_SND_SEQUENCER_OSS=y
CONFIG_SND_SUPPORT_OLD_API=y
CONFIG_SND_VERBOSE_PROCFS=y



CONFIG_SND_POWERMAC=m
CONFIG_SND_POWERMAC_AUTO_DRC=y




CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB_ARCH_HAS_EHCI=y
CONFIG_USB=y

CONFIG_USB_DEVICEFS=y

CONFIG_USB_EHCI_HCD=y
CONFIG_USB_OHCI_HCD=y
CONFIG_USB_OHCI_LITTLE_ENDIAN=y

CONFIG_USB_ACM=y
CONFIG_USB_PRINTER=y


CONFIG_USB_STORAGE=y

CONFIG_USB_HID=y
CONFIG_USB_HIDINPUT=y
CONFIG_USB_HIDINPUT_POWERBOOK=y
CONFIG_USB_APPLETOUCH=y


CONFIG_USB_MON=y













CONFIG_EXT2_FS=y
CONFIG_EXT3_FS=y
CONFIG_EXT3_FS_XATTR=y
CONFIG_JBD=y
CONFIG_FS_MBCACHE=y
CONFIG_ROMFS_FS=y
CONFIG_INOTIFY=y
CONFIG_DNOTIFY=y
CONFIG_AUTOFS_FS=y
CONFIG_AUTOFS4_FS=y

CONFIG_ISO9660_FS=y
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_ZISOFS_FS=y
CONFIG_UDF_FS=y
CONFIG_UDF_NLS=y

CONFIG_FAT_FS=y
CONFIG_MSDOS_FS=y
CONFIG_VFAT_FS=y
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="iso8859-1"
CONFIG_NTFS_FS=y
CONFIG_NTFS_RW=y

CONFIG_PROC_FS=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_RAMFS=y

CONFIG_HFSPLUS_FS=y

CONFIG_SMB_FS=y
CONFIG_CIFS=y

CONFIG_PARTITION_ADVANCED=y
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y

CONFIG_NLS=y
CONFIG_NLS_DEFAULT="iso8859-1"
CONFIG_NLS_CODEPAGE_437=y
CONFIG_NLS_CODEPAGE_737=m
CONFIG_NLS_CODEPAGE_775=m
CONFIG_NLS_CODEPAGE_850=m
CONFIG_NLS_CODEPAGE_852=m
CONFIG_NLS_CODEPAGE_855=m
CONFIG_NLS_CODEPAGE_857=m
CONFIG_NLS_CODEPAGE_860=m
CONFIG_NLS_CODEPAGE_861=m
CONFIG_NLS_CODEPAGE_862=m
CONFIG_NLS_CODEPAGE_863=m
CONFIG_NLS_CODEPAGE_864=m
CONFIG_NLS_CODEPAGE_865=m
CONFIG_NLS_CODEPAGE_866=m
CONFIG_NLS_CODEPAGE_869=m
CONFIG_NLS_CODEPAGE_936=m
CONFIG_NLS_CODEPAGE_950=m
CONFIG_NLS_CODEPAGE_932=m
CONFIG_NLS_CODEPAGE_949=m
CONFIG_NLS_CODEPAGE_874=m
CONFIG_NLS_ISO8859_8=m
CONFIG_NLS_CODEPAGE_1250=m
CONFIG_NLS_CODEPAGE_1251=m
CONFIG_NLS_ASCII=m
CONFIG_NLS_ISO8859_1=y
CONFIG_NLS_ISO8859_2=m
CONFIG_NLS_ISO8859_3=m
CONFIG_NLS_ISO8859_4=m
CONFIG_NLS_ISO8859_5=m
CONFIG_NLS_ISO8859_6=m
CONFIG_NLS_ISO8859_7=m
CONFIG_NLS_ISO8859_9=m
CONFIG_NLS_ISO8859_13=m
CONFIG_NLS_ISO8859_14=m
CONFIG_NLS_ISO8859_15=y
CONFIG_NLS_KOI8_R=m
CONFIG_NLS_KOI8_U=m
CONFIG_NLS_UTF8=y

CONFIG_CRC_CCITT=y
CONFIG_CRC32=y
CONFIG_ZLIB_INFLATE=y
CONFIG_ZLIB_DEFLATE=y
CONFIG_TEXTSEARCH=y
CONFIG_TEXTSEARCH_KMP=m
CONFIG_TEXTSEARCH_BM=m
CONFIG_TEXTSEARCH_FSM=m


CONFIG_LOG_BUF_SHIFT=14


CONFIG_CRYPTO=y
CONFIG_CRYPTO_HMAC=y
CONFIG_CRYPTO_NULL=y
CONFIG_CRYPTO_MD4=y
CONFIG_CRYPTO_MD5=y
CONFIG_CRYPTO_SHA1=y
CONFIG_CRYPTO_SHA256=y
CONFIG_CRYPTO_TGR192=y
CONFIG_CRYPTO_DES=y
CONFIG_CRYPTO_BLOWFISH=y
CONFIG_CRYPTO_TWOFISH=y
CONFIG_CRYPTO_SERPENT=y
CONFIG_CRYPTO_AES=y
CONFIG_CRYPTO_ARC4=y
CONFIG_CRYPTO_DEFLATE=y
CONFIG_CRYPTO_MICHAEL_MIC=y

---

### Post by pwlodarczak on 2006-09-09
> **tworkemon said:**
> Peter, Follow this guide.. It should work for not just NTFS but for any seconday hdd mount.

Yes, it worked, thanx a bunch.
Peter

---

### Post by starscalling on 2006-09-10
> **hanzomon4 said:**
> I got it to :-D  work. 
This is what I did

First I got the nvidia-kernel-source:
```
apt-get install nvidia-kernel-source
```
Next I cd to /usr/src/:
```
cd /usr/src/
```
Then I untared the nvidia-kernel-source:
```
 sudo tar -zxvf nvidia-kernel-source.tar.gz
```
Next I rebooted into the new kernel (2.6.17) logged in via the CLI and cd:
```
 cd /usr/src/modules/nvidia-kernel/nv/
```
read the README (cat README)for the last instructions
```
sudo make module
```
and 
```
sudo make install
```
and last 
```
sudo /etc/init.d/gdm restart
```
X started and I lived happily ever after.  ;)


hey good looking out! works like a charm :D
nekostar@dapper-xp:~$ uname -a
Linux dapper-xp 2.6.17.13 #1 Sun Sep 10 04:27:22 PDT 2006 i686 GNU/Linux

---

### Post by Jengist on 2006-09-10
I compiled 2.6.17.13. However, when booting, it displays "Kernel panic - not syncing: Unable to mount root FS on unknown-block(0,0)"

I found a report of the same error for an old Breezy installation where the fix was to install initrd-tools but that hasn't done anything for me either. My old kernel still works but I'd like to get the new one working as I put a lot of time into configuring it.

---

### Post by Razer(x) on 2006-09-12
i have this problem...when i try to compile the kernel

drivers/media/dvb/ttpci/budget-av.c: In function &#8216;frontend_init&#8217;:
drivers/media/dvb/ttpci/budget-av.c:1063: error: &#8216;struct budget_av&#8217; has no membe r named &#8216;reinitialise_demod&#8217;
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member &#8216;tuner_ops&#8217; in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: &#8216;philips_cu1216_tuner_set_param s&#8217; undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in .)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

---

### Post by Jengist on 2006-09-12
Did you read this post which has been referenced in the HOWTO and several times throughout the thread?
[http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106](http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106)

Anyway, as for my kernel panic problem, I was told on ##kernel the fix was almost certainly to have both the FS type I'm booting from and the chipset built in and not made as modules. I'm still getting the same error though so any ideas?

---

### Post by Razer(x) on 2006-09-12
thanx a lot

---

### Post by patrickfromspain on 2006-09-13
I've come across this tutorial but I don't like it much, sorry. The problem with the nvida and ati drivers, as well as ndiswrapper and some others (rt2500 cards for example, whose driver is in dapper kernel but not in the kernel.org one) would be easy solvable by installing ndiswrapper-source, nvidia-kernel-source, rt2500-source, fglrx-kernel-source and maybe there are more things.

After installing those with either synaptic or apt-get you can do gksudo nautilus /usr/src and unpack them. At the end, you should have a folder called modules, and inside that folder things like ndiswrapper-source, nvidia-source or whatever you need.

Then it should be fine and you shouldn't need to edit /etc/modules nor compile ndiswrapper from source.

Credit goes to Tseliot ([http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper))

---

### Post by smokinblues on 2006-09-13
> **KingArthur10 said:**
> Well, I attempted my first kernal compile.  Got through the whole thing with only one major hitch: my IPW 2200 card isn't working right now.  Graphics wasn't right, either, but I hadn't reinstalled my graphics card, but w/o networking, there was no point.  I made sure to checkmark the 2200 and 2100 cards in the wireless section, but still no luck.  Any ideas?

I had this same problem with my ipw2100.

If you are using dapper, the Firmware is already installed. It's just in the dapper kernel directory. Try this:

sudo cp /lib/firmware/2.6.15-23-386/ipw* /lib/firmware
then reboot

---

### Post by speedway on 2006-09-19
Howdy all

I just completed a compile of 2.6.17.13 as per this HowTo and tried to install the resulting .deb file. But I get these errors:

> 
root@mythmaster:/usr/src# dpkg -i kernel-image-2.6.17.13_686_i386.deb
(Reading database ... 85956 files and directories currently installed.)
Preparing to replace kernel-image-2.6.17.13 686 (using kernel-image-2.6.17.13_686_i386.deb) ...
Unpacking replacement kernel-image-2.6.17.13 ...
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17.13
Found kernel: /boot/vmlinuz-2.6.15-27-686
Found kernel: /boot/vmlinuz-2.6.15-26-686
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up kernel-image-2.6.17.13 (686) ...
Cannot find /lib/modules/2.6.17.13
Failed to create initrd image.
dpkg: error processing kernel-image-2.6.17.13 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 kernel-image-2.6.17.13


I looked in /lib/modules and there is a directory for 2.6.17.13-686 but not 2.6.17.13. So I symlinked the -686 dir to plain 2.6.17.13 but then the installer complained about it:

> 
root@mythmaster:/usr/src# dpkg -i kernel-image-2.6.17.13_686_i386.deb
(Reading database ... 85956 files and directories currently installed.)
Preparing to replace kernel-image-2.6.17.13 686 (using kernel-image-2.6.17.13_686_i386.deb) ...
You are attempting to install a kernel image (version 2.6.17.13)
However, the directory /lib/modules/2.6.17.13 still exists.  If this
directory belongs to a previous kernel-image-2.6.17.13 package, and if
you have deselected some modules, or installed standalone modules
packages, this could be bad. However, if this directory exists because
you are also installing some stand alone modules right now, and they
got unpacked before I did, then this is pretty benign.  Unfortunately,
I can not tell the difference.

If /lib/modules/2.6.17.13 belongs to a old install of
kernel-image-2.6.17.13, then this is your last chance to abort the
installation of this kernel image (nothing has been changed yet).

If this directory is because of stand alone modules being installed
right now, or if it does belong to an older kernel-image-2.6.17.13
package but you know what you are doing, and if you feel that this
image should be installed despite this anomaly, Please answer n to the
question.

Otherwise, I suggest you move /lib/modules/2.6.17.13 out of the way,
perhaps to /lib/modules/2.6.17.13.old or something, and then try
re-installing this image.
Do you want to stop now? [Y/n]


Any suggestions on how to fix this?

Thanks in advance

Cheers
Bruce

---

### Post by dshuck on 2006-09-21
These instructions count on being able to use X for using the GUI to adjust the configuration of the Kernel.  Is there a way to acheive the same results SSH'd into an Ubuntu Server?  Thanks!

---

### Post by veli on 2006-09-21
What about the latest kernel 2.6.18. Can I follow the same procedure described here? Thanks,

---

### Post by danderson3 on 2006-09-21
> **dshuck said:**
> These instructions count on being able to use X for using the GUI to adjust the configuration of the Kernel.  Is there a way to acheive the same results SSH'd into an Ubuntu Server?  Thanks!
use make menuconfig  instead of make xconfig

---

### Post by orangek3nny on 2006-09-21
@speedway:
Did you try to type sudo in front of your line? :)

@veli:
Well, I'm compiling it right now...I'll report my results tomorrow

---

### Post by Chickencha on 2006-09-21
> **veli said:**
> What about the latest kernel 2.6.18. Can I follow the same procedure described here? Thanks,

I compiled 2.6.18 by following this guide.  I'm running it right now and I haven't come across any problems so far.

---

### Post by veli on 2006-09-21
thanks a lot, I'll try it too.

---

### Post by orangek3nny on 2006-09-22
I also compiled it without problems.
Though there was a problem with flgrx and networkmanager-gnome 0.7 behaves weird...I suppose I just need to reinstall both

---

### Post by veli on 2006-09-22
I compiled 2.6.18 following the instructions. It works just fine, for the time being, :-)

It seems that all tweaks we did in 2.6.17 kernels, now are defaults, like CFQ scheduller, i.e.

---

### Post by orangek3nny on 2006-09-22
> 
k3nny@workstation-ubuntu:/usr/src$ sudo module-assistant prepare
Getting source for kernel version: 2.6.18
apt-get install linux-headers-2.6.18
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.18

Done!



Thats what I get when I wanted to build fglrx..

I DID install "kernel-headers-2.6.18_386_i386.deb"



Whats the problem? :/

---

### Post by Chickencha on 2006-09-22
I've been having the same problem.  I've tried a few solutions, but none have worked so far.

This is the first kernel I've compiled myself, so I kind of don't know what I'm doing.  It seems like kernel-headers-2.6.18 is the same thing as linux-headers-2.6.18.  That's what it looks like to me when I compare the directory structures for the kernel-headers-2.6.18 directory to my old linux-headers directory.   I could be wrong, though.

I've tried compiling fglrx anyway, specifying the directory /usr/src/kernel-headers-2.6.18 as the linux-headers 2.6.18 directory and I get a little further, but then I get some kind of permission denied error when executing sh?  (And yes, I'm using sudo.)  So I don't know what the problem is.

Anyone have any ideas?

---

### Post by orangek3nny on 2006-09-22
If you have time, you could try to integrate fglrx directly in your kernel before compiling...I will also try that tomorrow
Btw...there is also a possibility for patching that kernel to get better performance

[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper#HOWTO_Compile_kernel_with_the_latest_ATI_driver](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper#HOWTO_Compile_kernel_with_the_latest_ATI_driver)

---

### Post by tworkemon on 2006-09-23
You need to backport or install the latest module-assistant from edgy. The current version will not work with the 2.6.18 kernel.

---

### Post by neXenta on 2006-09-24
Hello all,

I have upgraded my kernel to 2.6.18 following the steps involved in the upper tutorial. Unfortunatelly it appears that i haven't included the support for iptables (Net filter Xtables so on) and after a quck search for alternatives (if any) i will recompile again the kernel with the Xtables support included. So, I rebooted into the older kernel 2.6.15-27-server and I will start again from the beginning. My question is as following: I read that the things are a little bit different from the first time compiling (now that I'm doing the second time).Should I follow the same steps from the tutorial? I noticed that I don't need to download again the 2.6.18 kernel from kernel.org because I allready have it from prev. upgrade. Is that another way to solve the iptables missing module from kernel avoiding the a new compile?

Thank you in advance,

---

### Post by neXenta on 2006-09-24
Sorry, I forgot to tell you that I followed the tutorial fot kernel 2.6.18 replaceing in the command line the credential for the 2.6.18 kernel.

Thx again!

---

### Post by termite on 2006-09-24
No, you have to recompile.  I did something silly yesterday when I compiled the new 2.6.18 too and had to do it all over.

Oh well, another couple of hours of watching meaningless text scroll down the screen while drinking lots of tea...

---

### Post by moore.bryan on 2006-09-25
*i've compiled the 2.6.18 kernel three times and all three times iptables won't work even though i have expressly permitted it in the qconf... any ideas?*

---

### Post by tworkemon on 2006-09-25
author Al Viro <viro@ftp.linux.org.uk> Sun, 24 Sep 2006 23:42:20 +0100 
committer Linus Torvalds <torvalds@g5.osdl.org> Sun, 24 Sep 2006 15:55:03 -0700 

    [PATCH] fix iptables __user misannotations


iptables are still being worked on in 2.6.18

---

### Post by moore.bryan on 2006-09-25
*so, would the suggestion be 2.6.17.13?*

---

### Post by GaryH on 2006-09-25
This "how to" worked just fine on my T20. 
Thank you!

---

### Post by moore.bryan on 2006-09-25
*i've compiled both the 2.6.18 and 2.6.17.13 kernels, made sure to enable iptables in theqconf, and neither allow iptables to run... what's the deal?*

---

### Post by bastupungen on 2006-09-25
I just have to says this really fast:
:start rant:
ARGH! Why put something so basic as IPTABLES support buried deep in 3-4 layers of commands. IT DOES NOT MAKE SENSE.

For some reason our dear kernel coders have lost their minds.

:Stop rant:

Anyways, thanks for the great guide. If you would have a section about adding IPTABLES to the guide it would be brilliant.

PS.
And just for reference, this is what i talk about:
Networking --->
     Networking options --->
          [*] Network packet filtering (replaces ipchains) --->
               Core Netfilter Configuration --->
                    <*> Netfilter Xtables support (!!!!required for ip_tables!!!!!)

Note the MANY exclamation marks. May help some of you others out there with the same problem
Ds.

---

### Post by bastupungen on 2006-09-26
Oh!
I noticed that i also needed to add another parameter to get iptables up and running. It was located under:
Networking --->
Networking options --->[*] Network packet filtering (replaces ipchains) ---> IP: Net Filter configuration ---> IP Tables Support.

I checked everything in there and now it works. So i don't know if you need everything in there but i guess it can't hurt.

---

### Post by hikaricore on 2006-09-27
Yea.... I'm just now compiling 2.6.18 WITH ip tables support, thanks for the tip :)

And remember kids if you use EVMS don't expect it to work "properly" from a source build, remember to patch.

[http://evms.sourceforge.net/install/kernel.html](http://evms.sourceforge.net/install/kernel.html)

I've learned this the hard way after compiling 3 different kernels over a long period of time... *sighs* each time span between kernels was long enough to let me forget I had to do this myself last time.  :P

---

### Post by smbm on 2006-09-28
Can anyone tell me how to get automounting of dvds ipods etc working again with my custom kernel. I've done a search of the forums but it did not come back with anything conclusive.

Thanks

---

### Post by moore.bryan on 2006-09-28
*are you sure it has to do with the new kernel, not a service being forgotten (e.g. gnome-volume-manager)?*

---

### Post by danderson3 on 2006-09-28
check out supermount at sourceforge

---

### Post by smbm on 2006-09-28
Gnome-volume-manager, hal and udev are all running. Just can't seem to get gvm to mount anything that hal sees. If I boot into the old kernel everything is working again. Bizarre. Any ideas?

---

### Post by moore.bryan on 2006-09-29
> **smbm said:**
> Gnome-volume-manager, hal and udev are all running. Just can't seem to get gvm to mount anything that hal sees. If I boot into the old kernel everything is working again. Bizarre. Any ideas?
*that is bizarre because i just noticed the same thing running 2.6.18... it won't mount my ipod... i guess there could have been a setting missed in kernel config...*

---

### Post by depu on 2006-09-29
I seem to have the same problem... i have my ntfs drives with all my music in them and i am not able to mount them it keeps saying that the disk(/dev/hda1) or the mount location is busy..
This is probably the third time that i had recompiled the 2.16.18kernel.

I removed the entries from the fstab and tried to mount them thru the command line but still no use....

I can still access them thru my old k7 kernel tho....
Any idea what could have possibly gone wrong?

---

### Post by moore.bryan on 2006-09-29
> **depu said:**
> I seem to have the same problem... i have my ntfs drives with all my music in them and i am not able to mount them it keeps saying that the disk(/dev/hda1) or the mount location is busy..
This is probably the third time that i had recompiled the 2.16.18kernel.

I removed the entries from the fstab and tried to mount them thru the command line but still no use....

I can still access them thru my old k7 kernel tho....
Any idea what could have possibly gone wrong?
*when you compiled, are you sure you enabled ntfs support in the config?*
*if so, i've got nothing...*

---

### Post by depu on 2006-09-29
> **moore.bryan said:**
> *when you compiled, are you sure you enabled ntfs support in the config?*
*if so, i've got nothing...*

yes i had done that..
went as far as installing the ntfsprogs as well (no reason actually just in case that helps)

---

### Post by mlind on 2006-09-29
> **depu said:**
> I seem to have the same problem... i have my ntfs drives with all my music in them and i am not able to mount them it keeps saying that the disk(/dev/hda1) or the mount location is busy..
This is probably the third time that i had recompiled the 2.16.18kernel.

I removed the entries from the fstab and tried to mount them thru the command line but still no use....

I can still access them thru my old k7 kernel tho....
Any idea what could have possibly gone wrong?

Search this thread few pages back and look for evms patch (bd-claim patch).
Apply this patch before compiling the kernel.

---

### Post by smbm on 2006-09-29
Does anyone know what Ubuntu does when you plug in a new device to try and automount it? I've tried everything I can think of but there doesn't seem to be much documentation on the matter. HAL definetely can see the ipod because it appeared in device manager. I can mount it manually too. Just no automount.

---

### Post by mlind on 2006-09-29
> **smbm said:**
> Does anyone know what Ubuntu does when you plug in a new device to try and automount it? I've tried everything I can think of but there doesn't seem to be much documentation on the matter. HAL definetely can see the ipod because it appeared in device manager. I can mount it manually too. Just no automount.

I think mounting is done by udev and there's a rule hidden somewhere in
/etc/udev/rules.d/. Try adding yourself to **plugdev** group and see if automounting works then.

```

sudo adduser *user* *group*

```

---

### Post by hikaricore on 2006-09-29
> **depu said:**
> I seem to have the same problem... i have my ntfs drives with all my music in them and i am not able to mount them it keeps saying that the disk(/dev/hda1) or the mount location is busy..
This is probably the third time that i had recompiled the 2.16.18kernel.

I removed the entries from the fstab and tried to mount them thru the command line but still no use....

I can still access them thru my old k7 kernel tho....
Any idea what could have possibly gone wrong?

yup i just mentioned this about 5 posts prior to yours :P

evms patch pwns you

---

### Post by Charles Hand on 2006-09-30
It made a ieee80211softmac module, but not an ieee80211 module.

Why would it not make the module and not generate an error?


```
$ grep -i ieee80211 .config
CONFIG_IEEE80211=y
# CONFIG_IEEE80211_DEBUG is not set
CONFIG_IEEE80211_CRYPT_WEP=y
CONFIG_IEEE80211_CRYPT_CCMP=y
CONFIG_IEEE80211_CRYPT_TKIP=y
CONFIG_IEEE80211_SOFTMAC=y
# CONFIG_IEEE80211_SOFTMAC_DEBUG is not set

```

---

### Post by depu on 2006-09-30
> **hikaricore said:**
> yup i just mentioned this about 5 posts prior to yours :P

evms patch pwns you

true :) ... just got rid of evms tho.. hopefully it wont cause any side effects
Thanks for the help all...

---

### Post by ijjz on 2006-10-02
Great guide, worked very well, thanks.

---

### Post by mikedep333 on 2006-10-02
I need to put kernel 2.6.18 on my system, but I am in a difficult situation.
[http://www.ubuntuforums.org/showthread.php?p=1541443#post1541443](http://www.ubuntuforums.org/showthread.php?p=1541443#post1541443)

Would I be able to install the new kernel from the live CD? I believe that is how other people have been able to get ubuntu to work on new hardware like mine.

---

### Post by TSP on 2006-10-04
Hi i need to compile a new kernel but i can't i try every day without luck only one time and with linux-source 2.6.15 from ubuntu repos i did it.
I always have diferents error. This time for example i get
```
  CC      drivers/pci/access.o
En el fichero incluído de <línea de orden>:1:
./include/linux/autoconf.h:302:2: error: directiva de preprocesamiento #defi inválida
make[3]: *** [drivers/pci/access.o] Error 1
make[2]: *** [drivers/pci] Error 2
make[1]: *** [drivers] Error 2
make[1]: se sale del directorio `/usr/src/linux-2.6.18'
make: *** [stamp-build] Error 2

```

I always try to make cahnges in the config but i can't compile my kernel, can someone please help me out with this?

Cheers!

---

### Post by prince_niceguy on 2006-10-09
worked like a charm without any issues :D 

thanks you...

---

### Post by GaryH on 2006-10-09
Worked like a charm except except for one multi-demensional issue. The 2.6.17 linux-restricted-modules folder wasn't created and consequently my modem no longer works. My modem relies on ltserial and ltmodem which would have been in the non-created folder.

What did I do wrong or what did I forget?

Thank you,
GaryH

---

### Post by chrisccoulson on 2006-10-11
I have tried compiling 2.6.18 as per these instructions for use on my amd64 Dapper machine. Unfortunately, the boot process hangs at 'Mounting root filesystem'. If I remove the quiet and splash kernel boot options, it seems that it cannot find /dev/mapper/nvidia_dgcadeeg6, which is my root filesystem.

After this, it just seems to pause.

Is there any way I can find out what (if any) device nodes are being allocated for my root filesystem with this kernel?

I also had this problem when compiling 2.6.17 from kernel.org.

---

### Post by nariusb on 2006-10-11
I've got to the 4th line and compiling stops with error:

root@narius-desktop:/usr/src/linux# sudo cp /boot/config-`uname -r` .config && sudo make xconfig
/usr/src/linux-2.6.18/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-2.6.18/scripts/gcc-version.sh: line 12: gcc: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2

I'm a beginner, so please help if you find a minute.
Thanks

---

### Post by nariusb on 2006-10-11
Could it be because of budget drivers as per:
[http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106](http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106)

It states to do:
Simply unset the following (change from module to nothing)
Device Drivers -> Multimedia Devices -> Digital Broadcasting Devices -> 

How do do that? If I supposto edit come config file - where do I look for it?
Thanks

---

### Post by nariusb on 2006-10-12
I figured it out. All it needed is apt-get install gcc-3.4.

I had gcc but not gcc3.4.
It compiled to 6.2.18 with no problems after that just over an hour.


> **nariusb said:**
> Could it be because of budget drivers as per:
[http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106](http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106)

It states to do:
Simply unset the following (change from module to nothing)
Device Drivers -> Multimedia Devices -> Digital Broadcasting Devices -> 

How do do that? If I supposto edit come config file - where do I look for it?
Thanks

---

### Post by PriceChild on 2006-10-12
I've changed the name of this thread to .18

---

### Post by Didjit on 2006-10-13
I had this problem w/Edgy's kernel too. Seeing the following errors in the syslog.

...irq 7: nobody cared (try booting with the "irqpoll" option)
.....
...Disabling IRQ #7

Should I be concerned? BTW, only way the kernel boots is w/"noapic" option.

Any help explaining this would be great.
Tx
Didjit

---

### Post by ciscosurfer on 2006-10-14
Does anyone know of a program that can summarily analyze my computer (spec out the hardware, etc.), then offer me a report of which options to set (or, ideally, set them for me) from within q*somethingorother (the kernel config program that got loaded after I typed in*** sudo cp /boot/config-`uname -r` .config && sudo make xconfig **[I]which I'm assuming was loaded via **make xconfig**.)

[/I] I understand the desire for uber-geeks wanting to tweak out their kernels to get them just the way they want them (hence, the nifty GUI tool to which I just referred), but I'd like to know if this process can in any way be shortened via a program that can offer me suggestions or recommendations on which options to set, modules to enable, flags to pull, etc., based on my hardware-setup.  Any comments are most welcome and quite desired.  

Btw, I'm compiling my first kernel as we speak, 2.6.18...I'll report back after I see how it goes.  I Just need to remember to reinstall my graphics drivers before I reboot.  Hopefully everything will work just peachy.  Stay tuned.  In the meantime, does anyone have  any thoughts on my question(s)?

---

### Post by Didjit on 2006-10-16
Anyone come across funky sound issues running 2.6.18? 

Every now and then, I get an event sound that goes in an infinite loop (constantly playing through my speakers). Then my system starts to get unresponsive. Reboot is the only way to clear it up.

This is a new PC w/on-board sound. I believe it still uses the Alsa drivers.

Tx

Didijt[FONT=Arial][/FONT]

---

### Post by GregaS on 2006-10-17
When I compile kernel 2.6.18, internet doesn't work anymore. Anyone has any ideas why?

---

### Post by hikaricore on 2006-10-17
> **GregaS said:**
> When I compile kernel 2.6.18, internet doesn't work anymore. Anyone has any ideas why?

did you make sure you compiled with network support?

you also might want to check

```
ifconfig eth0
```
(replace eth0 with the device name of your network device if needed)

you should see something like this

> [hikaricore@hikaricore:/media/devistate (2658.5 Mb)]$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:40:2B:70:D0:D8
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:2bff:fe70:d0d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2444589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2787649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1172836928 (1.0 GiB)  TX bytes:1960304183 (1.8 GiB)
          Interrupt:209 Base address:0xe000


make sure you have a valid ip address in your ISP's block if you are connecting directly to a cable modem.  If you use a router you'll see a variation of the 192.168.*.* address like mine is.  Also if you have a router check to see if you can ping it:

```
ping 192.168.1.1
```
(or your router's main ip address)

then if you know it has a webbased configuration menu see if you can access  it

[http://192.168.1.1](http://192.168.1.1)

if you can connect to your router or cable modem, or ping either of them, it's not a network issue.

you may just need to release and renew your wan connection.

failing all of that disable and hardware or software firewalls you may be running and see if this resolves the issue.


so many possibilities, i just hope you don't have a pppoe connection, i used to work for verizon and i know what kinda chite hardware companies like that provide you with for internet.

anyway good luck :)

---

### Post by civetta on 2006-10-18
Great guide. I've put off compiling a custom kernel for too long (until I found this)!

I eventually did it because my ACPI wasn't working properly under the current Edgy kernel, and now it's fixed.

The only difficulty I had was with wireless firmware. I needed to get the ipw2200 firmware drivers, and paste them into a new directory: /lib/firmware/2.6.18/ that's it.

With that out of the way, my system is running much more smoothly, booting up faster, suspending faster, and beryl and kiba-dock are running like better too!

Thanks again for the guide!

---

### Post by GregaS on 2006-10-18
Problem is with tulip/davicom driver. I solved the problem with this:

[http://www.ubuntuforums.org/showthread.php?t=168821&page=4](http://www.ubuntuforums.org/showthread.php?t=168821&page=4)

---

### Post by jazzykay on 2006-10-18
hello everyone, 

for some reason I am having trouble compiling the kernel. 

here is the error: any ideas on how to fix this
command used:  make-kpkg -initrd --revision=686 kernel_image kernel_headers modules_image

error: 
In file included from fs/devpts/inode.c:20:
include/linux/devpts_fs.h:20: error: syntax error before â%â token
In file included from fs/devpts/inode.c:20:
include/linux/devpts_fs.h:34:2: error: invalid preprocessing directive #%
include/linux/devpts_fs.h:13:1: error: unterminated #ifndef
make[3]: *** [fs/devpts/inode.o] Error 1
make[2]: *** [fs/devpts] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18'
make: *** [stamp-build] Error 2

any ideas?

thanks, 

jazzykay

---

### Post by d3v1ant_0n3 on 2006-10-19
Worked a treat...2 months ago I didn't even know what a kernel really WAS! And I just compiled my first one. Woo!

Only issues I encountered were typos on my part lol.

---

### Post by hikaricore on 2006-10-19
> **jazzykay said:**
> hello everyone, 

for some reason I am having trouble compiling the kernel. 

here is the error: any ideas on how to fix this
command used:  make-kpkg -initrd --revision=686 kernel_image kernel_headers modules_image

error: 
In file included from fs/devpts/inode.c:20:
include/linux/devpts_fs.h:20: error: syntax error before â%â token
In file included from fs/devpts/inode.c:20:
include/linux/devpts_fs.h:34:2: error: invalid preprocessing directive #%
include/linux/devpts_fs.h:13:1: error: unterminated #ifndef
make[3]: *** [fs/devpts/inode.o] Error 1
make[2]: *** [fs/devpts] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18'
make: *** [stamp-build] Error 2

any ideas?

thanks, 

jazzykay



Just a couple of thoughts, my guess would be either a corrupt file, or something went wrong with the gui configuration of the kernel.  You may want to try re-extracting the src archive from command line and watching for errors.  Failing that redownload and see if that solves the issue.  *shrug*  I never have any trouble building kernels so I can't offer much assistance.

---

### Post by bennyj on 2006-10-20
Hi folks!First off I wanted to say thanks for this great tutorial.I do however have one problem.I compiled the kernel with no prob,installed no prob,on reboot my ubuntu screen comes up and it shows everything loading as normal until it gets to the line "Starting Kernel Log".then it just hangs there.anyone know what might cause this? I booted back into 2.6.15 to come in here and post this.Just so you know I compiled the 2.6.18 kernel.Thanks

---

### Post by foxy123 on 2006-10-22
it's a great tutorial, however, though the kernel compiled it took all the space I've got on my /. I wonder if I can remove /usr/src/linux-2.6.18 as it is more than half a gig?

---

### Post by foxy123 on 2006-10-22
Also when I tried to install ndsiwrapper made with checkinstall I've got the following error:
```
dpkg: error processing ndiswrapper_1.26-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.18/modules.ofmap', which is also in package kernel-image-2.6.18
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ndiswrapper_1.26-1_i386.deb

```

---

### Post by mking213 on 2006-10-22
What would be the point in compiling a new kernel, -5 seconds boot time?

---

### Post by kikke on 2006-10-24
> **mking213 said:**
> What would be the point in compiling a new kernel, -5 seconds boot time?

Realtime preemtion support.

---

### Post by Malakia on 2006-10-24
Try installing ndiswrapper by using the source instead of the .deb file. I tried using ndiswrapper v. 1.26, 1.25 and 1.24 but neither of them would work with my card so I ended up using v. 1.23 and it worked perfectly. Just experiment with the different versions to see what works. Also you might need to download wireless tools v.28, just google wireless tools and it should be the first one.

---

### Post by ciscosurfer on 2006-10-24
> **mking213 said:**
> What would be the point in compiling a new kernel, -5 seconds boot time?

An optimized instruction set specific to your architecture.  This ideally makes the kernel faster as well as more finely tuned to your specific computer.  You can compile with/without certain modules thereby making the kernel an acutely-honed animal.

---

### Post by pichalsi on 2006-10-24
thanks, nice tutorial, now i got fresh 2.6.19-rc3 :)

---

### Post by Somniis on 2006-10-24
Thanks for the guide. :) It seemed to compile and install correctly.

However, on reboot, the X server diag comes up (expected) but when it goes back to the console (or what should be the console), it does nothing.  There is a "_" that blinks, but no prompt at all.  I reverted back to the 2.17 kernel right now, but would like to try and get the 2.18 working.  I can type and such at the screen, but no commands work.. it's like the console doesn't even load.  So, it's impossible to configure X (which I know how to do).

Any ideas?  I haven't read all the pages in this thread, so if there is an answer in here, please point it out to me. :)

---

### Post by pichalsi on 2006-10-24
i dont know if you tried ctrl alt f1, if that doesnt work i think you will have to recompile or what.

---

### Post by foxy123 on 2006-10-26
> **Malakia said:**
> Try installing ndiswrapper by using the source instead of the .deb file. I tried using ndiswrapper v. 1.26, 1.25 and 1.24 but neither of them would work with my card so I ended up using v. 1.23 and it worked perfectly. Just experiment with the different versions to see what works. Also you might need to download wireless tools v.28, just google wireless tools and it should be the first one.

you mean I would need to compile wireless tools as well?

---

### Post by foxy123 on 2006-10-27
The latest stable version on the [www.kernel.org](www.kernel.org) is 2.6.18.1. Should I use it instead of 2.6.18?

---

### Post by fguilhon on 2006-10-27
Hello!!
Thanks for the tutorial.. It's nice!
I compiled succesfully the first time... But then, I noticed the iptables missing.. and on my second compile I'm getting compilation errors:
> 
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
net/built-in.o: In function `checkentry':xt_physdev.c:(.text+0x233f0): undefined reference to `brnf_deferred_hooks'
:xt_physdev.c:(.text+0x23415): undefined reference to `brnf_deferred_hooks'


Anyone knows what this means??

---

### Post by fguilhon on 2006-10-27
Nevermind... I found the problem...
It is a known bug... link [here]("http://lkml.org/lkml/2006/9/21/294")..

---

### Post by foxy123 on 2006-10-27
no, even compiled from source ndiswrapper does not work.

I decided just to put the source from repositories into /usr/src/modules and compile it with the kernel. While the ndiswrapper modules compiled successfully I cannot install it.

```
 dpkg -i ndiswrapper-modules-2.6.18-ck1_1.8-0ubuntu2+686_i386.deb
Selecting previously deselected package ndiswrapper-modules-2.6.18-ck1.
(Reading database ... 148317 files and directories currently installed.)
Unpacking ndiswrapper-modules-2.6.18-ck1 (from ndiswrapper-modules-2.6.18-ck1_1.8-0ubuntu2+686_i386.deb) ...
dpkg: dependency problems prevent configuration of ndiswrapper-modules-2.6.18-ck1:
 ndiswrapper-modules-2.6.18-ck1 depends on ndiswrapper-utils (>= 1.8-1); however:
  Version of ndiswrapper-utils on system is 1.8-0ubuntu2.
dpkg: error processing ndiswrapper-modules-2.6.18-ck1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ndiswrapper-modules-2.6.18-ck1

```

For some reasons it depends on 1.8-1 version of ndiswrapper-utils, not 1.8. I wonder why...

---

### Post by pichalsi on 2006-10-27
Thanks for the howto, i installed 2.6.19-rc3 it works nice.
However i would like to ask, what do the patches do? are there any good for notebook? Like what does the -mm patch do? i havent tried wifi on my asus laptop, but everything else works nice, memory card reader, bluetooth, power management, maybe infrared i havent tried in this version but i think it worked before.

---

### Post by mintcoffee on 2006-10-28
Great HOWTO. I now have a nice 2.6.18 kernel running.. and it's solved my crashing SD card reader and buggy CPU frequency scaling issues :KS

---

### Post by ~LoKe on 2006-10-30
Just compiled the 2.6.18.1 kernel using some of the instructions here, as well as a few "guesses" on my part.  Was amazed it actually worked.

Thanks!

---

### Post by aalex77 on 2006-10-31
I got this error
```
for module in /usr/src/modules/fglrx ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.18" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="x86_64"                  \
                             KDREV="ale1" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \                      echo "in fact being built as root, please file a bug ";  \                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx'
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[2]: Entering directory `/usr/src/linux-2.6.18'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:233: error: ‘UTS_RELEASE’ undeclared here (not in a function)
/usr/src/modules/fglrx/firegl_public.c:447: warning: initialisation from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’:
/usr/src/modules/fglrx/firegl_public.c:570: warning: assignment discards qualifiers from pointer target type
/usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_put_user_ptr’:
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_unregister_ioctl32_conversion’:
/usr/src/modules/fglrx/firegl_public.c:2515: warning: ‘return’ with a value, in function returning void
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_vm_map’:
/usr/src/modules/fglrx/firegl_public.c:3175: error: ‘VM_SHM’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3175: error: (Each undeclared identifier is reported only once
/usr/src/modules/fglrx/firegl_public.c:3175: error: for each function it appears in.)
make[3]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[2]: *** [_module_/usr/src/modules/fglrx] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.18'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx'
Module /usr/src/modules/fglrx failed.
Hit return to Continue

```

anyone can help me??

---

### Post by tronica on 2006-10-31
something went wrong somewhere?

> root@ubuntu:/usr/src/linux-2.6.18# make-kpkg clean
exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean 
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
Bareword found where operator expected at -e line 1, near ""*** *** You have not yet configured your kernel! *** *** Please run some configurator (e.g. "make"
        (Missing operator before make?)
Bareword found where operator expected at -e line 1, near "" or *** "make"
        (Missing operator before make?)
Bareword found where operator expected at -e line 1, near "" or "make"
        (Missing operator before make?)
syntax error at -e line 1, near ""*** *** You have not yet configured your kernel! *** *** Please run some configurator (e.g. "make oldconfig"
Execution of -e aborted due to compilation errors.
/bin/sh: Syntax error: "(" unexpected
/usr/share/kernel-package/ruleset/misc/version_vars.mk:123: *** Error. The version number *** *** You have not yet configured your kernel! *** *** Please run some configurator (e.g. "make oldconfig" or *** "make menuconfig" or "make xconfig"). *** 2.*** *** You have not yet configured your kernel! *** *** Please run some configurator (e.g. "make oldconfig" or *** "make menuconfig" or "make xconfig"). *** 6.*** *** You have not yet configured your kernel! *** *** Please run some configurator (e.g. "make oldconfig" or *** "make menuconfig" or "make xconfig"). *** 18*** *** You have not yet configured your kernel! *** *** Please run some configurator (e.g. "make oldconfig" or *** "make menuconfig" or "make xconfig"). ****** *** You have not yet configured your kernel! *** *** Please run some configurator (e.g. "make oldconfig" or *** "make menuconfig" or "make xconfig"). *** is not all lowercase. Since the version ends up in the package name of the kernel image package, this is a Debian policy violation, and the packaging system shall refuse to package the image. .  Stop.
root@ubuntu:/usr/src/linux-2.6.18# 

---

### Post by dutchmega on 2006-11-01
I've got 2.6.18.1 also running here. Please put in the topicstart that modules like fglrx & nvidia need recompiling because the restricted modules in the repo are for an other kernel-version.

Unless someone knows a repo with 2.7.18.1 restricted models?

---

### Post by knowbody on 2006-11-03
On qconf, what to i pick for Pentium D ?? Is dual core supported?

---

### Post by jazzi on 2006-11-03
I've done everything and when I reboot it comes to a panic
There is the panic information:
> 
Kernel Panic--not syncing:VFS:unable to mount root fs on unknow block(0,0)


---

### Post by mainmojo on 2006-11-04
For those who require the ipw2200 module and get errors on boot that suggest the module was unable to load: something similar to:

```
ipw2200-bss.fw request_firmware failed: Reason -2
```
The above line will be one of the visible errors in dmesg.

You could try and compile the kernel as a loadable module (I don't think this is the default). To do this you need to be in the xconfig curses console (step #4 in first post of this thread). Now navigate to the ipw2200 driver setup by:
```
 Device Drivers ---> Network device support ---> Wireless LAN (non-hamradio) ---> <M> Intel PRO/Wireless 2200BG and 2915ABG Network Connection
```

The <M> instructs that the driver be built as a loadable module. This is what you want. For some reason if I leave it (default maybe?) at <*> (for built in), I get errors on startup and my wireless interface is never configured. Setting it at <M> automagically fixes it and the device is correctly configured.

I hope this helps someone.

---

### Post by doobit on 2006-11-05
I compiled the 2.6.18.1 kernel last night on my AMD Athlon 800 machine (an old Gateway2000) and it works great! I had to run dpkg -i (not cd .. && )for the two .deb files in the /usr/src folder. 
I also named them i386 instead of K7 even though I optimized for K7, because I didn't see the instructions for naming until after I already started the process. The new kernel works great though! It's noticeably quicker.

---

### Post by NeoLithium on 2006-11-05
All I have to say is WOW!  I just finished compiling my new 2.6.18; and man; I'm suprised at how much speed I gained from ditching some of those things that I didn't need!  Excellent how to; I had no problems, and step by step, I'm surprised how quick it actually was.

PS- Man does it ever feel great the first time you compile your own kernel ;)

---

### Post by sudonim on 2006-11-06
I didn't select any special options for my ipw2200 when compiling the kernel (other than making sure it was selected) and then upon boot didn't have wireless. All I had to do to fix the problem was copy the firmware files ipw2200*.* files from /lib/firmware/'old-kernel' to /usr/lib/firmware/'name of your new kernel here' and it worked great.

I installed the gentoo kernel patch for undervolting my pentium M which is also working great. The init scripts that came with it didn't seem to work but adding a line to my rc.locals file did the trick for that. All in all a great tutorial, all of my devices are currently working perfectly, so perfectly I don't want to upgrade. :)

---

### Post by mithras86 on 2006-11-07
Why do you need the headers for Qt3 and a libqt-mt.so symlink? These packages depends on lots of other packages. 

Since I want not so many KDE stuff on my Gnome box, need you those two to compile the 2.6.18 kernel?

---

### Post by coffee on 2006-11-07
I am trying to install 2.6.18.2. I get alot of deprecation errors while compiling. And now I can not "apt-get" or use Synaptic, all package managers seem to be broken and give me an error.

E: The package linux-image-2.6.18.2 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

help, don't whant to have to reinstall!

Ok, its me again I got it to install and allow me to use the package managers.  But it won't boot.  It starts up fine and gets to the Ubuntu usplash, then it goes to the terminal and sais the it can not mount my drives, they are busy.  It logs stuff in /var/log/fsck:  

Log of fsck -C -R -A -a 
Thu Nov  9 13:29:02 2006

fsck 1.39 (29-May-2006)
/home: clean, 30819/10715136 files, 684103/21424685 blocks
/var: clean, 372464/4767744 files, 1910506/9520520 blocks
/usr: clean, 18141/3932160 files, 1071500/7863817 blocks

Thu Nov  9 13:29:02 2006
----------------

This looks good to me. What am I doing wrong?

---

### Post by pirous on 2006-11-12
I followed every steps and compling process was sucsessful on my Toshiba Satellite Pro A-40. Restart was beautifully fast. But I noticed problem when I run toshset from terminal. It says:  

SciFeature:action: error setting CPU speed
        SciSet returned: FAILURE

I went back using my original generic kernel just to check, and everything´s fine under that kernel. I tried to recompile again and make sure that toshiba support was compiled into kernel. After rebooting, the same problem exist. I recompiled again and put toshiba support as module. After rebooting and I tried toshset, it says: toshiba support not loaded (something like that). I repeated the previous method.. same thing. Then I remember maybe I can load toshiba_acpi by modprobe. 
I typed modprobe -a toshiba_acpi. It gave result like this: 
 
WARNING: Error inserting toshiba_acpi (/lib/modules/2.6.18/kernel/drivers/acpi/toshiba_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I run dmesg. Let me copypaste the last line:
[ 5440.218000] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'

Somebody can help?

---

### Post by Golgoth on 2006-11-12
First time I try to compile my own kernel and it worked very well. 
Thank U very much!!

:D

---

### Post by rsavu on 2006-11-12
Hello I followed your exact tutorial for kernel 2.6.18.1.

My problem is that i cannot get DRI on my ATI X300 working.

Here is the output from flgrxinfo:

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1

```

Here is my xorg.conf
```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```
It was working on the default kernel (2.6.17.10).

What should i do?

---

### Post by anodizer on 2006-11-13
Why are the packages "libqt3-headers libqt3-mt-dev" needed? Just for Xconfig or something else too?

---

### Post by Matt Yun on 2006-11-14
> **fguilhon said:**
> Hello!!
Thanks for the tutorial.. It's nice!
I compiled succesfully the first time... But then, I noticed the iptables missing.. and on my second compile I'm getting compilation errors:

net/built-in.o: In function `checkentry't_physdev.c.text+0x233f0): undefined reference to `brnf_deferred_hooks'

Anyone knows what this means??

> **fguilhon said:**
> Nevermind... I found the problem...
It is a known bug... link [here]("http://lkml.org/lkml/2006/9/21/294")..

1) I had the same problem when I tried to compile iptables support, and found an [easy fix]("http://www.mail-archive.com/netdev@vger.kernel.org/msg22597.html").

cd to your linux source directory (eg /usr/src/linux-2.6.18) and edit the file net/netfilter/xt_physdev.c.

At lines 117 and 118, edit the lines as follows:

Old code:
```
 if (brnf_deferred_hooks == 0 &&
     info->bitmask & XT_PHYSDEV_OP_OUT &&
```

New code (changes in red):

```
if ([COLOR="Red"]([/COLOR]brnf_deferred_hooks == 0[COLOR="Red"])[/COLOR] &&
            [COLOR="Red"]([/COLOR]info->bitmask & XT_PHYSDEV_OP_OUT[COLOR="Red"])[/COLOR] &&
```

Then, insert a line before line 104 and add the following:
```
int brnf_deferred_hooks = 0;
```

2) I compiled netfilter iptables support as modules, rather than compiled in.

3) Also, for those of you having problems mounting your hard drive volumes:  the vanilla 2.6.18 kernel requires the evms patch for systems with more than one hard drive: see [Solved: "Mounting Local Filesystems" fails after compiling new kernel]("http://ubuntuforums.org/showthread.php?t=103900").  Also see my post in the [Gnome Locks Up on SMP Kernel]("http://ubuntuforums.org/showthread.php?t=262735") thread.

---

### Post by clfenwi on 2006-11-15
> **anodizer said:**
> Why are the packages "libqt3-headers libqt3-mt-dev" needed? Just for Xconfig or something else too?

I am reasonably certain that those packages are needed just for Xconfig. An alternative is to install the "libncurses5-dev" package and use menuconfig instead of xconfig.

See step five of the [How To Compile a Kernel the Ubuntu Way]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2") for some details on how to proceed with this approach.

---

### Post by ciscosurfer on 2006-11-15
xconfig is a lot nicer to use though, imo.

And btw, I've got my 2.6.18 kernel up and running.  Pretty nifty and it just zooms along!  Love it!

---

### Post by GQed76 on 2006-11-23
On step 4 i get the following output, and then it just hangs.


```
Local version - append to kernel release (LOCALVERSION) [] 
Automatically append version information to the version string (LOCALVERSION_AUTO) [N/y/?] n
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?] y
System V IPC (SYSVIPC) [Y/n/?] y
POSIX Message Queues (POSIX_MQUEUE) [Y/n/?] y
BSD Process Accounting (BSD_PROCESS_ACCT) [Y/n/?] y
  BSD Process Accounting version 3 file format (BSD_PROCESS_ACCT_V3) [Y/n/?] y
Export task/process statistics through netlink (EXPERIMENTAL) (TASKSTATS) [N/y/?] (NEW) 
```

---

### Post by Blazeix on 2006-11-23
I have a quick question. The tutorial says that we should look [here](http://www.ubuntuforums.org/showpost.php?p=1308736&postcount=106) for an important note. The note is for kernel version 2.6.17, while the guide was recently updated for 2.6.18. Is the bug still in there or has it been fixed? Thanks.

EDIT: I have the same problem as GQed76 above. If I'm interpreting this correctly (I am new to this) the new release has several features that aren't in the current release, so it wants our input to configure them. Unfortunately, there are a lot of new features, many of which I'm not sure about. Is there a way to have these automatically configured?

---

### Post by aniskasa on 2006-11-26
Hi,

I followed the how-to and everything seemed to go fine.

The problem: only black screen when booting and X not loading.

I tried to enter the recovery mode, and switch to runlevel 3 by 

```
telinit 3
```

Then I installed the nvidia drivers as told here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Everything seemed to get fine, reboot, same result.

Again to recovery mode and tried to start x from there, I'm told that the nvidia modules are not found. So, I put line

```
nvidia 
```

to /etc/modules.

Reboot, nothing. I'm just out of ideas what is wrong...

---

### Post by aniskasa on 2006-11-26
Problem solved, in recovery mode and runlevel 3, if that matters(?) did this:

```
sudo apt-get install nvidia-kernel-source
```

then cd /usr/src/ unpack the tarball, 'make module', 'make install'

reboot, and X is up and running.

---

### Post by balloons on 2006-11-26
fyi i think you meant gdm not gdu

> sudo /etc/init.d/gdu stop

great guide

---

### Post by Talon2 on 2006-11-26
Thanks for the guide.  First time through with a clean Edgy install everything went great.

I have a couple of issues:

1)  The guide doesn't address the situation where you go back, reconfigure and compile again.  I gave it my best guess but ended up with errors that are probably the result of me not knowing what to do.

2)  #7 - cd .. && dpkg -i <name of the file>

This is a little confusing because if you execute "cd .." twice you end up in the wrong directory.

---

### Post by aniskasa on 2006-11-27
I have a problem with mounting discs, which works fine when I boot with previous kernel.

in /etc/fstab I have:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home/aniskasa/filez     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc1       /home/aniskasa/mp3     ext3    defaults 0       1
/dev/hdc2       /home/aniskasa/leffat     ext3    defaults 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2       /media/iPod     vfat    nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```

Now 'mount' gives:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hda5 on /home/aniskasa/filez type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

So the /dev/hdc1 and /dev/hdc2 are not mounted.

```
sudo mount -t ext3 /dev/hdc1 /home/aniskasa/mp3/
```

gives

```
mount: /dev/hdc1 already mounted or /home/aniskasa/mp3/ busy
```

and finally 

```
lsof /home/aniskasa/mp3/
```

gives nothing, so the dir is not busy.

Same thing with the hdc2.

I even commented with # the hdc1 and hdc2 lines in fstab, rebooted, and still it told me that they are mounted or the dir is busy.

Any ideas?

---

### Post by EmanuilTolev on 2006-11-27
Only one little note: the kernel compilation step
(make-kpkg [a shitload of options and targets])

now reads: 'make-kpkg -initrd ......'
It should be 'make-kpkg --initrd .......', because initrd is an option, and it doesn't work with 1 dash for me :). Note that if the user can't help himself when encountering such a problem, he should definetely not be compiling a kernel :D.

---

### Post by N'Jal on 2006-11-28
I can't re-install my graphics driver after updating to the new kernel, well I can, but it does not do anything I installed the beta driver using the nvidia-glx and ran nvidia-xconfig and sure enough my driver is nvidia but X bombs out on me running the new kernel, old one works fine though. But if someone could help, i would appreciate it.

---

### Post by aniskasa on 2006-11-30
^ I had the same problem, solution for me is in the previous page, message #349  :)

So the idea is to compile and install the nvidia driver kernel module, which is also needed. With the package there is a README -file, too.

But does anyone have a solution for my mounting problem? I've been googling aroung and I assume that I'm missing a IDE/HD -supporting module, but don't know what to install. (And can I do it without compiling the kernel again...)

---

### Post by foxy123 on 2006-12-02
I used this howto to install the current stable version 2.6.19 and it worked pretty well as usual. The only issue I have with ndiswrapper. I decided to use the source from Feisty. The module compiled fine and I installed it with a backported Feisty ndiswrapper utils and common. But now I have the following error:
```
$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```
The module is installed:
```
$ ls /lib/modules/2.6.19/misc/lib/modules/2.6.19/misc
ndiswrapper.ko

```

It looks like modprobe does not see it. Any way to make it aware about where the module is?

---

### Post by kurty on 2006-12-02
I have a dell inspiron 6400, I would like to try compiling a kernel, but I am a newbie. Any special considerations I might need to do?

I have asked this question in a seperate post [here]("http://www.ubuntuforums.org/showthread.php?t=311064")

---

### Post by whomever21 on 2006-12-05
I tried this on 2.6.19.  It compiled without a hitch, but then on reboot I got this:

Begin: Waiting for root file system.. ...

And it just hangs.

---

### Post by foxy123 on 2006-12-06
> **whomever21 said:**
> I tried this on 2.6.19.  It compiled without a hitch, but then on reboot I got this:

Begin: Waiting for root file system.. ...

And it just hangs.

there is a new thread for 2.6.19 I believe.

---

### Post by ciscosurfer on 2006-12-06
> **foxy123 said:**
> there is a new thread for 2.6.19 I believe.Can you post the link for it?

---

### Post by foxy123 on 2006-12-06
> **ciscosurfer said:**
> Can you post the link for it?

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by PanzerMKZ on 2006-12-13
What about compiling on a SMP system?  Any options different?  Will this make use of both procs?


Panzer

---

### Post by L3oN on 2006-12-15
Hi, i'm trying to compile 2.6.19.1.... but i recived this error:```
In file included from mm/swap.c:26:
include/linux/mm_inline.h:25: error: redefinition of ‘add_page_to_inactive_list_tail’
include/linux/mm_inline.h:18: error: previous definition of ‘add_page_to_inactive_list_tail’ was here
make[2]: *** [mm/swap.o] Error 1
make[1]: *** [mm] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19.1'
make: *** [debian/stamp-build-kernel] Error 2

```

---

### Post by gejr on 2006-12-15
I don't feel like reading through 37 pages of problems not related to my problem. (I've read 10-15 pages I think) Anyway..I followed this guide with absolutely no problems, but when I rebooted I can't boot with the new kernel. Absolutely nothing seem to happen when I choos 2.6.19 from grub-menu. I only get a black screen with a white cursor blinking in the upper left corner. Has this issue been discussed? Is there a fix? Please help..

---

### Post by xoai on 2006-12-16
I have some problems at 4 step

```

xoai@Macbuntu:/usr/src/linux$ sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig
scripts/kconfig/conf -o arch/i386/Kconfig
.config:28:warning: trying to assign nonexistent symbol VERSION_SIGNATURE
.config:60:warning: trying to assign nonexistent symbol OBSOLETE_INTERMODULE
.config:169:warning: trying to assign nonexistent symbol THINKPAD_EC
.config:170:warning: trying to assign nonexistent symbol TP_SMAPI
.config:176:warning: trying to assign nonexistent symbol 05GB
.config:177:warning: trying to assign nonexistent symbol 1GB
.config:178:warning: trying to assign nonexistent symbol 2GB
.config:179:warning: trying to assign nonexistent symbol 3GB
..........
*
* Linux Kernel Configuration
*
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] y
*
* General setup
*
Local version - append to kernel release (LOCALVERSION) [] 
Automatically append version information to the version string (LOCALVERSION_AUTO) [N/y/?] n
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?] y
System V IPC (SYSVIPC) [Y/n/?] y
  IPC Namespaces (IPC_NS) [N/y/?] (NEW) 

```

:-S anybody knows how to solve it?

---

### Post by birdman3131 on 2006-12-17
ok im doing this with no internet in linux so im downloading the kernel in xp so what do i need to change? im new to linux

---

### Post by ostvarivanje on 2006-12-17
This is my first post here, and I' sorry for my bad english. 
For first time I compiled the kernel 2.6.19 but have problem with nvidia drivers. I tried few times to install, but it synaptic (or apt-get) didn't find 2.6.19 header, but only 2.6.17-generic. 
What can I do?
When I want to compile kernel, I put k7 (amd 3800+ X2, Edgy 64bit). Why in grub menu I have entry 2.6.19 and not 2.6.19.k7?
Before all these tries, I wanted to install k8 with apt-get install linux-k8 but it didn't any package with this name.

---

### Post by Camino on 2006-12-18
Hi,
I just compiled the 2.6.19.1 kernel and it´s working really great (great tutorial!!) except....

I can´t compile the Ralink RT61 drivers 1.1.0 downloaded from the supplier support page

Is there anyone who got them running with the latest kernel. The make process failed and wireless connection isn´t possible at all for me:(

Bye

---

### Post by compwiz18 on 2006-12-18
> **xoai said:**
> I have some problems at 4 step

```

xoai@Macbuntu:/usr/src/linux$ sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig
scripts/kconfig/conf -o arch/i386/Kconfig
.config:28:warning: trying to assign nonexistent symbol VERSION_SIGNATURE
.config:60:warning: trying to assign nonexistent symbol OBSOLETE_INTERMODULE
.config:169:warning: trying to assign nonexistent symbol THINKPAD_EC
.config:170:warning: trying to assign nonexistent symbol TP_SMAPI
.config:176:warning: trying to assign nonexistent symbol 05GB
.config:177:warning: trying to assign nonexistent symbol 1GB
.config:178:warning: trying to assign nonexistent symbol 2GB
.config:179:warning: trying to assign nonexistent symbol 3GB
..........
*
* Linux Kernel Configuration
*
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] y
*
* General setup
*
Local version - append to kernel release (LOCALVERSION) [] 
Automatically append version information to the version string (LOCALVERSION_AUTO) [N/y/?] n
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?] y
System V IPC (SYSVIPC) [Y/n/?] y
  IPC Namespaces (IPC_NS) [N/y/?] (NEW) 

```

:-S anybody knows how to solve it?
Just hold enter till you are returned to the prompt.

---

### Post by foureight84 on 2006-12-20
hmm would it be easier if i were to compile the new kernel on a fresh installation?

---

### Post by pay on 2006-12-20
> **foureight84 said:**
> hmm would it be easier if i were to compile the new kernel on a fresh installation?Not really. Just make sure you  have gcc and things like that installed. And reinstall your video drivers.

---

