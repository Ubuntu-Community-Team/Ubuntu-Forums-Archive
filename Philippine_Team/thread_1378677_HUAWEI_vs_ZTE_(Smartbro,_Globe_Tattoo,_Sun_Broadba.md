---
title: "HUAWEI vs ZTE (Smartbro, Globe Tattoo, Sun Broadband)"
date: 2010-01-11
forum: Philippine Team
---

### Post by manilaph on 2010-01-11
I have noticed that using Huawei USB 3G sticks are better than the ZTE models.

Out of the box Ubuntu 9.10, the Smartbro E156C model and the Globe Tattoo E1552 models work.

I am still trying to make my Sun Broadband Huawei E1550 to work.

I have an old ZTE MF622 and it does not work out of the box.

The new Smartbro (black model ZTE MF627) also does not work out of the box.

Care to share your Huawei or ZTE experiences?

---

### Post by stormsurge on 2010-01-11
Dude, I am currently using the new Smart Bro Plug-it. I got some help from Ubuntu community to make it work. So far, I am happ because I could surf the web almost ANYWHERE because Smart Bro has better network coverage....

---

### Post by manilaph on 2010-01-11
Thank you for sharing.

Could you please post the model (make and number) and a link on how you got it working?

So far, based on what I've read even on the non Philippines Ubuntu threads, Huawei is easier to use than ZTE because the Huawei models are more accessible to the developers abroad.

Thanks!

---

### Post by stormsurge on 2010-01-12
**[FONT=Arial]The new Smart Bro Plug it is MF627. For the step-by-step procedure, you may see the thread URL below. I provided a step by step procedure on how to make the new Smart Bro work. Of course, I would like to cite Sir Pepe Machine and Sir Loell as my references. Enjoy![/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial][http://ubuntuforums.org/showthread.php?t=1351927](http://ubuntuforums.org/showthread.php?t=1351927)[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial] [/FONT]**

---

### Post by kilosan on 2010-01-12
> I am still trying to make my Sun Broadband Huawei E1550 to work.
what seems to be the problem?

> I have an old ZTE MF622 and it does not work out of the box.

that thing works on older ubuntu versions.

---

### Post by Samhain13 on 2010-01-13
I haven't tried a lot of products but from my very short and narrow experience, I found it easier to work with Huawei. I tried both ZTE (PLDT WeRoam) and Huawei (Globe Tattoo) in Hardy and in Karmic. I was able to connect to Globe in both Ubuntu versions, but never to PLDT.

But as I said, that's a short and narrow experience. :D

---

### Post by manilaph on 2010-01-13
Huawei simply works "out of the box" and that is what newbies like. They do not like to follow strange (to them) codes or do scripts etc.

Just simply follow this tutorial and it also works for Karmic. This is for the Huawei model E156C and you will see how easy it is.

[http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/](http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/)

---

### Post by manilaph on 2010-01-14
It is confirmed.

My Sun Broadband Huawei E1550 works out of the box.

The only problem was that my load expired after 4 days and I had to reload regular load instead of those "time based" load.

Good job to Huawei.

---

### Post by e_mags18 on 2010-01-30
> **manilaph said:**
> It is confirmed.

My Sun Broadband Huawei E1550 works out of the box.

The only problem was that my load expired after 4 days and I had to reload regular load instead of those "time based" load.

Good job to Huawei.

Newbie here...

Sir, how did you make this work? I've also HUAWEI E1550, got it free from my new laptop but unable to use it on my ubuntu because i can't connect to the net. Even it is detected i cannot make it work. I have a blue light on the stick but don't know if i'm conected. Unlike when i'm using it on my Windows 7 Pro there's Sun application need to click "Connect" to start browsing. Any inputs will be much appreciated.
Thanks.

---

### Post by manilaph on 2010-01-31
can you please tell us what did you do to say that it does not work?

did you configure your huawei?

you can follow this [http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/](http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/) but please choose Sun/digitel instead of smart

---

### Post by e_mags18 on 2010-01-31
Thanks for the link S' manilaph.

I don't know whats wrong on my Sun Broadband it does say "Connection Established" but once I start browsing I get server not found. I got this free and it comes with php10,800 load good for 3 months use.
Anyway, thanks a lot. I will be using my wifi na lang to explore UBUNTU 9.10

:p:p:p

---

### Post by brgenst on 2010-02-01
> **e_mags18 said:**
> Thanks for the link S' manilaph.

I don't know whats wrong on my Sun Broadband it does say "Connection Established" but once I start browsing I get server not found. I got this free and it comes with php10,800 load good for 3 months use.
Anyway, thanks a lot. I will be using my wifi na lang to explore UBUNTU 9.10

:p:p:p

Use PAP lang on the PPP Settings configure and uncheck EAP, CHAP, MSCHAP, MSCHAPv2.

---

### Post by kilosan on 2010-02-02
or make sure your ubuntu 9.10 is up to date.

---

### Post by lod2 on 2010-03-02
> **manilaph said:**
> I have noticed that using Huawei USB 3G sticks are better than the ZTE models.

Out of the box Ubuntu 9.10, the Smartbro E156C model and the Globe Tattoo E1552 models work.

I am still trying to make my Sun Broadband Huawei E1550 to work.

I have an old ZTE MF622 and it does not work out of the box.

The new Smartbro (black model ZTE MF627) also does not work out of the box.

Care to share your Huawei or ZTE experiences?

Here are the steps to make ZTE MF627 nearly work out of the box for ubuntu 9.10

**How to make Smart Bro ZTE MF627 work on Ubuntu 9.10** 			 			 			 		   		 		 		**Smartbro on Ubuntu 9.10**

Device Needed:
-Smartbro USB modem model: ZTE MF627

Instructions:

1. Plug in the usb device. Once it appears on your desktop, right click the smartbro icon and select _eject_
2. The light will go out. Wait for a while until it goes back again. At this point, the usb is now switched from card reader to a modem.
3. Right click network manager and select _Edit Connections_
4. Select the _Mobile Broadband_ tab and click the _Add_ button
5. A window would appear and by default, the _ZTE Incorporated ..._ is selected. Click _Forward_
6. Select _Philippines_ as the provider's country and click _Forward_. A list of providers will be displayed. Choose _Smart_ and click [U]Forward
[/U]7. On the billing plan, click the drop down menu (the one which says _Default_) and select _My Plan is Not Listed_. A blank text box will appear.
    Type _smartbro_ as your access point name and click _Forward_ then click _Apply_

A new window will appear. There are many textboxes here but you only need to modify a few. 

8. Select the _PPP Settings_ Tab and click the _Configure Methods_ button
9. Uncheck all methods except PAP. Click _Ok_. Optionally you may also click _Connect Automatically_ then finally click _Apply_.
10. After clicking apply, your modem will attempt to connect. You will notice that the green light from your modem will start to blink and a 
   message saying _Established Connection_ or something similar will appear. Open your browser and test if you are now able to browse the web. If 
not, give wait for about 30 sec and retry opening your browser again. If it still fails, remove your usb and repeat steps 1 & 2. If all fails, repeat 
    all the steps. 

**More Tips:**

-When finished surfing, _left click_  the _network manager icon_ and click _disconnect_.
-When reconnecting, repeat step 1 & 2. And if you have checked _Connect Automatically_ from step 8, your modem will automatically connect the 
 moment it switches into modem mode.

---

### Post by aljoriz on 2010-03-02
I have both smartbro and tattoo

Smart MF627 requires you eject the smartbro CD and wait for 5min or you could download the easy mf627 by Mr. hughes and STILL WAIT for 5 minutes before the dongle would work. 

Tattoo e1552 simplly works from the get go. Too bad it does not have any unli offers like smart does (200 for 5days of unli via smart.com.ph web connect)

---

### Post by lavezarez on 2010-03-05
> **manilaph said:**
> I have noticed that using Huawei USB 3G sticks are better than the ZTE models.

Out of the box Ubuntu 9.10, the Smartbro E156C model and the Globe Tattoo E1552 models work.

I am still trying to make my Sun Broadband Huawei E1550 to work.

I have an old ZTE MF622 and it does not work out of the box.

The new Smartbro (black model ZTE MF627) also does not work out of the box.

Care to share your Huawei or ZTE experiences?

My recent experiences: 
1. Huawei E160 - Sun: with Ubuntu 9.10 Netbook Remix, or Ubuntu 9.10, or Linux Mint 8 - all with Linux kernel 2.6.31 works out-of-the-box

2. ZTE MF627 - Smartbro: with Ubuntu 9.10 Netbook Remix - dismal experience, couldn't get it to consistently work, kernel version was 2.6.31-20 (latest update downloaded as of March 5, 2010). It simply couldn't work out-of-the-box.  

Downloaded a PPA for the ZTE and usbmodeswitch thingy from [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way), and that helped Ubuntu see the ZTE during Network Connection setup of the new broadband.  But still no connection.

Then followed the steps in post #8 of this thread: [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934) and was estatic for a brief moment because then Smartbro got connected and I had Internet.  

But when I shut down the netbook, and later turned it on, AGAIN the ZTE modem couldn't connect anymore, although I verified the lsusb and all the things said in the thread and post#8.

So I have to totally agree with you:  Huawei modems DO WORK BETTER with Linux (not only Ubuntu), provided the kernel is not lower that 2.6.3x, I believe.  I had issues if the kernel was 2.6.2x.
HUAWEI E1550 Prepaid Sun also works painlessly.

---
as a side note: I do wish there was an easy source like a centralized wiki on how to successfully configure ZTE Smartbro modems to work on Ubuntu 9.10 (or Easy Peasy for that matter) and not make it so fragile that an innocent sudo apt-get update would destroy and reset the settings of the modem.  This issue was the **one** thing that prevented me from recommending to convert about 30+ netbooks from virus-laden Windows XP to Linux in the company I work for.

---

### Post by aljoriz on 2010-03-05
ZTE mf627 is pain even with the zte easy from Mr. Green Hughes, as you have to wait for a few minutes before the modem actually works.  

On a side note, there's an old Smartbro that uses Huawei and that works great on ubuntu ONLY if you can find one.

---

### Post by jurusu on 2010-03-17
> **brgenst said:**
> Use PAP lang on the PPP Settings configure and uncheck EAP, CHAP, MSCHAP, MSCHAPv2.

Huawei works fine with my ubuntu. 

What are EAP, CHAP, MSCHAP, MSCHAPv2? I also experience "connection established" but cant open webpages. So I try to disconnect and reconnect a couple of times until I can open webpages. I think I also left EAP and others "checked."

---

### Post by lod2 on 2010-03-19
> **jurusu said:**
> Huawei works fine with my ubuntu. 

What are EAP, CHAP, MSCHAP, MSCHAPv2? I also experience "connection established" but cant open webpages. So I try to disconnect and reconnect a couple of times until I can open webpages. I think I also left EAP and others "checked."

I experienced the same thing with my ZTE MF627 on Ubuntu 9.10, and I have yet to verify with post #15 if there's really a 5 minute delay before the modem actually works (despite having the "connection established" message appearing after a few seconds).

For the mean time, I'd go with the disconnect/reconnect thingy, because it works after a few retries without the need to go deep into modifying configurations and such.;)

---

### Post by aljoriz on 2010-03-20
Binenta ko na lang yung Smartbro ZTE MF627 ko at bumili na lang ng Smartbro Hauwei E1552 (white color) madali pang i-openline, you just need a the imei number, huawei code calculator and globe/sun sim para pag hina signal ng smart lipat ka sa globe.

yup Huawei E1552 is more linux friendly.

---

### Post by Arnold Martin on 2010-09-11
Off topic. Post deleted.

---

### Post by jeffreyvergara.NET on 2010-09-14
off topic, but just want to know the difference between huawei broadband usb modem model e156c / e1553 like speed etc?

---

### Post by Script Warlock on 2010-09-14
smartbro 100% working sa laptop ko using network manager.. 

Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

lsusb:

ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636

what i did:

1. add mobile broadband
2. "setup a mobile broadband connection" create a connection for this mobile broadband device - mine is -- ZTE Incorporated ZTE WCDMA Technologies MSM 
3. click forward
4. choose philippines
5. select your provider -- SMART
6. billing plan -- DEFAULT
7. APN -- internet
8. confirm settings and apply

what inside my smart default:

numer: *99#
username: scriptwarlock (my login name)
password: ******** (my login password)
APN: internet

yun lang and now i have net with smartbro... no idea paano masilip load balance.

---

### Post by apolloltiujr on 2010-09-15
[B][URL="http://blag.borap.net/2010/06/13/sun-broadband-on-ubuntu-10-04/"]
[/URL][/B]

Sun Broadband on Ubuntu 10.04

If you are using Sun Broadband Wireless (tested on Huawei E1550) and want it to work on Ubuntu 10.04 (Lucid Lynx), just install the linux-backports-modules-headers-lucid-generic package and the usb-modeswitch package.
view plain
print?
    $ sudo apt-get install linux-backports-modules-headers-lucid-generic usb-modeswitch

After installing, reboot.

Plug in the Sun Broadband. Then, a notification “New Mobile Broadband Connection” should appear. Follow the wizard dialog (you can just click next since the default values should be alright). Then, you should be connected now. 

Connection Name: Digitel (Sun Cellular) Connection

Mobile: *99#
Username:
Password:

Advance
APN: fbband
Network:
Pin:

---

### Post by apolloltiujr on 2010-09-15
Sun, Smart, or Globe Broadband on Ubuntu 10.04


If  you are using Sun Broadband Wireless (tested on Huawei E1550) and want  it to work on Ubuntu 10.04 (Lucid Lynx), just install the  linux-backports-modules-headers-lucid-generic package and the  usb-modeswitch package.view plainprint?   


$ sudo apt-get install linux-backports-modules-headers-lucid-generic usb-modeswitch


After installing, reboot.


Plug  in the Sun Broadband. Then, a notification “New Mobile Broadband  Connection” should appear. Follow the wizard dialog (you can just click  next since the default values should be alright). Then, you should be  connected now.


Connection Name: Digitel (Sun Cellular) Connection


Mobile: *99#
Username:
Password:


Advance 
APN: fbband
Network:
Pin:&#65279;

---

### Post by kor13ben on 2011-05-05
p { margin-bottom: 0.21cm; }  [FONT=Garuda][SIZE=2]Hi Folks,[/SIZE][/FONT]
 [FONT=Garuda][SIZE=2]I am failing to install the Huawei e1553 on my “emachine D725 from Acer”. I'm using Ubuntu 10.04 LTS. [/SIZE][/FONT] 
 [FONT=Garuda][SIZE=2]The [comgt info -d/dev/ttyUSB0 ] command gives two different answers for the [COLOR=#0047ff]IMEI and Serial Number[/COLOR] without having done any change to the modem between the two commands. [/SIZE][/FONT] 
 [FONT=Garuda][SIZE=2]The [ comgt -d /dev/ttyUSB0 ] command shows it to [COLOR=#ff0000]fail registration[/COLOR] and later to be r[COLOR=#ff0000]egistred on home network: “Smart”,2[/COLOR] [/SIZE][/FONT] 
 [FONT=Garuda][SIZE=2]Here what I get at  the Terminal[/SIZE][/FONT]
  

 

 [FONT=Verdana, sans-serif][SIZE=2]*kaspar@kaspar-laptop:~$ comgt -d /dev/ttyUSB0 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*SIM ready *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Waiting for Registration..(120 sec max) *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Registered on Home network: *[/SIZE][/FONT] 
 [COLOR=#ff3333][FONT=Verdana, sans-serif][SIZE=2]*Failed to register *[/SIZE][/FONT][/COLOR] 
 [FONT=Verdana, sans-serif][SIZE=2]*kaspar@kaspar-laptop:~$ comgt info -d/dev/ttyUSB0 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*##### Wireless WAN Modem Configuration ##### *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Product text: *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*==== *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*huawei *[/SIZE][/FONT] 
 [COLOR=#33cc66][FONT=Verdana, sans-serif][SIZE=2]*[COLOR=#000000]Model: E1553[/COLOR] *[/SIZE][/FONT][/COLOR] 
 [FONT=Verdana, sans-serif][SIZE=2]*Revision: 11.608.12.00.00 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*IMEI: 354112031977486 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*+GCAP: +CGSM,+DS,+ES *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*OK *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*==== *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Manufacturer:           *[/SIZE][/FONT] 
 [COLOR=#0047ff][FONT=Verdana, sans-serif][SIZE=2]*IMEI and Serial Number: *[/SIZE][/FONT][/COLOR] 
 [FONT=Verdana, sans-serif][SIZE=2]*Manufacturer's Revision: comgt 16:09:32 -> -- [COLOR=#0047ff]Error Report[/COLOR] -- *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*comgt 16:09:32 -> ---->                      ^ *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*comgt 16:09:32 -> Error @982, line 56, String is shorter than second argument. (7) *[/SIZE][/FONT] 
 

 

 [FONT=Verdana, sans-serif][SIZE=2]*kaspar@kaspar-laptop:~$ comgt info -d/dev/ttyUSB0 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*##### Wireless WAN Modem Configuration ##### *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Product text: *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*==== *[/SIZE][/FONT] 
 

 [FONT=Verdana, sans-serif][SIZE=2]*Manufacturer: huawei *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Model: E1553 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Revision: 11.608.12.00.00 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*IMEI: 354112031977486 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*+GCAP: +CGSM,+DS,+ES *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*OK *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*==== *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Manufacturer:           huawei *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*[COLOR=#0047ff]IMEI and Serial Number[/COLOR]: 354112031977486 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Manufacturer's Revision: *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*11.608.12.00. *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Hardware Revision:      *[/SIZE][/FONT] 
 

 [FONT=Verdana, sans-serif][SIZE=2]*Network Locked:         0 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Customisation:          *[/SIZE][/FONT] 
 

 [FONT=Verdana, sans-serif][SIZE=2]*Band settings:          ( *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*) *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*APN:                    1,"IP","SMARTBRO","0.0.0.0",0,0 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*##### END ##### *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*kaspar@kaspar-laptop:~$ comgt -d /dev/ttyUSB0 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*SIM ready *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Waiting for Registration..(120 sec max) *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*[COLOR=#ff0000]Registered on Home network: "SMART",2[/COLOR] *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*Signal Quality: 23,99 *[/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=2]*kaspar@kaspar-laptop:~$ *[/SIZE][/FONT] 
  

 

 

 [FONT=Verdana, sans-serif][SIZE=2]When I try to select the configured broadband connection listed under “available” in the Network-Manager it tells me after five “pulses” of the icon only that the GSM-Network is disconnected.[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]Could the Network-Manager be the problem?[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]Any help is highly appreciated.[/SIZE][/FONT]:grin::grin:
 

 [FONT=Verdana, sans-serif][SIZE=2]With many thanks     kor13ben[/SIZE][/FONT]

---

### Post by tech-hero on 2011-05-05
the first thing i did with huawei modems, i connected it to the internet first using windows, then boot in UBUNTU 10.04 LTS then it works. I didn't use usb-mode tool.

---

