---
title: "installing globe tattoo huawei e1552 in ubuntu 10.04"
date: 2010-06-06
forum: Philippine Team
---

### Post by gerryb23 on 2010-06-06
hello, im just a new user of ubuntu and experimenting on it. just installed ubuntu 10.04 last week. does anyone know how to install globe tattoo huawei e1552 usb dongle in ubuntu 10.04? will be glad to have a step by step instruction. thanks.

gerryb23

---

### Post by antoniomiguel on 2010-06-06
> **aljoriz said:**
> The QUICK GUIDE is in this site

[http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/](http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/)

just select GLOBE OR SMART OR DIGITEL for your provider.


There are some difference on the installation wizard since your using 10.04 and the guide is 9.04, but basically the idea is there.

---

### Post by gerryb23 on 2010-06-06
thanks antoniomiguel for the reply. i will try this out. :)

gerry

---

### Post by gerryb23 on 2010-06-06
Sir,

I tried the instructions that you posted here. This is what I did:

1. Right click network connections applet and click edit connections:

2. In the mobile broadband tab, click add.

3. IPv4 settings I set it at automatic PPP and clicked connect automatically, and clicked available to all users

4. In the mobile broadband tab I set the number (basic) as *99***1#

5. In APN I set it as http.globe.com.ph

6. In the PPP settings, I clicked configure methods... and set it to CHAP

Then I clicked Apply

However, having done all this, the mobile broadband connection did not appear in the network connections applet. Is there something missing, a step that I did not do?

Hope you could help me out sir. Many thanks.

Gerry

---

### Post by killer_d76 on 2010-06-06
try installing usb-mode-switch.. sudo apt-get install usb-mode-switch or simply go to Applications>Ubuntu Software Center>and type usb-mode-switch>click install.. this should fix the issue! ;)

[click here for more info]("http://ubuntuforums.org/showthread.php?t=1481930")

---

### Post by gerryb23 on 2010-06-06
killer, natry ko yung instructions mo. nadetect naman nya yung usb dongle at nagappear yung globe sa network applet. kaso di pa din ako makaconnect. parati nakalagay lang GSM disconnected. paano kaya ito? thanks.

gerry

---

### Post by antoniomiguel on 2010-06-07
Try these tweaks instead:

> **gerryb23 said:**
> 
4. In the mobile broadband tab I set the number (basic) as *99***1#
Set to *99#

> **gerryb23 said:**
> 
5. In APN I set it as http.globe.com.ph

Set to internet.globe.com.ph

> **gerryb23 said:**
> 
6. In the PPP settings, I clicked configure methods... and set it to CHAP
Tick all options instead


"GSM disconnected" warning means some of the requisites are not met. Hope this helps.

---

### Post by stormsurge on 2010-06-07
Smart Bro ka na lang. Smart Bro works right out of the box for 10.04. Yeah baby!!!!

---

### Post by aljoriz on 2010-06-07
> **gerryb23 said:**
> Sir,

6. In the PPP settings, I clicked configure methods... and set it to CHAP

Gerry

it should be **PAP not CHAP**
uncheck all methods except PAP

Hope this helps

---

### Post by blizzaga4 on 2010-06-08
anyone got any step by step ideas for my UBUNTU STUDIO 10.4 I've trying to figure this out for weeks and it won't even work. :(

---

### Post by gerryb23 on 2010-06-08
Kuya,

natry ko na po lahat ng sinasuggest ninyo kaso parang ayaw pa din nya magwork. i think storm is correct...magsmartbro na lang ako, huling tanong na lang po...compatible po kaya ang hardware ng huawei e1552 sa linux ubuntu. may nabasa po kasi ako na yung ibang modem ng globe ay di supported sa linux ubuntu. thanks po.

gerry

---

### Post by aljoriz on 2010-06-08
Huawei modems are very linux friendly baka di mo lang na install yung usb-modeswitch and usb-modeswitch-data.  

Dalawa modem ko puro Huawei E1553, Smartbro yan but na unlocked na.  Yung ZTE na itim ng smartbro yan ang masakit sa ulo but you still need usb-modemswitch for that.

---

### Post by vhinz on 2010-06-08
Just make sure to install usb-modeswitch and usb-modeswitch-data and set APN to internet.globe.com.ph (if you are prepaid subscriber) instead of http.globe.com.ph which is for postpaid.

Hope this helps.


> **killer_d76 said:**
> try installing usb-mode-switch.. sudo apt-get install usb-mode-switch or simply go to Applications>Ubuntu Software Center>and type usb-mode-switch>click install.. this should fix the issue! ;)

[click here for more info]("http://ubuntuforums.org/showthread.php?t=1481930")

> **aljoriz said:**
> Huawei modems are very linux friendly baka di mo lang na install yung usb-modeswitch and usb-modeswitch-data.  

Dalawa modem ko puro Huawei E1553, Smartbro yan but na unlocked na.  Yung ZTE na itim ng smartbro yan ang masakit sa ulo but you still need usb-modemswitch for that.

---

### Post by Ravskie on 2010-06-08
> **gerryb23 said:**
> Kuya,

natry ko na po lahat ng sinasuggest ninyo kaso parang ayaw pa din nya magwork. i think storm is correct...magsmartbro na lang ako, huling tanong na lang po...compatible po kaya ang hardware ng huawei e1552 sa linux ubuntu. may nabasa po kasi ako na yung ibang modem ng globe ay di supported sa linux ubuntu. thanks po.

gerry

Sir Huawei is very much compatible with Ubuntu because i use that one also with no hassle try to double check your settings and sundan mo yung sinabi nila sir aljoriz sir killer ....usb modeswitch pag install mo ( sudo apt-get install usb-modeswitch ) kasama na install ang usb-modeswitch data ... then make sure naka check lang yung PAP wala ng iba sa PPP settings IPv4 no need na galawin sa akin I'm using *99# .... the rest is sa provider mo na ...basta patience lang sa pag check ng config mo in that way you will learn also ...

---

### Post by gerryb23 on 2010-06-09
I will try again all the step-by-step procedure that you all mentioned...naginstall na po kasi ako ng usb-mode-switch, and followed every configuration you all suggested. talagang gsm disconnected pa din ako. tignan ko na lang ulit baka may naskip lang ako na gawin. ingat at salamat. :p

gerry

---

### Post by aljoriz on 2010-06-09
Make sure may load yung SIM kasi pag walang load disconnected talaga yan.

---

### Post by sencen on 2010-06-09
> **vhinz said:**
> Just make sure to install usb-modeswitch and usb-modeswitch-data and set APN to internet.globe.com.ph (if you are prepaid subscriber) instead of http.globe.com.ph which is for postpaid.

Hope this helps.

i have tried http.globe.com.ph and internet.globe.com.ph and even [www.globe.com.ph](www.globe.com.ph), wala naman silang problem pagnagko-connect ako. ano bang difference? ehehe.

---

### Post by aljoriz on 2010-06-09
yung http for PREPAID users daw at yung internet.globe.com.ph ay for post paid users.

---

### Post by vhinz on 2010-06-11
That's what I read some weeks back anyways but hindi talaga gumana ung default na internet.globe.com.ph sa akin kaya pinalitan ko ng http.globe.com.ph which worked.  Have been using it without problems.



> **aljoriz said:**
> yung http for PREPAID users daw at yung internet.globe.com.ph ay for post paid users.

---

### Post by majedaly on 2010-07-13
> **killer_d76 said:**
> try installing usb-mode-switch.. sudo apt-get install usb-mode-switch or simply go to Applications>Ubuntu Software Center>and type usb-mode-switch>click install.. this should fix the issue! ;)

[click here for more info]("http://ubuntuforums.org/showthread.php?t=1481930")

Thanks a million. The usb mode switch solved the problem in seconds and worked like charm on Lucid on Zain Kuwait;)
Just the code I used was a bit different
```
sudo apt-get install usb-modeswitch

```

---

### Post by raventech on 2010-07-19
to all of you guys who posted the methods and discussed them here, thank you so much.. i got it working by following your guides.. and the one specially from here: [http://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/](http://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/)

mine is Huawei E1552.. :popcorn:

---

### Post by Arnold Martin on 2010-07-21
wvdial if your using smartbro

---

### Post by Kyugetsuki on 2010-08-11
I am using peppermint OS Ice, I can't make it work for some reason after install.... but it could be detected immediately in the livecd... I need to know why...

---

### Post by micro_yoshimitsu on 2010-09-05
Anyone here knows how to install Globe Tattoo's dashboard on Ubuntu 10.04? Been searching over the internet and found nothing (or am I just not searching good enough? hehe..).
I can already use my E1552 modem for internet, I would also want it's call and text functionality in Ubuntu 10.04 that's why I like to have the dashboard.. Thanks!

Hope someone can help!

---

### Post by benlita on 2010-09-08
mines the same model too!

[http://ubuntuforums.org/showthread.php?t=1570405](http://ubuntuforums.org/showthread.php?t=1570405)

---

### Post by benlita on 2010-09-08
> **micro_yoshimitsu said:**
> Anyone here knows how to install Globe Tattoo's dashboard on Ubuntu 10.04? Been searching over the internet and found nothing (or am I just not searching good enough? hehe..).
I can already use my E1552 modem for internet, I would also want it's call and text functionality in Ubuntu 10.04 that's why I like to have the dashboard.. Thanks!

Hope someone can help!
sorry but the dashboard just doesnt work, try wammu instead for sms and network connections for the dialing :)

---

### Post by micro_yoshimitsu on 2010-09-08
> **benlita said:**
> sorry but the dashboard just doesnt work, try wammu instead for sms and network connections for the dialing :)

Ok.. will do that. Thanks!

---

### Post by benlita on 2010-09-09
just autosearch fr it using wammu via USB connection, it searches for a bit of a long time but it can retrieve msgs and contacts with ease (though i must say that the native dboard's faster)

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

### Post by fatboy07 on 2010-09-17
Hello! thanks you so much this topic help me a lot, now I can use my open lined broadband in my UBUNTU Lucid Lynx 10.04! great!

---

### Post by fatboy07 on 2010-09-19
> **benlita said:**
> just autosearch fr it using wammu via USB connection, it searches for a bit of a long time but it can retrieve msgs and contacts with ease (though i must say that the native dboard's faster)

great stuff! thanks!

---

### Post by lavezarez on 2010-10-29
*Tested successfully under the following system:*
Ubuntu 10.04 (lucid)
Kernel Linux 2.6.32-25-generic
Gnome 2.30.2
Huawei USB modem E1552 
Globe Tattoo PREPAID subscription

I didn't need to sudo apt-get install _***any***_ additional packages - such as usb-mode-switch or any backports stuff, btw.

***Instructions:***
1. Insert your Huawei USB.
2. From a terminal window, type **lsusb**:
```
snoopy@artemis:~$ **lsusb**
```hit Enter and you should see an output like this:
```
Bus 001 Device 011: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
snoopy@artemis:~$ 
```3. The output will show the vendor ID and the product ID (12d1 and 1001 in the above example - it might be different on your machine) .
4. Create a udev rule by typing 
```
snoopy@artemis:~$ **gksu gedit /etc/udev/rules.d/15-huawei-e620.rules**
```I named my file** 15-huawei-e620.rules** because that's what **lsusb** showed from no. 2
then copy+paste the code below:
```
SUBSYSTEM=="usb",SYSFS{idProduct}=="1001",SYSFS{idVendor}=="12d1",RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1001 --type option-zerocd"
```Just be sure to replace (if necessary) the correct values you got for your product and vendor IDs.
Save the file and type **exit** to close the terminal window.
5. Safely remove the USB drive then reinsert.
6. In my machine, the Gnome network manager didn't automatically detect my USB, so I had to create a new Mobile Broadband connection manually.  Just right-click on the network manager icon, choose **Edit Connections**, go to **Mobile Broadband**, and click **Add**.
7. Proceed with the prompts, choosing Huawei, and Globe (I chose ***plan unlisted***).
Here are the values that worked for me:
Number: *99#
APN: http.globe.com.ph
Under PPP settings, I chose PAP as the only authentication method.

---

### Post by sampaguita on 2011-02-01
> **gerryb23 said:**
> hello, im just a new user of ubuntu and experimenting on it. just installed ubuntu 10.04 last week. does anyone know how to install globe tattoo huawei e1552 usb dongle in ubuntu 10.04? will be glad to have a step by step instruction. thanks.

gerryb23

[B]Before this try first connect to other internet connection to install usb-modemswitch-data.
Note: You can't use globe tattoo unless you done this first.  
[/B] 
[LIST=1]
[*]Go to Application click Ubuntu Software Center search and install usb-modemswitch-data.
[*]Edit connection   tab mobile broadband Add connecttion.
[*]Enter Number: *99#
[*]Enter Username: globe
[*]Enter Password: globe
[*]Enter APN: http.globe.com.ph
[*]Tab PPP setting choose CHAP
[*]plug your globe tattoo modem choose globe connection
[*]   check your status
[*]   open your browser.
[/LIST]
I am using ubuntu 10.04 and globe tatoo works fine. I hope that I  help you. Clear.

---

### Post by djburn_c3 on 2011-04-23
hi sir gerryb23,

im having a problem also with my globe tattoo, i cannot install it with my ubuntu 10.04. Just like you im a new user of ubuntu and also experimenting on it.I've tried doing those posted in this forum and yet it didnt work.
Did you find solution about this matter?
thanks and looking forward to your reply.

djburn_c3

---

### Post by sampaguita on 2011-04-23
Try to install usb-modemswitch-data using under applications ubuntu software center via wired connection. After that do the following steps. I am globe prepaid subscriber. It works, otherwise if not try to test your usb modem to other computer using windows xp.

---

