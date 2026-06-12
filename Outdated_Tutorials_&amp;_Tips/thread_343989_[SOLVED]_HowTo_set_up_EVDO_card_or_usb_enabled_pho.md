---
title: "[SOLVED] HowTo set up EVDO card or usb enabled phone(CDMA)"
date: 2007-01-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Mach1US on 2007-01-22
[COLOR="Blue"][SIZE="4"]If your card is not configured automatically you can use one of the following howto's 
This HowTo has been revised and now includes three methods, first one using new Airprime driver, second(longer) using USBserial driver and third for [/COLOR][COLOR="Red"] USB760 users.[/SIZE][/COLOR]

If first one is not working for you try the second one , from my test there is no speed difference between both drivers .

**_[COLOR="SeaGreen"]First method using Airprime driver[/COLOR]_**

1 -Insert card

2 -in terminal type:
```
dmesg
```
If you see something like this:
```
[  171.945756] airprime 6-1:1.0: airprime converter detected
[  171.945890] usb 6-1: airprime converter now attached to ttyUSB0
[  171.945933] usb 6-1: airprime converter now attached to ttyUSB1
[  171.945983] usb 6-1: airprime converter now attached to ttyUSB2
[  171.945990] airprime 6-1:1.1: airprime converter detected
[  171.946034] usb 6-1: airprime converter now attached to ttyUSB3
[  171.946105] usb 6-1: airprime converter now attached to ttyUSB4
[  171.946149] usb 6-1: airprime converter now attached to ttyUSB5
[  171.946155] airprime 6-1:1.2: airprime converter detected
[  171.946200] usb 6-1: airprime converter now attached to ttyUSB6
[  171.946242] usb 6-1: airprime converter now attached to ttyUSB7
[  171.946284] usb 6-1: airprime converter now attached to ttyUSB8

```
These are your device identifiers for your EVDO card.
This means that your device has been installed with Airprime driver

3 -open new terminal window and type:
```
sudo wvdialconf
gksudo gedit /etc/wvdial.conf
```
 ```
      replace line:
Init1 = ATZ 
 
        with this:
Init1 = ATX0

        and add this :
Stupid Mode = on
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```
In the line " Username = " put your phone number followed by your providers domain , for Verizon it is :
your phone number(including area code) and domain(for verizon it is [COLOR="Blue"]**@vzw3g.com**[/COLOR]) ,
in this format: [COLOR="Blue"]**Username = 9178889999@vzw3g .com**[/COLOR]
for sprint it will be [email]9178889999@sprintpcs.com[/email], for At&t / Cingular [email]WAP@CINGULARGPRS.COM[/email] ,for Alltel [email]9178889999@alltel.net[/email] and so on , further post have config's posted for other providers.
In line "[COLOR="Blue"] password =[/COLOR] " in case of **Verizon** put : " [COLOR="Blue"]vzw[/COLOR] " for Cingular : " cingular1 " , for Alltel " alltel "and so on , make sure to check with your provider as username and/or password may differ for other regions and countries .

4.In the line "[COLOR="Blue"]**Phone =**[/COLOR]" your ISP's data phone number , most of the time it will be **[COLOR="RoyalBlue"]#777[/COLOR]** 

5.Now click save and open yet another terminal widow type: ```
**wvdial**
```
With some systems this window needs to stay open(although can be minimized)during usage of the card.

6.Open browser , in the tab [COLOR="Blue"]**_File_**[/COLOR] [COLOR="Red"]**[SIZE="4"]_UN_check[/SIZE]**[/COLOR][COLOR="Blue"] **_Work Offline_**[/COLOR] and try any site (like google.com for an example) .


[COLOR="DarkRed"]**For graphical interface setup just go to package manager and check box to install gnome-ppp .**[/COLOR]

[COLOR="Blue"][B] [SIZE="5"]If this howto has worked for your device please post it to this forum so your adapter can be listed  as one of compatible devices for others considering a purchase .[/SIZE] 
Happy surfing[/B][/COLOR].8)





 
[COLOR="SeaGreen"]**---------------------------------------------Second method useing USBserial driver.------------------------------------------**[/COLOR]

**[COLOR="Red"]This section has been created to fix issues created in Gutsy and applies to [B][SIZE="5"]Gutsy[/SIZE]** and **[SIZE="5"]Hardy[/SIZE]** and all future releases only [/COLOR][/B]
All upgrades directly from Feisty seem to work fine unless the Evdo card / modem is upgraded then it automatically plugs default Gutsy driver.
In case this happens or you just installed fresh 7.10 you can execute following fix.


[COLOR="Red"]**[SIZE="4"]                            !!! Since Gutsy USB handling has changed  !!![/SIZE] **[/COLOR]
 So absolutely make sure to re enable[COLOR="Red"]** /proc/bus/usb/devices**[/COLOR] by executing following  :

**With your evdo card removed**  type  following  in the terminal :

**1.**
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

**2.**
Now remove " # " symbols from the front of following lines of code :
```
        #mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb
```

**3.**
Now to  stop new Airprime driver from loading execute following in the terminal:
```
sudo gedit /etc/modprobe.d/blacklist

```

**4.**
Now insert following at the bottom :
```
#Block Airprime driver to force kernel to use usbserial
blacklist airprime
```

**5.**
Now you will need to reboot .

Upon successful completion of previous 5 steps you shoud have all neccesary directories created as well be able to obtain correct tty??? identifier for your device.
 
[COLOR="Red"]**Again!**[/COLOR]Above section section is a recent addition to fix problems with gutsy and hardy, if you are running feisty, start from here.
From here you should be able to continue with this how to as above fix will enable single device identifier which can be used for setup with wvdial , KPPP dialer or Gnome PPP .
If you find more streamlined way to do it or other posts that may help us feel free to let us know by posting it in this thread .

I always suggest to back up any files you will be editing in case you will need to retrace your steps  .
Devices i have used are Verizozn Motorola v3 EVDO enabled phone connected via USB cable as well  as number  of other EVDO cards like PC5750 .

Make sure your device is activated by service provider and if possible test on other OS to witch you may have software and drivers.

Open terminal window and type:
```
 sudo -i 
```enter your password.
Now all commands typed in this window will be executed with root privileges .
In terminal type:
```
apt-get update
apt-get upgrade
apt-get install wvdial 
```Before you insert the Card or connect USB cable (for Build-In minicards see bottom of this post)  open terminal window and type :
```
 cat /proc/bus/usb/devices > devices  
```Insert your data card or plug in USB cable and wait for a few seconds before continuing.
In terminal type:
```
dmesg
```You will get output with some device info like this :
```
[17186692.460000] usb 3-1: configuration #1 chosen from 2 choices
[17186692.460000] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[17186708.176000] usb 3-1: USB disconnect, address 4
[17186714.588000] usb 3-1: new full speed USB device using uhci_hcd and address 
```At the end of this output you will find your device witch will be represented like this:  ttyACM0 or ttyUSB  or similar , make note of it you will need it later.
Now type in terminal:
```
   diff /proc/bus/usb/devices devices | grep Vendor 
```Output will be similar to:
```
 < P: Vendor=_1234_ ProdID=_5678_ Rev= 0.00  
```Make note of lines:   _Vendor=[U]1234_ [/U] , _ProdID=[U]5678_ 
[/U]
Now in teminal type following code Replacing values _*1234*_ and _*5678*_ with your own output from previously noted lines ::
```
  modprobe usbserial vendor=0x_1234_ product=0x_5678_  
```Now you will edit wvdial config file by first typing in terminal :
```
  sudo gedit /etc/wvdial.conf   
```In new opened window replace all text with following :
```
[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = ??????????@vzw3g.com
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```In the line "Modem =" replace ttyACM0 with value you noted from output of " dmesg " command.
In the line " Username = " put your phone number  followed by your providers domain , for Verizon it is area code , your phone number and domain ,
in this format: [COLOR="Red"]917**888**9999@vzw3g.com[/COLOR]
for sprint it will be [COLOR="Red"]917**888**9999@sprintpcs.com[/COLOR] , for At&t / Cingular [COLOR="Red"]WAP@CINGULARGPRS.COM [/COLOR],for Alltel [COLOR="Red"]917**888**9999@alltel.net[/COLOR] and so on , further post have config's posted for other providers.
In line " password = "  in case of Verizon put : " vzw " for Cingular : " cingular1 " and so on , make sure to check with your provider as [COLOR="Sienna"]username and/or password[/COLOR] may differ for other regions and countries .

If you are Cingular/AT&T subscriber and after completing whole guide  you have problem with dropping connection you have to add another int line in wvdial script which is posted here [http://ubuntuforums.org/showthread.php?t=343989&page=3](http://ubuntuforums.org/showthread.php?t=343989&page=3)
If you need any specific info regarding your domain or password please contact your cellular provider.
The last thing you need to configure is wvdial line checking , by disabling LCP echo checking witch is not supported by most of providers.
Open terminal and type:
```
sudo gedit /etc/ppp/peers/wvdial 
```And insert aditionally those lines:
```
lcp-echo-failure 0
lcp-echo-interval 0
```Make sure your ethernet jack is unplugged and wifi radio switch is turned off.
Now you can start connection by typing in terminal :
```
wvdial
```

In case the kernel does not support one of your new devices (like Moto Q) you will need to to patch the kernel in order to recognize the new hardware.
This post will guide you through additional steps you'll need to take.
[http://ubuntuforums.org/showpost.php?p=3968282&postcount=1](http://ubuntuforums.org/showpost.php?p=3968282&postcount=1)
Additonal read on paching kernel modules:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
[https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)
[http://glasnost.beeznest.org/articles/340](http://glasnost.beeznest.org/articles/340)

If you are having problems installing using this method or if you have**[COLOR="Blue"] Built-In WAN Card[/COLOR]** see this post:
[http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/](http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/)

Another thing i have been suggested is automating the connection process.
To do so in Gnome go to :
```
System > Preferences > Sessions
 next, click on the tab labeled, "Startup Programs"
 then click the "Add" button. 
In the Startup Command field, enter "wvdial" and then click "OK". 
Then restart your system.
```Now make sure your EVDO card is inserted before you boot it up , it will initiate the connection process automatically in the background connecting you to internet the second you log in.

**_[COLOR="SeaGreen"] Third for Verizon USB760 users [/COLOR]_**

```

sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
find the line that contains **[COLOR="Red"] Novatel_Mass_Storage [/COLOR]** and append the following to it: 
```
RUN+="/usr/bin/eject %k"
```
save and close
```

sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```
Add this in the USB devices section
```
<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match> 
```
Save and close

Now plug in your card and make sure it didn't mount anything (Places -> Computer USB Drive shouldn't be mounted)
Now left click the network applet and select 'Auto mobile broadband (CDMA) connection'
Let it connect.
If it doesn't make sure to go into VZAccessManager on a Windows machine and activate your USB 760.

I like to thanks to all those that have helped me through forums,web pages  and personal support to create this how to .

Additional reads on the subject:
[http://ubuntuforums.org/archive/index.php/t-366229.html](http://ubuntuforums.org/archive/index.php/t-366229.html)
[http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/)
[http://doc.gwos.org/index.php/EV-DO](http://doc.gwos.org/index.php/EV-DO)

[COLOR="Blue"][B] [SIZE="5"]If this howto has worked for your device please post it to this forum so your adapter can be listed  as one of compatible devices for others considering a purchase .[/SIZE]
Additionally please let me know about any  fixes that would streamline this process. 
Happy surfing[/B][/COLOR].8)**[B][B]**[/B][/B]

---

### Post by autoexec on 2007-01-23
hi, i used this guide just then
initially everything worked except actually having firefox go to a page
but then i disabled the ethernet and that seemed to fix it
so yeah, no real problems, thanks for this.
(using telstra bigpond evdo to write this in ubuntu now :) )

is there some way that i can get it to connect without having to start the connection from the terminal? like have it in the backround? (its not a timed connection for me)

---

### Post by Mach1US on 2007-01-23
> **autoexec said:**
> hi, i used this guide just then
initially everything worked except actually having firefox go to a page
but then i disabled the ethernet and that seemed to fix it
so yeah, no real problems, thanks for this.
(using telstra bigpond evdo to write this in ubuntu now :) )

is there some way that i can get it to connect without having to start the connection from the terminal? like have it in the backround? (its not a timed connection for me)

Yes you can run it in the background by having it started automatically at the login.
To do so in Gnome go  to System > Preferences > Sessions  next, click on the tab labeled, "Startup Programs" and then click the "Add" button. In the Startup Command field, enter "wvdial" and then click "OK" and restart.
Now make sure your EVDO card is inserted before you boot it up , it will initiate the connection process automatically in the background connecting you to internet the second you log in.
I will be adding  this to this HowTo
Have fun.:D

---

### Post by truckboy on 2007-01-26
A great big thank you!!! This tutor got me up and running whereas I had tried some other tutors that left me stratching my head. This should be a sticky for sprint users of the evdo s620 card. :guitar:

---

### Post by raffij on 2007-03-23
Hi, I am able to get as far as able to talk to the modem using the terminal or gtkterm. (i.e. send AT commands).  However when I send ATDT commands I'm getting no carrier returned.

The card was activiated and used in Windows prior.

---

### Post by Mach1US on 2007-04-03
i have never used any other connection managers simply because wvdial is really easy to operate and just works.
Try Dmesg command to get exact info on serial connection setting  of your device , which can change by one digit simply by quick removal and insertion . 
Finally try to set it up using this how to and just compare /etc/***.conf  files on both applications, this way you should easily identify what exactly causing the problem .;)

---

### Post by rickdog on 2007-05-01
I'd just like to say that I used the steps posted and they worked for me. I'm using a Pantech PX500 with Sprint, on a Toshiba A45-S150 with Feisty.

The speeds I'm getting aren't blazing (430kbps down, 230kbps up) but they're not bad. I've heard that there is some fine tuning you can do to improve this. Something about patches and buffers, I'm not sure. If anyone knows of this let me know too please.

---

### Post by ebozzz on 2007-05-13
There's a great guide on the Sprint site that is actually based on Ubuntu. 

[http://www4.sprint.com/pcsbusiness/support/downloads/index.jsp?internalId=downloads](http://www4.sprint.com/pcsbusiness/support/downloads/index.jsp?internalId=downloads)

Select Linux and get the PDF file.

---

### Post by Mach1US on 2007-05-14
> **rickdog said:**
> I'd just like to say that I used the steps posted and they worked for me. I'm using a Pantech PX500 with Sprint, on a Toshiba A45-S150 with Feisty.

The speeds I'm getting aren't blazing (430kbps down, 230kbps up) but they're not bad. I've heard that there is some fine tuning you can do to improve this. Something about patches and buffers, I'm not sure. If anyone knows of this let me know too please.

I'm in process of testing TCP/IP tweaks but before i have started i was getting up to **[COLOR="Red"]1.2Mbps[/COLOR]** download speeds with Pantech Verizon card PC5750 and this HOW-TO.
The post above is great addition for GUI people new to linux or little shy of using shell , personally i prefer wvdial but regardless of your choice it only dials in to to ISP and makes sure the circuit stays up while actually what you do from there as well how you configure your system and browser determines your overall speed .
Try Swiftfox and take look at : 

 [WWW.SPEEDGUIDE.NET](WWW.SPEEDGUIDE.NET)

Look under Broadband > Registry Tweaks > Linux , you'll find lot of easy to follow guides on Tweaking for linux and lots of other good reads .

---

### Post by foulox on 2007-05-31
Thanks a ton!  Your howto worked great.

---

### Post by indiepop on 2007-06-07
thank you for this how-to. i actually am running OpenSuSE and i have been having a hellatious time with this whole process.  one thing i keep running into is that after adding wvdial to my startup, the computer boots up and seems to connect with my phone-as-modem; however, until i fool with the network manager, kill wvdial, and restart it, it doesn't seem to hold.

is there something wrong with the way my system is handling networking that could be causing this, i.e. should i kill the network manager applet?  if yes, how do i go about getting it back when i need to connect wirelessly/wired to a standard network?

thanks a bunch!

---

### Post by FlyingHat on 2007-06-12
This is a very good HOWTO, I especially enjoy using wvdial versus having to come up with your own PPPD scripts.  

However, using usbserial for these EVDO connections is a BAD, repeat **BAD** idea.  usbserial was not designed for high-speed connections such as EVDO connections.  

Since kernel 2.6.18, the Airprime driver has been patched to allow full-speed EVDO connections.  Essentially, instead of using usbserial, simply type in the following:

```
:~$ modprobe airprime
```

And then check dmesg to see if it was loaded correctly.  You should see something like: 
```
[ 1618.912000] usbcore: registered new interface driver airprime
```

And after inserting the device:
```
[ 1620.504000] usb usb6: configuration #1 chosen from 1 choice
[ 1620.504000] hub 6-0:1.0: USB hub found
[ 1620.504000] hub 6-0:1.0: 1 port detected
[ 1621.884000] usb 5-1: new full speed USB device using ohci_hcd and address 2
[ 1622.096000] usb 5-1: configuration #1 chosen from 1 choice
[ 1622.096000] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
```

Follow the rest of the walkthrough.  If it looks like it's connecting, go ahead and add airprime to /etc/modules or type in:

```
:~$ sudo depmod -a 
```

Try it!

---

### Post by Mach1US on 2007-06-14
> **FlyingHat said:**
> This is a very good HOWTO, I especially enjoy using wvdial versus having to come up with your own PPPD scripts.  

However, using usbserial for these EVDO connections is a BAD, repeat **BAD** idea.  usbserial was not designed for high-speed connections such as EVDO connections.  

Since kernel 2.6.18, the Airprime driver has been patched to allow full-speed EVDO connections.  Essentially, instead of using usbserial, simply type in the following:

Thanks for the input , I'll definitely try it and post back the result but can you shoot little more info on the subject especially that theinternal  serial USB  hubs using usbserial driver which are used as USB host controller interface to expose kernel to a serial device  , at least those newer ones (2.0) are capable of bus speeds at 480 Mbps  where EVDO connection averages at  around 1 Mbps which is very small fraction of the overall throughput capabilities of this particular type of a bus .
Except for default 1500 MTU size not being natively managed by your device there is nothing i could find that would impede data transfers. 
I'll really  appreciate if you could provide more detail on the issue. 


**[COLOR="Red"]To Indiepop[/COLOR]**

> **indiepop said:**
> thank you for this how-to. i actually am running OpenSuSE and i have be
en having a hellatious time with this whole process.  one thing i keep running into is that after adding wvdial to my startup, the computer boots up and seems to connect with my phone-as-modem; however, until i fool with the network manager, kill wvdial, and restart it, it doesn't seem to hold.

is there something wrong with the way my system is handling networking that could be causing this, i.e. should i kill the network manager applet?  if yes, how do i go about getting it back when i need to connect wirelessly/wired to a standard network?

thanks a bunch!

The Network Manager applet does not like to play with any configurations created by other apps or system config utilities.
the first thing i would try to edit out all instances from its interface configuration file.
The file is located at:
```
 sudo gedit /etc/network/interfaces 
``` 
First make a backup of that file and then comment it all out except for your wi-fi wep or other encription keys and paste the following:
```
 auto lo
iface lo inet loopback
```
let me know if you need more help with that.:D

---

### Post by Mach1US on 2007-06-15
My connection test result using standard usbserial driver :
[ATTACH]35455[/ATTACH]
I am getting average speeds between 1.1Mbps and 1.4Mbps

---

### Post by who_cares on 2007-06-16
has anyone managed to get this to work with Cingular/At&t?
When I try to run wvdial I get "NO CARRIER" after "ATDT #777"

---

### Post by Mach1US on 2007-06-16
Make sure your dialer script is configured properly and make you have configured correct serial device ( /dev/ttyUSB??? ) to be used by wvdial.
You can check it by inserting and removing your card and running _dmesg_ which will display your devices serial identifier and then you will need to correct it in the wvdial config script, you should see something similar :
```
m@m:~$ dmesg
    ...  * omitted output *
[17186692.460000] usb 3-1: configuration #1 chosen from 2 choices
[17186692.460000] cdc_acm 3-1:1.0: [COLOR="Blue"]_**ttyACM0**_[/COLOR]: USB ACM device
[17186708.176000] usb 3-1: USB disconnect, address 4
[17186714.588000] usb 3-1: new full speed USB device using uhci_hcd and address
```
To edit wvdial script  type in terminal :
```
 sudo gedit /etc/wvdial.conf
```
Dialer scripts in this how to will work on all standard carrier networks so i don't see why it wouldn't work with cingular / AT&T systems.

---

### Post by who_cares on 2007-06-16
I think I have the correct serial device (dev/ttyACM0)
I messed with the config file and got this far:
> root@ubuntu:~# wvdial
--> WvDial: Internet dialer version 1.56
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
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jun 17 01:46:34 2007
--> Pid of pppd: 10633
--> Using interface ppp0
--> pppd: 
--> [06][08]0[0f][06][08]
--> pppd: 
--> [06][08]0[0f][06][08]
--> pppd: 
--> [06][08]0[0f][06][08]
--> pppd: 
--> [06][08]0[0f][06][08]
--> pppd: 
--> [06][08]0[0f][06][08]
--> pppd: 
--> [06][08]0[0f][06][08]
--> Disconnecting at Sun Jun 17 01:46:35 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Sun Jun 17 01:46:37 2007

I'm not really sure what I'd need to change in my config file to fix that though.

---

### Post by stonecutter on 2007-06-17
I'm trying to get my Dell 5700 minipc Broadband card to work. When I run wvdial it kicks out 

> CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jun 16 23:11:19 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 11249
--> Using interface ppp0

then it lists an IP and DNS, pretty sure it's Verizon IP.  But then I cannot browse to the Internet.  

from my dmesg, I can't really tell which USB device it's attached to. 

> [ 3360.916000] usbcore: registered new interface driver usbserial

[ 3360.916000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic

[ 3361.008000] usbserial_generic 3-2:1.0: generic converter detected

[ 3361.008000] usb 3-2: generic converter now attached to ttyUSB0

[ 3361.008000] usbserial_generic 3-2:1.1: generic converter detected

[ 3361.008000] usb 3-2: generic converter now attached to ttyUSB1

[ 3361.008000] usbcore: registered new interface driver usbserial_generic

[ 3361.008000] drivers/usb/serial/usb-serial.c: USB Serial Driver core


When  I turn off my WLAN radio and run wvdial, it says No Carrier! Trying Again. Any thoughts as to what I need to look at? 
thanks.

---

### Post by Mach1US on 2007-06-17
**[COLOR="Red"]TO STONECUTTER [/COLOR]** your card is probably working correctly all you need to do is to restart the system , connect with EVDO making sure no other internet connection is interfering and then open the browser and all should work.
**[COLOR="Red"]TO WHO_CARES[/COLOR]**
I'v haven't encountered this problem yet but it definitely looks like pppd isn't going through or can not receive keepalives or replays from your carier but luckily you are getting  exit _code = 16 _and man page ( open terminal and type man pppd and look for error codes ) can point you in the right direction .

---

### Post by who_cares on 2007-06-17
all the man page says about exit code 16 is that it means the modem hung up.
I'm not sure if my phone hung up or if cingular cut the connection from their end though.
Any ideas on how to get the modem to not hang up?

---

### Post by who_cares on 2007-06-17
I messed with my config file and got it to work by adding Init3.
Here's a copy for anyone with the same problem:
> 
[Dialer pulse]
Dial Command = ATDP

[Dialer shh]
Init3 = ATM0

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","WAP.CINGULAR"
Phone = *99#
Modem Type = USB Modem
Stupid Mode = on
Auto DNS = 1
Baud = 115200
Modem = /dev/ttyACM0
Init = ATZ
ISDN = 0
Username = [email]WAP@CINGULARGPRS.COM[/email]
Password = CINGULAR1
Carrier Check = no
Auto Reconnect = on

---

### Post by FlyingHat on 2007-06-18
I got my information from this:

[http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html)

As well as some reading up on the patching done to the airprime driver from other sources which I've managed to lose...

---

### Post by Mach1US on 2007-06-18
Thanks [COLOR="Red"]WHO_CARES[/COLOR] for the follow up and i found another post with solution to another _exit code 16 _ and dropping connection:

[[http://ubuntuforums.org/showthread.php?t=351882](http://ubuntuforums.org/showthread.php?t=351882)]("http://ubuntuforums.org/showthread.php?t=351882")

---

### Post by who_cares on 2007-06-18
> **Mach1US said:**
> i found another post with solution to another _exit code 16 _ and dropping connection:

[http://ubuntuforums.org/showthread.php?t=351882](http://ubuntuforums.org/showthread.php?t=351882)
I had tried that fix too, I don't think it works with Cingular/AT&T

---

### Post by binarypower on 2007-07-13
Thank you Mach1US!!!


Here are the settings for Alltel (if anyone is interested)

```
[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = ??????????@alltel.net
Password = alltel
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```

---

### Post by mlexp on 2007-07-17
Can this be done with a CDMA2000 1900MHZ PDA phone like the Hitachi G1000?  Thanks.

---

### Post by Mach1US on 2007-07-17
> **mlexp said:**
> Can this be done with a CDMA2000 1900MHZ PDA phone like the Hitachi G1000?  Thanks.
This can definitely be done with any CDMA phone supporting evdo or other modem connections  as long as the kernel recognizes the device and of course if there is a way to connect it to the PC you should be ok .
The 1900MHZ is just the frequency on which your phone and carrier communicate and has no effect on its ability to connect
One of the simplest ways is to connect the phone to usb or for that matter any  connection of your choice and run " dmesg " command which will tell you what is happening when you connect it as well which connection is being assign to your device .
Additionally you can run " lshw " which will display all your hardware and it's kernel corresponding information.
If you happen to get your device up and running post back  your findings  .
:wink:

---

### Post by Wickednix on 2007-07-26
Hello guys, I have a sprint razor v3m and the kernel finds the phone but when I do the dmesg i get the following
```
[ 2563.704000] SCSI device sdb: 1994385 512-byte hdwr sectors (1021 MB)
[ 2563.704000] sdb: Write Protect is off
[ 2563.704000] sdb: Mode Sense: 03 00 00 00
[ 2563.704000] sdb: assuming drive cache: write through
[ 2563.708000] SCSI device sdb: 1994385 512-byte hdwr sectors (1021 MB)
[ 2563.708000] sdb: Write Protect is off
[ 2563.708000] sdb: Mode Sense: 03 00 00 00
[ 2563.708000] sdb: assuming drive cache: write through
[ 2563.708000]  sdb: sdb1
[ 2563.712000] sd 3:0:0:0: Attached scsi removable disk sdb
[ 2563.712000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 2737.252000] usb 3-3: USB disconnect, address 8
[ 2744.996000] usb 1-2: new full speed USB device using ohci_hcd and address 8
[ 2745.200000] usb 1-2: configuration #1 chosen from 1 choice
root@cloud9:~# 

```

 Is there any updates for this how-to. My phone has the evdo modem in the phone. I am trying to get this working on a Toshiba sat. with fiesty

---

### Post by Mach1US on 2007-07-28
Your dmesg shows that your phone is not being recognized by kernel .
This is mine dmesg output when the phone is connected, i used same phone with only difference that this one  is from verizon.
[HTML][ 4950.728000] ohci_hcd 0000:04:00.1: remove, state 0
[ 4950.728000] usb usb7: USB disconnect, address 1
[ 4950.728000] ohci_hcd 0000:04:00.1: USB bus 7 deregistered
[ 4950.728000] ACPI: PCI interrupt for device 0000:04:00.1 disabled
[ 5327.532000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 5327.704000] usb 4-2: configuration #1 chosen from 2 choices
[ 5327.704000] cdc_acm 4-2:1.0:ttyACM0: USB ACM device
[/HTML]
Make sure that your cable isn't damaged or has crossed pin out ideally try other cables to make sure it's not a phisical connection problem .
In the future try to provide as much details as you can as this may shed a clue on what is wrong,  
You should pay attention to ttyACM0 portion , this will tell you which connectuion idientifier has been assign to your device.

---

### Post by Wickednix on 2007-07-31
It cannot be the cable as it works in windows just fine.  I have tried it on another laptop and it gives the same output as posted above. I took my friends Razor verizon evdo phone and the OS gives out the correct output ( with the ttyAMO). Could it be that sprint has something disabled on the phone? 

My phone is the sprint Razor V3m (Red Phone).  I cant think of any other detail that you might need

---

### Post by Mach1US on 2007-08-01
Sprints Razr uses original Motorola software where Verizon has loaded their own version which is actually more restrictive ,verizon phones can not use bluetoth as a PC connection where sprint phones can (for the most part like razr v3 and some other ).
Assuming you are using updated feisty my next guess would be there is problem between your phone type and a driver.
You can try to patch the driver with airprime one.
I'v seen some claims stating that airprime allows you for faster speeds but after many of my own tests it has no impact (good or bad) on the overall speed , it may have been true in the past but i couldn't prove it so its just another way to connect the device.

To start  Install the minimum build environment, Linux sources, and Linux headers for your currently-running kernel:
apt-get install build-essential linux-headers linux-source

Go into /usr/src/ and uncompress the kernel source code:
cd /usr/src
tar xjvf linux-source-2.6.17.tar.bz2

Enter the directory containing the airprime driver:
cd linux-source-2.6.17/drivers/usb/serial

Now, either apply the patch, or replace airprime.c with the pre-patched version (see above for download links).

If patching:
patch -p0 < airprime-sjain-012807.patch

If replacing (not recommended, patching is safer):
mv airprime.c airprime.c.bak
mv airprime-sjain-012807.c airprime.c

Normally, to patch a driver, you have to recompile the entire kernel tree and replace all the kernel modules as well as the core kernel image itself. But since we are using Ubuntu&#8217;s sources, we can only compile the driver&#8217;s that we need and overwrite the old ones.

To compile only the airprime dirver (this actually compiles all drivers in the directory):
make -C /lib/modules/`uname -r`/build M=`pwd`

Then, install it (you need root privileges to overwrite the existing driver) and update module dependencies:
sudo cp airprime.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/airprime.ko
sudo depmod -a

 Reboot. Your device should now be recognized by the airprime driver, and a new device node /dev/ttyUSB0 created.  
The only problem is that when you upgrade the kernel it may override this driver with the serial usb driver .
more info on this site : 
[http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html)
let me know how it went .

---

### Post by DLinn on 2007-08-03
Hi-
My setup works (verizon pc5750 through Addonics CardBus/PCMCIA adapter into my desktop.

1- I have to plug my PCMCIA card in after I reach the log-in window or it will fail.

2- I can only log-in via root account but not as user. It goes through some changes when I'm user then exits w/ error code 2. I've tried every-which-o-way of card insertion , log-in, auto start and bupkus! However, if I log-in as root then log-out and in as user the connection hangs on but I have to wait about 10 minutes for the new log-in to come up.

I wanna connect as root AND as user. (waa-waa-baby is losing it)

TIA All,
DLinn

---

### Post by Mach1US on 2007-08-06
I'm currently using exactly same card as yours  (verizon pc5750) in dell inspiron 6000 with and i'v never experienced any of those symptoms which leds me to believe your adapter is causing  the problem.
Have you tried to use wvdial after issuing sudo -i .  
Sorry but i have no experience with this type of adapters .  :confused:

---

### Post by DLinn on 2007-08-06
Arr Matey-

Seems unlikely to be hardware 'cause it works as advertised when I log in as root.

If I am logged in as user and I use terminal to start wvdial I get a pppd error 2 which man pppd says is "An error was detected in processing the options given, such as two mutually exclusive options being used." Now for a relative noob such as I that's clear as mud.

So here is some stuff to consider.

root@Desktop:/usr/bin#			ls -l wvdial
-rwxr-xr-x 1 dlinn dialout 76220 2007-03-08 16:53 wvdial
root@Desktop:/usr/bin#			ls -l wvdialconf
-rwxr-xr-x 1 dlinn dialout 29540 2007-03-08 16:53 wvdialconf

root@Desktop:/etc#				ls -l wvdial.conf
-rw-r--r-- 1 dlinn dialout 349 2007-08-03 08:10 wvdial.conf

root@Desktop:/etc/ppp#			ls -l chap-secrets
-rw-rw-rw- 1 dlinn dialout 305 2007-08-03 22:13 chap-secrets
root@Desktop:/etc/ppp#			ls -l pap-secrets
-rw-rw-rw- 1 dlinn dialout 1863 2007-08-03 22:13 pap-secrets

root@Desktop:/etc/ppp/peers#	ls -l ppp0
-rw-r--r-- 1 root dialout 136 2007-08-03 07:57 ppp0

root@Desktop:/usr/sbin#			ls -l pppd
-rwxr-xr-- 1 root dialout 269224 2007-04-04 23:41 pppd
***************************************************************

root@Desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:3C:DA:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.218.206.226  P-t-P:66.174.161.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:875101 (854.5 KiB)  TX bytes:158784 (155.0 KiB)
***************************************************************

# /etc/wvdial.conf

[Dialer pulse]
Dial Command = ATDP

[Dialer shh]
Init3 = ATM0

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = vzw
Phone = #777
Modem Type = USB Modem
Stupid Mode = on
Baud = 921600
Modem = /dev/ttyACM0
Init = ATZ
ISDN = 0
Username = [email]xxxxxxxxxxx@vzw3g.com[/email]
Carrier Check = no
Auto Reconnect = on
***************************************************************

# /etc/ppp/chap-secrets

xxxxxxxxxx\@vzw3g\.com	*	vzw
***************************************************************

# /etc/ppp/pap-secrets
#
# INBOUND connections
guest	hostname	"*"	-
master	hostname	"*"	-
root	hostname	"*"	-
support	hostname	"*"	-
stats	hostname	"*"	-

# OUTBOUND connections
xxxxxxxxxx\@vzw3g\.com	*	vzw
***************************************************************

# /etc/ppp/peers/ppp0

connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"
usepeerdns
defaultroute
persist
/dev/ttyACM0
921600
debug
user "xxxxxxxxxxx@vzw3g.com"

***************************************************************

# /etc/chatscripts/ppp0

This file is blank
***************************************************************

So if this helps then ==> GREAT!!!  If not, not.

I know a local sysadmin, perhaps I can glean cure there.

I want to thank you for your help. If anything changes I will post again and if you got the cure please post again.

TIA

---

### Post by DLinn on 2007-08-06
OK progress

If I start wvdial as "sudo wvdial" I'm connected as user.

Now I want the Sessions gizmo to log me in. So far no luck.

:D

---

### Post by Mach1US on 2007-08-08
I know those error messages are very generic and basically are designed to say " something bad has happened , dig dipper to find out more " so i can understand your frustration.
Secondarily what do you mean  Session gizmo ?
Additionally it looks you are being registered to the providers network as their DHCP servers are assigning you a ip address ( 75.218.206.226 ) to your WAN interface ( ppp0 )  so this means you have wireless communication working .
 Also it shows receiving and sending communications between their routers  and your pc ( on the bottom RX bytes means received and  TX bytes means transmitted )  .
Try to test communications to internet by issuing a command " ping 216.239.59.147 " which is yahoo.com ip address.
If you will get reply something like  :
        64 bytes from 216.239.59.147: icmp_seq=1 ttl=233 time=578 ms
It means you are connected  to the internet and we have to look for other things.
And one more thing , you do not need a password in /etc/ppp/pap-secrets as this is only needed for PAP or CHAP authentication of which neither is used by Verizon also my  /etc/ppp/peers folder has no  ppp0 script .

---

### Post by DLinn on 2007-08-08
Helloooo Again-

1- The Sessions gizmo:
Ubuntu Feisty Fawn has a menu item System ==> Preferences ==> Sessions. This applet allows the user to insert commands that will run whenever your log-in, not when you boot-up, but log-in. Mine has Network Manger, Evolution Alarm Notifier, Power Manger, Restricted Drivers Manger, Touchpad, Update Notifier, and Volume control.
It's very useful to me so check it out.

Any way I've been studying up on "sudo" and "sudoer" so I have configured my /etc/sudoers file to allow me to use wvdial without a password. If this works then I will be logged onto the network as soon as my interface comes up!

All this just to save 4 keystrokes.

Thanks again, the pc5750 appears about solved.

Will write soon.

---

### Post by Mach1US on 2007-08-09
That's what you meant by  *Session Gizmo* :#-o
It's great way to automate the process , in my case i'm using EVDO in one one location Wi-Fi in other and modem in my cell phone in another so i waned to control when to use which.
For me the easiest way was to create custom button which i can move in any part of a task bar and which allows me to do it without any key strokes.
To create it :

right click on the any clear part of a task bar 
click_**Add To Panel**_
then click_**Custom Aplication Launcher**_
in the field following_**Command :**_ insert your command ( for instance **_wvdial_**) 
while you doing it you can also click on _**Icon **_ co create unique look to this button and from now every time you click on that newly created task bar button the command will be executed without opening the shell and typing the command.
Hope you can use it.

---

### Post by DLinn on 2007-08-10
Hey-

In my case the command would be *sudo wvdial*.

I'll give 'er a try.

Much Thanks

---

### Post by astanix on 2007-08-11
Hopefully someone in this thread can give me a hand.
I'm trying to use a newer phone running Windows Mobile 6 to do this.
I have a thread on it over here: [Tethering 6800/Mogul/Titan (Sprint)]("http://ubuntuforums.org/showthread.php?t=522600")

I'll just summarize my issue in this thread... when I try to connect to the inet with my phone in any way (through ppp, wvdial, just doing wvdialconf) I get this window on my phone and a failed attempt on linux.

[IMG]http://img373.imageshack.us/img373/1586/dsc00049xo8.jpg[/IMG]

any help would be greatly appreciated

---

### Post by Mach1US on 2007-08-13
Did you try this how-to step by step and able to completed it ?
Do you have EVDO service enabled on this phone or just a basic data plan  ?
I have not tried to set up sprint modems myself but i know for a fact that this how to works well with them.
If i'm not mistaking some sprint setups need user name and password in the wvdial.conf  so check that as the easiest starting point.

Come back if you still have a problem , we'll try to get you up and running.

---

### Post by astanix on 2007-08-13
Well I'm leaving for my trip in about an hour, so I don't have time to work on this right now.  I installed Windows 2000 on VirtualBox and am using pdanet through that for internet... works fine.  I'm thinking its most likely an issue with Windows Mobile 6 not working with the current Linux methods.  I'll work on it more when I get home next week and post anything I find out.

---

### Post by KyleYankan on 2007-08-17
Hi everyone,
 I posted on a diferent thread about my CHAP authentication errors, and got refered here. I tried the tutorial, but I still get this error:

```
kyle@Brandy:~$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Aug 17 07:34:17 2007
--> Pid of pppd: 20223
--> Using interface ppp0
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> Disconnecting at Fri Aug 17 07:34:28 2007
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
kyle@Brandy:~$ 

```

Please note that I'm on a Motorola E815 on /dev/rfcomm1

Thanks for all your help!

---

### Post by DLinn on 2007-08-17
Hi-

Your pppd error 19 means "We failed to authenticate ourselves to the peer."

As root go to /etc/ppp and 'gedit' the file 'options' and check that 'noauth' is not commented out w/ a '#'.

If it is remove the '#', save the file and try again.

DLinn

---

### Post by KyleYankan on 2007-08-17
Sorry, noauth is not commented in my /etc/ppp/options file. :-/

> **DLinn said:**
> Hi-

Your pppd error 19 means "We failed to authenticate ourselves to the peer."

As root go to /etc/ppp and 'gedit' the file 'options' and check that 'noauth' is not commented out w/ a '#'.

If it is remove the '#', save the file and try again.

DLinn

---

### Post by Mach1US on 2007-08-20
What DLinn means is make sure file /etc/ppp/options lists " noauth " command , this is what you shoud see when you done  :
```
# 
#Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth

```

---

### Post by KyleYankan on 2007-08-20
> **Mach1US said:**
> What DLinn means is make sure file /etc/ppp/options lists " noauth " command , this is what you shoud see when you done  :
```
# 
#Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth

```

I got that, sorry if my previous post was ambigous. My options file reads as above, as it was when I ran into the problem.

---

### Post by Mach1US on 2007-08-20
Your problem is definitely with the authentication , what is happening the other side does not recognizes you as a legitimate user  so it does not assigns you IP addres .
Check if your user name and password are configured correctly as this would be a first thing  that would cause it.
Was your EVDO card or modem connecting before with any other machine or os (windows or mac) ? 
Which provider do you use ?
Also What do you have in the /etc/wvdial.conf  ?

---

### Post by KyleYankan on 2007-08-20
> **Mach1US said:**
> Your problem is definitely with the authentication , what is happening the other side does not recognizes you as a legitimate user  so it does not assigns you IP addres .
Check if your user name and password are configured correctly as this would be a first thing  that would cause it.
Was your EVDO card or modem connecting before with any other machine or os (windows or mac) ? 
Which provider do you use ?
Also What do you have in the /etc/wvdial.conf  ?

Wel, I'm actually using a cell-phone over bluetooth for this, as I was told it should respond exactly as an EVDO card (it's a Motorola E815, which is basically a RAZR in disguise). I've never tried using it on windows, as this is my first computer with bluetooth, and the only time it booted into windows was by accident when I first got it.

My chap-secrets has this in it, with a similar entry in my pap-secrets:
```
5555555555\@vzw3g\.com	*	vzw
```

My /etc/wvdial.conf:
```
[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/rfcomm1
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = 5555555555@vzw3g.com
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```

Please note that I replaced my phone number with a generic 5555555555

Please let me know if anything obvious is sticking out. Thanks for all your help!

---

### Post by Mach1US on 2007-08-21
I do not have  _xxxxxxxxxx\@vzw3g\.com * vzw _ line in my /etc/ppp/chap-secrets  or /etc/ppp/pap-secrets as this i found out requires root privileges to log in due to fact that those files can be only modified by root.
First thing try to use :
```
 sudo wvdial
```  
and then  remove the lines from both of above mentioned files.

---

### Post by KyleYankan on 2007-08-21
> **Mach1US said:**
> I do not have  _xxxxxxxxxx\@vzw3g\.com * vzw _ line in my /etc/ppp/chap-secrets  or /etc/ppp/pap-secrets as this i found out requires root privileges to log in due to fact that those files can be only modified by root.
First thing try to use :
```
 sudo wvdial
```  
and then  remove the lines from both of above mentioned files.

OK, I ran `sudo wvdial` to the same result as before, so I removed the respective lines from [ch|p]ap-secrets, and treid again. This is that I got:

> --> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Aug 21 11:30:49 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 9214
--> Using interface ppp0
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> Connect time 0.1 minutes.
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> pppd: P[06][06][08]x
--> [06][08]
--> Disconnecting at Tue Aug 21 11:30:57 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
~[7f]}#@!}%}#} }$}%r~~[7f]}#@!}%}$} }$} ~~
--> Modem not responding.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
~[7f]}#@!}%}#} }$}%r~~[7f]}#@!}%}$} }$} ~~
--> Modem not responding.
--> Disconnecting at Tue Aug 21 11:31:40 2007

Now I'm getting a phone error. The command I use to attach my phone is `rfcomm connect 1 00:17:84:7C:D3:38 8`


I never get any luck! :-P

---

### Post by Mach1US on 2007-08-21
I am wondering if the BlueTooth connection isn't playing tricks with us?
Do you know for sure that it can support all features needed for PPP protocol ?
We should isolate the problem to find out which wireless connectiom might be at fault , PC to phone or phone to carrier network.
If you have or you can borrow a mini USB cable like that:
[http://cgi.ebay.com/Mini-USB-cable-F-Canon-Olympus-Digital-Camera-U25_W0QQitemZ280144526724QQihZ018QQcategoryZ88657QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Mini-USB-cable-F-Canon-Olympus-Digital-Camera-U25_W0QQitemZ280144526724QQihZ018QQcategoryZ88657QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
Try to use this how-to from beginning using the USB cable instead of BlueTooth.
Also once you get the cable you can check if the phones EVDO modem is properly activated on Verizons network by going to [http://vzw.smithmicro.com](http://vzw.smithmicro.com) where you can download windows and other versions of vzmanager software which includes all necessary drivers and setting for configuration less setup.
First try to get it up and running in windows which should take you less then 3 minutes to set it up , if it won't work trouble shoot with Verizon , once successful in windows try connect via USB and this how-to and again once you get it up and running see if BlueTooth will allow you to do the same.
From my own experience  when i switched from using Razr v3 as a modem to a PC Card i had to call them and they had to enable additional data options on their end before i was able to start using the PC Card  .
Hope this will do it.:wink:

---

### Post by CJJones on 2007-08-21
> **binarypower said:**
> Thank you Mach1US!!!


Here are the settings for Alltel (if anyone is interested)

```
[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = ??????????@alltel.net
Password = alltel
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```


worked great installing on p3 for my dad.  Used above for pc5750 starcom through alltel.  

I initially set it up on my xp laptop and then on ubuntu 7.04 compared speeds with [www.speedtest.net](www.speedtest.net) and they were pretty much identical.

---

### Post by JesCed on 2007-08-24
Hi, all.

I tried using the HOWTO, and after tweaking a few items, I got my connection working with a Kyocera KPC650 EVDO card using an Acer Aspire 3690 for Movistar in Venezuela. I just have one question, and I'm sorry if it's too silly.

How do I close my connection? :lolflag:

Thanks

---

### Post by Mach1US on 2007-08-24
If you are started it from shell promt the easiest way is to go back to it and press CTRL+C  or CTRL+Z .

---

### Post by JesCed on 2007-08-24
OK, but what about if I didn't start it from the terminal? In my case, I added a custom launcher to my panel, and click on it to connect.

BTW, has anyone got this working using a graphical interface like GNOME PPP or any other?

---

### Post by JesCed on 2007-08-25
Well, I managed to get this working with GNOME PPP, so I now have a quick graphical way of logging on and off. This should help a few people at the University. Thanks for all the help

---

### Post by IDeus on 2007-08-28
I am running Fiesty and have a Treo 700p Everytime i type sudo wvdial it reboots by treo!

I get 

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
-->  Modem not responding.

[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyUSB0
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = [email]5555555555@sprintpcs.com[/email]
Password = xxxxxxx
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP

---

### Post by Mach1US on 2007-08-30
First thing make sure the output from " dmesg " displays " ttyUSB0 " as an identifier for your Evdo Phone / modem.
If it does your problem is not with wvdial configuration , your phone is not communicating properly with kernel or has been assigned different device identifier.
Try to restart your machine , and follow all steps of this how to _Exactly_.
hopefully this will help.

---

### Post by Jamie Jackson on 2007-09-03
Here's my working Motorola RAZR V3t (T-Mobile) config. I don't know how much of it is necessary, and how much is superfluous, but it works.

Here are the bits from dmesg:
ttyACM0
Vendor=22b8 ProdID=4902 Rev= 0.01

Here's the wvdial config:
```
[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
#Init2 = at+cgdcont=1,"ip","internet2.voicestream.com"
#Init2 = at+cgdcont=1,"ip","internet3.voicestream.com"
Init2 = at+cgdcont=1,"ip","wap.voicestream.com"
Phone = *99# 
Username = web
Password = web
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```

---

### Post by JJL79 on 2007-09-04
Mach1US, just want to let you know this works for HTC Tytn too with no problems at all

---

### Post by Mach1US on 2007-09-04
Thanks for the follow up and feel free to post your configs .:)

---

### Post by buu700 on 2007-09-30
NICE! THANKS! I'm going to try this with my Verizon LG Chocolate/VX8500 as soon as I can (misplaced my USB cable... might have to order another one... oh well they're only like $2 anyways if you use eBay like I did). By the way, has anyone else tried this with an LG VX8500/Chocolate?

---

### Post by vacaloca on 2007-10-06
Just wanted to point out that this method worked successfully with the Motorola V9m over a micro-USB connection.

I should also mention that once you issue the modprobe command as on the first post, the phone charges directly from the USB cable. (Essentially the equivalent of installing the corresponding Motorola USB drivers on Windows... nice to know that Linux does it so easily w/o any addons!)

---

### Post by Mach1US on 2007-10-07
Additionally if you are outside of evdo coverage area you can use the same method to use the cell phone as a dial up modem .
The speed isn't impressive but at least you getting connected .

For anybody interested here is link for obtaining **FREE dialup  account** .
Registration is free as well as unlimited use , there is no charge whatsoever .
[www.metconnect.com](www.metconnect.com)

---

### Post by vmosorio on 2007-10-08
Mach1,

I've been searching hi and lo for a solution to my GPRS connection; I have followed your nice tutorial and have my wvdial file configured as this:

[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = *99***3# 
Username = webmegatel
Password = webmegatel
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP

When I run wvdial command in the terminal I get the following:

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***3#
--> Waiting for carrier.
ATDT*99***3#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Oct  8 14:23:18 2007
--> Pid of pppd: 5355
--> Using interface ppp0
--> pppd: ï¿½[12][06][08]x
--> [06][08]
--> pppd: ï¿½[12][06][08]x
--> [06][08]
--> pppd: ï¿½[12][06][08]x
--> [06][08]
--> pppd: ï¿½[12][06][08]x
--> [06][08]
--> pppd: ï¿½[12][06][08]x
--> [06][08]
--> pppd: ï¿½[12][06][08]x
--> [06][08]
--> Disconnecting at Mon Oct  8 14:23:22 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK

Same exit code 16. I have tried different set ups with no luck. My GPRS connection in windows with the Moto Phone tools ask for the "access point name" APN, and I have always wondered if I need that somewhere in the wvdial config. I have a Moto L6 cell and I'm using Ubuntu 7.04 and I live in Honduras.

Thanks for any help

---

### Post by Mach1US on 2007-10-09
Your setup looks good as well as it shows that your modem sees and more importantly communicates with the carrier.
Link establishment is another question , it looks that one of the phases of link establishment is failing and that is why you are not being issued a DHCP configs.
Your modem is configured properly , most likely you have to edit or add another int. line  to vwdial.conf .
Check back few posts back , some of the guys have posted their modifications and feel free to post yours once you find it .
Let me know if you'll still need little help.

---

### Post by vmosorio on 2007-10-11
I have tried those Init in the thread before  with the same result; if you see something obvious I should need please let me know. And thanks for answering my questions, this is about the first one I get on the forum.

Cheers.

---

### Post by Mach1US on 2007-10-13
Do not give up that easily , when you do it usually means you did get through 95% of all obstacles and you just have to grind through last few   unfortunately hardest steps.

What happens when you try the graphical way?
Sprints PDF  
[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)
Shoot me a e-mail and i'll sent you PDF on how to enable it through KPPP graphical dialer.

---

### Post by vmosorio on 2007-10-13
Thanks again for your help. I couldn't find your e-mail so I have to post mine here, send me that info to: [email]victor@radiojuticalpa.com[/email]  I'm not afraid of spam as you can see, hahaha!  GUI might be easier huh? I don't plan to give up yet as I intend to replace windows in all my PCs for good here at the radio station where I work. I'd like to use Campcaster and sound editors like Audacity ad the like.  Cheers.

---

### Post by scorpio_digit on 2007-10-15
Okay, so I'm using a Razr v3m to do this. I can get most of it working (the phone dials), but I get exit code 19 ( cannot authenticate). I do not have noauth commented out. What should I do?

---

### Post by Mach1US on 2007-10-15
> **scorpio_digit said:**
> Okay, so I'm using a Razr v3m to do this. I can get most of it working (the phone dials), but I get exit code 19 ( cannot authenticate). I do not have noauth commented out. What should I do?

Can you post exact syntax of the error message  (wvdial shell output) , your wvdial.conf  as well as a name of your  cell provider ?

---

### Post by scorpio_digit on 2007-10-16
I'm using a Razr v3m with Verizon. I had this working in XP. Here's the output:
[INDENT]root@nicole:/# wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&CpG.}'}"}(}"tP~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Oct 16 12:55:25 2007
--> Pid of pppd: 7359
--> Using interface ppp0
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> Disconnecting at Tue Oct 16 12:55:28 2007
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
[/INDENT]
And here's the wvdial.conf file:
[INDENT][Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = **********@vzw3g.com
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP[/INDENT]

---

### Post by Mach1US on 2007-10-17
Your wvdial.conf looks correct.
My own first setup was with this exact prone on Verizon network and since i must have set it up at least doznen times without single problem so it must be something really silly.

1)Do you see on phones display little symbol "  EVDO " indicateing you are in EVDO coverage ?
2)Is signal on your phone strong enough (two bars recommended) , if not try another location.
3)Did you put in your phone number in wvdial.conf correctly , without one in front of it , without spaces, brackets or anything else ?
4)Did you check another cable in case it's defective or incorrect ?
5)Have you tried it in windows recently to make sure EVDO service is still enabled and properly configured on Verizons end ?

If you want to try GUI dialer like KPPP or you need Verizon software for windows sent me e-mail and i'll send you a link and PDF file with instructions.
I'll check with my old V3m phone again and post the findings here.

---

### Post by JesCed on 2007-10-19
Hello, all.

Quite a few things have happened since my last post. First of all, due to a few incidents which were all my fault, I formatted my HD and reinstalled Ubuntu. Before doing so, I backed up my wvdial.conf file (along with my other personal files). After reinstalling, I copied the backed-up file into the appropriate folder, and found a problem similar to the one scorpio_digit describes: an error 19.

After this, Gutsy was released, so I downloaded and upgraded to Gutsy before getting back to my error 19.... the error still ocurred, so I decided to follow all the steps in this original HOWTO, and everything turned out fine (even using my original wvdial.conf). I can perfectly login from the terminal.

My new issue, however, is that I can't connect via GNOME PPP. I downloaded and installed it, and set my phone number, ID, password and other parameters, but it still doesn't connect. After clicking on "connect", the blue light on the card flashes, and I see the "dialing" message, but nothing else happens.

Here is the output on the log:

/home/jesus/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!"
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATX3
WvDial Modem<*1>: ATX3
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATM1L3DT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATM1L3DT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Fri Oct 19 23:56:57 2007
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 5929
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 10.97.9.251
WvDial<*1>: remote IP address 2.2.2.2
WvDial<*1>: primary   DNS address 200.35.65.3
WvDial<*1>: secondary DNS address 200.35.65.4

Any ideas as to what might be happening and how to solve this?

---

### Post by vmosorio on 2007-10-20
I have installed the GUI KPPP and the modem seems to work fine goes to the point where the connections starts logs in verifying username and password (according to the KPPP window) but then I get the same message of wvdial of exit code=16. 
What I want to do now is find a way to check the log or the process of connection in windows thorugh the Moto Phone Tools software which is what I use to connect, if you have any other idea please let me know. 

Best

---

### Post by Mach1US on 2007-10-20
There are few problems that surfaced post Gutsy :

There is no more /proc/bus/usb/devices directory **!!!**
Gutsy has changed its internal USB handling (this includes EVDO PCMCI cards) .
Additionally  now EVDO cards are recognized and assigned airprime driver by default  also device to kernel assignment has changed thus rendering previous set-ups unusable .
Once all those issues are solved i'll be posting Gutsy update so for now this how-to is valid up to Feisty (7.04).

[COLOR="Red"]**JesCed**[/COLOR] did you do a upgrade to gutsy or fresh install?

---

### Post by vmosorio on 2007-10-21
Alright Mach1, up to Feisty is now...

I found that the APN (access point name) can be sent on KPPP with this line in the init string: AT+CGDCONT=1,"IP","web.megatel.hn"   ...
I get the same error message exit code=16. I tried removing the APN in the windows machine; it doesn't connect and says that I'm not suscribed to the DATA feature, it connects right away with the APN. 
I haven't been able to find out in windows how to see the log of normal connection, there are some logs when there is trouble... here is one if you can understand it:

10-19-2007 07:21:58.901 - File: C:\WINDOWS\system32\tapisrv.dll, Version 5.1.2600   
10-19-2007 07:21:58.901 - File: C:\WINDOWS\system32\unimdm.tsp, Version 5.1.2600   
10-19-2007 07:21:58.901 - File: C:\WINDOWS\system32\unimdmat.dll, Version 5.1.2600   
10-19-2007 07:21:58.911 - File: C:\WINDOWS\system32\uniplat.dll, Version 5.1.2600   
10-19-2007 07:21:58.971 - File: C:\WINDOWS\system32\drivers\modem.sys, Version 5.1.2600   
10-19-2007 07:21:58.971 - File: C:\WINDOWS\system32\modemui.dll, Version 5.1.2600   
10-19-2007 07:21:59.051 - File: C:\WINDOWS\system32\mdminst.dll, Version 5.1.2600   
10-19-2007 07:21:59.051 - Modem type: Motorola USB Modem
10-19-2007 07:21:59.051 - Modem inf path: oem4.inf
10-19-2007 07:21:59.051 - Modem inf section: USBMOTOROLA_COMMON
10-19-2007 07:21:59.051 - Matching hardware ID: usb\vid_22b8&pid_4902
10-19-2007 07:21:59.151 - 230400,8,N,1, ctsfl=1, rtsctl=2
10-19-2007 07:21:59.212 - Initializing modem.
10-19-2007 07:21:59.222 - Send: AT<cr>
10-19-2007 07:21:59.232 - Recv: AT<cr>
10-19-2007 07:21:59.232 - Command Echo
10-19-2007 07:21:59.232 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:21:59.232 - Interpreted response: OK
10-19-2007 07:21:59.242 - Send: AT<cr>
10-19-2007 07:21:59.252 - Recv: AT<cr>
10-19-2007 07:21:59.252 - Command Echo
10-19-2007 07:21:59.252 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:21:59.252 - Interpreted response: OK
10-19-2007 07:21:59.262 - Send: AT+IFC=2,2<cr>
10-19-2007 07:21:59.272 - Recv: AT+IFC=2,2<cr>
10-19-2007 07:21:59.272 - Command Echo
10-19-2007 07:21:59.272 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:21:59.272 - Interpreted response: OK
10-19-2007 07:21:59.272 - Waiting for a call.
10-19-2007 07:21:59.282 - Send: ATS0=0<cr>
10-19-2007 07:21:59.292 - Recv: ATS0=0<cr>
10-19-2007 07:21:59.302 - Command Echo
10-19-2007 07:21:59.302 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:21:59.302 - Interpreted response: OK
10-19-2007 07:21:59.302 - Passthrough On
10-19-2007 07:22:20.352 - Passthrough Off
10-19-2007 07:22:20.352 - 230400,8,N,1, ctsfl=1, rtsctl=2
10-19-2007 07:22:20.532 - Initializing modem.
10-19-2007 07:22:20.542 - Send: AT<cr>
10-19-2007 07:22:20.542 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:20.542 - Interpreted response: OK
10-19-2007 07:22:20.552 - Send: AT<cr>
10-19-2007 07:22:20.562 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:20.562 - Interpreted response: OK
10-19-2007 07:22:20.572 - Send: AT+IFC=2,2<cr>
10-19-2007 07:22:20.582 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:20.582 - Interpreted response: OK
10-19-2007 07:22:20.582 - Waiting for a call.
10-19-2007 07:22:20.592 - Send: ATS0=0<cr>
10-19-2007 07:22:20.612 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:20.612 - Interpreted response: OK
10-19-2007 07:22:22.765 - Passthrough On
10-19-2007 07:22:23.236 - Passthrough Off
10-19-2007 07:22:23.236 - 230400,8,N,1, ctsfl=1, rtsctl=2
10-19-2007 07:22:23.256 - Initializing modem.
10-19-2007 07:22:23.266 - Send: AT<cr>
10-19-2007 07:22:23.276 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:23.276 - Interpreted response: OK
10-19-2007 07:22:23.286 - Send: AT<cr>
10-19-2007 07:22:23.296 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:23.296 - Interpreted response: OK
10-19-2007 07:22:23.306 - Send: AT+IFC=2,2<cr>
10-19-2007 07:22:23.316 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:23.316 - Interpreted response: OK
10-19-2007 07:22:23.316 - Waiting for a call.
10-19-2007 07:22:23.326 - Send: ATS0=0<cr>
10-19-2007 07:22:23.346 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:23.346 - Interpreted response: OK
10-19-2007 07:22:23.577 - 115200,8,N,1, ctsfl=1, rtsctl=2
10-19-2007 07:22:23.597 - Initializing modem.
10-19-2007 07:22:23.607 - Send: AT<cr>
10-19-2007 07:22:23.617 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:23.617 - Interpreted response: OK
10-19-2007 07:22:23.627 - Send: AT<cr>
10-19-2007 07:22:23.637 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:23.637 - Interpreted response: OK
10-19-2007 07:22:23.647 - Send: AT+IFC=2,2<cr>
10-19-2007 07:22:23.657 - Recv: <cr><lf>OK<cr><lf>
10-19-2007 07:22:23.657 - Interpreted response: OK
10-19-2007 07:22:23.667 - Dialing.
10-19-2007 07:22:23.677 - Send: ATD*##***##<cr>
10-19-2007 07:22:23.707 - Recv: <cr><lf>CONNECT<cr><lf>
10-19-2007 07:22:23.707 - Interpreted response: Connect
10-19-2007 07:22:23.707 - Receive Connect but CD was low, Waiting for signal to go high
10-19-2007 07:22:23.727 - CD has been raised
10-19-2007 07:22:23.727 - Connection established at 115200bps.
10-19-2007 07:22:23.727 - Error-control off or unknown.
10-19-2007 07:22:23.727 - Data compression off or unknown.
10-19-2007 07:22:53.740 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
10-19-2007 07:24:53.743 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
10-19-2007 07:26:53.735 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
10-19-2007 07:28:53.738 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0


etc etc.... sorry for taking up so much space!!!!

---

### Post by JesCed on 2007-10-22
Mach1US

Hello. Answering your question, I did an upgrade to Gutsy, not a fresh install.

I also find it curious that you mention that previous installs don't work. As I said, I followed the original HOWTO posted on this thread, and it actually **does** work. As I said, I can connect fine from the terminal. It's only when I connect via GNOME PPP that I haven't been able to.

---

### Post by mimsmall on 2007-10-22
could I expect this setup to work on T-Mobile using Sierra Aircard 750 or any other aircard for that matter. I just want to surf the net when I am out and about.

---

### Post by vmosorio on 2007-10-22
Finally my Friend Mach!!!

I've got my GPRS connection running! 
While searching for APN (as you wisely suggested) I found that the int line: AT+CGDCONT=1,"IP","web.megatel.hn" had to be added in the modem commands tab.  I added that but still couldn't get online until I decided to try a different number ( I don't know why, maybe a flash!) so i tried *99***1# instead of *99***3# of the windows configuration... I did that and voila! Ubuntu is online!
I'm using GUI KPPP.

For mimsmall I found this page with info on Sierra cards...

[http://mycusthelp.com/sierrawireless/supportkbitem.asp?sSessionID=&Inc=2870&sFilA=FAQ%20Category&sFilB=Products&sFilC=&KEY=775](http://mycusthelp.com/sierrawireless/supportkbitem.asp?sSessionID=&Inc=2870&sFilA=FAQ%20Category&sFilB=Products&sFilC=&KEY=775)

Hope this helps and THANKS SO MUCH FOR THAT GREAT HELP!

---

### Post by pumrum on 2007-10-24
Here is the process I used in Feisty for my Pantech. If you have the Vendor and Product ID, the same process works for Gutsy (you may need to reboot to get the kernel to assign the card to ttyACM0... but once it does that it works fine.

If you're in Gutsy, as noted before, you can't do the devices stuff.... so just skip to step 10. Might be worth doing this once on a Feisty install to get your productID/vendorID.... or just try the values I have. works great.

With no tweaking, I've seen torrent download speeds up to 2.5 megabits per second (average, not burst).


#
Configure the Sprint EVDO Broadband Card

   1. Remove the broadband card if it is already inserted
   2. Navigate Applications > Accessories > Terminal
   3. Type sudo cat /proc/bus/usb/devices > devices and press Enter
   4. Insert the broadband card and wait 15 seconds
   5. Type dmesg and press Enter
   6. Make a note of the last few lines similar to:

          cdc_acm 6-1:1.0: ttyACM#: USB ACM device

   7. Type diff /proc/bus/usb/devices devices | grep Vendor and press Enter
   8. Make a note of the output similar to:

          Vendor=106c ProdID=3702 Rev= 1.00

   9. Type sudo modprobe usbserial vendor=0x**** product=0x#### and press Enter
         1. Replace **** with the Vendor from the diff output in step C.9
         2. Replace #### with the ProdID from the output in step C.9
  10. Type sudo gedit /etc/wvdial.conf and press Enter
  11. Replace the entire file with the following text, replacing ttyACM# with the output from step C.7:

          [Dialer Defaults]
          Stupid Mode = on
          Modem = /dev/ttyACM#
          Baud = 921600
          Init = ATZ
          Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
          Phone = #777
          Username = 5856156939
          Password = 0000
          Init1 = ATZ
          ISDN = 0
          Modem Type = Analog Modem
          Auto Reconnect = on
          Carrier Check = no
          [Dialer shh]
          Init3 = ATM0
          [Dialer pulse]
          Dial Command = ATDP

  12. Save the file and exit
  13. Type sudo gedit /etc/ppp/peers/wvdial and press Enter
  14. Append the following to the end of the file

          lcp-echo-failure 0
          lcp-echo-interval 0

  15. Save the file and exit
  16. Type sudo ifdown eth0 and press Enter
  17. Type wvdial and press Enter
         1. Verify that the modem connects and presents you with an IP address
         2. If you are presented with an error that it cannot find the device, you may need to restart the computer
  18. Press CTRL-SHIFT-T to open a new terminal tab
  19. Type ping 129.21.3.17 and press Enter
         1. Verify that you receive responses to the pings
  20. Press CTRL-C to close the broadband connection
  21. Type rm -rf /devices and press Enter to remove the temporary file
  22. Type exit and press Enter
  23. To start the dialer in the background:
         1. Press ALT-F2
         2. Type wvdial and click Run

---

### Post by Mach1US on 2007-10-24
> **vmosorio said:**
> Finally my Friend Mach!!!

I've got my GPRS connection running! 
While searching for APN (as you wisely suggested) I found that the int line: AT+CGDCONT=1,"IP","web.megatel.hn" had to be added in the modem commands tab.  I added that but still couldn't get online until I decided to try a different number ( I don't know why, maybe a flash!) so i tried *99***1# instead of *99***3# of the windows configuration... I did that and voila! Ubuntu is online!
I'm using GUI KPPP.

For mimsmall I found this page with info on Sierra cards...

[http://mycusthelp.com/sierrawireless/supportkbitem.asp?sSessionID=&Inc=2870&sFilA=FAQ%20Category&sFilB=Products&sFilC=&KEY=775](http://mycusthelp.com/sierrawireless/supportkbitem.asp?sSessionID=&Inc=2870&sFilA=FAQ%20Category&sFilB=Products&sFilC=&KEY=775)

Hope this helps and THANKS SO MUCH FOR THAT GREAT HELP!
 
Glad to hear it's finally working , thanks for the update and feel free to to submit your help .

> **mimsmall said:**
> could I expect this setup to work on T-Mobile using Sierra Aircard 750 or any other aircard for that matter. I just want to surf the net when I am out and about.

This setup has been successfully tested on T-mobile network but not this exact card but i do not see any reason why it would be a problem . 

> **JesCed said:**
> Mach1US

Hello. Answering your question, I did an upgrade to Gutsy, not a fresh install.

I also find it curious that you mention that previous installs don't work. As I said, I followed the original HOWTO posted on this thread, and it actually **does** work. As I said, I can connect fine from the terminal. It's only when I connect via GNOME PPP that I haven't been able to.

You are absolutely right , i should have been more clear , the setup does in fact work using wvdial when upgreded from Feisty to Gutsy.
All the machines that i have been able (sort of ;-)) successfully upgrade to Gutsy are using previous settings,scripts and drivers .
Unfortunately with fresh installs i had to pull down some system files from old backups and kind a rig it just to get it to connect at all   which my get ruined again with nearest update or kernel upgrade .
I haven't stumbled upon any clean methods of setting it up so it would be greatly appreciated if anybody finding anything useful on Gutsy have it posted here.

---

### Post by tttampa on 2007-10-24
:confused:  the main problem to why the EVDO card does not work is because the file /proc/bus/usb/devices does not exist anymore (as Mach1 said), so the modem does not show up in any list. My Verizon PC5750 card was working great in 7.04 but it shows up as usb5 and usb6 in /dev . In KPPP, the selection of modem does not fill this selection so -dead in the water- and doing the list from point 10 on won't help. How can we point to a modem when it does not show up? It was ttyACM0 in 7.04.

Rafa

---

### Post by Mach1US on 2007-10-25
The problem is that Gutsy automatically plugs it a Airprime driver which does not assigns any particular device identifier to which the dialer (wvdial,KPPP or Gnome PPP) can be pointed to .
I do figured out how to change USB handling and reenable /proc/bus/usb/devices again so now we just need to address a driver problem.
If you guys find any reliable way to pach the kernel back to use usbseria driver we can get the ball rolling on updating the setup for Gutsy .

---

### Post by Mach1US on 2007-10-26
**OK here is update on the issue **
All upgrades directry from Feisty seem to work fine unless the Evdo card / modem is upgraded then it automatically plugs default Gutsy driver.
In case this happens or you just installed fresh 7.10 you can execute following fix.

Gutsy changed USB handling so to re enable /proc/bus/usb/devices directory type in terminal : 

```
gedit /etc/init.d/mountdevsubfs.sh
```

Now remove " # " symbols from the front of following lines of code :
```
        #mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb
```

Now to so stop new Airprime driver from loading execute following in the terminal:
```
sudo gedit /etc/modprobe.d/blacklist

```

Insert at the bottom :
```
#Block Airprime driver to force kernel to use usbserial
blacklist airprime
```

From here you should be able to continue with this how to as above fix will enable single device identifier which can be uset for setup with wvdial , KPPP dialer or Gnome PPP .

If you find relevant threads or site please let me know.:!:

---

### Post by moogle on 2007-10-26
Hey Mach, 
I've been keeping an eye on this thread as I'm working on my phone. I run Xubuntu and I'm attempting to tether my htc-mogul (ppc-6800) with sprint as my provider. The best I've managed so far is to use wvdial to create a ppp0 device using /dev/ttyACM0 and it seems to be getting an IP and dns settings. I only seem to be able to do this when I run a program on the phone called "USB Modem" which seems to activate the phone as a serial device (guessing here). Does anyone on this thread have any experience with this phone or tethering with the mogul specifically? I can post my wvdial.conf file if you need. Btw thanks for taking as much time as you do on these forums to help! It IS appreciated, even if not vocalized so often

---

### Post by keepertoad on 2007-10-28
Thanks for posting this how to.  my Verizon card worked flawlessly with 7.04 but broke on upgrade to 7.10.  Found this afte struggling for several days and it's back in business.  thanks again.

---

### Post by Mach1US on 2007-10-28
Thanks for the kind words , it's great to hear that .
  
Moogle , if you are being assign the IP address and given DNS addresses  you shoud be able connect to the internet  .
What happens when you ping known web servers ( cisco server IP is 198.133.219.25 ) ?
What happens when you ping serial links peer router ( cell provider ) address , or any of the DNS servrs ?

---

### Post by el_bizarro on 2007-10-28
I'm using Kubuntu and I cannot save the /etc/init.d/mountdevsubfs.sh
file as I get "No Permissions to save this file"

Any Ideas please as 2 things currently stop me from Dropping Windows..

1 - This Problem
2 - getting Delorme Street atlas or MS Streets and Trips to work with my USB Bluetooth adapter..

El.

---

### Post by Mach1US on 2007-10-28
> **el_bizarro said:**
> I'm using Kubuntu and I cannot save the /etc/init.d/mountdevsubfs.sh
file as I get "No Permissions to save this file"

Any Ideas please as 2 things currently stop me from Dropping Windows..

1 - This Problem
2 - getting Delorme Street atlas or MS Streets and Trips to work with my USB Bluetooth adapter..

El.

1.For the first one put  ```
sudo 
```in front of the command this allows you to execute commands as Root which in turn allows to make changes to the system files .

2.For the second one try [www.gpsdrive.de](www.gpsdrive.de) which i use myself with Pharos receiver which originally came with Microsoft street and trips .

---

### Post by el_bizarro on 2007-10-28
That worked thanks but..

The following commands came with errors..

The CAT and DIFF commands did not work

No Such File or Directory..

Am I doing something wrong,,

El..

---

### Post by scottvan on 2007-10-28
Thanks, Mach1US!  It finally works on 7.10 after a few reboots...

---

### Post by Mach1US on 2007-10-29
> **el_bizarro said:**
> That worked thanks but..

The following commands came with errors..

The CAT and DIFF commands did not work

No Such File or Directory..

Am I doing something wrong,,

El..

Ok i assume that you are running Gutsy in which case you have follow the bigging of this how-to which has a fix for those issues .
After you finish the first part at the beginning follow the rest of it after which you will need to reboot (sometime more then once ) .

---

### Post by coskierken on 2007-11-03
There is suppose to be a VZAccess Manager for Linux V1.2.  I cant find a link for a download site.  Can anyone help?  Thanks!

---

### Post by coskierken on 2007-11-03
Oh, was able to find the modem and the port it is on (ttyUSB0) and get wvdial to activate.  It comes up with the errors of not having a valid phone number, login, and password.  The system should not need a login and password, though.

---

### Post by Mach1US on 2007-11-03
You are probably use to Windows which actually uses all of those entries with the difference that the software supplies of it automatically .
VZmanager last time i checked was windows and mac only and  i too would like to see the linux version as well.
Do not worry about some of those ubiquitous messages .
Your EVDO card ( or phone ) has assigned Phone number so your USERNAME is that number followed by **@vzw3g.com** .
Your password is** vzw** .
For Verizon the number you have to dial is always **777**

Web address for the verizon download page is :
[http://Vzw.smithmicro.com](http://Vzw.smithmicro.com)
VZmanager requirements:
[http://ubuntuforums.org/showthread.php?p=3699342#post3699342](http://ubuntuforums.org/showthread.php?p=3699342#post3699342)
[http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

---

### Post by gcampathome on 2007-11-04
I'm confused.  I can't figure out what the name of the device is to enter into wvdial.conf.

This is the output from dmesg.

 81.651571] ohci_hcd 0000:04:00.1: irq 18, io mem 0x54001000
[   81.686597] usb usb9: configuration #1 chosen from 1 choice
[   81.686767] hub 9-0:1.0: USB hub found
[   81.686819] hub 9-0:1.0: 1 port detected
[   82.441847] usb 8-1: new full speed USB device using ohci_hcd and address 2
[   82.453828] usb 8-1: configuration #1 chosen from 1 choice
root@dell-notebook:~# 

I am using a Kyocera KPC650 pcmcia card that works ok in winXP...

garyathome

---

### Post by Mach1US on 2007-11-04
> **gcampathome said:**
> I'm confused.  I can't figure out what the name of the device is to enter into wvdial.conf.

This is the output from dmesg.

 81.651571] ohci_hcd 0000:04:00.1: irq 18, io mem 0x54001000
[   81.686597] usb usb9: configuration #1 chosen from 1 choice
[   81.686767] hub 9-0:1.0: USB hub found
[   81.686819] hub 9-0:1.0: 1 port detected
[   82.441847] usb 8-1: new full speed USB device using ohci_hcd and address 2
[   82.453828] usb 8-1: configuration #1 chosen from 1 choice
root@dell-notebook:~# 

I am using a Kyocera KPC650 pcmcia card that works ok in winXP...

garyathome

If you are using gutsy you need to follow the how to from very beginning where it gives you the fix for it.

when you issue dmesg  you should see lines like :
```
[17186692.460000] usb 3-1: configuration #1 chosen from 2 choices
**[17186692.460000] cdc_acm 3-1:1.0: ttyACM0: USB ACM device**
[17186708.176000] usb 3-1: USB disconnect, address 4
[17186714.588000] usb 3-1: new full speed USB device using uhci_hcd and address
```
The  **ttyACM0** would be your identifier , device identifier always starts with"** tty **" and follows with ACM or USB with numeric value after that.
Try it from beginning and let me know what happened .

---

### Post by bigcat40 on 2007-11-04
I new to Linux and trying to set-up my Verizon 5700 card on a Dell e1505 with Gutsy. I started from the beginning of the how to and my card is still not being recognized. From reading the posts it seems that the kernel still doesn't recognize the card.When I run Dmesg after taking out the card I get this line:

[  988.228000] usb 1-2: USB disconnect, address 7

When I insert the card I get:
[ 1021.984000] usb 1-2: new full speed USB device using uhci_hcd and address 8
[ 1022.140000] usb 1-2: configuration #1 chosen from 1 choice

I never see anything about TTY. Any help would be greatly appreciated. 


Jeff

---

### Post by Mach1US on 2007-11-05
> **bigcat40 said:**
> I new to Linux and trying to set-up my Verizon 5700 card on a Dell e1505 with Gutsy. I started from the beginning of the how to and my card is still not being recognized. From reading the posts it seems that the kernel still doesn't recognize the card.When I run Dmesg after taking out the card I get this line:

[  988.228000] usb 1-2: USB disconnect, address 7

When I insert the card I get:
[ 1021.984000] usb 1-2: new full speed USB device using uhci_hcd and address 8
[ 1022.140000] usb 1-2: configuration #1 chosen from 1 choice

I never see anything about TTY. Any help would be greatly appreciated. 


Jeff
Which connection method do you use?
Are you using same connection interface for both machines ( PCMCI , USB , etc... ) ?  
Are both machines laptops ?
Have they ever been working with Feisty ?

And this are sites with earlier requested help for intel wireless issues.
[http://ubuntuforums.org/showpost.php?p=4265912&postcount=2](http://ubuntuforums.org/showpost.php?p=4265912&postcount=2)
[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)
[http://ubuntuforums.org/showpost.php?p=3888968&postcount=4](http://ubuntuforums.org/showpost.php?p=3888968&postcount=4)
[http://ubuntuforums.org/showpost.php?p=3372668&postcount=12](http://ubuntuforums.org/showpost.php?p=3372668&postcount=12)

---

### Post by Mach1US on 2007-11-08
Since USBSERIAL is part of default driver package included in Ubuntu i never needed and i haven't worked with a Franklin's ( [http://www.fklt.com/support.php](http://www.fklt.com/support.php) ) driver so i'm not sure how it handles the device .
> It appears when I run the Linux driver.
 At the laptop the CDU always appears as scsi0 and sda.
sda is an identifier for your Hard Drive , it is not your Wireless Device .
.
.
> [ 2161.009087] usb 2-1: USB disconnect, address 2
[ 2161.329429] scsi 2:0:0:0: rejecting I/O to dead device
[ 2219.599287] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 2219.765331] usb 2-1: configuration #1 chosen from 1 choice
Seeing this indicates USB device probem which can be either software or hardware.
To make sure it isn't conflicting with the evdo device disconnect all non essential peripherals   ( ideally everything except KVM )
and then tested again to isolate the problem.
Additionally try it with LIVE CD as this will eliminate any misconfigurations  of  the installation itself .
If it is a installation problem and you are not comfortable with recompiling the kernel  or at least patching it probably the easiest and quickest will be a fresh install .
Hope this helps.

---

### Post by srbeards on 2007-11-09
I have a Dell Wireless 5700 built-in mini card for Verizon in my Dell Laptop. I can setup the connection just fine, but any time I restart my system, the usbserial module does not start again. I can run the "sudo modprobe usbserial vendor=0x413c product=0x8114" command to get it to work again, but it is there any way to get the usbserial mod to start automaticly?

I ahve tried adding "usbserial vendor=0x413c product=0x8114" to the /etc/modules, which will succesfully start usbserial at startup, but it does not open the serial ports on the card, so ttyUSB0 is not available.

Any help would be great.

---

### Post by Ocyberbum on 2007-11-10
I got this working with gusty and my Samsung i760 (WM6) phone, after i did the 
"Gutsy changed USB handling so to re enable /proc/bus/usb/devices directory " , i rebooted and everything worked by default only changing the phone#@vzw. I also pay the 15month for the tethering plan.

thanks again, this script is awesome

---

### Post by MichiganBill on 2007-11-12
I had a similar experience to vmosorio. I connect to AT&T with a Razr V3 using wvdial. When I upgraded to Gutsy from Feisty it stopped working with error 16 (timeout).

As vmosorio found, it works after I changed the line of wvdial to be *99***1# instead of *99***3#. (With Feisty both worked.)

Also I discovered that with when I first used the new number (*99***1#) I was able to connect, but still nothing happened when I tried Firefox. I had to reboot, and then everything worked swimmingly. This is a new behaviour with Gutsy, with Feisty I never had to reboot.

Hope this helps!! (and thanks vmosorio!)

Bill

:KS

---

### Post by Mach1US on 2007-11-13
> **srbeards said:**
> I have a Dell Wireless 5700 built-in mini card for Verizon in my Dell Laptop. I can setup the connection just fine, but any time I restart my system, the usbserial module does not start again. I can run the "sudo modprobe usbserial vendor=0x413c product=0x8114" command to get it to work again, but it is there any way to get the usbserial mod to start automaticly?

I ahve tried adding "usbserial vendor=0x413c product=0x8114" to the /etc/modules, which will succesfully start usbserial at startup, but it does not open the serial ports on the card, so ttyUSB0 is not available.

Any help would be great.
Try loading it as a session command after all essentials are loaded .

---

### Post by jimbojones on 2007-11-13
> **srbeards said:**
> I have a Dell Wireless 5700 built-in mini card for Verizon in my Dell Laptop. I can setup the connection just fine, but any time I restart my system, the usbserial module does not start again. I can run the "sudo modprobe usbserial vendor=0x413c product=0x8114" command to get it to work again, but it is there any way to get the usbserial mod to start automaticly?

I ahve tried adding "usbserial vendor=0x413c product=0x8114" to the /etc/modules, which will succesfully start usbserial at startup, but it does not open the serial ports on the card, so ttyUSB0 is not available.

Any help would be great.

I have a Dell5700 in an XPS1210, I have "usbserial vendor=..." in my /etc/modules file and my card loads at start up.  Did you blacklist the airprime driver?  I wonder if that could interfere

---

### Post by gnubunny on 2007-11-15
If you have a HTC Mogul/6800 or HTC Touch/6900, here is how i got them to work as a modem with ubuntu. Sadly I did not go with tether via wire. But i was able to do it via a bluetooth connection. I wrote a pdf file which gives step by step instructions on how to do it. I wrote the pdf for work but figure it will be more useful here.

---

### Post by frainbart on 2007-11-20
> **scorpio_digit said:**
> I'm using a Razr v3m with Verizon. I had this working in XP. Here's the output:
[INDENT]root@nicole:/# wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&CpG.}'}"}(}"tP~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Oct 16 12:55:25 2007
--> Pid of pppd: 7359
--> Using interface ppp0
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> pppd: H[06][06][08]p
--> [06][08]
--> Disconnecting at Tue Oct 16 12:55:28 2007
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
[/INDENT]
And here's the wvdial.conf file:
[INDENT][Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = **********@vzw3g.com
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP[/INDENT]

I have the same phone with Verizon service. I looked up the USB information like the product ID and port using the Hardware Information under System Preferences after plugging in my phone (It shows up as Motorola V3c, check the advanced tab). I followed the directions on [www.hacktherazr.com](www.hacktherazr.com) to disable EVDO and setup dial up networking. I was getting the same error about authenticating. I fixed it by just removing the "@vzw3g.com". Just use your phone number for the Username. I do not have a broadband access plan, my connection just uses minutes (see the website above) so watch out if you are during peak time. I suppose this is slower than EVDO but 1x is still fast enough for web surfing.

---

### Post by peacepipejv on 2007-11-20
I just want to mention that a reboot after modifying gedits may help. I don't know if it goes w/out saying but thats what solved any issues I had. Also fyi, this setup with pc5750 had no negative effects on internet sharing via ethernet and firestarter. Just thought Id let everyone know. YAY!

---

### Post by mastercomputerwizard on 2007-11-22
Does anyone happen to know what to use for username and password for U.S. Cellular?
[http://www.uscc.com/uscellular/SilverStream/Pages/uscellular.html](http://www.uscc.com/uscellular/SilverStream/Pages/uscellular.html)

Thanks!

---

### Post by peacepipejv on 2007-11-24
> **CanyonDrifter said:**
> Recent letter to Sierra support:

   My card will be run over by a truck as soon as I can possibly get something else figured out, 

Can I have it instead?:)

---

### Post by MarcRJacobs on 2007-11-27
I just wanted to say "THANKS" for this great thread.  I am running a Toshiba P105-S9337 with Kubuntu 7.10, and with your help, a Verizon PC5750.  The instructions worked like a dream, except for a needed reboot after the Gutsy instructions are followed.  Now that this is working, can someone tell me how to setup KPPP, so my system is a little friendlier for the family?
Thanks

---

### Post by Holleywood on 2007-12-05
This is the end of my dmesg report:
[ 3020.448000] usb 2-1: USB disconnect, address 2
[ 3030.856000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 3031.020000] usb 2-1: configuration #1 chosen from 1 choice
[ 3031.028000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3031.028000] usb-storage: device found at 3
[ 3031.028000] usb-storage: waiting for device to settle before scanning
[ 3036.028000] usb-storage: device scan complete
[ 3036.032000] scsi 3:0:0:0: Direct-Access     Motorola RAZRV3xx         2.31 PQ: 0 ANSI: 2
[ 3036.036000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 3036.036000] sd 3:0:0:0: Attached scsi generic sg2 type 0

I read through the suggested post, but I need help please. What must I do to achieve the acm or usb address I need? Thanks

---

### Post by Mach1US on 2007-12-06
You must blacklist the AIRPRIME driver.
The very bigining of this how-to will tell you exactly how to do it.
:)

---

### Post by lazyart on 2007-12-10
What kind of throughput are you getting with this? I was under the impression that the airprime driver is more efficient than usbserial-- it's what I use with my Sprint mobile broadband card...

---

### Post by Mach1US on 2007-12-10
I'm glad somebody asked for that , in fact the Airprime is a more recent development then usbserial.
I have tried both drivers and basically they have performed same using Verizon Evdo Card .
Where i was testing i was getting between 1.2 and 1.4Mb/s using either driver.
Basically both of them offer more throughput than wireless broadband can dish out with some marginal advantage in favor of Airprime which is capable of handling bigger fames (higher MTU) , reducing the need to fragment certain data transmissions thus saving on the frame overhead.
Thats in theory but in reality  it plays bigger role in LANs which tipically have port speeds of 100 and 1000 Mb so additional framing overhead amounts to some real bandwidth .
Actually inherently all wireless connections have the biggest bandwidth loses due retransmissions so in many cases it is more desirable to use smaller frames which requires to retransmit only small parts that have been lost as oppose to having to retransmit the entire segment.
           Aside from theorizing i'm very interested on how did you set up your Evdo card.
In Feisty i use to get automatic usbserial association which presented me with device identifier and in turn allowed me to configure Wvdial to use the device.
To use Airprime in Feisty i had to actually patch the kernel.
With the arrival of Gutsy my card was automatically associated with Airprime but it didn't give me a device identifier, without which i couldn't set up wvdial so after few days of trying all sorts of reverse engineering i found the way to get good old usbserial with it's identifiers.
            Anyway i would be very appreciative if you could point me to some material on seating up Gutsy directly with Airprime.
Do you know it it works with cards other then Sprint EVDO ?

---

### Post by lazyart on 2007-12-11
I started using my aircard (Novatel U727) about week before Gutsy was released and it did involve patching the airprime.c file to include the device and vendor IDs.

Once done I used KPPP to create the connection.  The method is outlined [here]("http://samat.org/weblog/20070128-sprints-evdo-mobile-broadband-on-ubuntu-linux.html") for patching, then use the KPPP setup outlined in Sprint's own documentation, found [here (PDF)]("http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf").  If usbserial is giving the same performance as airprime, then Sprint's directions are all you need.

Mate your device with a snazzy udev rule and it will connect automagically when the device is plugged in.

---

### Post by Mach1US on 2007-12-12
You make me want to hear about it more .:shock:,what do you mean undev rule ?
That is actually my problem too , Gutsy has changed the usb handling so now simply running dmesg to get a device designation doesn't work :(
Hopefully somebody will realize that Linux systems need network connection just like the rest of the bunch.
Sadly it probably won't  come from manufactures or even service providers, the only hope we have is that guys from outfits like Automatix or Easy Ubuntu gonna  write something to help us cope with industry negligence

---

### Post by tlpayne on 2007-12-13
Thanks for all the input and how to (s) I have a Kyocera 650 air card and  was wanting to use ubuntu on my laptop. This made life alot easier. One problem tho. If i have to disable my ethernet card, how am I, if possible, gonna share this connection to the rest of my network. My aircard is the only source of Broadband in my area and its my only link to the Internet from my house. 

I may have missed something in this thread, i will apologize now if I did. I did see how one person was able to share, he just didnt go into any details. 

Thanks!

---

### Post by Mach1US on 2007-12-13
You don't have to disable Ethernet card.
In fact you can use either your Ethernet card or your wi-fi to share the access to the internet for other wireless laptops.
There are are numerous how-to's on the subject, i do it through VMappliance called "Internet Connection Sharing Appliance" :
[http://www.vmware.com/appliances/directory/395](http://www.vmware.com/appliances/directory/395)

Instructions are for MS 2000 but you get the idea.
[http://www.vmware.com/support/reference/win/connex_share_w2k.html](http://www.vmware.com/support/reference/win/connex_share_w2k.html)

It takes little tweaking but once you get it done it is bulletproof and this way you can use your wi-fi and ethernet card normally and simply with a click of a mouse on the vmware icon they can become internet gateways for the other computers

---

### Post by jhorner on 2007-12-17
Excellent walk through, thank you much to everyone.  My only input is that if you are using Kubuntu (with the KNetworkManager program), completely exit KNetworkManager or the EVDO card will never get the correct DNS settings.  Or atleast this was my experience.  Thanks again.

---

### Post by janik29 on 2007-12-21
Hi,

I am "Brand New" to Ubuntu and since I have installed it yesterday I absolutely love it!! What a great OS indeed.

I am not new to Unix and have quite a experience in Unix (except Linux) so I am trying out new things.

Here is my problem with using Motorola V770, LG Voyager and LG 8600 phone as modem with Ubuntu71.

I set it devices as in instruction on first chat and worked like a charm! I immediately connected via Motorola V770 by wvdial. Speed is not bad at all! And I tested out different web pages.

But LG phones are different story, both Voyager and 8600 did not work as phone modem.

Here errors I am getting:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Fri Dec 21 15:50:58 2007
WvDial<Notice>: Pid of pppd: 5908
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: &#1556;[06][08]
WvDial<*1>: pppd: &#1556;[06][08]
WvDial<*1>: pppd: &#1556;[06][08]
WvDial<*1>: pppd: &#1556;[06][08]
WvDial<*1>: pppd: &#1556;[06][08]
WvDial<*1>: Disconnecting at Fri Dec 21 15:51:06 2007
WvDial<*1>: The PPP daemon has died: Authentication error.
WvDial<*1>: We failed to authenticate ourselves to the peer.
WvDial<*1>: Maybe bad account or password? (exit code = 19)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 19)

Interesting thing I noted that Motorola V700 seems to dial #777 as unknown number with data connection while LG phones shows its dials to 3g 1x Data. I assume since LG are newer models, they are trying to access High Speed National Access which requires username/passwords provided by Verizon when you sign up Broadband Access service $59/month in US.

Anyone has tried to use LG phones, specially new ones like Voyager (LG10000 or LG8600) and has experienced the same error? I will appreciate any help!

Thanks and great job on Ubuntu!!! :)

---

### Post by janik29 on 2007-12-21
**Update:**

I did try to disable EVDO from following steps on LG phones but still are getting same (exit code = 19) error.

Here are steps to disable EVDO...

1) Press the Menu key (ok)
2) Push the zero key (0) seven times
3) Push the three key (3) for network select
4) Push the one key (1) for Mode Preference
5) Choose 1X Only or Digital Only Non Hybrid.

To re enable EV follow steps 1 - 4 and for step #5 choose Digital Only Hybrid

Btw my Motorola V710 (sorry for typo earlier) still works with my current wvdial.conf

Thanks

---

### Post by boriquajake on 2008-01-04
I am excited about getting this to work but when I attempt the first step (removing the "#" symbols from those lines and saving) I am told that I do not have permission to save. Any advice?

---

### Post by who_cares on 2008-01-04
You need to edit the config file with root privileges.

---

### Post by boriquajake on 2008-01-04
> **who_cares said:**
> You need to edit the config file with root privileges.

Sweet! How do I change my privilege level?  I am sorry to ask such a basic question.

Seriously, I have been screwing around with this forever. I have looked all over the "mountdevsubfs.sh" document for a way to change my privileges to no avail.

---

### Post by who_cares on 2008-01-04
either use
```
sudo nano wvdial.conf
```
or
```
gksudo gedit wvdial.conf
```

The second one lets you use gedit.

---

### Post by boriquajake on 2008-01-04
Who_Cares,

Thanks, I was able to procede. I am no stuck on this part:

> At the end of this output you will find your device witch will be represented like this: ttyACM0 or ttyUSB or similar , make note of it you will need it later.

I must have done something else wrong because nowhere in my output do I see anything that begins with tty.

---

### Post by boriquajake on 2008-01-05
Do you have any ideas as to why the device is not showing up?

---

### Post by Paul86fxr on 2008-01-14
I have a question: I dont understand how to type this line of code, the part that throws me is the "grep Vendor and the symbol before it, I dont know how to type it or what the symbol is telling me to type  this is the line "diff /proc/bus/usb/ devices devices "*" grep Vendor

Please assume I'm too stupid to even use a rotary telephone.
Thanks, Paul:)

---

### Post by NDH2008 on 2008-01-14
followed the instructions and this is the output, but it is not connecting...Thoughts?


nathan@nathan-laptop:~$ sudo wvdial
[sudo] password for nathan:
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Mon Jan 14 14:31:20 2008
WvDial<Notice>: Pid of pppd: 5989
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]
WvDial<*1>: local  IP address 70.14.251.154
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]
WvDial<*1>: remote IP address 68.28.177.69
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]
WvDial<*1>: primary   DNS address 68.28.178.91
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]
WvDial<*1>: secondary DNS address 68.28.186.91
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#1560;[06][08]

---

### Post by rabbito on 2008-01-21
Does this process fully work for a Blackberry 8703e? I just got it set up but when it gets to the 'Waiting for Carrier' i get a no dial tone then disconnects. Does that mean i set something up wrong or is there something i need to tweak? i have verizon by the way if that helps.

Let me know if i need to post anything to help with my problem

**EDIT: posted for 8303e but it should have been for a 8703e

---

### Post by Mach1US on 2008-01-21
> **Paul86fxr said:**
> I have a question: I dont understand how to type this line of code, the part that throws me is the "grep Vendor and the symbol before it, I dont know how to type it or what the symbol is telling me to type  this is the line "diff /proc/bus/usb/ devices devices "*" grep Vendor

Please assume I'm too stupid to even use a rotary telephone.
Thanks, Paul:)

This symbol is located above RETURN key the symbok on the keybord looks similar to : but it is actually displayed as | , is most comonnly shared with \ (forward slash) so you will need to hold shift while you press it.

> **rabbito said:**
> Does this process fully work for a Blackberry 8303e? I just got it set up but when it gets to the 'Waiting for Carrier' i get a no dial tone then disconnects. Does that mean i set something up wrong or is there something i need to tweak? i have verizon by the way if that helps.

Let me know if i need to post anything to help with my problem
I have successfully set up couple Blackberrys ,all from Verizon.
If you get no dial tone most likely  your port settings (tty...) are mis configured  .Check dmesg and correct wvdial.conf

---

### Post by rabbito on 2008-01-21
Problem is when i used dmesg i did not get any post for anything tty...
mine is currently set for ttysl0 (would be curious to know what your blackberries defaulted to) which i got from running wvdialconf in the terminal. Is there a setting on the blackberry that needs to be enabled for internet to post? Sort of difficult as i dont have the laptop in front of me since i have been setting it up for my mom who has a blackberry. If there is another tty that works i will give it a try.

---

### Post by Mach1US on 2008-01-22
I don't remember which tty blackberry hardware uses ,but if i remember correctly you need to evdo enabled on the device beside the normal data service that the smart phones are usin, there is additional charge like 15 or something close to that for subscription to it, you need to call verizon and have them enable it.
It was some time ago so check if they changed it since.

---

### Post by rabbito on 2008-01-22
yeah the EVDO is enabled and i called and here is the wvdial.conf file:

[Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttySL0
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = <number>@vzw3g.com
Password = vzw
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Auto Reconnect = on
Carrier Check = no
[Dialer shh]
Init3 = ATM0
[Dialer pulse]
Dial Command = ATDP

anything look wrong?

---

### Post by Mach1US on 2008-01-22
It depends,check  if your dmesg output definitely  points to ttySL0 as your blackberry port.

---

### Post by rabbito on 2008-01-22
okay, i will report back tomorrow afternoon with what dmesg gives. how do you copy lines from the terminal to the text editor? not essential but would be the easiest.

MACH1US thank you for helping out and i will post my findings tomorrow:)

---

### Post by rabbito on 2008-01-22
here is the last part of what dmesg gives:

[ 1436.356000] NET: Registered protocol family 10 
[ 1436.356000] lo: Disabled Privacy Extensions 
[ 1436.356000] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 1436.356000] ADDRCONF(NETDEV_UP): eth1: link is not ready 
[ 2046.128000] usb 3-2: new full speed USB device using uhci_hcd and address 2 
[ 2046.344000] usb 3-2: configuration #1 chosen from 1 choice 
[ 2046.516000] usbcore: registered new interface driver berry_charge 
[ 2076.140000] usb 3-2: USB disconnect, address 2 
[ 2076.380000] usb 3-2: new full speed USB device using uhci_hcd and address 3 
[ 2076.540000] usb 3-2: configuration #1 chosen from 1 choice 


i dont see anything that has tty attached to it so i am not sure what is going on. any tips would be helpfull. i followed the steps posted on how to set up EVDO as a modem in the tips section of the forums. Do i have to have xmblackberry installed for this to work? i have seen other tutorials and that install xmblackberry but i am not sure if this is required or not.

---

### Post by rabbito on 2008-01-23
tried using the phone number as the password instead of vzw but that did not work either. Guess i can try installing xmBlackberry if there is no other way. Suggestions anyone?

---

### Post by stackable1 on 2008-01-24
Thanks - worked great on a Dell Latitude 620 runing Gutsy using a Versions PC5750! 
Now as I'm a Linux newbie how do I safely disconnect the Connecton and unmount or power down the PC5750 PCMCIA card? 

Thanks again - now for my next trick - make my VPN connection to a SonicWall 2040 firewall that requires their Global VPN client to connect! only runs on Windows as far as I know.. Maybe WINE don't know... the tunnel adaper will probably need kernal mode access. 

Once I do this I can be Windows Free on my Laptop at least - shh don't tell big M - I'm a professional Windows Systems Admin 12+ years but Vista was the last straw (Vista -YUCK! what complete trash!) Ubuntu ROCKS!

---

### Post by boriquajake on 2008-01-24
Dude, I am to the point now where I will pay anyone that can help me get my freaking EVDO card to work. I have tried to follow the steps here (I am very grateful for this thread, by the way) but I am too dense to make it work. If anyone thinks they can help me get my Kyocera KPC650 EVDO card working I will gladly pay for your time.  That is pretty much my last obstacle to being 100% linux.

---

### Post by rabbito on 2008-01-24
> **boriquajake said:**
> Dude, I am to the point now where I will pay anyone that can help me get my freaking EVDO card to work. I have tried to follow the steps here (I am very grateful for this thread, by the way) but I am too dense to make it work. If anyone thinks they can help me get my Kyocera KPC650 EVDO card working I will gladly pay for your time.  That is pretty much my last obstacle to being 100% linux.

I am with you. Once i get my BB 8703e working there really is not anything holding me back from complete Linux. Have you tried the simpler  'wvdialconf' ---> wvdial ? it actually set up most of the proper settings for me but i still can not connect. Never know though it might for you and i think there is another post that explains a little more about it.

---

### Post by boriquajake on 2008-01-24
OK, I am still hammering away at this like and idiot. When I reach this point in the instructions:
```
   diff /proc/bus/usb/devices devices | grep Vendor
```

I get this output:

> root@jake-V2000:~#    diff /proc/bus/usb/devices devices | grep Vendor
diff: /proc/bus/usb/devices: No such file or directory


What am I doing wrong?

---

### Post by Mach1US on 2008-01-24
Guys,
Rabbito and  boriquajake  

I have changed the bigging of the how to just for you two, follow the steps 1 through 5 in the bigging of this how to .
boriquajake  needs to enable /proc/bus/usb/devices devices , just follow steps 1-5 .
Rabbito yo need to block Airprime from messig with your identifiers, you can also fix it by correctly following steps 1-5.
Sorry for slow reply time but we are swamped at work , however you do not need to pay anybody to do it  , by doing it yourself first of all you learn new linux stuff second you can scrap it and recreated from scratch without the fear that every time you crash it it will cost you to get it back . 
You guys almost there.

And for others wit kyocera cards check the following post
[http://ubuntuforums.org/showpost.php?p=4198067&postcount=2](http://ubuntuforums.org/showpost.php?p=4198067&postcount=2)

---

### Post by boriquajake on 2008-01-24
> **Mach1US said:**
> Guys,
Rabbito and  boriquajake  

I have changed the bigging of the how to just for you two, follow the steps 1 through 5 in the bigging of this how to .
boriquajake  needs to enable /proc/bus/usb/devices devices , just follow steps 1-5 .
Rabbito yo need to block Airprime from messig with your identifiers, you can also fix it by correctly following steps 1-5.
Sorry for slow reply time but we are swamped at work , however you do not need to pay anybody to do it  , by doing it yourself first of all you learn new linux stuff second you can scrap it and recreated from scratch without the fear that every time you crash it it will cost you to get it back . 
You guys almost there.

And for others wit kyocera cards check the following post
[http://ubuntuforums.org/showpost.php?p=4198067&postcount=2](http://ubuntuforums.org/showpost.php?p=4198067&postcount=2)

Thank you so much for your reply. I know that time spent here is volunteer time. 

I had already completed steps 1-5, I thought. I will do them again to make sure I didn't screw them up.

---

### Post by boriquajake on 2008-01-24
I went back and checked steps 1-5 and made sure I had done them. All seems to go just fine until it is time for step where I am to ```
 cat /proc/bus/usb/devices > devices
```

When I do that the output is:
> cat: /proc/bus/usb/devices: No such file or directory


What do you suggest?

---

### Post by Mach1US on 2008-01-24
it means  you did not successfully enabled this directory .
It is  important to do all 5 steps without getting any errors.
 Now before you start type in the terminal :
sudo -i
and then put your password and do all 5 steps again, this will allow you to do all those steps as a root.

---

### Post by nowhere@cox.net on 2008-01-25
Hi all,

I have a T61 with a fresh install of Gutsy 64. I have a Novatel U727 from Sprint and I cannot get it to connect. This is what I tried so far?

Boot, plug it in, check dmesg |grep acm and I get nothing
dmesg |grep ttyUSB and I get nothing.

Boot + modprobe airprime, lsmod shows airprime on usbcore line, dmesg |grep acm =nothing dmesg |grep ttyUSB = nothing

Boot, Follow steps 1-5, dmesg |grep acm = nothing, dmesg |grep ttyUSB = nothing, dmesg |grep ACM = nothing.

No point in continuing since I don't have a device name to give the dialer. 

Anyone know what's going on?

If I check /var/log/messages I do get a line
python[5877]: segfault at ...buncha 0's ... rip ... rsp ... error 4 
every time I insert the device.


Thanks,
Eric

---

### Post by Mach1US on 2008-01-25
You need to _BLACKLIST_ Airprime to force kernel in to using usbserial.
Airprime in gutsy wont give you those identifiers.
I'll check outputs of my own lsmod but i think with Airprome properly blacklisted it should come back with usbserial .
Make sure you are not doing anything else that would enable it back again.

Additionally make sure that your hardware does not need additional drivers outside those included in latest kernel  or require some other dependencies .

---

### Post by nowhere@cox.net on 2008-01-25
Thanks for the quick reply. I did follow steps 1-5 so airprime should be blacklisted. lsmod|grep air returns nothing.

I have no idea how to determine if the U727 needs additional drivers. I should note that it has a small flash drive imbedded as well as a microSDslot (with no card installed). I do get the pop up automount readonly stuff for the mini drive with Sprint/Novatel stuff on it and I do see entrys in dmesg for the microSD reader.

At this point there are no ttyUSB entries in dmesg. HOWEVER, if I eject the mini readonly flash drive, then check dmesg, there are now 4 ttyUSB's listed (0-4). But still no ttyACM's and kppp cannot query the modem on any of the ttyUSB's.

This help diagnose any?

Thanks!
Eric

---

### Post by nowhere@cox.net on 2008-01-25
Ok I got a connection! The U727 seems exceptionally sensitive to the order in which you do things. I have already followed this HOWTO's steps 1-5 to blacklist airprime. Next I need to connect the USB modem, then eject the CD (readonly flashdrive) that is automounted. Then:
```
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100
```

Then I am able to query the modem on /dev/ttyUSB0. I had to be careful since there were also /dev/tty/ttyUSB0 devices listed in kppp.

I am in the process of running dslreports speed test but I had to dl java plugins and such and the 22MB required is taking 10 minutes to dl so I suspect the speed is not too good :-D

Next stop will be a speed tweaking HOWTO.

I hope this helps anyone else with this particular device get connected!

Eric

---

### Post by boriquajake on 2008-01-25
> At the end of this output you will find your device witch will be represented like this: ttyACM0 or ttyUSB or similar , make note of it you will need it later.

Wow, I think I am finally making progress here. The only thing that sucks is that I have no idea what I am doing, I am just blindly following instructions. :-)

Anyway my output for this instruction:
```
dmesg
```

was this:

> bus registered, assigned bus number 4
[ 2090.552000] ohci_hcd 0000:06:00.0: irq 16, io mem 0x54000000
[ 2090.636000] usb usb4: configuration #1 chosen from 1 choice
[ 2090.636000] hub 4-0:1.0: USB hub found
[ 2090.636000] hub 4-0:1.0: 1 port detected
[ 2090.740000] PCI: Enabling device 0000:06:00.1 (0000 -> 0002)
[ 2090.740000] ACPI: PCI Interrupt 0000:06:00.1[B] -> GSI 17 (level, low) -> IRQ 16
[ 2090.740000] PCI: Setting latency timer of device 0000:06:00.1 to 64
[ 2090.740000] ohci_hcd 0000:06:00.1: OHCI Host Controller
[ 2090.740000] ohci_hcd 0000:06:00.1: new USB bus registered, assigned bus number 5
[ 2090.740000] ohci_hcd 0000:06:00.1: irq 16, io mem 0x54001000
[ 2090.824000] usb usb5: configuration #1 chosen from 1 choice
[ 2090.824000] hub 5-0:1.0: USB hub found
[ 2090.824000] hub 5-0:1.0: 1 port detected
[ 2092.260000] usb 4-1: new full speed USB device using ohci_hcd and address 2
[ 2092.472000] usb 4-1: configuration #1 chosen from 1 choice
jake@jake-V2000:~$ 


The thing that confuses me is that nowhere is there anything looks like ttyAMCO or ttyUSB. Where did I mess up?

Anyway, I kept on going even though I did not see the output I was looking for.

I coded:```
   diff /proc/bus/usb/devices devices | grep Vendor
```

and this is what came up:

> jake@jake-V2000:~$    diff /proc/bus/usb/devices devices | grep Vendor
< P:  Vendor=0000 ProdID=0000 Rev= 2.06
< P:  Vendor=0000 ProdID=0000 Rev= 2.06
< P:  Vendor=0c88 ProdID=17da Rev= 0.00


Then as I attempted to follow this:

```
 modprobe usbserial vendor=0x1234 product=0x5678
```

I got this:

> jake@jake-V2000:~$ modprobe usbserial vendor=0x0c88 product=0x17da
FATAL: Error inserting usbserial (/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted

So there it is, I have laid out my ignorance in all of its glory.

---

### Post by rabbito on 2008-01-26
seems to only get worse, here is my dmesg i get AFTER following steps 1-5:


[  169.164000] CCMP: decrypt failed: STA=00:13:46:fe:a9:ad
[  175.748000] printk: 7 messages suppressed.
[  175.748000] CCMP: decrypt failed: STA=00:13:46:ee:91:05
[  179.748000] printk: 1 messages suppressed.
[  179.748000] SoftMAC: Open Authentication completed with 00:13:46:ee:91:05
[  190.012000] printk: 4 messages suppressed.
[  192.544000] printk: 4 messages suppressed.
[  203.052000] printk: 22 messages suppressed.
[  210.184000] printk: 2 messages suppressed.
[  221.292000] printk: 1 messages suppressed.
[  239.860000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  240.024000] usb 3-1: configuration #1 chosen from 1 choice
[  240.164000] usbcore: registered new interface driver berry_charge

   diff /proc/bus/usb/devices devices | grep Vendor gives:
 Vendor=0fca ProdID=0001 Rev= 1.04

Here are my current blacklisted:

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

#Block Airprime driver to force kernel to use usbserial
blacklist airprime

**edit

rebooted and ran everything from root steps 1-5 and this is the dmesg output (bottom of it anyways):

[  130.300000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  130.460000] usb 3-1: configuration #1 chosen from 1 choice
[  130.564000] usbcore: registered new interface driver berry_charge
[  137.932000] printk: 1 messages suppressed.
[  137.932000] SoftMAC: Open Authentication completed with 00:13:46:ee:91:05

---

### Post by Mach1US on 2008-01-27
> **boriquajake said:**
> Wow, I think I am finally making progress here. The only thing that sucks is that I have no idea what I am doing, I am just blindly following instructions... 


> **rabbito said:**
> seems to only get worse, here is my dmesg i get AFTER following steps 1-5...

Make sure that when you doing 1-5 the card isn't inserted in at any time until just before dmesg.

previous post may help you to get the concept:
[http://ubuntuforums.org/showpost.php?p=4205671&postcount=153](http://ubuntuforums.org/showpost.php?p=4205671&postcount=153)

---

### Post by rabbito on 2008-01-28
thanks MACH1US, i will take a look at it. I will have a chance to work on the laptop again on wednesday so i will report back then. I have done a clean install of 7.10 in case all of my various attempts and methods to get it working has caused problems. I will also follow the post that you referred to. thanks again

---

### Post by s1m0n13 on 2008-01-28
MACH1US,  i'm trying to use my MotoQ as a modem.  I followed your instructions except I get the following when performing a dmesg w/ the phone plugged in over usb.

bad CDC descriptors

It does not return any info about the modem assignment (e.g. ttyACM0 or ttyUSB)

Thoughts?

---

### Post by boriquajake on 2008-01-28
Mach1US,

I started over from the beginning, meaning I even reversed the edits to the text files so all was as before I began. ThenI went back and redid everything making sure that I did not plug in the EVDO card until just before dmseg, and the output for dmseg still did not show anything like ttyACM0 or ttyUSB. I even copied the entire output and pasted into a text file so  I could search for anything resembling either option.

Even though I couldn't find what I thought should be there I continued on with the rest of the instructions. (This is a well done guide, I was able to understand each step, I think) 

All seemed to be fine until I got to the last step:

```
wvdial
```

I get:
> jake@jake-V2000:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttyACM0: No such file or directory
WvDial<Err>: Cannot open /dev/ttyACM0: No such file or directory
WvDial<Err>: Cannot open /dev/ttyACM0: No such file or directory


I am absolutely sure that I rebooted when the instructions said to reboot and that I did not plug in the card until directed, but obviously I did something else equally wrong. Any ideas?

---

### Post by Mach1US on 2008-01-31
It actually performs as designed,unfortunately.
With your configuration you need to obtain accurate tty... identifier to properly set dialing rules.
By simply pointing to a ttyACM0 you instructing wvdial to use nonexistent device and that is why it is returning with that message.
You need to do some troubleshooting,make sure device and its connections are performing as designed by running the setup on different OS like Mac or Windows using cell-service providers software.
Once you have absolutely confirmed all the hardware is working properly  check other posts , google and such to find an additional drivers or dependencies for your device that would enable or allow it to communicate and assign proper "ttyxxx"  identifiers.
Alternatively you can find a local LUG (Linux User Group) and attend meting where you can get some opinions and advice from their own experts, this guys are always helpful and they really know their stuff .   
       And lastly,  not all hardware is guaranteed to work with Linux, it largely depends on chipset used bythe device  manufacturers, so if you really need it you may have settle to run Linux as a virtual machine shearing the connection with other host system that is compatible with your hardware or switch to one of the EVDO cards or phones known to be working with Linux.
This thread mentions lots of equipment from broad range service providers that have been tested and proven working, the one i'm currently using is Verizons PC5750 which takes about 10 min to set it up ,does not need anything else , it simply just works.
Hope this helps.

---

### Post by G_Allen on 2008-01-31
Just in case anyone is looking I have the Verizon Wireless UM150 USB EVDO card and I followed these instructions and got it working GREAT!!  Thanks for the post as a newbie to Ubuntu/Linux command lines I never would have figured this out for myself!!

---

### Post by icebergwtq on 2008-02-02
> With your evdo card removed you can do it by typing following in the terminal :


Unfortunately, I have a Lenovo x61, and the Sierra 5725 card is embedded, so I can't remove it.

Any alternate suggestions?  I've tried everything possible to get this card working in Gutsy, with no luck.  In fact, I've probably tried so many things I've screwed something up.  Unfortunately, I'm a novice, so I don't know what I might have broken, or how to find and fix it.

Any help would be much appreciated.  I've solved every other wish list item I had in my transfer from Windows - got Quicken 2007, Worden Telechart, Pretty Good Solitaire, and even RoboForm running flawlessly, as well as sound and standard WiFi.  But I really, really need EVDO. 

Thanks for whatever you can offer.

:confused

---

### Post by icebergwtq on 2008-02-02
> With your evdo card removed you can do it by typing following in the terminal :


Unfortunately, I have a Lenovo x61, and the Sierra 5725 card is embedded, so I can't remove it.

Any alternate suggestions?  I've tried everything possible to get this card working in Gutsy, with no luck.  In fact, I've probably tried so many things I've screwed something up.  Unfortunately, I'm a novice, so I don't know what I might have broken, or how to find and fix it.

Any help would be much appreciated.  I've solved every other wish list item I had in my transfer from Windows - got Quicken 2007, Worden Telechart, Pretty Good Solitaire, and even RoboForm running flawlessly, as well as sound and standard WiFi.  But I really, really need EVDO. 

Thanks for whatever you can offer.

:confused:

---

### Post by icebergwtq on 2008-02-02
> With your evdo card removed you can do it by typing following in the terminal :


Unfortunately, I have a Lenovo x61, and the Sierra 5725 card is embedded, so I can't remove it.

Any alternate suggestions?  I've tried everything possible to get this card working in Gutsy, with no luck.  In fact, I've probably tried so many things I've screwed something up.  Unfortunately, I'm a novice, so I don't know what I might have broken, or how to find and fix it.

Any help would be much appreciated.  I've solved every other wish list item I had in my transfer from Windows - got Quicken 2007, Worden Telechart, Pretty Good Solitaire, and even RoboForm running flawlessly, as well as sound and standard WiFi.  But I really, really need EVDO. 

Thanks for whatever you can offer.

:confused

---

### Post by icebergwtq on 2008-02-02
I am trying my damnedest to post a reply to the original post, but this forum, like every other damned think linux, is neither simple, straightforward, obvious, or sensible.  Everything I try shunts my post off to this weird little corner.

To hell with it.

I give up.

---

### Post by icebergwtq on 2008-02-02
Sigh.  Okay, I'm an idiot.  Is there some way I can remove all but one of the dupe posts, and the outraged screech?

:(

---

### Post by Mach1US on 2008-02-03
:-P:-P:-P Don't worry we all have been there , this is actually how this forum  was suppose to work .
If you want to edit any of your posts simply log in ,click on EDIT, located on right bottom of each post (brown rectangle with white lettering ) and simply change any parts to your likings.
As far as your build in EVDO card take a Tylenol or two and  try this tutorial:
[http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/](http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/)
Or if you are using ATT this can be more accurate for you:
[http://ubuntuforums.org/showpost.php?p=3236731&postcount=2](http://ubuntuforums.org/showpost.php?p=3236731&postcount=2) 
Let me know if you get stuck.

For the MOTO Q posts earlier this looks like solution to the driver problem you have had .
[http://ubuntuforums.org/showpost.php?p=3968282&postcount=1](http://ubuntuforums.org/showpost.php?p=3968282&postcount=1)

---

### Post by Carton on 2008-02-04
I followed the tutorial but when I tried to connect it told me the modem was not responding.  I'm new and have no idea what to do now any help will be appreciated.

---

### Post by Mach1US on 2008-02-04
> **Carton said:**
> I followed the tutorial but when I tried to connect it told me the modem was not responding.  I'm new and have no idea what to do now any help will be appreciated.

Try to post the exact message you are getting, and explanation on exactly when it is happening .

---

### Post by txhellkat138 on 2008-02-04
This same howto is what we have on sprint.com for our customers and it also works for most sprint phone as modem phones.

---

### Post by Carton on 2008-02-04
luke@luke-laptop:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.


That is what is happening I'm using a Air Card 595u

---

### Post by Mach1US on 2008-02-04
The one on sprint site has been mentioned few times in previous posts to this thread , unfortunately it has not been updated recently to work with Gutsy.
Nevertheless is well constructed paper especially for people that feel more comfortable with graphical way of doing things like KPPP.

And for Carton you are getting classic at that point
```
Cannot get information for serial port.
```
It basically means you have not gotten infamous tty identifier or one in your wvdial.conf is different than the one from dmesg  .
Just in case take your card out , put it back in and post the dmesg output.

---

### Post by Carton on 2008-02-04
I saw that but couldn't figure out how to get the kpp program up

---

### Post by Mach1US on 2008-02-04
see above post and like i'v posted before it has not been updated for Gutsy so you need to do your home work here, get proper identifier and than i can send to KPPP configuration posts.

---

### Post by Carton on 2008-02-04
[   17.686157] CPU: Physical Processor ID: 0
[   17.686159] CPU: Processor Core ID: 1
[   17.686242] AMD Turion(tm) 64 X2  stepping 02
[   17.689916] Brought up 2 CPUs
[   18.585804] migration_cost=278
[   18.585755] NET: Registered protocol family 16
[   18.585838] ACPI: bus type pci registered
[   18.585844] PCI: Using configuration type 1
[   18.586818] ACPI: EC: Look up EC in DSDT
[   18.588974] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[   18.599576] ACPI: System BIOS is requesting _OSI(Linux)
[   18.599579] ACPI: Please test with "acpi_osi=!Linux"
[   18.599580] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   18.599886] ACPI: Interpreter enabled
[   18.599890] ACPI: (supports S0 S3 S4 S5)
[   18.599906] ACPI: Using IOAPIC for interrupt routing
[   18.610714] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[   18.610768] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.610776] PCI: Probing PCI hardware (bus 00)
[   18.611941] PCI: Transparent bridge - 0000:00:10.0
[   18.611971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.612074] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   18.612115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   18.612146] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   18.703356] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 22 23) *0, disabled.
[   18.703554] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 22 23) *10
[   18.703748] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 *10 11 14 15)
[   18.703942] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[   18.704137] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
[   18.704334] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *11
[   18.704529] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
[   18.704726] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 22 23) *0, disabled.
[   18.704924] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 22 23) *10
[   18.705128] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 22 23) *11
[   18.705327] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 22 23) *11
[   18.705527] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 22 23) *7
[   18.705735] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 22 23) *11
[   18.705941] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 22 23) *0, disabled.
[   18.706143] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 22 23) *0, disabled.
[   18.706344] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 22 23) *0, disabled.
[   18.706544] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 22 23) *0, disabled.
[   18.706753] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 22 23) *5
[   18.706959] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 22 23) *0
[   18.707056] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.707073] pnp: PnP ACPI init
[   18.707082] ACPI: bus type pnp registered
[   18.710707] pnp: PnP ACPI: found 11 devices
[   18.710709] ACPI: ACPI bus type pnp unregistered
[   18.710774] PCI: Using ACPI for IRQ routing
[   18.710777] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.710880] NET: Registered protocol family 8
[   18.710882] NET: Registered protocol family 20
[   18.710962] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   18.710966] hpet0: 3 32-bit timers, 25000000 Hz
[   18.712026] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   18.712032] pnp: 00:02: ioport range 0x1000-0x107f has been reserved
[   18.712035] pnp: 00:02: ioport range 0x1080-0x10ff has been reserved
[   18.712038] pnp: 00:02: ioport range 0x1400-0x147f has been reserved
[   18.712042] pnp: 00:02: ioport range 0x1480-0x14ff has been reserved
[   18.712045] pnp: 00:02: ioport range 0x1800-0x187f has been reserved
[   18.712048] pnp: 00:02: ioport range 0x1880-0x18ff has been reserved
[   18.712051] pnp: 00:02: ioport range 0x2000-0x203f has been reserved
[   18.712376] PCI: Bridge: 0000:00:02.0
[   18.712378]   IO window: disabled.
[   18.712381]   MEM window: b3000000-b30fffff
[   18.712384]   PREFETCH window: disabled.
[   18.712386] PCI: Bridge: 0000:00:03.0
[   18.712389]   IO window: 4000-4fff
[   18.712392]   MEM window: b4000000-b7ffffff
[   18.712395]   PREFETCH window: d0000000-d01fffff
[   18.712398] PCI: Bridge: 0000:00:10.0
[   18.712400]   IO window: disabled.
[   18.712404]   MEM window: b8000000-b80fffff
[   18.712407]   PREFETCH window: disabled.
[   18.712417] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.712424] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   18.712432] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   18.712486] NET: Registered protocol family 2
[   18.713604] Time: hpet clocksource has been installed.
[   18.761645] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   18.762092] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   18.764444] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.765214] TCP: Hash tables configured (established 131072 bind 65536)
[   18.765218] TCP reno registered
[   18.777702] checking if image is initramfs... it is
[   19.443583] Freeing initrd memory: 7747k freed
[   19.448803] Simple Boot Flag at 0x36 set to 0x1
[   19.449419] audit: initializing netlink socket (disabled)
[   19.449430] audit(1202156232.356:1): initialized
[   19.451646] VFS: Disk quotas dquot_6.5.1
[   19.451701] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.451789] io scheduler noop registered
[   19.451792] io scheduler anticipatory registered
[   19.451794] io scheduler deadline registered
[   19.451893] io scheduler cfq registered (default)
[   19.451913] Boot video device is 0000:00:05.0
[   19.669711] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   19.669734] assign_interrupt_mode Found MSI capability
[   19.669738] Allocate Port Service[0000:00:02.0:pcie00]
[   19.669802] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   19.669823] assign_interrupt_mode Found MSI capability
[   19.669825] Allocate Port Service[0000:00:03.0:pcie00]
[   19.695439] Real Time Clock Driver v1.12ac
[   19.695633] hpet_resources: 0xfed00000 is busy
[   19.695671] Linux agpgart interface v0.102 (c) Dave Jones
[   19.695674] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.696760] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.696890] input: Macintosh mouse button emulation as /class/input/input0
[   19.696969] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.697258] i8042.c: Detected active multiplexing controller, rev 1.1.
[   19.697332] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.697337] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   19.697340] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   19.697343] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   19.697346] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   19.697612] mice: PS/2 mouse device common for all mice
[   19.697777] TCP cubic registered
[   19.697837] NET: Registered protocol family 1
[   19.698063] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.698074] Freeing unused kernel memory: 296k freed
[   19.703249] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.895441] AppArmor: AppArmor initialized<5>audit(1202156233.800:2):  type=1505 info="AppArmor initialized" pid=1260
[   20.902563] fuse init (API version 7.8)
[   20.906992] Failure registering capabilities with primary security module.
[   20.940919] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.940972] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.952997] ACPI: Thermal Zone [TZS0] (31 C)
[   20.958094] ACPI: Thermal Zone [TZS1] (34 C)
[   21.544761] usbcore: registered new interface driver usbfs
[   21.544785] usbcore: registered new interface driver hub
[   21.544813] usbcore: registered new device driver usb
[   21.545550] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.545926] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   21.545936] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 23
[   21.546098] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   21.546106] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   21.546261] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   21.546283] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xb0004000
[   21.572304] SCSI subsystem initialized
[   21.577710] libata version 2.21 loaded.
[   21.610738] usb usb1: configuration #1 chosen from 1 choice
[   21.610768] hub 1-0:1.0: USB hub found
[   21.610780] hub 1-0:1.0: 8 ports detected
[   21.678770] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   21.688958] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.688965] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.716399] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   21.716412] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 22
[   21.716595] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   21.716603] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   21.716659] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   21.716702] ehci_hcd 0000:00:0b.1: debug port 1
[   21.716707] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   21.716720] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000
[   21.716730] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.716827] usb usb2: configuration #1 chosen from 1 choice
[   21.716855] hub 2-0:1.0: USB hub found
[   21.716862] hub 2-0:1.0: 8 ports detected
[   21.822927] sata_nv 0000:00:0e.0: version 3.4
[   21.822943] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   21.823285] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 18
[   21.823295] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 18 (level, high) -> IRQ 18
[   21.823497] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   21.823644] scsi0 : sata_nv
[   21.823690] scsi1 : sata_nv
[   21.823766] ata1: SATA max UDMA/133 cmd 0x00000000000130b0 ctl 0x00000000000130a6 bmdma 0x0000000000013090 irq 18
[   21.823772] ata2: SATA max UDMA/133 cmd 0x00000000000130a8 ctl 0x00000000000130a2 bmdma 0x0000000000013098 irq 18
[   22.287733] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.295898] ata1.00: ATA-7: ST9160821AS, 3.BHD, max UDMA/100
[   22.295902] ata1.00: 312581808 sectors, multi 16: LBA48 
[   22.311887] ata1.00: configured for UDMA/100
[   22.431429] usb 2-3: new high speed USB device using ehci_hcd and address 2
[   22.573466] usb 2-3: configuration #1 chosen from 1 choice
[   22.623545] ata2: SATA link down (SStatus 0 SControl 300)
[   22.634299] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.BH PQ: 0 ANSI: 5
[   22.634504] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   22.634542] NFORCE-MCP51: chipset revision 241
[   22.634545] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   22.634553] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   22.634562]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:pio, hdb:pio
[   22.634572]     ide1: BM-DMA at 0x3088-0x308f, BIOS settings: hdc:pio, hdd:pio
[   22.634579] Probing IDE interface ide0...
[   22.634887] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 17
[   22.634897] ACPI: PCI Interrupt 0000:05:09.0[A] -> Link [LNK1] -> GSI 17 (level, high) -> IRQ 17
[   22.686770] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   22.686783] sd 0:0:0:0: [sda] Write Protect is off
[   22.686786] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.686800] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.686855] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   22.687074] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   22.686864] sd 0:0:0:0: [sda] Write Protect is off
[   22.686868] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.686881] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.686887]  sda: sda1 sda2 < sda5 >
[   22.739275] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.743282] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.888009] Attempting manual resume
[   22.888014] swsusp: Resume From Partition 8:5
[   22.888016] PM: Checking swsusp image.
[   22.888192] PM: Resume from disk failed.
[   22.901747] EXT3-fs: INFO: recovery required on readonly filesystem.
[   22.901752] EXT3-fs: write access will be enabled during recovery.
[   23.035109] usb 2-8: new high speed USB device using ehci_hcd and address 4
[   23.176662] usb 2-8: configuration #1 chosen from 1 choice
[   23.177303] usbcore: registered new interface driver libusual
[   23.180866] Initializing USB Mass Storage driver...
[   23.231028] Probing IDE interface ide1...
[   23.483097] usb 1-5: new low speed USB device using ohci_hcd and address 2
[   23.690844] usb 1-5: configuration #1 chosen from 1 choice
[   23.693720] scsi2 : SCSI emulation for USB Mass Storage devices
[   23.693783] usb-storage: device found at 2
[   23.693785] usb-storage: waiting for device to settle before scanning
[   23.693810] usbcore: registered new interface driver usb-storage
[   23.693813] USB Mass Storage support registered.
[   23.703008] usbcore: registered new interface driver hiddev
[   23.708668] input: HID 062a:0000 as /class/input/input2
[   23.708690] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:0b.0-5
[   23.708701] usbcore: registered new interface driver usbhid
[   23.708704] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   23.974750] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[07e40a00d90f5123]
[   24.006798] hdc: MATSHITADVD-RAM UJ-851S, ATAPI CD/DVD-ROM drive
[   24.367530] ide1 at 0x170-0x177,0x376 on irq 15
[   24.370028] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 16
[   24.370038] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 16 (level, high) -> IRQ 16
[   24.370045] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   24.370053] forcedeth: using HIGHDMA
[   24.614523] kjournald starting.  Commit interval 5 seconds
[   24.614751] EXT3-fs: sda1: orphan cleanup on readonly fs
[   24.614761] ext3_orphan_cleanup: deleting unreferenced inode 8487336
[   24.614802] EXT3-fs: sda1: 1 orphan inode deleted
[   24.614804] EXT3-fs: recovery complete.
[   24.616385] EXT3-fs: mounted filesystem with ordered data mode.
[   24.898429] eth0: forcedeth.c: subsystem: 0103c:30b5 bound to 0000:00:14.0
[   28.692553] usb-storage: device scan complete
[   28.693955] scsi 2:0:0:0: Direct-Access     Memorex  TRAVELDRIVE 005B PMAP PQ: 0 ANSI: 0 CCS
[   28.696438] sd 2:0:0:0: [sdb] 4028416 512-byte hardware sectors (2063 MB)
[   28.698185] sd 2:0:0:0: [sdb] Write Protect is off
[   28.698188] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   28.698190] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   28.703558] sd 2:0:0:0: [sdb] 4028416 512-byte hardware sectors (2063 MB)
[   28.705182] sd 2:0:0:0: [sdb] Write Protect is off
[   28.705185] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   28.705187] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   28.705191]  sdb: sdb1
[   28.706741] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   28.706774] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   32.482695] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.494289] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.511472] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   32.511508] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   32.553422] input: PC Speaker as /class/input/input3
[   32.586898] sdhci: Secure Digital Host Controller Interface driver
[   32.586903] sdhci: Copyright(c) Pierre Ossman
[   32.591970] sdhci: SDHCI controller found at 0000:05:09.1 [1180:0822] (rev 19)
[   32.592335] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 23
[   32.592339] ACPI: PCI Interrupt 0000:05:09.1[B] -> Link [LNK2] -> GSI 23 (level, high) -> IRQ 23
[   32.592659] mmc0: SDHCI at 0xb8000800 irq 23 DMA
[   32.820850] Linux video capture interface: v2.00
[   32.904194] ieee80211_crypt: registered algorithm 'NULL'
[   32.906638] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   32.906643] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   32.933737] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[   32.933747] Uniform CD-ROM driver Revision: 3.20
[   32.979859] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   32.981138] usbcore: registered new interface driver uvcvideo
[   32.981143] USB Video Class driver (v0.1.0)
[   33.017547] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   33.047578] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   33.094194] bcm43xx driver
[   33.094660] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
[   33.094671] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 19
[   33.094682] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   33.100935] bcm43xx: Unsupported 80211 core revision 13
[   33.102739] bcm43xx: Invalid PHY Revision 9
[   33.331606] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   33.331612] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 22 (level, high) -> IRQ 22
[   33.331780] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   34.317000] lp: driver loaded but no devices found
[   34.433474] Adding 2634620k swap on /dev/sda5.  Priority:-1 extents:1 across:2634620k
[   34.692765] EXT3 FS on sda1, internal journal
[   35.757530] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   35.769905] No dock devices found.
[   35.914473] ACPI: AC Adapter [ADP1] (on-line)
[   35.971921] input: Power Button (FF) as /class/input/input5
[   35.971943] ACPI: Power Button (FF) [PWRF]
[   35.971988] input: Sleep Button (CM) as /class/input/input6
[   35.972007] ACPI: Sleep Button (CM) [SLPB]
[   35.972045] input: Power Button (CM) as /class/input/input7
[   35.972060] ACPI: Power Button (CM) [PWRB]
[   36.073179] ACPI: Battery Slot [BAT0] (battery present)
[   36.232328] powernow-k8: Found 2 AMD Turion(tm) 64 X2  processors (version 2.00.00)
[   36.232159] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   36.232164] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   36.232167] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   37.063534] capifs: Rev 1.1.2.3
[   37.191133] ppdev: user-space parallel port driver
[   37.328882] audit(1202156251.216:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5149 profile="/usr/sbin/cupsd"
[   37.447064] eth0: no link during initialization.
[   37.601832] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   39.599995] Failure registering capabilities with primary security module.
[   39.773210] Bluetooth: Core ver 2.11
[   39.773277] NET: Registered protocol family 31
[   39.773282] Bluetooth: HCI device and connection manager initialized
[   39.773287] Bluetooth: HCI socket layer initialized
[   39.780632] Bluetooth: L2CAP ver 2.8
[   39.780637] Bluetooth: L2CAP socket layer initialized
[   39.786663] Bluetooth: RFCOMM socket layer initialized
[   39.786681] Bluetooth: RFCOMM TTY layer initialized
[   39.786684] Bluetooth: RFCOMM ver 1.8
[   41.204001] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   54.553940] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   70.307093] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   86.577308] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   97.088903] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  107.643508] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  144.678095] NET: Registered protocol family 10
[  144.678208] lo: Disabled Privacy Extensions
[  144.678323] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  167.414321] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  224.922163] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  282.659485] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  343.656253] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  401.939795] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  459.558563] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  514.941053] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  570.057162] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  626.922370] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  689.507099] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  747.519574] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  755.822054] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  774.594382] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  837.198653] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  899.949815] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  969.774594] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1029.475091] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1084.684643] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1140.141699] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1196.315252] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1228.381797] usbcore: registered new interface driver usbserial
[ 1228.381888] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 1228.382016] usbcore: registered new interface driver usbserial_generic
[ 1228.382019] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 1251.862168] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1307.338766] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1362.808269] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1417.949090] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1466.331334] usb 1-6: new full speed USB device using ohci_hcd and address 3
[ 1466.427717] usb 1-6: configuration #1 chosen from 1 choice
[ 1466.428988] usbserial_generic 1-6:1.0: generic converter detected
[ 1466.429193] usb 1-6: generic converter now attached to ttyUSB0
[ 1466.429266] usb 1-6: generic converter now attached to ttyUSB1
[ 1466.429336] usb 1-6: generic converter now attached to ttyUSB2
[ 1466.472467] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
[ 1466.472786] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
[ 1466.473052] usbcore: registered new interface driver sierra
[ 1466.473056] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.0.6
[ 1473.438566] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1530.271308] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1587.466382] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1643.676231] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1700.503513] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1741.113084] usb 2-3: USB disconnect, address 2
[ 1744.953831] usb 1-6: USB disconnect, address 3
[ 1744.954180] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[ 1744.954265] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[ 1744.954348] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[ 1744.954365] usbserial_generic 1-6:1.0: device disconnected
[ 1758.829967] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1814.350982] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1869.716049] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1924.820932] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1980.336602] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2035.667495] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2091.873982] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2154.093213] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2214.488443] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2238.538112] usb 1-6: new full speed USB device using ohci_hcd and address 4
[ 2238.632716] usb 1-6: configuration #1 chosen from 1 choice
[ 2238.634000] usbserial_generic 1-6:1.0: Sierra USB modem (3 port) converter detected
[ 2238.634267] usb 1-6: Sierra USB modem (3 port) converter now attached to ttyUSB0
[ 2238.634342] usb 1-6: Sierra USB modem (3 port) converter now attached to ttyUSB1
[ 2238.634418] usb 1-6: Sierra USB modem (3 port) converter now attached to ttyUSB2
 

There is the insanely  long dmesg, on a different subject I found how to install kppp but it says I need active internet connection which is what I'm trying to set up.....

---

### Post by Mach1US on 2008-02-04
i know , catch 22 :)
I'll go through it in the morning and let you know what we have here.

---

### Post by Carton on 2008-02-04
Thanks!

---

### Post by sierra1bravo on 2008-02-05
I am having exactly the same problem with EV-DO and Gutsy. After modprobe, the USB modem is recognized and binds to /dev/ttyUSB2, but it doesn't respond at the ATZ command, either in the wvdial script or directly through minicom.

Any help would be appreciated.

TIA

sierra bravo

---

### Post by Mach1US on 2008-02-07
> **sierra1bravo said:**
> I am having exactly the same problem with EV-DO and Gutsy. After modprobe, the USB modem is recognized and binds to /dev/ttyUSB2, but it doesn't respond at the ATZ command, either in the wvdial script or directly through minicom.

Any help would be appreciated.

TIA

sierra bravo

What do you exactly mean by "  but it doesn't respond at the ATZ command " .
Also minicom is serial port text interpretation software , what exactly have you been trying to do with minicom and evdo modem (just asking) ?
You actully in luck if you have gotten as far as recognizing proper tty , all it is now to to just paste the wvdial.con file with modification of your own personal cell info.  

TO :  [COLOR="Red"]**Carton**[/COLOR]
It seems like are in fact using USBSERIAL but you are given 3 different tty identifiers :
 ```
[ 2238.538112] usb 1-6: new full speed USB device using ohci_hcd and address 4
[ 2238.632716] usb 1-6: configuration #1 chosen from 1 choice
[ 2238.634000] usbserial_generic 1-6:1.0: Sierra USB modem (3 port) converter detected
[ 2238.634267] usb 1-6: Sierra USB modem (3 port) converter now attached to ttyUSB0
[ 2238.634342] usb 1-6: Sierra USB modem (3 port) converter now attached to ttyUSB1
[ 2238.634418] usb 1-6: Sierra USB modem (3 port) converter now attached to ttyUSB2
``` 
Try ttyUSB0 , ttyUSB1 and ttyUSB2 to see if one of them is attache d to your modem.

---

### Post by tdelphous on 2008-02-11
i entered all of the information and for some reason when i restart i have to reload the drivers every time.  any suggestions?  I have a novatel u727.  What do i have to do so i don't have to keep reloading the drivers every time i restart my computer.

---

### Post by Mach1US on 2008-02-13
USBSERIAL is loaded as soon as you plug the cell phone in, what driver are you useing ?

---

### Post by tdelphous on 2008-02-15
i dont know, it keeps attaching the generic driver all the time.   when i insert the aircard no drivers are attached.   so i have to enter
sudo modprobe usbserial vendor=0x1410 product=0x4100....
any suggestions?

---

### Post by Mach1US on 2008-02-15
That's a first one for me???
 When you detach the device and plug it back in without the reboot does it still work properly ?

---

### Post by txhellkat138 on 2008-02-15
I have read the past few posts and I cannot say where I work in advanced tech but I can tell you I use these cards daily and I know they work with gutsy now I dont suggest wvdial though we would use kppp or gnome ppp i do know that the previously mentioned document on the that certain company's website will be updated very soon. once you set up kppp use the modem query function on the different tty's it mentions until you find the one that repsonds. now as far as the u727 goes it is a real pita to make it work because of the having to unmount the cdrom drive it recognizes as but once that is doen it can be setup just the same as any of the other cards mentioned int his post.

Btw I apologize for the vagueness I have to be a little careful because I can get in alot of trouble at work and potentially lose my job if you guys need any specifics or help with anything please pm me so I can help a little more in depth. I deal with these cards and alot of cdma phones as modems daily with my gutsy laptop i have done the ins and outs of maing them work and im more than willing to do what I can to help.

---

### Post by john_linuxuser on 2008-02-16
My Verizon USB EVDO worked with the very first try. I used the same configu and chat script as with Fedora 7.

This is the first time I use Ubuntu; I install some version of Ubuntu 1 or 2 years ago, but I didn't use it, and I removed it in a day or two.

Now, my Ubuntu is Gutsy. My modem is USB720

I posted my chat script and config at
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Using_USB_EVDO_Internet_modem](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Using_USB_EVDO_Internet_modem)

I wonder if we can add this EVDO port to wvdial. If I contribute to it, this will be the first time I contribute to Linux. I first used Linux 7 years ago.

---

### Post by john_linuxuser on 2008-02-16
I actually went one step further with EVDO.

I make a script check the connection every 2 minutes, if the connection fails, it dials again. Also, every 2 minutes, it ftp my IP address to my geocities.com account.

My PC with the EVDO connection became a server. I can ssh home to do works.

---

### Post by Mach1US on 2008-02-17
> **john_linuxuser said:**
> I actually went one step further with EVDO.

I make a script check the connection every 2 minutes, if the connection fails, it dials again. Also, every 2 minutes, it ftp my IP address to my geocities.com account.

My PC with the EVDO connection became a server. I can ssh home to do works.

Thanks john_linuxuser!
Great Job.

---

### Post by geenet on 2008-02-23
I am set.  This worked EXACTLY as stated.  I am using a Sprint Motorola Q and it works perfectly.  This was the last reason that I kept Windows around for.  

By the way if anyone is looking for the password for Sprint it is anything. The card/phone does the authentication so no password is required.  I put in "sprintpcs" and it worked the first time.

---

### Post by taydu on 2008-02-24
> **FlyingHat said:**
> This is a very good HOWTO, I especially enjoy using wvdial versus having to come up with your own PPPD scripts.  

However, using usbserial for these EVDO connections is a BAD, repeat **BAD** idea.  usbserial was not designed for high-speed connections such as EVDO connections.  

Since kernel 2.6.18, the Airprime driver has been patched to allow full-speed EVDO connections.  Essentially, instead of using usbserial, simply type in the following:

```
:~$ modprobe airprime
```

And then check dmesg to see if it was loaded correctly.  You should see something like: 
```
[ 1618.912000] usbcore: registered new interface driver airprime
```

And after inserting the device:
```
[ 1620.504000] usb usb6: configuration #1 chosen from 1 choice
[ 1620.504000] hub 6-0:1.0: USB hub found
[ 1620.504000] hub 6-0:1.0: 1 port detected
[ 1621.884000] usb 5-1: new full speed USB device using ohci_hcd and address 2
[ 1622.096000] usb 5-1: configuration #1 chosen from 1 choice
[ 1622.096000] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
```

Follow the rest of the walkthrough.  If it looks like it's connecting, go ahead and add airprime to /etc/modules or type in:

```
:~$ sudo depmod -a 
```

Try it!

do i need to update if running Ubuntu 7.10 ?

my connection can't get any faster then 50kbps :( follow your guide but it doens't work

---

### Post by Mach1US on 2008-02-24
If thats the case it is something other then need for Airprime .
Actually if you want Airprime to load instead of USBSERIAL just skip the step that tells you to black list Airprime or if you have already done it just uncomment it and the kernel will automatically load airprime.
The post you have mention applies only to earlier versions , Gutsy loads airprime _automatically _ .

---

### Post by dchen37 on 2008-02-28
I've been trying this with Gutsy on a Treo 755p with Sprint.  I get 2 results after typing in dmesg:

> [25568.816000] usb 4-1: generic converter now attached to ttyUSB0
[25568.816000] usb 4-1: generic converter now attached to ttyUSB1

When I chose ttyUSB1 nothing happnes, with ttyUSB0 my Treo resets.  Anyone else get this to work?

---

### Post by Mach1US on 2008-02-28
> **dchen37 said:**
> I've been trying this with Gutsy on a Treo 755p with Sprint.  I get 2 results after typing in dmesg:



When I chose ttyUSB1 nothing happnes, with ttyUSB0 my Treo resets.  Anyone else get this to work?

Send this guy a  message i believe he had some details on that:
[http://ubuntuforums.org/member.php?u=35039](http://ubuntuforums.org/member.php?u=35039)

---

### Post by DarkerViolet on 2008-03-06
Simply blacklisting the airprime driver is all my system needed.  It then started using the usbserial driver for the card under ACM0 and I setup KPPP to dial #777 with user/user as the username/password.  Up and running in seconds.

Thanks for reminding me about the blacklist fix.  I had this working originally under 7.10 but then my drive crashed and I had to start from scratch.

---

### Post by dollraves on 2008-03-07
For AT&T/Cingular folks using the USBConnect 881 or another TruInstall type of USB modem, this will not allow us to connect.  The problem is that Ubuntu recognizes the TruInstall usb modems as cd roms because they contain the modem software for Windows.

The SierraWireless Website has a workaround that involves recompiling the kernel to something 2.6.23 or higher and then applying the TruInstall patch:  [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1077](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1077)

I haven't done it yet - slated to do it this weekend.  Hope this helps some folks.

-Carlota

---

### Post by gambit0608 on 2008-03-08
A Huge THANK YOU to Mach1US!!!!!!!!!!!!!!!!!!!!
Your tutorial worked flawlessly, very easy to follow :)

Goodbye Windows.


On a side note i would like to thank all of the members on this forum for their advice and solutions for noobs like me,:KS

---

### Post by ljoslin on 2008-03-13
I'm trying to do this on a Sprint Treo 755p connected via the USB cable.

when I do this part

```
dmesg

You will get output with some device info like this :
Code:

[17186692.460000] usb 3-1: configuration #1 chosen from 2 choices
[17186692.460000] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[17186708.176000] usb 3-1: USB disconnect, address 4
[17186714.588000] usb 3-1: new full speed USB device using uhci_hcd and address


```

I get 2 results ttyUSB0  and ttyUSB1.

I tried both results, with sort of the same results

```
ljoslin@ljoslin-laptop:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.
ljoslin@ljoslin-laptop:~$ 


```

the only difference is with ttyUSB0 the phone starts to reboot but freezes.  Anybody get one of the new treos to work?  Or anyone have any insight on this problem?  Thanks!

-=Ljoslin=-

---

### Post by dchen37 on 2008-03-13
Here's what worked for me on my Sprint 755p.

I used [this program]("http://www.mobile-stream.com/usbmodem.html") on my Treo to set it into USB Modem mode which unfortunately costs $24. 

Then I put the line 

> Modem = /dev/ttyACM 

in the wvdial.conf file

I found the settings from this [website.]("http://ubuntu-tutorials.com/2007/06/07/dialup-networking-via-treo-700p-and-ubuntu-usb-connection/")

Anyone know of a way of doing this without having to pay for the USB Modem program?

---

### Post by soupbadger on 2008-03-17
Just found this post and wanted to say it works with the Moto Q on Alltel. Thanks so much.

---

### Post by MikeyXX on 2008-03-19
I've found that if airprime is not blacklisted, wvdial won't find the ttyUSB0. That's fine, it was mentioned. 

My problem is that using my ZTE aircard on Ubuntu I'm getting 400 down and 120 up. In XP I get 1000down and 120 up.


Why am I getting such slow speeds? Anyone know?

---

### Post by Mach1US on 2008-03-19
I'm assume you have been using browser based speed tests.
Did you try a swiftfox , i haven't had a chance to study which setting makes the difference but it has helped more than once.
Most generic versions of browsers are set up to work on all hardware that means it is slow enough to be still compatible with all sorts of ancient pc's , but some tweaked versions like swiftfox help to strip all those limitations .

---

### Post by MikeyXX on 2008-03-20
Yes, it was browser based. However, I find it difficult to believe that it would strip half the speed off in firefox than IE in windows. But I will give it a go!

Is this something that is available via apt-get?

---

### Post by chapterthree on 2008-03-21
I wanted to post to stay that I got an EVDO connection working on my LG 8600 on the first try by just following the steps.

I seem to be able to sustain download speeds of 64KB/s with spkes as high as 128KB/s using the USB cable.  A little later I'm going to give my bluetooth dongle a try.

Thanks for the helpful and straight forward guide!! \\:D/

---

### Post by Mach1US on 2008-03-24
> **MikeyXX said:**
> Yes, it was browser based. However, I find it difficult to believe that it would strip half the speed off in firefox than IE in windows. But I will give it a go!

Is this something that is available via apt-get?
You can get it from Automatix which is good for whole bunch other stuff.

---

### Post by DeVonne on 2008-03-28
Thank you! it works with the um150 with alltel, I am new to ubuntu also and it was VERY easy to follow

I do have 1 question, When I was on windows I used quicklink mobile and it showed if I was on evdo or rtt and and it showed the dbm or signal strength,

Is it possible to get that on ubuntu?

Thanks!

um150 works :) (used it to write this article)

---

### Post by condorface on 2008-03-30
Hey, I have an alltel UM150 wireless modem that I am trying to get to work with my newly installed Ubuntu Studio 7.10 OS.  I noticed that someone else on this forum got their alltel UM150 to work.  I followed all the directions for Gutsy and am not able to get it working.  I type wvaudio into the terminal, and this is all I get:

matthew@ubustud:~$ wvdial 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvModem<*1>: Cannot get information for serial port. 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<*1>: Sending: ATDT#777 
WvDial<*1>: Waiting for carrier. 
WvDial Modem<*1>: ATDT#777 
WvDial Modem<*1>: CONNECT 
WvDial<*1>: Carrier detected.  Starting PPP immediately. 
WvDial<Notice>: Starting pppd at Fri Mar 28 16:55:27 2008 
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied 
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky. 
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied 
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky. 
WvDial<Notice>: Pid of pppd: 5419 
WvDial<*1>: Disconnecting at Fri Mar 28 16:55:27 2008 
WvDial<*1>: The PPP daemon has died: pppd options error (exit code = 2) 
WvDial<*1>: man pppd explains pppd error codes in more detail. 
WvDial<Notice>: I guess that's it for now, exiting 
WvDial<Notice>: The PPP daemon has died. (exit code = 2) 
matthew@ubustud:~$ sudo -i 
root@ubustud:~# wvdial 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvModem<*1>: Cannot get information for serial port. 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<*1>: Sending: ATDT#777 
WvDial<*1>: Waiting for carrier. 
WvDial Modem<*1>: ATDT#777 
WvDial Modem<*1>: CONNECT 
WvDial<*1>: Carrier detected.  Starting PPP immediately. 
WvDial<Notice>: Starting pppd at Fri Mar 28 16:55:58 2008 
WvDial<Notice>: Pid of pppd: 5433 
WvDial<*1>: Disconnecting at Fri Mar 28 16:55:58 2008 
WvDial<*1>: The PPP daemon has died: pppd options error (exit code = 2) 
WvDial<*1>: man pppd explains pppd error codes in more detail. 
WvDial<Notice>: I guess that's it for now, exiting 
WvDial<Notice>: The PPP daemon has died. (exit code = 2) 

Notice I tried it with and without the root user.  Both return back slightly different results, but no connection could be made.  I am brand new to this, so is there something I could be missing?  Is there a driver I need, or something.  Thanks for any help you may have.  Ubuntu Studio is not running right on my brand new hp hardware, so the internet is definitely needed to get the correct drivers.  By the way, I know that the UM150 is functional,  because I am using it right now in Windows Vista (i'm dual-booting).

If you need any additional information, please specify what it is and how to get it in laymans terms, I am new to Ubuntu.

---

### Post by DeVonne on 2008-03-31
Condorface yes that was me :)

Have you tried unplugging it waiting 10 seconds?

I notice you said you used wvaudio try wvdial

It works fine for me, Try it a few times I can have a disconnect problem

If you still need help I am subscribed to this thread :)

---

### Post by condorface on 2008-03-31
Yeah, I used wvdial.  That was just a typo.  Got audio on the brain, I guess.  I'll give it another try. Didn't try unplugging and trying again.   I noticed the modem does have trouble connecting sometimes even in Vista.

---

### Post by condorface on 2008-03-31
Tried it over and over again with the same results.  I also tried it in xubuntu 7.10 with the same results.  Is there something I'm missing?  Do you get the same error messages that I posted earlier, DeVonne?  How frequently does yours not connect? I called alltel and made sure I had the correct password and everything, and the alltel guy said that as long as I have the correct drivers, it should be fine.  Do I need certain drivers that don't come with the Gutsy installation, or does the alltel guy not know what he is talking about?  At a loss as to what to do next.

---

### Post by DeVonne on 2008-03-31
Condorface, I don't think I have gotten error 2, not sure,
If anyone knows what error 2 is please tell us!

Mine will disconnect sometimes but I just wvdial it back
I do get the problem where it goes out and then wvdial says its busy unplugging then seems to fix that also

OK here is what I want you to do,

REINSTALL wvdial, sometimes when I reinstall things it fixes it,
In case it gets rid of your configs backup all the files the guide has you edit so you can restore them, also post it here so I can see if it matches mine

Also goto vista tell me if its on RTT or EVDO, and tell me your signal strength or DBM

And yes please try unplugging it and plugging it in when it don't work,

Make SURE everything on the guide was done, read it again to make sure you did not miss something


I am determined to help you to the best I can! :KS

---

### Post by condorface on 2008-03-31
Thanks for replying, Devonne.  I am very new to computers, so there is some terminology that hangs me up.  I understood all the stuff about reinstalling wvdial and getting the configs on here, but I don't know how to check on Vista to see if the modem is an RTT or EVDO, and I am not too sure what you mean by signal strength or DBM.  I know that in the "Capability" section of the "about" menu, it says that the UM150's capability is 1XEVDO, so I assume that it is EVDO and not RTT.  I don't even know what RTT is.  
I am the middle of a big download tonight, so I can't get back into Ubuntu until tomorrow.  I will posts the results then.  
Again, thanks for your help.

---

### Post by DeVonne on 2008-03-31
You're welcome, I know how it can get when you don't get the help you need or someone refuses to,

And make note, before you post your config don't include your telephone number and pass for security reasons

RTT would be the slower cell phone tower, lets say you are out of the reach to the EVDO tower it will goto the RTT one,
I am between the 2 so it tends to go back and forth

If you really want more information on what EVDO and RTT is try google or asking an alltel techie

Ok I will wait until then for your configs :) good luck

EDIT:

Oh I forgot to mention, you can find the signal and that stuff in quicklink mobile on windows,

---

### Post by dtl2009 on 2008-04-02
Hello,

I have been trying to get my Sierra 597E Sprint EVDO card working on my laptop.  I have tried many different sets of instructions including those from this thread and have had no success.  I am starting to think I may have an idea what is going on, I believe that the TRU-install feature of my card is the culprit.  When I follow these instrutions I never seem to be able to find my card after inserting it and running the dmesg command.  Also when I run the diff /proc/... command I get a vendor id that matches Sierra 0x1199 but the product id is not 0x0021 as it should be. I have included some of the terminal output. Any help you can provide will be greatly appreciated,

---

### Post by condorface on 2008-04-03
Ok, I was finally able to try it all again.  I reinstalled wvdial from the alternate cd, and checked all og my config files to see that they were correct.  As far as I can tell, they were.  Here is my mountdevsubfs.sh file:

[COLOR="Red"]#! /bin/sh 
### BEGIN INIT INFO 
# Provides:          mountdevsubfs mountvirtfs 
# Required-Start:    mountkernfs 
# Required-Stop: 
# Default-Start:     S 
# Default-Stop: 
# Short-Description: Mount special file systems under /dev. 
# Description:       Mount the virtual filesystems the kernel provides 
#                    that ordinarily live under the /dev filesystem. 
### END INIT INFO 

PATH=/lib/init:/sbin:/bin 
TTYGRP=5 
TTYMODE=620 
[ -f /etc/default/devpts ] && . /etc/default/devpts 

TMPFS_SIZE= 
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs 

KERNEL="$(uname -s)" 

. /lib/lsb/init-functions 
. /lib/init/mount-functions.sh 

do_start () { 
	# 
	# Mount a tmpfs on /dev/shm 
	# 
	SHM_OPT= 
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT="-osize=$SHM_SIZE" 
	domount tmpfs shmfs /dev/shm $SHM_OPT 

	# 
	# Mount /dev/pts. Create master ptmx node if needed. 
	# 
	domount devpts "" /dev/pts -ogid=$TTYGRP,mode=$TTYMODE 

	# 
	# Magic to make /proc/bus/usb work 
	# 
	mkdir -p /dev/bus/usb/.usbfs 
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644 
	ln -s .usbfs/devices /dev/bus/usb/devices 
	mount --rbind /dev/bus/usb /proc/bus/usb 
} 

case "$1" in 
  "") 
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2 
	do_start 
	;; 
  start) 
	do_start 
	;; 
  restart|reload|force-reload) 
	echo "Error: argument '$1' not supported" >&2 
	exit 3 
	;; 
  stop) 
	# No-op 
	;; 
  *) 
	echo "Usage: mountdevsubfs [start|stop]" >&2 
	exit 3 
	;; 
esac
[/COLOR]
[COLOR="Black"]
I took all the pound  signs off where it was called for in the tutorial.  I put the whole file on here just in case there is something else wrong with it that a trained eye can see.

Here is my wvdial config file(with stars where my username should be):[/COLOR]


[COLOR="Red"]
[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = [email]**********@alltel.net[/email] 
Password = alltel 
Initl = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check =no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP[/COLOR]
[COLOR="Black"]

The only other thing that I can think of is that when I put in 
"diff /proc/bus/usb/devices devices | grep Vendor," it returns this:[/COLOR]

[COLOR="Red"]< P:  Vendor=106c ProdID=3711 Rev= 1.00 [/COLOR]

Should the number for Vendor have a "c" at the end, and, if so, should I type it in or disregard it when I follow the next step?
As it is, I did use the "c".  I typed:
[COLOR="Red"]root@ubustud:~# modprobe usbserial vendor=0X106c product=0X3711 [/COLOR]
[COLOR="Black"]Anyways, everything turned out the same.  It didn't work, and I got the same error messages.[/COLOR]

---

### Post by rockingmtranch on 2008-04-03
I just got the UM 150 USB Modem (phone) and got it working in Ubuntu
[http://www.montanamenagerie.org/forum/viewtopic.php?t=903](http://www.montanamenagerie.org/forum/viewtopic.php?t=903)

---

### Post by condorface on 2008-04-03
thanks rockingmtranch, I got mine working using that link.  Thanks to DeVonne as well.  I had all but given up without the encouragement.  NOw to get sound and video and the settings Daemon working......

---

### Post by freefalljd on 2008-04-05
Worked like a champ. Thanks for the great tutorial. Running Gutsy w/ a UM150VW (Verizon).

---

### Post by rockingmtranch on 2008-04-05
Glad to help. I was super happy when I got mine working.

---

### Post by windoze87 on 2008-04-19
Man, this worked like a charm for my USB720! I was so frustrated over trying to get it to work with PCLinux that i gave up on Linux altogether for a while, till a friend of mine gave me this Fiesty Fawn disc...tried that code...and BAM! Worked like magic, the first time. Thank you so much
:D

---

### Post by Mach1US on 2008-05-05
For anybody looking for NEW Sprint Aircard 595U install on Ubuntu Hardy 7.10 or rc :

[http://ubuntuforums.org/showpost.php?p=4890048&postcount=10](http://ubuntuforums.org/showpost.php?p=4890048&postcount=10)

---

### Post by lsearcey on 2008-05-07
After getting it setup I tried running wvdial like Mach1US original post said and I got the following error:


[IMG]http://img395.imageshack.us/img395/2296/wvdialerrorxv8.png[/IMG]
By [lsearcey](http://profile.imageshack.us/user/lsearcey) at 2008-05-07

I am using Alltel and a Motorola E815 phone.  I have Ubuntu 7.10 installed.  
One problem is I don't have internet on my ubuntu Install.  I have to restart to XP get data then reboot. I really ne to get Ubuntu to read my phone.

Thank You

---

### Post by Mach1US on 2008-05-08
You guys with Alltell service sometime need additional init line in wvdial.conf as well correct domain and pasword configuration.
[PHP][Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = ??????????@alltel.net
Password = alltel
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP[/PHP]
I see other people having same problem, if it wont fix it you may want to send them a private message or e-mail to get exact specs.
Those some of posts i seen with this same problem:
[http://ubuntuforums.org/showpost.php?p=3228261&postcount=53](http://ubuntuforums.org/showpost.php?p=3228261&postcount=53)
[http://ubuntuforums.org/showpost.php?p=4618224&postcount=205](http://ubuntuforums.org/showpost.php?p=4618224&postcount=205)
I'v never worked with Alltell so i'm somewhat fuzzy on what exactly causes exit code-2 in this case but i know that bunch of people got their Alltell Evdo modems running using this how to .

---

### Post by Mach1US on 2008-05-08
For Alltell i have also seen this How to in the forums:

Step 1 - Get the phone recognized.
This is, by far, the hardest part, and what caused most of my problems. The V3a is unique enough that the kernel build in Kubuntu 7.04 didn't recognize it, and give it a port immediately. I felt my way along many a blind alley trying to get cdc-acm to work, and finally found a solution in usbserial (info for that gleaned from [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)).

When you plug the cellphone into the computer, cdc-acm is supposed to automatically assign it a /dev point to bind to. With the V3a being so new, the kernel can't figure it out, and you end up with the following in dmesg:

Code:

~$ dmesg | tail
[23574.428000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[23574.644000] usb 2-1: configuration #1 chosen from 1 choice

Notice, no info on a port assignment or the like, it notes that there's only one choice available to the kernel, and that's basically that it's there, and nothing more. A useless brick, if you will, connected via USB.

cdc-acm is supposed to kick in here and assign it a point. As I said, that doesn't happen with the V3a. So, we have to determine the info from the phone that we can, and use usbserial instead.

We'll need to compare device listing outputs to do this, so for now, disconnect your phone.
Code:

~$ cat /proc/bus/usb/devices > devices

This will create a file ~/devices, basially a listing of all devices currently connected to your machine. A snapshot, if you will, of the current stuff attached to your computer.

Now, connect your phone. Give it a few moments, the phone should beep a few times. We can now compare what's currently connected to what was connected, and find the info from the phone itself.
Code:

~$ diff /proc/bus/usb/devices devices | grep Vendor

What that command does is looks at the current device list (/proc/bus/usb/devices) and compares it (using the diff command) to what you had when you didn't have the phone connected. Finally, we filter it through grep (a search engine of sorts) for just what we want, the vendor info. You should get a single line detailing the vendor and product ID.
Code:

~$ diff /proc/bus/usb/devices devices | grep Vendor
< P:  Vendor=22b8 ProdID=2ac4 Rev= 0.01

Now, we have the vendor and product info for the phone.

Next, we need to load the usbserial module in, with that specific information associated with it.

Code:

~$ sudo modprobe usbserial vendor=0x22b8 product=0x2ac4

That loads usbserial in, and gives it a vendor and product to work with. If you do this while the phone is still connected, it should beep at you.

Finally, disconnect the phone, and reconnect it. After a few seconds (and a few beeps from the phone), check the message log again.

Code:

~$ dmesg | tail
[24439.348000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[24439.564000] usb 2-1: configuration #1 chosen from 1 choice
[24439.564000] usbserial_generic 2-1:1.0: generic converter detected
[24439.564000] usb 2-1: generic converter now attached to ttyUSB0
[24439.568000] usbserial_generic 2-1:1.1: generic converter detected
[24439.568000] usb 2-1: generic converter now attached to ttyUSB1

As you can see, we've now got it assigned to a port we can work with, in this case, /dev/ttyUSB0.

Step 2 - setting up a ppp dialer
Everyone will have their favorite method of doing this, what with the multitude of ppp dialers out there. Everything from fancy GUIs to collections of shell scripts. Personally, I use KDE, and like the KPPP dialer. It manages everything rather well for me.

The basics:
Username - your 10-digit phone [email]number@alltel.net[/email]
Password - alltel
Number - #777
Device - /dev/ttyUSB0

That should be what you'd need for most any dialer out there. The rest that follows is specific to KPPP.

Launch KPPP, click Configure.

On the Accounts tab, click New. In the warning, click Manual Configuration. For configuration name, put in anything you want (I put AllTel). Click Add, and enter #777 for the phone number. Click OK twice, and you'll be back on the KPPP Configurations dialog.

On the Modems tab, click New. For modem name, enter anything (I put V3a), for device, choose /dev/ttyUSB0. Click OK.

OK out of the KPPP Configuration dialog.

Enter your username (remember, your 10-digit phone [email]number@alltel.net[/email]), and the password (alltel).

You should be all set now, you can choose to "show log window" if you want, to see the progress, but otherwise, click connect and go!

There's 2 problems with this setup, you'll need to modprobe that same device every time you want to use your EVDO 'net access, but the Prod/vendor info never change. Easily done in a shell script or during boottime, up to you. The other issue is if you disconnect, then want to reconnect right away, it appears the phone doesn't really 'let go' properly, and must be unplugged and reconnected to make that 2nd ppp connection. Again, you don't have to go through the finding/modprobe step again, just pull the cable and reconnect it.

---

### Post by lsearcey on 2008-05-08
This may sound stupid but the one help says to run the PPP or KPPP how do I do that?  Throught the terminal?

Thank You

---

### Post by Mach1US on 2008-05-08
Few posts back there is a link to sprint  document outlining the process.

---

### Post by Jaxl on 2008-05-11
Yes very much ty for that :D

---

### Post by stingray17 on 2008-05-12
Just another happy user letting you know this worked great for me!

OS: kubuntu desktop 8.04
Hardware: ASUS S6F laptop
Modem: PANTECH UM150VW USB
Provider: Verizon

Thank you!!

---

### Post by evdo_user on 2008-05-26
Hi,

I was able to make my card work with 2GB of memory, but after upgrading to 4GB of memory it fails to detect the card.

The command "cat /proc/bus/usb/devices" does not list the device.
With 2GB it shows up as 

 Vendor=106c ProdID=3702 Rev= 1.00

Also when the card is inserted with 4GB of memory /var/log/messages reports the following.

May 26 15:23:20 wrc-laptop kernel: pccard: CardBus card inserted into slot 0
May 26 15:23:20 wrc-laptop kernel: PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
May 26 15:23:20 wrc-laptop kernel: ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ
 18
May 26 15:23:20 wrc-laptop kernel: ACPI: PCI interrupt for device 0000:04:00.0 disabled
May 26 15:23:20 wrc-laptop kernel: ohci_hcd 0000:04:00.0: init 0000:04:00.0 fail, -14
May 26 15:23:20 wrc-laptop kernel: ohci_hcd: probe of 0000:04:00.0 failed with error -14
May 26 15:23:20 wrc-laptop kernel: PCI: Enabling device 0000:04:00.1 (0000 -> 0002)
May 26 15:23:20 wrc-laptop kernel: ACPI: PCI Interrupt 0000:04:00.1[B] -> GSI 19 (level, low) -> IRQ 18
May 26 15:23:20 wrc-laptop kernel: ACPI: PCI interrupt for device 0000:04:00.1 disabled
May 26 15:23:20 wrc-laptop kernel: ohci_hcd 0000:04:00.1: init 0000:04:00.1 fail, -14
May 26 15:23:20 wrc-laptop kernel: ohci_hcd: probe of 0000:04:00.1 failed with error -14

When the card is inserted with 2GB of memory it reports the following.

May 26 13:48:08 wrc-laptop kernel: pccard: CardBus card inserted into slot 0
May 26 13:48:08 wrc-laptop kernel: PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
May 26 13:48:08 wrc-laptop kernel: ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 18
May 26 13:48:08 wrc-laptop kernel: ohci_hcd 0000:04:00.0: OHCI Host Controller
May 26 13:48:08 wrc-laptop kernel: ohci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
May 26 13:48:08 wrc-laptop kernel: ohci_hcd 0000:04:00.0: irq 18, io mem 0x8c000000
May 26 13:48:09 wrc-laptop kernel: usb usb8: configuration #1 chosen from 1 choice
May 26 13:48:09 wrc-laptop kernel: hub 8-0:1.0: USB hub found
May 26 13:48:09 wrc-laptop kernel: hub 8-0:1.0: 1 port detected
May 26 13:48:09 wrc-laptop kernel: PCI: Enabling device 0000:04:00.1 (0000 -> 0002)
May 26 13:48:09 wrc-laptop kernel: ACPI: PCI Interrupt 0000:04:00.1[B] -> GSI 19 (level, low) -> IRQ 18
May 26 13:48:09 wrc-laptop kernel: ohci_hcd 0000:04:00.1: OHCI Host Controller
May 26 13:48:09 wrc-laptop kernel: ohci_hcd 0000:04:00.1: new USB bus registered, assigned bus number 9
May 26 13:48:09 wrc-laptop kernel: ohci_hcd 0000:04:00.1: irq 18, io mem 0x8c001000
May 26 13:48:09 wrc-laptop kernel: usb usb9: configuration #1 chosen from 1 choice
May 26 13:48:09 wrc-laptop kernel: hub 9-0:1.0: USB hub found
May 26 13:48:09 wrc-laptop kernel: hub 9-0:1.0: 1 port detected
May 26 13:48:11 wrc-laptop kernel: usb 8-1: new full speed USB device using ohci_hcd and address 2
May 26 13:48:11 wrc-laptop kernel: usb 8-1: configuration #1 chosen from 1 choice
May 26 13:48:11 wrc-laptop kernel: cdc_acm 8-1:1.0: ttyACM0: USB ACM device
May 26 13:48:11 wrc-laptop kernel: usbcore: registered new interface driver cdc_acm
May 26 13:48:11 wrc-laptop kernel: drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters

Any ideas on how to fix this?

Thanks

---

### Post by Mach1US on 2008-05-27
Unfortunately i haven't seen this before but from the log it looks that you are not getting proper IRQ addressing which has been changed since you installed new chips.
First try just reloading the driver for the evdo card and if this wont work you will have to reload drivers for the card connector (usb or PCMCI) and then reload driver for the card itself again .
With new drivers it will assign new IRQ interrupt addresses corresponding to new memory.

---

### Post by erothoff on 2008-06-02
I got internet working with an Alltel LG AX8600 and wvdial, but I would like to get it working with Network manager. (As I have to constantly tell Firefox that I am online to browse.) But for some reason it isn't working. I am using port /dev/ttyACM0 for my connection in wvdial, but the network manager doesn't give it as an option. (So I enter it manually.)
  Other posts say that "It just works." with the dialer like that. I am blacklisting like first suggested. Any suggestions?

---

### Post by eric9477 on 2008-06-15
I was able to get my alltel um150 to work with this thread for the most part.  I can get online to surf the web with firefox, but I have to uncheck the work offline button every time. I also can't seem to get anything else to recognize I'm online such as Synaptic, apt-get, etc.  The network icon in the upper right of gnome says "no network connection".  Any help would be appreciated. :)

---

### Post by Mach1US on 2008-06-17
I have not been able to replicate the problem but it definitely  looks like its Network Manager problem not a Evdo card issue so i suggest to look in the threads regarding additional configurations in Network Manager itself.

---

### Post by eric9477 on 2008-06-18
I'm not sure what the problem is.  Somehow my computer was looking for a connection through my ethernet card instead of my um150.  I've kept messing with it and everything seems to be working for now except my weather report applet.  Going to System > Administration > Network and setting my wired connection config to "automatic config (dhcp)" seemed to fix my problem with Firefox making me uncheck "work offline" every time.

---

### Post by Mach1US on 2008-06-18
One more thing coming of the top of my head is to restore /etc/network/interfaces file to original cofigs as network manager does not know how to handle interfaces configured by other software.
To do so type :
```
sudo gedit /etc/network/interfaces
```
and make sure that all it is in that file is the following :
```
auto lo
iface lo inet loopback

```
and uncomment everything else.

Hope this helps.

---

### Post by eric9477 on 2008-06-18
> **Mach1US said:**
> One more thing coming of the top of my head is to restore /etc/network/interfaces file to original cofigs as network manager does not know how to handle interfaces configured by other software.
To do so type :
```
sudo gedit /etc/network/interfaces
```
and make sure that all it is in that file is the following :
```
auto lo
iface lo inet loopback

```
and uncomment everything else.

Hope this helps.
Well, I spoke too soon.  The changes I made earlier didn't stay after a complete shutdown/restart (I had only rebooted before and they had stayed put then).  I checked the network interfaces file and everything looked fine.  Thanks for the suggestions!

---

### Post by MrDetermination on 2008-06-23
I am getting disconnected after a very short time.
[U]
Verizon Wireless + PC5740 + Hardy[/U]
[B]sudo wvdialconf
sudo gedit /etc/wvdial.conf[/B]
```
[Dialer Defaults]
Stupid Mode = on
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB3
ISDN = 0
Phone = #777
Password = 123
Username = 6661114444@vzw3g.com
Carrier Check = no
Auto Reconnect = on
lcp-echo-interval = 0

```

**wvdial**
_Result_
```
--> Connect time 2.5 minutes.
--> Disconnecting at Fri Jun 20 15:44:09 2008
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)
```

No problems in Windows (dual boot).  What am I missing?

---

### Post by Mach1US on 2008-06-23
> **MrDetermination said:**
> I am getting disconnected after a very short time.
[U]
Verizon Wireless + PC5740 + Hardy[/U]
.....  What am I missing?
Wvdial was originally developed for dial-up connections such as ISDN and supports a feature called echo checking which most of the time isn't supported by cell providers ( Verizon doesn't support it for sure ) so it should be turn off to make a connection "always active" .

To do so Open terminal and type:
Code:

```
sudo gedit /etc/ppp/peers/wvdial
```

And insert additionally those lines:
Code:

```
lcp-echo-failure 0
lcp-echo-interval 0
```

Restart the connection and you should be on unless you lose the signal or your provider kicks you out .

---

### Post by MrDetermination on 2008-06-23
Mach1US is my hero.

---

### Post by Jaxl on 2008-06-24
if anyones interested GPPP IS ALL YOU NEED LOOK HEIR
[http://ubuntuforums.org/showthread.php?t=838891&highlight=1xevdo](http://ubuntuforums.org/showthread.php?t=838891&highlight=1xevdo)
Tested with gnome ubuntu 8.04

---

### Post by Mach1US on 2008-06-24
Thanks for additional info , it got me interested but as i tried it without blacklisting the dmesg give me two identifiers.
What is the method you have chose to isolate correct dev ?

---

### Post by Mach1US on 2008-07-13
Just got this short and simple method on the evdo setup , haven't tested it yet on new install but if this is as simple as it appears it may be the easiest way to get EVDO cards working.

Citing directly from the post 
```
1) open terminal and type sudo wvdialconf
2) in terminal type sudo gedit /etc/wvdial.conf
3) after Init1 make it say ATX0.
username is INSERTPHONE#HERE@alltel.net
password is alltel

save and close
4) in terminal type wvdial

you should be on the internet now.
 make sure to uncheck work offline under file in the browser.
.
```
Originally posted slick8199

---

### Post by zieglerj on 2008-07-15
Thank you this worked wonders. I have a slightly unique set up that this worked with using only minor tweeking so I figured I should post it. 
I'm using a Huawei EC360 data card laptop modem in a desktop computer through a PCI to PCMCIA Controller Card (yes they exist). 
In order to get it to work with your instructions I just had to leave out the part about blacklisting airprime and then it worked beautifully. 
I would have never been able to get this working without you, thanks again, you easily saved me $80 with thes instructions. 

P.s. my service provider is alltel.

---

### Post by bwainscott on 2008-07-20
Folks this post is absolutely awesome and works as advertised.  I am on an Acer Aspire 3690-???? running 8.04.  I have a UM150 USB Modem that I use with Verizon.  I was extremely worried about being able to carry it over to my Linux Machine.  Is there a GUI application for wvdial?  Thanks again for the wonderful How-to!

---

### Post by motapa on 2008-07-22
I have recently upgraded to ubuntu hard from dapper. While in dapper my evdo modem was working just fine, but there was a problem with Hardy. So I followed the spteps outlined in this thread, but then they messed up with the graphics. Apparently by enabling /dev/bus/usb it disbales other drivers. (it could be my laptop that is causing this). What ever the problem was, after I commented out the lines in /etc/init.d/mountdevsubfs.sh, my graphics were back to normal. (Oh did I mention that the steps here did not solve my internet problem). So now I am back to square one.

Any ideas. By the way where does one report their modem if it works with Linux. I use a ZTE MY39 evdo modem. Thanks in advance.

---

### Post by Ghost_of_the_Devil on 2008-07-25
novatel v740 express card works without a hitch on 8.04 using airprime

---

### Post by burtzacarach on 2008-07-25
I can already tell that Linux is gonna be quite a task to tackle!
I'm using a Verizon 5740 EVDO and i got it running using Airprime, but initially when i started the connection the terminal would repeatedly lose the carrier. It worked after I turned off the carrier check and LCP echos, and my laptop has working internet now! Thanks a lot.

---

### Post by oneloveamaru on 2008-07-27
Hey guys, running Kubuntu Hardy Heron 8.04.1 (newest ISO I could find). I tried using the airprime driver with my PC5750(verizon) and it would hard lock my laptop, Dell D531. 

I was on Kubuntu 7.10 and used the USB way before. Had to use it again with 8.04 but worked great! The only problem I ran into, was trying to connect when my Wireless/Bluetooth was on. Had to turn it off before it wanted to connect.

Thanks for the how to guys! I LOVE the ubuntu community!

---

### Post by marsbdc on 2008-07-31
I am come from China, My name is Mars, Very glade to meet you here. I'm professional CDMA&GSM/GPRS/EDGE &HSDPA modem manufacturer. If you have any require,please feel free let me know. website:[www.bdcchina.com](www.bdcchina.com)

Phone:+008613927484257
Email:mars.gaolin@gmail.com
MSN:salesbdcchina@hotmail.com
Skype:salesbdcchina:guitar:

---

### Post by herda05 on 2008-08-05
For anyone with a usb727, I followed the steps here and the modem would disconnect after about 3 seconds with authorization errors.

Finally, I logged into Windows, used VZAccess and connected the modem. I then disconnected in Windows and booted into Ubuntu. When I tried wvdial at that point, the modem connected and stayed connected. I could open Firefox and surf the web.

Hope this helps.

Dan H.

---

### Post by zfouts on 2008-08-07
So, I have a Palm Treo 700wx (Running Windows Mobile :() that I am trying to tether to.

```

zach@yubz:~$ dmesg | tail
[  125.216968] eth1: associated
[  125.220565] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  139.468593] eth1: no IPv6 routers present
[  141.466847] usb 1-2: USB disconnect, address 4
[  141.653512] usb 1-2: new full speed USB device using uhci_hcd and address 5
[  141.681687] usb 1-2: configuration #1 chosen from 1 choice
[  170.045197] usb 1-2: USB disconnect, address 5
[  197.146226] usb 1-1: new full speed USB device using uhci_hcd and address 6
[  197.154723] usb 1-1: configuration #1 chosen from 1 choice

```

```
zach@yubz:~$ diff /proc/bus/usb/devices /root/devices | grep Vendor
< P:  Vendor=045e ProdID=0301 Rev= 0.00

```

```
zach@yubz:~$ lsusb | grep 045e
Bus 001 Device 009: ID 045e:0301 Microsoft Corp. 

```


```
zach@yubz:~$ wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

```


-- 

So as you can see, I'm having issues with my phone being detected. The sync module I've blacklisted (rndis_host) since that's all that would be detected previously. It adds an additional entry to my network manager (as eth2) however it's really being a hassle.

Any suggestions on what to do? I can't even get it to work with bluetooth.


edit:
This is what happens when I modprobe rndis_host ->
```
[  141.466847] usb 1-2: USB disconnect, address 4
[  141.653512] usb 1-2: new full speed USB device using uhci_hcd and address 5
[  141.681687] usb 1-2: configuration #1 chosen from 1 choice
[  170.045197] usb 1-2: USB disconnect, address 5
[  197.146226] usb 1-1: new full speed USB device using uhci_hcd and address 6
[  197.154723] usb 1-1: configuration #1 chosen from 1 choice
[  211.392601] usb 1-1: USB disconnect, address 6
[  230.736790] usb 1-1: new full speed USB device using uhci_hcd and address 7
[  230.756977] usb 1-1: configuration #1 chosen from 1 choice
[  242.361861] usb 1-1: USB disconnect, address 7
[  244.333257] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  244.356862] usb 1-1: configuration #1 chosen from 1 choice
[  246.662408] usb 1-1: USB disconnect, address 8
[  247.374402] usb 1-1: new full speed USB device using uhci_hcd and address 9
[  247.396860] usb 1-1: configuration #1 chosen from 1 choice
[  256.738156] usb 1-1: USB disconnect, address 9
[  267.557979] usb 1-1: new full speed USB device using uhci_hcd and address 10
[  267.581571] usb 1-1: configuration #1 chosen from 1 choice
[  269.141529] usb 1-1: USB disconnect, address 10
[  291.901906] usbcore: registered new interface driver cdc_ether
[  291.903127] usbcore: registered new interface driver rndis_host
[  292.070983] usb 1-1: new full speed USB device using uhci_hcd and address 11
[  292.082296] usb 1-1: configuration #1 chosen from 1 choice
[  292.187015] eth2: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, 80:00:60:0f:e8:00
[  293.119452] eth1: deauthenticate(reason=3)

```

---

### Post by motapa on 2008-08-07
I was wrong. This process works perfectly. I went back to my drawing board to see what I had done wrong and found out. I had not included usb after /proc/bus/, and that over rided other drivers. But now I am ok, my modem is working perfectly. Thank you all. Thank you very much. I bet my ISP never thought their modem would work under LINUX.

This is great.

---

### Post by zfouts on 2008-08-08
Finally got it after I used the "USBModem" application that costs $25.

---

### Post by kgantchev on 2008-08-17
The second method worked like a charm!

I have Ubuntu Hardy 8.04 (AMD64)
Kernel Linux 2.22.3

Wireless Card: QUALCOMM 3G CDMA
Interface: PCMCIA
PN: PC5750

Provider: Verizon Wireless

I even use the Gnome PPP dialer (instead of dialing wvdial every time I want to connect).

To use the Gnome PPP dialer just start it from Applications->Internet->GNOME PPP.  The first time you use it you must enter: 
1. Your user name (for vzw users it's [email]your_phone_number@vzw3g.com[/email]).
2. Password (for vzw users the password is vzw)
3. The number to dial (for vzw users it's #777).
4. Click on Setup.
5. Under the modem tab select Type-> USB (the wireless card is considered a USB modem even though it's connected through PCMCIA).
6. Next to device click Detect and it should bring up the /dev/ttyACM0 or whatever device was detected when you plugged in the card.
7. Save the settings and then click Connect on the main GNOME PPP window.
8. The dialer will dial (it's a bit slow, it takes me about 1min+ to connect) and once you're connected you're GOOD TO GO! :)

A note for FireFox users: **make sure that you have Work Offline _UN_checked!!!** Firefox does not detect that you're online, so you have to force it by going to File->Work Offline and un-check the box.

---

### Post by bleedingpowers on 2008-08-21
Thanks,

The **Offline** Firefox trick made it worked. In Kubuntu, using KPPP (and nothing else), everything was just plug, configure a bit, and play. Just needed to enter the right information like in the second post from [http://ubuntuforums.org/showthread.php?t=497445]("http://ubuntuforums.org/showthread.php?t=497445")

By the way, I'm using a Verizon CDMA card (Novatel USB720).

---

### Post by sandmanfvr on 2008-08-28
Something I never could get past:  On my U727 on Ubuntu and Sprint, it works fine, BUT I am limited to 61KB down.  No more.  Can I not get any faster?

---

### Post by Mach1US on 2008-08-29
Which driver do you use ?

---

### Post by scottslinux on 2008-08-31
> **Mach1US said:**
> Thanks john_linuxuser!
Great Job.

just to let you know there is a way to avoid these disconnections that occur at 2:30 .  sudo kwrite and edit the file /etc/ppp/peers/kppp-options

add these lines:

lcp-echo-failure 0
lcp-echo-interval 0

save it and the next time you connect there will be no disconnection. My modem stays up for 24 hours no problem.

I hope that this helps..

Scott
:)

---

### Post by Mach1US on 2008-09-01
Just to let you know , look again at the bottom of the second method (USBserial)and you'll find this, it's always been there, nevertheless thanks for input :

```
Open terminal and type:
Code:

sudo gedit /etc/ppp/peers/wvdial

And insert aditionally those lines:
Code:

lcp-echo-failure 0
lcp-echo-interval 0

Make sure your ethernet jack is unplugged and wifi radio switch is turned off.
Now you can start connection by typing in terminal :
Code:

wvdial


```

---

### Post by foresthill on 2008-09-05
Hi all,

I am using a Kyocera KPC650 PCMCIA card to connect to Cricket broadband. The card works fine in Windows and has been activated, so hardware problems can be eliminated right off the bat.

I am running OpenSuse 11, but the issues seem similar enough to post my question here since no one on the Suse boards seems to be able to answer it.

I was able to get the modem recognized and dialing out through Kinternet, Wvdial, and Gnome Network Manager. However I am not able to get through the authentication process using any of these methods. Here is my Kinternet log:

[PHP]SuSE Meta pppd (smpppd-ifcfg), Version 1.59 on linux-uwcp.
Status is: disconnected
trying to connect to smpppd
connect to smpppd
Status is: disconnected
Status is: connecting
pppd[0]: Plugin passwordfd.so loaded.
pppd[0]: --> WvDial: Internet dialer version 1.56 (abuild@mandelbrot)
pppd[0]: --> Initializing modem.
pppd[0]: --> Sending: ATZ
pppd[0]: ATZ
pppd[0]: OK
pppd[0]: --> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
pppd[0]: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
pppd[0]: OK
pppd[0]: --> Sending: ATM1
pppd[0]: ATM1
pppd[0]: OK
pppd[0]: --> Sending: ATX3
pppd[0]: ATX3
pppd[0]: OK
pppd[0]: --> Modem initialized.
pppd[0]: --> Sending: ATDT#777
pppd[0]: --> Waiting for carrier.
pppd[0]: ATDT#777
pppd[0]: CONNECT
pppd[0]: --> Carrier detected.  Waiting for prompt.
pppd[0]: ~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&[0e];~o}'}"}(}"z:~
pppd[0]: --> PPP negotiation detected.
pppd[0]: Serial connection established.
pppd[0]: Renamed interface ppp0 to modem0
pppd[0]: Using interface modem0
Status is: connecting
pppd[0]: Connect: modem0 <--> /dev/ttyUSB0
pppd[0]: CHAP authentication failed
Authentication error. Maybe bad account or password.
pppd[0]: CHAP authentication failed
Authentication error. Maybe bad account or password.
pppd[0]: Connection terminated.
Status is: disconnected
pppd[0] died: Authentication error (exit code 19)[/PHP]

I have done some reading about pap and chap secret files, and have tried altering the files in every way I can think of with no success.

Earlier in this thread there were some folks getting the same "exit code 19" errors, but I never saw what they did to fix the problem.

So my question is, what can I try next, and does anyone out there have experience connecting to Cricket Broadband in Linux?

---

### Post by Mach1US on 2008-09-05
> **foresthill said:**
> Hi all,

I am using a Kyocera KPC650 PCMCIA card to connect to Cricket broadband. The card works fine in Windows and has been activated, so hardware problems can be eliminated right off the bat.

I am running OpenSuse 11, but the issues seem similar enough to post my question here since no one on the Suse boards seems to be able to answer it.

I was able to get the modem recognized and dialing out through Kinternet, Wvdial, and Gnome Network Manager. However I am not able to get through the authentication process using any of these methods. Here is my Kinternet log:

[PHP]SuSE Meta pppd (smpppd-ifcfg), Version 1.59 on linux-uwcp.
Status is: disconnected
trying to connect to smpppd
connect to smpppd
Status is: disconnected
Status is: connecting
pppd[0]: Plugin passwordfd.so loaded.
pppd[0]: --> WvDial: Internet dialer version 1.56 (abuild@mandelbrot)
pppd[0]: --> Initializing modem.
pppd[0]: --> Sending: ATZ
pppd[0]: ATZ
pppd[0]: OK
pppd[0]: --> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
pppd[0]: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
pppd[0]: OK
pppd[0]: --> Sending: ATM1
pppd[0]: ATM1
pppd[0]: OK
pppd[0]: --> Sending: ATX3
pppd[0]: ATX3
pppd[0]: OK
pppd[0]: --> Modem initialized.
pppd[0]: --> Sending: ATDT#777
pppd[0]: --> Waiting for carrier.
pppd[0]: ATDT#777
pppd[0]: CONNECT
pppd[0]: --> Carrier detected.  Waiting for prompt.
pppd[0]: ~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&[0e];~o}'}"}(}"z:~
pppd[0]: --> PPP negotiation detected.
pppd[0]: Serial connection established.
pppd[0]: Renamed interface ppp0 to modem0
pppd[0]: Using interface modem0
Status is: connecting
pppd[0]: Connect: modem0 <--> /dev/ttyUSB0
pppd[0]: CHAP authentication failed
Authentication error. Maybe bad account or password.
pppd[0]: CHAP authentication failed
Authentication error. Maybe bad account or password.
pppd[0]: Connection terminated.
Status is: disconnected
pppd[0] died: Authentication error (exit code 19)[/PHP]

I have done some reading about pap and chap secret files, and have tried altering the files in every way I can think of with no success.

Earlier in this thread there were some folks getting the same "exit code 19" errors, but I never saw what they did to fix the problem.

So my question is, what can I try next, and does anyone out there have experience connecting to Cricket Broadband in Linux?

Firs of all i have never worked with Cricket Broadband so this is  new one for me.
When comes to special ISP instructions it usually comes down to some proprietary INIT line in a config file, try google for altrnative INIT strings regarding your ISP .
               As a background study a Wiki on Chap ,authentication protocol which is part of PPP protocol used to establish Cell-tower-to-Cell-modem connection.
[http://en.wikipedia.org/wiki/Challenge-handshake_authentication_protocol](http://en.wikipedia.org/wiki/Challenge-handshake_authentication_protocol)
let us know if you get correct INIT ..

---

### Post by foresthill on 2008-09-05
I will study the link. When you say init strings, are you referring to the AT commands that the modem issues when initiating the connection? I had not messed with those, figuring they were irrelevant once a connection was established.

I was also wondering if there is some way I could monitor and save to log file exactly what is happening when the modem connects in Windows and simply recreate that in Linux. Are there network monitoring tools that would reveal the CHAP authentication process on my end?

From looking at the Network settings, I notice that EAP is not enabled, but the boxes for PAP, SPAP, CHAP, MSCHAP, and MSCHAP v2 are all checked, but who knows if they are actually used or not.

I doubt that Cricket uses anything too different than Verizon or any of the other providers though. The phone number used to dial in is #777 and the username is my phone number plus @mycricket.com and the password is blank. 

But that's about all I know for sure so far. :(

---

### Post by foresthill on 2008-09-05
OK, turns out I was using the wrong password. The one that worked was "cricket".

However, my connection speeds are quite bad. Feels like about 56k, or maybe even slower. Anyone have any tips for optimising connection speeds? Does raising the baud rate help at all? I will probably try that first.

Thanks for everyone who posted on this thread and got me this far. Feels great to be rid of Windows while surfing the internet! I hated going back to Windows for the past week. It felt like torture.

EDIT: I was able to connect with my previous set-up, but could not finish loading even the first web page. My data rate never got above 1.5 kb/s and would eventually just stall out.

What I did was re-read the first page of the guide in this thread and edited my wvdial.conf file to change the first init string from ATZ to ATX0. This seemed to make the difference for me, and I can now load web pages fine (knocks on wood).

After spending the last 4 days fighting this series of problems and set-backs, it's almost a let-down to finally have a good reliable internet connection. Oh well, I guess I will get over it.

---

### Post by Mach1US on 2008-09-06
> **foresthill said:**
> 

After spending the last 4 days fighting this series of problems and set-backs, it's almost a let-down to finally have a good reliable internet connection. Oh well, I guess I will get over it.

Hey , CONGRATULATIONS ! =D>
You have actually solved the problem YOURSELF and possibly helped some other poor soul having same problem just as you did , that is the spirit of the open source movement !
Just to make you feel better , two years ago when i got my first EVDO card there was no Ubuntu how-to's what so ever , it took me a MONTH ! to get it working, i'v spent hours many times til 2AM talking with Verizon tech specialist just to hit the web next morning in search of clues that ware inching me closer to the solution.
I have to say i was close to giving up on numerous failed tries, but today you have hordes of posts that spell you all the magic so few hours over few days doesn't seem so severe.
Most importantly i would like to thank you for shareing the solution , i'm sure it'll be a great help to someone.
Keep your spirit up ;)

---

### Post by CaminoSS on 2008-09-07
Procedure worked slick....using a Dell XPS M1530, NVidia Graphics with NVidia driver, Intel Duo 2 Ghz, 3 Gb Ram, Intel Chip set, Intel internal wireless, Ubuntu 8.04, Sierra Wireless 597U (USB)

Cheers...

---

### Post by foresthill on 2008-09-07
> **Mach1US said:**
> Hey , CONGRATULATIONS ! =D>
You have actually solved the problem YOURSELF and possibly helped some other poor soul having same problem just as you did , that is the spirit of the open source movement !
Just to make you feel better , two years ago when i got my first EVDO card there was no Ubuntu how-to's what so ever , it took me a MONTH ! to get it working, i'v spent hours many times til 2AM talking with Verizon tech specialist just to hit the web next morning in search of clues that ware inching me closer to the solution.
I have to say i was close to giving up on numerous failed tries, but today you have hordes of posts that spell you all the magic so few hours over few days doesn't seem so severe.
Most importantly i would like to thank you for shareing the solution , i'm sure it'll be a great help to someone.
Keep your spirit up ;)

Thanks for the encouragement! And also all the grunt work you have done not only in figuring this stuff out for yourself, but helping others above and beyond the C.O.D. It can be very complicated stuff.

My wvdial set up stopped working yesterday so I fought with it for about 12 hours. Every time I dial in, the process behaves slightly different. Sometimes there is CHAP authentication shown in the terminal, sometimes not. Pppd seems to be doing things to try to fix the problem, but it does not tell me exactly what it is up to.

And the various programs you can use to connect don't always share information (e.g. Network Manager, Kppp, Kinternet, Wvdial). If you try to connect in one program it fails for one reason, and so you try another program and it fails for some other reason. Then throw smpppd interaction into the mix, and it gets very confusing.

All I can say for sure now is, it's working, but I'm not entirely sure why, or whether it will still be working this afternoon. 

*crosses fingers*

EDIT: Sure enough it quit working. I could connect OK, but the browser would hang on the first webpage I tried to load. I think it may have to do with compression since the times I was able to connect, I'd see a message in wvdial saying "compression disabled".

So I went into the pppd folder and added to the "Options" file a line saying "nodeflate" and this seems to have done the trick (for now).

EDIT: It's still working 24 hours later, so that was definitely my problem.

---

### Post by dalrympm on 2008-09-18
Confirmed Working

Verizon ExpressCard V740 (Merlin)
Ubuntu 8.04.1
Dell Stuio 1535

Also found [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/]("http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/") that goes over Gnome PPP

I really didn't think this would be so easy.  Thanks.

---

### Post by Mach1US on 2008-09-18
It's probably good idea to add it to this How-To.

---

### Post by OldDirtyTurtle on 2008-09-21
Well, I found this thread after posting a query about setting up the CDU-550 from Franklin Wireless and it went unanswered.  The directions here seemed to work - at least the modem was recognized and dialed.  However, it never got past dialing in wvdial.

Here's the output - any ideas?

```
jason@jason-desktop:~$ wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Sep 21 12:23:34 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5831
--> Using interface ppp0
--> pppd: p[06][08][06][08]
--> pppd: p[06][08][06][08]
--> pppd: p[06][08][06][08]
--> pppd: p[06][08][06][08]
--> Disconnecting at Sun Sep 21 12:23:58 2008
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
```

---

### Post by Mach1US on 2008-09-21
Good news is your modem is installed properly and is functioning as it should this means all Modem-to-Linux was configured correctly .
The only problem is that the cell provider info you provided for your modem to connect is not correct , the values you need to correct can be one of the following :

Incorrect phone number for dial-out (for US Verizon is #777 )
Incorrect Password
Incorrect provider domain or modem phone number
Modem not being activated , wrong ESN,SIM ...

Make sure to correct above user issues as your hardware works correctly and does not need adjusting.

---

### Post by OldDirtyTurtle on 2008-09-22
I realized last night that it should be alltel.net instead of alltel.com.  That fixed it.  Thanks!

---

### Post by foresthill on 2008-09-22
Who is "the peer" anyway? Does that refer to the provider or the user or both? I found this confusing when setting up my CDMA card and trying to decipher error messages.

Also, has anyone worked with fine tuning compression? I have it completely disabled on my system. I need to or the authentication process fails. However, in reading the ppd man file, it sounds as if the amount of compression can be fine-tuned, as well as turned off completely, so I wonder if playing around with this setting might increase my connection speed.

My speeds are quite slow, seemingly slower than dial up at times, especially in the afternoons. And even during times when I can achieve 50-60 kbs per second, the speed drops off after a minute or so to around 8-10 kbs per second, such as when trying to watch a video on YouTube.

Is this typical, or do other people have more reliable connection speeds. I very feel cheated at times when I have to wait 2-3 minutes just for my Yahoo Mail page to load. I'm thinking it's probably due to my provider (Cricket) taking on too many subscribers on their network, but if there's anything I could do on my end to speed things up, I'd like to try it.

---

### Post by rcadby on 2008-09-24
Wow! I sure do thank you. Now, all I have to do is figure out how to use Gnome!

I'm now online with my Pantech UM150 USB modem via Verizon.

A backward newbie.........Ron

---

### Post by joeizang on 2008-09-28
Hey guys,

Just wanted to say i tried this howto with a huawei EC325 CDMA DataModem and it worked alright though it loads the usb drivers anyway from the begining of the process. I am Nigerian so for all those nijah ubuntu users it was what visafone gave and it works. Replied on the visafone link. 

Cheers

---

### Post by omegamormegil on 2008-09-30
> **who_cares said:**
> I messed with my config file and got it to work by adding Init3.
Here's a copy for anyone with the same problem:

That script from page 3 of this thread got my Sierra Wireless Compass 885 3G USB modem working with wvdial, thanks!

---

### Post by ba_rich on 2008-10-06
Great tutorial. I've successfully configured two Novatel U727s to connect to Sprint. The devices show up as ttyUSB0 and ttyUSB4. They are automatically detected on boot. I've manually created the ppp0 and ppp1 connections with wvdial.

What I cannot find in the tutorial is how to automatically start the connections on boot. Do I put wvdial commands in one of the startup scripts? What is the best way?

---

### Post by rg_stephens on 2008-10-07
Thanks for the tutorial. I am having a problem on the desktop computer: I just installed Hardy Heron on this machine. I can connect using the tethered LG phone and the PPP0 connection shows up when I type *ifconfig* but the connection isn't recognized by Network Monitor, and I can't connect to the net. 

Do I need to update my programs? If so I'll have to find a different way to connect. I've already rebooted the machine.

**ba_rich**, you can add wvdial to the sessions menu so that it automatically starts, but I haven't tried it yet. The modem will have to be plugged in when you start the machine. Others have done it, so try searching this thread.

EDIT: Yes, it works!
And I fixed the desktop computer by unplugging it's Ethernet adapter...

---

### Post by carterw65 on 2008-10-07
Hello!

I have a PX-500. I have been trying to get this thing working. I have no other internet. I have got so far as:

Carrier detected. Starting PPP imediately
Unable to run /usr/sbin/pppd.
Check permissions, or specify a "PPPD Path" option in wvdial.conf.

Any thoughts???

Thanks a bunch,

Bill

---

### Post by carterw65 on 2008-10-07
Silly me, I typed "sudo wvdial" and it worked. Now it's surf city!

---

### Post by zoomy942 on 2008-10-08
here is what i get...

i know i am so close!

```
 zimmerman@ubuntu-tablet:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
zimmerman@ubuntu-tablet:~$ 

```

---

### Post by foresthill on 2008-10-08
Unplug your device and run this command

[PHP]sudo dmesg -c[/PHP]

This will clear the info. Wait 20 seconds and plug it back in and run this command:

[PHP]sudo dmesg[/PHP]

You should get a listing of where your device is located (dev/ttyUSB0 or something similar).

Use this info to add to your wvdial script.

It looks like you just need to add the name of the correct device.

(NOTE: This works in OpenSuse, so no guarantee it will work in Ubuntu, but it's worth a try).

---

### Post by Mach1US on 2008-10-12
> **zoomy942 said:**
> here is what i get...

i know i am so close!

```
 zimmerman@ubuntu-tablet:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
zimmerman@ubuntu-tablet:~$ 

```

Can you post your wvdial.conf and dmesg output immidietaly after you plug your evdo card in .

---

### Post by Nameless Neko on 2008-10-24
Alright, I've got my UM150 working under Ubuntu, but it won't connect to any websites unless my networking is disabled.  Is there any way to get it working with the network going?  I need to set it up so that the connection is shared out through my wireless router out to a couple of laptops in the house.  Here's the setup:

                                                    /Laptop (Ubuntu 8.04)
UM150 EVDO -> Desktop PC (Ubuntu) -> Wireless router
                                                    \Laptop (Vista)

The desktop PC has two network interfaces - one runs to the internet port on the router to share the network connection, another to port 1 to share files.  It works flawlessly for me under XP, but I'm having issues with it in Ubuntu.  Any advice?

---

### Post by Mach1US on 2008-10-25
I did it with dapper and what i needed was to remove Network-Manager and set up all interfaces from command line and it was working fine.
This days i always recommend hardware solution as Evdo routers became cheap , with multiple choices in brand and functionality. While some are the size of a deck of cards and battery powered the most beneficial feature is that they provide gateway services without the overhead of running another PC just for internet access , additionally routing traffic on a PC requires additional precessing which in turn degrades the performance.
Again if you running your Gateway PC as a home server it may make sense to let it handle routing and firewall solution, like i said you will need to set it up manually without Network-Manager,for some reason Network-Manger does not like external input controlling networking functions .
Hope this helps.

---

### Post by Nameless Neko on 2008-10-25
> **Mach1US said:**
> I did it with dapper and what i needed was to remove Network-Manager and set up all interfaces from command line and it was working fine.
This days i always recommend hardware solution as Evdo routers became cheap , with multiple choices in brand and functionality. While some are the size of a deck of cards and battery powered the most beneficial feature is that they provide gateway services without the overhead of running another PC just for internet access , additionally routing traffic on a PC requires additional precessing which in turn degrades the performance.
Again if you running your Gateway PC as a home server it may make sense to let it handle routing and firewall solution, like i said you will need to set it up manually without Network-Manager,for some reason Network-Manger does not like external input controlling networking functions .
Hope this helps.Hm, got a link to a cheap EVDO router?  The only one tigerdirect came up with in a quick search was nearly 200 dollars, which is a bit out of my price range at the moment, till I find a new job :(
I'll give your advice about dropping network-manager a shot tonight, after my fiancee goes to sleep and I don't need a steady net connection.  Thanks!

---

### Post by Mach1US on 2008-10-25
```
$109  Kyocera KR1
http://www.amazon.com/Kyocera-KR1-Mobile-Router-Wireless/dp/B000IOYW5W/ref=sr_1_19?ie=UTF8&s=electronics&qid=1224976423&sr=1-19

$124  Linksys 3G
http://www.amazon.com/Linksys-Wireless-G-Router-Mobile-Broadband/dp/B000E0VM30/ref=dp_cp_ob_e_title_2

$133 D-link DIR-450 3G Wireless Mobile Router
http://www.techforless.com/cgi-bin/tech4less/DIR-450?mv_pc=nextag&tts=20081025151223

$139 Cradlepoint CTR-350 
http://www.amazon.com/Cradlepoint-CTR350-Cellular-Travel-Router/dp/B000UO18FC/ref=pd_cp_cps_1_img?pf_rd_p=413863801&pf_rd_s=center-41&pf_rd_t=201&pf_rd_i=B001212ELY&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=1TNBQ67BB4W0KPCHZT04
```

I have KR1 in my car because i use PC-card(PC5750) and i paid $78 for it on e-bay, it comes with wall as well as car(cigarette lighter) power adapter and has PC-card slot and USB port for EVDO card or phone.
The only complain i have that it takes about 45 to 50 sec to initialize but once connected works flawlessly.
I have also bought few Cradle point routers for USB modem folks, they and they rave about them so i would suggest looking into that one too.
Cradlepoint sales portable one with battery power option.
[http://www.evdoinfo.com/content/view/2201/63/](http://www.evdoinfo.com/content/view/2201/63/)
Make sure to check if the one you buying supports your card, same my require latest firmware for newest cards but it's ekstremaly easy to upload it.
Hopefully you can find one that fits your price range and desired features.

---

### Post by afterburnais on 2008-10-31
> **joeizang said:**
> Hey guys,

Just wanted to say i tried this howto with a huawei EC325 CDMA DataModem and it worked alright though it loads the usb drivers anyway from the begining of the process. I am Nigerian so for all those nijah ubuntu users it was what visafone gave and it works. Replied on the visafone link. 

Cheers
hi
i'm nigerian and I am using the visafone Huawei EC226 usb modem and i installed gnome ppp on intrepid ibex,gnome ppp seems to read the modem but each time i try to connect,this shows up in the log


--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
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
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }=}!}$}%\}"}&} } } } }#}%B#}%}%}& I1^}'}"}(}"[0f]-~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& I_N}'}"}(}"[17]c~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& I*[15]}'}"}(}",Z~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& I)[12]}'}"}(}"}3(~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& I[0e])}'}"}(}"}0W~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

 i really dont know what else i should be doing being a noob and all.pls any help will be appreciated.

---

### Post by Mach1US on 2008-10-31
Try running it with gksudo privileges .

---

### Post by afterburnais on 2008-10-31
all i got when i ran wvdial was this

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
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

any ideas i can fix this.ive been trying to get this to work thsi 7.04 with a different card and still no luck

---

### Post by Mach1US on 2008-10-31
make sure that wvdial.conf contains correct phone number for your Cell-ISP provider.
The #777 is generic to most US based cell providers, additionally the domain name and format of password is proprietary to your cell provider and it's crucial for successful connection.
    On the bright side from the output it looks that your modem communicates with your kernel properly so i would suggest contacting your cell provider and adjusting to their requests, that is the only thing that you are missing.
Just for verification post your wvdial.conf

---

### Post by afterburnais on 2008-10-31
here is my wvdial.conf, i substituted the details with the username ,password and number which is #777 here,just like in the US.

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>

thanks for the help,really appreciated.here's hoping it finally works.

---

### Post by Mach1US on 2008-11-01
I see the problem,

You NEED to correct following fields:
```
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>
```
first of all remove " [COLOR="Red"];[/COLOR] " symbol from the beginning of the previous lines .

Secondly, _INSERT_correct
1- Target phone number   !!!
2- ISP password for your EVDO connection
3- Login User Name ( US verizon uses **@vzw3g.com** after your assigned cell number {**917-345-5678** )while entering number _DO NOT_ use dashes (-) .

Make sure to use correct Domain (after @ sign )

You are really close, all you need to correct those 3 fields.
Let me know how it went:)

---

### Post by afterburnais on 2008-11-01
well,somethins changed at least,heres what i got when i made the changes,still no connection though.its cool though,it never got this far anyway.

adamu@Bumblebee:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.
~[7f]}#@!}!} } }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[02]+}1I}'}"}(}"?2~~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[02]+[07]W}'}"}(}"d|~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[02]+X*}'}"}(}"[1a]7~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[02]+[19] }'}"}(}"eV~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[02]+@M}'}"}(}".{~

thanks.

---

### Post by Mach1US on 2008-11-01
It says that it has lost carrier signal, try some other location where you know that the signal strength is good. 
Ware you able to connect at this location via another OS like windows ?

---

### Post by afterburnais on 2008-11-01
> **Mach1US said:**
> It says that it has lost carrier signal, try some other location where you know that the signal strength is good. 
Ware you able to connect at this location via another OS like windows ?

i works really well on windows xp with full signal.

---

### Post by Mach1US on 2008-11-01
Ok , I've looked over your wvdial.conf and next thing we'll try is this:
```
      replace line:
Init1 = ATZ 
 
        with this:
Init1 = ATX0

        and add this :
Stupid Mode = on
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```

If you'll still have problem post what is the output when you run **sudo wvdial**command in terminal, also post what your wvdial.conf looks like now.
Make sure to use a wvdial from command line .

---

### Post by afterburnais on 2008-11-02
here is the wvdial.conf 

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
 Phone = #777
ISDN = 0
 Username = [email]x@visafone.com.ng[/email]
Init1 = ATX0
 Password = x
Modem = /dev/ttyUSB0
Baud = 9600
Stupid Mode = on
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP

and here is the output when i run wvdial from terminal

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX0
ATX0
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!} } }=}!}$}%\}"}&} } } } }#}%B#}%}%}& }9+[17]}'}"}(}"n[02]~~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& }8x}&}'}"}(}"J/~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& }9 $}'}"}(}"lx~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& }99J}'}"}(}"x}1~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}& }9zN}'}"}(}"<H~

just for this post i put x's in place of the username and password but in the actual file its the real username and password.i have this feeling that we are close to a solution,thanks for all the help,greatly appreciated.

---

### Post by Mach1US on 2008-11-02
Insert this into wvdial.conf 
```
New PPPD = yes
```
Run it from command line and if still having problem post both outputs again.

---

### Post by afterburnais on 2008-11-02
you are a genius,it finally works!!!!after a whole yr+ of trying everything it finally works,you rock!!!now i'm closer to my mission of dumping windows entirely,bwa ha ha!!!
thanks for all the help,greatly appreciated.

sorry to bother you again,i had another card that i stopped using because it doesnt even read on ubuntu,if its not too much trouble when i find it,can you help me with setup tips for that one?thanks again

---

### Post by Mach1US on 2008-11-02
Glad it worked and  sure, drop me a line and we'll see what we can do.

---

### Post by TechDragon on 2008-11-06
Can you help me too please,

wvdial.conf
```

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = #777
ISDN = 0
Username = phonenumber@sprintpcs.com
Init1 = ATX0
Password = x
Modem = /dev/ttyUSB0
Baud = 9600
Stupid Mode = on
Auto Reconnect = on
Carrier Check = no
[Dialer shh]
Init3 = ATM0
[Dialer pulse]
New PPPD = yes
Dial Command = ATDP
```

output
```
cisco@catalyst-3750g:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
cisco@catalyst-3750g:~$ 
```

---

### Post by Mach1US on 2008-11-06
First we'll give it a long shot,in wvdial.conf change 
```
Modem = /dev/ttyUSB0 
to:
Modem = /dev/ttyACM0
```
Try to connect then take out your evdo card, insert it back again then in terminal type:   dmesg   and post your output.

---

### Post by TechDragon on 2008-11-07
First, THANK YOU

Second:
Equipment
Laptop is an IBM T61 apears to be all intel except for nvidia video
USB Sprint Card -- Novatel Ovation u727

Third, that didn't fix it when I do a dmesg my output is so large that it deletes the first part but here is what I have, I have been fighting this for a week or so and even upgraded to IBEX hoping that the new network manager would fix it.  No such luck. :)

> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
cisco@catalyst-3750g:~$ 


```
[ 1159.037259] end_request: I/O error, dev sr1, sector 12160
[ 1159.103267] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1159.103302] sr: Sense Key : No Sense [current] 
[ 1159.103312] sr: Add. Sense: No additional sense information
[ 1159.632268] end_request: I/O error, dev sr1, sector 12160
[ 1159.697263] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1159.697297] sr: Sense Key : No Sense [current] 
[ 1159.697307] sr: Add. Sense: No additional sense information
[ 1160.232255] end_request: I/O error, dev sr1, sector 12160
[ 1160.297298] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1160.297333] sr: Sense Key : No Sense [current] 
[ 1160.297342] sr: Add. Sense: No additional sense information
[ 1160.835246] end_request: I/O error, dev sr1, sector 12160
[ 1160.835258] __ratelimit: 206 callbacks suppressed
[ 1160.835265] Buffer I/O error on device sr1, logical block 1520
[ 1160.835335] Buffer I/O error on device sr1, logical block 1520
[ 1160.835391] Buffer I/O error on device sr1, logical block 1534
[ 1160.835412] Buffer I/O error on device sr1, logical block 1534
[ 1160.835473] Buffer I/O error on device sr1, logical block 4
[ 1160.835496] Buffer I/O error on device sr1, logical block 5
[ 1160.835549] Buffer I/O error on device sr1, logical block 1535
[ 1160.835570] Buffer I/O error on device sr1, logical block 1535
[ 1160.835602] Buffer I/O error on device sr1, logical block 1535
[ 1160.835635] Buffer I/O error on device sr1, logical block 1535
[ 1160.907251] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1160.907284] sr: Sense Key : No Sense [current] 
[ 1160.907293] sr: Add. Sense: No additional sense information
[ 1161.435248] end_request: I/O error, dev sr1, sector 12160
[ 1161.502306] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1161.502340] sr: Sense Key : No Sense [current] 
[ 1161.502349] sr: Add. Sense: No additional sense information
[ 1162.031256] end_request: I/O error, dev sr1, sector 12160
[ 1162.097291] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1162.097327] sr: Sense Key : No Sense [current] 
[ 1162.097337] sr: Add. Sense: No additional sense information
[ 1162.631272] end_request: I/O error, dev sr1, sector 12160
[ 1162.705298] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1162.705333] sr: Sense Key : No Sense [current] 
[ 1162.705343] sr: Add. Sense: No additional sense information
[ 1163.242246] end_request: I/O error, dev sr1, sector 12160
[ 1163.313308] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1163.313343] sr: Sense Key : No Sense [current] 
[ 1163.313352] sr: Add. Sense: No additional sense information
[ 1163.844213] end_request: I/O error, dev sr1, sector 12160
[ 1163.907211] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1163.907229] sr: Sense Key : No Sense [current] 
[ 1163.907233] sr: Add. Sense: No additional sense information
[ 1164.436249] end_request: I/O error, dev sr1, sector 12160
[ 1164.516249] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1164.516285] sr: Sense Key : No Sense [current] 
[ 1164.516295] sr: Add. Sense: No additional sense information
[ 1165.055260] end_request: I/O error, dev sr1, sector 12160
[ 1165.164316] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1165.164349] sr: Sense Key : No Sense [current] 
[ 1165.164359] sr: Add. Sense: No additional sense information
[ 1165.694247] end_request: I/O error, dev sr1, sector 12160
[ 1165.760267] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1165.760302] sr: Sense Key : No Sense [current] 
[ 1165.760312] sr: Add. Sense: No additional sense information
[ 1166.298251] end_request: I/O error, dev sr1, sector 12160
[ 1166.298265] __ratelimit: 206 callbacks suppressed
[ 1166.298272] Buffer I/O error on device sr1, logical block 1520
[ 1166.298331] Buffer I/O error on device sr1, logical block 1520
[ 1166.298395] Buffer I/O error on device sr1, logical block 1534
[ 1166.298417] Buffer I/O error on device sr1, logical block 1534
[ 1166.298478] Buffer I/O error on device sr1, logical block 4
[ 1166.298500] Buffer I/O error on device sr1, logical block 5
[ 1166.298553] Buffer I/O error on device sr1, logical block 1535
[ 1166.298573] Buffer I/O error on device sr1, logical block 1535
[ 1166.298606] Buffer I/O error on device sr1, logical block 1535
[ 1166.298640] Buffer I/O error on device sr1, logical block 1535
[ 1166.364261] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1166.364304] sr: Sense Key : No Sense [current] 
[ 1166.364314] sr: Add. Sense: No additional sense information
[ 1166.895266] end_request: I/O error, dev sr1, sector 12160
[ 1166.969296] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1166.969332] sr: Sense Key : No Sense [current] 
[ 1166.969342] sr: Add. Sense: No additional sense information
[ 1167.506267] end_request: I/O error, dev sr1, sector 12160
[ 1167.572491] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1167.572525] sr: Sense Key : No Sense [current] 
[ 1167.572534] sr: Add. Sense: No additional sense information
[ 1168.102259] end_request: I/O error, dev sr1, sector 12160
[ 1168.168300] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1168.168334] sr: Sense Key : No Sense [current] 
[ 1168.168343] sr: Add. Sense: No additional sense information
[ 1168.698258] end_request: I/O error, dev sr1, sector 12160
[ 1168.771257] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1168.771292] sr: Sense Key : No Sense [current] 
[ 1168.771302] sr: Add. Sense: No additional sense information
[ 1169.301236] end_request: I/O error, dev sr1, sector 12160
[ 1169.360266] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1169.360289] sr: Sense Key : No Sense [current] 
[ 1169.360295] sr: Add. Sense: No additional sense information
[ 1169.901222] end_request: I/O error, dev sr1, sector 12160
[ 1169.967301] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1169.967337] sr: Sense Key : No Sense [current] 
[ 1169.967347] sr: Add. Sense: No additional sense information
[ 1170.506261] end_request: I/O error, dev sr1, sector 12160
[ 1170.584355] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1170.584391] sr: Sense Key : No Sense [current] 
[ 1170.584401] sr: Add. Sense: No additional sense information
[ 1171.115228] end_request: I/O error, dev sr1, sector 12160
[ 1171.186324] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1171.186360] sr: Sense Key : No Sense [current] 
[ 1171.186370] sr: Add. Sense: No additional sense information
[ 1171.720236] end_request: I/O error, dev sr1, sector 12160
[ 1171.720247] __ratelimit: 206 callbacks suppressed
[ 1171.720252] Buffer I/O error on device sr1, logical block 1520
[ 1171.720301] Buffer I/O error on device sr1, logical block 1520
[ 1171.720351] Buffer I/O error on device sr1, logical block 1534
[ 1171.720366] Buffer I/O error on device sr1, logical block 1534
[ 1171.720410] Buffer I/O error on device sr1, logical block 4
[ 1171.720425] Buffer I/O error on device sr1, logical block 5
[ 1171.720462] Buffer I/O error on device sr1, logical block 1535
[ 1171.720476] Buffer I/O error on device sr1, logical block 1535
[ 1171.720498] Buffer I/O error on device sr1, logical block 1535
[ 1171.720519] Buffer I/O error on device sr1, logical block 1535
[ 1171.780264] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1171.780301] sr: Sense Key : No Sense [current] 
[ 1171.780311] sr: Add. Sense: No additional sense information
[ 1171.911184] Inbound IN=eth0 OUT= MAC=00:1c:25:74:52:a6:00:0a:b8:df:29:44:08:00 SRC=209.85.239.31 DST=10.12.12.173 LEN=40 TOS=0x00 PREC=0x00 TTL=62 ID=41900 DF PROTO=TCP SPT=80 DPT=57330 WINDOW=4096 RES=0x00 ACK URGP=0 
[ 1172.315264] end_request: I/O error, dev sr1, sector 12160
[ 1172.383260] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1172.383293] sr: Sense Key : No Sense [current] 
[ 1172.383303] sr: Add. Sense: No additional sense information
[ 1172.913211] end_request: I/O error, dev sr1, sector 12160
[ 1172.972303] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1172.972338] sr: Sense Key : No Sense [current] 
[ 1172.972347] sr: Add. Sense: No additional sense information
[ 1173.504254] end_request: I/O error, dev sr1, sector 12160
[ 1173.570264] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1173.570298] sr: Sense Key : No Sense [current] 
[ 1173.570308] sr: Add. Sense: No additional sense information
[ 1174.120312] end_request: I/O error, dev sr1, sector 12160
[ 1174.183221] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1174.183238] sr: Sense Key : No Sense [current] 
[ 1174.183242] sr: Add. Sense: No additional sense information
[ 1174.716236] end_request: I/O error, dev sr1, sector 12160
[ 1174.790316] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1174.790352] sr: Sense Key : No Sense [current] 
[ 1174.790362] sr: Add. Sense: No additional sense information
[ 1175.325252] end_request: I/O error, dev sr1, sector 12160
[ 1175.391265] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1175.391299] sr: Sense Key : No Sense [current] 
[ 1175.391309] sr: Add. Sense: No additional sense information
[ 1175.921255] end_request: I/O error, dev sr1, sector 12160
[ 1175.990269] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1175.990305] sr: Sense Key : No Sense [current] 
[ 1175.990314] sr: Add. Sense: No additional sense information
[ 1176.527245] end_request: I/O error, dev sr1, sector 12160
[ 1176.599306] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1176.599340] sr: Sense Key : No Sense [current] 
[ 1176.599349] sr: Add. Sense: No additional sense information
[ 1177.130254] end_request: I/O error, dev sr1, sector 12160
[ 1177.130269] __ratelimit: 206 callbacks suppressed
[ 1177.130277] Buffer I/O error on device sr1, logical block 1520
[ 1177.130355] Buffer I/O error on device sr1, logical block 1520
[ 1177.130416] Buffer I/O error on device sr1, logical block 1534
[ 1177.130437] Buffer I/O error on device sr1, logical block 1534
[ 1177.130498] Buffer I/O error on device sr1, logical block 4
[ 1177.130520] Buffer I/O error on device sr1, logical block 5
[ 1177.130572] Buffer I/O error on device sr1, logical block 1535
[ 1177.130592] Buffer I/O error on device sr1, logical block 1535
[ 1177.130623] Buffer I/O error on device sr1, logical block 1535
[ 1177.130656] Buffer I/O error on device sr1, logical block 1535
[ 1177.195294] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1177.195329] sr: Sense Key : No Sense [current] 
[ 1177.195338] sr: Add. Sense: No additional sense information
[ 1177.732263] end_request: I/O error, dev sr1, sector 12160
[ 1177.799295] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1177.799331] sr: Sense Key : No Sense [current] 
[ 1177.799341] sr: Add. Sense: No additional sense information
[ 1178.335266] end_request: I/O error, dev sr1, sector 12160
[ 1178.404259] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1178.404293] sr: Sense Key : No Sense [current] 
[ 1178.404302] sr: Add. Sense: No additional sense information
[ 1178.936258] end_request: I/O error, dev sr1, sector 12160
[ 1179.011303] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1179.011338] sr: Sense Key : No Sense [current] 
[ 1179.011348] sr: Add. Sense: No additional sense information
[ 1179.541251] end_request: I/O error, dev sr1, sector 12160
[ 1179.661230] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1179.661246] sr: Sense Key : No Sense [current] 
[ 1179.661250] sr: Add. Sense: No additional sense information
[ 1180.195261] end_request: I/O error, dev sr1, sector 12160
[ 1180.261301] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1180.261335] sr: Sense Key : No Sense [current] 
[ 1180.261345] sr: Add. Sense: No additional sense information
[ 1180.791246] end_request: I/O error, dev sr1, sector 12160
[ 1180.864275] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1180.864314] sr: Sense Key : No Sense [current] 
[ 1180.864324] sr: Add. Sense: No additional sense information
[ 1181.394249] end_request: I/O error, dev sr1, sector 12160
[ 1181.459265] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1181.459298] sr: Sense Key : No Sense [current] 
[ 1181.459307] sr: Add. Sense: No additional sense information
[ 1181.990253] end_request: I/O error, dev sr1, sector 12160
[ 1182.056309] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1182.056345] sr: Sense Key : No Sense [current] 
[ 1182.056355] sr: Add. Sense: No additional sense information
[ 1182.592252] end_request: I/O error, dev sr1, sector 12160
[ 1182.592267] __ratelimit: 206 callbacks suppressed
[ 1182.592274] Buffer I/O error on device sr1, logical block 1520
[ 1182.593445] Buffer I/O error on device sr1, logical block 1520
[ 1183.104234] end_request: I/O error, dev sr1, sector 12272
[ 1183.104245] Buffer I/O error on device sr1, logical block 1534
[ 1183.104630] Buffer I/O error on device sr1, logical block 1534
[ 1183.105324] Buffer I/O error on device sr1, logical block 4
[ 1183.106143] Buffer I/O error on device sr1, logical block 5
[ 1183.106993] Buffer I/O error on device sr1, logical block 1535
[ 1183.107369] Buffer I/O error on device sr1, logical block 1535
[ 1183.108239] Buffer I/O error on device sr1, logical block 1535
[ 1183.109147] Buffer I/O error on device sr1, logical block 1535
[ 1183.169264] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1183.169298] sr: Sense Key : No Sense [current] 
[ 1183.169308] sr: Add. Sense: No additional sense information
[ 1183.699258] end_request: I/O error, dev sr1, sector 12160
[ 1183.765300] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1183.765336] sr: Sense Key : No Sense [current] 
[ 1183.765346] sr: Add. Sense: No additional sense information
[ 1184.301259] end_request: I/O error, dev sr1, sector 12160
[ 1184.367269] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1184.367302] sr: Sense Key : No Sense [current] 
[ 1184.367312] sr: Add. Sense: No additional sense information
[ 1184.899267] end_request: I/O error, dev sr1, sector 12160
[ 1184.971308] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1184.971345] sr: Sense Key : No Sense [current] 
[ 1184.971355] sr: Add. Sense: No additional sense information
[ 1185.507251] end_request: I/O error, dev sr1, sector 12160
[ 1185.573293] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1185.573328] sr: Sense Key : No Sense [current] 
[ 1185.573337] sr: Add. Sense: No additional sense information
[ 1186.103259] end_request: I/O error, dev sr1, sector 12160
[ 1186.169302] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1186.169338] sr: Sense Key : No Sense [current] 
[ 1186.169348] sr: Add. Sense: No additional sense information
[ 1186.704261] end_request: I/O error, dev sr1, sector 12160
[ 1186.777318] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1186.777352] sr: Sense Key : No Sense [current] 
[ 1186.777361] sr: Add. Sense: No additional sense information
[ 1187.306255] end_request: I/O error, dev sr1, sector 12160
[ 1187.371304] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1187.371340] sr: Sense Key : No Sense [current] 
[ 1187.371350] sr: Add. Sense: No additional sense information
[ 1187.906250] end_request: I/O error, dev sr1, sector 12160
[ 1187.906266] __ratelimit: 182 callbacks suppressed
[ 1187.906273] Buffer I/O error on device sr1, logical block 1520
[ 1187.906321] Buffer I/O error on device sr1, logical block 1520
[ 1187.907853] Buffer I/O error on device sr1, logical block 1534
[ 1187.909737] Buffer I/O error on device sr1, logical block 1534
[ 1187.911601] Buffer I/O error on device sr1, logical block 4
[ 1187.913344] Buffer I/O error on device sr1, logical block 5
[ 1187.915107] Buffer I/O error on device sr1, logical block 1535
[ 1187.917236] Buffer I/O error on device sr1, logical block 1535
[ 1187.919583] Buffer I/O error on device sr1, logical block 1535
[ 1187.921974] Buffer I/O error on device sr1, logical block 1535
[ 1187.991268] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1187.991300] sr: Sense Key : No Sense [current] 
[ 1187.991310] sr: Add. Sense: No additional sense information
[ 1188.520257] end_request: I/O error, dev sr1, sector 12160
[ 1188.593309] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1188.593345] sr: Sense Key : No Sense [current] 
[ 1188.593354] sr: Add. Sense: No additional sense information
[ 1189.130255] end_request: I/O error, dev sr1, sector 12160
[ 1189.198265] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1189.198298] sr: Sense Key : No Sense [current] 
[ 1189.198307] sr: Add. Sense: No additional sense information
[ 1189.280269] usb 4-2: USB disconnect, address 2
[ 1189.280288] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.280302] end_request: I/O error, dev sr1, sector 12160
[ 1189.280454] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.280462] end_request: I/O error, dev sr1, sector 12160
[ 1189.280634] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.280645] end_request: I/O error, dev sr1, sector 12272
[ 1189.280771] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.280780] end_request: I/O error, dev sr1, sector 12272
[ 1189.281028] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281037] end_request: I/O error, dev sr1, sector 32
[ 1189.281150] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281158] end_request: I/O error, dev sr1, sector 40
[ 1189.281258] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281266] end_request: I/O error, dev sr1, sector 12280
[ 1189.281391] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281400] end_request: I/O error, dev sr1, sector 12280
[ 1189.281541] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281550] end_request: I/O error, dev sr1, sector 12280
[ 1189.281692] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281700] end_request: I/O error, dev sr1, sector 12280
[ 1189.281838] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281846] end_request: I/O error, dev sr1, sector 12280
[ 1189.281985] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.281995] end_request: I/O error, dev sr1, sector 12280
[ 1189.282138] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.282147] end_request: I/O error, dev sr1, sector 12280
[ 1189.282294] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.282303] end_request: I/O error, dev sr1, sector 12224
[ 1189.282440] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.282449] end_request: I/O error, dev sr1, sector 12272
[ 1189.282588] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.282597] end_request: I/O error, dev sr1, sector 12280
[ 1189.282735] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.282743] end_request: I/O error, dev sr1, sector 12280
[ 1189.282975] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.282986] end_request: I/O error, dev sr1, sector 32
[ 1189.283140] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.283150] end_request: I/O error, dev sr1, sector 32
[ 1189.283305] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.283314] end_request: I/O error, dev sr1, sector 32
[ 1189.283463] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.283472] end_request: I/O error, dev sr1, sector 32
[ 1189.283623] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.283634] end_request: I/O error, dev sr1, sector 32
[ 1189.283814] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.283824] end_request: I/O error, dev sr1, sector 32
[ 1189.283972] sr 2:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1189.283981] end_request: I/O error, dev sr1, sector 32
[ 1243.712148] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 1243.871505] usb 4-2: configuration #1 chosen from 1 choice
[ 1243.884701] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1243.887779] usb-storage: device found at 3
[ 1243.887793] usb-storage: waiting for device to settle before scanning
[ 1248.886478] usb-storage: device scan complete
[ 1248.889373] scsi 3:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
[ 1248.924379] sr1: scsi-1 drive
[ 1248.924970] sr 3:0:0:0: Attached scsi CD-ROM sr1
[ 1248.926428] sr 3:0:0:0: Attached scsi generic sg2 type 5
[ 1249.110242] sr1: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
[ 1249.110258] sr: Sense Key : No Sense [current] 
[ 1249.110262] sr: Add. Sense: No additional sense information
[ 1249.242197] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1249.242237] sr: Sense Key : No Sense [current] 
[ 1249.242246] sr: Add. Sense: No additional sense information
[ 1249.798238] end_request: I/O error, dev sr1, sector 12160
[ 1249.798254] __ratelimit: 86 callbacks suppressed
[ 1249.798262] Buffer I/O error on device sr1, logical block 1520
[ 1249.800099] Buffer I/O error on device sr1, logical block 1520
[ 1249.800161] Buffer I/O error on device sr1, logical block 1534
[ 1249.800187] Buffer I/O error on device sr1, logical block 1534
[ 1249.800249] Buffer I/O error on device sr1, logical block 4
[ 1249.800272] Buffer I/O error on device sr1, logical block 5
[ 1249.800324] Buffer I/O error on device sr1, logical block 1535
[ 1249.800344] Buffer I/O error on device sr1, logical block 1535
[ 1249.800375] Buffer I/O error on device sr1, logical block 1535
[ 1249.800407] Buffer I/O error on device sr1, logical block 1535
[ 1249.814253] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1249.814285] sr: Sense Key : No Sense [current] 
[ 1249.814295] sr: Add. Sense: No additional sense information
[ 1249.928269] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1249.928306] sr: Sense Key : No Sense [current] 
[ 1249.928316] sr: Add. Sense: No additional sense information
[ 1250.467237] end_request: I/O error, dev sr1, sector 12160
[ 1250.496303] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1250.496337] sr: Sense Key : No Sense [current] 
[ 1250.496347] sr: Add. Sense: No additional sense information
[ 1250.619246] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1250.619280] sr: Sense Key : No Sense [current] 
[ 1250.619289] sr: Add. Sense: No additional sense information
[ 1251.152247] end_request: I/O error, dev sr1, sector 12160
[ 1251.222363] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1251.222398] sr: Sense Key : No Sense [current] 
[ 1251.222407] sr: Add. Sense: No additional sense information
[ 1251.763242] end_request: I/O error, dev sr1, sector 12160
[ 1251.844254] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1251.844289] sr: Sense Key : No Sense [current] 
[ 1251.844298] sr: Add. Sense: No additional sense information
[ 1252.379245] end_request: I/O error, dev sr1, sector 12160
[ 1252.445306] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1252.445342] sr: Sense Key : No Sense [current] 
[ 1252.445351] sr: Add. Sense: No additional sense information
[ 1252.987239] end_request: I/O error, dev sr1, sector 12160
[ 1253.053294] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1253.053328] sr: Sense Key : No Sense [current] 
[ 1253.053337] sr: Add. Sense: No additional sense information
[ 1253.585243] end_request: I/O error, dev sr1, sector 12160
[ 1253.657301] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1253.657336] sr: Sense Key : No Sense [current] 
[ 1253.657346] sr: Add. Sense: No additional sense information
[ 1254.192238] end_request: I/O error, dev sr1, sector 12160
[ 1254.257301] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1254.257336] sr: Sense Key : No Sense [current] 
[ 1254.257346] sr: Add. Sense: No additional sense information
[ 1254.791247] end_request: I/O error, dev sr1, sector 12160
[ 1254.854214] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1254.854228] sr: Sense Key : No Sense [current] 
[ 1254.854232] sr: Add. Sense: No additional sense information
[ 1255.383244] end_request: I/O error, dev sr1, sector 12160
[ 1255.383260] __ratelimit: 233 callbacks suppressed
[ 1255.383267] Buffer I/O error on device sr1, logical block 1520
[ 1255.383345] Buffer I/O error on device sr1, logical block 1520
[ 1255.383414] Buffer I/O error on device sr1, logical block 1534
[ 1255.383437] Buffer I/O error on device sr1, logical block 1534
[ 1255.383500] Buffer I/O error on device sr1, logical block 4
[ 1255.383523] Buffer I/O error on device sr1, logical block 5
[ 1255.383577] Buffer I/O error on device sr1, logical block 1535
[ 1255.383597] Buffer I/O error on device sr1, logical block 1535
[ 1255.383628] Buffer I/O error on device sr1, logical block 1535
[ 1255.383660] Buffer I/O error on device sr1, logical block 1535
[ 1255.449282] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1255.449317] sr: Sense Key : No Sense [current] 
[ 1255.449327] sr: Add. Sense: No additional sense information
[ 1255.986240] end_request: I/O error, dev sr1, sector 12160
[ 1256.045303] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1256.045339] sr: Sense Key : No Sense [current] 
[ 1256.045349] sr: Add. Sense: No additional sense information
[ 1256.582254] end_request: I/O error, dev sr1, sector 12160
[ 1256.649300] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1256.649336] sr: Sense Key : No Sense [current] 
[ 1256.649346] sr: Add. Sense: No additional sense information
[ 1257.184219] end_request: I/O error, dev sr1, sector 12160
[ 1257.247287] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1257.247320] sr: Sense Key : No Sense [current] 
[ 1257.247330] sr: Add. Sense: No additional sense information
[ 1257.778244] end_request: I/O error, dev sr1, sector 12160
[ 1257.852286] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1257.852322] sr: Sense Key : No Sense [current] 
[ 1257.852331] sr: Add. Sense: No additional sense information
[ 1258.387239] end_request: I/O error, dev sr1, sector 12160
[ 1258.454298] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1258.454331] sr: Sense Key : No Sense [current] 
[ 1258.454341] sr: Add. Sense: No additional sense information
[ 1258.984230] end_request: I/O error, dev sr1, sector 12160
[ 1259.049289] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1259.049326] sr: Sense Key : No Sense [current] 
[ 1259.049336] sr: Add. Sense: No additional sense information
[ 1259.584241] end_request: I/O error, dev sr1, sector 12160
[ 1259.679304] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1259.679339] sr: Sense Key : No Sense [current] 
[ 1259.679348] sr: Add. Sense: No additional sense information
[ 1260.214257] end_request: I/O error, dev sr1, sector 12160
[ 1260.283301] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1260.283335] sr: Sense Key : No Sense [current] 
[ 1260.283344] sr: Add. Sense: No additional sense information
[ 1260.814244] end_request: I/O error, dev sr1, sector 12160
[ 1260.814258] __ratelimit: 206 callbacks suppressed
[ 1260.814265] Buffer I/O error on device sr1, logical block 1520
[ 1260.814340] Buffer I/O error on device sr1, logical block 1520
[ 1260.814407] Buffer I/O error on device sr1, logical block 1534
[ 1260.814429] Buffer I/O error on device sr1, logical block 1534
[ 1260.814490] Buffer I/O error on device sr1, logical block 4
[ 1260.814511] Buffer I/O error on device sr1, logical block 5
[ 1260.814561] Buffer I/O error on device sr1, logical block 1535
[ 1260.814584] Buffer I/O error on device sr1, logical block 1535
[ 1260.814616] Buffer I/O error on device sr1, logical block 1535
[ 1260.814646] Buffer I/O error on device sr1, logical block 1535
[ 1260.881289] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1260.881323] sr: Sense Key : No Sense [current] 
[ 1260.881332] sr: Add. Sense: No additional sense information
[ 1261.411258] end_request: I/O error, dev sr1, sector 12160
[ 1261.478290] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1261.478365] sr: Sense Key : No Sense [current] 
[ 1261.478375] sr: Add. Sense: No additional sense information
[ 1262.014232] end_request: I/O error, dev sr1, sector 12160
[ 1262.072281] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1262.072317] sr: Sense Key : No Sense [current] 
[ 1262.072326] sr: Add. Sense: No additional sense information
[ 1262.610244] end_request: I/O error, dev sr1, sector 12160
[ 1262.675296] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1262.675330] sr: Sense Key : No Sense [current] 
[ 1262.675340] sr: Add. Sense: No additional sense information
[ 1263.205244] end_request: I/O error, dev sr1, sector 12160
[ 1263.271285] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1263.271322] sr: Sense Key : No Sense [current] 
[ 1263.271331] sr: Add. Sense: No additional sense information
[ 1263.807239] end_request: I/O error, dev sr1, sector 12160
[ 1263.876257] usb 4-2: USB disconnect, address 3
[ 1263.877437] scsi 3:0:0:0: rejecting I/O to dead device
[ 1263.886795] scsi 3:0:0:0: rejecting I/O to dead device
[ 1263.886834] scsi 3:0:0:0: rejecting I/O to dead device
[ 1270.212141] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 1270.366495] usb 4-1: configuration #1 chosen from 1 choice
[ 1270.377207] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1270.381371] usb-storage: device found at 4
[ 1270.381388] usb-storage: waiting for device to settle before scanning
[ 1275.382396] usb-storage: device scan complete
[ 1275.385300] scsi 4:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
[ 1275.436470] sr1: scsi-1 drive
[ 1275.436700] sr 4:0:0:0: Attached scsi CD-ROM sr1
[ 1275.436935] sr 4:0:0:0: Attached scsi generic sg2 type 5
[ 1275.545229] sr1: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
[ 1275.545246] sr: Sense Key : No Sense [current] 
[ 1275.545250] sr: Add. Sense: No additional sense information
[ 1275.657237] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1275.657273] sr: Sense Key : No Sense [current] 
[ 1275.657283] sr: Add. Sense: No additional sense information
[ 1276.198256] end_request: I/O error, dev sr1, sector 12160
[ 1276.198271] __ratelimit: 134 callbacks suppressed
[ 1276.198279] Buffer I/O error on device sr1, logical block 1520
[ 1276.198352] Buffer I/O error on device sr1, logical block 1520
[ 1276.198423] Buffer I/O error on device sr1, logical block 1534
[ 1276.198444] Buffer I/O error on device sr1, logical block 1534
[ 1276.198504] Buffer I/O error on device sr1, logical block 4
[ 1276.198527] Buffer I/O error on device sr1, logical block 5
[ 1276.198578] Buffer I/O error on device sr1, logical block 1535
[ 1276.198598] Buffer I/O error on device sr1, logical block 1535
[ 1276.198629] Buffer I/O error on device sr1, logical block 1535
[ 1276.198659] Buffer I/O error on device sr1, logical block 1535
[ 1276.215253] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1276.215280] sr: Sense Key : No Sense [current] 
[ 1276.215291] sr: Add. Sense: No additional sense information
[ 1276.326283] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1276.326321] sr: Sense Key : No Sense [current] 
[ 1276.326331] sr: Add. Sense: No additional sense information
[ 1276.869259] end_request: I/O error, dev sr1, sector 12160
[ 1276.895260] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1276.895292] sr: Sense Key : No Sense [current] 
[ 1276.895301] sr: Add. Sense: No additional sense information
[ 1277.018260] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1277.018294] sr: Sense Key : No Sense [current] 
[ 1277.018303] sr: Add. Sense: No additional sense information
cisco@catalyst-3750g:~$ 

```

---

### Post by Mach1US on 2008-11-07
I see what the problem is, your card is not being recognized by a Kernel,it means your kernel doesn't see your evdo card.
If quick removal and insertion of the card at end of dmesg does not produce something like this :
```
[  171.945756] airprime 6-1:1.0: airprime converter detected
[  171.945890] usb 6-1: airprime converter now attached to ttyUSB0
[  171.945933] usb 6-1: airprime converter now attached to ttyUSB1
[  171.945983] usb 6-1: airprime converter now attached to ttyUSB2
[  171.945990] airprime 6-1:1.1: airprime converter detected
[  171.946034] usb 6-1: airprime converter now attached to ttyUSB3
[  171.946105] usb 6-1: airprime converter now attached to ttyUSB4
[  171.946149] usb 6-1: airprime converter now attached to ttyUSB5
[  171.946155] airprime 6-1:1.2: airprime converter detected
[  171.946200] usb 6-1: airprime converter now attached to ttyUSB6
[  171.946242] usb 6-1: airprime converter now attached to ttyUSB7
[  171.946284] usb 6-1: airprime converter now attached to ttyUSB8
```
your card is not being seen by your linux machine.
This could be caused because by the fact that your card is really new and linux kernel does not have a drivers for it yet .
You may have to google and search forums for proper driver or get a separate cheap EVDO router or get a card that works with linux (99% of them work) .
One thing you may want to try if USBserial ( the second method from this tutorial) will recognize it.

---

### Post by chanders on 2008-11-11
Well I get it to connect no problem but  when I open up Firefox it doesnt go to any pages and keeps timing out. Any ideas?

---

### Post by Mach1US on 2008-11-11
If you are getting ip's and DNS server ip all you need to do is go to File menu in firefox and uncheck Work Offline.

---

### Post by chanders on 2008-11-11
When it connects (I use wvdial) I can see the assigned ip address and DNS server address in the console. I uncheck "work offline" in firefox but it still cant seem to find any sites. 

Even trying a "Ping" command to google.com times out..

---

### Post by OldDirtyTurtle on 2008-11-11
May be a dumb question, but is there any way to permanently uncheck that box?  I've looked and looked but can't seem to find a way to avoid having to go the the menu each time.

> **Mach1US said:**
> If you are getting ip's and DNS server ip all you need to do is go to File menu in firefox and uncheck Work Offline.

---

### Post by Mach1US on 2008-11-11
> **chanders said:**
> When it connects (I use wvdial) I can see the assigned ip address and DNS server address in the console. I uncheck "work offline" in firefox but it still cant seem to find any sites. 

Even trying a "Ping" command to google.com times out..

Shut down your other network interfaces (wireless,wired) , turn off firewall,reboot and try again.


> **OldDirtyTurtle said:**
> May be a dumb question, but is there any way to permanently uncheck that box?  I've looked and looked but can't seem to find a way to avoid having to go the the menu each time.
Start wvdial prior to opening firefox

---

### Post by OldDirtyTurtle on 2008-11-11
I always start wvdial and wait for the IPs to list before starting firefox.  

> **Mach1US said:**
> Start wvdial prior to opening firefox

---

### Post by Mach1US on 2008-11-11
I had this problem with one of my pc's,Network-Manager is a coulprit and i adjusted it in firefox itself, but at the time i was doing lots of browser tweaking and i can't quite remember how i did it but if you type in your browser  ```
about:config
```  you will get all the options where you need to change one the values (this is where i draw blank) to  ```
disable
``` at which point firefox will have the Work Offline option disabled entirely. 

Another solution:
I had to edit /etc/NetworkManager/nm-system-settings.conf and changed the line under [ifupdown] to managed=true

edit: possibly unrelated, but after doing that, I found that my boot was hanging up on "Configuring Network Devices". So I edit /etc/network/interfaces and commented out all the lines that deal with my ethernet. This fixed my slow boot and my wired connection still works. in fact it plays alot nicer with nm-applet now.
I got this from the from **sroops[B]**[/B]

Few links:
```
[ http://kb.mozillazine.org/About:config_entries ]( http://kb.mozillazine.org/About:config_entries )
remove  <b></b> from address bar once link loads
```
[http://maketecheasier.com/28-coolest-firefox-aboutconfig-tricks/2008/08/21](http://maketecheasier.com/28-coolest-firefox-aboutconfig-tricks/2008/08/21)
[https://bugs.launchpad.net/network-manager/+bug/256054](https://bugs.launchpad.net/network-manager/+bug/256054)
[http://www.mjmwired.net/resources/mjm-fedora-f9.html#network](http://www.mjmwired.net/resources/mjm-fedora-f9.html#network)

hope it helps.

---

### Post by OldDirtyTurtle on 2008-11-11
Cool - thanks!  I'll take a look.

---

### Post by jka4321 on 2008-11-18
use ubuntu 8.1 and the pentech card by sprint plugs right in and works right off the bat in 8.1 32bit and also 64bit 8.1
great job on ubuntu ver 8.1 you guys are great

---

### Post by Mach1US on 2008-11-19
That's great to hear that.

---

### Post by Saghaulor on 2008-11-20
First,
Thank you for your tutorial. I have successfully configured and connected to Verizon mobile broadband using the Novatel Wireless Merlin XV620 card.

Second, and most importantly.
The connections only lasts for approximately one minute.

Here is what I receive while connecting and disconnecting.

> stephen@stephen-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX0
ATX0
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT<#777>
--> Waiting for carrier.
ATDT<#777>
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Nov 20 16:54:57 2008
--> Pid of pppd: 6516
--> Using interface ppp0
--> pppd: [03][7f]
--> pppd: [03][7f]
--> pppd: [03][7f]
--> local  IP address 70.212.73.197
--> pppd: [03][7f]
--> remote IP address 66.174.61.4
--> pppd: [03][7f]
--> primary   DNS address 66.174.95.44
--> pppd: [03][7f]
--> secondary DNS address 66.174.92.14
--> pppd: [03][7f]
--> pppd: [03][7f]
--> pppd: [03][7f]
--> Connect time 2.5 minutes.
--> pppd: [03][7f]
--> pppd: [03][7f]
--> pppd: [03][7f]
--> Disconnecting at Thu Nov 20 16:57:28 2008
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)

Any help would be appreciated. Thank you in advance.

---

### Post by OldDirtyTurtle on 2008-11-21
Well - I've been running the second fix on an old Dell with Hardy for a few months.  No problems.

However, when I tried to set it up on Intrepid 64-bit on my new Sys76 Serval Pro I get the exit error 19.

Any ideas?:confused:

---

### Post by Mach1US on 2008-11-21
> **Saghaulor said:**
> First,
Thank you for your tutorial. I have successfully configured and connected to Verizon mobile broadband using the Novatel Wireless Merlin XV620 card.

Second, and most importantly.
The connections only lasts for approximately one minute.

Here is what I receive while connecting and disconnecting.



Any help would be appreciated. Thank you in advance.

Do this:
[http://ubuntuforums.org/showpost.php?p=6090366&postcount=296](http://ubuntuforums.org/showpost.php?p=6090366&postcount=296)



 
OldDirtyTurtle's 
	
> Well - I've been running the second fix on an old Dell with Hardy for a few months. No problems.

However, when I tried to set it up on Intrepid 64-bit on my new Sys76 Serval Pro I get the exit error 19.

Any ideas

Is the EVDO card 64-bit, if you are using the same 32-bit card it will not work with a 64-bit hardware. 
With 64-bit PC you need to upgrade all peripherals to be 64-bit compatible.

---

### Post by OldDirtyTurtle on 2008-11-21
Thanks for the bad news!  Looks like it is time to go with $atellite internet.  Chaching...:cry:

---

### Post by Mach1US on 2008-11-21
Don't give up just yet, you can get cheap evdo router and connect via Ethernet or Wi-Fi additionally you will be able connect multiple PC's via same card.

Links to cheap Evdo routers:
[http://ubuntuforums.org/showpost.php?p=6033463&postcount=284](http://ubuntuforums.org/showpost.php?p=6033463&postcount=284)

---

### Post by OldDirtyTurtle on 2008-11-21
Now you're talking my language.  Thanks!

> **Mach1US said:**
> Don't give up just yet, you can get cheap evdo router and connect via Ethernet or Wi-Fi additionally you will be able connect multiple PC's via same card.

Links to cheap Evdo routers:
[http://ubuntuforums.org/showpost.php?p=6033463&postcount=284](http://ubuntuforums.org/showpost.php?p=6033463&postcount=284)

---

### Post by dccrens on 2008-11-23
Has anyone gotten this to work with the Novatel USB760 from verizon? I just bought one and it work great in windbloze but I haven't had time to try it in Ubuntu.

---

### Post by Mach1US on 2008-11-23
I think that one has a same chipset from Pantech as PC5750 and UM150 so it should work without any problems.

---

### Post by Saghaulor on 2008-11-24
> **Mach1US said:**
> Do this:
[http://ubuntuforums.org/showpost.php?p=6090366&postcount=296](http://ubuntuforums.org/showpost.php?p=6090366&postcount=296)


That was already present in my config file. I'll post my config file for further assistance. I noticed in the post below that the card must be 64bit compatible for 64bit hardware. I'm not sure if this is my problem, but I am running 8.04 AMD64. Would my card still be able connect if it was 32bit, albeit a very short connection time?

My config file.

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 921600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
 Phone = <#777>
 Password = <vzw>
 Username = <##########@vzw3g.com>
Stupid Mode = 1
Init = ATZ
ISDN = 0
Auto Reconnect = on
Carrier Check = no
 [Dialer shh]
Init3 = ATM0
 [Dialer pulse]
Dial Command = ATDP
```

---

### Post by Saghaulor on 2008-11-24
Also, for more info, and for my own knowledge, I'm not sure as to whether or not Airprime or the USBSerial drivers is running. It looks like Airprime is not running, even though I modprobe'd it. 

I believe the below information is what is required from the dmesg command.

```
[   36.001237] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   36.001270] option 2-5:1.0: GSM modem (1-port) converter detected
[   36.001429] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB0
[   36.001443] option 2-5:1.1: GSM modem (1-port) converter detected
[   36.001526] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB1
[   36.001537] usbcore: registered new interface driver option
[   36.001539] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
```

The error I receive upon wvdial terminating is below.
```

> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
```

Now I consider myself very inexperienced to linux, but might this be caused by Airprime and USBSerial running side by side?

How do I know what driver is running?

---

### Post by pvillela on 2008-11-24
The instructions for the first method using Airprime driver worked flawlessly with a Verizon UM175 USB modem on Ubuntu 8.04.  Many thanks!

---

### Post by Mach1US on 2008-11-25
> **Saghaulor said:**
> Also, for more info, and for my own knowledge, I'm not sure as to whether or not Airprime or the USBSerial drivers is running. It looks like Airprime is not running, even though I modprobe'd it. 

I believe the below information is what is required from the dmesg command.

```
[   36.001237] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   36.001270] option 2-5:1.0: GSM modem (1-port) converter detected
[   36.001429] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB0
[   36.001443] option 2-5:1.1: GSM modem (1-port) converter detected
[   36.001526] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB1
[   36.001537] usbcore: registered new interface driver option
[   36.001539] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
```

The error I receive upon wvdial terminating is below.
```

> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
```



Open terminal and type:
sudo gedit /etc/ppp/peers/wvdial
And insert aditionally those lines:
```
lcp-echo-failure 0
lcp-echo-interval 0
```

---

### Post by sandyeggoboy on 2008-11-25
THANK YOU!!!! my card works perfectly now!!!

---

### Post by dccrens on 2008-11-25
Well I have the Novatel USB760 from verizon and it seems neither of the methods here will work. When I insert the device it is recognized as a USB storage device and mounted as a cdrom. This is because the device has internal storage (where the windows verizon programs are stored) and it also has a micro sd card slot. 

When I look through dmesg output there is no mention of "airprime" or of a GSM Modem or serial. 

Any thoughts?

---

### Post by Saghaulor on 2008-11-26
> **Mach1US said:**
> Open terminal and type:
sudo gedit /etc/ppp/peers/wvdial
And insert aditionally those lines:
```
lcp-echo-failure 0
lcp-echo-interval 0
```

Hey, I nearly figured out how to do it on myself using this thread.
[http://ubuntuforums.org/archive/index.php/t-619938.html](http://ubuntuforums.org/archive/index.php/t-619938.html)

But your post definitely helped.

---

### Post by Saghaulor on 2008-11-26
> **dccrens said:**
> Well I have the Novatel USB760 from verizon and it seems neither of the methods here will work. When I insert the device it is recognized as a USB storage device and mounted as a cdrom. This is because the device has internal storage (where the windows verizon programs are stored) and it also has a micro sd card slot. 

When I look through dmesg output there is no mention of "airprime" or of a GSM Modem or serial. 

Any thoughts?

I believe that you have to patch the kernel with the Airprime driver. The following link details how one would go about doing so.

[http://ubuntuforums.org/showthread.php?t=461991](http://ubuntuforums.org/showthread.php?t=461991)

I haven't tried it yet, but I believe all should work as written.

---

### Post by NTolerance on 2008-11-26
> **erothoff said:**
> I got internet working with an Alltel LG AX8600 and wvdial, but I would like to get it working with Network manager. (As I have to constantly tell Firefox that I am online to browse.) But for some reason it isn't working. I am using port /dev/ttyACM0 for my connection in wvdial, but the network manager doesn't give it as an option. (So I enter it manually.)
  Other posts say that "It just works." with the dialer like that. I am blacklisting like first suggested. Any suggestions?

I'm also looking for help with the Alltel AX8600 and Network Manager on Intrepid.  Ubuntu detects the USB connection to the phone and creates a /dev/ttyACM0 device, but Network Manager does nothing when I try to connect with the AX8600.  No error message, no timeout, nothing.  Is there a log for Network Manager or a way to run it from the terminal to get more information?

Edit:  In a record time of 45 minutes I have solved this problem.  First of all, Network Manager log data is stored in /var/log/syslog.  I found some "pin code" errors in there.  Turns out my AX8600's security lock had been enabled.  I went into the security section of the settings menu on the phone and entered the default unlock code which was the last 4 digits of my phone number.  I then plugged the now-unlocked phone back into the USB port and Network Manager automatically created a new profile which fired up in seconds.  Sweet!

---

### Post by djedi on 2008-11-28
Hello all!
Please be patient.  I am a complete nube (to Linux and ubuntu) and am trying to set up the EVDO modem in 8.10.
I have edited the wvdial.conf file as suggested, but keep getting this message in the gnome pppd log:
"unable to run /usr/sbin/pppd
check permissions , or specify a "PPPD path" option in wvdial.conf"
Then, after a while, I get:
"NO CARRIER
Max attempts Exceeded  Aborting
Disconnect at   (date and time)"

I think I am getting the hang of some things but others escape me.
Thanks in advance.
WK

---

### Post by Mach1US on 2008-11-30
> **djedi said:**
> Hello all!
Please be patient.  I am a complete nube (to Linux and ubuntu) and am trying to set up the EVDO modem in 8.10.
I have edited the ...
WK
 Open the terminal and type sudo wvdial, then pass ...
Post the output from the terminal shell and your wvdial.conf file.

---

### Post by Czaruno on 2008-12-01
Just wanted to add that I was able to use a Verizon USB 720 right out of the box with no command line changes on (X) Ubuntu 8.10 on an older laptop:

Laptop Details:
Sony Vaio PCG-SR33K
Processor Celeron 600 MHz
128 MB (SDRAM)
10 GB IDE Hard Drive

---

### Post by THE TECH on 2008-12-03
Ok, I guess I'm having similar problems as others have.  wvdial gives me the error:

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

When I try gnome-ppp, I get a bit closer to connecting but still can't get on.  I know I have good signal cause it works on my Windows based comp.  Here is the error I get from gnome-ppp:

WVCONF: /home/thetech/.wvdial.conf
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM0L0DT#777
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM0L0DT#777
GNOME PPP: STDERR: CONNECT
GNOME PPP: STDERR: --> Carrier detected.  Waiting for prompt.
GNOME PPP: STDERR: --> Connected, but carrier signal lost!  Retrying...
GNOME PPP: STDERR: --> Sending: ATM0L0DT#777
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: NO CARRIER
GNOME PPP: STDERR: --> No Carrier!  Trying again.
GNOME PPP: STDERR: --> Maximum Attempts Exceeded..Aborting!!
GNOME PPP: STDERR: --> Disconnecting at Wed Dec  3 07:29:59 2008


I would love to be able to get online with my new machine if anyone can help me out!!

Thanks in advance!

---

### Post by THE TECH on 2008-12-03
Ok, I was finally able to connect.  Now, even though it says I'm connected, I can't access any sites.  I know I am sooo close to getting this working.

---

### Post by foresthill on 2008-12-03
I was having a similar problem. I could connect but no web pages would load, they would start to load then just die after a second or two.

I added this line to my etc/pppd/options file:
[PHP]nodeflate[/PHP]

This disables compression, and for some reason it worked on my system. You'll need super user privileges to do this.

Just stick it in there like this, without a # mark in front of it.

nodeflate

# If no local IP address is given, pppd will use the first IP address
# that belongs to the local hostname. If "noipdefault" is given, this
# is disabled and the peer will have to supply an IP address.
noipdefault

# With this option, pppd will accept the peer's idea of our local IP
# address, even if the local IP address was specified in an option.
#ipcp-accept-local

# With this option, pppd will accept the peer's idea of its (remote) IP
# address, even if the remote IP address was specified in an option.
#ipcp-accept-remote

# Run the executable or shell command specified after pppd has terminated
# the link.  This script could, for example, issue commands to the modem
# to cause it to hang up if hardware modem control signals were not
# available.
# If mgetty is running, it will reset the modem anyway. So there is no need
# to do it here.
#disconnect "chat -- \d+++\d\c OK ath0 OK"

(NOTE: This is just the first part of my "options" file, not the whole thing)

---

### Post by THE TECH on 2008-12-03
> **foresthill said:**
> I was having a similar problem. I could connect but no web pages would load, they would start to load then just die after a second or two.

I added this line to my etc/pppd/options file:
[PHP]nodeflate[/PHP]

This disables compression, and for some reason it worked on my system. You'll need super user privileges to do this.

Just stick it in there like this, without a # mark in front of it.

nodeflate

# If no local IP address is given, pppd will use the first IP address
# that belongs to the local hostname. If "noipdefault" is given, this
# is disabled and the peer will have to supply an IP address.
noipdefault

# With this option, pppd will accept the peer's idea of our local IP
# address, even if the local IP address was specified in an option.
#ipcp-accept-local

# With this option, pppd will accept the peer's idea of its (remote) IP
# address, even if the remote IP address was specified in an option.
#ipcp-accept-remote

# Run the executable or shell command specified after pppd has terminated
# the link.  This script could, for example, issue commands to the modem
# to cause it to hang up if hardware modem control signals were not
# available.
# If mgetty is running, it will reset the modem anyway. So there is no need
# to do it here.
#disconnect "chat -- \d+++\d\c OK ath0 OK"

(NOTE: This is just the first part of my "options" file, not the whole thing)

When I try pulling that folder up with gedit, it is blank.  Should there be something in there already?

---

### Post by foresthill on 2008-12-03
I suppose I should mention I'm running OpenSuse 11. I thought the files would be in the same places but maybe not. There should be a pppd options file somewhere though. 

Another thought is perhaps you could *try* putting this line in your wvdial.conf file if no "pppd options" file can be found.

---

### Post by THE TECH on 2008-12-03
> **foresthill said:**
> I suppose I should mention I'm running OpenSuse 11. I thought the files would be in the same places but maybe not. There should be a pppd options file somewhere though. 

Another thought is perhaps you could *try* putting this line in your wvdial.conf file if no "pppd options" file can be found.

Hmm...maybe I should just wait for another response on this.  wvdial.conf doesn't look like the correct place for that command according to what it looks like already.

---

### Post by foresthill on 2008-12-03
Does Ubuntu have a file called "man pppd"?

In Suse, to bring it up you go the the terminal and type [PHP]man pppd[/PHP]

This brings up a help guide or "manual" which contains all the options you can add to your pppd files and what all the various error codes mean.

---

### Post by THE TECH on 2008-12-03
> **foresthill said:**
> Does Ubuntu have a file called "man pppd"?

In Suse, to bring it up you go the the terminal and type [PHP]man pppd[/PHP]

This brings up a help guide or "manual" which contains all the options you can add to your pppd files and what all the various error codes mean.

I don't know if it does, but when I try that command, I just get an error.

---

### Post by foresthill on 2008-12-03
Well, anyway, find out how to disable compression and try that. It should involve adding that line to one of the config files.

---

### Post by THE TECH on 2008-12-04
With the help of user cek, I was finally able to get online and see webpages.  Thanks to everyone who helped me out!!!  I couldn't have done it without all of you!

---

### Post by foresthill on 2008-12-04
And the solution was . . . 

*drum roll*

---

### Post by foresthill on 2008-12-11
*crickets chirping*

I guess he's gone.

---

### Post by Mach1US on 2008-12-12
> **foresthill said:**
> *crickets chirping*

I guess he's gone.

I know you didn't get proper recognition so i like to thank you for your work here and I'm sure it will be useful for others.
    =D>

---

### Post by emufambirwi on 2008-12-13
I want to make my Ubuntu box a proxy server running squid so that 3 machines at my office can connect to the internet using the proxy. The ubuntu box is the one that has a cdma modem connected to it. 

Other posts in similar forums suggest that I can't use both ppp0 (cdma modem) and eth0 (LAN) at the same time. Has anyone ever done it

---

### Post by F1nny on 2008-12-13
I am a total beginner to Linux and Ubuntu.  I received my Verizon USB 760.  I read the forum and I can not get it to work.  My guess is that it is being recongized as a flash drive since it doubles as one.  Anyone been able to get it to work or have some advice?

---

### Post by Mach1US on 2008-12-14
You need to have evdo card working propoerly first .
I have used different method for connection shearing but mu Linux box was strictly dedicated as a Linux router so answer is yes you can have two and more interfaces running at the same time.
But save yourself same headaches and processor cycles on your machine and just buy cheap EVDO router .
You can new router from my previous post recommending some 
or can get used one on e-bay for $50 .

---

### Post by foresthill on 2008-12-14
I would like to mention that I got a PCMCIA to PCI converter at NewEgg for around $15 that works great, allowing me to use my PCMCIA card in my various desktop systems.

No set-up was required and it was instantly configured at boot up time (the converter, not the EVDO Card).

I think I actually get better performance in the desktop systems that on my notebook.

Just thought I'd let people know about one more possible option for using a PCMCIA card.

---

### Post by donwinchell on 2008-12-15
I am running ubuntu 8.10 using network manager to connect.
Novatel P720 card and Bell Canada as a provider.
I can establish a connection and get these results.
/etc/ppp$ tail -f /var/log/messages

Dec 15 10:02:44 d510 pppd[19099]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Dec 15 10:02:44 d510 pppd[19099]: pppd 2.4.4 started by root, uid 0
Dec 15 10:02:44 d510 pppd[19099]: Using interface ppp0
Dec 15 10:02:44 d510 pppd[19099]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 15 10:02:44 d510 pppd[19099]: local  IP address 70.25.176.27
Dec 15 10:02:44 d510 pppd[19099]: remote IP address 206.47.201.2
Dec 15 10:02:44 d510 pppd[19099]: primary   DNS address 206.47.201.246
Dec 15 10:02:44 d510 pppd[19099]: secondary DNS address 204.101.237.136
Dec 15 10:06:52 d510 pppd[19099]: Terminating on signal 15
Dec 15 10:06:52 d510 pppd[19099]: Connect time 4.2 minutes.
Dec 15 10:06:52 d510 pppd[19099]: Sent 0 bytes, received 0 bytes.
Dec 15 10:06:52 d510 pppd[19099]: Connection terminated.
somewhere else I determine that my subnet mask is 255.255.255.255
I appear to have an actual connection but can not ping the DNS or use firefox, etc.
It seems I am very close but no real success.
Any thoughts?
Thank you

---

### Post by Mach1US on 2008-12-15
There are few people that have had this problem and they have came up with few different solutions, skim through the posts and you'll find some good workarounds.
One of them being on this page :
[http://ubuntuforums.org/showpost.php?p=6301566&postcount=335](http://ubuntuforums.org/showpost.php?p=6301566&postcount=335)

---

### Post by foresthill on 2008-12-15
My pppd manual shows error 15 as being due to this:

> #15. The link was terminated because the peer is  not  responding  to
echo requests.


HTH

Just curious, did you add these lines to your wvdial.conf file as shown in page one of this thread?

lcp-echo-failure 0
lcp-echo-interval 0

---

### Post by emufambirwi on 2008-12-17
Is there a specific way of configuring the linux box as a router

---

### Post by Mach1US on 2008-12-17
> **foresthill said:**
> My pppd manual shows error 15 as being due to this:



HTH

Just curious, did you add these lines to your wvdial.conf file as shown in page one of this thread?

lcp-echo-failure 0
lcp-echo-interval 0

This have been already answer in this thread.
[http://ubuntuforums.org/showpost.php?p=6249236&postcount=324](http://ubuntuforums.org/showpost.php?p=6249236&postcount=324)


> **emufambirwi said:**
> Is there a specific way of configuring the linux box as a routerY
There is many different configuration in which you can run Ubuntu as a router , i had one running with 4 interfaces and routing protocol but for home/small office use you would not need that, search threads expaining **how to share internet connection**.
This will be less taxing on your machine and a whole lot easier to set it up.

---

### Post by Sirius [b] of Jehovah on 2008-12-21
I configured my verizon usb720 air card by going to vpn connections;
then configure vpn;
clicked Mobil broadband;
then clicked + Add
picked T Mobil (Internet)
erased T Mobil in the name box.
Typed Verizon.
Then verizon came up to be able to edit.
clicked Edit.
checked connect automatic box
in the name box Typed;   *777
in the username box typed my Air card Telephone number @vzw3g.com
 SO here is a example;      [email]7049291234@vzw3g.com[/email]
in the password box Typed lower case;    vzw

in the apn box there was already internet2.voicestream.com I did not make a change in this box.
 I left the network;pin and puk boxs empty.
Re booted with my air card in. 
the broad band radio tower showed up.
clicked on the icon radio tower
clicked automobil broadband (CDMA) connection.
 and it connected and works twice as fast as it was with no cutouts as it was before I changed to Ubuntu: YAAAA !
 I know nothing about programming and read every Article and could not figure it out;for two days. So I decided to do what I do best.Use what I was given as a complete package believing there is a way.
 The old saying I will love you so many ways I know you will love one of them eventually.

---

### Post by Mach1US on 2008-12-21
That's great i'll try it sometime next week , sound like just point and click.
Cool. :)

---

### Post by JDuc on 2008-12-27
I've followed the instructions in the first post and have managed to get connected with my Sprint EVDO card.

However, now, I cannot connect back to my wireless network for some reason.

I've downloaded the GNOME PPP interface, but haven't tried it yet, is it an alternative to the method mentioned in the original post?  If so, how can I go about reverting all of the changes that I made per the first post?

[INDENT][COLOR=Blue] EDIT: I've now tried Gnome PPP, but I cannot get it to connect.  Looking at the log, I'm seeing this:

```
Configuration does not specify a valid phone number.
```What gives?  Is there a walk through anywhere about what numbers should go where?
[/COLOR][/INDENT]  
[COLOR=Red]_**Most importantly**_[/COLOR] at this moment though is how to get connected back to my wireless network?

Thanks for any and all help!

---

### Post by Mach1US on 2009-01-15
The Network Manager applet does not like to play with any configurations created by other apps or system config utilities.
the first thing i would try to edit out all instances from its interface configuration file.
The file is located at:
```
 sudo gedit /etc/network/interfaces 
``` 
First make a backup of that file and then comment it all out except for your wi-fi wep or other encription keys and paste the following:
```
 auto lo
iface lo inet loopback
```

Then reinstall network manager
```
sudo apt-get remove network-manager
sudo apt-get install network-manager
```
restart and you're done .

---

### Post by kevcart3 on 2009-01-16
I've searched the forums over and have been trying to get a really good answer on how to set up my Franklin cdu680. I have searched the forums here a lot and haven't really found any solid information for the CDU-680.

Thanks.

edit: btw, my modem is giving a segmentation fault error when i try to connect and it doesn't seem that i can use the changemode script either.

---

### Post by SaintDanBert on 2009-03-04
When I connect my phone, I see blather in the logs talking about
rndis_host.  I run lsmod and there is rndis_host, but the logs
insist things won't connect.

I think this is the relevant parts of the log, but I don't know 
exactly when things started.
--------------------------
kernel: usb 3-1: new full speed USB device using uhci_hcd and address 2
kernel: Device driver usbdev3.2_ep00 lacks bus and class support for being resumed.
kernel: usb 3-1: configuration #1 chosen from 1 choice
kernel: Device driver usbdev3.2_ep81 lacks bus and class support for being resumed.
kernel: Device driver usbdev3.2_ep82 lacks bus and class support for being resumed.
kernel: Device driver usbdev3.2_ep03 lacks bus and class support for being resumed.
kernel: usbcore: registered new interface driver cdc_ether
kernel: Device driver eth1 lacks bus and class support for being resumed.
kernel: eth1: register 'rndis_host' at usb-0000:00:1a.1-1, RNDIS device, 80:00:60:0f:e8:00
kernel: usbcore: registered new interface driver rndis_host
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
dhcdbd: Unrequested down ?:3
kernel: usb 3-1: USB disconnect, address 2
kernel: eth1: unregister 'rndis_host' usb-0000:00:1a.1-1, RNDIS device
--------------------------------------

I have no clue what to do next to sort this out.

~~~ 0;-D

---

### Post by Mach1US on 2009-03-06
Have you tried any of the two methods in this tread ?
If your device isn't configured automatically you need to use one of the two methods.

---

### Post by scaudell on 2009-03-21
I'm having a different issue, I had the Sprint 5720 card working great with network-manager for weeks. I'm not quite sure what happened but it no longer works despite it connecting, geting an IP address & DNS. It increments a few packets, but won't do anything else.

```

lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 06eb (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

```

```
lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 009: ID 413c:8152 Dell Computer Corp. 
Bus 004 Device 008: ID 413c:8154 Dell Computer Corp. 
Bus 004 Device 007: ID 413c:8153 Dell Computer Corp. 
Bus 004 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 005: ID 413c:8149 Dell Computer Corp. 
Bus 004 Device 004: ID 0c45:63f8 Microdia 
Bus 004 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0a5c:5800 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 413c:8134 Dell Computer Corp. Wireless 5720 Sprint Mobile Broadband (EVDO Rev-A) Minicard Status Port
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
dmesg | grep usb
[    2.437525] usbcore: registered new interface driver usbfs
[    2.437543] usbcore: registered new interface driver hub
[    2.437576] usbcore: registered new device driver usb
[    2.466700] usb usb1: configuration #1 chosen from 1 choice
[    2.673007] usb usb2: configuration #1 chosen from 1 choice
[    2.875094] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    2.876510] usb usb3: configuration #1 chosen from 1 choice
[    3.036624] usb 1-1: configuration #1 chosen from 1 choice
[    3.104332] usb usb4: configuration #1 chosen from 1 choice
[    3.158833] usb 1-1: USB disconnect, address 2
[    3.313117] usb usb5: configuration #1 chosen from 1 choice
[    3.416970] usb usb6: configuration #1 chosen from 1 choice
[    3.521005] usb usb7: configuration #1 chosen from 1 choice
[    3.664100] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    3.788364] usb usb8: configuration #1 chosen from 1 choice
[    3.796686] usb 4-1: configuration #1 chosen from 1 choice
[    4.228328] usb 4-6: new high speed USB device using ehci_hcd and address 4
[    4.403230] usb 4-6: configuration #1 chosen from 1 choice
[    4.644318] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.821622] usb 3-1: configuration #0 chosen from 1 choice
[    4.821633] usb 3-1: config 0 descriptor??
[    5.144487] usb 4-1.1: new high speed USB device using ehci_hcd and address 5
[    5.237734] usb 4-1.1: configuration #1 chosen from 1 choice
[    5.325462] usb 4-1.2: new full speed USB device using ehci_hcd and address 6
[    5.435249] usb 4-1.2: configuration #1 chosen from 1 choice
[    5.885644] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    6.045129] usb 7-2: configuration #1 chosen from 1 choice
[    6.136275] usb 4-1.2.1: new full speed USB device using ehci_hcd and address 7
[    6.251805] usb 4-1.2.1: configuration #1 chosen from 1 choice
[    6.325329] usb 4-1.2.2: new full speed USB device using ehci_hcd and address 8
[    6.423813] usb 4-1.2.2: configuration #1 chosen from 1 choice
[   11.842068] input: Laptop_Integrated_Webcam_0.3M as /devices/pci0000:00/0000:00:1a.7/usb4/4-6/4-6:1.0/input/input8
[   11.842180] usbcore: registered new interface driver uvcvideo
[   11.949921] usbcore: registered new interface driver hiddev
[   11.952686] input: HID 413c:8153 as /devices/pci0000:00/0000:00:1a.7/usb4/4-1/4-1.2/4-1.2.1/4-1.2.1:1.0/input/input9
[   11.973397] usb 4-1.2.2: usbfs: process 2814 (hid2hci) did not claim interface 0 before use
[   11.976192] input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8153] on usb-0000:00:1a.7-1.2.1
[   11.979209] input: HID 413c:8154 as /devices/pci0000:00/0000:00:1a.7/usb4/4-1/4-1.2/4-1.2.2/4-1.2.2:1.0/input/input10
[   12.008168] input,hidraw1: USB HID v1.11 Mouse [HID 413c:8154] on usb-0000:00:1a.7-1.2.2
[   12.008208] usbcore: registered new interface driver usbhid
[   12.008215] usbhid: v2.6:USB HID core driver
[   12.249133] usb 4-1.2.3: new full speed USB device using ehci_hcd and address 9
[   12.365862] usb 4-1.2.3: configuration #1 chosen from 1 choice
[   13.750555] usbcore: registered new interface driver btusb
[   14.658936] usbcore: registered new interface driver usbserial
[   14.658952] usbserial: USB Serial support registered for generic
[   14.658998] usbserial_generic 7-2:1.0: generic converter detected
[   14.659139] usb 7-2: generic converter now attached to ttyUSB0
[   14.659148] usbserial_generic 7-2:1.1: generic converter detected
[   14.659220] usb 7-2: generic converter now attached to ttyUSB1
[   14.659229] usbserial_generic 7-2:1.2: generic converter detected
[   14.659302] usb 7-2: generic converter now attached to ttyUSB2
[   14.659311] usbserial_generic 7-2:1.3: generic converter detected
[   14.659383] usb 7-2: generic converter now attached to ttyUSB3
[   14.659416] usbcore: registered new interface driver usbserial_generic
[   14.659419] usbserial: USB Serial Driver core
[   26.732518] usb 4-1.2.2: usbfs: process 6441 (hid2hci) did not claim interface 0 before use

```

Can anyone offer any advice?

---

### Post by Mach1US on 2009-03-22
Can you ping any sites using ip addressing also can you post what happens when you connect via wvdial

---

### Post by johnnylavah on 2009-04-01
i am using a pc5750 aircard.  ubuntu recognizes  the card, but the connection always fails.  any ideas?

---

### Post by Mach1US on 2009-04-03
First try booting with previous kernel, second try following guide to use wvdial (first page of this thread ) and if still want work come back with output from wvdial and we'll go from there.

---

### Post by shocktenn on 2009-04-04
im fairly new to linux. im currently running xubuntu 8.10 and i have a Motorola MotoRAZORv3a and i can get the network to run for awhile but after 2 minutes or so it will disconnect. any help would be much appreciated! :guitar:

---

### Post by johnnylavah on 2009-04-05
> **johnnylavah said:**
> i am using a pc5750 aircard.  ubuntu recognizes  the card, but the connection always fails.  any ideas?

i was able to get the card working by editing "10-modem.fdi" and adjusting the ttyusb serial it called on...in my case, i change it from 0 to 1.

---

### Post by senor_smile on 2009-04-06
My USB Pantech card on Verizon has been working fine for months, but all of a sudden isn't connecting.  I tried running 
sudo wvdial

and I get the following: 
> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory

I saw another person on this thread that had that error, but never actually posted how to fix it.  Has anyone any idea how to fix this?

---

### Post by shocktenn on 2009-04-08
i tried the first of the two methods. when i command it to dial it shows this. 

wvdial 
--> WvDial: Internet dialer version 1.60 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATXO 
ATXO 
NO CARRIER 
--> Sending: ATQ0 
ATQ0 
OK 
--> Re-Sending: ATXO 
ATXO 
NO CARRIER 
--> Modem not responding. 


my wvdial configuration settings 

[Dialer Defaults] 
Init1 = ATXO 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Modem Type = USB Modem 
Baud = 460800 
New PPPD = yes 
Modem = /dev/ttyACM0 
ISDN = 0 
; Phone = #777 
; Password = alltel 
; Username = xxxxxxxxxx@alltel .net 
Stupid Mode = on 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATMO 
[Dialer pulse] 
Dial Command = ATDP




please tell me what i did wrong or how to fix! thanks:p

---

### Post by Mach1US on 2009-04-20
There seems to be a driver conflict in current version of the kernel.
Easiest way to get card working is to restart pc and  at boot choose 2.6.27-7 kernel which still works.
2.6.27-13 should have a fix when it comes out.

---

### Post by NTolerance on 2009-04-25
I posted earlier in this thread about getting my Alltel AX8600 working with a USB cable and Intrepid's Network Manager.  That broke shortly after I made that post and I wasn't able to connect until Jaunty was released.  Now my AX8600 is automatically detected by Jaunty's Network Manager and I can connect again.  Hopefully it stays working this time.

---

### Post by LukonLinux on 2009-05-03
Great How To!

Thx guys...

Added:

Ok guys, maybe you can help me with a couple of tweaks.  I changed authorizations to access the modem to 'anyone,' so now it no longer asks for a password in terminal.  I created a shortcut in a panel.  It works as an 'application' if the modem has already been accessed once in terminal that session - otherwise it only works as an 'application in terminal.'  Is there anyway to make it work without opening a terminal window the first time [as an application?]

Also, Firefox always initially opens with the 'Work Offline' box checked - even if I am connected.  How do I change that, so I don't have to go back, uncheck the box, and reload my homepage, each time I connect?

Thanks,

Luke

P.S. Did anyone determine whether in fact it runs faster, if you use the air-port driver, as opposed to USB0?

---

### Post by linko47 on 2009-05-13
thank you who_cares

[code]
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","WAP.CINGULAR"
Phone = *99#
Modem Type = USB Modem
Stupid Mode = on
Auto DNS = 1
Baud = 115200
Modem = /dev/ttyACM0
Init = ATZ
ISDN = 0
Username = WAP@CINGULARGPRS.COM
Password = CINGULAR1
Carrier Check = no
Auto Reconnect = on 
[code]

Works perfectly with my Motorola RAZR V3xx with AT&T.

Thank you!

---

### Post by Mach1US on 2009-07-22
Kernel update has finally fixed evdo and ethernet connection problem:)

---

### Post by hankjw on 2009-10-18
This worked beautifully on my new Compaq Mini 110c-1001, yes the verizon fios gimme. It was WinXP w/ 1GB RAM and 16GB SSD HDD, upgraded to 2GB RAM and 160GB SATA HDD. The modem is the compass 597u through Sprint. The OS is the :netbook remix.

Note: needed to install WVDIAL as it is not in the netbook remix and once installed all I have to do is select the auto mobile broadband nic in the network icon, no cli required. :)

---

### Post by GregIthaca on 2009-11-18
First of all, thanks to everyone here for a great thread.  I have things working nicely either with a borrowed USB760 or with my MiFi2200.  (They both need the 'unmount the CD' fix, and actually use identical USB identifiers.)  Running XUbuntu Hardy 8.04.

I've been looking *all over* for the answer to what I think is a simple question.  I don't want to spend yet another $90 on an EVDO router like the CTR350 after all the fees I've paid to get the devices and the wireless contract and the... anyway.  And the MiFi's wireless is unreliable and it doesn't have an Ethernet port.  So here's the question:

What exactly is it that trips Verizon's "there's another device trying to use this connection" that makes them drop me with the classic "LCP terminated by peer" message?  Clearly both the EVDO routers and Windoze internet connection sharing get around this.  I am guessing I need some kind of NATting, but I haven't found anything that actually describes the solution.  (There is the suggestion to use some complex VMWare solution, but as far as I can tell that's layering a whole bunch of extra software to do something that is probably rather trivial.)

Mach1US, I know that you favor the EVDO router, but it sounded like you'd figured out what was needed and just decided not to do it for performance reasons.  Could you elaborate?  Or is there a HOWTO or post someplace else that covers this?

Thanks,
Greg Nelson
White Hawk Ecovillage
Ithaca, NY 14850
[www.whitehawk.org](www.whitehawk.org)

---

### Post by perlsyntax on 2009-11-27
How do i setup a Virgin modile usb modem model mc760on ubuntu 9.10?

---

### Post by Mach1US on 2009-11-27
just plug the modem into usb port, click little antenna icon in taskbar next to battery icon,you will see options for mobile broadband and setup your modem from there .

---

### Post by pizza-is-good on 2010-02-25
OK, I got my co-worker's Verizon Novatell-Wireless USB 760 working nicely with this tutorial. The thread with my problem is [here]("http://ubuntuforums.org/showthread.php?p=8770492"). 

I had to restart the computer once before it worked, but it did.
[B][SIZE=7]
[/SIZE][/B][LEFT]**[SIZE=7]MANY THANKS!!!!!!![/SIZE]**
[/LEFT]


~pizza

---

### Post by tlcstat on 2010-04-02
Greetings,
You can depend on the Motorola Quantico W845 to work with both tether and bluetooth. I run Ubuntu Karmic and US Cellular.
tlcstat

---

### Post by pbenerjee on 2010-06-11
Hi Friends,

Could you let me know which page I should look to get some wvdial help on sorting connection with my USB modem ? I am getting the below error when I run wvdial :

The PPP daemon has died. (exit code = 19)

---

### Post by Mach1US on 2010-06-24
> **pbenerjee said:**
> Hi Friends,

Could you let me know which page I should look to get some wvdial help on sorting connection with my USB modem ? I am getting the below error when I run wvdial :

The PPP daemon has died. (exit code = 19)

Page 28
[http://ubuntuforums.org/showpost.php?p=5829379&postcount=267](http://ubuntuforums.org/showpost.php?p=5829379&postcount=267)

---

### Post by bevers86 on 2010-07-19
Will this work for the Cricket broadband card?

---

### Post by Mach1US on 2010-07-19
> **bevers86 said:**
> Will this work for the Cricket broadband card?
> **bevers86 said:**
> Will this work for the Cricket broadband card?

Yes, this will work for all providers but you will need to enter proper dial # and if needed password and phone extension which can be obtained from your provider

For example verizon
Phone = #777 
Username = [email]2223334444@vzw3g.com[/email]   _(replace 2223334444 with your#)_
Password = vzw

---

### Post by colorprint on 2010-07-22
my C-Motech CNU-550 usb modem worked fine before, but not works now (maybe after kernel update, don't know) - it connect and disconnet when attached to the USB port:
[12096.291341] usb 6-1: USB disconnect, address 10
[12106.580505] usb 6-2: new full speed USB device using uhci_hcd and address 11
[12106.845771] cdc_acm 6-2:1.0: ttyACM0: USB ACM device
[12112.791360] usb 6-2: USB disconnect, address 11
etc.
LEDs are switching on and off...
Somebody have the same problem?

---

### Post by colorprint on 2010-07-22
and I have found that it disconnects from the system right after connection to the cell network... without the SIM card it detected fine...

---

### Post by JoJerome on 2010-12-04
I sure hope someone in the know is still watching this thread to help us beginners! 

I'm trying to follow the instructions on the first page but keep getting error messages to the effect of: gedit: command not found.

I'm using Maverick on an older IBM Thinkpad, trying to install a Verizon USB760 card. Naturally, Verizon tech support had never heard of Linux. 

Thanks in advance!

---

### Post by senor_smile on 2010-12-04
> **JoJerome said:**
> I sure hope someone in the know is still watching this thread to help us beginners! 

I'm trying to follow the instructions on the first page but keep getting error messages to the effect of: gedit: command not found.

I'm using Maverick on an older IBM Thinkpad, trying to install a Verizon USB760 card. Naturally, Verizon tech support had never heard of Linux. 

Thanks in advance!

That is a little strange.  gedit is the graphical text editor installed by default in Ubuntu.  I'm not sure why it wouldn't be working.  

Which specific line are you trying to enter?  
Are you doing so from a terminal?(I assume so)
Have you ever used nano?(Nano is a terminal based text editor that's quite easy to use.)

Also, type
```
sudo uname -a

```
into a terminal and post back what it says.  This will tell us the specific version of the linux kernel running to ensure you are indeed running Maverick.

---

### Post by senor_smile on 2010-12-04
> **JoJerome said:**
> I sure hope someone in the know is still watching this thread to help us beginners! 

I'm trying to follow the instructions on the first page but keep getting error messages to the effect of: gedit: command not found.

I'm using Maverick on an older IBM Thinkpad, trying to install a Verizon USB760 card. Naturally, Verizon tech support had never heard of Linux. 

Thanks in advance!

By the way, Verizon does actually have Linux drivers for the 760 aircard.  However, they're only available to Business "enterprise" customers.  That modem works just fine without the drivers using built in commands.  

On further thought, have you tried simply plugging the 760 aircard in and looking in network manager (the place where you can normally see wifi connections) for a new device. I have used quite a few different verizon aircards in ubuntu 10.10 and have always had success using network manager.  It's quick and simple and doesn't involve any terminal work.  

Let us know how you fare or if you don't get any where.

---

### Post by JoJerome on 2010-12-04
Thank you both for the speedy replies! It's finals week, my Mac just died, and I'm screwed enough without at least getting my Linux backup laptop here fully net-friendly. Here's what I'm getting:

~$ sudo gedit /etc/init.d/mountdevsubfs.sh
sudo: gedit: command not found
~$ sudo uname -a
Linux death 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010 i686 GNU/Linux


As to Network Manager, I'm seeing under System Settings -> Network Settings ... is that what you mean? I'm not seeing the Verizon card anywhere there.

---

### Post by senor_smile on 2010-12-04
> **JoJerome said:**
> Thank you both for the speedy replies! It's finals week, my Mac just died, and I'm screwed enough without at least getting my Linux backup laptop here fully net-friendly. Here's what I'm getting:

~$ sudo gedit /etc/init.d/mountdevsubfs.sh
sudo: gedit: command not found
~$ sudo uname -a
Linux death 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010 i686 GNU/Linux


As to Network Manager, I'm seeing under System Settings -> Network Settings ... is that what you mean? I'm not seeing the Verizon card anywhere there.

The network manager will probably be a much easier and stable(imho) way of connecting this 760 aircard in maverick.  

The network manager is probably a little icon near the upper right portion of the top toolbar.  It will either have two arrows, one pointing up and one pointing down, or a little wireless symbol.  
Here are some examples:

[URL="http://ubuntu.allmyapps.com/data/n/e/network-manager-gnome-network-manager/icon_48x48_icon.png"]http://ubuntu.allmyapps.com/data/n/e/network-manager-gnome-network-manager/icon_48x48_icon.png
[/URL]

[URL="http://shot1.org/wp-content/uploads/2010/04/screenshot70.png"]http://shot1.org/wp-content/uploads/2010/04/screenshot70.png
[/URL]

[]("http://primevpn.org/images/setup/linux-openvpn/24.jpeg")[http://primevpn.org/images/setup/linux-openvpn/24.jpeg](http://primevpn.org/images/setup/linux-openvpn/24.jpeg)

It changes based on what type of connection is currently the default, I believe.  

Also, when you first plug the 760 into the USB port, does a new "hard disk" appear on your desktop?  I have a spare 760 at my office, so I can try it out Monday if you still haven't gotten it connected.

---

### Post by JoJerome on 2010-12-04
Ok, I see the interface you're talking about. I also tried under network settings, setting up a new CDMA celluar connection. It asks for phone number, which I have, and user name and password. Verizon tells me there's no specific username and password affiliated with this account. Am I just making one up?

Secondly, I'm not seeing a way to disconnect from the wifi in order to try connecting with the broadband, other than maybe to delete the wifi from network settings.

---

### Post by senor_smile on 2010-12-04
> **JoJerome said:**
> Ok, I see the interface you're talking about. I also tried under network settings, setting up a new CDMA celluar connection. It asks for phone number, which I have, and user name and password. Verizon tells me there's no specific username and password affiliated with this account. Am I just making one up?

Secondly, I'm not seeing a way to disconnect from the wifi in order to try connecting with the broadband, other than maybe to delete the wifi from network settings.

I believe the settings should be as follows:

Username = [email]1234567890@vzw3g.com[/email]
Password = yourpassword
Phone = #777

replace the 1234567890 with the phone number of the aircard(sometimes you can just leave it as 1234567890 and it won't even matter)
yourpassword doesn't matter either.  Just leave it.  
The phone number HAS to be #777.  That's the modem number for verizon aircards to dial up.  

As far as the wifi thing; if you are actually connected to a wifi network, underneath the connection there would be a Disconnect link.  You can always right click on the network manager and uncheck "Enable Wireless".  Your wired connections and aircard connections will still be enabled.

---

### Post by JoJerome on 2010-12-04
Holy crap ... Senor_Smile, I owe you a drink, or a hug, or something!

As with so many things Kubuntu, I knew it had to be something simple, it's just getting there. And I can't believe Verizon tech support has nothing to help with Linux users.

So now while I panic over my non-booting mac with all my school notes on it, I at least have my wonderfully working backup Linux machine upon which to finish writing term papers. Thanks again and again and again...


:D

---

### Post by senor_smile on 2010-12-04
> **JoJerome said:**
> Holy crap ... Senor_Smile, I owe you a drink, or a hug, or something!

As with so many things Kubuntu, I knew it had to be something simple, it's just getting there. And I can't believe Verizon tech support has nothing to help with Linux users.

So now while I panic over my non-booting mac with all my school notes on it, I at least have my wonderfully working backup Linux machine upon which to finish writing term papers. Thanks again and again and again...


:D

haha.  glad you got it connected.

---

### Post by Mach1US on 2010-12-04
> **JoJerome said:**
> I sure hope someone in the know is still watching this thread to help us beginners! 

I'm trying to follow the instructions on the first page but keep getting error messages to the effect of: gedit: command not found.

!
I used to have USB760 and problem with it was that it have built in CD-Rom emulator which has to be disabled in order to prjojperly assign dev identifier.

Can you post output from following command:
```
ifconfig

``` 
also can you tell me what happens when you just type gedit by itself.
Additionally if left click on your wireless connection icon you will see option to disconnect from a particular wireless network

---

### Post by JoJerome on 2010-12-05
D'oh!!!

~$ sudo gedit /etc/init.d/mountdevsubfs.sh
sudo: gedit: command not found
~$ sudo uname -a
Linux death 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010 i686 GNU/Linux

Am installing it now. 

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:60:2d:18:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:04:23:6e:9b:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:120350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81761905 (81.7 MB)  TX bytes:6748919 (6.7 MB)
          Interrupt:11 Base address:0x6000 Memory:c0200000-c0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186756 (186.7 KB)  TX bytes:186756 (186.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.211.93.175  P-t-P:66.174.216.161  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5854120 (5.8 MB)  TX bytes:463373 (463.3 KB)

---

### Post by Mach1US on 2010-12-05
Looks like you have ip from your cell connection, unfortunately most likely you will need to restart your laptop to connect again if you pull the 760 out or suspend the laptop, instructions at the beginning of this thread fixes this issue.

Just FYI you can also turn in on or off via command line:
```
ifconfig          -displays all interfaces on your machine
iwconfig          -displays wireless interfaces
sudo ifdown eth1  -takes wireless(usually eth1)interface down
sudo ifup eth1    -brings wireless interface up (eth1 in this case)
sudo dhclient eth1  -refreshes DHCP
sudo lshw -C network  -shows all NIC interface info
sudo /etc/init.d/network restart   -to restart networking services
```

---

