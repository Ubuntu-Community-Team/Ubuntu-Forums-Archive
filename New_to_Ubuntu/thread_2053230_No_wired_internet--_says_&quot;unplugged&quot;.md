---
title: "No wired internet-- says &quot;unplugged&quot;"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by PieEconomics on 2012-09-04
My wired internet does not work in Ubuntu even though it works in windows 7 in the same computer. I used the windows downloader to install Ubuntu. Ubuntu does list the correct MAC address: 90:FB:A6:E2:2A:CD (eth0). But it says the wired internet is unplugged. My Acer computer has a Realtek RTL8168C(P) Family PCI-E Gigabit ethernet NIC (NDIS 6.20). I entered lspci at the terminal; the last line of output did mention my Realtek network card.

Are there any simple steps for getting my wired connection?

---

### Post by PieEconomics on 2012-09-05
-

---

### Post by The Cog on 2012-09-05
Try physically turning the machine off and on again and make sure you boot straight into Ubuntu. I have seen in the past (can't remember which make adapter) a problem where each OS left the hardware in a state where the other OS couldn't initialise the card properly without a full power-down.

Another test - use the command ifconfig and look at the state of eth0. Look for the word "RUNNING". If that's not there, then the driver things there is no cable plugged in. I know this is what network manager says, but I prefer to look "underneath" gui programs when things aren't working right.

---

### Post by PieEconomics on 2012-09-05
"Try physically turning the machine off and on again..." No change.

ifconfig readout:

eth0 Link encap; Ethernet HWaddr 90:fb:ab:e2:2a:cd
UP BROADCAST MULTICAST MTU:1500 metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0(0.0B) TX bytes:0(0.0B)
Interrupt:42

lo Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0(0.0B) TX bytes:0(0.0B)

BTW: My router is an Actiontec MI1424WR.
Should I repower the router while Ubuntu is running? If I do this, do I risk losing wired internet for when I switch back to windows 7?

---

### Post by The Cog on 2012-09-05
That has reached the end of my knowledge. eth0 shows UP which means it is administrationally up - trying to work. But it is not RUNNING, which I have only ever seen when the cable is not connected. Sorry, I don't know what to do from here on. 

P.S. I found this:
[http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

---

### Post by PieEconomics on 2012-09-05
This is known bug #998200, in Ubuntu 12.04, for anyone who has a Realtek RTL8168 network card. Ubuntu erroneously includes the RTL8169 driver instead, which causes wired internet to act as if unplugged.

The fix is to install the correct RTL8168 driver in Ubuntu's Linux kernel.

I am told the correct driver can be installed with this terminal command: sudo apt-get install linux-backports-modules-net-oneiric-generic

I entered that command at the terminal, but the output was that the module referenced cannot be located.

How do I download "linux-backports-modules-net-oneiric-generic"?

If I download it using windows 7, how will Ubuntu find it?

---

### Post by The Cog on 2012-09-05
If you can download the .deb file of this package and copy it to the ubuntu machine (e.g. by USB stick), then just double-clicking the file or opening it with gdebi should bring up an installer dialog for it.

---

### Post by gandaran on 2012-09-05
> **PieEconomics said:**
> This is known bug #998200, in Ubuntu 12.04, for anyone who has a Realtek RTL8168 network card. Ubuntu erroneously includes the RTL8169 driver instead, which causes wired internet to act as if unplugged.

The fix is to install the correct RTL8168 driver in Ubuntu's Linux kernel.

I am told the correct driver can be installed with this terminal command: sudo apt-get install linux-backports-modules-net-oneiric-generic

I entered that command at the terminal, but the output was that the module referenced cannot be located.

How do I download "linux-backports-modules-net-oneiric-generic"?

If I download it using windows 7, how will Ubuntu find it?
this package will not work for ubuntu 12.04, you will have to get the exact matching package for the kernel you are using, the easy way to install was from software center if you have an internet connection maybe wireless.
but if you go to [ubuntu packages 12.04]("http://packages.ubuntu.com/precise/allpackages") and find the matching package (scroll down to linux-backports-modules-net) then just download the .deb file and transfer the file to ubuntu to install with a double click, it should be easy but take into account you need the exact file as you will see there are a lot linux-backports-modules-net files there and ubuntu 12.04 uses the generic-pae kernel now not generic.

---

### Post by NikTh on 2012-09-05
> **PieEconomics said:**
> This is known bug #998200, in Ubuntu 12.04, for anyone who has a Realtek RTL8168 network card. Ubuntu erroneously includes the RTL8169 driver instead, which causes wired internet to act as if unplugged.

The fix is to install the correct RTL8168 driver in Ubuntu's Linux kernel.



Hello , 

what version of Ubuntu you use ? 

In 56th comment on the bug you mentioned is says that the package installed and worked is one from Quantal (12.10). This : [https://launchpad.net/ubuntu/quantal/+package/r8168-dkms](https://launchpad.net/ubuntu/quantal/+package/r8168-dkms)

Here is the comment : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998200/comments/56](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998200/comments/56)

Thanks

---

### Post by dr1094 on 2012-09-05
1. I had a similar problem with my Toshiba laptop, here's how I fixed it. At first I figured out that I hadn't plugged in the ethernet cable all the way in from the router connection (yeah, i'm still a noob). 

2. The I clicked the button that shows the wifi or ethernet connection at near top right (beside the speaker button). Disable wireless, and then disable networking. 

(Make sure the cable is connected as you are doing these.) 

3. Then enable Networking (but NOT wireless). If the arrows pointing up and down appear within 15 seconds you got a connection.

4. If it's still not connecting... log out, while the wire is still connected to your machine. and then log back in after 15 seconds.

5. If still not working, leave the wire plugged in and restart your computer (remember the enable wireless button should not be ticked, but enable networking should be ticked, after the initial connection success, you can re-enable wireless.)

I had it working for me by step 4. I hope this helps,

cheers.

---

### Post by PieEconomics on 2012-09-05
[COLOR="Blue"]Which of these 13 packages should I download[/COLOR] (from Ubuntu's download website: packages.ubuntu.com/precise/allpackages)?

(1)linux-backports-modules-net-3.2.0-24-generic (3.2.0-24.8*) [security] Linux ethernet modules for version 3.2.0 on x86/x86_64

(2)linux-backports-modules-net-3.2.0-24-generic-pae (3.2.0-24.8*) [security] Linux ethernet modules for version 3.2.0 on x86

(3)linux-backports-modules-net-3.2.0-25-generic (3.2.0-25.10) [security] Linux ethernet modules for version 3.2.0 on x86/x86_64

(4)linux-backports-modules-net-3.2.0-25-generic-pae (3.2.0-25.10) [security] Linux ethernet modules for version 3.2.0 on x86

(5)linux-backports-modules-net-3.2.0-26-generic (3.2.0-26.11) [security] Linux ethernet modules for version 3.2.0 on x86/x86_64

(6)linux-backports-modules-net-3.2.0-26-generic-pae (3.2.0-26.11) [security] Linux ethernet modules for version 3.2.0 on x86

(7)linux-backports-modules-net-3.2.0-27-generic (3.2.0-27.12) [security] Linux ethernet modules for version 3.2.0 on x86/x86_64

(8*)linux-backports-modules-net-3.2.0-27-generic-pae (3.2.0-27.12) [security] Linux ethernet modules for version 3.2.0 on x86

(9)linux-backports-modules-net-3.2.0-29-generic (3.2.0-29.14) [security] Linux ethernet modules for version 3.2.0 on x86/x86_64

(10)linux-backports-modules-net-3.2.0-29-generic-pae (3.2.0-29.14) [security] Linux ethernet modules for version 3.2.0 on x86

(11)linux-backports-modules-net-precise-generic (3.2.0.29.31) [security] Backported ethernet drivers for generic kernel image.

(12)linux-backports-modules-net-precise-generic-pae (3.2.0.29.31) [security] Backported ethernet drivers for generic kernel image.

(13)linux-backports-modules-net-precise-server (3.2.0.29.31) [security] Backported ethernet drivers for generic kernel image.

Here are my system settings: ubuntu 12.04 LTS; Processor AMD Athlon(tm)11X2 215 Processor x2: OS type 64-bit.

When I double clicked a DEB file in the USB drive, [COLOR="Blue"]the Ubuntu Software Center opened, and it displayed the file, but the install button on the file's page was greyed out and inoperable[/COLOR].

If and when the Ubuntu Software Center makes the install button operable, and I can install the driver, [COLOR="Blue"]do I still have to enter the command: sudo apt-get install linux-backports-modules-net-[...][/COLOR]?

(*Disregard the "*". The number eight with ")" after it is a shortcut for a face, in this forum.)

---

### Post by gandaran on 2012-09-05
it's probably number 2
```
linux-backports-modules-net-3.2.0-24-generic-pae
```
because if you haven't updated your system yet you'll be running the 3.2.0-24 kernel or maybe not.
to find the kernel version type in terminal
```
uname -a
```
if you had internet you would use this one instead
```
linux-backports-modules-net-precise-generic-pae 
```
this is an empty package that would install the right package for the kernel and keep it updated for every new kernel.
> When I double clicked a DEB file in the USB drive, the Ubuntu Software Center opened, and it displayed the file, but the install button on the file's page was greyed out and inoperable.
well this can be a problem, if software center wont install the .deb try asking for help on a new thread but try coping the file first from usb drive to ubuntu home directory or desktop then try install.
> If and when the Ubuntu Software Center makes the install button operable, and I can install the driver, do I still have to enter the command: sudo apt-get install linux-backports-modules-net-[...]?
no, **sudo apt-get install** is for installing packages from command line after you have internet working.
software center should install the .deb packages without running any command but if this package does fix the internet problem you will want to install the empty linux-backports-modules-net-precise-generic-pae package either from command line or ubuntu software center to avoid problems with kernels updates.

---

### Post by PieEconomics on 2012-09-06
My version of Ubuntu:
~$ uname -a 
Linux ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

So, we can narrow down to l of these 5 choices:

(9)linux-backports-modules-net-3.2.0-29-generic (3.2.0-29.14) [security] Linux ethernet modules for version 3.2.0 on x86/x86_64

(10)linux-backports-modules-net-3.2.0-29-generic-pae (3.2.0-29.14) [security] Linux ethernet modules for version 3.2.0 on x86

(11)linux-backports-modules-net-precise-generic (3.2.0.29.31) [security] Backported ethernet drivers for generic kernel image.

(12)linux-backports-modules-net-precise-generic-pae (3.2.0.29.31) [security] Backported ethernet drivers for generic kernel image.

(13)linux-backports-modules-net-precise-server (3.2.0.29.31) [security] Backported ethernet drivers for generic kernel image.

Note that my Ubuntu operating system type is 64 bit. Why does driver #9 (generic) mention 64, as in 64 bit, while driver #10 (generic-pae) does not? Even though I am 64 bit, do you still recommend the pae driver? Also, what are the "precise" drivers #11, #12, and #13 for-- they wouldn't be the right ones?

Even moving the DEB file from the USB drive to the desktop did not allow the install button to become ungreyed on the installer program.* Should I get on the terminal, using the # prompt rather than the $ prompt to force the installer to allow installation of the correct DEB file? The drivers (as DEB files) are located on my ubuntu desktop. [COLOR="Blue"]What is an exact script I can enter into the terminal to force installation?[/COLOR]

*This notice appeared near the greyed out install button: "You likely do not want to install this package directly. Instead, install the unix-backports-modules-net-generic-pae metapackage, which will ensure that upgrades work correctly, and that supporting packages are also installed. Dependency is not satisfiable: linux-image-3.2.0-generic-pae."

---

### Post by gandaran on 2012-09-06
> Linux ubuntu  3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
so your ubuntu is fully updated? how did you do it? you must have had internet!
well the 64-bits is using the generic kernel version (not pae) of the driver that's the one you have to choose (3.2.0-29) and ensure you are downloading 64-bits version.
> Also, what are the "precise" drivers #11, #12, and #13 for-- they wouldn't be the right ones?

number 11 would be the correct one and would save you all this trouble just by install with this one command, don't need anything else, it will take care to install the right drivers for the kernel.
```
sudo apt-get install linux-backports-modules-net-precise-generic
```
you must have working internet to run the command.
> *This notice appeared near the greyed out install button: "You likely do not want to install this package directly. Instead, install the unix-backports-modules-net-generic-pae metapackage, which will ensure that upgrades work correctly, and that supporting packages are also installed. Dependency is not satisfiable: linux-image-3.2.0-generic-pae."
you are forcing the pae kernel for 32-bits, try with the right packages, post any errors

---

### Post by PieEconomics on 2012-09-06
No, my Ubuntu has not been updated and my wired internet still does not work in Ubuntu.(BTW, my computer has wired internet only; it does not have a wireless internet card.)

I only installed Ubuntu a few days ago (using the windows installer), so this reflects only that original installation: Linux ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux.

(I downloaded the DEB files using windows 7, transferred them to the USB drive, and moved them to the Ubuntu desktop.)

---

### Post by gandaran on 2012-09-07
> **PieEconomics said:**
> No, my Ubuntu has not been updated and my wired internet still does not work in Ubuntu.(BTW, my computer has wired internet only; it does not have a wireless internet card.)

I only installed Ubuntu a few days ago (using the windows installer), so this reflects only that original installation: Linux ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux.

(I downloaded the DEB files using windows 7, transferred them to the USB drive, and moved them to the Ubuntu desktop.)
is the problem fixed now? did software center install the linux-backports-modules-net-3.2.0-29-generic.deb?

---

### Post by PieEconomics on 2012-09-07
Software center did not install that module, nor any of the other modules. The latest message when I double clicked the file, was: "Only install if you trust the source", but the install button was still greyed out, and nothing happened when I clicked it.

I guess I'll just have to wait until they fix it in a future release of the overall Ubuntu program. I believe I'll be able to delete the program within windows "add or remove programs", but I hope it doesn't mess up the boot next time I turn on the computer. Anyone know if I can just overwrite the old installation using a later Wubi installation?

---

### Post by Carl.Spackler on 2012-09-07
I may be able to offer another possible way to resolve. Although it is not really overly simple. I have put together a script from reading on this issue that I used to fix my LAN connection with the same exact issue. It handles most everything aside from downloading a few files. _If you are not comfortable with the command line, please do not attempt this_.

You will need the 'build-essential' package installed your system.

```
sudo dpkg -l build-essential
```


You will need the Realtek Ethernet driver for Linux here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")

Just download it from any of the US links on the same line as "LINUX driver for kernel 3.x and 2.6.x and 2.4.x"

Here is a copy of the script I used to build and install the correct module for the r8168. Copy it out and save it in a file. Change the file permissions to execute (chmod a+x). Run this from the same directory where you have saved the file you downloaded from Realtek.

```
#!/bin/bash
tar -xvjf ./r8168-8.032.00.tar.bz2
cd r8168*
make modules
sudo cp ./src/r8168.ko /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8169.ko.old
sudo depmod -a
sudo sh -c "echo 'r8168' >> /etc/modules"
sudo sh -c "echo 'blacklist r8169' >> /etc/modprobe.d/blacklist.conf"
sudo sh -c "rmmod r8169"
sudo sh -c "modprobe r8168"
cd ..
rm -Rf r8168-8.032.00
```

---

### Post by gandaran on 2012-09-08
> **PieEconomics said:**
> Software center did not install that module, nor any of the other modules. The latest message when I double clicked the file, was: "Only install if you trust the source", but the install button was still greyed out, and nothing happened when I clicked it.

I guess I'll just have to wait until they fix it in a future release of the overall Ubuntu program. I believe I'll be able to delete the program within windows "add or remove programs", but I hope it doesn't mess up the boot next time I turn on the computer. Anyone know if I can just overwrite the old installation using a later Wubi installation?
then try the terminal command line to install the .deb
```
sudo dpkg -i [COLOR="Blue"]full_package_name[/COLOR].deb
```
to make things simple and to avoid using the cd command move the .deb to home user directory and the package name must match or use this trick type only **sudo dpkg -i** then drag and drop the .deb file inside terminal.
I believe the matching kernel driver package is this one linux-backports-modules-net-3.2.0-29-generic, this is the only package you will be able to install any other that is not matching will require the install of dependencies first.
if any errors installing post them.
[http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/](http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/)

---

### Post by gandaran on 2012-09-08
> **Carl.Spackler said:**
> I may be able to offer another possible way to resolve. Although it is not really overly simple. I have put together a script from reading on this issue that I used to fix my LAN connection with the same exact issue. It handles most everything aside from downloading a few files. _If you are not comfortable with the command line, please do not attempt this_.

You will need the 'build-essential' package installed your system.

```
sudo dpkg -l build-essential
```


You will need the Realtek Ethernet driver for Linux here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")

Just download it from any of the US links on the same line as "LINUX driver for kernel 3.x and 2.6.x and 2.4.x"

Here is a copy of the script I used to build and install the correct module for the r8168. Copy it out and save it in a file. Change the file permissions to execute (chmod a+x). Run this from the same directory where you have saved the file you downloaded from Realtek.

```
#!/bin/bash
tar -xvjf ./r8168-8.032.00.tar.bz2
cd r8168*
make modules
sudo cp ./src/r8168.ko /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8169.ko.old
sudo depmod -a
sudo sh -c "echo 'r8168' >> /etc/modules"
sudo sh -c "echo 'blacklist r8169' >> /etc/modprobe.d/blacklist.conf"
sudo sh -c "rmmod r8169"
sudo sh -c "modprobe r8168"
cd ..
rm -Rf r8168-8.032.00
```
the problem here for the OP is that  'build-essential' package in not installed on the system, to install without working internet would be a nightmare to get/download and install all the dependencies.
 
however looking at your script and the realtek driver package install instructions I'm not sure the compiling tools from 'build-essential' are required so it may work without build-essential but I don't know really.

---

### Post by PieEconomics on 2012-09-08
While I still can't get wired internet, the package...

linux-backports-modules-net-3.2.0-29-generic.deb

...did successfully install.

I know this because when I tried to install it a second time, I was taken to software-center where it displayed a page for that package, with the word "installed" together with a green check mark.

But on the same page (as before), this warning appeared: "You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

I believe meta-packages, like build-essential, require internet access from within Ubuntu to install.

Should I next try Carl Spackler's script?

Should I skip...

sudo dpkg -l build-essential

...since it won't work without internet access from within Ubuntu? Carl, did you have wireless access from within Ubuntu when you ran that command?

Also, please re-post your script showing exactly where this line of code goes: chmod a+x

---

### Post by gandaran on 2012-09-08
> **PieEconomics said:**
> While I still can't get wired internet, the package...

linux-backports-modules-net-3.2.0-29-generic.deb

...did successfully install.

I know this because when I tried to install it a second time, I was taken to software-center where it displayed a page for that package, with the word "installed" together with a green check mark.

But on the same page (as before), this warning appeared: "You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

I believe meta-packages, like build-essential, require internet access from within Ubuntu to install.

Should I next try Carl Spackler's script?

Should I skip...

sudo dpkg -l build-essential

...since it won't work without internet access from within Ubuntu? Carl, did you have wireless access from within Ubuntu when you ran that command?

Also, please re-post your script showing exactly where this line of code goes: chmod a+x
did you reboot to load the driver?
or maybe you have to blacklist the r8169 module
post the output of **lsmod** command to check what modules are loaded 
and don't try any other method until we run out of options with this one, I knew you could install the package but I don't know what drivers are included or  even if it will fix the problem, we'll see.
also ensure on the panel network icon that network is enabled.

and the output of this one too
```
sudo lshw -C network
```

---

### Post by PieEconomics on 2012-09-08
$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
psmouse                87692  0 
serio_raw              13211  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
k10temp                13166  0 
sp5100_tco             13791  0 
snd_hda_codec_hdmi     32474  1 
i2c_piix4              13301  0 
radeon                804372  3 
snd_hda_codec_realtek   224066  1 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
wmi                    19256  0
mac_hid                13253  0
snd_hda_intel          33773  4
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_algo_bit           13423  1 radeon
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37277  0 
r8169                  62099  0 
usb_storage            49198  1 

sudo -c network
usage: sudo [-D level] -h | -K | -k | -V 
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user             name|#uid] 
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user             name] [-u user name|#uid] [-g groupname|#gid] [command] 
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u             user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>] 
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u             user name|#uid] file ...

---

### Post by gandaran on 2012-09-08
> r8169 62099 0 
its still r8169 but before removing this module I would like the output of
```
sudo lshw -C network
```
copy and paste to avoid errors

---

### Post by PieEconomics on 2012-09-08
$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 90:fb:a6:e2:2a:cd
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff

---

### Post by gandaran on 2012-09-08
> configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/[COLOR="Red"]rtl8168e-2[/COLOR].fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
okay try this
```
sudo rmmod r8169
```
then
```
sudo modprobe r8168 
```
or maybe it should be [COLOR="Red"]rtl8168[/COLOR] try both options if the other didn't work.
after running the commands check if internet is enabled and working, don't reboot, if not working try checking with **lsmod** command if r8169 was removed and r8168 loaded.
if this works then we will make it permanent blacklisting the driver, if not then I cant help further.
good luck

edit:
post the output of
```
dmesg | grep 81
```
I think this will show if any other driver besides r8169 is really available.

---

### Post by PieEconomics on 2012-09-08
$ sudo modprobe r8168 
FATAL: Module r8168 not found. 

$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12713  1  
nls_cp437              16991  1  
vfat                   17585  1  
fat                    61512  1 vfat 
rfcomm                 47604  0  
bnep                   18281  2  
parport_pc             32866  0  
bluetooth             180104  10 rfcomm,bnep 
ppdev                  17113  0  
lp                     17799  0  
parport                46562  3 parport_pc,ppdev,lp 
radeon                804372  3  
ttm                    76949  1 radeon 
snd_hda_codec_hdmi     32474  1  
psmouse                87692  0  
serio_raw              13211  0  
drm_kms_helper         46978  1 radeon 
drm                   242038  5 radeon,ttm,drm_kms_helper 
snd_hda_codec_realtek   224066  1  
wmi                    19256  0  
snd_seq_midi           13324  0  
snd_rawmidi            30748  1 snd_seq_midi 
snd_hda_intel          33773  4  
i2c_algo_bit           13423  1 radeon 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13668  1 snd_hda_codec 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi_event     14899  1 snd_seq_midi 
mac_hid                13253  0  
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event 
k10temp                13166  0  
snd_timer              29990  2 snd_pcm,snd_seq 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    78855  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device 
sp5100_tco             13791  0  
edac_core              53746  0  
edac_mce_amd           23709  0  
shpchp                 37277  0  
i2c_piix4              13301  0  
soundcore              15091  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
usb_storage            49198  1  

---------------
Comparing to the last four lines of the old lsmod...

snd_page_alloc 18529 2 snd_hda_intel,snd_pcm
shpchp 37277 0 [COLOR="Blue"]<---now gone[/COLOR]
r8169 62099 0 [COLOR="Blue"]<---now gone[/COLOR]
usb_storage 49198 1 
---------------

$ dmesg | grep 81
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011fc00000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.149481] PM: Registering ACPI NVS region at cf79e000 (270336 bytes)
[    0.149481] print_constraints: dummy: 
[    0.149481] RTC time: 20:26:15, date: 09/08/12
[    0.149481] NET: Registered protocol family 16
[    0.149481] node 0 link 0: io port [1000, ffffff]
[    0.149481] TOM: 00000000d0000000 aka 3328M
[    0.149481] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.149481] node 0 link 0: mmio [a0000, bffff]
[    0.149481] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.149481] node 0 link 0: mmio [f0000000, fe7fffff]
[    0.149481] node 0 link 0: mmio [fe800000, fe9fffff]
[    0.149481] node 0 link 0: mmio [fea00000, ffefffff]
[    0.149481] TOM2: 0000000130000000 aka 4864M
[    0.149481] bus: [00, 07] on node 0 link 0
[    0.149481] bus: 00 index 0 [io  0x0000-0xffff]
[    0.149481] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.149481] Trying to unpack rootfs image as initramfs...
[    0.149481] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.149481] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.149481] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
[    0.149481] Extended Config Space enabled on 1 nodes
[    0.149481] ACPI: bus type pci registered
[    0.149481] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149481] PCI: not using MMCONFIG
[    0.149481] PCI: Using configuration type 1 for base access
[    0.149481] PCI: Using configuration type 1 for extended access
[    0.230812] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.231581] pci 0000:00:13.0: reg 10: [mem 0xfe7fd000-0xfe7fdfff]
[    0.232181] pci 0000:00:15.0: supports D1 D2
[    0.232281] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.232769] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.232814] pci 0000:03:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.252492] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.261781] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.262052] pnp 00:02: [io  0x0081-0x0083]
[    0.263581] pnp 00:0b: [io  0x0910-0x091f]
[    0.263681] system 00:0b: [io  0x0b00-0x0b1f] has been reserved
[    0.648100] thermal LNXTHERM:00: registered as thermal_zone0
[    0.648103] ACPI: Thermal Zone [THRM] (19 C)
[    0.648195] thermal LNXTHERM:01: registered as thermal_zone1
[    0.648196] ACPI: Thermal Zone [THRS] (44 C)
[    0.768148] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.031981] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.060181] ata6: SATA link down (SStatus 0 SControl 300)
[    1.228145] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.238132] scsi 4:0:0:0: CD-ROM            ATAPI    DVD A  DH16AASH  SA15 PQ: 0 ANSI: 5
[    1.334490] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.334550] r8169 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.334586] r8169 0000:03:00.0: setting latency timer to 64
[    1.334640] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    1.335036] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xffffc9000060e000, 90:fb:a6:e2:2a:cd, XID 0c200000 IRQ 42
[    1.335039] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.476480] sd 7:0:0:0: [sdg] 1981440 512-byte logical blocks: (1.01 GB/967 MiB)
[   13.308185] snd_hda_intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.309273] [drm] Initialized drm 1.1.0 20060810
[   13.478143] [drm] radeon defaulting to kernel modesetting.
[   13.478146] [drm] radeon kernel modesetting enabled.
[   13.489001] [TTM] Zone  kernel: Available graphics memory: 1887816 kiB.
[   14.618460] r8169 0000:03:00.0: eth0: link down
[   14.618468] r8169 0000:03:00.0: eth0: link down
[   32.185367] type=1400 audit(1347150407.656:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1810 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  132.681636] r8169 0000:03:00.0: PCI INT A disabled

ADD: then, I ran these again:

$ sudo dpkg -i '/home/xxxxx/Desktop/linux-backports-modules-net-3.2.0-29-generic_3.2.0-29.14_amd64.deb'  
(Reading database ... 137804 files and directories currently installed.) 
Preparing to replace linux-backports-modules-net-3.2.0-29-generic 3.2.0-29.14 (using .../linux-backports-modules-net-3.2.0-29-generic_3.2.0-29.14_amd64.deb) ... 
Unpacking replacement linux-backports-modules-net-3.2.0-29-generic ... 
Setting up linux-backports-modules-net-3.2.0-29-generic (3.2.0-29.14) ... 
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic 
Warning: No support for locale: en_US.utf8


$ sudo modprobe r8168
FATAL: Module r8168 not found.

entering rtl8168 instead of r8168 made no difference.

I realize I'll probably just have to wait for an updated, bug-free new install, but I want to thank gandaran for helping and the others who commented.

---

### Post by gandaran on 2012-09-09
> [ 1.335036] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xffffc9000060e000, 90:fb:a6:e2:2a:cd, XID 0c200000 IRQ 42
well r8169 is the only driver available but RTL8168 firmware is installed, maybe there's something or just a little trick missing to get it working but I just don't know how this backports package is supposed to fix the problem, maybe you should post in the [networking and wireless section]("http://ubuntuforums.org/forumdisplay.php?f=336"), you'll get better support there and don't give up, from my searches this problem has been around a long time on many Ubuntu versions so it's not likely to be fixed soon.
also from my searches I have found there is a launchpad PPA linux-backports-modules package with a r8169 fixed driver but without internet it's not possible.
If you have a wireless router you could buy a wireless adapter one that will work out of the box, there are many cheap ones on [ebay]("http://www.ebay.co.uk/sch/i.html?_nkw=+wireless+adapter&_sacat=0&_odkw=usb+wireless+adapter&_osacat=0") guaranteed to work out of the box for about 5/10 euros, look for the ones with the penguin logo, this would solve your problems installing drivers.


[http://ubuntuforums.org/showthread.php?t=1861865&highlight=r8169](http://ubuntuforums.org/showthread.php?t=1861865&highlight=r8169)

---

### Post by gandaran on 2012-09-09
PieEconomics
> description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
I have the same exact ethernet chip and using r8169 driver (just found out now) the only difference is I have Ubuntu 32-bits so maybe the problem is something else with PC not drivers.
well you could try 32-bits without installing, download the ISO then either burn to a CD or live USB drive, boot the drive to run the live session and check if internet works.

---

### Post by PieEconomics on 2012-09-09
I was successful in completely removing Ubuntu from the computer using "add or remove a program" in windows 7.

Then, I installed Ubuntu on an older computer that also has an r8168 network card, and wired internet showed up and worked immediately.

So beware, wired internet on Ubuntu might work with some computers that have the r8168 card but not with others that have that card.

---

