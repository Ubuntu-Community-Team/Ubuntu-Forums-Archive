---
title: "slow wireless with linux - any ideas?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-13
Hi

I have been using Ubuntu for a few months and have no regrets to switching other than my Wireless internet seems to be a lot slower than when I had windows.

Nothing has changed with the location of routers, or computer, no hardware changes - so my only conclusion is ubuntu (for some unknown reason) is slower.

The change in speed is very noticeable, and annoying - for example a 3min video on youtube may take 10mins to load, and my average download speed now is 20kbs, whereas it was 100kbs.

when I installed Ubuntu, i installed the packages 
jockey-common
jockey-gtk 

which are common drivers (I think)

has anyone else experienced this, and any ideas?

thanks - much appreciated

---

### Post by tangibleorange on 2008-08-13
> **phantomjoker said:**
> Hi

I have been using Ubuntu for a few months and have no regrets to switching other than my Wireless internet seems to be a lot slower than when I had windows.

Nothing has changed with the location of routers, or computer, no hardware changes - so my only conclusion is ubuntu (for some unknown reason) is slower.

The change in speed is very noticeable, and annoying - for example a 3min video on youtube may take 10mins to load, and my average download speed now is 20kbs, whereas it was 100kbs.

when I installed Ubuntu, i installed the packages 
jockey-common
jockey-gtk 

which are common drivers (I think)

has anyone else experienced this, and any ideas?

thanks - much appreciated

if you wireless card is in the computer, could you please post the output of this command:
```
lspci
```
or if it's USB, use this one instead:
```
lsusb
```

also, the output of this command:
```
iwconfig
```

---

### Post by phantomjoker on 2008-08-14
> mckenzie@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


and

> mckenzie@ubuntu:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Agapanthus"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:B4:D2:D8   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=56/100  Signal level=-72 dBm  Noise level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Is that kind of whats expected?

or is there a problem?

cheers

---

### Post by tangibleorange on 2008-08-14
OK those commands were just to show what card you are using. Jockey is just a program that allows the download of restricted drivers. You can find it at System > Administration > Hardware Drivers.
Does it offer any drivers relating to the network for download? If so, it should be pretty straightforward to install them with jockey. Could you also post the output of:
```
lsmod | grep bcm
```
and then right click on the network icon on one of your panels and select 'Connection Information'. What does it say next to 'driver'?

---

### Post by phantomjoker on 2008-08-14
I have no output to the above command - and apparently I don't have a driver?! (according to my 'connection information')

and this is what my hardware driver information is -

[IMG]http://i38.tinypic.com/s6ncle.png[/IMG]

so it looks like its recognised...

---

### Post by tangibleorange on 2008-08-14
have you tried following the instructions in this thread?
[http://ubuntuforums.org/showthread.php?t=880218]("http://ubuntuforums.org/showthread.php?t=880218")
if it still doesn't work, we can try and set up a different driver using ndiswrapper, but try the stuff in the thread first.

---

### Post by phantomjoker on 2008-08-14
on the instructions posted I have to create a file - it says I dont have the permissions.... how do I sudo in gui, or do i have to do create the file within the terminal? if so - how?

thanks

---

### Post by fdsasdf on 2008-08-14
I don't know what's going on with the driver stuff (to lazy to read it),  but I can help you with the sudo thing.
Gnome usually uses gksudo to run programs with higher privileges.  But, you'll probably have to create a "shortcut" to it.
I think it would be easier to use 'nano' on the command line (Nano is a nice simple terminal text editor).  You would have to type "sudo nano -w /path/to/file"
The "-w" switch for nano is there to make sure that it doesn't use wordwrap to screw up all the line breaks in your file.
If you want to use gedit for this kind of thing in the future, you can make a .sh or .desktop file.
The .sh file would need to be:
#!/bin/sh
gksudo gedit

And you'll have to make it executable in the file manager (or w/ chmod u+x).

---

### Post by prshah on 2008-08-14
> **phantomjoker said:**
> 
wlan0 IEEE 802.11g ESSID:"Agapanthus"
Mode:Managed Frequency:2.462 GHz Access Point: 00:11:50:B4:D2:D8
[color=red]Bit Rate=1 Mb/s[/color] Tx-Power=27 dBm
Retry min limit:7 RTS thr:off Fragment thr=2346 B
Link Quality=56/100 Signal level=-72 dBm Noise level=-65 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


Ooohh too slow. Try the following command in a terminal (Applications-Accessories-Terminal), then run iwconfig again to see if it's changed. ```
sudo iwconfig wlan0 rate auto
sudo /etc/init.d/networking restart
```

---

### Post by crjackson on 2008-08-14
If it says anything less than 54Mb/s, open up (as root)```
gksudo gedit /etc/rc.local
```  

and add the following lines: 
```

ifconfig wlan0 up
iwconfig wlan0 rate 54M

```
Replace wlan0 with **YOUR** interface name. Worked for me. Then from the terminal run
```
sudo /etc/init.d/networking restart
```

---

### Post by phantomjoker on 2008-08-14
prshat - did nothing - same text - heres what I did, and what I got =

> mckenzie@ubuntu:~$ sudo iwconfig wlan0 rate auto
[sudo] password for mckenzie: 
mckenzie@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
                                                                         [ OK ]
mckenzie@ubuntu:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Agapanthus"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:B4:D2:D8   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=56/100  Signal level=-72 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mckenzie@ubuntu:~$ 


(I apreshiate the help - but I do know how to open a terminal :) even if my thread is on a simple topic)

---

### Post by phantomjoker on 2008-08-14
crjackson - which bit is MY interface name?

> wlan0     IEEE 802.11g  ESSID:"Agapanthus"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:B4:D2:D8   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=56/100  Signal level=-72 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by tangibleorange on 2008-08-14
your interface is wlan0.

as for creating the file, you simply need to type something in it and save it, and the file will be created:

```
gksu gedit /etc/modprobe.d/blacklist-bcm43
```

and add the lines from the thread.

---

### Post by phantomjoker on 2008-08-14
nope - no luck - just tried it and neither versions connected - so had to undo what I did...
scary not having any internet for a sec there :|

---

### Post by phantomjoker on 2008-08-14
crjackson - tried what you said - didn't really know how to right it so tried

> #ifconfig wlan0 up
#iwconfig wlan0 rate 54M

exit 0

> ifconfig wlan0 up
iwconfig wlan0 rate 54M

exit 0

> #!/bin/sh -e
#ifconfig wlan0 up
#iwconfig wlan0 rate 54M

exit 0

and 

> !/bin/sh -e
ifconfig wlan0 up
iwconfig wlan0 rate 54M

exit 0

but after a network restart and then looking at my iwconfig - nothing changed - did i enter it wrong or is it just not working for me?

---

### Post by tangibleorange on 2008-08-15
ok i guess it would be best to try ndiswrapper. a couple of questions:

what model is your computer (including any numbers)?
do you still have a working windows installation on your computer, and if so, what release? (XP, vista)

---

### Post by phantomjoker on 2008-08-15
Um, my computer is home built so - I can't remember whats in it. Can I type something into the terminal to find out the spec or is it a case of hands and knees?

also no - i have no windows partition, only Ubuntu. I don't know why you want to know - but incase it helps I do have bartPE on disk - but i doubt it helps :|

---

### Post by tangibleorange on 2008-08-15
no i was just wondering if you had a working wireless driver we could use in ndiswrapper. anyway:

Download & load ndiswrapper:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
sudo depmod -a
sudo modprobe ndiswrapper
```
open up a blacklist:
```
gksu gedit /etc/modprobe.d/blacklist-bcm43
```
Add these lines:
```
blacklist b43
blacklist ssb
blacklist b43legacy
```
and save&close. now, add 'ndiswrapper' to /etc/modules:
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
sudo ndiswrapper -m
```
get the windows driver and install it:
```
wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
mkdir ndis_temp
mv sp33008.exe ndis_temp
cd ndis_temp
sudo apt-get install cabextract
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl5.inf

```
check the only entries in /etc/network/interfaces are
```
auto lo
iface lo inet loopback
```
by running this command:
```
gksu gedit /etc/network/interfaces
```
delete any other lines (unless then begin with a '#').
and reboot. now try connecting with the network icon as usual and test your download speed!

if it doesn't work:
```
sudo rm /etc/modprobe.d/blacklist-bcm43
```
remove the line 'ndiswrapper from /etc/modules:
```
gksu gedit /etc/modules
```

---

### Post by phantomjoker on 2008-08-15
i got this during the when adding ndis..to the modules folder...

 > mckenzie@ubuntu:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************



what does this mean?

---

### Post by tangibleorange on 2008-08-15
that's fine. it's just a warning. you can contiune from that point.

---

### Post by phantomjoker on 2008-08-15
This is whats in my network/interfaces - do i need to remove anything?

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.2.200
netmask 255.255.0.0
gateway 192.168.2.1

---

### Post by tangibleorange on 2008-08-15
no it's fine. you should just be able to reboot now and it will work.

---

### Post by phantomjoker on 2008-08-15
ok, and just to check - if I can't connect after the reboot, I follow the next set of instructions? (of which i've save to a text doc.)

---

### Post by tangibleorange on 2008-08-15
yep (and then reboot). good luck!

---

### Post by phantomjoker on 2008-08-15
Nope, unfortunatly did not connect to the internet. I didn't have the option to connect to a wireless network either, and the only connection option was point to point - of which i dont have. Thanks for trying though.

---

### Post by tangibleorange on 2008-08-15
ok could you post the output of:
```
ndiswrapper -l
```

---

### Post by phantomjoker on 2008-08-15
yep - i get 

> mckenzie@ubuntu:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)


---

### Post by tangibleorange on 2008-08-15
ok try this:
```

sudo ndiswrapper -r bcmwl5
wget http://home.nc.rr.com/thehinnants/stuff/drivers/bcmwl5.zip
unzip bcmwl5.zip
cd bcmwl5
sudo ndiswrapper -i bcmwl5.inf
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
echo 'ndiswrapper' | sudo tee -a /etc/modules

```
open up this file:
```
sudo gedit wirelessfix.sh
```
and paste this:
```
#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 
```

restart. now run the wireless fix script:
```
cd bcmwl5
sudo sh wirelessfix.sh
```

now if that doesn't work:
```
sudo ndiswrapper -r bcmwl5
cd bcmwl5
sudo ndiswrapper -i bcmwl5a.inf
```

restart. now run the wireless fix script:
```
cd bcmwl5
sudo sh wirelessfix.sh
```

and if THAT doesn't work, back to the old config:
[LIST]
[*]remove 'ndiswrapper' from /etc/modules (using gksu gedit)
[*]remove 'blacklist bcm43xx' from /etc/modprobe.d/blacklist (using gksu gedit)
[*]do NOT run the wirelessfix script (duh)
[*]reboot
[/LIST]
good luck! hopefully we'll get it working soon :guitar:!

---

### Post by phantomjoker on 2008-08-15
ok - this time I connected... (using the first list of instructions, i didnt have to use the 'if that doesn't work' bit...)

But whats strange is the command
```
sudo ndiswrapper -i bcmwl5
```
did not work - but i carried on.

then after the reboot, but before i entered
```
 mckenzie@ubuntu:~/bcmwl5$ sudo sh wirelessfix.sh 
```
i was connected, then once i entered it my connection died for a second then came back - and i did a 

iwconfig but got the same =
> mckenzie@ubuntu:~/bcmwl5$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Agapanthus"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:B4:D2:D8   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=55/100  Signal level=-73 dBm  Noise level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by tangibleorange on 2008-08-15
yep sorry i forgot you need to specify the file with a .inf at the end. are you using ndiswrapper at the moment? (or did you restore the old config using the instructions at the bottom?)

---

### Post by phantomjoker on 2008-08-15
well i didnt restore anything so - i guess ndiswapper?!

um, do I need to go back and re enter that command differantly?

---

### Post by tangibleorange on 2008-08-15
ok. the first command will crash your internet until reboot i'm afraid, so you might wanna save this to a text file:
```
sudo rmmod ndiswrapper
sudo ndiswrapper -r bcmwl5
cd bcmwl5
sudo ndiswrapper -i bcmwl5.inf
```

and reboot. then run the script. 
then run:
```
sudo iwconfig wlan0 rate 54M
sudo /etc/init.d/networking restart
```
if that doesn't work, you can continue with the instructions in that part of the thread (with the bcmwl5a driver). then repeat the two commands above after a reboot.

---

### Post by phantomjoker on 2008-08-15
i have done the first set of commands, but not yet rebooted - and my internet _did not_ crash.. is that bad?? (it does seem slower though)

---

### Post by tangibleorange on 2008-08-15
is there any output from this command:
```
lsmod | grep ndiswrapper
```

---

### Post by phantomjoker on 2008-08-15
i think i F***ed up?!

you edited the text and i did the commands before you entered the 
sudo ndiswrapper -r bcmwl5
command...

so i did it after the 
sudo ndiswrapper -i bcmwl5.inf

and it seemed to work... then i didnt think any of that worked... since i did it in the wrong order.

so i started again and when i entered 
sudo rmmod ndiswrapper

i got 

mckenzie@ubuntu:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules


AH!

---

### Post by phantomjoker on 2008-08-15
No, no output...

---

### Post by tangibleorange on 2008-08-15
its fine! reboot and run the wireless fix script. then, if there is output from the command above, run the two commands about changing the rate.

---

### Post by phantomjoker on 2008-08-15
ok, rebooted and enter the command 
lsmod | grep ndiswrapper

then did a iwconfig and its changed!
> mckenzie@ubuntu:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Agapanthus"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:B4:D2:D8   
          [COLOR="Red"]Bit Rate=18 Mb/s[/COLOR]   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=60/100  Signal level=-69 dBm  Noise level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


did you want me to enter the changing rate command??

---

### Post by phantomjoker on 2008-08-15
hate to break it to you - but i ran the rate change commands and lost internet - i am now on another computer - how do I undo the last two commands?

```
sudo iwconfig wlan0 rate 54M
sudo /etc/init.d/networking restart 
```

cheers

---

### Post by phantomjoker on 2008-08-15
ok, so i did a reboot, and im back online... but my Bit rate has returned to 1mb/s

AHH traveling in circles I SWEAR! 

thanks for all your help!

---

### Post by nicedude on 2008-08-15
It looks to me like maybe that means your adapter just couldn't use 54MB speed so maybe try some slower ones like 11MB and see what the fastest yours supports is.

---

### Post by tangibleorange on 2008-08-16
yeah i'm afraid that the post above may be correct. if you haven't tried already...
[LIST]
[*]reboot
[*]run the wirelessfix script
[*]run the change rate commands. instead of 54M, you could try putting 'auto' (no quotes)
[*]try downloading a file.

if that doesn't work, i think the poster above may be (sadly) correct.[/LIST]

---

### Post by phantomjoker on 2008-08-16
ok, I shall give that a go. What do you think could be stopping me from getting 54+ MB?
 my network card or router or something else?

cheers

---

### Post by tangibleorange on 2008-08-17
well you don't use a driver for you router so it must be the card. if you do decide to buy another card, I know a good USB one that works out the box at 54M.

---

### Post by prshah on 2008-08-17
> **phantomjoker said:**
> What do you think could be stopping me from getting 54+ MB?



AFAIK (I have not been able to confirm this) 54 Mbps will work only for unencrypted connections. This is not a linux limitation.

Encrypted connections will work at 11Mbps top speed, but will speed degrade with signal quality.

---

### Post by phantomjoker on 2008-08-17
the maximum I have got for bit rate when i typed in iwconfig is 18 so that can't be it

---

