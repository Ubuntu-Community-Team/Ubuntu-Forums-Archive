---
title: "Using a GSM Cellphone as a GPRS Modem"
date: 2006-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by gr0kzer0 on 2006-04-26
HOWTO: Use a GSM mobile phone as a GPRS modem, with wvdial, under Ubuntu 5.10 Breezy Badger

Why would anyone _want_ to use a mobile phone as a modem? Call costs are expensive, connections are unreliable, and data transfer speeds are slow. In these days of high-speed wireless connections, what's the point?

Well, costs aren't necessarily that high. True, voice calls can be pretty pricey, but I'm talking about using the phone as a GPRS modem, not regular dial-up. This means that, instead of using the usual voice circuit, we will be using the "always on" GPRS connection.

"Always on"?!! That's even worse!!

No. Although the terminology is "always on", cellphone service providers tend to charge for GPRS traffic in one of two ways: 1. per KB of data transferred; or 2. a fixed rate regardless of how much traffic there actually is.

I think I'd better explain a few points before we go on.

GSM cellphone networks use a protocol called GPRS (General Packet Radio Service) for transmission of data. This is used, for instance, for photo messaging or WAP browsing, though it can also be used to make a regular internet connection.

If you use your cellphone's GPRS service to make an internet connection, your phone service provider is also your internet service provider. You dial a special number that gives you access to their GPRS network, you use their domain name servers, etc.

At this point, I think it's simplest for me to describe what I did to use my mobile phone as a modem.

Before you can do anything, you will need a means to link your phone to your computer, and a copy of wvdial.

To make the connection, if your phone and PC are suitably equipped, you may be able to use Bluetooth or infrared. But my phone, a lowly Nokia 3220, has neither of these. So I used a third-party's USB-Serial data cable, which I believe is a copy of Nokia's DKU-5 cable. Ubuntu identifies it as:

Bus 001 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

Now, connect your phone to your PC, making sure that the phone is on "stand by" (ie not using its WAP browser or making a call). Then give the command

sudo wvdialconf /etc/wvdial.conf

and you should get output along the lines of this:

t0p@lapt0p:~$ sudo wvdialconf
Password:
Usage: wvdialconf <configfile-name>
        (create/update a wvdial.conf file automatically)
t0p@lapt0p:~$ sudo wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

Port Scan<*1>: Scanning ttyLTM0 first, /dev/modem is a link to it.
ttyLTM0<*1>: ATQ0 V1 E1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 Z -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyLTM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.31
ttyLTM0<*1>: Speed 4800: AT -- OK
ttyLTM0<*1>: Speed 9600: AT -- OK
ttyLTM0<*1>: Speed 19200: AT -- OK
ttyLTM0<*1>: Speed 38400: AT -- OK
ttyLTM0<*1>: Speed 57600: AT -- OK
ttyLTM0<*1>: Speed 115200: AT -- OK
ttyLTM0<*1>: Max speed is 115200; that should be safe.
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47  S48
Port Scan<*1>: S49  S50  S51  S52  S53
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Nokia
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- ~\uffff
ttyUSB0<*1>: Speed 460800: AT -- [06]\uffff
ttyUSB0<*1>: Speed 460800: AT -- ~\uffff
ttyUSB0<*1>: Max speed is 230400; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyLTM0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB0<Info>: Speed 230400; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
t0p@lapt0p:~$

Looking at this output, we can see wvdial found 2 modems: /dev/ttyLTM0 (also known as /dev/modem) and /dev/ttyUSB0. How do we know which (if either) is the phone? By the line:

ttyUSB0<*1>: Modem Identifier: ATI -- Nokia

Wvdial dumps its info to the file /etc/wvdial.conf. If we have a look at that fkile it says:

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
; Username = <Your Login Name>
; Password = <Your Password>

Hmm. Not much good to us, seeing as it's referring to /dev/ttyLTM0, which is my laptop's built-in Lucent winmodem. But wvdial will use this file when dialling out. So we need to edit it. Remember the last 2 lines of all that output from the wvdialconf command? Just kn case your photographic memory's playing up, here they are again:

ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB0<Info>: Speed 230400; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

You'll need to call your cell service provider and get some info from them, such as Username and Password. Then, by amalgamating what you learn from the wvdialconf input and what your friendly cellphone people tell you, you should be able to create an /etc/wvdial.conf file that looks similar to this:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = A
Password = B
Stupid Mode = 1

Your completed file is unlikely to be exactly the same as mine. For instance, for my mobile network (Orange UK) Username and Password are blank. But wvdial doesn't like that, you _must_ put something in there. Also, it will not connect unless you include that line

Stupid Mode = 1

As for that unusual phone number, *99# - that's what you need to make the GPRS connection. Different mobile networks, especially in other countries, will need different numbers. And another user of Orange UK (using a Sony Ericsson phone) reported having to use *99***4*. All I can suggest is: ask your network what to use. If it doesn't work, experiment.

So, now you have a completed wvdial.conf file, and your phone is connected to your computer, all that's left is to try it. Open a console (Ctrl+Alt+F1) and type

sudo wvdial

With any luck, your output will resemble this:

t0p@lapt0p:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Apr 26 23:11:44 2006
--> pid of pppd: 11096
--> Using interface ppp0
--> local  IP address 10.33.228.142
--> remote IP address 10.6.6.6
--> primary   DNS address 193.35.133.10
--> secondary DNS address 193.35.134.10

Now, the output stops, and seems to "hang". But it's not doing nothing - it's holding the connection open and waiting for you to use it.

To test it, change to another console (eg Ctrl+Alt+F2) and type

ping -c1 80.84.72.25

and if the connection's ok, you should get comething like this:

t0p@lapt0p:~$ ping -c1 80.84.72.25
PING 80.84.72.25 (80.84.72.25) 56(84) bytes of data.
64 bytes from 80.84.72.25: icmp_seq=1 ttl=42 time=781 ms

--- 80.84.72.25 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 781.703/781.703/781.703/0.000 ms
t0p@lapt0p:~$

So, now to do something _useful_ with  this internet connection - like surfing the web. Swap to the graphical interface (Ctrl+Alt+F7), and launch Firefox (or whatever browser you have). If you're lucky, it's already configured for this... just type in the URL [www.google.com](www.google.com), and it takes you there!

Note: it very well be quite slow. But that's only to be expected. This isn't broadband, cable, not even 56K dialup. It's a cellular phone, dammit!

Nevertheless, it's very useful. You can web-surf, use telnet and ssh. Downloading software probably isn't a very good idea as it's so slow. Plus a lot of cell plans charge per KB transferred, so you may need to watch your data usage. Then again, if like me you pay a fixed amount no matter how much data you transfer... go for it!!!

When you've finished your session, return to the console where you initiated wvdial (Ctrl+Alt+F1 or whatever) and press Ctrl+C. That will break the connection/hang up.

Well, I can't think of anything to add. If you want to ask me something - feel free!

---

### Post by cvmostert on 2006-05-25
Looks like a great guide, I will try and use it when I am on holliday in SA thanx

---

### Post by hellmet on 2006-07-31
gr8 guide dude.
thanks

---

### Post by vaibhavkaushal123 on 2006-08-19
OK great Guide. But that was NOKIA 3220. How do I connect my SAMSUNG SGH c-200 as modem for the DAPPER DRAKE??? I connect to internet using this phone and without any problems on my Windows XP system. I need the DAPPER DRAKE to do the same thing. 

SO overall I have two questions:
1. How does ubuntu linux IDENTIFY a cable connected to it??? Ihad also tried to connect my mom's NOKIA 3220 but i did not get any prompt like windows XP which couls say of the device was identified or not. I know the rules are different for Linux but i need to know of UBUNTU is able to identify the deive. ** My phone is not a NOKIA 3220. It is a SAMSUNG SGH c200. ** Where do we get the info on what is connected to the system?? I mean to ask...how do I come to know if UBUNTU successfully identifies that something is connected to my USB ( exactly speakin com-5 port)?? I know my target phone number. I also have almost the same configuration as that seems to be of gr0kzer0. So I think I will be able to configure the rest but I am syuck in the first point:

MAKING UBUNTU IDENTIFY MY DEVICE. HOW DO I COME TO KNOW THAT UBUNTU HAS IDENTIFIED THAT A DEVICE IS CONNECTED TO THE SYSTEM???

the seond question is of course about configuring wvdial but then it can help only if I get the linux identify the USB connection.
PLease help me. 

Vaibhav (*_*)

---

### Post by linuxn00b73 on 2006-12-14
Well across the pond in the States mobile phone data connections are actually faster than 56K dialup. My phone for example goes 230Kbps and an EVDO capable phone as fast as 700Kbps. I have unlimited usage for a few bucks a month. Not having to find a WiFi hotspot is well worth it.

I don't know for other phones in the U.S., but for SprintPCS you put the number dialed #777 with the pound sign included.

A couple _QUESTIONS_ though. **Will wvdial allow me to go 230Kbps? Or 700K if I upgrade my phone?** Also my username and password are blank also, guess they authenticate by the cell phone you call from. **Do I just put "A" for username and "B" for password for it to work?**
Also my phone is CDMA not GSM so I hope this works.

---

### Post by pavel_kbc on 2006-12-16
Hello , can you make Howto for edgy please ..

---

### Post by gr0kzer0 on 2007-01-23
Hi guys n gals. Sorry i havent been much help figuring how to use Wvdial with other set-ups. My discovery was down to trial n error, and as for doin it with other phones/networks, i got no clue at all. Eg, non-nokia 3220, non-orange uk? I'm sure some of you will get me right. And now _I_ need help: more network-specific info is an idea, i wana help good as can be. Help me? Plz? Or am i a waste?

---

### Post by thesandeep on 2007-01-27
Thanx buddy,
This work really fine.
Good work, keet it up.

I am using a Sony Ericsson K320i

---

### Post by nicnocquee on 2007-02-04
hi, i'm using sony ericson phone, and i only have infrared connection. can you tell me how to do it?or link so that i can try..thx...

---

### Post by mloudon on 2007-02-07
wvdial can't automatically configure this modem, but i've managed to connect using the following wvdial.conf (for vodacom in South Africa - you might have to dial a different number, and you'll have to change the pin)

```
[Dialer Defaults]

Phone = *99***1#
#Phone = *99#
Username = anything
Password = anything
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer gprs]
Modem = /dev/ttyS0
Baud = 115200
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
```

then, connect with 

```
sudo wvdial gprs
```

--
Melissa

---

### Post by dodgy_devil on 2007-02-15
> **mloudon said:**
> wvdial can't automatically configure this modem, but i've managed to connect using the following wvdial.conf (for vodacom in South Africa - you might have to dial a different number, and you'll have to change the pin)

```
[Dialer Defaults]

Phone = *99***1#
#Phone = *99#
Username = anything
Password = anything
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer gprs]
Modem = /dev/ttyS0
Baud = 115200
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
```

then, connect with 

```
sudo wvdial gprs
```

--
Melissa
Thanks for this confict file it really helped me to get connected. Just one small question, I got connected according to the terminal and the connection even showed on my phone but i am still unable to browse the web.... Do you have any idea why or how i can find out what my connection status is. Im also from South Africa connecting with a Sony Ericsson w800i on Ubuntu edgy to Vodacom.

Would appriciate you help
Thanks
Dodgy

---

### Post by gr0kzer0 on 2007-02-23
I'm currently thinking of writing a more comprehensive guide n this matter - ie not restricted to Nokia 3220s, not restricted to Orange UK.  I see some of you have posted your experiences involving other phones and in other countries.  What would be cool is if everyone who gives this a go could write up what happened: if it was successful or not, what you tried, anything really that has to do with this subject.  You could write it in this thread or you could send me a personal message, or you could email me (mtop6867@gmail.com).  This guide will appear in my Wordpress blog, so the Comments there would also be a good place to write to me.

As I mentioned before, I worked this out mostly through trial and error.  There's very little on the web concerning the use of mobile phones as modems. I emailed one of the developers of wvdial about what I'd learned, and he told me that he had never heard of wvdial being used for this.  (He was also very happy to learn that his program was still finding uses *new* uses, no less! - so long after he created it, and in a world so used to broadband highspeed connections that an app like wvdial, made for dial-up internet access, might be considered by some to be obsolete.  (Note to Ubuntu developers: *please don't stop including wvdial in your distros.*  Broadband may be pretty much default nowadays in the so-called developed world; but in the "developing" world, dial-up access is still popularly used, not to mention the necesity of using wvdial in what I'm doing.) So a guide on it is sorely needed - and the more universal the guide is, the more people it is relevant to and can help, the better.   So please, if you can connect your phone to your computer (with a data cable, or bluetooth, or infrared), please give it a go and drop me a line saying how it went.  Thanks!

EDIT: My blog is at [http://mtop6867.wordpress.com](http://mtop6867.wordpress.com).  There ain't much there right now, but I plan to fill it with stuff to do with Linux and Ubuntu, plus other material that you may or may not be interested in.  So, pay it a visit some time - hopefully after you've experimented with using wvdial to access the net, and can write lots of useful insight in the Comments.

---

### Post by orzeuek on 2007-02-24
Thanx, worked like a charm.

I have a Samsung SHG-Z370 UMTS phone for testing purposes. All I had to do was change Your Initial settings and Phone number [it was given to me and is special for this network, so no help if I would post it here]. I also have blank user and pass and that's why my gnome-ppp wouldn't work [still asking for password on connection].

So wvdial was the perfect solution. Thanks again.

---

### Post by AlanR8 on 2007-05-09
Well, what can I say. This thread sorted things for me here in Manchester UK!

THANKS gr0kzer0!!!!!

My phone is a Nokia 6280, on Vodafone, that I connect with the supplied lead which I believe is the DKU5. I run Kubuntu Fiesty and found that wvdial was already installed. 

I ran the conf file as suggested but then went straight to it and opened it as Root and made the edits using *99# as the number to dial, A as the user name and B as the password.

Connected first time!

Alan

---

### Post by pratik_narain on 2007-05-18
Just tell how to know that the cable is recognized. I tried dmesg but I couldn't understand the output as I don't know the product and vendor IDs for the DKU 5 cable.

---

### Post by simongdkelly on 2007-05-24
> **dodgy_devil said:**
> Thanks for this confict file it really helped me to get connected. Just one small question, I got connected according to the terminal and the connection even showed on my phone but i am still unable to browse the web.... Do you have any idea why or how i can find out what my connection status is. Im also from South Africa connecting with a Sony Ericsson w800i on Ubuntu edgy to Vodacom.

Would appriciate you help
Thanks
Dodgy

I have exactly the same problem. WVDial seems to connect fine :
```

--> pppd: &#65533;[10][06][08]x [06][08]
--> local  IP address 10.64.124.86
--> pppd: &#65533;[10][06][08]x [06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;[10][06][08]x [06][08]

```

but then I can't even ping anything. I'm also in SA using a SonyEricson v600i on Ubunty Feisty.
Anybody else having this problem? Anybody found a solution?
Simon

---

### Post by ERGOsgirl on 2007-05-25
:KS
Don't know if this will help anyone.

I have a Motorola V557 connected by USB data cable to my IBM Thinkpad R50.  I have At&t/Cingular service.  

I am running Feisty Fawn, first apt-get or go to synaptic and install Gnome PPP
  Phone #  *99***1#
User:  [email]ISP@CINGULARGPRS.COM[/email]
password:  CINGULAR1

Next, go into Setup  auto detect the device
Type: usb modem
Uncheck the "wait for dialtone"

under Options:
uncheck all boxes except "Ignore terminal strings (stupid mode)"
Hit close and then connect.
Happy Internet experiences to you.

---

### Post by aquavitae on 2007-05-29
> **simongdkelly said:**
> I have exactly the same problem. WVDial seems to connect fine :
```

--> pppd: &#65533;[10][06][08]x [06][08]
--> local  IP address 10.64.124.86
--> pppd: &#65533;[10][06][08]x [06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;[10][06][08]x [06][08]

```

but then I can't even ping anything. I'm also in SA using a SonyEricson v600i on Ubunty Feisty.
Anybody else having this problem? Anybody found a solution?
Simon

I have exactly the same problem, though I've been using kppp instead of wvdial.  I'm on CellC with a Sony Ericsson K800i.  It worked fine until a couple of days ago when it suddenly stopped.  As a check I tried it in windows (after installing the drivers) and it works there so I assume its something to do wither ubuntu rather than with the service provider.

---

### Post by MichiganBill on 2007-06-16
Thanks gr0kzer0!!!:KS:KS

Your guide worked like a charm!!

I am running Feisty Fawn with Gnome PPP and wvdial. I use Cingular (AT&T) and a Motorola V3.
The following worked for me first time:

Phone # *99***3#
User: [email]WAP@CINGULARGPRS.COM[/email]
password: CINGULAR1

Ubuntu is great.

Thanks again!

---

### Post by Danni on 2007-06-20
Thank you so much for this! After having a ton of trouble trying to set up an internet connection using bluetooth, this worked perfectly first time :)

Nokia E61 on T-Mobile UK.

---

### Post by eyecolor on 2007-06-20
many thnxx
with
Modem = /dev/rfcomm0 

for the bluetooth module worx for nokia 6230

---

### Post by theDaveTheRave on 2007-06-27
> **pratik_narain said:**
> Just tell how to know that the cable is recognized. I tried dmesg but I couldn't understand the output as I don't know the product and vendor IDs for the DKU 5 cable.

I don't know how this cable connects up, but if like I expect it is a USB connection at one end then try the following.
[QUOTE=]
davem@Dartagnon:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 003: ID 03f0:0904 Hewlett-Packard DeskJet 845c
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 050d:7051 Belkin Components
Bus 001 Device 001: ID 0000:0000
davem@Dartagnon:~$
[/QUOTE]

If i then hook up my Nokia E65 and run the same command
[QUOTE=]
davem@Dartagnon:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 004: ID 0421:0508 Nokia Mobile Phones
Bus 003 Device 003: ID 03f0:0904 Hewlett-Packard DeskJet 845c
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 050d:7051 Belkin Components
Bus 001 Device 001: ID 0000:0000
davem@Dartagnon:~$
[/QUOTE]

To be honest the thing I would like to be able to do is get at the images and files on the phone, then I could get hold of a memory card and use it like a glorified USB memory stik, even better if it could communicate with evolution! - but all this is probably outside of the scope of this thread.... so I'll just have to be happy that I like the phone!

Dave

---

### Post by mafitzpatrick on 2007-06-29
Just a note to say for those with Sony Ericsson K800i / W800i phones (and perhaps other makes / models) there is an easier method for using a mobile phone as a modem. I've put together [a How To and posted it here in ]("http://ubuntuforums.org/showthread.php?t=487838")the forums.  It only requires a few settings on the phone itself and no fiddling with configs.

Using the tutorial in this thread I managed to get a connection but (as a few other people have reported) was not able to ping or browse the internet.  If you're having similar problems you may want to try this instead! Thanks & let me know how you get on.

---

### Post by ZDUNAS on 2007-06-29
Hey,
I've got one problem with connecting my nokia 6020 to Ubuntu Feisty, and I see that you are very experienced at things like that. I would be very glad if anyone of you could help me because I'm starting my adventure with linux;).
OK so here we go:
When I type lsusb, I've got "Nokia Connectivity Cable DKU-5" not "PL2303" :/
I've also downloaded a program (pGPRS) which connects to internet through cell phone modem, but it
seems that system doesn't see the modem :/ This program is making some files in /etc/ppp/peers/ which should make this connection to work, but it doesn't :/  If I type pppd call gprs (commend to connect) i've got this "unrecognized option /dev/ttyUSB0" and it happens with every USB port!!!

Please help me... What should I do? How to make it work? How to make my ubuntu to see the phone not cable?
Ubuntu without internet is like hand without fingers...

---

### Post by seetho on 2007-07-10
I was actually using my Nokia E61 mobile phone as a 3G modem on my Edgy/Feisty notebook some time already.  Since I recently configure another 2 phones and service providers on my other notebook running Dapper, I should post here in case it helps others trying the same thing.  I will describe the connections using cable since I most often use it while on the road - phone batteries last a little longer than using bluetooth.  All the steps are tested working on Dapper using Nokia 6230 and Nokia E61 connected with DKU-2 cable (USB), and Samsung SGH-Z720 connected with the cable that came with the phone.  I connect to 2 providers on GPRS, EDGE and 3G services.  They all work.  In fact I'm writing this post on a bus travelling to another city - a 5 hour journey. 

What I did was quite straight forward and uncomplicated.  So here it goes...

First you must make sure that your phone settings are done correctly.  My providers have a service where they send a service message with the correct settings to my phone.  Once I save these messages the settings are applied and I'm ready to go.  You can test your settings by connecting using your phone's wap or web browser.

Connect the cable to your phone and to a USB port on your notebook/PC.  On the Nokia the phone shows the message "Data enhancement connected" once I connect.  On the Samsung it ask me if I wish to disable bluetooth - select "Yes", otherwise it will not work.

I will use wvdial to dialup.  You can use gnome-ppp, but it only allows one single configuration which doesn't work for me since I have multiple phones and providers.

There's a default configuration file for wvdial: /etc/wvdial.conf.  It is essentially empty by default. Mine looks like the following:

```

[Dialer Defaults]
Phone =
Username =
Password =
New PPPD = yes

```

You can edit this file and put your configurations here.  wvdial uses this configuration file by default.  If you do that then you have to make it readable by everyone so that you do not have to use the "sudo" command to connect everytime you want to connect.  Just do:

```

sudo chmod 644 /etc/wvdial.conf

```

Alternatively you can create .wvdialrc in your home directory.  If this file exists then wvdial will use it.  I prefer to create this file since I do daily rsync backup of my entire home directory to my remote backup server, so this configuration file gets backed up along with everything else.

The following is the content in my config file (~/.wvdialrc):

```

[Dialer Defaults]
Phone = 
Username = 
Password =
New PPPD = yes


[Dialer DigiCable]
Modem = /dev/ttyACM0
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","diginet"
Phone = *99#
Dial Command = ATDT
Username = digi
Password = digi
Ask Password = off
Auto DNS = on
Check Def Route = off
Carrier Check = off
Stupid Mode = on
Auto Reconnect = off
Idle Seconds = 0
Abort on Busy = off
Abort on No Dialtone = off
Dial Attempts = 1


[Dialer DigiBluetooth]
Modem = /dev/rfcomm0
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","diginet"
Phone = *99#
Dial Command = ATDT
Username = digi
Password = digi
Ask Password = off
Auto DNS = on
Check Def Route = off
Carrier Check = off
Stupid Mode = on
Auto Reconnect = off
Idle Seconds = 0
Abort on Busy = off
Abort on No Dialtone = off
Dial Attempts = 1

```

I left the default configuration blank on purpose to force the use of a specific dialer configuration.  You will notice that I also have Bluetooth dialer configure.  The only difference between the 2 configurations is the "Modem" line.  (Bluetooth configuration needs you to do a bit more - which I will not get into here.)

Change the "Phone" number to dial.  Not all providers use *99#.  You of course have to change "Init3" line to match the information given by your provider.  It still works on mine if I remove it.  Of course you have to change "Username" and "Password" to match yours.

When you are ready you can dialup using the command in terminal:

```

wvdial DigiCable

```

This will select the DigiCable section of the configuration to apply to wvdial.  That's all!  You should be connected by now.  Open your favourite web browser and test it.

To disconnect just use Ctl-C.

You can create separate launcher's for the different dialer configs.

---

### Post by thenailedone on 2007-11-14
... just stumbled onto this thread, I have been trying to connect to the net using a Samsung F300i on Feisty... no luck so far... I will be reading and trying some of the info in this guide and see if it helps...

---

### Post by seetho on 2007-11-15
> **thenailedone said:**
> ... just stumbled onto this thread, I have been trying to connect to the net using a Samsung F300i on Feisty... no luck so far... I will be reading and trying some of the info in this guide and see if it helps...

If you're not getting any luck you should post back here.  Maybe someone can offer some help.

If you get it working do post back here.  The info may help others.

Good luck.

---

### Post by SaltyCrak on 2007-11-24
if this works and i can get my w950i to dial up then i'm sold on ubuntu and removing my win partition :)
RESPECT!

---

### Post by SaltyCrak on 2007-11-24
gr0kzer0, you are a legend!

i'm new to ubuntu, but am not going back to win :) thank you. 

one thing... i'm trying to use gnome ppp and it says i'm connected, but i have no net access, i can't ping either. 
if i use sudo wvdial gprs it goes through perfectly and everythin works. but i don't really want the terminal window open. logically the connection closes when i close the window. 

i quite like the idea of using gnome ppp, any ideas on how to get this working?

anyway, have a great weekend further. :guitar:

---

### Post by thenailedone on 2007-12-07
Hello again... so far no luck... I keep getting the same error message no matter what I do... and I keep forgetting to make a screen shot :(

I will be waiting for Gutsy and trying again...

---

### Post by Lu Bu on 2008-01-19
> **SaltyCrak said:**
> gr0kzer0, you are a legend!

i quite like the idea of using gnome ppp, any ideas on how to get this working?

anyway, have a great weekend further. :guitar:

it kinda work
But compare with my the two modems that i have
My Nokia 6822 was easier to installed than my so-called AK-56KI-LU modem

I can go online with both of these modems in windows
But it is a different story with Ubuntu
The hardest part now is to get the right configuration to get it working.

---

### Post by bharadwaj on 2008-01-28
thanx man really helped out!

---

### Post by doi65535 on 2008-01-31
looky how i did it with a motorola v1075 on vodafone/romania via usb and bluetooth

[http://ubuntuforums.org/showthread.php?t=318733&page=2](http://ubuntuforums.org/showthread.php?t=318733&page=2)

---

### Post by SB-RAD on 2008-01-31
A handy command which you can use if you can query the com port of the modem is:

AT+CGDCONT?

This will respond back with the packet switched Access Point Names (APN) currently configured in the modem of your device for those who use more than one APN

+CGDCONT: 1,"IP","internet","0.0.0.0",0,0
+CGDCONT: 2,"IP","acmedotcom","0.0.0.0",0,0

So in the dial script you can use:

*99***1# to get the modem to call internet

or

*99***2# to get the modem to call acmedotcom

If no APNs are configured you can enter them in with:

AT+CGDCONT=?,"IP","nameofapn"

? is the location and relates to the dial code
" must enclose the IP (Uppercase) and name of the APN.

You can use this if you use the device with multiple SIMs or a SIM with multiple APNs.

A mobile subscription may have more one or more APNs but you may not see them wth +cgdcont command so check the net or ask your service provider.

---

### Post by kumarkrishnan on 2008-04-20
Hi,
  I am using Sony Ericsson W810I, BSNL, India connection. I am trying to use GPRS connection for web browsing in Ubuntu. I am getting following message after &#8220;wvdial" command. I am getting GPRS connection symbol in my phone. But, still I tried &#8220;ping &#8211;c1 80.84.72.25&#8221;. I got 
--- 80.84.72.25 ping ststistics ---
1 packets transmitted, o received, +1 errors, 100% packet loss, time 0ms.


Also find my wvdial.conf file content at last. In that, My Username and password is deleted to post in forum.


[root@localhost ~]# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***4#
--> Waiting for carrier.
ATDT*99***4#
CONNECT
~[7f]}#@!}!}!} }8}#}$@#}(}"}'}"}"}&} } } } }%}&}%L}6Chy~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Apr 20 13:23:15 2008
--> Pid of pppd: 25958
--> Using interface ppp0
--> pppd: &#65533;[0c]# `
--> #
--> pppd: &#65533;[0c]# `
--> #
--> pppd: &#65533;[0c]# `
--> #
--> pppd: &#65533;[0c]# `
--> #
--> pppd: &#65533;[0c]# `
--> #
--> local  IP address 10.0.18.23
--> pppd: &#65533;[0c]# `
--> #
--> remote IP address 10.64.64.64
--> pppd: &#65533;[0c]# `
--> #
--> primary   DNS address 218.248.240.23
--> pppd: &#65533;[0c]# `
--> #
--> secondary DNS address 218.248.240.135
--> pppd: &#65533;[0c]# `
--> #









Wvdial.conf content

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = 
Phone = *99***4#
Modem Type = USB Modem
Stupid Mode = 1
Baud = 460800
Modem = /dev/ttyACM0
ISDN = 0
Username = 
New PPPD = yes

---

### Post by davidgutu on 2008-04-20
Nice guide thought it was someone who needed help

---

### Post by justotech on 2008-04-30
> **MichiganBill said:**
> Thanks gr0kzer0!!!:KS:KS

Your guide worked like a charm!!

I am running Feisty Fawn with Gnome PPP and wvdial. I use Cingular (AT&T) and a Motorola V3.
The following worked for me first time:

Phone # *99***3#
User: [email]WAP@CINGULARGPRS.COM[/email]
password: CINGULAR1

Ubuntu is great.

Thanks again!

I wish I could say the same for the Samsung A707.  It doesn't work at all.  It keeps telling me that I have the wrong number, username and password.

I'm using Hardy and AT&T.

---

### Post by Franko30 on 2008-05-09
Hi There,

many thanks for this howto.

I didn't think it would be that easy to use my Motorola Razr V3i together with my Nexoc-Osiris Laptop (no bluetooth available).

I simply enabled the data mode for USB connections on my phone (as opposed to the standard "data mode"), connected the mobile via USB-cable, went through your guide and found the GPRS access data via Google.

[B]So, for T-Mobile (D1) in Germany the number to dial is

*99#

The username is t-mobile
The password is t-d1
But I don't know if these are just needed by wvdial or are actually used to establish the connection. It just worked.
[/B]

Using sudo wvdial just worked. Thanks! Now I can use my T-Mobile "handy flat" (all inclusive data plan) with my Nokia N810 internet tablet and even my laptop if needed.

Cheers

Frank

---

### Post by seetho on 2008-05-11
> **Franko30 said:**
> 
The username is t-mobile
The password is t-d1
But I don't know if these are just needed by wvdial or are actually used to establish the connection. It just worked.


Normally the username and password is already specified in your connection profile set in your phone.  It's not really necessary to have it in the wvdialrc.  I've tried mine without username and password and it still works.

---

### Post by gangalee on 2008-05-21
[this is the real way to do it now...]("http://ubuntuforums.org/showpost.php?p=5005143&postcount=9")

---

### Post by Franko30 on 2008-05-22
> **gangalee said:**
> [this is the real way to do it now...]("http://ubuntuforums.org/showpost.php?p=5005143&postcount=9")

Hi,

what's that supposed to mean? For me, everything works fine with a Motorola Razr v3i phone via USB doing it the way you described in your first post to this thread.

Cheers

Franko30

---

### Post by Mach1US on 2008-05-27
> **gangalee said:**
> [this is the real way to do it now...]("http://ubuntuforums.org/showpost.php?p=5005143&postcount=9")

If still looking for EVDO and WVDIAL help see this 
[http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

I have been using this since 2006 on many devices

---

### Post by kumarkrishnan on 2008-06-16
Hi,
   I got gprs connected with UBUNTU and I was using it for past one month. Suddenly from past two days it is not working. I tried 1. GPRS settings change. 2. DNS number verified and changed. 3. Wvdial.conf creation from "wvdialconf". 4. Fire fox settings checked. 5. Checked in vista and working there. 6. Ubuntu, reinstalled and followed all the procedure as early.

The main problem is, GPRS is getting connected. But, could not able to browse in fire fox or ping [www.google.com](www.google.com) in terminal.

Please provide me some solution.
With advanced Thanks,

---

### Post by kumarkrishnan on 2008-06-16
Hi,
   Now it is working. After trial and error method I found that one of the control string in wvdial.conf was missing.
KK

---

### Post by manishanchan on 2008-06-16
If we use a mobile phone as a modem call costs will not be  expensive.In  connections  with the mobile phones without the GPRS modem are reliable but the thing is GSM cellphones is connected with the GPRS modem internet connection can be done 
in moblilephones and even through mobilephones can be connected to PC or notebook to browse the internet through GPRS connection..

---

### Post by manishanchan on 2008-06-17
Now many of them are using it for internet connecton and for downloading and transfer the pho message.

---

### Post by dishguy123 on 2008-06-19
I've followed all the above steps, however, after pairing the phone, when I try to bind it with rfcomm0, it gives me this error:

Cannot open /dev/rfcomm0: No such file or directory

How do I resolve that?

I have a sony vaio vgn-t370p laptop that i'm trying to connect to Moto Q.  I have AT&T (former cingular).  

ThanX for all your help!

---

### Post by kumarkrishnan on 2008-06-20
post your wvdial.conf content or refer [http://ubuntuforums.org/showthread.php?t=756777](http://ubuntuforums.org/showthread.php?t=756777) 

This is how I got it.
KK

---

### Post by justotech on 2008-06-21
I'm using Hardy with Gnome and the phone is connected via USB.  Here is what you have to do with a Samsung A707 (Sync) and AT&T in the U.S.  I found it on another forum.  It works perfectly!

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 921600
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+CGDCONT=3,"IP","WAP.CINGULAR"
FlowControl = None
Username = [email]WAP@CINGULARGPRS.COM[/email]
Password = CINGULAR1
Phone = *99***3#
Stupid Mode = 1

---

### Post by seetho on 2008-06-22
> **dishguy123 said:**
> I've followed all the above steps, however, after pairing the phone, when I try to bind it with rfcomm0, it gives me this error:

Cannot open /dev/rfcomm0: No such file or directory


It seems you do not have your /etc/bluetooth/rfcomm.conf config'ed correctly.  Can you post it here if you still have problems.

---

### Post by seetho on 2008-06-22
OK... In an earlier post in this thread I mentioned that I may write about how to get connect via bluetooth, so here it goes.

On Hardy this is even much easier since all the necessary tools are already present.

1. Turn your phone on and bluetooth enabled on it and your pc.

2. use hcitool to scan for you phone bluetooth device address:
```
hcitool scan
```
On my system it return something like:
```
00:12:D1:B6:2B:16 Pari
```
The six hex bytes make up your bt device address and 'Pari' is the name I gave my phone.

3. Make sure you have DUN (dial up networking) service on your phone:
```
sdptool browse 00:12:D1:B6:2B:16
```

4. Now edit your /etc/bluetooth/rfcomm.conf file to get something like this:
```
rfcomm0 {
    bind yes;
    device 00:12:D1:B6:2B:16;
    channel 2;
    comment "My Nokia Phone";
}
```

Please note that channel must be 2 for all since this is allocated to DUN.  If you have more than one phone that you are using then make another section rfcomm1, rfcomm2, .... etc., each with unique bt device address.

5. You may want to edit /etc/bluetooth/hcid.conf to change the default passkey from '1234' to something else.  Leave other settings unchanged.

6. Restart you bluetooth service:
```
sudo /etc/init.d/bluetooth restart
```

Now configure your wvdial as descibed before and you should be good to go.

Good luck.

seetho

---

### Post by rfkrocktk on 2008-11-01
I am having nothing but problems with this.
I'm running a Nokia 6555 on Ubuntu Hardy on ATT wireless. I can get my phone to connect through USB to Ubuntu and I can start the wvdial and it connects, but I get no internet at all. 

Here's what I've got:
/etc/wvdial.conf
[INDENT][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = *99#
ISDN = 0
Password = CINGULAR1
Username = [email]WAP@CINGULAR.COM[/email]
Modem = /dev/ttyACM0
Baud = 460800[/INDENT]

And I run sudo wvdial and I get this:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> PPP negotiation detected.
--> Starting pppd at Sat Nov  1 13:02:27 2008
--> Pid of pppd: 10235
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 10.88.54.230
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.6.6.6
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 172.18.7.170
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 172.18.7.170
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]

And... it doesn't work. I get no internet access. What do I do?

---

### Post by kenjiru on 2008-11-02
I have some problems connecting to Vodafone Live Romania, using a Nokia N95 8G as a modem.

Here is the /etc/wvdial.conf
```

[Dialer Defaults]
Phone = *99#
Username = internet.vodafone.ro
Password = vodafone
Dial Command = ATDT
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT E0
Init4 = AT+CGATT=0
Init5 = AT+CGDCONT=1,"ip","internet.vodafone.ro";
ISDN = 0
Modem Type = USB Modem
Carrier Check = no
Stupid Mode = 1

```

Here is the output from wvdial:
```

root@akira:/home/radu# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT E0
AT E0
OK
--> Sending: AT+CGATT=0
OK
--> Sending: AT+CGDCONT=1,"ip","internet.vodafone.ro";
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Nov  2 18:46:21 2008
--> Pid of pppd: 7799
--> Disconnecting at Sun Nov  2 18:46:21 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

```

What could be the problem here?

---

### Post by GeorgeVita on 2008-11-02
Hi**kenjiru**, searching the internet found

[B]VODAFONE (Romania)
APN:internet.vodafone.ro
Username:internet.vodafone.ro
Password:internet
[/B]

[http://www.modmyi.com/wiki/index.php?title=Carrier_APN_Settings#VODAFONE_.28Romania.29](http://www.modmyi.com/wiki/index.php?title=Carrier_APN_Settings#VODAFONE_.28Romania.29)

They have a different **password=internet**

EDIT: Also why are you using the following lines in your wvdial.conf?
[B]Init3 = AT E0
Init4 = AT+CGATT=0
[/B]
My opinion is to remove them.

---

### Post by seetho on 2008-11-05
rfkrocktk:

It seems you are connected fine to your provider.  You can see the IP numbers returned and the DNS.  Are you sure you are not getting internet connection?

---

### Post by seetho on 2008-11-05
kenjiru:

Your pppd exit code suggests this:
 2      An error was detected in processing the options given,  such  as
              two mutually exclusive options being used.


GeorgeVita is correct, remove the Init3 and Init4 strings.

Also I have Stupid Mode = on (instead of Stupid Mode = 1).  I'm not sure if this makes a difference. Try it.

---

### Post by rfkrocktk on 2008-11-05
@seetho: I'm pretty sure I'm not getting internet. 
I open up terminal, dial in wvdial, wait for it to complete... and I've got nothing. I'm connected to a WLAN network right now, and when I try using wvdial with my phone, I have no internet at all, but when I've closed wvdial I have internet just fine.

---

### Post by seetho on 2008-11-12
> **rfkrocktk said:**
> @seetho: I'm pretty sure I'm not getting internet. 
I open up terminal, dial in wvdial, wait for it to complete... and I've got nothing. I'm connected to a WLAN network right now, and when I try using wvdial with my phone, I have no internet at all, but when I've closed wvdial I have internet just fine.

Leave the terminal window you used to dial open (you have to to remain connected).  Open another terminal window and try pinging the DNSes return by pppd.  If ping is sucessful then you are truely connected and problem lies somewhere else.

---

### Post by jp_frnds on 2008-12-24
hi..
i hope that u can solve my problem...

i m using NOKIA 6020 and i use it to access internet via infrared via KINGSUN KS-959 irda dongle.
but i m unable access even my cellphone in ubuntu 8.10 intrepid.

when i connected the dongle, ubuntu recognized it.
but not my cellphone. :(
plz tell me why? and how can i connect it..

Any help will be appreciated..

Thank You...

---

### Post by majidsaba on 2011-03-18
sudo : wvdialconf : not found

---

### Post by seetho on 2011-03-21
> **majidsaba said:**
> sudo : wvdialconf : not found

Could you be more specific about the problem you have.  It'd easier for anyone to help you out here.

---

