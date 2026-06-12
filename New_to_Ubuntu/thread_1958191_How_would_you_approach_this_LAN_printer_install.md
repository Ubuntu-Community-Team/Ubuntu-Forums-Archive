---
title: "How would you approach this LAN printer install?"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-13
My MSHOME work-group is visible on my 11.10.

A Brother NFC-440CN printer functions on that LAN when I use WIN7.

I tried pinging the printer IP address but it does not see it.

How would you go about connecting to the printer?

I believe that the printer install is the last task I need to complete before I wave goodbye to Windows.

(Except for Netflix)

---

### Post by daslinkard on 2012-04-13
1. A network printer with built-in ethernet port usually provides a menu  button that will allow you to display IP address assigned to it. You  may also try printing self test or configuration page from your printer. 



 2. If you can't find an IP address of a network printer from the menu  display or your printer is connected to a printer server with no  display, you may find its address from any networked computer configured  to use the printer. To find the printer IP address from a **Windows**  machine, perform the following.  
[LIST]
[*]Start -> Printers and Faxes, or Start -> Control Panel -> Printers and Faxes
[*]Right-click the printer name, and left-click Properties
[*]Click the Ports tab, and widen the first column which displays IP address of the printers
[/LIST]
Once you get the IP address then you can go to add Printer...select Find Network Printer....in the Host box you will then input the Printer IP address....from there it should walk you through the rest of the install.  Good luck!

---

### Post by matt_symes on 2012-04-13
Hi

You may be able to use hp-probe to find the printer on the net from the Linux command line.

```
hp-probe -bnet
```Check out the man page.

Kind regards

---

### Post by Boyntonstu on 2012-04-13
> **matt_symes said:**
> Hi

You may be able to use hp-probe to find the printer on the net from the Linux command line.

```
hp-probe -bnet
```Check out the man page.

Kind regards

Probing network for printers. Please wait, this will take approx. 10 seconds...

warning: No devices found on the 'net' bus. If this isn't the result you are expecting,
warning: check your network connections and make sure your internet
warning: firewall software is disabled.
---------------------


From the control panel of the printer:

IP  169.254.067.200

boyntonstu@boyntonstu-s5704y:~$ ping 169.254.067.200
PING 169.254.067.200 (169.254.55.200) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable


The PC that the printer is connected to:  192.168.1.100

boyntonstu@boyntonstu-s5704y:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_req=1 ttl=128 time=0.313 ms
64 bytes from 192.168.1.100: icmp_req=2 ttl=128 time=0.182 ms
64 bytes from 192.168.1.100: icmp_req=3 ttl=128 time=0.174 ms
^C
   Printer Sharing is set on the XP machine.

That's where I am.

---

### Post by daslinkard on 2012-04-13
Once you get the IP address (192.168.1.100) then you can go to add Printer...select Find  Network Printer....in the Host box you will then input the Printer IP  address....from there it should walk you through the rest of the  install.  Good luck!

---

### Post by daslinkard on 2012-04-13
I read the original IP addy too fast....I would try the following IP addy for the printer of 192.168.1.102...I know in our old house this was the IP addy for the network printer we had back then.

---

### Post by cjazz on 2012-04-13
First of all, are your drivers installed? The drivers for your printer model are included in the packages brother-lpr-drivers-bh7 and brother-cups-wrapper-bh7, both of which can be installed through the Ubuntu Software Center or through sudo apt-get install from the command line.

Your next steps depend on your setup, and I'm a little confused as to what that is. Is your printer directly connected to a router by eternet or is it connected to a Windows printer?

---

### Post by Boyntonstu on 2012-04-14
> **cjazz said:**
> First of all, are your drivers installed? The drivers for your printer model are included in the packages brother-lpr-drivers-bh7 and brother-cups-wrapper-bh7, both of which can be installed through the Ubuntu Software Center or through sudo apt-get install from the command line.

Your next steps depend on your setup, and I'm a little confused as to what that is. Is your printer directly connected to a router by eternet or is it connected to a Windows printer?

Thanks, making some progress.

I installed brother-lpr-drivers-bh7  and then ran from Terminal  brprintconf_mfc440cn

Got:

boyntonstu@boyntonstu-s5704y:~$ brprintconf_mfc440cn
function list : /usr/./././Brother/Printer/mfc440cn/inf/brmfc440cnfunc
resource file : /usr/./././Brother/Printer/mfc440cn/inf/brmfc440cnrc

Usage on MFC440CN:
brprintconf_mfc440cn <[option command] [setting]>...
 -md    : Media
   Plain     : Plain Paper
   Inkjet    : Inkjet Paper
   BrotherGlossy : Brother Premium Glossy Photo Paper
   Glossy    : Photo Paper
   Transparencies : Transparencies
 -reso  : RResolution
   Draft     : Fast
   Fast      : Fast Normal
   Normal    : Normal
   Fine      : Fine
   Photo     : Photo
   Highest   : Highest
 -bidir : BiDirPrint
   OFF       : OFF
   ON        : ON
 -mirro : MirrorPrint
   OFF       : OFF
   ON        : ON
 -pt    : PaperType
   A4        : A4
   BrA4_B    : A4 (Borderless)
   Letter    : Letter
   BrLetter_B : Letter (Borderless)
   Legal     : Legal
   Executive : Executive
   B5        : JIS B5
   A5        : A5
   A6        : A6
   BrA6_B    : A6 (Borderless)
   PostC4x6  : Photo
   BrPostC4x6_B : Photo (Borderless)
   IndexC5x8 : Index Card
   BrIndexC5x8_B : Index Card (Borderless)
   PhotoL    : Photo L
   BrPhotoL_B : Photo L (Borderless)
   Photo2L   : Photo 2L
   BrPhoto2L_B : Photo 2L (Borderless)
   PostCard  : Postcard 1
   BrHagaki_B : Postcard 1 (Borderless)
   DoublePostCardRotated : Postcard 2 (Double)
   EnvC5     : C5 Envelope
   EnvDL     : DL Envelope
   Env10     : Com-10
   EnvMonarch : Monarch
   EnvYou4   : JE4 Envelope
 -thick : PaperThick
   Regular   : Regular
   Thick     : Thick
 -copy  : Copies
   numerical value
 -corm  : ColorOrMono
   Mono      : Grayscale
   Color     : Color
 -collate : Collate
   OFF       : OFF
   ON        : ON
 -doc   : Document
   Photo     : Photo
   Graphics  : Graphics
   Custom    : Custom
 -cm    : ColorMatch
   Natural   : Natural
   Vivid     : Vivid
   None      : None
 -ht    : HalfTone
   Diffusion : Diffusion
   Dither    : Dither
 -ce    : ColorEnhance
   OFF       : OFF
   ON        : ON
 -sd    : SlowDrying
   OFF       : OFF
   ON        : ON
 -brit  : Brightness
   numerical value
 -cont  : Contrast
   numerical value
 -red   : RedKey
   numerical value
 -green : GreenKey
   numerical value
 -blue  : BlueKey
   numerical value
==================================================


Next step?

---

### Post by cjazz on 2012-04-14
I apologize for being a little slow, but I'm still not sure how your printer is connected. Is it connected by ethernet to a router, for example, or by USB to a Windows computer?

---

### Post by mastablasta on 2012-04-14
as i understand it is actually connected to a windows mashcine which is on a network.
in which case you will need to connect it via samba. 

use command smbtree to see the exact address under which linux sees you printer.

then add a printer and select the option to add a network printer via samba. then in the network address put the path to printer and continue/forward. select the your printer in the next screen. this should set up the printer, since you already have the drivers for it.

---

### Post by Boyntonstu on 2012-04-14
> **mastablasta said:**
> as i understand it is actually connected to a windows mashcine which is on a network.
in which case you will need to connect it via samba. 

use command smbtree to see the exact address under which linux sees you printer.

then add a printer and select the option to add a network printer via samba. then in the network address put the path to printer and continue/forward. select the your printer in the next screen. this should set up the printer, since you already have the drivers for it.


smbc tree yielded:

Samba Commander 1.2.2                       Inspiration is my wife Magda (Arida)
&#9484;/home/boyntonstu/&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9484;//MSHOME/&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;T&#9474;file or directory name        &#9474;size &#9474;&#9474;T&#9474;workgroup, share, file or dire&#9474;size &#9474;
&#9474;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9474;&#9474;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9474;
&#9474;D&#9474;..                            &#9474;     &#9474;&#9474;D&#9474;..                            &#9474;     &#9474;
&#9474;D&#9474;.adobe                        &#9474; 4.0K&#9474;&#9474;H&#9474;JANDESKTOP | Jan's Desktop    &#9474;     &#9474;
&#9474;D&#9474;.cache                        &#9474; 4.0K&#9474;&#9474; &#9474;                              &#9474;     &#9474;
&#9474;D&#9474;.compiz&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   &#9474;     &#9474;
&#9474;D&#9474;.compiz&#9474;                                                          &#9474;   &#9474;     &#9474;
&#9474;D&#9474;.config&#9474;                      I can't enter to                    &#9474;   &#9474;     &#9474;
&#9474;D&#9474;.dbus  &#9474;                         JANDESKTOP                       &#9474;   &#9474;     &#9474;
&#9474;D&#9474;.fontco&#9474;                       Access denied.                     &#9474;   &#9474;     &#9474;
&#9474;D&#9474;.FreeCA&#9474;                                                          &#9474;   &#9474;     &#9474;
&#9474;D&#9474;.gconf &#9474;                           [ OK ]                         &#9474;   &#9474;     &#9474;
&#9474;D&#9474;.gegl-0&#9474;                                                          &#9474;   &#9474;     &#9474;
&#9474;D&#9474;.gimp-2&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;   &#9474;     &#9474;
&#9474;D&#9474;.gnome2                       &#9474; 4.0K&#9474;&#9474; &#9474;                              &#9474;     &#9474;
&#9474;D&#9474;.gstreamer-0.10               &#9474; 4.0K&#9474;&#9474; &#9474;                              &#9474;     &#9474;
&#9474;D&#9474;.gvfs                         &#9474;   0B&#9474;&#9474; &#9474;                              &#9474;     &#9474;
&#9474;D&#9474;.hplip                        &#9474; 4.0K&#9474;&#9474; &#9474;                              &#9474;     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Retry read shares list 1

Is there anything else that you notice?


In PLACES  I can see MSHOME and I have access to JANDESKTOP and all of the files on the C: drive.

How do I set Acess on JANDESKTOP  a P4 2.6 Ghz PC with Win XP SP2.

Why does places work fine for files sharing and Samba not?

We are making progress.

Thanks

P.S.  On review is "Jan's Desktop" the problem?

---

### Post by matt_symes on 2012-04-14
Hi

> From the control panel of the printer:

IP  169.254.067.200

boyntonstu@boyntonstu-s5704y:~$ ping 169.254.067.200
PING 169.254.067.200 (169.254.55.200) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable


The PC that the printer is connected to:  192.168.1.100

boyntonstu@boyntonstu-s5704y:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_req=1 ttl=128 time=0.313 ms
64 bytes from 192.168.1.100: icmp_req=2 ttl=128 time=0.182 ms
64 bytes from 192.168.1.100: icmp_req=3 ttl=128 time=0.174 ms

Sorry for the late reply.

Your printer IP: _169.254.067.200_.
Your computer IP: _192.168.1.101_
Your other conputer: _192.168.1.100_.

Your printer is on a different subnet than the computers on your network. 

Give the printer a valid ip address and subnet; say (192.168.1.102/24) if it is free and available. Also try to give it a static ip address

Kind regards

---

### Post by Boyntonstu on 2012-04-15
> **matt_symes said:**
> Hi



Sorry for the late reply.

Your printer IP: _169.254.067.200_.
Your computer IP: _192.168.1.101_
Your other conputer: _192.168.1.100_.

Your printer is on a different subnet than the computers on your network. 

Give the printer a valid ip address and subnet; say (192.168.1.102/24) if it is free and available. Also try to give it a static ip address

Kind regards

Thanks for hanging in there.

I tried a few different ip addresses.  192.168.1.102 pinged with dups.

192.168.1.103,4....... would not ping.

---

### Post by matt_symes on 2012-04-15
Hi

> **Boyntonstu said:**
> Thanks for hanging in there.

I tried a few different ip addresses.  192.168.1.102 pinged with dups.

192.168.1.103,4....... would not ping.

The printer may not respond to pings but when it's on the same subnet as your computer does.....
[FONT=monospace]
[/FONT]```
hp-probe -bnet
```
...find the printer ?

Kind regards

---

### Post by Boyntonstu on 2012-04-18
> **matt_symes said:**
> Hi



The printer may not respond to pings but when it's on the same subnet as your computer does.....
[FONT=monospace]
[/FONT]```
hp-probe -bnet
```
...find the printer ?

Kind regards

Ye, I found the printer after I installed Hardy.

My USB wifi adapter works and I can see the LAN workgroup and the files on my wife's PC.   Close to installing the printer, but not there yet.

---

### Post by alphacrucis2 on 2012-04-18
The Address 169.254.067.200 indicates that there is no DHCP server available to the printer. It is from a special local address block that is used when a device is unable to locate a DHCP server:

> [COLOR="Red"]In IPv4, link-local addresses are codified in RFC 5735 and RFC 3927. Their utility is in self-autoconfiguration by network devices when Dynamic Host Configuration Protocol (DHCP) services are not available and manual configuration by a network administrator is not desirable.

The block 169.254.0.0/16 is reserved for this purpose, with the exception of the first and the last /24 subnets in the range. If a host on an IEEE 802 (ethernet) network cannot obtain a network address via DHCP, an address from 169.254.1.0 to 169.254.254.255 may be assigned pseudorandomly. The standard prescribes that address collisions must be handled gracefully.[/COLOR]


Why don't you just plug an ethernet cable into your printer and connect it up to your router or switch and it will get a proper IP address allowing all your PC's to talk to the printer directly without having to go via the Windows machine. Better still, after directly connecting your printer the the network, then configure it with a static address in the 192.168.1.x range as someone else suggested. make sure it doesn't conflict with your dhcp range though.

---

### Post by Shazaam on 2012-04-18
"Why don't you just plug an ethernet cable into your printer and connect it up to your router or switch and it will get a proper IP address allowing all your PC's to talk to the printer directly without having to go via the Windows machine".

+1
That's what I did with my MFC420CN. Plugged it into my dsl modem and it works fine. I also don't need to have my other pc running to access the printer.

---

### Post by mastablasta on 2012-04-19
> **Boyntonstu said:**
> How do I set Acess on JANDESKTOP a P4 2.6 Ghz PC with Win XP SP2.

 
This should be address:
smb://MSHOME/jandesktop
 
followed by /printers/yourprinternameinwidnows or something like that.printer needs to be shared to other users and also if oyu want fiels to be shared form windows mashicne you need to mark folder that is shared and i am not sure maybe partition also.
 
the problem i see here is that it doesn't see the printer. if printer is indeed LAN printer that connect via ethernet cable to computer it is indeed much better and mroe logical to simply connect it directly to router (or nowadays modems often can already connect more than one user...).

---

