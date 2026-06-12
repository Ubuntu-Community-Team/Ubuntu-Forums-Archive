---
title: "Globe Tattoo on Ubuntu Jaunty"
date: 2009-10-02
forum: Philippine Team
---

### Post by ragadanga63 on 2009-10-02
I recently got myself a Globe Tattoo USB Modem.  I followed the installation instructions from this site:  [http://neildecapia.wordpress.com/2009/07/05/globe-tattoo-on-ubuntu-jaunty-9-04/](http://neildecapia.wordpress.com/2009/07/05/globe-tattoo-on-ubuntu-jaunty-9-04/).  It worked flawlessly.  

My daughter also bought another Tattoo for her laptop. As she has no Terminal knowledge, I made a script for her.  I figure I'll share this with the rest of you just in case you need it.  (This is my first script, so proceed at your own risk.)

Installing Globe Tattoo Huawei E1552 HSDPA USB Stick on Ubuntu Jaunty.  Make sure that the Globe Tattoo USB Modem is NOT PLUGGED at this time:

1.  First download the attached file.  This tar file contains the following:
     a)    The files **62-option-modem-modeswitch.rules**
     b)    **globetattooinstall.sh** This file is the installation script.
     c)    **udev-extras** .deb package for Ubuntu Jaunty Jackalope
2.  Extract above files to the desktop.
3.  Click on the file globetattooinstall.sh.  Then click on "Run on Terminal"
4.  Supply your password as required.
5.  Wait.
6.  The Terminal closes and you're done.

Above script has been tested on MoonOS (3 pc's) and Ubuntu Jaunty (2 pc's).  It obviously will not run on other Ubuntu versions as the udev-extras package is for Ubuntu Jaunty.

Good luck.

---

### Post by Script Warlock on 2009-10-02
nice thanks for sharing...

---

### Post by kulabong on 2009-10-12
I've been looking for this, salamat po!
Try ko later...:popcorn:

---

### Post by girlette on 2009-11-16
will this work on Hardy? :)

---

### Post by john patol on 2009-11-16
gagana ba ito sa E156G?

---

### Post by artesm8 on 2009-11-17
Hi, 

Thank you for posting the fix for jaunty. 
I seem to have the same probl
broadband stick to work.

---

### Post by hkphooey on 2009-11-22
Excellent. Got this working with your help. 

Now my only problem is the speed. I'm getting about 1kb/sec. Google main page takes 50 seconds to load. Actually slower than my 2400 baud modem I had 20 years ago ... I love the Philippines.

---

### Post by pinoyskull on 2009-11-22
> **hkphooey said:**
> Excellent. Got this working with your help. 

Now my only problem is the speed. I'm getting about 1kb/sec. Google main page takes 50 seconds to load. Actually slower than my 2400 baud modem I had 20 years ago ... I love the Philippines.
maybe you're connected using GPRS, lock it to WCDMA/UMTS/HSDPA then see what happens.

BTW im using Globe Visibility locked to HSDPA, my speed varies from 30Kbps ~ 2mbps

---

### Post by hkphooey on 2009-11-22
I think its highly likely I'm connecting via GSM (not even GPRS). In the last two houses I've lived in I've been unable to get a 3G signal - when I turn it on, I'm unable to receive calls or SMS. Great stuff, but I've learnt to live with it ... 

> maybe you're connected using GPRS, lock it to WCDMA/UMTS/HSDPA then see what happens.

So how do you lock the modem to one of these under Linux? I'll definitely give it a try, and even if I get 30kb/s I'll be happy. I've found this link [http://ubuntuforums.org/showthread.php?p=8340483](http://ubuntuforums.org/showthread.php?p=8340483) which looks hopeful, so I'll tinker around with that this evening.

---

### Post by hkphooey on 2009-11-22
> **ragadanga63 said:**
> Installing Globe Tattoo Huawei E1552 HSDPA USB Stick on Ubuntu Jaunty.  Make sure that the Globe Tattoo USB Modem is NOT PLUGGED at this time:


If I can suggest a slight modification to your script, it can all be done in a couple of lines. 

```
#! /bin/bash

read -p "This script installs Globe Tattoo USB Modem on Ubuntu. Please unplug it and press any key to continue" 
sudo apt-get install udev-extras
sudo echo 'ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"' > /etc/udev/rules.d/62-option-modem-modeswitch.rules
sudo /etc/init.d/udev restart
echo "Process completed.  Please insert Globe Tattoo modem."
```

---

### Post by pinoyskull on 2009-11-22
> **hkphooey said:**
> I think its highly likely I'm connecting via GSM (not even GPRS). In the last two houses I've lived in I've been unable to get a 3G signal - when I turn it on, I'm unable to receive calls or SMS. Great stuff, but I've learnt to live with it ... 

> maybe you're connected using GPRS, lock it to WCDMA/UMTS/HSDPA then see what happens.

So how do you lock the modem to one of these under Linux? I'll definitely give it a try, and even if I get 30kb/s I'll be happy. I've found this link [http://ubuntuforums.org/showthread.php?p=8340483](http://ubuntuforums.org/showthread.php?p=8340483) which looks hopeful, so I'll tinker around with that this evening.
i used to use UMTSMon ([http://ubuntuforums.org/showthread.php?p=5449081](http://ubuntuforums.org/showthread.php?p=5449081)) or you can boot to XP and do it via MobileConnect

---

### Post by Samhain13 on 2009-12-03
> **girlette said:**
> will this work on Hardy? :)

Right. Here's what I did. (Forgive me for not crediting other sources, I wasn't able to bookmark them).

Anyway, if you have a Huawei dongle, you can try the instructions here:
[http://tux-n00b.blogspot.com/2009/05/huawei-ec168c-on-ubuntu-804-hardy-heron.html](http://tux-n00b.blogspot.com/2009/05/huawei-ec168c-on-ubuntu-804-hardy-heron.html)

That's for dealing with the "flip-flop" nature of the dongle. Basically, you need to get the dongle recognised as a modem instead of a mass storage device.

Then, you need to run wvdialconf:
```
$ sudo wvdialconf 
```

This will detect you modems.

Of course, wvidal and wvdialconf should be installed in your system. I believe it already comes with the default installation.

Then, edit the file /etc/wvdial.conf:
```
$ gksu gedit /etc/wvdial.conf
```

It should contain this:
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","http.globe.com.ph"
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = globe
Username = globe
Stupid Mode = yes
```

Save and close.

To start the connection:
```
$ sudo wvdial
```

To terminate the connection:
Focus on the terminal where you started the connection and press CTRL + C.

---[edit]---

You can also use Wammu to manage the SIM, or treat the dongle as a cellphone. To get Wammu:
```
$ sudo apt-get install wammu
```

This works only if:
1. the dongle is recognised as a modem
2. you are not connected to the Internet via the dongle
3. the dongle is not mounted but is still attached to a USB port

**To configure Wammu** through the Phone Wizard:
1. select Guided Configuration, next
2. set connection type to USB Cable, next
3. set phone type to "I don't know", next
4. set connection type to AT Based, next
5. next
6. port field should be "/dev/ttyUSB[x]" (where [x] is a number, mine is 0, so /dev/ttyUSB0), next
7. wait for Wammu to complete testing the phone, mine said "Manufacturer: huawei, Model: unknown", next
8. put a name for your new profile, like "Globe Tattoo", **finish**

**To connect to your "phone"**: **Phone** > **Connect**

**To check your balance**:
1. **Create** > **Message**
2. check "Send message"
3. set Recipient's numbers to 222
4. in the message box, type: BAL
5. send

Finally: wait a couple of minutes, then **Retrieve** > **Messages**. You should now see a new entry from GLOBE in the box middle, click it to read the response to your balance enquiry.

---

### Post by manilaph on 2009-12-17
guys,

i have both the globe tattoo and smartbro huawei usb modems and they are both automatically detected by network manager although some editing of the configurations must be done.

For example, the APN of globe tattoo should be http.globe.com.ph (erase the passwords)

and for smartbro, erase the passwords too and APN smartbro

---

### Post by brgenst on 2009-12-17
These are init strings.

For Huwawei
Any: **AT^SYSCFG=2,0,3FFFFFFF,2,4**
2G: **AT^SYSCFG=13,1,3FFFFFFF,2,4**
3G: **AT^SYSCFG=14,2,3FFFFFFF,2,4**
2G preferred: **AT^SYSCFG=2,1,3FFFFFFF,2,4**
3G preferred: **AT^SYSCFG=2,2,3FFFFFFF,2,4 **

For ZTE
ANY: **AT^ZSNT=0,0,0**
2G_ONLY: **AT^ZSNT=1,0,0**
3G_ONLY: **AT^ZSNT=2,0,0**
2G_PREF: **AT^ZSNT=0,0,1**
3G_PREF: **AT^ZSNT=1,0,2**

Though I don't know how to use it, no option for init strings is available in NetworkManager. Maybe you put it in gconf?

---

### Post by AlexanderDGreat on 2010-01-14
> **manilaph said:**
> guys,

i have both the globe tattoo and smartbro huawei usb modems and they are both automatically detected by network manager although some editing of the configurations must be done.

For example, the APN of globe tattoo should be http.globe.com.ph (erase the passwords)

and for smartbro, erase the passwords too and APN smartbro

Maraming salamat po! Nagwork ito sa Karmic using Globe Tattoo HUAWEI Model E160E.

I also installed gnome-phone-manager to check balances.

---

### Post by mvalviar on 2010-01-16
Hello. Ubuntu 9.10 po gamit ko. Nasubukan ko na yung instrutions dito. Eto po ginawa ko.

1) Plug in globe tatoo usb.

2) Set up yung connection using the wizard from network manager applet. For the service type I selected Internet which is the default on the drop down. I'm not sure which one to choose honestly.

3) Tweaked the settings. Inalis ko yung laman ng username at password field and changed APN to http.globe.com.ph

Nakakaconnect naman po ako pero it only lasts for a few seconds.

Gumawa po ko ng seperate post regarding this [here]("http://ubuntuforums.org/showthread.php?p=8672956#post8672956"). 

Naobserbahan ko po kasi dun sa logs na parang connect/disconnect yung ginagawa ng os.

Patulong naman po. I really need to get this to work. Nasa probinsya po ako. Meron ako linya ng net pero in a week it is down for at least a day. Kailangan ko po naman internet ko sa trabaho. Sana po matulungan nyo ako.

Tagtataka lang ako. Nag-paload ako ng Php 20 (1 hr) para i-test to pero di ko naman sya nagamit for reasons described above. Pero naubos load ko? I this related to item 2 above?

As I was typing this the dongle is connected to my pc and I got this prompt ```

Unable to mount Globe Broadband

Error mounting: mount exited with exit code 32: mount: /dev/sr1 is not a valid block device

```

What am I doing wrong here?

Regards,

Marco Enrico Alviar

---

### Post by AlexanderDGreat on 2010-01-16
@mvalviar - ako po gamit ko Karmic,

> 1) Plug in globe tatoo usb.

2) Set up yung connection using the wizard from network manager applet. For the service type I selected Internet which is the default on the drop down. I'm not sure which one to choose honestly.

3) Tweaked the settings. Inalis ko yung laman ng username at password field and changed APN to http.globe.com.ph


Tama na po ito, don't remove username and password which is globe. Yung #2, yun naman po yun ang APN. Also, make sure na di maluwag ang usb device. Tingin ko, kaya naubos po ang load niyo kasi P5 / 15 mins every connection. So kapag connect niyo P5 kagad yun, disconnect, connect, etc... Also, medyo mabagal ang Globe Tattoo in my case, kaya you really need to wait. Nakapag browse po ba kayo?

---

### Post by mvalviar on 2010-01-17
Ok try ko po yang suggestion nyo. 

Kung wala ako load and meron ako connection. Makikita ko po dapat sa browser na kailangan ko na magload di ba? Ayaw ko po muna kasi magload before I'm sure it's 100% working. 

Hindi nga ako nakapagbrowse eh. Pagsinubukan ko na I connect sya via network manager applet. Connect lang sya for around 20 secs tapos maddc na.

---

### Post by AlexanderDGreat on 2010-01-17
> Kung wala ako load and meron ako connection. Makikita ko po dapat sa browser na kailangan ko na magload di ba?

Not really, magloload lang siya forever. Kaya po nauso yung proxying to get free Internet browsing. :) 

> Ayaw ko po muna kasi magload before I'm sure it's 100% working. 

Sadly, kelangan niyo po talaga ng load. Pero just do what you did and make sure you're not getting disconnected, magwowork yan!

> Hindi nga ako nakapagbrowse eh. Pagsinubukan ko na I connect sya via network manager applet. Connect lang sya for around 20 secs tapos maddc na.

Advice ko lang po. 1. Isolate the problem. Kuha muna po kayo ng stable connection. Try it on Windows, kung ganun pa rin at least alam niyo na hardware ang issue, if not then sa Karmic ang issue. 2. Magload po kayo kahit na P50. It sucks but education has a price, para matest niyo talaga. :) 3. Try to "remove then add" a new mobile connection in the nm-applet. Just make sure may login, password, at APN, all else are defaults. 4. Kapag nakaconnect na kayo make sure you have this in /etc/resolv.conf - here's mine: nameserver 202.126.40.5 nameserver 222.127.143.5

---

### Post by mvalviar on 2010-01-17
> **AlexanderDGreat said:**
> Not really, magloload lang siya forever. Kaya po nauso yung proxying to get free Internet browsing. :) 

Kala ko parang sa windows. Pagwala load nareredirect yung broswer sa isang page na nagsasabing wala na ako load

> **AlexanderDGreat said:**
> 
Advice ko lang po. 1. Isolate the problem. Kuha muna po kayo ng stable connection. Try it on Windows, kung ganun pa rin at least alam niyo na hardware ang issue, if not then sa Karmic ang issue. 2. Magload po kayo kahit na P50. It sucks but education has a price, para matest niyo talaga. :) 3. Try to "remove then add" a new mobile connection in the nm-applet. Just make sure may login, password, at APN, all else are defaults. 4. Kapag nakaconnect na kayo make sure you have this in /etc/resolv.conf - here's mine: nameserver 202.126.40.5 nameserver 222.127.143.5

Natry ko na rin sa windows eh. After ko magpaload sa windows ko muna try. Nakakabrowse naman ako. Pero naddc rin sya after a while. It's either
1) Mahina signal ng globe.
2) Mahina yung power supply ng usb port

Natest ko na rin yung dongle sa pc ng kaibigan ko ok naman sya.

Since you provided me with the correct setting which I know works on your karmic madali na siguro 'to (I hope).

Salamat sa reply.

---

### Post by mvalviar on 2010-01-17
Ok na ser thanks sa help. I'm replying to this thread as I'm connected to globe tatoo. 

Now, pano nga proxying? >:)

---

### Post by AlexanderDGreat on 2010-01-17
Nice one sir! Ito po yung mga links:

[http://www.gensansale.com/viewtopic.php?t=7878]("http://www.gensansale.com/viewtopic.php?t=7878")

[http://www.pinoyrepublic.org/f44/globe-tattoo-smartbro-free-internet-browsing-20414/]("http://www.pinoyrepublic.org/f44/globe-tattoo-smartbro-free-internet-browsing-20414/")

[http://www.istorya.net/forums/computer-hardware/229319-free-unlock-codes-for-globe-tattoo-smartbro-and-sun-modems-huawei-and-amoi-brands-only.html]("http://www.istorya.net/forums/computer-hardware/229319-free-unlock-codes-for-globe-tattoo-smartbro-and-sun-modems-huawei-and-amoi-brands-only.html")

I believe ito magagawa niyo kapag binasa niyo mga yan:

1. Switch SIM cards so you can use Globe, Smart, or Sun using any Mobile Internet modem (like Globe Tattoo) - ito yata yung inuunlock.

2. Free Internet basta punta lang kayo sa website na ibibigay nila tapos you enter the URL in that website you want to go to.

Haven't tried them because busy pa. I think no. 2 is useful if you're setting up a home webserver and you can't check it because you're on your home network, for educational purposes only. Good luck!

---

### Post by mvalviar on 2010-01-18
Ser Alexander. You mentioned gnome-phone-manager. I want to try I out. I read about it else where on the net. Pano ko gagamitin to sa globe tatoo? To send and receive messages to and from my pc. Parang yung globe tatoo app sa windows.

Off topic: Na try ko na to gamitin sa cellphone. Nokia 3220 pero clock synching lang nakuha kong function.

Maraming salamat.

---

### Post by AlexanderDGreat on 2010-01-18
Sir dali lang yan.

```
sudo apt-get install gnome-phone-manager
```

Tapos to launch it, Applications > System Tools > Phone Manager

Magkakaroon kayo ng icon sa panel niyo. Click on Preferences - tapos lagay niyo po sa port /dev/ttyUSB0 or /dev/ttyUSB1 - it depends kung san po nadetect ang phone niyo, then for me, I needed to restart kasi di nakakareceive ng text. Note: It's only for receiving and sending SMS, no phonebooks, etc... Then send to 222, message: bal. Tapos magaapear you have a text message w/ your current balance. :)

---

### Post by budigos on 2010-03-17
Mukhang promising itong gnome phone manager ah.. i'll try installing this tomorrow.

As for globe tattoo, di pa rin ako makapag-connect on Ubuntu Jaunty. I'm using Huawei E1550 usb dongle (had it unlocked). Sun Cellular, Smart Buddy and Smart Bro connects fine. Pero pag globe SIM, ayaw talaga. So I don't think it's a USB power supply issue since other SIMs are able to connect. Hmmmm.... Pero yun, la lang, Adik lang gusto lang mapagana lahat ng SIM. Hehe. :p

---

### Post by shun_kent on 2010-11-09
pwede po pa unlock yung globe tatoo ko.
 
Globe Tatoo
Model:E1552
IMEI:353143030380738
Software Version:11.300.05.18.158

---

### Post by shun_kent on 2010-11-09
Globe Tatoo
Model:E1552
IMEI:353143030380738
Software Version:11.300.05.18.158

---

### Post by caloy230 on 2011-06-14
pare anything for smartbro zte mf627,di kse mdetect sakin e..ubuntu 11.04 aq

---

### Post by elite1826 on 2011-08-15
> **hkphooey said:**
> If I can suggest a slight modification to your script, it can all be done in a couple of lines. 
 
```
#! /bin/bash
 
read -p "This script installs Globe Tattoo USB Modem on Ubuntu. Please unplug it and press any key to continue" 
sudo apt-get install udev-extras
sudo echo 'ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"' > /etc/udev/rules.d/62-option-modem-modeswitch.rules
sudo /etc/init.d/udev restart
echo "Process completed.  Please insert Globe Tattoo modem."
```
 
 
how to run this script?

---

### Post by tech-hero on 2011-08-15
copy and paste lang bro. or pwede ding ipaste mo nalng per line sa terminal. :)

---

### Post by elite1826 on 2011-08-16
> **tech-hero said:**
> copy and paste lang bro. or pwede ding ipaste mo nalng per line sa terminal. :)


ah ok po tnxz: )

---

### Post by Aj pasig on 2012-01-16
bos papano po xa irun kc hnd po xa mag run na exract ko na po xa sa may dextop wla po lomalabas na run

---

