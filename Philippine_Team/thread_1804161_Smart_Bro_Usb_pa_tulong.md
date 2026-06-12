---
title: "Smart Bro Usb pa tulong"
date: 2011-07-14
forum: Philippine Team
---

### Post by KaPePinG on 2011-07-14
Mga idol..bago ako dito sa forum.. and as simpre bagong install lang ng linux.. e gusto ko mag ka net.. paano ko install un smart bro.. plug it.. detect siya pero walang GUI interface.. sorry newbie lang sa linux.. sana matulungan nyo ako..

---

### Post by daison3 on 2011-07-14
[B]The GUI Interface:
[/B]well, Ubuntu Linux is a Unix system and not a win32 OS,therefore ubuntu can't run a **.exe** program, and if you want to run a .exe program use a Wine software, as what i've read to other sections, Through wine softwares can't detect a driver over the Ubuntu, thats why even you have GUI to your Ubuntu, that wont run..but there's a solution maybe if it will suit to your Broadband, because i'm using a Sun Broadband(e1550)
[B]

Suggested Way to run your Broadband:[/B]
If you have a Wired Connection and if its working then use this command:
-Run your Terminal, goto Applications>accesories>Terminal
```

[I]sudo apt-get update
sudo [/I]*apt-**get install linux-backports-modules-headers-lucid-**generic usb-modeswitch*

```after the installation, restart your PC. maybe this thing works to you because i'm using Sun Broadband..

**Other Way to run your Broadband:**(if you are using e1550 Modem)
```

*sudo gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules*

```then a gEdit will prompt-open to you, and paste this code

```

SUBSYSTEM=="usb",SYSFS{idProduct}=="1446",SYSFS{idVendor}=="12d1",RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

```then unplug and plug your **USB Broadband**, if this one works then post a reply so that other members know how they can run their USB Broadband, and if it is still not working..don't hesitate to post your comment.

**Other Way Solution:**
If you don't have a Wired Connection then find a person or a friend or to your family that has a Sun Broadband, Sun Broadband uses a e1550 Modem, they are stick to that modem maybe because its cheaper to HUAWEI Corp.
-Then use the method: **Other Way to run your Broadband:**(if you are using e1550 Modem)
-After you add that rules using a gEdit
-then use the above code: **Suggested Way to run your Broadband:**

---

### Post by tech-hero on 2011-07-14
AFAIK, Smart Bro USB broadband works out of box in UBUNTU. You just have to configure the Access point via network manager.

---

### Post by KaPePinG on 2011-07-14
mga bossing salamat..sorry d ko na update un thread ko.. aus ko na un connection..kapa kapa ko lang.. un pag text sa broadband nlng kulang.. aausin ko nlng to mamaya.. salamat idol thumbs up :popcorn:

---

### Post by Script Warlock on 2011-07-15
sa lucid nasubukan ko na umtsmon magtext using smartbro.

---

### Post by tech-hero on 2011-07-15
you could try wammu. Welcome to ubuntu.

---

### Post by KaPePinG on 2011-07-16
@sensei warlock nabasa ko na lahat ng thread sa forum na to.. confusing lang. newbie lang po kc.. willing matuto naman din.. 

panu po yan lucid..? nababasa ko din yan dito sa mga past thread. anu function ng lucid  at panu po install? di ko po ma solve un pang text e.. salamat po sorry kong matanung hehe

@tech-hero salamat po.. enjoy ko nga po tong ubuntu.. panu po yan wammu and anung function?

---

### Post by daison3 on 2011-07-16
"lucid" means the alias name of Ubuntu Version 10.04, the "natty" also means the 11.04 latest version of Ubuntu

---

### Post by tech-hero on 2011-07-17
install it via software center. It's a messaging function with GUI utilizing your broadband modem.

---

### Post by KaPePinG on 2011-07-17
salamat po sa tulong.. at sa info.. please wait 2 seconds for an uncompressed image, or press Ctrl+F5 for original quality page

---

### Post by arscariosus on 2011-07-17
> **tech-hero said:**
> you could try wammu. Welcome to ubuntu.

Thanks dito, I actually have the same question. Ngayon lang kasi nagka-USB 3G modem :P

---

### Post by tech-hero on 2011-07-17
NP. Welcome to the community. ;)

---

### Post by jvgeli on 2011-07-20
haha. Parang ako lang dati. cant get USB to work, now Im compiling my own kernels. Anyway, recent Ubuntu versions support most USB Modems out of the box, if not there is little tweaking to be done. as for the GUI dont count on getting something like the one you have with windows. Good luck and hope you stay.

---

### Post by Prescilla on 2011-08-03
@tech-hero Hi. I did install wammu but somehow it cannot detect or connect to my smartbro. I used the Phone configuration wizard and automatic search for a phone but it cannot find smartbro. Please help!!!

---

### Post by jepong on 2011-08-03
i don't like wammu... device detection is trial and error but once detected properly it works good.

have anyone tried gnome phone manager ([http://ubuntuforums.org/showthread.php?t=849874)?](http://ubuntuforums.org/showthread.php?t=849874)?)

---

### Post by tech-hero on 2011-08-03
> **Prescilla said:**
> @tech-hero Hi. I did install wammu but somehow it cannot detect or connect to my smartbro. I used the Phone configuration wizard and automatic search for a phone but it cannot find smartbro. Please help!!!
First of all sir, make your broadband modem work first. :) Tell us what happened, if you have successfully configured it to work for Internet browsing.

---

### Post by KaPePinG on 2011-08-08
tama nga un wammy trial n error... at first na detect nya.. pero kinabukasan d ma detect.. ala nmn akong binago sa setting o config.. tas nag ka ganun..

un gnome manager naman d madetect.. un smart bro usb.. panu ba to? patulong naman .. bka mali un settings ko.. pa2long panu config..

---

### Post by tech-hero on 2011-08-08
use lsusb. check mo muna boss kung nadedetect yung modem mo among listed devices. then kung nadedetect naman sya, malamang ok yun, settings lang siguro ang problema.

---

### Post by Fleshsym on 2011-10-06
Some tips on using the USB Mobile Broadband.

Background: I'm on Maverick, btw. I had used 3 Huawei USB mobile broadband sticks (2 sticks SUN and 1 from Globe) over the past few months. I used Wammu for text messaging and the native connection manager for Internet.

1. When you insert the USB Broadband stick... wait for it to appear in your "connection manager". Depending on the model/brand, the name that appears will be different. 

2. If your stick has internet access already, then you should be ready to go.

3. If you need to send an SMS to load the necessary internet plan then you must disconnect. DO NOT PULL OUT THE USB Broadband stick. Just use the connection manager to disconnect. (On Maverick, just click on the connections icon then click on the name of you broadband stick.)

4. You can WAMMU to send the SMS. Wammu will only detect and/or connect to you USB stick if it is disconnected in your "Connection Manager". For Wammu to recieve the reply you must actively retrieve. (Parang pag check ng mail sa POP3 kailangan pang mag send/recieve). Wala siyang auto recieve ng mga messages, kung meron man di ko nakita. Close mo na yung wammu.

5. Open the connections manager then click the name of your USB stick to connect.

Notes to remember:

1. Sa connections manager, dalawa ang identifier kung connected ang usb stick mo. Una naka BOLD yung font at pangalawa may naka lagay na "disconnect" sa ilalim nito. Kung naka disconnect isa lang siya, "regular" ang font ng name niya.

2. Matutong maghintay... I learned this the hard way. For some reason kahit mabilis yung laptop na ginamit ko may kabagalan ang paggamit ng Wammu.

I hope this helps!!!!!

---

### Post by tech-hero on 2011-10-06
> **Fleshsym said:**
> Some tips on using the USB Mobile Broadband.

Background: I'm on Maverick, btw. I had used 3 Huawei USB mobile broadband sticks (2 sticks SUN and 1 from Globe) over the past few months. I used Wammu for text messaging and the native connection manager for Internet.

1. When you insert the USB Broadband stick... wait for it to appear in your "connection manager". Depending on the model/brand, the name that appears will be different. 

2. If your stick has internet access already, then you should be ready to go.

3. If you need to send an SMS to load the necessary internet plan then you must disconnect. DO NOT PULL OUT THE USB Broadband stick. Just use the connection manager to disconnect. (On Maverick, just click on the connections icon then click on the name of you broadband stick.)

4. You can WAMMU to send the SMS. Wammu will only detect and/or connect to you USB stick if it is disconnected in your "Connection Manager". For Wammu to recieve the reply you must actively retrieve. (Parang pag check ng mail sa POP3 kailangan pang mag send/recieve). Wala siyang auto recieve ng mga messages, kung meron man di ko nakita. Close mo na yung wammu.

5. Open the connections manager then click the name of your USB stick to connect.

Notes to remember:

1. Sa connections manager, dalawa ang identifier kung connected ang usb stick mo. Una naka BOLD yung font at pangalawa may naka lagay na "disconnect" sa ilalim nito. Kung naka disconnect isa lang siya, "regular" ang font ng name niya.

2. Matutong maghintay... I learned this the hard way. For some reason kahit mabilis yung laptop na ginamit ko may kabagalan ang paggamit ng Wammu.

I hope this helps!!!!!
Thanks bro!

---

### Post by whchaz1027 on 2011-10-11
Pwede pa bang humirit dito mga sensei? same prob kasi eh. pagod nako sa kakaintindi ng mga ingles sa ibang site. Buti nlng may tagalog dito. 

Ubunto Natty gamit ko. nung unang insert ko sa SmartBro Stick, nadetect nman ang modem, nag appear sya sa NM applet tapos naka gawa ako ng mobile connection at succesful, naka-online ako. 

pero nung pag insert ko ulit ng stick, di na nya madetect. gumamit nako ng probing at usb_modeswitch pero di parin successful. siguro may mali sa ginawa ko pero sa tingin ko mga sensei ha, di na dapat i-tweak ang Natty, di gaya ng Maverick at Lucid kasi nung first attempt ko, succesful eh...

meron lang siguro akong dapat i-enable, yung parang "Enable this device" kaso di ko makita sa Natty eh. Tingin ko kasi hindi ko na remove properly ung modem kaya nagkaganun. 

RESCUE PLEASE....](*,)

---

### Post by whchaz1027 on 2011-10-11
Mga Sensei...di ako nakatulog kagabi sa kaiisip kung aanhin to PERO ngayon tinuloy ko ang pagresolve at SUCCESS mga sensei!

May kulang lang sa Natty, kelangan pang iinstall ang "libusb-dev" at nag usb_modeswitch ulit ako, cheneck ko yung "Connect Automatically" sa Mobile Connection ko (SmartBro) at i-nuncheck ko yung ibang connections (Wired) para pag login, ang SmartBro ang mag automatic connect, tapos reboot. 

Yun, hintay lang ng mejoooo sandali at nag reload ang Network Manager Applet sa panel at nag connect yung SmartBro Mobile Connection ko.

Preview: [http://img3.imageshack.us/img3/6495/smartbrostickonnattynar.png:guitar:]("http://img3.imageshack.us/img3/6495/smartbrostickonnattynar.png")

---

