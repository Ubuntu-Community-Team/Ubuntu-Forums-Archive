---
title: "ATI radeonhd 3xxx/4xxx r5xx/r6xx driver/kvm 3d graphics tutorial"
date: 2010-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by kronictokr on 2010-04-27
IMPORTANT, READ **NOTE** BEFORE CONTINUING!!!!!!!!!
AND BACKUP IMPORTANT INFO!!!! and make sure you are fully updated before continuing!!!
again
******************only update when the tut tells you to************** 
                                you have been warned!!!!  
follow the tut and you'll boot up fine, think you know better, than you better, or be a victim of your own faite..... muhahhaha, ok ok, it works great, :P                               ********************************************************

[B][U]if using karmic, i recomend this update for your system, it fixes sound issues, and installs most multimedia needed, including flashplayer
[http://ubuntuforums.org/showthread.php?t=1395089](http://ubuntuforums.org/showthread.php?t=1395089)
[/U][/B] 
_** First section for karmic, second for lucid**_

**note** this has been tested on hp pavilion dv6/dv7 with amd64 and ati radeon hd 4xxx series, and radeon hd 3xxx series, using r6xx/r7xx drivers. **end note**

*_**first section**_*

                            make sure you update your system, including backports and such , before doing this tut!!!

make sure youre menu.list is recent and up to date

in a terminal

code:
gksudo gedit /etc/apt/sources.list

replace current list with this one

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

save and exit
then

code:
sudo apt-get update

code:
sudo reboot



we want to add the ppa repos so we can upgade our drivers and enable 3d accelerated graphics.

open your software sources from administration. the go to add source. and add each of these lines one at a time.

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 

deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 

close and reload


open a terminal and paste in the next line and hit enter

code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542

code:
mkdir kerneldebs

code:
cd kerneldebs/

code:
sudo wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb")

sudo dpkg -i linux*


new terminal
code:
sudo apt-get update

code:
sudo update-initramfs `2.6.33-020633` -u

code:
sudo update-grub

yes it will say missing files, we are about to fix, dont reboot untill the tut tells you, or , you will be your own demise when you have to start over with a fresh install, because yr box doesnt boot right. FOLLOW THE TUT!!

code:
cd /lib/firmware/2.6.33-020633-generic/radeon

code:
sudo wget [http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R600_rlc.bin") [http://people.freedesktop.org/~agd5f/radeon_ucode/R700_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R700_rlc.bin")
[http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R600_rlc.bin") [http://people.freedesktop.org/~agd5f/radeon_ucode/R700_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R700_rlc.bin")


new terminal

code:
echo vesafb | sudo tee -a /etc/initramfs-tools/modules
code:
echo fbcon | sudo tee -a /etc/initramfs-tools/modules

lets configuring some files, to ensure everything reloads and reboots properly when we need it to.

to do this the easy way, still in our terminal, or open a new one.
we do

code:
gksudo nautilus

click on the left filesystem. go to this path /etc/default/grub, double clicking the grub file.

Add radeon.modeset=1 to the end of the line
GRUB_CMDLINE_LINUX_DEFAULT=

like so
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=1"
replacing, "soft splash" otion, which has been known to cause issues.
save, close the file.

still in gksudo, next path, /etc/grub.d/40_custom , double clicking 40_custom file, and add "radeon.modeset=1" at the bottom of the file, without the quotes, and without changing anything else, save and exit.

for good measure, and to cut down posible errors
To make sure the radeon modules is initialized before gdm (and X) is starting, insert "modprobe radeon" into your /etc/init/gdm.conf just before the gdm-binary is executed:

...
initctl emit starting-dm DM=gdm

modprobe radeon
exec gdm-binary $CONFIG_FILE
end script

close windows till you exit nautilus and get back into your terminal

then in terminal

code:
sudo aptitude install libvirt-bin qemu kvm libvirt ubuntu-vm-builder bridge-utils virt-viewer

tab , hit enter, choose "no configuration" hit enter

code:
sudo apt-get update

code:
sudo aptitude install xf86-video-radeonhd xserver-xorg-video-radeonhd

code:
sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core

code:
sudo apt-get update

code:
sudo apt-get upgrade 
you may be promted to select who will maintain pakages, use maitainers since were going through all the trouble ;) "y" to install pakage maintainers version, twice, second time use arrow and enter.

these next two commands are to ensure compiz runs without restrictions

code:
mkdir -p $HOME/.config/compiz

code:
echo 'WHITELIST="$WHITELIST radeonhd"' >> $HOME/.config/compiz/compiz-manager

code:
echo vesafb | sudo tee -a /etc/initramfs-tools/modules

code:
echo fbcon | sudo tee -a /etc/initramfs-tools/modules

code:
sudo update-initramfs `2.6.33-020633` -u

code:
sudo update-grub

code:
sudo apt-get update

code:
sudo reboot

** #############################################################**

*_**second section**_*

Lucid begin here

Code:
sudo aptitude install libvirt-bin qemu kvm ubuntu-vm-builder bridge-utils virt-viewer

tab , hit enter, choose "no connection" hit enter

when done, still in terminal

you may not have to do this, but i havent had any problems using it. this is if you plan on using compiz

Code:
mkdir -p $HOME/.config/compiz

Code:
echo 'WHITELIST="$WHITELIST radeonhd"' >> $HOME/.config/compiz/compiz-manager


now we are going to configure a few files to ensure a successfull load of all our programs and drivers.

to do this the easy way, still in our terminal, or open a new one.
we do 

code:
gksudo nautilus

click on the left filesystem. go to this path  /etc/default/grub, double clicking the grub file.

Add   radeon.modeset=1    to the end of the line 
GRUB_CMDLINE_LINUX_DEFAULT=

like so
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=1"
replacing,    "soft splash"    otion, which has been known to cause issues.
save, close the file.

still in gksudo, next path,     /etc/grub.d/custom40     , double clicking   40_custom    file, and add      "radeon.modeset=1"     at the bottom of the file, without the quotes, and without changing anything else, save and exit.

for good measure, and to cut down posible errors
To make sure the radeon modules is initialized before gdm (and X) is starting, insert "modprobe radeon" into your /etc/init/gdm.conf just before the gdm-binary is executed:

    ...
    initctl emit starting-dm DM=gdm

    modprobe radeon
    exec gdm-binary $CONFIG_FILE
end script

like so ^^^^ above, save and exit


now exit nautilus, to bring you back into your terminal

new lucid kernel/ajust according to your current kernel version

Code:
cd /lib/firmware/2.6.32-21-generic/radeon

Code:
sudo wget [http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R600_rlc.bin") [http://people.freedesktop.org/~agd5f/radeon_ucode/R700_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R700_rlc.bin")


close and open a new terminal

Code:
sudo update-initramfs -u

Code:
sudo update-grub

now we want to add the ppa repos so we can upgrade our drivers and enable 3d accelerated graphics.

open your software sources from administration. the go to add source. and add each of these lines one at a time.

 lucid

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main 

deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main 

close and reload



open a terminal and paste in the next line and hit enter

Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542 

Code:
sudo aptitude install xserver-xorg-video-radeonhd

Code:
sudo aptitude upgrade

now we update/notify our system of changes made

First update modules.dep:

Code:
sudo depmod -a $(uname -r)

then
Update the initramfs:

Code:
sudo update-initramfs -u -k $(uname -r) 

code:
sudo update-grub

code:
sudo reboot



###OPTIONAL###

you can boot to recovery at this point, and drop into root. you will have had to set your root password for this option. 

this section is to configure you "xorg.conf" file. however it is optional, as you can boot without the file. how ever if you want to produce an acurate xorg.conf which you can configure for other options, that you may not be able to do with kmv, then do the following.  

while in root do the following command

code:
sudo Xorg -configure

then 

Code:
sudo depmod -a $(uname -r)

then
Update the initramfs:

Code:
sudo update-initramfs -u -k $(uname -r) 

code:
sudo update-grub

code:
sudo reboot

---

### Post by banskt on 2010-07-23
Thanks, I was having some problems with the ATI Catalyst driver in 3D rendering for compiz and cairo-dock.

It was not much of an issue, but as I saw your post, I thought I would give it a try.

Finally, I did it yesterday. It was a nice tutorial...

However, after installing the driver, when I booted to recovery mode to update xorg.conf, I started getting errors. After a bit of troubleshooting, I found the reason:
For Lucid Lynx the package xserver-xorg-video-vmware is  broken, as on July-22-2010.
I had to remove that package, and obviously xserver-xorg-video-all, for that reason.

After that, I had to compile my xorg.conf once again, and everything was back to normal. 

Again on reboot, I ran into the initramfs terminal --- again I had to go into recovery mode, update-initramfs, and finally my system is up and running. 

And obviously, now I have some nice 3D effects on my desktop. [See here.]("http://ubuntuforums.org/showpost.php?p=9625676&postcount=612")

Btw, is there any way / commands by which I can know that my video drivers are doing their job properly?

However, another problem on my system, the resolution at the grub menu is still persisting. [See discussion here.]("http://ubuntuforums.org/showthread.php?p=9625701#post9625701")

---

### Post by kronictokr on 2010-07-23
tx for the props in your original post btw.

i have the same chipset for a graphics card, 4200 HD, mine is mobile though.  but i havent had any trouble with either of those pakages. 
did you do an update through your system, those pakages could be fixed in an update already. like i said i dont have any weird behavior, and it all seems to update nicely.

you can add screen resolutions in your xorg.conf file, the options should show up after you reboot, and go to whatever program you use to control your monitor.

there are commands to see that you are running the proper gfx card. im working on a resume right now, when i have time ill see if i cant dig em up. if i recall, do a search for "ubuntu radeonhd"  make sure it the ubuntu page, and i believe the info is at the top of the page, its been a while, so...i look when i have a minute

and what program are you using for screen recording , i havent found one that works decent yet?

also, in my last redo of this tut, i never did the last optional part, to configure my xorg.conf, you may wana try without to see if your resolution gets fixed, or like i said add the proper screen config to your xorg.conf file

---

### Post by kronictokr on 2010-07-23
quote "djscribe" 
Hey Kronic, 

"First and foremost, I thank you and all others that contribute to our  evolution in overall computing within the Open Source community - you  guys don't thanked enough. 2nd, I'm a conservatively experienced user  when it comes to Linux/Ubuntu. So, that having been said, please take my  feedback with best of intentions. Ok

Not sure where I went wrong, but the [[http://ppa.launchpad.net/xorg-edgers...ts/lucid/main/]("http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/lucid/main/")  repositories were unreachable, even after tried pointing to  dists/lucid/main/amd-64 in my case etc. Also the r600_rlc and 700 bins  were not found either in the following command you cited:

sudo wget [http://people.freedesktop.org/~agd5f...e/R600_rlc.bin]("http://people.freedesktop.org/%7Eagd5f...e/R600_rlc.bin")  [http://people.freedesktop.org/~agd5f...e/R700_rlc.bin]("http://people.freedesktop.org/%7Eagd5f...e/R700_rlc.bin")  

Get an ERROR 404: Not Found.

Was this fix ONLY for intel? Here's what I'm running just in case:

MoBo: M4A89GTD PRO USB3
OnBoard ATI Radeon HD4200
CPU: AMD Phenom II X6 1090T 3.2GHz
RAM: 4GB
640GB 64MBCache 6gb/s WD SATA Drive

Any info would be cool, as I'm still running on generic drivers, so no  OpenGL.     "



well, make sure you have added the repositories, otherwise, you wont, be  able to download the necessary files.
[here]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Manually_add_repositories")  

also, if the kernel version you are running is different than the ones used here

new lucid kernel
Code:
cd /lib/firmware/2.6.32-21-generic/radeon

check your kernel version, located in your root boot file, and just change the kernel number accordingly. you may want to start over using the correct kernel version.

also make sure you dont miss steps in this section, as there is a key that must be used to unlock the repositories. make sure the before and after are all completed as well, but this area may be whats causing issues if youve missed it.

open your software sources from administration. the go to add source.  and add each of these lines one at a time.

karmic

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)  karmic main 

deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)  karmic main 

close and reload


lucid

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)  lucid main 

deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)  lucid main 

close and reload



open a terminal and paste in the next line and hit enter

Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542 


if you follow this tut, you install the radeonhd driver, with kvm. kvm, makes it accelerated 3D graphics. radeonhd is the gfx driver for your 4200hd

there are a lot of steps, make sure you dont miss any, and that all file paths are the same (they should be) as well as your kernel version. if your kernel version is diferent it goes to a different file path, and cause the firmware driver to not be found. 

everything must be completed in order, and ALL steps done, except for the last optional step.  this has been tested to work on multiple computers. 

it is made for and64 and ati chipsets, the specific info is posted at the top of the tutorial.

tx for your tx, any more questions, ill do my best to help

---

### Post by djscribe on 2010-07-23
Thanks for the flash response Kronic. I did forget to mention, I'm running Lucid 2.6.32.23.

Per the link you sent, once the kerneldebs are successfully fetched[3files]; here's what I get running the "sudo dpkg -i linux*" code:
---
dpkg: error processing linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
dpkg: error processing linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Setting up linux-headers-2.6.33-020633 (2.6.33-020633) ...
Errors were encountered while processing:
 linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb
 linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb

By the way, I've been able to make it fine up until the initframfs, it's adding the binary and source repos that it fails. See that link can't be reached...it seems it's been changed from

[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/lucid/main](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/lucid/main)
to 
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/lucid/main](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/lucid/main)

This is where both the binary-amd64 and sources libs are.

I appreciate your patience on this - Can't help feel like a dumbarse coming back to you on this, but this path simply doesn't exist. Correct me if I'm right, if enter this url in the browser, it should take me to the dir where these GZ files exist, correct? It does lead me to the 1st URL I typed back to you...which btw, still doesn't work. Even adding the correct path, yields:
--------------
Failed to fetch h tt p://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/lucid/main/binary-amd64/dists/lucid/main/**binary-i386/Packages.gz** 404  Not Found

Failed to fetch h t tp://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/lucid/main/source/dists/lucid/main/source/Sources.gz[/url]  404  Not Found

Some index files failed to download, they have been ignored, or old ones used instead.
--------------

Actually, I'm seeing it reference i-386 files in the Failed error, but that's not the path in my Software Sources. Where is it getting that from? My sources path ends at lucid/main. That's it.

---

### Post by kronictokr on 2010-07-23
ohhhhhhh, now it all makes sense my friend, im affraid you have the intel, or i386 version of ubuntu installed.  if you have amd64 processor, you may want to go to the ubuntu download page and get the amd64 version. then you should be able to complete this no problem. its not that my link were wrong, but that they dont line up with your install. sorry.
if you reinstall and try again, you should not have any problems. if you do , i will be able to help you much easier.  
sorry for the confusion

---

### Post by djscribe on 2010-07-23
Hey Kronic,

Well, considering I was getting NOTHING when I typed uname -m or even -a, to get the release, even though the CD I got from Canonical has no indications of it being AMD64, it is labeled as such when viewing through Computer while in the tray. Either way, system was quirky and manifesting other inconsistencies, so I've just reinstalled from scratch, new ext4, on a new partition and yes, *uname -a* now yields **X86_64 GNU/Linux**. dpkg --print-architecture = amd64. i386 may've come from the endless attempts I'd made to fix this before running into your solution. Valid concern from you, nonetheless.

Just so you know, there *are* updates pending, some of which will upgrade the linux kernel, libs and such, so I haven't done that, I'm still on 2.6.32.21. 

All steps previous to this, went without incident. Here's where I snagged.

Reloading after adding Sources:
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542

Fetching Key:
LYNX:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

So, I'm reluctant to move on. I tried several paths for the Sources, the one you've posted is the one that's errored the least for me. Let me know what's next.

---

### Post by kronictokr on 2010-07-23
well it seems the link may be outdated, i appologise, im having a few beer right now, but after work tomorrow, ill look further into this and find the original link, they may have changed the key, which is bizare, because my system is based on this tut, and it still updatates and boot without issue. none the less i will check it tomorrow.

and yes its bizare you had i386 on your system, especially considering it is an amd64 from source. 

heres a quick thought before i log out tho, did you add the key before the repo and download?

---

### Post by kronictokr on 2010-07-23
ive tested this method, over and over, so make sure you execute theses comands exactly, all previous commands are just as important. i may do a test install, and change file paths and kernel numbers acording to the new ones. if i have time on sunday

---

### Post by djscribe on 2010-07-24
That's a good question - I can't tell which other code would've summoned the key other than the one after the repo entries:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542

But likely, I'm having a few beers myself, albeit, under the hood of my car getting my AC fixed - just checkin up on whether or not I can entertain myself fixing this issue later this weekend. I don't deserve being labeled a geek, but having spent substantial $$ on a new rig motivates me to make it work. 

Anyway,thank you for all your time and effort. God bless Open Source and the Linux community.

Cheers to you and yours, bud.

---

### Post by djscribe on 2010-07-27
See Below...

---

### Post by djscribe on 2010-07-27
Hey Kron,

Son of a bee sting, I posted a quick reply and the forum completely ignored it. :D

Ok, I apologize if you run into it 2ice, I can't see my reply so here goes...again.

I think I may've stumbled onto why your script won't work for me. I was originally using [**this**]("http://ubuntuforums.org/showthread.php?t=1464748") post of yours, indicating:
**LUCID START AT PART 2!!**

...which of course took me past the whole reboot in low-graphics mode, etc...but the post on this page doesn't have such a remark. I did go through anything that didn't say Karmic on it, *after* I started running into snags, course this may've had a different effect altogether if any at all, maybe? 

Anyway...I'm back on a shiny new ext4 partition, installed from scratch. One thing I wanted to clarify, I should **not** run any of the 238 pending updates, correct? Just making sure, because it did occur to me that because I never have, there may be an update-reliant code in your script and this is why I'm fumbling? Not to mention I need to be on 2.6.32-21 for this to work right? The updates have header/kernel upgrades, hence my reluctance.
:-k

---

### Post by kronictokr on 2010-07-27
about to test this again, but, the day before you told me something was wrong. someone had tried this and had no problem at all. please double check your hardware and make sure you properly follow the instructions.  
i do have a full time job, this is what i do in my spare time. which i dont have enough of. i like to help, but please do some research, or review your work, first
if i sound irritated i am, im quitting smoking :P

---

### Post by djscribe on 2010-07-28
I undestand. Again, maybe I'm being over-sensitive about this, but can you at least clarify if I should follow everything that DOESN'T say Karmic from the beginning vs jumping straight to Part 2?

Thanks for all your help though, good luck with the habit kick!
:]

---

### Post by ShapeShifter499 on 2010-07-28
I was about to post saying something went wrong, your tutorial is useless, bla bla....   Until I spotted this one small error.  I had put the line "modprobe radeon" in the wrong spot in the file /etc/init/gdm.conf xD  I was worried for a while because till I fixed the problem I could not boot into a GUI

---

### Post by ShapeShifter499 on 2010-07-28
What do I do when there is a kernel update?

---

### Post by kronictokr on 2010-07-28
ok... first off, dont know how , but the order is wrong for karmic, i swear ive gone over and over this. 

so im fixing it now.

if you do this tut, its a custom build. meaning updating is not recomemded. if you like to update, do not follow this tut.

as this installs kernels that are developed by sources other than ubuntu, not that theirs are any more stable. but if it works, dont fix it ;)

once the order is fixed for karmic, i will change it.

---

### Post by auroraa9420 on 2010-07-28
does this work for ati 5830 too?

---

### Post by kronictokr on 2010-07-28
has not been tested to my knowledge on that gfx card

scribe, im working on it ;)


ok.... it been tested, tested again, and tested again, so BEFORE making comments, just so you know, i will answer, unless, it obvious, you did NOT follow or read the tut. in which case yr on your own, unless you care to pay me for my time, tx! that is all :P

btw, karmic part works great, and never had a problem with the lucid part!!!!

---

