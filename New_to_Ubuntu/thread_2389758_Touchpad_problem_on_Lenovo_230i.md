---
title: "Touchpad problem on Lenovo 230i"
date: 2018-04-21
forum: New to Ubuntu
---

### Post by pantazi on 2018-04-21
Using Ubuntu 16.4.4 LTS fresh download.

I have a problem with the cursor over-scrolling on the Synaptics touchpad making it tricky to work. Mouse and trackpoint ok. It seems to be a problem with this model as it does not present itself on my HP Elitebook 8460p which has the same touchpad.

After researching the forum, I tried  sudo apt install xserver-xorg-input-synaptics and got:


[code]
The following packages have unmet dependencies. 
 xserver-xorg-input-synaptics : Depends: xorg-input-abi-22 
                                Depends: xserver-xorg-core (>=  2:1.17.99.902) 
E: Unable to correct problems, you have held broken packages. [code]

Any ideas where I go from here?   I have found this suggestion:   http://fzheng.me/2017/05/11/fix-touchpad-ubuntu-1604/ but as a novice I am wary of sudo su commands.
Regards

---

### Post by cruzer001 on 2018-04-21
Xserver-xorg-input-synaptics is part of the default install and xorg-input-abi-22 is part of the xserver-xorg-core package that should already be installed.  Try something simple, in terminal:

```
sudo apt -f install
##and
apt policy *xorg-core *synaptics
```

Please post the outputs.

---

### Post by pantazi on 2018-04-21
```

anne@anne-ThinkPad-X230:~$ sudo apt -f install
[sudo] password for anne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 11 not to upgrade.
anne@anne-ThinkPad-X230:~$ apt policy *xorg-core *synaptics
xserver-xorg-core:
  Installed: (none)
  Candidate: 2:1.18.4-0ubuntu0.7
  Version table:
     2:1.18.4-0ubuntu0.7 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     2:1.18.3-1ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main i386 Packages
xorg-driver-synaptics:
  Installed: (none)
  Candidate: (none)
  Version table:
xserver-xorg-input-synaptics:
  Installed: (none)
  Candidate: 1.8.2-1ubuntu3
  Version table:
     1.8.2-1ubuntu3 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main i386 Packages
anne@anne-ThinkPad-X230:~$ 

```

---

### Post by cruzer001 on 2018-04-21
It will probably be necessary to resolve broken packages first.  Please post the output of:

```
sudo apt update && sudo apt full-upgrade
```

But you can still try an install.

```
sudo apt install xserver-xorg-core
```
 
If xorg installs:

```
sudo apt install xserver-xorg-input-synaptics
```

How did you install Ubuntu, did you checksum the download?  Were there any errors during the install?

---

### Post by pantazi on 2018-04-22
Thanks for reply Cruzer: Installed with flash drive, didn't know about checksum but the install was straightforward.

Output is 

```

anne@anne-ThinkPad-X230:~$ sudo apt update && sudo apt full-upgrade
[sudo] password for anne: 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [67.6 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [72.2 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [107 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 DEP-11 Metadata [319 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [147 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [240 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [574 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 DEP-11 Metadata [245 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [328 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [7,156 B]
Get:15 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main i386 DEP-11 Metadata [3,328 B]
Get:16 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe i386 DEP-11 Metadata [5,092 B]
Fetched 2,421 kB in 1s (1,453 kB/s)                                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
11 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-ibus-1.0 ibus ibus-gtk ibus-gtk3 libibus-1.0-5 libpam-modules
  libpam-modules-bin libpam-runtime libpam0g snapd ubuntu-core-launcher
11 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 10.3 MB of archives.
After this operation, 2,342 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 libpam0g i386 1.1.8-3.2ubuntu2.1 [57.7 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 libpam-modules-bin i386 1.1.8-3.2ubuntu2.1 [38.4 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 libpam-modules i386 1.1.8-3.2ubuntu2.1 [257 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 ubuntu-core-launcher i386 2.32.3.2 [1,566 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 snapd i386 2.32.3.2 [9,458 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 libpam-runtime all 1.1.8-3.2ubuntu2.1 [37.9 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 libibus-1.0-5 i386 1.5.11-1ubuntu2.1 [128 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 ibus i386 1.5.11-1ubuntu2.1 [218 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 gir1.2-ibus-1.0 i386 1.5.11-1ubuntu2.1 [65.9 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 ibus-gtk i386 1.5.11-1ubuntu2.1 [15.4 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 ibus-gtk3 i386 1.5.11-1ubuntu2.1 [15.6 kB]
Fetched 10.3 MB in 5s (1,802 kB/s) 
Preconfiguring packages ...
(Reading database ... 212599 files and directories currently installed.)
Preparing to unpack .../libpam0g_1.1.8-3.2ubuntu2.1_i386.deb ...
Unpacking libpam0g:i386 (1.1.8-3.2ubuntu2.1) over (1.1.8-3.2ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up libpam0g:i386 (1.1.8-3.2ubuntu2.1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
(Reading database ... 212599 files and directories currently installed.)
Preparing to unpack .../libpam-modules-bin_1.1.8-3.2ubuntu2.1_i386.deb ...
Unpacking libpam-modules-bin (1.1.8-3.2ubuntu2.1) over (1.1.8-3.2ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpam-modules-bin (1.1.8-3.2ubuntu2.1) ...
(Reading database ... 212599 files and directories currently installed.)
Preparing to unpack .../libpam-modules_1.1.8-3.2ubuntu2.1_i386.deb ...
Unpacking libpam-modules:i386 (1.1.8-3.2ubuntu2.1) over (1.1.8-3.2ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpam-modules:i386 (1.1.8-3.2ubuntu2.1) ...
(Reading database ... 212599 files and directories currently installed.)
Preparing to unpack .../ubuntu-core-launcher_2.32.3.2_i386.deb ...
Unpacking ubuntu-core-launcher (2.32.3.2) over (2.29.4.2) ...
Preparing to unpack .../snapd_2.32.3.2_i386.deb ...
Unpacking snapd (2.32.3.2) over (2.29.4.2) ...
Preparing to unpack .../libpam-runtime_1.1.8-3.2ubuntu2.1_all.deb ...
Unpacking libpam-runtime (1.1.8-3.2ubuntu2.1) over (1.1.8-3.2ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpam-runtime (1.1.8-3.2ubuntu2.1) ...
(Reading database ... 212604 files and directories currently installed.)
Preparing to unpack .../libibus-1.0-5_1.5.11-1ubuntu2.1_i386.deb ...
Unpacking libibus-1.0-5:i386 (1.5.11-1ubuntu2.1) over (1.5.11-1ubuntu2) ...
Preparing to unpack .../ibus_1.5.11-1ubuntu2.1_i386.deb ...
Unpacking ibus (1.5.11-1ubuntu2.1) over (1.5.11-1ubuntu2) ...
Preparing to unpack .../gir1.2-ibus-1.0_1.5.11-1ubuntu2.1_i386.deb ...
Unpacking gir1.2-ibus-1.0:i386 (1.5.11-1ubuntu2.1) over (1.5.11-1ubuntu2) ...
Preparing to unpack .../ibus-gtk_1.5.11-1ubuntu2.1_i386.deb ...
Unpacking ibus-gtk:i386 (1.5.11-1ubuntu2.1) over (1.5.11-1ubuntu2) ...
Preparing to unpack .../ibus-gtk3_1.5.11-1ubuntu2.1_i386.deb ...
Unpacking ibus-gtk3:i386 (1.5.11-1ubuntu2.1) over (1.5.11-1ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for libgtk2.0-0:i386 (2.24.30-1ubuntu1.16.04.2) ...
Processing triggers for libgtk-3-0:i386 (3.18.9-1ubuntu3.3) ...
Setting up snapd (2.32.3.2) ...
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ...
snapd.snap-repair.service is a disabled or a static unit, not starting it.
Setting up ubuntu-core-launcher (2.32.3.2) ...
Setting up libibus-1.0-5:i386 (1.5.11-1ubuntu2.1) ...
Setting up gir1.2-ibus-1.0:i386 (1.5.11-1ubuntu2.1) ...
Setting up ibus (1.5.11-1ubuntu2.1) ...
Setting up ibus-gtk:i386 (1.5.11-1ubuntu2.1) ...
Setting up ibus-gtk3:i386 (1.5.11-1ubuntu2.1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...

```

Have installed sudo apt install xserver-xorg-core ok followed by the synaptics code suggested. Cursor still jumpy, the guide is the little pointers in the Shotwell viewer left panel. It is difficult to place the cursor as is jumps about a quarter inch (6mm) off.

---

### Post by cruzer001 on 2018-04-22
Hello

Google tells me that your not the only one with a jumpy cursor and I have not found good answer for this.  Could be one reason why the x230/230i was never certified.

[https://certification.ubuntu.com/certification/make/Lenovo/?category=Laptop&query=&release=&level=Any&page=3](https://certification.ubuntu.com/certification/make/Lenovo/?category=Laptop&query=&release=&level=Any&page=3)

Now that you have the synaptics driver installed it is possible to tweak your touchpad settings, however I am concern about the bigger picture.  Those packages that you installed are part of the default install, it should not of been necessary to install them.  Makes me wonder if other default packages are missing.  

Since this is a fresh install I think you should explore other options before committing to this 16.04 install.

One suggested touchpad fix is a kernel upgrade.
In a few days 18.04 will be officially released for download, you could download it now and give it a test using the option to try it before installing to your laptop.  This could solve the problem, also...

One link claimed that Ubuntu Mate worked out of the box with the x230i.  I think its also worth a test run.

Ubuntu Mate 18.04 download
32bit
[http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/bionic-desktop-i386.iso](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/bionic-desktop-i386.iso)
64bit
[http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/bionic-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/bionic-desktop-amd64.iso)

Ubuntu 18.04 download
64bit (32bit support has been dropped)
[http://cdimage.ubuntu.com/daily-live/current/bionic-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/bionic-desktop-amd64.iso)

Is there a reason you choose to run 32bit?

---

### Post by pantazi on 2018-04-22
Thanks again for the reply.

Re your suggestion of not committing to this install, I appreciate where you're coming from, but it's taken me a while to get my wife orientated on this (her) notebook and I'm loathed to change at this time. ( From W7 )

I may try 18.04 on my Elitepad and note the changes. Generally I would normally wait a few months for bugs to be ironed out. (edit: as I write this and relaying your suggestions, I received a positive response!)

I was slightly confused re the Ubuntu download page suggesting that the 64bit d/load is for AMD chips only, and if there is an Intel chip, to use 32 bit.

I had Googled extensively before posting and also noted that the 230i notebook has experienced touchpad problems since 12.04 but the bug seems to have been ignored or not fixed.
I'll research the possible kernel upgrade, I've not seen that mentioned before but I'm willing to learn.

I appreciate your taking the time and trouble to post.

Regards

---

### Post by cruzer001 on 2018-04-22
> "AMD64" is the name chosen by AMD for their 64-bit extension to the Intel x86 instruction set. Before release, it was called "x86-64" or "x86_64", and some distributions still use these names. Intel refers to its AMD64 implementation as "?Intel64" previously named "?EM64T". The architecture is AMD64-compatible and Debian AMD64 will run on AMD and Intel processors with 64-bit support. Because of the technology paternity, Debian uses the name "AMD64"

[https://wiki.debian.org/DebianAMD64Faq](https://wiki.debian.org/DebianAMD64Faq)

If your still on 16.04, I now see whats going on with xorg.
What kernel are you currently running?

```
uname -r
```

There are different packages for different kernels that I had forgotten about.  Sorry

---

### Post by pantazi on 2018-04-23
Please don't apologise.

```

4.13.0-38-generic

```

---

### Post by cruzer001 on 2018-04-23
As stated earlier in this thread there are two touchpad drivers.  Try the other one (libinput) and see if it works any better.
```
sudo apt install xserver-xorg-input-libinput-hwe-16.04
```
Remove the current driver(s)
```
sudo apt remove xserver-xorg-core xserver-xorg-input-synaptics xserver-xorg-input-synaptics-hwe-16.04
```
And to be sure everything is now in  order, please post:
```
apt policy xserver-xorg-core* xserver-xorg-input-synaptics*
```
If your touchpad is still not usable it will be time to tweak some settings.

---

### Post by pantazi on 2018-04-23
Entering your first code brings up the following-looks like a no go, should I continue?

```
~$ sudo apt install xserver-xorg-input-libinput-hwe-16.04
[sudo] password for anne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 xserver-xorg-input-libinput-hwe-16.04 : Depends: xorg-input-abi-24
                                         Depends: xserver-xorg-core-hwe-16.04 (>= 2:1.18.99.901) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by cruzer001 on 2018-04-24
> **pantazi said:**
> Entering your first code brings up the following-looks like a no go, should I continue?

Please hold, I will post back with new instructions later.

---

### Post by cruzer001 on 2018-04-24
Ok, lets have a look at everything installed.  In terminal: 
```
sudo apt install pastebinit
```
Next generate a list and send it to pastebin:
```
dpkg --get-selections > installed.txt && cat ~/installed.txt | pastebinit
```
The above command will take a minute and will reply with a link.  Please post that link.

Also post:
```
lsb_release -a && echo $XDG_SESSION_TYPE
```

---

### Post by pantazi on 2018-04-25
Thank you for your time and trouble, it is appreciated.



[http://paste.ubuntu.com/p/t7zDjKtFSF/](http://paste.ubuntu.com/p/t7zDjKtFSF/)

[code]anne@anne-ThinkPad-X230:~$ lsb_release -a && echo $XDG_SESSION_TYPE
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
x11
[code]

---

### Post by cruzer001 on 2018-04-25
Ok, to get back to hwe, in terminal:
```
sudo apt install xserver-xorg-hwe-16.04
```

Now install libinput:
```
sudo apt install xserver-xorg-input-libinput-hwe-16.04
```

Remove synaptics touchpad driver:
```
sudo apt remove xserver-xorg-input-synaptics-hwe-16.04
```

For good measure :)
```
reboot
```

Your now running your touchpad with libinput, try it for a while.  See what you think.  If you wish to switch back to synaptics just install synaptics, it will over ride libinput.
```
sudo apt install xserver-xorg-input-synaptics-hwe-16.04
```

---

### Post by pantazi on 2018-04-26
ok Cruzer did that and the cursor is rock- steady, however the touchpad does not show up in settings thus edge scrolling and tap cannot be set.

Researching, it seems that it maybe libinput is part of Gnome and not fully compatible with Unity.

For now I have re-enabled Synaptics  with it's inherent problem. I may have a crack at 18.04, being Gnome based.

If you've any other thoughts, then I will be grateful. If not, then as previously mentioned, thank you for your efforts, at least I've learned a bit!

---

### Post by cruzer001 on 2018-04-26
> **pantazi said:**
> it seems that it maybe libinput is part of Gnome and not fully compatible with Unity.  I may have a crack at 18.04, being Gnome based.

You are running Gnome with he Unity interface :)

A suggestion
Ubuntu Mate 18.04 has a Unity theme that I think your wife would be happy with.  Its a good match with what your currently running, and comes with libinput.  Good chance it will work out of the box.

---

### Post by pantazi on 2018-04-27
Ah, got it now thank you.:D

Will check out Mate and the latest Bionic Beaver.

---

### Post by pantazi on 2018-05-03
Not wishing to be beaten with this problem, I began again from #15 as suggested by Cruzer and followed up with the info found at:

[https://askubuntu.com/questions/949323/restore-natural-scrolling-in-ubuntu-16-04-on-dell-xps-13](https://askubuntu.com/questions/949323/restore-natural-scrolling-in-ubuntu-16-04-on-dell-xps-13).

I followed the instructions until I reached the same point as 'the section should look this way'



The post said reboot, but that had no effect, I guess that as the text editor is read only that is to be expected, so how do I proceed from here?

Ah, do I need to copy the revised text and paste into xorg.conf.d and reboot?

---

### Post by pantazi on 2018-05-05
Am I on the right track?

---

### Post by pantazi on 2018-05-11
Anyone, please? Just don't wish to mess it up!

---

