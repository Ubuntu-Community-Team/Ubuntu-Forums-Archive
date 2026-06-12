---
title: "Zoom 5510 ADSL USB Modem Install (UK)"
date: 2006-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Malac on 2006-05-26
[SIZE=2]T[/SIZE][SIZE=5][SIZE=2]here is a 6.06 "Dapper" install here:
[http://www.ubuntuforums.org/showthread.php?t=194237](http://www.ubuntuforums.org/showthread.php?t=194237)[/SIZE]
[/SIZE][B]_[SIZE=5]Zoom 5510A ADSL USB Modem Install[/SIZE]_
[SIZE=2](This is for the slim dark grey one issued in the UK by alot of providers. 5510-72 Mine says.
[/SIZE][/B][ATTACH]18729[/ATTACH]
**[SIZE=2] May work with other Connexant Chip Modems, just compile and run cxacru-fw and put extracted file in the cxacru folder).[/SIZE]**

 This was done on a Fresh Install of Ubuntu 5.10 "Breezy".
 [B][U][SIZE=5]Okay to start

[/SIZE][/U][/B]  On an Internet Enabled OS or Machine
 
 Get the following files from the internet.
 Change the i386 part of the name if you are running amd64, sparc or powerpc.
 [B]
gcc-3.4-base, cpp-3.4 and gcc-3.4[/B]  
 [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
 [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
 [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)
 [B]
Kernel-Package[/B]  
 [http://archive.ubuntu.com/ubuntu/pool/main/k/kernel-package/kernel-package_9.001ubuntu5_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kernel-package/kernel-package_9.001ubuntu5_all.deb)
 
 **Linux-Stuff**
 [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-tree-2.6.12_2.6.12-9.23_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-tree-2.6.12_2.6.12-9.23_all.deb)
 [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-source-2.6.12_2.6.12-9.23_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-source-2.6.12_2.6.12-9.23_all.deb)
 [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-patch-ubuntu-2.6.12_2.6.12-9.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-patch-ubuntu-2.6.12_2.6.12-9.23_i386.deb)
 
 **libncurses5**
 [http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5-dev_5.5-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5-dev_5.5-1ubuntu3_i386.deb)
 [http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5_5.5-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5_5.5-1ubuntu3_i386.deb)
 
 **USBATM Driver**
 [http://prdownloads.sourceforge.net/accessrunner/usbatm-20050216.tar.bz2?download](http://prdownloads.sourceforge.net/accessrunner/usbatm-20050216.tar.bz2?download)
 [http://prdownloads.sourceforge.net/accessrunner/cxacru_bundle-2004-05-11.tar.bz2?download](http://prdownloads.sourceforge.net/accessrunner/cxacru_bundle-2004-05-11.tar.bz2?download)
 
 **CXACRU Extraction Utility**
 [http://homepage.ntlworld.com/malacandra/cxacru.zip](http://homepage.ntlworld.com/malacandra/cxacru.zip)
[SIZE=-2]I can't remember where I got this one from so I have put a copy here.[/SIZE]
 [SIZE=-2]This is the one with a pre-extracted Zoom 5510 firmware file.[/SIZE]
 
**I also installed this one but I don't know if It is needed.**  
 [http://archive.ubuntu.com/ubuntu/pool/universe/x/xdslusb/xdslusb-source_0.0.20031029-5_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xdslusb/xdslusb-source_0.0.20031029-5_all.deb)
 
 Put them in a folder called "adslusb"(without the quotes) in the root of your machine.
 Also save this page to that folder as a ".complete" file
 
 If you are *not* dual booting you will have to burn the folder onto a CD-R.
 If you *are* dual booting with (I assume) Windows, when Back in Ubuntu mount your Windows Drive using "mount" in the root Terminal(described later).
 
 Back in Ubuntu
 Login as normal user.
 I found this made life easier, saving having to type sudo all the time.
 Run nautilus as root and gnome-terminal as root.
 Choose [Applications->System Tools->Run as different user], type "gnome-terminal"(without the quotes) in the box.
 Enter Password.
 Choose [Applications->System Tools->Run as different user], type "nautilus"(without the quotes) in the box.
  DO NOT CLOSE THESE UNTIL THE END.

 ------ Dual-Boot Hard Disk Section, if folder is on a CD-R miss this section out -----
 In Nautilus
 Go to Filesystem:/mnt/, right-click on space, choose "Create Folder" and call it "win".
 In Terminal
 If Windows drive is C: then this should be sufficient:
```

mount /dev/hda1 /mnt/win

```----- End Section -----

 In Nautilus
 Go to FileSystem:/mnt/win/ or to the CD.
Right-click the folder "adslusb" and choose copy.
Go to Filesystem:/usr/src/, right-click on space, choose "Paste".
Choose "Bookmarks" in the top menu and "Add to Bookmarks", (This will aid with navigation later).
 
 Open Synaptic (...)
 Click [Search] and type "build-essential" (without quotes), change Search In to "Name".
 Mark build-essential for installation. It will ask you if it is okay to mark other packages for installation.
Click [Mark] to this.
[Apply] and Exit Synaptic.
 
 In Terminal
 You can install the packages using dpkg command.

 Type the following in this order. 
```

 cd /usr/src/adslusb
 dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
 dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb
 dpkg -i gcc-3.4_3.4.4-6ubuntu8_i386.deb
 dpkg -i kernel-package_9.001ubuntu5_all.deb
 dpkg -i linux-source-2.6.12_2.6.12-9.23_all.deb
 dpkg -i linux-patch-ubuntu-2.6.12_2.6.12-9.23_i386.deb
 dpkg -i linux-tree-2.6.12_2.6.12-9.23_all.deb
 dpkg -i libncurses5_5.5-1ubuntu3_i386.deb
 dpkg -i libncurses5-dev_5.5-1ubuntu3_i386.deb
 dpkg -i xdslusb_0.0.20031029-5_i386.deb
 cd /usr/src
 tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
 ln -s /usr/src/linux-source-2.6.12 /usr/src/linux

```  If this last line throws error "File Already Exists".
 Type :   ```
rm /usr/src/linux
```And re-enter the last line.
 
 In Nautilus
 Go to Filesystem: /usr/src/adslusb folder.
Open usbatm-20050216.tar.bz2 by double-clicking on it.
Extract "drivers" folder to Filesystem: /usr/src/linux .
[SIZE=-2](Using [Extract] choose "Other" in "Extract in Folder" pulldown
Browse to Filesystem:/usr/src/linux, Click [Open] then [Extract])[/SIZE]
  Open cxacru_bundle-2004-05-11.tar.bz2
Extract "cxacru" folder to Filesystem: /usr/src [SIZE=-2](same process as above)[/SIZE].
Open cxacru-fw.zip
Extract "cxacru-fw" folder to Filesystem: /usr/src [SIZE=-2](same process as above)[/SIZE].
 
 In Terminal
 ```

 cd /usr/src/cxacru-fw
 cp /usr/src/cxacru-fw/cxacru-fw.bin /lib/hotplug/firmware/cxacru-fw.bin
 cd /usr/src/cxacru/scripts
 make install
 cd /usr/src/linux
 make oldconfig

```At this prompt:
  Conexant AccessRunner USB support (USB_CXACRU) [N/m/?] (NEW)
  Press [ M ] key then [Enter].
 
```
make menuconfig
``` This can get complicated but you need to choose your processor here.
 Go to Processor type and features ---> using the arrow keys.
 Hit [Enter].
 Choose Processor family --->.
 For my system High memory support was not needed as I don't have more than 4GB.
 I turned it off by scrolling down and choosing the option.
 Then keep selecting Exit option using tab key until it is highlighted and then say yes to the save prompt.

 In Terminal
 
```

 make-kpkg clean
 make-kpkg --initrd --append-to-version=-[COLOR=DarkGreen]adslusb[/COLOR] kernel_image kernel_headers
 
``` You can put anything you want instead of "[COLOR=DarkGreen]adslusb[/COLOR]" (lowercase only) but this made sense to me.
 Wait about 45-60 mins. (Yep that's right, go make a brew, read a book or something.)
 
 When it's finally finished type the following:
```

 cd /usr/src
 ls

``` You'll see a list of the names of the files in the folder as well as the names of your new kernel image and kernel headers.
 They should look (approximately)like these:

[COLOR=red]kernel-image-2.6.12-adslusb_10.00.Custom_i386.deb
kernel-headers-2.6.12-adslusb_10.00.Custom_i386.deb
 [/COLOR]   
 Now install them by typing these commands
(change the name of the files to the ones you have seen after 'ls' command) ```

 dpkg -i kernel-image-2.6.12-adslusb_10.00.Custom_i386.deb
 dpkg -i kernel-headers-2.6.12-adslusb_10.00.Custom_i386.deb
 
``` Reboot and choose your new kernel.
Hopefully all is working and the green "link" light is flashing then staying on letting you know the firmware is loaded and the modem is ready to connect.
 Congratulations, Stage 1 completed, hurrah.

 IF ANYTHING GOES WRONG;
 REBOOT
 CHOOSE THE ORIGINAL KERNEL
 LOGIN
 ISSUE THESE COMMANDS IN ROOT TERMINAL[SIZE=-2](see above).[/SIZE]
```

 dpkg -r kernel-image-2.6.12-adslusb
 dpkg -r kernel-headers-2.6.12-adslusb

``` Okay hopefully you reached this point.
 Re-open Root Nautilus and Root Terminal[SIZE=-2](see above).[/SIZE]
 
In Terminal
 ```

 cp /usr/share/doc/ppp/examples/peers-pppoa /etc/ppp/peers/yourprovidername

``` In Nautilus
 Go to Filesystem: /etc/ppp/peers folder.
Open the file [COLOR=green]yourprovidername[/COLOR] by double clicking on it.
Change the "user=you@yourrealm" field to ```
"user=[COLOR=DarkGreen]yourusername[/COLOR]@[COLOR=DarkGreen]yourprovidername[/COLOR]"(without the quotes)
``` The only other things in this file should be.
```

plugin pppoatm.so
noipdefault
usepeerdns
defaultroute
persist
noauth
nopcomp
noccp
novj

``` Save and Exit
  Go to Filesystem: /etc/ppp folder
Open the file "chap-secrets"
Add a line ```
"[COLOR=DarkGreen]yourusername[/COLOR] * [COLOR=DarkGreen]yourpassword[/COLOR]"[SIZE=-2](without the quotes)[/SIZE]
```Open the file "pap-secrets"
And do the same.
Rename the file "options" to "options.orig"(right-click choose "Rename").
Create new file "options" and enter these values:
```

asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 60
lcp-echo-failure 4
noipx
replacedefaultroute
noipdefault
#noauth
persist
lcp-max-configure 50
-pap
name any
user '[COLOR=DarkGreen]yourusername[/COLOR]'(without the quotes) 
defaultroute
plugin /usr/lib/pppd/2.4.3/pppoatm.so 0.38

``` Create file "resolv.conf"(right-click choose "Create Document"--->"Empty File")
Open this file and add this:
```

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```Where xxx.xxx.xxx.xxx is replaced by your ISP DNS Servers.
  Go to /etc folder.
Open the file "modules"
Add a line:
```
"pppoatm"(without the quotes).
``` Save and Exit.
----- COPY SECTION - If files "cxacru" and/or "cxacru.service" are not in "/etc" directory do this section, otherwise skip it. -----
Go to Filesystem: /usr/src/cxacru/scripts/service folder.
Right-click on cxacru choose "Copy"
Go back to Filesystem: /etc
Right-click on space and choose "Paste"
Right-click and choose "Rename", and call it "cxacru.service"[SIZE=-2](without the quotes)[/SIZE].
Go to Filesystem: /usr/src/cxacru/scripts/config folder.
Right-click on cxacru choose "Copy"
Go back to Filesystem: /etc
Right-click on space and choose "Paste"
----- END COPY SECTION -----
Open "/etc/cxacru" file and change it to read like this.    # 
```

# Config file for Conexant AccessRunner 
# 

# Driver mode 
DRIVER_MODE=1 # 1 = normal, 2 = debug, 3 = normal+max speed (without ask adsl status), 4 = debug+max speed (without ask adsl status) 

# Protocol 
PROTOCOL_MODE=**2** # 1 = RFC1483/2684 routed, 2 = PPP over ATM (pppoa), 3 = RFC1483/2684 bridged, 4 = PPP over Ethernet (pppoe) 

# Paths 
BINARY_PATH="/usr/sbin" 
ATM_PATH="" 

# ADSL 
# if OPEN_MODE is blank then cxload uses default mode acoording VID & PID 
# Values for OPEN_MODE are: 
# 0 = auto selection, G.Handshake 
# 1 = auto selection, T1.413 
# 2 = G.Handshake 
# 3 = ANSI T1.413 
# 4 = ITU-T G.992.1 (G.DMT) 
# 5 = ITU-T G.992.2 (G.LITE) 
OPEN_MODE= 

# ATM 
VPI=**0**
VCI=**38**

# Specific for RFC1483/2684 routed/bridged
#  if IP_ADDRESS is blank in bridged mode then it uses DHCP to get IP
IP_ADDRESS=
NETMASK=255.255.255.0
GATEWAY=

``` The altered numbers are **PROTOCOL_MODE** and **ATM**.
  Save and Exit.
Go to Filesystem: /usr/src/cxacru/scripts folder.
Add this folder to Bookmarks.
Copy all files ending in .sh
 Can be done by pressing Ctrl-A then, whilst holding down Ctrl, click the folders and files you don't want. Then press Ctrl-C
  Go to FileSystem: /etc
Right-click on space and choose "Paste". Go to Filesystem: /etc/network folder.
Open file "interfaces".
 Comment out (put a # at the front) of these lines, if they are there:
```

iface ppp0 inet ppp
provider ppp0

``` And insert the following:
```

# The ADSL connection
iface ppp0 inet ppp
    provider [COLOR=DarkGreen]yourproviderfile[/COLOR]
    # waits 70 seconds for the line to be ready
    pre-up /usr/local/sbin/checkADSL.sh
    # enables ip forwarding (this is a gateway)
    pre-up echo 1 > /proc/sys/net/ipv4/ip_forward
    pre-up iptables-restore < /etc/iptables.up.rules

auto ppp0

``` In Nautilus
  Go to Filesystem: /usr/local/sbin folder.
Create file and call it "checkADSL.sh"[SIZE=-2](without the quotes)[/SIZE].
Open it to edit.
 And type in the values:
```

#!/bin/sh
## For /usr/local/sbin run it on boot
count=0
while [ $count -lt 70 ]
do
    sync=$(dmesg | grep "ADSL line: up")
    if [ ! -z "$sync" ]
    then
        exit 0
    fi
    sleep 1
    count=$((1+$count))
done

```Save and Exit.
 Right-click choose "Properties" then "Permissions" Tab and tick all the Read and Execute boxes.
 This script is a delay which you need or the interface will not be connected when the network is brought up at boot.
 
 This is a fix-up but it does work.
 In Nautilus
  Go to Filesystem: /usr/local/lib folder.
Right-click choose "Create Folder" and call it "cxacru"[SIZE=-2](without the quotes)[/SIZE]. 

 In Terminal
```
cp /usr/src/cxacru-fw/cxacru-fw.bin /usr/local/lib/cxacru/cxfirm5.bin
``` I would also get rid of the ntpdate check on boot as you aren't connected anyway.
 To do this choose System->Administration->Services and uncheck (ntpdate)

 REBOOT (Do not try dialing yet.)

 When you reboot and login type:
 In Terminal
  
```
pppd call yourproviderfile
```    And I hope it works for you as it did for me. Good Luck.
------------------------------------------------------------------------------------------------------------------------------------------

Slight Addendum:
Don't use kppp, gnome-ppp or System->Administration->Networking to change the PPP settings as it screws up the files for this connection.

I re-did my entire install from scratch several times during doing this walkthrough to make sure it worked.

It should work on a fresh install of "Breezy", I can't vouch for anything else or if you have already altered your system from the default.

This is for a UK broadband ISP so I don't know if it will work in other countries.

Have Fun.

---

### Post by zxc on 2006-06-09
Tried this on Dapper but couldn't get past near enough the first step as dpkg -i stuff just breaks straight away (lacks dependecies...from what I remember binutils). :(

---

### Post by Malac on 2006-06-09
Hi,
I am a Ubuntu/Linux newbie this was just a howto that worked for me. There are probably some steps that don't need doing in it, it was just what worked for me as I had seen alot of posts about this particular modem, so I don't know the technical reasons why it hasn't worked for you.

I upgraded from Breezy to Dapper when it came out.
This method would not work for me on this upgraded Dapper system.
[I]
However:[/I]
The only thing I had to do to get the Zoom 5510 to work on the upgraded Dapper was put the cxacru-fw.bin file in /lib/hotplug/firmware and in /lib/firmware/2.6.15-23-386 and all worked fine.

This was on an upgraded system I have not tried it out on a fresh install yet.
I will try to get round to it this weekend some time.

If this does work for you please let me know here and I can save some time.
Thanks in Advance. :)

---

### Post by zxc on 2006-06-09
Actually got quite far...about 

"In Terminal
Code:

cd /usr/src/cxacru-fw cp /usr/src/cxacru-fw/cxacru-fw.bin /lib/hotplug/firmware/cxacru-fw.bin cd /usr/src/cxacru/scripts make install cd /usr/src/linux make oldconfig


At this prompt:
Conexant AccessRunner USB support (USB_CXACRU) [N/m/?] (NEW)
Press [ M ] key then [Enter]."

I fell down as I didn't get this prompt but a LOAD of other ones which I had no idea how to answer and basically answered randomly.

Another problem I had was this:

 cp /usr/src/cxacru-fw/cxacru-fw.bin /lib/hotplug/firmware/cxacru-fw.bin

As their was no hotplug folder :/.

---

### Post by zxc on 2006-06-09
Woops wasn't really expecting a reply :eek: 

I'm compiling at the moment (with the above problem). I didn't put it in the lib/firmware/22 thingy...any ideas how I can backtrack to that point?

Should I exit the compiling (which is compiling with the .bin file in the wrong place and I selected a bunch of options which at the press [M] bit I didn't know...there was about 20-30 questions).


edit: I'm compiled with the wrong stuff, where should I go from just having compiled it

I'm at the end of

> You can put anything you want instead of "adslusb" (lowercase only) but this made sense to me.
Wait about 45-60 mins. (Yep that's right, go make a brew, read a book or something.)

Edit 2: I'm going to do a fresh install...the only other problem I had in installation was:

 cd /usr/src/cxacru-fw
 cp /usr/src/cxacru-fw/cxacru-fw.bin /lib/hotplug/firmware/cxacru-fw.bin
 cd /usr/src/cxacru/scripts
 make install
 cd /usr/src/linux
 make oldconfig

Make install wouldn't work until I copied all the files from cxacru/scripts ---> usr/sbin then I think it worked.

---

### Post by zxc on 2006-06-09
Ok, definitive post. I did a complete reinstall.

It seems to be fine up to:

> In Terminal
Code:

cd /usr/src/cxacru-fw cp /usr/src/cxacru-fw/cxacru-fw.bin /lib/hotplug/firmware/cxacru-fw.bin cd /usr/src/cxacru/scripts make install cd /usr/src/linux make oldconfig


At this prompt:
Conexant AccessRunner USB support (USB_CXACRU) [N/m/?] (NEW)
Press [ M ] key then [Enter].

Code:

make menuconfig



When make oldconfig is pressed you get about 30 options similar to the one above (but not for the same thing, other things like sounds and graphics). I haven't actually seen the above "Connexant AccessRunner" show as one of the options. The Compiling bugs up (most probably because I just select the above choices randomly between y/n/m and when I do the ls command I do not get:

kernel-image-2.6.12-adslusb_10.00.Custom_i386.deb
kernel-headers-2.6.12-adslusb_10.00.Custom_i386.deb

Any help would be appreciated :| 

Thanks in advance.

---

### Post by Malac on 2006-06-09
Okay zxc,
As I said I have not tried it as a fresh install of Dapper.
And I am a newbie so I am doing this "by-rote" as it were.
I will try to do a fresh install of Dapper tomorrow(Saturday) and check all the steps I do.

My approach is somewhat "hap-hazhard" as I don't know the technical details of the individual setup steps. They tend to be from other tutorials that I try and if they work I merge/adapt to the Zoom 5510 process but this is a series of trial and (lots of) errors. :)

This does require some time though as if the process mungs up somewhere I have to wipe the drive and start again with a fresh install so I don't do something that affects the process without me realising it.

As soon as I possibly can I will try to get this sorted for Dapper.
If anyone else reading this knows anything helpful please chip in.
In the mean time try the forums for kernel compilation howto's for Dapper.
As for the "N/m/?" thing just hit return at each of the prompts for stuff you don't know what it is and it will use the default option. Don't hit random N's or m's as this _will_ mung up the compilation.

Stick with it.

---

### Post by Malac on 2006-06-10
Okay I've done it with a fresh install of "Dapper" and it is working.
**No need to re-compile kernel. (Hurrah) =D>**
It has taken me all day and several re-installs from scratch to get it to work.
I will post a full howto tomorrow as I have to go out now.
Sorry to dangle it in front of you but thought I'd let you know it's possible so you don't give up all hope.
It's also easier than with "Breezy".

---

### Post by Malac on 2006-06-11
Okay I have posted a full "walkthrough" in the General Howto Section of the Forums for "Dapper".

[http://www.ubuntuforums.org/showthread.php?t=194237](http://www.ubuntuforums.org/showthread.php?t=194237)

Hope this helps any problems let me know.

---

