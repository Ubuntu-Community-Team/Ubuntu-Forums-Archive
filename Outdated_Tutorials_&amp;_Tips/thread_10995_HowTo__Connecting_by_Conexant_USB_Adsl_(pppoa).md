---
title: "HowTo : Connecting by Conexant USB Adsl (pppoa)"
date: 2005-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by heema on 2005-01-13
Connecting by Conexant USB Adsl (pppoa) using Ubuntu

NOTE : This is not a complete howto as i may have forgotten some things


Connecting by Conexant USB Adsl (pppoa) using Ubuntu :

1) Open synaptic and install build-essential

2) Go to [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) ,
download these packages :

bin86_0.16.14-1_i386.deb
kernel-package_8.091.0ubuntu4_all.deb
kernel-source-2.6.8
libatm1-dev_2.4.1-15_i386.deb
libncurses5-dev_5.4-4_i386.deb
libusb-dev_1%3a0.1.8-11_i386.deb
linux-patch-debian-2.6.8.1_2.6.8.1-16_all.deb
linux-tree-2.6.8.1_2.6.8.1-16_all.deb

3) Install the packages

4) Go to [http://www.zullinux.it/linux/accessrunner.html](http://www.zullinux.it/linux/accessrunner.html) ,
download cxacru-2003-10-05-src.tgz and patch-upto_2.6.5_20040517_accessrunner.gz

5) Type :
sudo -s
cd /usr/src
tar xvjf kernel-source-2.6*
ln -s kernel-source-2.6.8.1 linux

6) Patch the kernel
# cd /usr/src/linux
# gunzip -c patch-2.6.x_YYYYMMDD_accessrunner.gz | patch -p1

7) Recompile the kernel
cd /usr/src/linux
cp /boot/config-2.6.8.1-3-686 .config
make oldconfig
make menuconfig


Go to section

Device Driver -> Networking Support -> Networking Options -> ....

<M> Asynchronous Transfer Mode (ATM) (EXPERIMENTAL)
<M> Classical IP over ATM (EXPERIMENTAL)
[*] Do NOT send ICMP if no neighbour (EXPERIMENTAL)
<M> LAN Emulation (LANE) support (EXPERIMENTAL)
<M> Multi-Protocol Over ATM (MPOA) support (EXPERIMENTAL)
<M> RFC1483/2684 Bridged protocols
[*] Per-VC IP filter kludge




Then Go to section

Device Driver -> USB Support ->
<M> Support for USB
.... (go near the end of the page)
<M>Alcatel Speedtouch USB support (NEW)

then save

make-kpkg --revision=1 –append -686 --initrd kernel_image

Wait.

Install the generated kernel-image debs.

8) Restart

9) Untar cxacru package to any folder and type
# make new

10) Substitute cxload.sh and cxunload.sh in "/usr/sbin" with the modified ones that you have downloaded from the site

11) Edit file /etc/cxacru to your needs
here is mine :

#
# Config file for Conexant AccessRunner
#

# Driver mode
DRIVER_MODE=1 # 1 = normal, 2 = debug, 3 = normal+max speed (without ask adsl status), 4 = debug+max speed (without ask adsl status)

# Protocol
PROTOCOL_MODE=2 # 1 = RFC1483/2684 routed, 2 = PPP over ATM (pppoa), 3 = RFC1483/2684 bridged, 4 = PPP over Ethernet (pppoe)

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
VPI=8
VCI=35

# Specific for RFC1483/2684 routed/bridged
# if IP_ADDRESS is blank in bridged mode then it uses DHCP to get IP
IP_ADDRESS=
NETMASK=
GATEWAY=

12) Edit your options file in /etc/ppp
#lock
#noauth
#noipdefault
#usepeerdns

noipdefault
noauth
persist
lcp-max-configure 50
-pap
usepeerdns
name any
user "insert your username here"
defaultroute
plugin /usr/lib/pppd/2.4.1/pppoatm.so 8.35

13) Edit the pap-secrets file
# Secrets for authentication using PAP
# client server secret IP addresses
'username' * 'password'

14) Edit the chap-secrets file
# Secrets for authentication using PAP
# client server secret IP addresses
'username' * 'password' *

15) Edit the resolv.conf in /etc and insert in it your DNS
if you dont know it you could get it from windows by typing ipconfig /all

16) Go to /usr/sbin
# su

# ./cxstart.sh


And wish that it will connect the first time

---

### Post by rarstar on 2005-02-21
I've downloaded all the packages in step 2.

How do I install them?

Can anyone point me in the right direction please?

Thanks.

---

### Post by heema on 2005-02-22
to install a package , you have to be in its directory then type :

```
sudo dpkg -i filename.deb
``` 

if u have them in a seperate directory , u could install them all by typing :


```
sudo dpkg -i *.deb
```

---

### Post by rarstar on 2005-02-25
cool, thanks.

i think i've got the driver installed now, but i still can't connect.

i type 

```

root@ubuntu:/home/tony # cd /usr/sbin
root@ubuntu:/usr/sbin # su
root@ubuntu:/usr/sbin # ./cxstart.sh

``` 

to start the modem, and it does the following...

```

>>> Inits Conexant AccessRunner <<<

>>> Removing cxacru driver...

>>> Loading firmware...
Conexant AccessRunner microcode upload program. 6/9/2003
Josep Comas <jcomas@gna.es>
See credits in documentation

I found ADSL modem with VendorID = 0572 & ProductID = cb00
Loading and sending /usr/sbin/cxfirm4.bin...
Firmware is sent!
Setting configuration...
Waiting ADSL line is up (until 90 seconds)...
.............
ADSL line is up (Downstream 576 Kbits/s, Upstream 288 Kbits/s)
>>> Loading driver...
Launching driver in normal mode...

/usr/sbin/cxload.sh successful
Setting PPP over ATM...
>>> Setting PPPoA <<<

>>> Loading ppp_generic...

>>> Loading pppoatm...

>>> Activating send/receive data...
Conexant AccessRunner ioctl call. 6/9/2003
Josep Comas <jcomas@gna.es>
See credits in documentation

I found ADSL modem with VendorID = 0572 & ProductID = cb00

>>> Loading pppd daemon...
Plugin /usr/lib/pppd/2.4.2/pppoatm.so loaded.
PPPoATM plugin_init
PPPoATM setdevname - remove unwanted options
PPPoATM setdevname_pppoatm - SUCCESS:8.35

/usr/sbin/cxnet2up.sh successful

```

which i think indicates that the driver is working, but when i try to connect...

```

root@ubuntu:/usr/sbin # sudo pon

```

... i get error messages: 

```

Plugin /usr/lib/pppd/2.4.2/pppoatm.so loaded.
PPPoATM plugin_init
PPPoATM setdevname - remove unwanted options
PPPoATM setdevname_pppoatm - SUCCESS:8.35
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option 'connect'

```

Not really sure what's going on, and I can't find anything on the net about this.

Any help would be appreciated!

Cheers,
rar

---

### Post by heema on 2005-02-27
you dont have to type sudo pon  as you are already connect

make sure first that you have entered ur DNS

Go to Computer -> System Configuration -> Networking 
 
then there is a tab for entering the DNS

then connect then try opening firefox

---

### Post by vale on 2005-03-07
Hi,
I really appreciated your HOWTO!
But I don't understand what I have to do at step 4)...
I went to 
[http://www.zullinux.it/linux/accessrunner.html](http://www.zullinux.it/linux/accessrunner.html) ,
and downloaded cxacru-2003-10-05-src.tgz 
but I don't know hot to get patch-upto_2.6.5_20040517_accessrunner.gz
...I can't see it... Where can I find it?

Thanks
   & Cheers
      Vale

---

### Post by heema on 2005-03-07
[QUOTE=vale]Hi,
I really appreciated your HOWTO!
But I don't understand what I have to do at step 4)...
I went to 
[http://www.zullinux.it/linux/accessrunner.html](http://www.zullinux.it/linux/accessrunner.html) ,
and downloaded cxacru-2003-10-05-src.tgz 
but I don't know hot to get patch-upto_2.6.5_20040517_accessrunner.gz
...I can't see it... Where can I find it?

Thanks
   & Cheers
      Vale[/QUOTE]


[http://www.zullinux.it/linux/patch-upto_2.6.5_20040517_accessrunner.gz](http://www.zullinux.it/linux/patch-upto_2.6.5_20040517_accessrunner.gz)

---

### Post by vale on 2005-03-07
Ok,
now sorry my ignorance again...
How and were must I save this .gz file?

Thanks very  very much!
   Vale

---

### Post by heema on 2005-03-07
its ok   :smile: 

right click on it and choose "save as" , then save it in ur home folder temporary for now until you extracted the kernel source then copy it to /usr/src/linux to be able to patch the kernel  

or 

if u want u could leave it in ur home folder but in step 6 change :
gunzip -c patch-2.6.x_YYYYMMDD_accessrunner.gz | patch -p1
to
gunzip -c /home/whereitis/patch-2.6.x_YYYYMMDD_accessrunner.gz | patch -p1

---

### Post by vale on 2005-03-07
Other 2 things...
1) Which file I have to download from
[http://security.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.8/](http://security.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.8/)
??
Do I have to put it in /usr/src? Is it the same of step 5?
 
2)  
About
linux-patch-debian-2.6.8.1_2.6.8.1-16_all.deb
linux-tree-2.6.8.1_2.6.8.1-16_all.deb
Are the ones I can get with synaptic ok?

   thanks

---

### Post by heema on 2005-03-07
[QUOTE=vale]Other 2 things...
1) Which file I have to download from
[http://security.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.8/](http://security.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.8/)
??
Do I have to put it in /usr/src? Is it the same of step 5?
 [/QUOTE]

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/linux-source-2.6.8.1_2.6.8.1-16_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/linux-source-2.6.8.1_2.6.8.1-16_all.deb)

when you install it , it will put the kernel-source*.tar file in /usr/src so then you will have to extract it 

> 
2)  
About
linux-patch-debian-2.6.8.1_2.6.8.1-16_all.deb
linux-tree-2.6.8.1_2.6.8.1-16_all.deb
Are the ones I can get with synaptic ok?

you could use the ones in this site

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/)

---

### Post by vale on 2005-03-07
Sorry but there is always a new problem!
I downloaded 
linux-patch-debian-2.6.8.1_2.6.8.1-16_all.deb
linux-tree-2.6.8.1_2.6.8.1-16_all.deb
and linux-source...
and made sudo dpkg -i *.deb
but I had the next error... can you tell me why?

 :-( 

(Reading database ... 137508 files and directories currently installed.)
Preparing to replace linux-patch-debian-2.6.8.1 2.6.8.1-16 (using linux-patch-debian-2.6.8.1_2.6.8.1-16_all.deb) ...
Unpacking replacement linux-patch-debian-2.6.8.1 ...
Preparing to replace linux-tree-2.6.8.1 2.6.8.1-16 (using linux-tree-2.6.8.1_2.6.8.1-16_all.deb) ...
Unpacking replacement linux-tree-2.6.8.1 ...
Setting up linux-patch-debian-2.6.8.1 (2.6.8.1-16) ...
dpkg: dependency problems prevent configuration of linux-tree-2.6.8.1:
 linux-tree-2.6.8.1 depends on linux-source-2.6.8.1 (= 2.6.8.1-5) | linux-source-2.6.8.1 (= 2.6.8.1-6) | linux-source-2.6.8.1 (= 2.6.8.1-7) | linux-source-2.6.8.1 (= 2.6.8.1-8) | linux-source-2.6.8.1 (= 2.6.8.1-9) | linux-source-2.6.8.1 (= 2.6.8.1-10) | linux-source-2.6.8.1 (= 2.6.8.1-11) | linux-source-2.6.8.1 (= 2.6.8.1-12) | linux-source-2.6.8.1 (= 2.6.8.1-13) | linux-source-2.6.8.1 (= 2.6.8.1-14) | linux-source-2.6.8.1 (= 2.6.8.1-15) | linux-source-2.6.8.1 (= 2.6.8.1-16) | linux-source-2.6.8.1 (= 2.6.8.1-1) | linux-source-2.6.8.1 (= 2.6.8.1-2) | linux-source-2.6.8.1 (= 2.6.8.1-3) | linux-source-2.6.8.1 (= 2.6.8.1-4); however:
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
dpkg: error processing linux-tree-2.6.8.1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-tree-2.6.8.1

---

### Post by heema on 2005-03-07
you have to install linux-source and extract it before installing linux-tree

---

### Post by vale on 2005-03-07
ok... :-( 
I did
in /usr/src   tar xvjf linux-source-2.6.8.1.tar.bz2
then in my home I did
sudo dpkg -i linux-patch-debian-2.6.8.1_2.6.8.1-16_all.deb 
and that's ok...
then I did, always from my home
 sudo dpkg -i linux-tree-2.6.8.1_2.6.8.1-16_all.deb
but I had the sames error like before:


root@dhcpvisitor21768:~/prova # sudo dpkg -i linux-tree-2.6.8.1_2.6.8.1-16_all.deb (Reading database ... 137508 files and directories currently installed.)
Preparing to replace linux-tree-2.6.8.1 2.6.8.1-16 (using linux-tree-2.6.8.1_2.6.8.1-16_all.deb) ...
Unpacking replacement linux-tree-2.6.8.1 ...
dpkg: dependency problems prevent configuration of linux-tree-2.6.8.1:
 linux-tree-2.6.8.1 depends on linux-source-2.6.8.1 (= 2.6.8.1-5) | linux-source-2.6.8.1 (= 2.6.8.1-6) | linux-source-2.6.8.1 (= 2.6.8.1-7) | linux-source-2.6.8.1 (= 2.6.8.1-8) | linux-source-2.6.8.1 (= 2.6.8.1-9) | linux-source-2.6.8.1 (= 2.6.8.1-10) | linux-source-2.6.8.1 (= 2.6.8.1-11) | linux-source-2.6.8.1 (= 2.6.8.1-12) | linux-source-2.6.8.1 (= 2.6.8.1-13) | linux-source-2.6.8.1 (= 2.6.8.1-14) | linux-source-2.6.8.1 (= 2.6.8.1-15) | linux-source-2.6.8.1 (= 2.6.8.1-16) | linux-source-2.6.8.1 (= 2.6.8.1-1) | linux-source-2.6.8.1 (= 2.6.8.1-2) | linux-source-2.6.8.1 (= 2.6.8.1-3) | linux-source-2.6.8.1 (= 2.6.8.1-4); however:
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
  Version of linux-source-2.6.8.1 on system is 2.6.8.1-16.11.
dpkg: error processing linux-tree-2.6.8.1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-tree-2.6.8.1

---

### Post by Ebbi on 2005-03-19
HI!
I don't have internet in ubuntu, so i cant find some packeges in archive.ubuntu.com. Could u give direct link, pls?
bin86_0.16.14-1_i386.deb
kernel-source-2.6.8
libncurses5-dev_5.4-4_i386.deb
libusb-dev_1%3a0.1.8-11_i386.deb

---

### Post by cheezee on 2005-03-24
it realy works with Hoary 5.04???

---

### Post by arvir on 2005-04-03
evrything has been done till step 7 but there is problem generating the kernel debs.there sre some errors when i use the command

make-kpkg --revision=1 –append -686 --initrd kernel_image

like 
append unknown option
686 unknown option.


can any one help me

---

### Post by tarasbulba on 2005-04-03
hello,could you explain more,compiling kernel for this modem?for dummies :( 
I want to try it for ubuntu Hoary 5.04 with kernel-2.6.10...Please tell us more..Im going crazy.I cant compile kernel in ubuntu...pls help

---

### Post by raid996 on 2006-04-11
On step 7:
make oldconfig
make menuconfig

I get this error:
```

root@ubuntu:/usr/src/linux# make oldconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  SHIPPED scripts/kconfig/zconf.tab.h
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/mconf.o
scripts/kconfig/mconf.c:91: error: static declaration of &#8216;current_menu&#8217; follows non-static declaration
scripts/kconfig/lkc.h:63: error: previous declaration of &#8216;current_menu&#8217; was here
make[1]: *** [scripts/kconfig/mconf.o] Error 1
make: *** [oldconfig] Error 2

```
```

root@ubuntu:/usr/src/linux# make menuconfig
  HOSTCC  scripts/kconfig/mconf.o
scripts/kconfig/mconf.c:91: error: static declaration of &#8216;current_menu&#8217; follows non-static declaration
scripts/kconfig/lkc.h:63: error: previous declaration of &#8216;current_menu&#8217; was here
make[1]: *** [scripts/kconfig/mconf.o] Error 1
make: *** [menuconfig] Error 2

```

Any help???? And then i just cant find that "device driver --> ... --> Networking options", where should these folders be?
](*,) ](*,) ](*,) ](*,) 

oh! almost forgot on the patch step I also had this problem:
```

root@ubuntu:/usr/src/linux# gunzip -c /home/claudia/Desktop/patch-upto_2.6.5_20040517_accessrunner.gz | patch -p1
patching file drivers/usb/misc/speedtch.c
Hunk #2 FAILED at 108.
Hunk #3 succeeded at 169 (offset 4 lines).
Hunk #4 succeeded at 217 (offset 4 lines).
Hunk #5 succeeded at 228 (offset 4 lines).
Hunk #6 succeeded at 414 (offset 17 lines).
Hunk #7 succeeded at 566 (offset 17 lines).
Hunk #8 succeeded at 592 (offset 17 lines).
Hunk #9 succeeded at 608 (offset 17 lines).
Hunk #10 succeeded at 639 (offset 17 lines).
Hunk #11 succeeded at 679 (offset 17 lines).
Hunk #12 succeeded at 764 (offset 17 lines).
Hunk #13 succeeded at 1098 (offset 16 lines).
Hunk #14 succeeded at 1139 (offset 16 lines).
Hunk #15 succeeded at 1219 (offset 16 lines).
Hunk #16 succeeded at 1278 (offset 16 lines).
Hunk #17 succeeded at 1303 (offset 16 lines).
1 out of 17 hunks FAILED -- saving rejects to file drivers/usb/misc/speedtch.c.rej


```

Please help me. i've been trying to make this modem work for long time already...

---

### Post by ioargento on 2006-05-11
This thread seem to be the answer i was looking for.... So i'm trying to get this working. 

**The question made by Cheezee regarding if this was going to work under Hoary, it's accually a good one.** Any answer? 

My first problem was that i couldnt find the same version of the kernel source. I found the 2.6.10...  it's going to work anyway? 

if not, please someone who can tell me where i can find the correct version? 

Thanks in advance!

---

