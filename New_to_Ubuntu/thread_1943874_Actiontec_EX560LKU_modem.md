---
title: "Actiontec EX560LKU modem"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by merle330 on 2012-03-20
Can someone help me to get Ubuntu / gnome dialer to recognize my Actiontec EX560LKU modem? 
I recently upgraded to Lucid and the internal modem with a Linuxant driver is no longer working. Because of poor support and the frequent problem with their expensive drivers not working after upgrades I chose to follow recommedations and get an external modem hoping it would simply work. It has not been detected.
I am using usb cable for connecting the modem to my Dell. Do I need to use a serial cable or what can I do?
There's probably a simple solution but I have spent hours searching Ubuntu forums without success.
Is there any help?
thanks,
 merle

---

### Post by lkraemer on 2012-03-20
Merle,
Power up the modem, and connect it to your USB port.  Open a Terminal Window (Console)
and copy & paste the following commands:
```

lsusb
lsmod
ndiswrapper -l

```
Post the output of these commands.

You should see something similar to these messages.
> 
larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID **058f:9720** Alcor Micro Corp. USB-Serial Adapter
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Now, cut and paste the following command in your Linux Terminal Window, substituting your device information:
```

lsusb -v -d **058f:9720**

```
Post your information.

> 
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 2 Communications
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x058f Alcor Micro Corp.
idProduct 0x9720 USB-Serial Adapter
bcdDevice 0.00
.
.
.
.


You need to add yourself to DIP group.  
Refer to posting #2 at [http://ubuntuforums.org/showthread.php?t=1943624](http://ubuntuforums.org/showthread.php?t=1943624)


You need to download wvdial, and the following dependencies for whatever
version you have installed......and get the 32 or 64 bit debs to match
your installed version.......then install via Synaptics...............
realizing you don't have Ethernet or Wifi.....available yet on Ubuntu and
are trying your best to get wvdial installed and configured to get Dialup Working......

wvdial & dependencies: (ALL are .deb files)
```

libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

```
Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP or Ubuntu, then copy the *.deb files to USB Flash Drive, & then to Ubuntu
subdirectory /var/cache/apt/archives & then install using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
**OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES**
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install wvdial from the CDR.


First, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window (Console):
```

sudo pppconfig

```
You will need your [B]userlogin, password, ISP provider information, and
pap or chap information for the connectio[/B]n. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

The pap-secrets at /etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```
**ASSUME:**
your loging name is **GeraldJones**
your password is **MyPassWord**

Your last section of the pap-secrets file should be:
```

# OUTBOUND connections

# Here you should add your userid & password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"**GeraldJones**" provider "**MyPassWord**"

```


Now, since you are using USB versus a typical Serial COMM Port you may need to create
a symbolic link, to link the USB port to the serial port so the software will work.

**A bit of information about the Serial Ports first!**
[B]
SERIAL PORT NAMES:[/B]
If you are wondering how the ttyUSB0/(ttyACM0) is related to a comm port or how to set it up?

Dos/Windows use the COM name while the messages from the serial driver use ttyS00, ttyS01, etc.
Older serial drivers (2001 ?) used just tty00, tty01, etc.

The tables below shows some examples of serial device names. The IO addresses are the default addresses
for the old ISA bus (not for the newer PCI and USB buses).

dos common IO USB-BUS ( ACM => acm modem )
name name major minor address || common name common name
COM1 /dev/ttyS0 4, 64; 3F8 || /dev/ttyUSB0 | /dev/ttyACM0
COM2 /dev/ttyS1 4, 65; 2F8 || /dev/ttyUSB1 | /dev/ttyACM1
COM3 /dev/ttyS2 4, 66; 3E8 || /dev/ttyUSB2 | /dev/ttyACM2
COM4 /dev/ttyS3 4, 67; 2E8 || /dev/ttyUSB3 | /dev/ttyACM3
- /dev/ttyS4 4, 68; various


**SYMBOLIC LINKING the COMM PORT:**
To locate the possible used COMM PORTS in Ubuntu, cut and paste the following command:
```

ls -l /dev/ttyS*

```
Notice that ttyS0 through ttyS3 are defined as shown, along with the symbolic link
we will create in a minute.
> 
crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3
lrwxrwxrwx 1 root root 12 2009-11-27 18:24 /dev/ttyS5 -> /dev/ttyACM0

So, I picked /dev/ttyS5 to use, and linked this to COMM PORT 6 with the following command:
```

ln -s /dev/ttyACM0 /dev/ttyS5

```
Your Serial Port choice will depend on what you select.  If you chose one that
exists, for example /dev/ttyS3, you will need to remove it with the following
command:
```

sudo rm /dev/ttyS3

```
then, build your symbolic link.......


ADDITIONAL Extra Misc Info:
[http://wiki.debian.org/Modem/3G/Vodafone](http://wiki.debian.org/Modem/3G/Vodafone)

Does the /dev/ttyS0 device exist? If not, try 'ln -s /dev/ttyUSB0 /dev/ttyS0'

Do you have read access to /dev/ttyUSB0? Depending on the config of your box, it may only be accessible by root.
```

id
ls -l /dev/ttyUSB0

```


In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains something like this, but yours will be slightly different:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

wvdial.conf info:
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

PPP HOWTO:
[http://tldp.org/HOWTO/PPP-HOWTO/index.html](http://tldp.org/HOWTO/PPP-HOWTO/index.html)

PAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1034.html](http://tldp.org/HOWTO/PPP-HOWTO/x1034.html)

CHAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1053.html](http://tldp.org/HOWTO/PPP-HOWTO/x1053.html)

Setting up PPP Manually
[http://tldp.org/HOWTO/PPP-HOWTO/manual.html](http://tldp.org/HOWTO/PPP-HOWTO/manual.html)


Finally, when wvdial is working you can configure/set up Gnome-PPP.

Just go slow and post with any questions..............

lk

---

### Post by merle330 on 2012-03-20
thank you for your quick response. This will take me some time. I had a bit of spare time this pm and attempted a few times to save your info on a flashdrive and open it in Ubuntu but .......unsuccessful. I intend to follow your suggestions but as you say, it will have to be slow! 
merle

---

### Post by merle330 on 2012-03-20
Attached is the output from the first set of commands. I tried to copy and paste but evidently in Puppy [my crutch] a pdf is read only. Hopefully the attachment will come through.
merle

---

### Post by merle330 on 2012-03-21
The wvdial and dependencies seem to be installed

The modem is not on the list with the lsusb output. 
Dead modem?
Use serial cable?
Not sure what to do next.
merle

---

### Post by lkraemer on 2012-03-21
Merle,
You are correct, as the command lsusb didn't show any information about the modem.
First thing to do is make sure if the modem has a power adapter, and uses it (IF REQUIRED)
to power the modem, then plug it in.  Then power up the computer, and after it's booted, and
you are logged in, plug in the USB cable in a different USB Port...directly not through a USB Hub.

Then do these commands again:
```

lsusb
dmesg | tail

```
and post the output, as you did previously.

If that doesn't work you will be forced to use a Serial cable.  That isn't a problem,
except you might not have one easily available.  You will need to know if your system
requires a straight through cable or a cable with crossed conductors and the appropriate
Male/Female ends.  You must use an Volt/OHM meter to locate the TX Pins Signals of the
Computer(Typical DB9-Pin #3) and the Modem(Typical DB9-Pin#2) -- (DTE to DCE). Notice that
the DCE's TX pin is Pin #2, and is marked as RX.........

I've included some photo's of the wiring that you may need.  You will have to locate
the DB25 or DB9 connectors on both ends and test from GND (really Signal Common) to
the TX pins of the Computer and also the Modem.  Those pins will have Negative Voltage's
on them.  From there you just need the appropriate cable to connect TX to RX for each device.
I think you will follow and understand what I am stating, as you look at the BMP pictures.

Once you have the Serial Cable you're ready to continue...with the command:
```

sudo pppconfig

```
Following the above information.....

Then skip to:
```

sudo wvdialconf /etc/wvdial.conf

```
and post the output.  You're almost there.


lk

---

### Post by merle330 on 2012-03-21
Ok - but first a question. Where on my keyboard do I find the center character
in the command below??  merle

dmesg | tail

---

### Post by lkraemer on 2012-03-21
Merle,
Mine is a US Keyboard and it is located on the key with the \ 
as a SHIFTED character.  It's right above the ENTER Key on my keyboard.


lk

---

### Post by merle330 on 2012-03-21
Never mind the last post. Copy / paste works in Ubuntu:KS
Modem powered on.
Usb into another port.
Attached is the output
thanks,
merle

ps- I do have a USB / serial adapter cable although that didn't seem to work either.

---

### Post by lkraemer on 2012-03-21
Merle,
The USB Modem isn't detected.  No problem.  Just proceed but use a Serial Cable instead of using the USB Cable.  More than likely it is a straight through cable, but it's easy to verify with your meter.  Assuming it's a 9 Pin connector on both ends.

More than likely your system has the default 4 Serial Ports.  Verify with:
```

ls -alt /dev/ttyS*

```
You should see smething like:
> 
larry@debian:~$ ls -alt /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 Mar 21 09:04 /dev/ttyS0
crw-rw---- 1 root dialout 4, 66 Mar 21 09:04 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 Mar 21 09:04 /dev/ttyS3
crw-rw---- 1 root dialout 4, 65 Mar 21 09:04 /dev/ttyS1
larry@debian:~$

which are COM1 thru COM4 for wvdial.

I extracted the Command set from the ISO posted on their site.
It is attached.

lk

---

### Post by merle330 on 2012-03-21
Ok- this will take some time to check out the serial cable possibilities. I do not have a meter but may be able to borrow one or something. Of course I would need to purchase a cable also, so it'll be awhile but hopefully I can confirm sometime whether it worked or no. Thank you for your help!
merle

---

### Post by merle330 on 2012-04-02
After all this time I have **not **had the time [other priorities] to find a test meter to confirm what sort of serial cable I need, however a friend shared a serial cable with me, presumably a straight through. Is there a way I can check to see if this works without using a meter since I don't have one [tester] in my possession? 
wondering,
Merle

---

### Post by lkraemer on 2012-04-02
Merle,
Absolutely!  Plug the Serial cable into the Modem and your Computer.
Turn on the Modem's power.

Open a Terminal Window (Console) and type or copy & paste:
```

sudo wvdialconf /etc/wvdial.conf

```
Then look at the response of wvdial's search & configuration of the modem.
The wvdial configuration file is at /etc/wvdial.conf.  You can edit that
with nano or gedit.

If your Modem isn't found, then the cable is incorrect.

lk

---

### Post by merle330 on 2012-04-02
Must be the wrong one. 
Here's the output.
                         [SIZE=2]merle[/SIZE]

[SIZE=2]merle@merle-desktop:~$ sudo wvdialconf /etc/wvdial.conf[/SIZE]
    [SIZE=2]Editing `/etc/wvdial.conf'.[/SIZE]
        [SIZE=2]Scanning your serial ports for a modem.[/SIZE]
        [SIZE=2]ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud[/SIZE]
    [SIZE=2]ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud[/SIZE]
    [SIZE=2]ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.[/SIZE]
    [SIZE=2]Modem Port Scan<*1>: S1   S2   S3   [/SIZE]
            [SIZE=2]Sorry, no modem was detected!  Is it in use by another program?[/SIZE]
    [SIZE=2]Did you configure it properly with setserial?[/SIZE]
        [SIZE=2]Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)[/SIZE]
    [SIZE=2]merle@merle-desktop:~$ [/SIZE]

---

### Post by merle330 on 2012-04-24
ok.......... I finally have a voltage tester, however using it is a bit of a stretch for me. Wasn't expecting to get into this sort of thing. I've checked a bit but haven't learned much. I assume black wire [tester] goes onto ground pin to check voltage on other pins but how do I know which is the ground? i do have the photos which shows either pin # 5 or 7 as ground  but I'm not sure how the pins are numbered. Do I start at top left and count both rows?
Thanks,
merle

QUOTE=lkraemer;11782401]Merle,

If that doesn't work you will be forced to use a Serial cable.  That isn't a problem,
except you might not have one easily available.  You will need to know if your system
requires a straight through cable or a cable with crossed conductors and the appropriate
Male/Female ends.  You must use an Volt/OHM meter to locate the TX Pins Signals of the
Computer(Typical DB9-Pin #3) and the Modem(Typical DB9-Pin#2) -- (DTE to DCE). Notice that
the DCE's TX pin is Pin #2, and is marked as RX.........

I've included some photo's of the wiring that you may need.  You will have to locate
the DB25 or DB9 connectors on both ends and test from GND (really Signal Common) to
the TX pins of the Computer and also the Modem.  Those pins will have Negative Voltage's
on them.  From there you just need the appropriate cable to connect TX to RX for each device.
I think you will follow and understand what I am stating, as you look at the BMP pictures.

Once you have the Serial Cable you're ready to continue...with the command:
```

sudo pppconfig

```Following the above information.....

Then skip to:
```

sudo wvdialconf /etc/wvdial.conf

```and post the output.  You're almost there.


lk[/QUOTE]

---

### Post by lkraemer on 2012-04-26
Merle,
All DB9 & DB25 Connectors have the Pins numbered on the Front or Back of the Connector.  You'll likely need a Magnifying Glass to read them.

To check your cable for a Crosswired Modem Cable do the following.  With your Black Meter Lead touching a small Diameter Paper clip inserted into Pin 2 of one DB9 (or DB25) connector.....Then use the Red Meter Lead to touch a small Diameter Paper Clip inserted into Pin 3 of DB9 (or DB25) connector.  The meter should be set for OHMS.  You should get ~ZERO OHMS
if there is continuity.  That tells you if the cable is cross wired. ie. Pin 2 to Pin 3 on both ends of the cable.

Pinout of DB9 Connector on a Computer:
	Pin Number	Signal Description		Direction
	Pin 1		Data Carrier Detect (DCD)	<-------
	Pin 2		Receive Data (RX)		<-------
	Pin 3		Transmit Data (TX)		------->
	Pin 4		Data Terminal Ready (DTR)	------->
	Pin 5		Signal Ground			<------>
	Pin 6		Data Set Ready (DSR)		<-------
	Pin 7		Request to Send (RTS)		------->
	Pin 8		Clear to Send (CTS)		<-------
	Pin 9		Ring Indicator (RI)		<-------

Pinout of DB25 Connector on a Computer:
        Pin 1		Chassis Ground
        Pin 2		Transmit Data (TX)		------->
        Pin 3		Receive Data (RX)		<--------
        Pin 4		Request to Send (RTS)		------->
        Pin 5		Clear to Send (CTS)		<-------
        Pin 6		Data Set Ready (DSR)		<-------
        Pin 7		Signal Ground			<------>
        Pin 8		Data Carrier Detect (DCD)	<-------
        Pin 20		Data Terminal Ready (DTR)	------->
        Pin 22		Ring Indicator (RI)		<-------

If you have continuity from Pin 2 to Pin 2, then it's a wrong cable.

REF:
[http://pinouts.ru/SerialPorts/Serial9_pinout.shtml](http://pinouts.ru/SerialPorts/Serial9_pinout.shtml)
[http://pinouts.ru/connector/9_pin_D-SUB_male_connector.shtml](http://pinouts.ru/connector/9_pin_D-SUB_male_connector.shtml)

[http://pinouts.ru/connector/9_pin_D-SUB_female_connector.shtml](http://pinouts.ru/connector/9_pin_D-SUB_female_connector.shtml)


lk

---

### Post by merle330 on 2012-04-27
You're right! tiny numbers though. I checked the cable and there's continuity between between pin # 2 male and # 2 on the female end so I guess it's a straight through cable. Later today I hope to check the computer and modem ends.
Thanks,
merle

---

### Post by merle330 on 2012-04-27
Here's what I found on the modem and on the computer.
Computer: pin # 3,4,& 7 show neg. voltage [-11.]
modem: # 1,2,6,8,9 give a voltage reading [3.5] 
Is this meaningful info? Doesn't seem to identify tx and rx pins or does it?
merle

---

### Post by lkraemer on 2012-04-28
Merle,
Yes, that is exactly what I would expect to see on the Computer.

Pinout of DB9 Connector on a Computer:
Pin Number Signal Description Direction
Pin 1 Data Carrier Detect (DCD) <-------
Pin 2 Receive Data (RX) <-------
Pin 3 Transmit Data (TX) ------->
Pin 4 Data Terminal Ready (DTR) ------->
Pin 5 Signal Ground <------>
Pin 6 Data Set Ready (DSR) <-------
Pin 7 Request to Send (RTS) ------->
Pin 8 Clear to Send (CTS) <-------
Pin 9 Ring Indicator (RI) <-------

> 
Computer: pin # 3,4,& 7 show neg. voltage [-11.]


Pin #3 is Transmit and is a Negative Voltage,
Pins #4 is DTR, & Pin #7 is RTS, and could be Negative or Positive depending on the Port's State.  If DTR and/or RTS is "ASSERTED" it will be a Positive Voltage.

> 
modem: # 1,2,6,8,9 give a voltage reading [3.5] 


As far as the Modem those readings seem strange..............

The US Robotics shows the following information for the Pinout:

DB-25 DB-9 Circuit  Function
2     3    BA       Transmitted Data
3     2    BB       Received Data
4     7    CA       Request To Send
5     8    CB       Clear To Send
6     6    CC       Data Set Ready
7     5    AB       Signal Ground
8     1    CF       Carrier Detect
12    ---  SCF      Speed Indicate
20    4    CD       Data Terminal Ready
22    9    CE       Ring Indicate

lk

---

### Post by merle330 on 2012-04-28
I checked again just to be sure. 
# 5 appears to be the ground and 1,2,6,8,9 all have voltage. 
Any recommends for a cable or a crossover adapter for the cable? [don't know whats available]
Or is it time to try another modem? 
Is there any dial-up modem that will be recognized with a serial cable or maybe with USB?
merle

---

### Post by lkraemer on 2012-04-29
Merle,
I use a Serial Cable like this one:
[http://www.rogersystems.com/db9f-db25m-6.html](http://www.rogersystems.com/db9f-db25m-6.html)

It's going to depend on what Serial Connection you have on the Modem and also on the Computer.

I've sent you a PM.

Larry

---

### Post by EzioAuditore on 2012-04-29
Have you looked here?
[www.murga-linux.com/puppy/viewtopic.php?p=160748](www.murga-linux.com/puppy/viewtopic.php?p=160748)

---

### Post by merle330 on 2012-04-30
Thanks for those replies,
EzioAuditore: I don't think that thread will help me a lot since I'm trying to get set  up in Ububtu. I am currently booting with Puppy when I need to go online since it recognizes my PCI modem. 
Larry - I'll check out the PM. Thanks for your help as well.
merle

---

### Post by lkraemer on 2012-05-02
Merle,
The Modem's switches are preset correctly.  I sent a PM with my wvdial.conf
contents.  Your Modem, Login, and Password will be different.  Just use my
/etc/wvdial.conf as a guide.

Be sure to run the wvdial configuration to let wvdial find the modem and then have a look at the wvdial.conf file.  

When you connect wth wvdial, you will keep that terminal window open, and just minimize it, and go to Firefox (your Browser).  You should be ONLINE.

When you decide to exit or quit surfing, you should close the browser, and then go to the terminal window where wvdial is running and type CNTL C
to terminate wvdial.  Once wvdial is working setup Gnome-PPP.  (You may have to install it via a modem connection.)

Somewhere I have posted my Gnome-PPP PNG files on the Ubuntu forum.  I'll have to search for them.

Your Modem (Device) will likely be different because I use a USB to Serial Cable for my US Robotics Hardware Serial Modem.

[http://ubuntuforums.org/showthread.php?t=1589966&highlight=Gnome-PPP](http://ubuntuforums.org/showthread.php?t=1589966&highlight=Gnome-PPP)
Posting #4


lk

---

### Post by merle330 on 2012-05-03
Larry,
Wow! That USR modem did come today. Setup was very simple since I already had Gnome PPP installed. I powered the modem and Gnome detected it quickly. Since I already had my Juno information in the dialer it was as simple as connecting to the phone line. Bingo! It works. The only problem now is firefox isn't allowing me to go online maybe firewall or something [I was able to get my email] but that will have to wait for another day. Thank you very much for your help! 
merle

---

### Post by lkraemer on 2012-05-04
Merle,
Open Firefox, then Left Click on FILE and make sure WORK OFFLINE is NOT
Checked.

If you can get your email, you should be able to Browse with Firefox.

Larry.

---

### Post by merle330 on 2012-05-04
Larry,
I'm good there. This trouble started when I upgraded to 10.4 from C E Ubuntu. Sometime ago [before I tried to set-up with an external modem] I had the computer at a friend's house to check out a few things. He has hi-speed internet and wasn't able to use Firefox either [with my computer] but was able to do upgrades and etc online. I suspect it may have to do with the Dans Guardian filter that comes with CE although I'm not sure. I ended up uninstalling Firefox this morning so I'll need to reinstall that. Hopefully I'll be able to do that. This morning when I was connected I tried installing something but the download was always cancelled with a message about the site not being authenticated?? Again maybe filter interference? I'll see what happens when I try to reinstall Firefox.
merle

---

### Post by merle330 on 2012-05-04
Finally - able to go online again.
I made a few changes in the network proxy preferences and was able to download a new browser. No apparent problem at this point. 

Larry - kudos to you for your assistance. This has been a bit of stress for awhile but a simple fix once I had the right [US Robotics] modem. 
thank you very much,
merle

---

### Post by lkraemer on 2012-05-04
Merle,
You are Welcome!

Larry

---

