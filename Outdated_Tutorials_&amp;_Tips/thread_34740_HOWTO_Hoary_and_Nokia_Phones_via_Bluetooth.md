---
title: "HOWTO: Hoary and Nokia Phones via Bluetooth"
date: 2005-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by globalspace on 2005-05-16
**This how to is tested with Hoary and Nokia 6630 and a Dongle Bluetooth (Usb Bluetooth)** 

*With this How To you could :*

- Send Files via Bluetooth from your Pc to your Nokia Phone
- Send Files via Bluetooth from your Nokia Phone to your Pc
- Do everything you want with Bluetooth  :-P 

**Let's Start** 


- Open Synaptics

> sudo synaptic 

- Install this packages and their dependences

> gnome-bluetooth
obexserver
bluez-utils


- Load this modules into the kernel : l2cap, rfcomm

> sudo modprobe l2cap 
> sudo modprobe rfcomm 

- Create the new device of the Dongle. We create a virtual bind from the Usb to the Serial Device

> sudo mknod /dev/rfcomm0 c 216 0

- Activate the Bluetooth in your Phone . For the Nokia 6630 :

> Menu -> Connect. -> Bluetooth -> On 
> Menu -> Connect. -> Bluetooth -> My phone's visibility -> Shown to all 
> Menu -> Connect. -> Bluetooth -> My Phone's Name -> "Insert a name for your phone" 

- Scan for your phone 

> hcitool scan 
This utils will scan the devices's Bluetooth ... it'll show something like this :

> Scanning ...
        00:11:9F:C0:FE:21       YOUR_PHONE_NAME 

The first number is your Phone's Address. Obviously yours will be different ! :)
Copy your Address on a post-it ! 

- Edit your /etc/bluetooth/rfcomm.conf

> sudo gedit /etc/bluetooth/rfcomm.conf 

Cancell all and insert this :

> rfcomm0 {

  device ADDRESS_OF_YOUR_PHONE;
  channel 10;
  comment "What you want  ;)";

}  

In ADDRESS_OF_YOUR_PHONE you must insert the Address wich you have write in the Post it :) 
For example :

> rfcomm0 {

  device 00:11:9F:C0:FE:21;
  channel 10;
  comment "My Nokia Phone";

}  

- Add the Nokia Channel (10) to communicate with your phone

> sudo sdptool add --channel=10 OPUSH 

- Do the binding

> sudo rfcomm bind /dev/rfcomm0 ADDRESS_OF_YOUR_PHONE 10

for example :  rfcomm bind /dev/rfcomm0 00:11:9F:C0:FE:21 10

- Now we can test the connectivity 

To **Send from the PC to your Nokia Phone** 
> gnome-obex-send filename 
for example 
gnome-obex-send /home/massi/Desktop/Video.3gp
It'll show a prompt with the Bluetooth Device. Select your Phone and Click OK.

To **Send from Your Nokia Phone to your PC** 
Activate the ObexServer on your PC to accept connections from other Bluetooth Devices :
> obexserver 
Go to your Gallery of the Phone and do Send file with Bluetooth. For Nokia 6630 :
> Menu -> Gallery -> Images -> NamePhoto.jpg -> Options -> Send -> Via Bluetooth 
and Select your Pc and click SELECT
You can find your files into the temp directory /tmp/

**Tips** 

This works perfectly on Nokia 6630 but i think it could works on ALL Nokia Phone with Bluetooth because we use the Channel number 10 which is the default channel of all Nokia Phone.
I think also that if you know the channel number of your Phones which isn't Nokia you could replace in the How To and it could works !

Everytime that you reboot you must re apply this things (which you could insert into a boot-script)
> modprobe l2cap
sudo modprobe rfcomm
sudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
sudo rfcomm bind /dev/rfcomm0 YOUR_PHONE_ADDRESS 10

**Have Fun Ubuntu's user !!!**

---

### Post by rwabel on 2005-05-16
you are my hero!! now bluetooth is finally working for me.
I've a sony ericsson T610 and channel 10 works also for me. By default it was set to 1. I've no idea what channel means what. If someone knows, it would be great to le me know

in rfcomm.conf you could also set bind to yes, maybe this would make some commands obsolete. Unfortunately I know barely nothing about bluetooth and linux.
it looks like that for me now
 ```
 rfcomm0 {
  bind yes;
#	# Bluetooth address of the device
	device 00:0E:07:D3:B0:08;
#	# RFCOMM channel for the connection
	channel	10;
#	# Description of the connection
	comment "My T610";
}
```

---

### Post by globalspace on 2005-05-16
[QUOTE=rwabel]you are my hero!! now bluetooth is finally working for me.
I've a sony ericsson T610 and channel 10 works also for me. By default it was set to 1. I've no idea what channel means what. If someone knows, it would be great to le me know

in rfcomm.conf you could also set bind to yes, maybe this would make some commands obsolete. Unfortunately I know barely nothing about bluetooth and linux.
it looks like that for me now
 ```
 rfcomm0 {
  bind yes;
#	# Bluetooth address of the device
	device 00:0E:07:D3:B0:08;
#	# RFCOMM channel for the connection
	channel	10;
#	# Description of the connection
	comment "My T610";
}
```[/QUOTE]


i'm very happy for you !
glad that my how to is profit  :-P

---

### Post by derrick1985 on 2005-05-25
Thanks man, I was FINALLY able to get my motorola V551 to transer files! (now, if I could only get my webcam working i'd get completely rid of windows)

For anybody with a Motorola one, here is what you have to do:

First, go into your menu (middle button) connections---Bluetooth---setup

Turn on Bluetooth. Turn on "Find Me" (nokia reference shown to all)

Follow tutorial from hcitool down to sending/receiving files.  

To be able to send files from your phone, you will first have to send a file to it. Why? Motorola has to be able to have a connection in the list in order to send files from it, and since we can't manually add one, we have to give one to the phone. Start up a file transfer of a file (any file) and then as soon as transfer starts, cancel it. There, our phone now has the neccessary settings to send files.

My example, I took some pictures. Lets get my pictures. Goto settings--- Multimedia---Pictures. Select a picture you want to send to your PC.  Highlight it and press the middle button. A bunch of options are shown, scroll down to MOVE. The name of your computer that you sent a file to your phone from, will be listed. MAKE SURE OBEXSERVER is on, and you can transfer files no problem. Same things goes with recorded sounds and videos.

NOTE: Unlike windows, we cannot copy and paste more than one file at a time. (unless someone knows how) because after one files transfers, obexserver shuts down, so you have to reopen it everytime.

Anyone know how to keep obexserver on all the time, please post it here, it is REALLY frustrating.

---

### Post by globalspace on 2005-05-26
[QUOTE=derrick1985]Anyone know how to keep obexserver on all the time, please post it here, it is REALLY frustrating.[/QUOTE]

i think you could run at startup like all the command ... ;)

---

### Post by derrick1985 on 2005-05-26
[QUOTE=globalspace]i think you could run at startup like all the command ... ;)[/QUOTE]

No, I mean when I type obexserver to receive a file, it receives it and then the program shuts down. I have to turn it on everytime to receive a file.

---

### Post by globalspace on 2005-05-26
[QUOTE=derrick1985]No, I mean when I type obexserver to receive a file, it receives it and then the program shuts down. I have to turn it on everytime to receive a file.[/QUOTE]


try to use 

> gnome-obex-server 

let me know  ;-)

---

### Post by derrick1985 on 2005-05-26
Better, but still a no go. Every time my computer receives a file now, it asks to save it, and that interfers on the continuous transfer. The good news is i don't have to continuously start obexserver after every upload.

Oh yeah, and gnome-obex-server now saves the files in my home directory, that's another plus.

---

### Post by andreasDK on 2005-05-26
When my 6600 finds my PC it asks for a code.

Hence everything I type is in asterixes i cannot spell my user/root code.

Does anyone know of a solution to this?

---

### Post by nullzero on 2005-05-27
worked like a charm for me!
thx a lot man!
Keep up the good brain use :D

---

### Post by globalspace on 2005-05-27
[QUOTE=andreasDK]When my 6600 finds my PC it asks for a code.

Hence everything I type is in asterixes i cannot spell my user/root code.

Does anyone know of a solution to this?[/QUOTE]


i think is going to paring the devices ... try to set a number .. like "1" and then type it in cell ... or try to set the default code of nokia phone "12345"

---

### Post by bk452 on 2005-05-28
What's the purpose of doing this?  What do you do with it?

---

### Post by derrick1985 on 2005-05-28
[QUOTE=bk452]What's the purpose of doing this?  What do you do with it?[/QUOTE]
This allows you to transfer files to and from your phone. Ex. I have a camera phone, and I usually want a copy of the pictures on the phone stored on my pc, so I use Bluetooth to transfar the files to my computer.

---

### Post by bk452 on 2005-05-28
[QUOTE=derrick1985]This allows you to transfer files to and from your phone. Ex. I have a camera phone, and I usually want a copy of the pictures on the phone stored on my pc, so I use Bluetooth to transfar the files to my computer.[/QUOTE]


Way too cool!!!  Thanks!!! I have to pay .25 a pic to load it into my pc.  You just saved me a lot of money!

---

### Post by TheCondor on 2005-05-28
[QUOTE=andreasDK]When my 6600 finds my PC it asks for a code.

Hence everything I type is in asterixes i cannot spell my user/root code.

Does anyone know of a solution to this?[/QUOTE]

I have the same problem when trying to synchronize my contacts with the pc. I dont know what to type and it doesnt give me access. 

Im assuming this happens to you when you are trying to put the pc into the trusted list of the bluetooth devices on your phone? ( because I have the 7610 Nokia and it does that when Im trying to do what I said ) 

Are there any other good bluetooth applications? I cant find much things with synaptic  ](*,)

---

### Post by angol on 2005-05-29
dear globalspace,

seems you have already done the world a great service with that how to - well done!!
problem is, it doesn't work for me :-(

on hcitool scan I get:

Device is not available: Success

lsusb shows:
Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

lsmod shows:
hci_usb                13960  0
bluetooth              46340  7 rfcomm,l2cap,hci_usb

and hciconfig:
 hciconfig
hci0:   Type: USB
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0  SCO MTU: 0:0
        DOWN
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:0 acl:0 sco:0 commands:0 errors:0

nada, niente, nic, zilch aaaargh!

I think I must be missing something EXTREMELY obvious so forgive if this is a stoopid question - I've searched through nearly every google post for hours now about rfcomm.config, hcitool etc. etc. and I can't seem to find out why - I have a Cambridge dongle with a Nokia 6230 which works no probs in windoze but I really want to be linux self-sufficient and not have to load windoze all the time in order to transfer files...

if you can, pleeeeeeeeeeeeeeeeeeeeeeeeeeease heelp!!!

---

### Post by globalspace on 2005-05-29
[QUOTE=angol]dear globalspace,

seems you have already done the world a great service with that how to - well done!!
problem is, it doesn't work for me :-(

on hcitool scan I get:

Device is not available: Success

lsusb shows:
Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

lsmod shows:
hci_usb                13960  0
bluetooth              46340  7 rfcomm,l2cap,hci_usb

and hciconfig:
 hciconfig
hci0:   Type: USB
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0  SCO MTU: 0:0
        DOWN
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:0 acl:0 sco:0 commands:0 errors:0

nada, niente, nic, zilch aaaargh!

I think I must be missing something EXTREMELY obvious so forgive if this is a stoopid question - I've searched through nearly every google post for hours now about rfcomm.config, hcitool etc. etc. and I can't seem to find out why - I have a Cambridge dongle with a Nokia 6230 which works no probs in windoze but I really want to be linux self-sufficient and not have to load windoze all the time in order to transfer files...

if you can, pleeeeeeeeeeeeeeeeeeeeeeeeeeease heelp!!![/QUOTE]


well i think the problem is very simple ... mmmm
so, sorry for my stupid questions :)

1. Have you enabled the Bluetooth on Nokia Phone ?
2. Did you set the visibility of your Nokia Phone (in the bluetooth menu) .. sorry i don't know the english menu .. i think its name is Visibility ... you must set it to All...

---

### Post by angol on 2005-05-29
[QUOTE=globalspace]well i think the problem is very simple ... mmmm
so, sorry for my stupid questions :)

1. Have you enabled the Bluetooth on Nokia Phone ?
2. Did you set the visibility of your Nokia Phone (in the bluetooth menu) .. sorry i don't know the english menu .. i think its name is Visibility ... you must set it to All...[/QUOTE]
 thank you for your patience in answering my long message. yes, bluetooth is enabled in the phone and visible to all (and works when I switch my removable hard disk to windows xp).

Thank you! I have finally found the answer - and yes, it was stupid. the phone was enabled and visible to all - but I had the dongle in my usb hub and not directly in a usb port - it's working now!!! all my best wishes to you...

---

### Post by globalspace on 2005-05-30
[QUOTE=angol]thank you for your patience in answering my long message. yes, bluetooth is enabled in the phone and visible to all (and works when I switch my removable hard disk to windows xp).

Thank you! I have finally found the answer - and yes, it was stupid. the phone was enabled and visible to all - but I had the dongle in my usb hub and not directly in a usb port - it's working now!!! all my best wishes to you...[/QUOTE]


Oh ... i didn't know that your dongle doesn't work with your ubuntu ... i'm sorry but i don't know so much to help you (i've putted my dongle and it worked)... the only thing i know is that there are a lot of how-to which can help you :)

[http://www.holtmann.org/linux/bluetooth/](http://www.holtmann.org/linux/bluetooth/)

hope that help you :)

---

### Post by hamil on 2005-05-30
Hello!

Thanx for this howto, it helps me sending files from my pc to my mobile.
But......
In Warty, I had a nice GUI for sending files to my mobile. I was able to right klick the files in Nautilus, and choose "send via bluetooth". How is this possible in Hoary??

My second trouble with this howto, is that I am not able to send files to my pc.
When inputing "obexserver" in the terminal, I just ge a message in the terminal showing "Waiting for connection". When trying to send from my mobile, I get an error message on my mobile, saying "Did not find any units to conect to" "sending failed"
My mobile is an Nokia 6230, and I use a blutooth-dongle.
Everything worked fine in Warty, whats the difference in Hoary?
This problem is really starting to bug me....  ](*,) 

Hope that someone is able to provide a working solution for me??

Brgds
Lasse

---

### Post by zupermanz on 2005-05-30
Thanks allot !!!!!!!!!!
It really works!
Is there a gui to sent files to nokia or do i have to do it allways from the console

---

### Post by globalspace on 2005-05-30
[QUOTE=zupermanz]Thanks allot !!!!!!!!!!
It really works!
Is there a gui to sent files to nokia or do i have to do it allways from the console[/QUOTE]

you can add the gnome-obex-send application in the list of the Open With ...
Click Right -> Open With -> Another Application

insert   gnome-obex-send 

pay attention that it modify the default application of Open With so adjust it with : right click -> properties -> select the default application

ps. i think you can add a simply script in nautilus but sorry i don't know how create script .. try google ;)

---

### Post by zupermanz on 2005-05-31
Thanks!!!
I hope it works with kubuntu

---

### Post by djp on 2005-05-31
Would this howto be usable with the Sony Ericsson K700i? Also, would implementing the [this advice](http://www.hentges.net/misc/k700i/) after following the howto described here work?

---

### Post by derrick1985 on 2005-05-31
Should. Give it a try and see what happens.

---

### Post by djp on 2005-05-31
[QUOTE=derrick1985]Should. Give it a try and see what happens.[/QUOTE]

Apparantly installing gnome-bluetooth adds a "Send via Bluetooth" entry into the context menu of nautilus.

---

### Post by djp on 2005-06-02
Right. Have followed the howto and have managed to transfer files from my PC to my mobile phone (K700i). However, if i try and send a file the other way (from my phone to my PC), I get a connection failed error. I have added my PC to my phones devices and entered the passcode of 1234 which it seems to accept. I have checked the status of my PC listing on my phone and object push is the only service that appears as supported. Is that correct? Any help in getting the phone to send to my PC would be most appreciated. djp

---

### Post by kb00heda on 2005-06-03
Thanks --- your (globalspace) howto worked nicely on my Acer Ferrari 3000 laptop with a Motorola V525 cell phone!

---

### Post by derrick1985 on 2005-06-23
Hey all, I made a HOWTO for sending files without having to go through the terminal.

[http://ubuntuforums.org/showthread.php?t=43843](http://ubuntuforums.org/showthread.php?t=43843)

---

### Post by sickdude on 2005-06-28
yes!!!

dam that was so easy :D

thnx dude really nice job it works super :D

---

### Post by Outsider on 2005-06-30
[QUOTE=djp]Right. Have followed the howto and have managed to transfer files from my PC to my mobile phone (K700i). However, if i try and send a file the other way (from my phone to my PC), I get a connection failed error. I have added my PC to my phones devices and entered the passcode of 1234 which it seems to accept. I have checked the status of my PC listing on my phone and object push is the only service that appears as supported. Is that correct? Any help in getting the phone to send to my PC would be most appreciated. djp[/QUOTE]
 I have the same problem as djp, it works great. Except I can't send files from the phone to the PC. The phone can't find/pair with the PC at all. Any clues? Its a Samsung D500

---

### Post by davidpronk on 2005-07-01
Thanks for the HOWTO.
I also managed to setup Bluetooth in Hoary and even find my Nokia 6820. But from my phone I can't find my PC. It appears to be invisible. And I would really like to be able to send files from my phone to my PC. And i did start the obexserver when I tried to find my PC.

---

### Post by Simplesso on 2005-07-04
Hi .... sorry for my english :) ..... i'am italian

I've a problem... i downloaded Phone Manager for receive and send Sms by my notebook....but it works only the first time... after.... it can't connect :( 
i try... but i not find the problem...

However the phone can send and receive file...

Help me !

Thanks !!!

---

### Post by lotech on 2005-07-11
I am an Ubuntu newbie and I used Knoppix for internet, there is build in support for bluetooth dongle, I simply search for my phone and then create a connection to it, then I can connect to the internet like using dial up, is there a simple way in Ubuntu to setup bluetooth purely for connect to the internet if I don't need the file transfer.

Thanks !

---

### Post by tealc_sg1 on 2005-07-11
Works perfectly with my NOKIA 6670, Thanks !

---

### Post by nwillis on 2005-07-11
Alirght, I need help, this doesn't work for me.  I have a Nokia 6620, it's visible to the PC and vice versa.  I try to send a file from the phone's "Gallery" application and select the PC from the list of devices, then it says "Connecting" for about a minute then reports Unable To Connect.

MEANWHILE on the PC side, gnome-obex-server is live; when I start the send on the phone side, a "conn_request: bdaddr 00:02:etcetera" message pops into the terminal window, followed by "conn_complete: status 0x00" ... but nothing happens.

What does this mean?

This worked out-of-the-box on Fedora with identical hardware; what's different?

---

### Post by denkedran on 2005-07-16
For all those who have problems connecting from phone to pc.
I found this at google [http://www.ubuntu-de.org/wiki/mobil:bluetooth_einrichten](http://www.ubuntu-de.org/wiki/mobil:bluetooth_einrichten).
Because it is german I'll explain the essential parts.
If your Phone doesn't find the pc's bluetooth device try this:
```
sudo gedit /etc/bluetooth/hcid.conf
```
search for
```
# Local device class
class 0x100;
```
change to
```
# Local device class
class 0x100100;
```
after that you have to restart the bluetooth service and pray
```
sudo /etc/init.d/bluez-utils restart
```
i hope this while help a bit

I have still one question:
Is it somehow possible to send a m3u playlist to my Nokia 6230. In other words is it possible to specify a pathname at for other end.

---

### Post by nwillis on 2005-07-16
Hmm.  I'll have to try it.  

As for sending any particular file, there is a Symbian Series60 application called "Forward" that I use -- with it you can open any message and save the file to anywhere in the filesystem.  That sounds like it will do what you want.

Assuming you're running S60, anyway.  I found it here: [http://www.compsoc.man.ac.uk/~ashley/](http://www.compsoc.man.ac.uk/~ashley/) 

Nate

---

### Post by miatapaul on 2005-07-16
Has anyone been able to access the GPS info in order to use the phone as a GPS receiver? I don't have a buetooth phone now, but will be upgrading soon. Or is this something better suited to a usb connection?

---

### Post by denkedran on 2005-07-17
[QUOTE=nwillis]
Assuming you're running S60, anyway.  I found it here: [http://www.compsoc.man.ac.uk/~ashley/](http://www.compsoc.man.ac.uk/~ashley/) 

Nate[/QUOTE]

My Nokia 6230 runs with Symbian Series 40. So I cant use that piece of software. But I made a nautilus-script solution with gammu (gammu --nokiaaddfile Playlist <file>) and fapg (Fast Audio Playlist Generator). Now I can fill my 1 GB mmc, with music in subfolders.

---

### Post by Heliode on 2005-07-19
Hey, thanks for the howto! Sending stuff to mobile phones and PDA's works great, but if I try to send stuff from those devices to my laptop, the phones ask for a password. Where do I set this? It won't connect without it.

---

### Post by souraka on 2005-07-22
hello all
this how to is fantastic helps a lot.
but i have 1 problem i can't resolved
1/ i can not send big files like mp3 it started to send it but stop and nothing happend so it is unable to send all the file !! why?? 
 

what shoul i do to resolve this


thanks for your help

---

### Post by Perfect Storm on 2005-08-01
I got a Samsung E720.

Anyone have any success getting Samsung phones working on ubuntu/bluetooth?

---

### Post by _.-m. on 2005-08-05
[QUOTE=kb00heda]Thanks --- your (globalspace) howto worked nicely on my Acer Ferrari 3000 laptop with a Motorola V525 cell phone![/QUOTE]
 I have an Ferrari 3000 too but i cann't get it work.
The Button for activating Bluetooth does not blink if i press it.

hcitool scan sais:
[HTML]Device is not available: Success[/HTML]


hcitool dev:
[HTML]Devices:[/HTML]


Anybody know how to start the broadcom bt-dev in the commandline?

```
sudo /etc/init.d/bluez-utils restart
```   shoud do this

After starting gnome-bluetooth-manager from terminal there is:

```
(Bluetooth Device Manager:10055): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
/usr/lib/python2.4/site-packages/gnomebt/manager.py:153: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.iconlist.set_sorted (gtk.TRUE)

```


lsmod shows:

```
Module                  Size  Used by
binfmt_misc            11272  1
nfs                   183396  1
lockd                  58152  1 nfs
sunrpc                137188  4 nfs,lockd
rfcomm                 36252  2
l2cap                  24324  5 rfcomm
bluetooth              46340  12 rfcomm,l2cap
powernow_k7             8744  0
proc_intf               4100  0
freq_table              4100  1 powernow_k7
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
ipt_limit               2688  8
iptable_mangle          2944  0
ipt_LOG                 6656  8
ipt_MASQUERADE          3584  0
iptable_nat            24648  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              6528  1
ip_conntrack_irc       71856  0
ip_conntrack_ftp       72624  0
ipt_state               2048  6
ip_conntrack           43668  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3840  1
ip_tables              17408  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
fglrx                 229568  7
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  11
sd_mod                 16784  0
af_packet              20744  2
via_rhine              19972  0
mii                     4736  1 via_rhine
usb_storage            64064  0
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
usbhid                 29376  0
ehci_hcd               29444  0
uhci_hcd               30224  0
ohci1394               31876  0
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
via_agp                 9216  1
agpgart                31784  2 via_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
ndiswrapper           109044  0
usbcore               107384  6 usb_storage,usbhid,ehci_hcd,uhci_hcd,ndiswrappersr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  4 sd_mod,usb_storage,sr_mod,sbp2
joydev                  9408  0
ieee1394              100408  2 ohci1394,sbp2
evdev                   9088  1
tsdev                   7488  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  2
jbd                    54168  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  4
ide_core              118988  5 usb_storage,ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  1079
thermal                13576  0
processor              22708  2 powernow_k7,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
```

rfcomm and l2cap are present.
I dont know what to try next...
The Bluetoothdevice is a CSR, as far as i got this right. Installation of openbt fails out of several reasons (which i also dont know)
```
 make
make -C linux/drivers/char/bluetooth
make[1]: Entering directory `/home/tiax/Desktop/openbt/linux/drivers/char/bluetooth'
gcc -D__KERNEL__ -DMODULE -I../../../include -I/usr/src/linux/include -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -fno-strength-reduce  -MD   -c -o bluetooth.o bluetooth.c
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/mm.h:4,
                 from /usr/include/linux/poll.h:10,
                 from ../../../include/linux/bluetooth/sysdep-2.1.h:68,
                 from bluetooth.c:44:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/mm.h:4,
                 from /usr/include/linux/poll.h:10,
                 from ../../../include/linux/bluetooth/sysdep-2.1.h:68,
                 from bluetooth.c:44:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/mm.h:4,
                 from /usr/include/linux/poll.h:10,
                 from ../../../include/linux/bluetooth/sysdep-2.1.h:68,
                 from bluetooth.c:44:
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/mm.h:4,
                 from /usr/include/linux/poll.h:10,
                 from ../../../include/linux/bluetooth/sysdep-2.1.h:68,
                 from bluetooth.c:44:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
bluetooth.c:49:26: linux/malloc.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from bluetooth.c:77:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from bluetooth.c:77:
/usr/include/linux/irq.h:70: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/include/linux/irq.h:72,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from bluetooth.c:77:
/usr/include/asm/hw_irq.h:28: error: `NR_IRQS' undeclared here (not in a function)
/usr/include/asm/hw_irq.h:31: error: `NR_IRQS' undeclared here (not in a function)
bluetooth.c: In function `bt_open':
bluetooth.c:422: error: structure has no member named `device'
bluetooth.c:422: error: request for member `minor_start' in something not a structure or union
bluetooth.c:425: error: called object is not a function
bluetooth.c:425: error: syntax error before string constant
bluetooth.c:432: warning: `MOD_INC_USE_COUNT' is deprecated (declared at /usr/include/linux/module.h:482)
bluetooth.c:422: warning: unused variable `line'
bluetooth.c: In function `bt_close':
bluetooth.c:441: error: structure has no member named `device'
bluetooth.c:441: error: request for member `minor_start' in something not a structure or union
bluetooth.c:443: error: called object is not a function
bluetooth.c:443: error: syntax error before string constant
bluetooth.c:451: warning: `MOD_DEC_USE_COUNT' is deprecated (declared at /usr/include/linux/module.h:494)
bluetooth.c: In function `bt_put_char':
bluetooth.c:457: error: called object is not a function
bluetooth.c:457: error: syntax error before string constant
bluetooth.c: In function `bt_flush_chars':
bluetooth.c:464: error: called object is not a function
bluetooth.c:464: error: syntax error before string constant
bluetooth.c:465: error: request for member `flush_chars' in something not a structure or union
bluetooth.c:466: error: request for member `flush_chars' in something not a structure or union
bluetooth.c: In function `bt_write_room':
bluetooth.c:475: error: called object is not a function
bluetooth.c:475: error: syntax error before string constant
bluetooth.c: In function `bt_chars_in_buffer':
bluetooth.c:482: error: structure has no member named `device'
bluetooth.c:482: error: request for member `minor_start' in something not a structure or union
bluetooth.c:484: error: called object is not a function
bluetooth.c:484: error: syntax error before string constant
bluetooth.c: In function `bt_flush_buffer':
bluetooth.c:493: error: called object is not a function
bluetooth.c:493: error: syntax error before string constant
bluetooth.c: In function `__bt_ioctl':
bluetooth.c:543: error: called object is not a function
bluetooth.c:543: error: syntax error before string constant
bluetooth.c:548: error: called object is not a function
bluetooth.c:548: error: syntax error before string constant
bluetooth.c:554: error: called object is not a function
bluetooth.c:554: error: syntax error before string constant
bluetooth.c:583: error: called object is not a function
bluetooth.c:583: error: syntax error before string constant
bluetooth.c:590: error: called object is not a function
bluetooth.c:590: error: syntax error before string constant
bluetooth.c:640: error: called object is not a function
bluetooth.c:640: error: syntax error before string constant
bluetooth.c:667: error: called object is not a function
bluetooth.c:667: error: syntax error before string constant
bluetooth.c:707: error: called object is not a function
bluetooth.c:707: error: syntax error before string constant
bluetooth.c:737: error: called object is not a function
bluetooth.c:737: error: syntax error before string constant
bluetooth.c:751: error: called object is not a function
bluetooth.c:751: error: syntax error before string constant
bluetooth.c:763: error: called object is not a function
bluetooth.c:763: error: syntax error before string constant
bluetooth.c:777: error: called object is not a function
bluetooth.c:777: error: syntax error before string constant
bluetooth.c:788: error: called object is not a function
bluetooth.c:788: error: syntax error before string constant
bluetooth.c:798: error: called object is not a function
bluetooth.c:798: error: syntax error before string constant
bluetooth.c:828: error: called object is not a function
bluetooth.c:828: error: syntax error before string constant
bluetooth.c:839: error: called object is not a function
bluetooth.c:839: error: syntax error before string constant
bluetooth.c:852: error: called object is not a function
bluetooth.c:852: error: syntax error before string constant
bluetooth.c:865: error: called object is not a function
bluetooth.c:865: error: syntax error before string constant
bluetooth.c:879: error: called object is not a function
bluetooth.c:879: error: syntax error before string constant
bluetooth.c:912: error: called object is not a function
bluetooth.c:912: error: syntax error before string constant
bluetooth.c:922: error: called object is not a function
bluetooth.c:922: error: syntax error before string constant
bluetooth.c:932: error: called object is not a function
bluetooth.c:932: error: syntax error before string constant
bluetooth.c:945: error: called object is not a function
bluetooth.c:945: error: syntax error before string constant
bluetooth.c:955: error: called object is not a function
bluetooth.c:955: error: syntax error before string constant
bluetooth.c:969: error: called object is not a function
bluetooth.c:969: error: syntax error before string constant
bluetooth.c:983: error: called object is not a function
bluetooth.c:983: error: syntax error before string constant
bluetooth.c:996: error: called object is not a function
bluetooth.c:996: error: syntax error before string constant
bluetooth.c:1018: error: called object is not a function
bluetooth.c:1018: error: syntax error before string constant
bluetooth.c:1025: error: called object is not a function
bluetooth.c:1025: error: syntax error before string constant
bluetooth.c: In function `bt_throttle':
bluetooth.c:1202: error: called object is not a function
bluetooth.c:1202: error: syntax error before string constant
bluetooth.c: In function `bt_unthrottle':
bluetooth.c:1208: error: called object is not a function
bluetooth.c:1208: error: syntax error before string constant
bluetooth.c: In function `bt_set_termios':
bluetooth.c:1215: error: called object is not a function
bluetooth.c:1215: error: syntax error before string constant
bluetooth.c:1219: error: request for member `set_termios' in something not a structure or union
bluetooth.c:1221: error: called object is not a function
bluetooth.c:1221: error: syntax error before string constant
bluetooth.c: In function `bt_start':
bluetooth.c:1226: error: called object is not a function
bluetooth.c:1226: error: syntax error before string constant
bluetooth.c: In function `bt_stop':
bluetooth.c:1232: error: called object is not a function
bluetooth.c:1232: error: syntax error before string constant
bluetooth.c: In function `bt_hangup':
bluetooth.c:1238: error: called object is not a function
bluetooth.c:1238: error: syntax error before string constant
bluetooth.c: In function `bt_tty_read':
bluetooth.c:1265: error: called object is not a function
bluetooth.c:1265: error: syntax error before string constant
bluetooth.c: In function `bt_tty_write':
bluetooth.c:1287: error: called object is not a function
bluetooth.c:1287: error: syntax error before string constant
bluetooth.c:1289: error: request for member `write' in something not a structure or union
bluetooth.c: In function `bt_tty_ioctl':
bluetooth.c:1302: error: called object is not a function
bluetooth.c:1302: error: syntax error before string constant
bluetooth.c: In function `bt_tty_poll':
bluetooth.c:1327: error: called object is not a function
bluetooth.c:1327: error: syntax error before string constant
bluetooth.c: In function `bt_tty_open':
bluetooth.c:1335: error: called object is not a function
bluetooth.c:1335: error: syntax error before string constant
bluetooth.c: In function `bt_tty_room':
bluetooth.c:1375: error: called object is not a function
bluetooth.c:1375: error: syntax error before string constant
bluetooth.c: In function `bt_tty_wakeup':
bluetooth.c:1387: error: syntax error before string constant
bluetooth.c: In function `bt_reset_phys_hw':
bluetooth.c:1423: error: called object is not a function
bluetooth.c:1423: error: syntax error before string constant
bluetooth.c: In function `bt_write_lower_driver':
bluetooth.c:1450: error: called object is not a function
bluetooth.c:1450: error: syntax error before string constant
bluetooth.c:1463: error: request for member `write_room' in something not a structure or union
bluetooth.c:1464: error: syntax error before string constant
bluetooth.c:1470: error: request for member `write' in something not a structure or union
bluetooth.c:1474: error: syntax error before string constant
bluetooth.c:1482: error: called object is not a function
bluetooth.c:1482: error: syntax error before string constant
bluetooth.c: In function `bt_write_top':
bluetooth.c:1518: error: structure has no member named `device'
bluetooth.c:1518: error: request for member `minor_start' in something not a structure or union
bluetooth.c:1529: error: called object is not a function
bluetooth.c:1529: error: syntax error before string constant
bluetooth.c:1535: error: called object is not a function
bluetooth.c:1535: error: syntax error before string constant
bluetooth.c: In function `bt_wait_tx':
bluetooth.c:1685: error: request for member `chars_in_buffer' in something not a structure or union
bluetooth.c: In function `bt_connect':
bluetooth.c:1854: error: called object is not a function
bluetooth.c:1854: error: syntax error before string constant
bluetooth.c:1870: error: called object is not a function
bluetooth.c:1870: error: syntax error before string constant
bluetooth.c:1875: error: called object is not a function
bluetooth.c:1875: error: syntax error before string constant
bluetooth.c:1896: error: called object is not a function
bluetooth.c:1896: error: syntax error before string constant
bluetooth.c:1930: error: called object is not a function
bluetooth.c:1930: error: syntax error before string constant
bluetooth.c:1939: error: called object is not a function
bluetooth.c:1939: error: syntax error before string constant
bluetooth.c:1956: error: called object is not a function
bluetooth.c:1956: error: syntax error before string constant
bluetooth.c:1959: error: called object is not a function
bluetooth.c:1959: error: syntax error before string constant
bluetooth.c:1969: error: called object is not a function
bluetooth.c:1969: error: syntax error before string constant
bluetooth.c: In function `bt_execute_sdp_request':
bluetooth.c:1985: error: called object is not a function
bluetooth.c:1985: error: syntax error before string constant
bluetooth.c:1989: error: called object is not a function
bluetooth.c:1989: error: syntax error before string constant
bluetooth.c:2000: error: syntax error before string constant
bluetooth.c:2008: error: called object is not a function
bluetooth.c:2008: error: syntax error before string constant
bluetooth.c: In function `bt_connect_ind':
bluetooth.c:2026: error: called object is not a function
bluetooth.c:2026: error: syntax error before string constant
bluetooth.c:2026: warning: left-hand operand of comma expression has no effect
bluetooth.c:2026: error: syntax error before ')' token
bluetooth.c: In function `bt_connect_cfm':
bluetooth.c:2040: error: called object is not a function
bluetooth.c:2040: error: syntax error before string constant
bluetooth.c:2049: error: called object is not a function
bluetooth.c:2049: error: syntax error before string constant
bluetooth.c:2060: error: called object is not a function
bluetooth.c:2060: error: syntax error before string constant
bluetooth.c:2061: error: called object is not a function
bluetooth.c:2061: error: syntax error before string constant
bluetooth.c:2068: error: called object is not a function
bluetooth.c:2068: error: syntax error before string constant
bluetooth.c:2072: error: called object is not a function
bluetooth.c:2072: error: syntax error before string constant
bluetooth.c: In function `bt_send_sdp_data_received':
bluetooth.c:2082: error: called object is not a function
bluetooth.c:2082: error: syntax error before string constant
bluetooth.c:2089: error: called object is not a function
bluetooth.c:2089: error: syntax error before string constant
bluetooth.c:2093: error: called object is not a function
bluetooth.c:2093: error: syntax error before string constant
bluetooth.c: In function `bt_disconnect':
bluetooth.c:2113: error: called object is not a function
bluetooth.c:2113: error: syntax error before string constant
bluetooth.c:2121: error: called object is not a function
bluetooth.c:2121: error: syntax error before string constant
bluetooth.c:2129: error: called object is not a function
bluetooth.c:2129: error: syntax error before string constant
bluetooth.c:2157: error: called object is not a function
bluetooth.c:2157: error: syntax error before string constant
bluetooth.c: In function `bt_disconnect_ind':
bluetooth.c:2169: error: called object is not a function
bluetooth.c:2169: error: syntax error before string constant
bluetooth.c:2169: warning: left-hand operand of comma expression has no effect
bluetooth.c:2169: error: syntax error before ')' token
bluetooth.c: In function `bt_disconnect_cfm':
bluetooth.c:2180: error: called object is not a function
bluetooth.c:2180: error: syntax error before string constant
bluetooth.c: In function `bt_hangupline':
bluetooth.c:2195: error: called object is not a function
bluetooth.c:2195: error: syntax error before string constant
bluetooth.c:2203: error: called object is not a function
bluetooth.c:2203: error: syntax error before string constant
bluetooth.c: In function `bt_init':
bluetooth.c:2293: warning: assignment makes integer from pointer without a cast
bluetooth.c:2294: error: structure has no member named `table'
bluetooth.c: In function `bt_init_stack':
bluetooth.c:2537: warning: implicit declaration of function `get_free_page'
bluetooth.c:2606: warning: label `init_failed_exit0' defined but not used
bluetooth.c: In function `bt_register_rfcomm':
bluetooth.c:2762: error: called object is not a function
bluetooth.c:2762: error: syntax error before string constant
bluetooth.c:2776: error: called object is not a function
bluetooth.c:2776: error: syntax error before string constant
bluetooth.c:2776: warning: left-hand operand of comma expression has no effect
bluetooth.c:2776: warning: left-hand operand of comma expression has no effect
bluetooth.c:2776: error: syntax error before ')' token
bluetooth.c: In function `bt_register_sdp':
bluetooth.c:2787: error: called object is not a function
bluetooth.c:2787: error: syntax error before string constant
bluetooth.c:2794: error: called object is not a function
bluetooth.c:2794: error: syntax error before string constant
bluetooth.c:2799: error: called object is not a function
bluetooth.c:2799: error: syntax error before string constant
bluetooth.c:2806: error: called object is not a function
bluetooth.c:2806: error: syntax error before string constant
bluetooth.c: In function `bt_unregister_rfcomm':
bluetooth.c:2814: error: called object is not a function
bluetooth.c:2814: error: syntax error before string constant
bluetooth.c:2829: error: called object is not a function
bluetooth.c:2829: error: syntax error before string constant
bluetooth.c: In function `bt_unregister_sdp':
bluetooth.c:2842: error: called object is not a function
bluetooth.c:2842: error: syntax error before string constant
bluetooth.c:2845: error: called object is not a function
bluetooth.c:2845: error: syntax error before string constant
bluetooth.c:2853: error: called object is not a function
bluetooth.c:2853: error: syntax error before string constant
bluetooth.c: In function `bt_register_tty':
bluetooth.c:2871: error: structure has no member named `device'
bluetooth.c:2871: error: request for member `minor_start' in something not a structure or union
bluetooth.c:2886: error: called object is not a function
bluetooth.c:2886: error: syntax error before string constant
bluetooth.c:2910: error: called object is not a function
bluetooth.c:2910: error: syntax error before string constant
bluetooth.c: In function `bt_unregister_tty':
bluetooth.c:2925: error: called object is not a function
bluetooth.c:2925: error: syntax error before string constant
bluetooth.c:2944: error: called object is not a function
bluetooth.c:2944: error: syntax error before string constant
bluetooth.c: At top level:
bluetooth.c:3007: error: syntax error before "kdev_t"
bluetooth.c:3008: warning: function declaration isn't a prototype
bluetooth.c: In function `wq_timeout':
bluetooth.c:3075: error: called object is not a function
bluetooth.c:3075: error: syntax error before string constant
bluetooth.c: In function `bt_exit':
bluetooth.c:3091: warning: implicit declaration of function `save_flags'
bluetooth.c:3092: warning: implicit declaration of function `cli'
bluetooth.c:3096: warning: implicit declaration of function `restore_flags'
bluetooth.c: At top level:
bluetooth.c:3026: warning: `psmname' defined but not used
make[1]: *** [bluetooth.o] Error 1
make[1]: Leaving directory `/home/tiax/Desktop/openbt/linux/drivers/char/bluetooth'
make: *** [all] Error 2
root@mephistopheles:/home/tiax/Desktop/openbt # make install
install apps/bluetooth/btd/btd /usr/local/bin
install: cannot stat `apps/bluetooth/btd/btd': No such file or directory
make: *** [install] Error 1

```
I really need to work with ubuntu - an such things driving me frustrated, because i will never want to switch to xp exept for playing games. Fact ist that windows is destroying my hardware. Therefor i am angry about that software pushing my RAM's to glow and never stop itching on the harddrive.
I would be glad and satisfied if everything works for me in ubuntu - and not that i have to work for it and it still doesn't work. I am not that educated on this things, but i am ready to learn from you. google brought no success for my specific problem.
peaceful greetings from austria!

---

### Post by rstana on 2005-08-09
i got stuck on step where you issue:

hcitool scan

it starts looking for phone (Nokia 6230) but finds nothing and times-out after a while, making me helpless

what do I need to do? thanks for help here

---

### Post by kombipom on 2005-08-11
Thanks for the How-To, I've now got my P800 and Ubuntu talking to each other, the only change I had to make was to use channel 1 rather than 10.  I am however having the same problem that souraka reported with large files (mp3's).  The phone tells me that the connection was severed by the other device. Is there a max transfer time in a config file somewhere which can be adjusted?

---

### Post by dinap1 on 2005-08-22
Hi!
I did everything th 1st post says. at the point where i wrote

"sudo mknod /dev/rfcomm0 c 216 0"

it gave me this error message:

"mknod: `/dev/rfcomm0': File already exists"

But i continued. when i tried to send a jpg picture from my 6260 phone, on the phone screen appeared

"sending falied"

although before it found my computer's name when it was searching fot BT devices.
Any ideas please?

Nokia 6260, usb BT dongle: Omnuis, Ubuntu 5.0.4.
Thanx!

---

### Post by ramesh_thiru on 2005-09-02
Thanks, at last now I can connect to my Nokia 6600, but still I'm not able to use GPRS... I searced everywhere how I could, and I didn't find luck  :| any help?

---

### Post by stuoolong on 2005-10-02
Hi, I'm a complete newbie! Looking forward to spending quite a bit of time here...

This howto worked great for me, as did the one by Derrick1985 on setting up Gnome scripts. The only problem is that it won't transfer files with a space in the name...there's probably a really simple solution but I can't work it out. Nearly all of my music files have a space in the name somewhere, so short of changing all the names I can't really transfer them to the phone. :???: No problem getting pics from the phone to the PC though! I'm using a Motorola V3, used channel 10.:D

---

### Post by bladesonfire on 2005-10-06
I have a Dell Inspiron 8600 with an integrated bluetooth device and a Sony Ericsson K750i. The device is detected correctly, but when I run "hcitool scan", it doesn't work for me.

```
$ hcitool scan
Scanning ...
$
```

My "hciconfig" output:

```
hci0:   Type: USB
        BD Address: 00:10:C6:50:CC:8F ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING
        RX bytes:225 acl:0 sco:0 events:28 errors:0
        TX bytes:318 acl:0 sco:0 commands:15 errors:0
```

I have another machine running Windows XP with a bluetooth dongle installed that has connected to the phone as we speak and transfered files to my phone.  When I scan with the phone, it finds the WinXP machine, but not the laptop.

I'd prefer not to attach the bluetooth dongle to my laptop, since that was the whole point of getting integrated bluetooth in the first place.

Any suggestions, please? Thanks.

---

### Post by ranf on 2005-10-07
[QUOTE=Heliode]Hey, thanks for the howto! Sending stuff to mobile phones and PDA's works great, but if I try to send stuff from those devices to my laptop, the phones ask for a password. Where do I set this? It won't connect without it.[/QUOTE]
It asks for the bluetooth PIN.
For the PC side it is usually stored in:
 /etc/bluetooth/pin

---

### Post by k1G on 2005-10-08
Here's my experience with a Sony Ericsson K700i and a Belkin Bluetooth dongle...

First things first - I'm new to Ubuntu having run mainly on SuSE since 2001 with odd flirtations with various Red Hats, so it took a while for me to figure out that I had to un-comment some lines in /etc/apt/sources.list so that I could apt-get install some of the packages I needed...:)

Secondly, I had already tested the hardware on another box running SuSE 9.0, so that I knew it worked OK - this was also handy because I knew the things that I had had to tweak in order to get things working OK under SuSE.

Anyway, this is how I got things working with Ubuntu. I basically followed the contents of this HOWTO but also did the following...

* As was suggested in this thread I edited /etc/bluetooth/rfcomm.conf adding the line "bind yes;" - this seemed to cure the phone hanging after sending a file - it would report back "Bluetooth is currently busy" or similar, and Bluetooth could not be stopped, the phone had to be shut off first.
* As per an earlier post I edited /etc/bluetooth/hcid.conf # Local device class to show class 0x100100;
* I also edited /etc/bluetooth/hcid.conf to un-comment the line auth enable; under # Authentication and Encryption. I did this as a precaution because this was one of the tweaks that this hardware combination needed under SuSE

Thanks to everyone for posting ideas and suggestions - this was driving me crazy knowing that the damn thing worked under SuSE but not Ubuntu... :D

---

### Post by emperon on 2005-10-10
Hello, I think the article is excellent. However what i want is connecting to internet through GPRS with my Bluetooth connected phone Nokia 6230.

So far, i can pair the phone and my computer. So Bluetooth is working.
But i am stuck at the next step. Theres a program called Easy GPRS connector for linux but it is somehow not working for me.

I am looking for a solution, please help.

Note: Windows is capable of doing that with this machine and my phone without any extras. So i know my hardware is ok for GPRS.

---

### Post by ranf on 2005-10-10
[QUOTE=emperon]Hello, I think the article is excellent. However what i want is connecting to internet through GPRS with my Bluetooth connected phone Nokia 6230.[/QUOTE]

Have a look at this site: 
[http://tuxmobil.org/phones_survey_nokia.html]("http://tuxmobil.org/phones_survey_nokia.html")

---

### Post by mokeyjoe on 2005-10-17
I'm trying to connect a 6680 to Ubuntu Hoary but by using the USB lead, not Bluetooth. Would the procedure be similar to this? All I really want to do is transfer files between the phone and PC.

---

### Post by Tom^ on 2005-10-19
So is there any way to sync my evolution with 6630? Even if I have to compile stuff, is there a way? All I have are dead ends and I'm disappointed. :( Thank you for your answers!

---

### Post by rwabel on 2005-10-21
everything is working fine. I can find my phone and my phone finds my ubuntu box and I can pair it. But whenever I want to send a file from my phone to my ubuntu box I get "connection failed". I've started the gnome-obex-server!

---

### Post by NicP on 2005-10-24
[QUOTE=ranf]It asks for the bluetooth PIN.
For the PC side it is usually stored in:
 /etc/bluetooth/pin[/QUOTE]

my pin file is set as 1234, however when i put this in it still says passcode failed, i also tried changing it to 1, and 1111, with the same result. any ideas?

---

### Post by ranf on 2005-10-24
[QUOTE=NicP]my pin file is set as 1234, however when i put this in it still says passcode failed, i also tried changing it to 1, and 1111, with the same result. any ideas?[/QUOTE]
What program do you run on the PC side?

---

### Post by NicP on 2005-10-24
[QUOTE=ranf]What program do you run on the PC side?[/QUOTE]

I installed gnome-bluetooth and gnome-phone-manager from synaptic (and dependancies). The phone came up in the bluetooth manager straight away. I also tried following the procedure at the beginning of this thread and got exactly the same result, it just rejects the passcode.

---

### Post by rwabel on 2005-10-25
[quote=djp]Right. Have followed the howto and have managed to transfer files from my PC to my mobile phone (K700i). However, if i try and send a file the other way (from my phone to my PC), I get a connection failed error. I have added my PC to my phones devices and entered the passcode of 1234 which it seems to accept. I have checked the status of my PC listing on my phone and object push is the only service that appears as supported. Is that correct? Any help in getting the phone to send to my PC would be most appreciated. djp[/quote]

same problem here. I can bind my computer with my phone. I can send from computer to phone. but I cannot send from phone to computer!

---

### Post by Eldan on 2005-11-08
Excelent Howto, thank you so much for taking the time to put the word out.

Everything worked 100% as you documented, except for one step.  For some reason  I was not able to send from my Nokia 6600 to my Linux box until after I rebooted.  Although I am sure I probably could have restarted the obex server for the same results.  I had used obexserver and gnome-obex-server commands, possibly some conflict arose there.

Ubuntu rocks!  This has been the simplest, best documented Linux varient I have tried yet.  Everything just works!  =D>

---

### Post by freyro on 2005-11-11
Excellant post this is. Worked like a charm for me on my Dell D505 - difference is I have an on motherboard bluetooth device and hence my connection string was a bit longer is:

/sys/devices/pci0000\:00/0000\:00\:1d.0/usb1/1-2/1-2\:1.0/

but not:

/dev/rfcomm0

(unless I've overlooked something big time) The above /sys/dev... being the usb.linux.sysfs_path param (available from Device Manager).

Thanks - 

Freyr O

---

### Post by d34th on 2005-11-18
Hi

I have a little problem
I'm not able to transfer big files to my phone (nokia 6230), I think it's because it stores the file in the phone memory, but when a file is bigger than the phone memory, the transfer fails.
I would like to send files directly to the mmc card.
Is there any way to transfer sets of files at the same time?

Finally, would it be possible to mount (or something like this) the phone in order to grafically explore it? 


Greetings from Spain

----------EDIT------------

I've read something about btfs, what about it?

---

### Post by tomwell on 2005-11-22
Hey,

Does anyone feel that bluetooth integration in Breezy is appalling and that it should be made into easy GUI program for the next release??

I mean i am not even going to bother using bluetooth support in linux if i have to restart everytime i send a file...!!!

Easier to reboot into windows and use the nokia software... and transfer into FAT32...

Just a thought...

Peace

Tom

---

### Post by tomwell on 2005-11-22
Oh and before anyone has a go at me...

I have set bluetooth up and it works fine i dont have any problems with at all expet the ease of use...!!!

Peace

Tom

---

### Post by zasf on 2005-12-31
[QUOTE=freyro]Excellant post this is. Worked like a charm for me on my Dell D505 - difference is I have an on motherboard bluetooth device and hence my connection string was a bit longer is:

/sys/devices/pci0000\:00/0000\:00\:1d.0/usb1/1-2/1-2\:1.0/

but not:

/dev/rfcomm0

(unless I've overlooked something big time) The above /sys/dev... being the usb.linux.sysfs_path param (available from Device Manager).

Thanks - 

Freyr O[/QUOTE]

I also have an internal bluetooth device, I had no problems following this how-to to use an external USB bluetooth dongle.. but the internal one doesn't work.. I don't even find it with 

```
matteo@ubuntu:~$ sudo hcitool dev
Devices:
```

How do I use device manager to discover my internal bluetooth device address??
Thanks

---

### Post by brunog on 2005-12-31
Thank you for the effort put into this post.
It helped me set up my Nokia 8620 to send and receive files from my PC running Ubuntu Breezy (5.10).
I would like to report that I have also maneged to get connected to the internet via my bluetooth connection to my phone and GPRS.

Setting up my phone accoring to this post enabled my to send and receive files to and from my phone.
I could not access the internet though.
Each time I wanted to connect my phone requested a password for pairing.
1st problem:  My phone wanted to pair with "Brunog Home" my home PC name. This was the name already on my phone due to being pared in Windows.
After deleting this paring from my phone, my phone found my PC as "ubuntu-0"
When I had a password problem - phone requesting password for pairing - the one that worked for me was "1234".
There has been advice about resetting passwords, I tried this first - no need to reset password

Pairing done.

I also followed advice in this post regarding change of # Local device class to class 0x100100 through sudo gedit /etc/bluetooth/hcid.conf.
I believe this assisted my phone in seeing my PC.

All this and I still could not connect to internet.

My greatest source of info was this post and one done by GrootBrak : [http://ubuntuforums.org/showthread.php?t=50496](http://ubuntuforums.org/showthread.php?t=50496)

He used port 1 for his phone,  whereas this post suggests port 10.
After trying 100 things I decided to also use port 1 rather than 10.  For whatever reason this seemed to work.
So it seems that port 10 is not the only one to be used with Nokia phones??

Hopes this feedback helps someone out there. :) 

Now if I can only get my winmodem to work (been trying for 3 months....) I will be in heaven....:p 

I whish you all a wonderful new year in 2006

---

### Post by lateo on 2006-03-01
[QUOTE=andreasDK]When my 6600 finds my PC it asks for a code.
Hence everything I type is in asterixes i cannot spell my user/root code.
Does anyone know of a solution to this?[/QUOTE]

not your NIP?

[edit(s)]
oh i see. same problem here since i made the mistake to reboot and try nokia pc suite.
now under ubuntu i still can send & receive files, but each time i try to 'connect' to pc from phone there's this boring passwd that doesn't match the /etc/bluetooth/pin :-/
i did not have this problem before installing & trying nokia pc suite under win32. maybe a phone config change?
also tried 'gnome-phone-manager'. looks good but i have the same pb : 'connection' between pc & phone is ok, but i'm asked for the passwd to 'link' them.


i'd really like someone to help made the phone use home internet connection 'via' bluetooth
found something for pda [here (in french but cmd line is universal ;))]("http://www.melaneum.com/linux/bluetooth.html") but 6230i does not seem to offer enough flexibility to be configured this way. 
any tip welcomed!

this one looks good for bluetooth internet access, but it's for laptop : [http://fedoranews.org/.../bluetooth]("http://fedoranews.org/contributors/muhammad_al_ismail/bluetooth/")

found something at operamini forums but don't really understand what to do/how to do :
[I]U mean like using OM as a browser on the phone which is connected via bluetooth to PC which has internet access? It's very easy - U don't have to change anything on the phone.
1. Get the SE J2ME SDK
2. Set up the serial connection with the phone using bth
3. Use ConnectionProxy from seJ2MEsdk - make connection with the phone
4. Use DeviceExplorer from the sdk - fire it up
5. In DeviceExplorer, choose File -> Serial Networking (turn on)
6. On the left U have the list of apps installed on the phone - choose Opera Mini, right click and Start
7. Enjoy using Opera Mini arround the house ;>[/I]

sent a mail to nokia for internet bluetooth purpose. i'm not expecting any answer but at least they know some users request this. asked them if there were any 'phone profile' to be applied on the phone to have more functions available.

---

### Post by lateo on 2006-03-06
nokia france answer : 
"En réponse à votre courriel, je vous informe que le 6230i ne peut bénéficier de connexion en IP Passthrough, permettant d'utiliser le mobile comme navigateur Web en connexion à un PC. De plus, nous ne développons aucun pilote / logiciel sous Linux, mais uniquement sous WIndows."

my fast (and quite bad) translation :
6230i cannot use IP Passthrough connection in order to surf the web from your phone using PC's internet connection. Anyway, we're only looking for windows, we do not work on linux drivers & utilities.

doh. had to try :-/

---

### Post by warpforge on 2006-04-08
I've posted an updated guide to this:
[https://wiki.ubuntu.com/BluetoothDialup](https://wiki.ubuntu.com/BluetoothDialup)

---

### Post by pnk on 2006-05-10
Someone asked for a script which would recieve files automaticly and put it in the home directory so I put together a real simple script to show you. The script doesn't care about overwriting existing files so you might consider adding a little while loop to change the name while there are exact matching filenames. What I think is the coolest is that this will put the files directly on the Desktop in Ubuntu.

Open your favourite editor and save the following script as bluetooth.sh
```

#!/bin/sh

# Real simple script to keep obexserver running
# eirik.hjelle@gmail.com wed 10.mai 06 12:51

# Configuration
UPLOADDIR=~/Desktop

while [ 1 ]; do
  TEMPFILENAME=`obexserver | grep tmp | awk '{ print $2 }'`
  mv $TEMPFILENAME $UPLOADDIR
  sleep 1
done

```

Then execute the following command to make it an executable file.
```

chmod a+x bluetooth.sh 

```

Set up all your bluetooth settings as explained in the tutorial and run the following command. The ending & puts it in the background. 
```
 
./bluetooth.sh &

```

---

### Post by Raavea on 2006-05-11
Is there a way to get this to work in Breezy with an NEC e616V (3g phone) ??


 When I do 'hcitool scan' it says 'Device is not available: No such device' o.O
I made the phone discoverable. Whats goin wrong?

---

### Post by JoNas-fr on 2006-05-14
Your HOWTO is so nice! It works perfectly on my Nokia 6230 ans Ubuntu 5.10.

But I still have a problem : how can I install .jar files (java apps) on it? Under windows I used "Nokia pc suite" and it works. When I send a .jar files under ubuntu, my nokia receive it but did'nt recognize his file type.

PS: Sorry for my pretty bad english :D

---

### Post by roland67 on 2006-06-22
Absolutely fantastic. Worked like a charm for my NOKIA 6820.
Thanks!

---

### Post by vivtho on 2006-07-12
> **andreasDK said:**
> When my 6600 finds my PC it asks for a code.

Hence everything I type is in asterixes i cannot spell my user/root code.

Does anyone know of a solution to this?

You don't need to type in your Ubuntu password.  Type in any number (usually limited to four digits).  You should then get a prompt on your monitor asking you to type in a code.  Just type the same number and hit enter... That should do it.

The same procedure worked on my 7710.

---

### Post by mostwanted on 2006-07-14
Thank you! Worked great, just transfered a jpg from my PC to my Samsung phone. I tried doing it the other way though, and my phone wouldn't recognise my PC properly (it saw the bluetooth signal, but when I tried connecting I got an error). Gonna check this out some more. At least it works one-way for now! :)

---

### Post by QkEterror on 2006-07-19
> **vivtho said:**
> You don't need to type in your Ubuntu password.  Type in any number (usually limited to four digits).  You should then get a prompt on your monitor asking you to type in a code.  Just type the same number and hit enter... That should do it.

The same procedure worked on my 7710.

I have a 7710 too. Can you pair your phone with Ubuntu? When I let my phone try to pair with Ubuntu nothing pops up to ask for a code. The phone says pairing failed.

By the way. Are you able to sync your 7710 through bluetooth with evolution?

---

### Post by clauguia on 2006-08-15
It worked not only to send to/from my nokia 6230 but to send files to/from my palm as well!!! :-O  Goodbye cables! :-)

(I know some people prefer to make a sync with palm, but sometimes you want just to move a file and i liked drive mode a lot, but it works only with craddle/cable thing. This way i have my "drive mode" with bluetooth, at least to rapidely move a file to and fro)

My /etc/bluetooth/rfcomm.conf file reads like this:

> #
# RFCOMM configuration file.
#


 rfcomm0 {
#  bind yes;
#       # Bluetooth address of the device
        device 00:11:9F:61:9C:80;
#       # RFCOMM channel for the connection
        channel 10;
#       # Description of the connection
        comment "Fone Nokia 6230";

}

 rfcomm1 {
#  bind yes;
#       # Bluetooth address of the device
        device 00:07:E0:8F:04:02;
#       # RFCOMM channel for the connection
        channel 10;
#       # Description of the connection
        comment "Palm T5";

}


Whats the "bind" thing?

Unfortunately, when i try gnome-obex-server it returns:
> 
** (gnome-obex-server:27500): WARNING **: OBEX server register error: -1

** (gnome-obex-server:27500): WARNING **: Unable to initialize OBEX source

** (gnome-obex-server:27500): WARNING **: Couldn't initialise OBEX listener


So, still obexserver to me... :-(

---

### Post by Cris987 on 2006-08-31
I have a Sony Ericsson T610 and it fails to detect my computer w/ Ubuntu Dapper. I followed this guide, but when I got to "hcitool scan", I received a response of "Device is not available: No such device". Would someone like to help me out ?

---

### Post by ingwarzeph on 2006-08-31
You are an absolute peach :p 

Just following the first post I was able to send and receive files on my Sony-Ericsson K608i without any problem at all. =D>

---

### Post by DanielTJ on 2006-09-12
Thanks globalspace, it was one of the important things for me to use windows for. do you think that calender sync is also possible anytime soon? is anybody busy with it?
and im really curious: how could you do this? what did you read?
thanks again.=D>

---

### Post by DanielTJ on 2006-09-12
Thanks globalspace, it was one of the important things for me to use windows for. do you think that calender sync is also possible anytime soon? is anybody busy with it?
and im really curious: how could you do this? what did you read?
thanks again.=D>

---

### Post by mborsato on 2006-10-27
And how can I use this HOWTO to hotsync Evolution with my Palm?

Tks.

---

### Post by movil on 2006-10-31
Thanks for the tutorial globalspace !

It worked great in my Dapper :)

Way cool!

---

### Post by Mrs Harris on 2006-11-07
Superb... works like a dream with Dapper, my bluetooth dongle and SE p910... thanks muchly :)

---

### Post by LKRaider on 2007-01-03
Thank you very much for this HowTo!

I too was having problems sending Phone -> PC, all the while PC -> Phone worked fine.

My phone is a **LG MG320c** (aka. **KG320**) and it uses the channel 9 for file transfers. You can find the channel used by your phone with this command (replace with your phone address):
```
sdptool records 00:05:C9:32:9F:91
```
then look for the **OBEX File Transfer** channel.

It still wasn't working for me, but then I finally figured out that my phone needed the FTP service on channel 9 instead of OPUSH, so I enabled the service:
```
sdptool add --channel=9 FTP
```

I also needed to enable authentication at the end of the file _/etc/bluetooth/hcid.conf_ :
```
        # Authentication and Encryption (Security Mode 3)
        auth enable;
        #encrypt enable;
```

And now it works! :D

---

### Post by pyrforos on 2007-01-26
i can see that the phone is trying to pair *( the bluetooth icon doesn't flashes) but i get this
```
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect

```
heeelpppp

---

### Post by mpneerkaje on 2007-07-28
Thanks a lot for this tutorial! it works really great for me in ubuntu 64-bit!
Though i had to struggle lil-bit as the library libopenobex-1.0-0 and obexserver for 64 bit were not available in the repository. i did some google search to fix this.
Other than that, everything worked amazingly superb! I'm very happy.
Thanks a lot once again.

---

### Post by Serax on 2007-09-11
> **andreasDK said:**
> When my 6600 finds my PC it asks for a code.

Hence everything I type is in asterixes i cannot spell my user/root code.

Does anyone know of a solution to this?

I am having the same problem and "CODE:gnome-obex-server" isnt working for me

---

### Post by asafm on 2007-09-22
> **andreasDK said:**
> When my 6600 finds my PC it asks for a code.

Hence everything I type is in asterixes i cannot spell my user/root code.

Does anyone know of a solution to this?

Same here - Anybody knows where I establish the code?

---

### Post by daniel1985 on 2007-11-17
think the standart pin is 1234

---

### Post by savethewabbit on 2008-04-17
hi, i'm trying to follow your guide but i'm already having a problem installing the packages. i can't get obexserver, here's the error i get:

```
The following packages have unmet dependencies:
  obexserver: Depends: libopenobex-1.0-0 (>= 1.0.0-rel) but it is not installable
E: Broken packages

```

any idea how to move around that and install obexserver? thanks.

---

### Post by rahid on 2008-11-11
Somebody thinks that blutooth communication with phone is not for Ubuntu. This is completly wrong. I found severel here where this type help available. 

After i bought a Sagem x700 without a data cable. I thought i cann't able to use internet with 3G/EDGE  network. But i find a great help on [Ubuntu-help.co.cc]("http://Ubuntu-help.co.cc"). 

If you  need youcan visit [this link]("http://ubuntu-help.co.cc/index.php/ubuntu-help/35-internet/45-connecting-internet-through-mobile-phone").

Thanks everybody.

---

### Post by mafi127 on 2011-05-09
DId everything what is in the first post but still cant connect wammu whit my phone.

[PHP]
Wammu is now searching for phone:
Discovering Bluetooth devices using PyBluez
Checking 6C:9B:02:54:DD:83 (Nokia Photon C6-03) - Could not guess vendor - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'blueobex']
All Bluetooth devices discovered, connection tests still in progress...
Finished 6C:9B:02:54:DD:83 (Nokia Photon C6-03) - Could not guess vendor - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'blueobex']
All finished, found 0 phones
No phone has been found!

[/PHP]

---

