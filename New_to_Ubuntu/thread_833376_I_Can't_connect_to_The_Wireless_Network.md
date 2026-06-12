---
title: "I Can't connect to The Wireless Network"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Papenco on 2008-06-18
Ok, I Finally could install the driver for my Wireless Card in my Dell E1505 With Ubuntu. The problem is I can see the Wireless Networks but can't connect to them. When I try to connect it asks for the password, I enter it and it tries to connect, but after a minute or so, it asks me for the password again. 
Thanks for your help.

---

### Post by pytheas22 on 2008-06-18
Please post the output of these commands so that we can help better:

```
lspci
iwconfig
lshw -C Network
iwlist scan
```

---

### Post by Papenco on 2008-06-18
OK, lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lshw -C Network:

 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5c:22:2c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.0.3 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:b1:a2:c0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

iwlist:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Thanks for the help, I don't want to get back to Windows, Ubuntu:guitar:.

---

### Post by pytheas22 on 2008-06-18
Try following [this how-to]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/").  It's for 7.10 but it should all be basically the same for you, and it's for the same kind of wireless card that you have.

The one difference is that you should ignore step 2 of that tutorial (because bcm43xx is already blacklisted in Hardy by default) and instead run these commands:

```
sudo apt-get remove b43-fwcutter
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
exit
```

Otherwise, follow that tutorial exactly as it says and your card should be working.  Let us know how it goes.

---

### Post by Papenco on 2008-06-20
Are the >> necessary in this code you've written here?. I mean, do I have to write them in my terminal?
I'm new to this Ubuntu thing. 
Thanks.

---

### Post by pytheas22 on 2008-06-20
Sorry, I made a big mistake in my directions (don't worry, it didn't damage anything, but it explains why the tutorial didn't work)...the commands that you should run are:

```
sudo apt-get remove b43-fwcutter
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
exit

```

(notice the "/blacklist" at the end of those lines...this is very important and I forgot it before; I apologize for not checking).

So please following the tutorial again and when you get to step 2, use the commands above, which are the right ones.  Everything else should still be done as you did it before.

> 
Are the >> necessary in this code you've written here?. I mean, do I have to write them in my terminal?

Yes, the >> are necessary.  You should enter this whole line in your terminal, all at once, and then press enter:
```

echo 'blacklist b43' >> /etc/modprobe.d/blacklist
```

and so on for the other lines.  The reason you do this is that you need to "blacklist" a few modules (in Linux a module is essentially what you would call a driver in Windows), which means tell the system not to use them, because they cause problems with ndiswrapper.  To blacklist the modules, we add their names to the file /etc/modprobe.d/blacklist.  If you type in a terminal:

gedit /etc/modprobe.d/blacklist

you would see the file and the names of modules to be blacklisted.  After running the commands, you should see at the bottom of the file the lines "blacklist b43," "blacklist b43legacy" and so on.

FYI: basically >> means "append to file," and in this case the file that it's getting appended to is /etc/modprobe.d/blacklist.  The thing that's getting appended is the output of the command "echo 'blacklist b43'"  There are other ways to get this done but the method I use is the simplest when giving instructions, because it can just be copied and pasted.

As for ndiswrapper: it's a program that allows you to use the Windows driver to make your wireless card work in Linux.  In some cases this is necessary because there are no good Linux drivers for certain cards (there are Linux drivers for the kind of card that you have, but they are new and may not work well, so it's better to try the ndiswrapper method first).

Again, I'm sorry for my oversight, but with the corrected commands it should work.

---

### Post by Papenco on 2008-06-20
when I do sudo make in the ndiswrapper directory, this appear: 
```
leandro@leandro-laptop:~/ndiswrapper-1.49$ make
make -C driver
make[1]: se ingresa al directorio `/home/leandro/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/leandro/ndiswrapper-1.49/driver
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/leandro/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Alto.
make[2]: *** [_module_/home/leandro/ndiswrapper-1.49/driver] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/home/leandro/ndiswrapper-1.49/driver'
make: *** [all] Error 2
```

I know it's in spanish so:
Directorio means directory
se sale means to get out
se ingresa means to get in

Are that errors that appear at the end of the code right?
I mean, must the appear?

---

### Post by dwhitney67 on 2008-06-20
That's odd... I also have a Dell E1505, same wifi chip-set, and it is the B43 driver that is needed.  The driver that should be blacklisted is the bcm43xx.

---

### Post by dwhitney67 on 2008-06-20
> **Papenco said:**
> when I do sudo make in the ndiswrapper directory, this appear: 
```
leandro@leandro-laptop:~/ndiswrapper-1.49$ make
make -C driver
make[1]: se ingresa al directorio `/home/leandro/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/leandro/ndiswrapper-1.49/driver
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/leandro/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Alto.
make[2]: *** [_module_/home/leandro/ndiswrapper-1.49/driver] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/home/leandro/ndiswrapper-1.49/driver'
make: *** [all] Error 2
```

I know it's in spanish so:
Directorio means directory
se sale means to get out
se ingresa means to get in

Are that errors that appear at the end of the code right?
I mean, must the appear?

You should not have to build ndiswrapper.  The setup for your wifi chip-set is available in the restricted repos.  Read my last post.

---

### Post by Papenco on 2008-06-20
Oh, thanks. Did you get the Wireless CArd working on the E1505 Laptop?
Can you explain how?
Thanks.

---

### Post by pytheas22 on 2008-06-20
> That's odd... I also have a Dell E1505, same wifi chip-set, and it is the B43 driver that is needed. The driver that should be blacklisted is the bcm43xx.

The last I knew, Broadcom 4311 cards didn't work reliably with the native drivers, but that could have changed when b43 was released.  If dwhitney67 is sure that it works, then he or she probably knows better than me, as I don't have that kind of laptop.  The ndiswrapper way should also work but since you're having problems, try b43 first I guess.

As for the make errors, did you make sure to run these commands first:
```

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r`
```

if not, it would be the problem.  But like I said, I would stop worrying about this for now, and try the b43 method first.

---

### Post by Papenco on 2008-06-20
I'm sorry for being so newbie but what do you mean by b43 way?

---

### Post by dwhitney67 on 2008-06-20
What's strange is that I did not have to do anything, other than accept Ubuntu's pop-up query if I wanted to enable the restricted drivers... which of course I did.  That's it!  This all took place after I had installed Ubuntu.

Btw, my /etc/modprobe.d/blacklist looks like the following.  Note the bcm43xx is the (kernel) driver that is blacklisted for the E1505's wifi.
```
$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
```

---

### Post by dwhitney67 on 2008-06-20
Papenco, see if you have this Gnome menu item...  **System -> Administration -> Hardware Drivers**.

It is using this Gnome interface that I was able to enable the restricted drivers for both my ATI video chip-set and the Broadcom B43 wifi chip-set.  If you have this interface, then select "Enabled" for the Broadcom.

---

### Post by Papenco on 2008-06-20
Ok, that pop op offering me to update my drivers also appeared. I accepted it. And after installing it I could see the wireless networks, but as the title of my thread says, I cuoldn't connect. I click the symbol with the two computers in the top right of my screen and I CAN actually see the wireless networks, what I can't do, is to connect to them.
Thanks although. And, any idea?

---

### Post by pytheas22 on 2008-06-20
> I'm sorry for being so newbie but what do you mean by b43 way?

It's ok, sorry for not explaining this more.

Basically there are two ways to make your card work: one way is by using ndiswrapper, which is the method used in the tutorial that I suggested.  As I said earlier, ndiswrapper makes the card work by using the Windows driver.

The second method is by using the b43 driver.  b43 is an open-source wireless driver for Linux.  I thought that your wireless card didn't work with b43 yet, but I guess I was wrong.

So to Papenco, please do this to try the b43 method:

type in a terminal:
```

sudo gedit /etc/modprobe.d/blacklist
```

Erase everything in that file and in its place put all of this:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
```

Now run the command:
```

sudo apt-get install b43-fwcutter
```

If you are prompted to automatically download firmware, say yes.

Now reboot.  After rebooting, go to System>Administration>Hardware Drivers (I don't know what this is called in Spanish, but if you can't figure it out, I can post a screenshot).  You should see an item relating to your wireless card there and a checkbox asking if you want to use the card.  Click the box to enable it.  Ubuntu may then ask you to download some things to make the card work; do this.  Then reboot and see if your wireless works.

Hopefully this will solve the problem.  If not, the ndiswrapper method should still also work, but the b43 method is better.

---

### Post by pytheas22 on 2008-06-20
> Ok, that pop op offering me to update my drivers also appeared. I accepted it. And after installing it I could see the wireless networks, but as the title of my thread says, I cuoldn't connect. I click the symbol with the two computers in the top right of my screen and I CAN actually see the wireless networks, what I can't do, is to connect to them.
Thanks although. And, any idea?

You're all typing faster than me :)

What is the output now of:
```

iwconfig
iwlist scan
```

Also try running this command and see if it helps:
```

sudo apt-get install b43-fwcutter
```

---

### Post by dwhitney67 on 2008-06-20
> **pytheas22 said:**
> You're all typing faster than me :)

What is the output now of:
```

iwconfig
iwlist scan
```

Also try running this command and see if it helps:
```

sudo apt-get install b43-fwcutter
```

Pytheus - I understand you are trying to help, but many of the suggestions you are asking Papenco to install are _not_ necessary.  He can see the wireless access points now.

---

### Post by dwhitney67 on 2008-06-20
Papenco

Are you trying to connect to a wireless access point that is protected with a security key, or one that has no protection?

Either way, just to get you going from a clean slate, remove the following directory that holds the keyrings.  Sometimes it contains garbage.

$ rm -rf .gnome2/keyrings

Then try to connect to the wireless access point of your choice.  If you are attempting to connect to a protected access point you should see a pop-up querying you for the security password.  You will also be prompted to insert a password to protect your newly created keyring.  I use my login-password, but you can use whatever you like.

---

### Post by Papenco on 2008-06-20
Ok.
First: I'm writting from my XP partition because after reinstalling the driver, I couldn't even connect with my cable connection.
Second: Yes, my Wireless network has a password.
Third: How do I remove this thing you say?
Fourth: Why is this not working? I mean, if it worked for you and we both have the same laptop.
Thanks

---

### Post by dwhitney67 on 2008-06-20
I initially had Ubuntu 7.10 on my system, then I upgrade to 8.04.  In both cases, the wireless always worked (because I was prompted if I wished to use the restricted drivers).

The Ethernet controller I have in my laptop (for wired connections), as verified by running '**lspci**' is:
```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```

The wifi chip-set:
```
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

In both cases, I believe it is the b43 driver that is used.  This is important... you must verify that the 'bcm43xx' driver is blacklisted!

Run this command to verify if it is...
```
$ cat /etc/modprobe.d/blacklist | grep bcm43xx
```

If this command returns nothing, then the 'bcm43xx' is not blacklisted.  You will need to add it to the file.
```
$ sudo su
# echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
# reboot
```

---

### Post by Papenco on 2008-06-20
Ok, I will try that when I solve the connection problem, I can't even connect by the ethernet cable :lolflag:. 
Thanks although, I was planning to reinstall ubuntu to see if I can make it work from the starting. I will you how I go.

---

### Post by dwhitney67 on 2008-06-20
If you plan on doing a re-install, make sure you use the wired-connection during installation.  For some bizarre reason, it helps the Ubuntu installer set up the network controller correctly.

Also, moments (and this could be a minute or two) after you first log in, Ubuntu will prompt you concerning the restricted drivers... one for the ATI (if that is what you have) and the other for the Broadcom wifi chip-set.  Enable them if applicable.

---

### Post by Papenco on 2008-06-20
Ok will have al that in mind. I'm planning doing the reinstallation in about 10 minutes. 

Thanks for your help, I'll let you know how i'm going after finishing installation.

---

### Post by thinking2loud on 2008-06-21
Do you have security turned on for the wireless network?  I'm on a Dell E1505 now.  Works fine.  I never have a problem connecting to an unsecured network.  I have some sort of problem (which I haven't figured out) connecting to a WPA2 network.

---

### Post by Papenco on 2008-06-21
OK, I have finished with the re installation. I have installed this b43 thing and the result is the same as before, I can see my Wireless Network but when trying to connect to it and typing the pass; after 20 - 40 seconds, it asks for the pass again. I tried connecting to a non-secured Network but it doesn't work either. 
Any Help?
Thanks.

---

### Post by dwhitney67 on 2008-06-21
Have you tried removing the existing keyrings directory that is located in ~/.gnome2:
```
$ rm -rf ~/.gnome2/keyrings
```
Then try to connect to your wireless access point.  I am able to connect to an access point that uses WPA Personal.  I do not have any idea if WPA2 would work or not... I have never tried it.

Btw, make sure that wpa_supplicant is running.  It should automatically be started when the system is booted.  You can verify if it is running or not with:
```
$ ps -ef | grep wpa
```
As to what launches wpa_supplicant, I haven't a clue, but you should see something like:
```
root      6056     1  0 Jun20 ?        00:00:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global
```

---

### Post by Jazzy_Jeff on 2008-06-21
What type of encryption are you using on your router? Make sure it is the same as you are telling the connection manager. I had the same problem until I made sure it was connecting through WEP.

---

### Post by Papenco on 2008-06-21
But I also can't connect to the non-secured networks. I can see them all, but can't connect.
What shall I do?
Thanks.

---

### Post by Papenco on 2008-06-21
Ok, I must tell everyone: THANKS FOR YOUR HELP, but I finally realized what I had to do; it was quite complicated.
THANKS.

---

### Post by unutbu on 2008-06-21
Since others may someday reach this thread searching for an answer, would you please give some details of the solution? Much thanks.

---

### Post by Papenco on 2008-06-21
Ok, and sorry for not doing it, I didn't realize.

I had to do this things in this order:

1) Install the b43 driver with the hardware driver utility. System -- Administration -- HArdware Drivers.

2) Install the Driver with ndiswrapper. (There's a nice HOWTO in the tutorial section.

3) When trying to connect to my NETWORK, changed the type of password to hexadecimal 64/128 bits type.

Reboot.

Again, thanks to everyone that helped.

---

### Post by dwhitney67 on 2008-06-22
I'm surprised that you need to perform step 2.  I didn't... maybe my system is special?

I don't understand step 3... are you using WEP?  Be aware that someone can easily break (derive) your password and begin using your wireless access-point (if you are using WEP).

---

### Post by Papenco on 2008-06-22
I know, but WPA or WPA personal types of passwords aren't available for me to choose.

---

### Post by DrRSP on 2008-06-23
Hi

I appear to be having a similar problem in Hardy. I'm running a Dell with a Netgear WPN111 & a Netgear DG834PN router with WPA-PSK (TKIP encryption by default). I too am new to Unbunto, and very pleased with it over windows, right up to configuring wireless. I've done the ndiswrapper thing (looking at some very good tutorials on this forum), and supplicant appears to be running ok.

I can see wireless networks and cannot connect to my own WPA network (all other networks are protected too, so have not tried an unsecure network). The wireless network manager repeatedly asks for the paraphrase - I can enter this, and it times out again and repeats the request for a password. I'm assuming this is should be an ASCII password and not hex?  Any clues? Thanks in anticipation!](*,)

---

### Post by unutbu on 2008-06-23
DrRSP, try the instruction at [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495).

Regarding the WPA PSK password: Was the password set in ASCII or hex on the router? Whichever way you did it on the router is probably the way it should be entered in /etc/wpa_supplicant.conf.

---

### Post by DrRSP on 2008-10-29
Hi

I'd put the password phrase in ASCII, same as the router.  Here are my further adventures with some command output. If it appears a little random, its because I'm still learning/persevering! Goodness, I must be close though...

Thanks. Richard

**Situation:**
I'm still a newcomer to linux(even after the earlier posts), and finding wireless networking far too time consuming and frustrating!  I have a dell laptop with a Netgear WPN111 usb wireless adapter. I checked the ubuntu doc etc and appear to be going around in circles, although I did find the wifi docs wireless troubleshooting guide excellent. I lost the plot on notes on WPA (3.3.2) though.

Having installed ndiswrapper, WPA supplicant etc., I cannot get WPA to work. However, I can use manual configuration for an open unsecured connection (see commands and output below).

Iwconfig:
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:D2:A4:C0
                    ESSID:"router1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:96:19:bb
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe96:19bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4680007 (4.4 MB)  TX bytes:582900 (569.2 KB)

iwlist scan:
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:D2:A4:C0
                    ESSID:"router1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


**Symptoms:**
Using network administration (manual configuration) WPA settings are:
Roaming unchecked
Wireless connection
EESID router1
WPA Personal (WPA and WPA2 on Router)
Password in ASCII (same as Router)

Driver OK, just for good measure, lshw:

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:96:19:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.52+NETGEAR,09/26/2005,1.5.0.21 multicast=yes wireless=IEEE 802.11g

Still no connection is found in iwconfig (below):

iwconfig:
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:96:19:bb
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:0f:b5:96:19:bb
          inet addr:169.254.7.71  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

file:///etc/modprobe.d/ndiswrapper:
alias wlan0 ndiswrapper
file:///etc/network/interfaces:

auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid router1

auto wlan0
file:///etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

**Finally**
I also note that I've edited my wireless network using the gnome nm-editor 0.6.6 from the launcher.... settings appear stored (in network interfaces above, could there be a clash for binding to ndiswrapper?).

Help! It was never this hard in windows, but I don't want to go back there! Is there simple step by step advice I've missed (I've looked and I'm now confused, with different network managers and auto start up configurations)... Either that or could some kind soul take pity. Thanks in anticipation.](*,)

---

### Post by unutbu on 2008-10-29
Hi DrRSP, unfortunately, I don't know enough to help you directly. However, perhaps give this guide a try:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

It is rather long, so take it slow and follow it point by point. If you have any questions on any point, make a post. The squeaky wheel does get the grease.

I noticed a few things there that you could try:
[list]
[*]Make sure wpasupplicant has been installed
[*]Your /etc/network/interfaces needs some editing
[list]
[*]Maybe try the static connection settings, along the lines of what weiman01 describes in the guide.
Note your gateway address may be different than his, so change the numbers as appropriate
[*]He also has a number of other wpa-specific lines that yours seems to be lacking
[*]The wpa-psk key should be in hex, not ASCII.
See "WPA PSK Key Generation"
[/list]
[*]Note weiman01's comments in the section "Post this if you are stumped". 
[*]Finally, a tip: There are some knowledgable forum helpers who search the Absolute Beginner Talk (ABT) forum for unanswered posts. Some of these people do not attempt to read threads (like this one) which have many posts already. So to run your post by these people it is best to start a new thread in the ABT forum.
[/list]

Good luck.

---

### Post by pytheas22 on 2008-10-29
DrRSP: first of all, you may want to try connecting using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  Sometimes wicd has better luck trying to negotiate WPA authentication.  There are installation instructions for wicd on its site, but if you can't figure it out, let me know.  Note that you will have to uninstall Network Manager to install wicd (the package manager should deal with this automatically for you, but if not, uninstall NM using Synaptic).

You should also look at (or post here) the output of:
```

dmesg | grep -e ndis -e wlan
```

If the ndiswrapper driver is loading correctly, usually it prints out a line in dmesg regarding which encryption methods it thinks it should support.  From the behavior you describe, I wonder if ndiswrapper simply doesn't think that it supports WPA at all.  I see that your Windows driver was built in 2005, so you'd think it would support WPA, but you never know.  You could try installing a different Windows driver (i.e. the Windows 2000 driver instead of the XP one, or version 1.0 instead of 2.0); sometimes this makes a difference.

Are you positive that your card itself supports WPA?

It would also be good to see the output of:
```

lsusb
```

while the card is plugged in.  With that information, we'd know your precise chipset, which would make it might be possible to google around for a possible solution to your problem.

If none of the above helps, then you should follow the link from unutbu's post, which will have you doing WPA negotiation manually.  That's not fun, but if all of the GUI connection managers fail, it's the only way to figure out what's wrong.

---

