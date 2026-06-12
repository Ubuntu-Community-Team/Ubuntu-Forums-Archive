---
title: "[SOLVED] Installing a Wireless Card Driver in a Ndiswrapper"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by getitright on 2008-09-22
I am attempting an installation of a XP driver for a wireless card in an ndiswrapper, on a laptop. I have used ndistgk for this.

Inputting the command line

'ndiswrapper -l'

returns the information that the Driver had been installed OK. I then proceeded to load the module using command lines:

'sudo depmode -a

sudo modprobe ndiswrapper'

and got the display 'FATAL. Module ndiswrapper not found'

Can anyone help me please?

---

### Post by NullHead on 2008-09-22
I'd remove your .inf file, sudo ndiswrapper -r <driver>, and install it again. If that fails, look for ndiswrapper, lsmod | grep ndiswrapper. If ndiswrapper don't show up ... uninstall ndiswrapper from synaptic, and download the source, compile, install it. 

You'll need to install build-essential to compile ndiswrapper. When you get it downloaded, extract it, move into ndiswrappers directory, and run "make" and once that's done, run "sudo make install" 

Then proceed with your regular ndiswrapper setup; install drivers.

Their website seems to be down atm ... [here](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=602481) is there download page though. At least that works.

---

### Post by timcredible on 2008-09-22
did you try using the gui?  system->administration->windows wireless drivers

---

### Post by getitright on 2008-09-22
Thanks NullHead. What are the command lines for your suggested actions?

---

### Post by knix on 2008-09-22
> **getitright said:**
> Thanks NullHead. What are the command lines for your suggested actions?

I haven't been able to access ndiswrapper's website (ndiswrapper.sourceforge.net), but here's the ubuntu tarball.[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper_1.50.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper_1.50.orig.tar.gz")

You can use ```
wget http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper_1.50.orig.tar.gz
```

then tar -xjvf ndiswrapper*.tar.gz```

```

then ```
cd ndiswrapper*
```

than ```
make
```

then ```
sudo make install
```

From my experience, you can just leave the preinstalled drivers, you just need a kernel module.

If not, before compiling ndiswrapper as above,

```
sudo ndiswrapper -r bcmwl5
``` (or whatever)

```
sudo dpkg -r ndiswrapper-common ndiswrapper-utils-1.9
```

Now compile ndiswrapper

now install drivers with ```
sudo ndiswrapper -i bcmwl5.inf
``` (or whatever.inf)

```
ndiswrapper -l
```

just in case: ```
sudo ndiswrapper -m
```

sud modprobe ndiswrapper (you should reboot first)

---

### Post by anewguy on 2008-09-22
Both ndiswrapper packages are on the installation CD in /pool/main/n/ and can be installed from there by simply double-clicking on each file name - there is no need to compile ndiswrapper from source.  Additionally, the ndiswrapper -m is supposed to put the entry in /etc/modules so at boot the ndiswrapper kernel module is automatically loaded.  unfortunately, that doesn't always seem to work.  It is advised to 

sudo gedit /etc/modules

Check to see if ndiswrapper shows on a line by itself in that file - if not, add a line to the end that simply says ndiswrapper.  Then save the file, exit the editor and reboot (so that you can be sure the modules in /etc/modules really get loaded at boot).

EDIT:  forgot to mention 2 other things:  Depending on the given wireless, it may be necessary to edit the /etc/modprobe.d/blacklist file and blacklist the default Ubuntu driver.  For example. using the bcmwl5.inf as mentioned in the previous post - that is the name normally associated with Broadcom wireless chipsets.  If you load a driver via ndiswrapper for these, then you need to black list bcm43xx (there might even be another one something like B43) otherwise the driver still won't work.

dave :)

---

### Post by NullHead on 2008-09-22
> **anewguy said:**
> Both ndiswrapper packages are on the installation CD in /pool/main/n/ and can be installed from there by simply double-clicking on each file name - there is no need to compile ndiswrapper from source.  Additionally, the ndiswrapper -m is supposed to put the entry in /etc/modules so at boot the ndiswrapper kernel module is automatically loaded.  unfortunately, that doesn't always seem to work.  It is advised to 

sudo gedit /etc/modules

Check to see if ndiswrapper shows on a line by itself in that file - if not, add a line to the end that simply says ndiswrapper.  Then save the file, exit the editor and reboot (so that you can be sure the modules in /etc/modules really get loaded at boot).

EDIT:  forgot to mention 2 other things:  Depending on the given wireless, it may be necessary to edit the /etc/modprobe.d/blacklist file and blacklist the default Ubuntu driver.  For example. using the bcmwl5.inf as mentioned in the previous post - that is the name normally associated with Broadcom wireless chipsets.  If you load a driver via ndiswrapper for these, then you need to black list bcm43xx (there might even be another one something like B43) otherwise the driver still won't work.

dave :)

ndiswrapper -m is deprecated and is no longer needed. You simply add ndiswrapper to modules if ndiswrapper fails to load automatically. 

The OP's problem, it seems to me, is that the ndiswrapper debs somehow got broke. I'd suggest using the debs, but apparently they're already installed, but simply not working. 

Anyhow, getitright, knix has posted the right instructions, but I'd use the newest tarball. You can download it off of my server, here: [http://wopr.ath.cx/files](http://wopr.ath.cx/files)

---

### Post by anewguy on 2008-09-23
Hence why I mentioned it - it was not mentioned in the preceeding post.  Also, there should be no need to compile ndiswrapper - simply remove it then add it again via the installation CD.  You can explore that CD and simply double-click each of the 2 files for ndiswrapper and it will reinstall.  This looks identical to another post which I answered on the weekend, so I'm thinking it's either the same person using a different username, or else some problem has cropped up.  Since 8.04 has been out for quite a while, and I've had others install/reinstall ndiswrapper from the livecd, I would doubt it's some problem that has just cropped up, but you never know.  I would like to see a copy/paste of the terminal window when this happens to know for sure.

Regardless, the blacklisting is also needed if it is one of the Broadcom chipsets as indicated by the name of the .inf file used in the preceeding post.

Dave :)

---

### Post by getitright on 2008-09-23
I have been unsuccessful in installing build essential. I used the command line:

'sudo apt-get install build-essential'

from disc source.

After set up I am given the resources to be used and asked if I wish to proceed with installation Y/n. Entering Y and get:

'Media Change: Please insert the disc labelled 'Ubuntu 8.04 Hardy Heron -release i386 (20080423)' in the drive'cdrom/' and press enter'

When I do as requested I just get the above message again.

What am I doing wrong?

---

### Post by NullHead on 2008-09-23
Try anewguy's suggestion first.

---

### Post by getitright on 2008-09-23
I have done what anewguy suggested. I have uninstalled and then reinstalled ndiswrapper. Have ensured that there is a file 'ndiswrapper' in /etc/modules. Checked thaat the card is seen in ndiswrapper -l, still does not work. I will go away and have a quiet mental breakdown.

---

### Post by anewguy on 2008-09-23
When you uninstall ndiswrapper, be sure to use the "purge" option if using apt-get or the "mark for complete removal" option if using Synaptic package manager.  The packages are cached, so you want to be sure you completely remove any of the old package before going with the install.  So, here is what I'd like you to try 1 more time:

(1) completely remove ndiswrapper - copy and paste the output from that back in a reply here

(2) install ndiswrapper from the livecd, but don't try any command line with it yet

(3) do the command line stuff for ndiswrapper (the list, the removal of any existing drivers, the load, the sudo depmod -a, the modprobe of ndiswrapper, etc., up to your failure) - copy and paste the output from that back into the same reply as (1)

Also, there is a package called ndisgtk that is a gui'd front end to ndiswrapper so you don't have to use the command line.  You may want to try downloading, installing and trying it.  Some people have better luck with it than they do the command line.  If needed, I could see if I can attach a copy of it to a post here if you are unable to download it.

EDIT: I see in reviewing the post you originally used ndisgtk.  

Dave :)

---

### Post by anewguy on 2008-09-23
BTW - something I never saw mentioned is what wireless card/chipset we are dealing with for sure.  So, please also post the output of "lspci" back here as well.

Dave :)

EDIT:  In reviewing your original thread before you opened this duplicate, you are making at least 1 error:

it's not "sudo depmode -a"

but "sudo depmod -a"

Also, I wouldn't mix ndisgtk and command line ndiswrapper.  While ndisgtk is the graphical front-end to ndiswrapper, I'm not sure what it does/doesn't do for you.  So, either go all ndisgtk, or go all command line.  If going all command line, do the following:

(1) Be sure ndiswrapper is installed

(2) Get your Windows XP (not Vista) driver for your wireless card.  "Unpack" it if necessary and place the files in a subfolder called wireless.

(3) Open up a terminal window

(4) cd wireless

(5) sudo ndiswrapper -l <enter> That's a lower case "L" for "List"

(6) for each driver returned in (5):

sudo ndiswrapper -e xxxxxx <enter> where xxxxxx is the driver name returned in (5)

repeat (5) and (6) until an empty list is returned

(7) sudo ndiswrapper -i xxxxxx.inf <enter> where xxxxxx is the name of the correct .inf file, the driver for your wireless.  If you select the incorrect .inf, the wireless probably will not work.

(8) sudo ndiswrapper -l <enter> List again, to be sure it shows your driver and does not show any errors associated with it

(9) sudo depmod -a

(11) sudo modprobe ndiswrapper

(12) copy/paste the terminal window showing all of the above into a text file in case we ask you to post it back here.

(13) you have already added the line "ndiswrapper" to the end of the /etc/modules file.

(14) REBOOT.

After reboot, click on your network manager icon and see if it shows any wireless networks.  Be sure roaming is enabled under system/administration/network.  If your router is set to not broadcast the network name, it will not show in network manager - you must select the "Connect to Other Wireless Network" option and manually enter in the network name and associated data such as wep or wpa information if used.

Dave

---

### Post by getitright on 2008-09-23
anewguy, this is the inf. you requested in #12.

1. Completely removed ndiswrapper using Synaptic using"mark for complete removal". There did not appear to be any pastable output, just a statement that the uninstall was complete.

2. Reinstalled ndiswrapper from livecd by double clicking on folders. Reinstalled ndistgk at the same time.

3. Doing the command line stuff this is what I got:

mary@mary-laptop:~$ ndiswrapper -l 
neti2220 : driver installed 
	device (17FE:2220) present 
mary@mary-laptop:~$ sudo depmod -a
[sudo] password for mary: 
mary@mary-laptop:~$ sudo modprobe ndiswrapper 
FATAL: Module ndiswrapper not found. 

I have done gedit /etc/modules and confirm that ndiswrapper is listed.


Just noticed #13, will give this my attention now.

---

### Post by anewguy on 2008-09-23
Strange.....could you post the output of lspci back here so we can see that?

Did you check the checksum, etc., after burning the livecd to be sure it matched okay?

If you use ndiswrapper to remove your driver, then use ndisgtk to set it up and not do anymore in the command line, just ndisgtk, what happens?

---

### Post by getitright on 2008-09-24
anewguy, this is the response to #13.

lspci yields:

mary@mary-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02) 
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge 
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) 
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) 
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) 
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 1a) 
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller 
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c 
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01) 
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) 
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] 
02:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) 
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01) 
mary@mary-laptop:~$ 


Installing driver (Files unpacked to Desktop) yields:

mary@mary-laptop:~$ cd Desktop 
mary@mary-laptop:~/Desktop$ sudo ndiswrapper -l 
[sudo] password for mary: 
neti2220 : driver installed 
	device (17FE:2220) present 
mary@mary-laptop:~/Desktop$ sudo ndiswrapper -e neti2220 
mary@mary-laptop:~/Desktop$ sudo ndiswrapper -l 
mary@mary-laptop:~/Desktop$ 
mary@mary-laptop:~/Desktop$  sudo ndiswrapper -l 
mary@mary-laptop:~/Desktop$ sudo ndiswrapper -i neti2220.inf 
couldn't open neti2220.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
mary@mary-laptop:~/Desktop$ 

Should I still go ahead as suggested in #15?

---

### Post by anewguy on 2008-09-24
> 
mary@mary-laptop:~/Desktop$  sudo ndiswrapper -l 
mary@mary-laptop:~/Desktop$ sudo ndiswrapper -i neti2220.inf 
couldn't open neti2220.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
mary@mary-laptop:~/Desktop$ 

Should I still go ahead as suggested in #15?

The error is saying it can't find the neti2220.inf file in your current directory (which according to what you have copied is your desktop).  List your desktop to be sure that file exist - in fact, post back a copy/paste of:

cd ~/Desktop
ls -al net*.*

dave :)

---

### Post by getitright on 2008-09-24
Hi anewguy.

I have resolved my problem.

What I did was pretty drastic.

1. Reinstalled Ubuntu 8.04. The reasoning was that having tried everything else the problem could have been caused by a corrupted Ubuntu file.

2. Reinstalled ndiswrapper and ndistgk by double clicking the appropriate folders on the installation disc.

3. Installed the wi-fi driver using ndistgk.

My sincere thanks to you and everyone else who gave me great advice. I have learned a lot of good things from all of you.

---

### Post by anewguy on 2008-09-24
I'm glad you got your problem resolved.  Sorry you had to "start from scratch" but if it helps any you are far from alone! :)

I think what probably caused this was a result of the things people were trying to have you do in your other thread about the same subject.  Somewhere in downloading the ndiswrapper source, trying to compile it, etc., I suspect it "hosed something up" and trying to reverse what was done there was a near impossibility.

If you could, please use the "Thread Tools" option on this thread and mark it as "Solved".

Hope you enjoy Ubuntu!!

Dave :)

---

