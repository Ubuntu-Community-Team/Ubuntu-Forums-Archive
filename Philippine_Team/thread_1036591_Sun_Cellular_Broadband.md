---
title: "Sun Cellular Broadband"
date: 2009-01-11
forum: Philippine Team
---

### Post by llemm on 2009-01-11
Mabuhay!!

Medyo matagal na rin ako gumagamit ng Ubuntu since feisty fawn, pero hindi ako geek dahil puro office.org at firefox lang gamit ko dito. Gusto ko lang malaman may paraan ba para mapagana tong Sun Cellular Broadband ko dito sa Ubuntu ko. Nag install ako ng ibex sa spare HDD ko, nadetect at nainstall naman ang driver problem naghahanap ng username at password. Eh sa XP ko plug and play ito no need for Pasword and Username. 

Any Guide or Instruction is deeply appreciated mga tol.

Huwawei e220 ang Modem na gamit nito. Thanks

llemm

---

### Post by pendletone on 2009-01-11
subukan mo tong link na to:

[http://ubuntuforums.org/showthread.php?t=1018922]("http://ubuntuforums.org/showthread.php?t=1018922")


[UPDATE]

here's a step-by-step guide for your perusal:

[Using Sun Broadband Wireless with Ubuntu Linux in 10 Easy Steps]("http://blog.kaliwanagan.ath.cx/index.php/2008/12/30/using-sun-broadband-wireless-with-ubuntu-linux-in-10-easy-steps/")

basically, just change your APN from 'minternet' to 'fbband'. :)

---

### Post by jepong on 2009-01-11
Share ko lang: I borrowed my boss' huawei for the weekend and it doesn't work. this is one of the first release of SUN kasi sister company namin sila so kami mga IT nag-test nito.

i later found out from a macbook user na in order to get this work on mac and linux eh sun needs to add something or upgrade the huawei. now eh ok naman at mas mabilis compared sa na try namin na globe visibility. cguro dahil konti lang nagamit sa ngayon.

tested ok on linux, mac, and windows.

---

### Post by llemm on 2009-01-11
Thanks bro sa reply. Pero paano kung sa 8.04? Nagtry ako ng isang driver na nakita ko rito pero ayaw. ung he220rc3.

I copied the terminal logs pero masyado mahaba para ipost kaya paste ko lang gedit at sinave sa rapidshare.

[http://rapidshare.com/files/182283874/Huawei_Install_attempt.html](http://rapidshare.com/files/182283874/Huawei_Install_attempt.html)
[http://rapidshare.com/files/182284553/Huawei_Install_attempt.doc.html](http://rapidshare.com/files/182284553/Huawei_Install_attempt.doc.html)

isang pang word at isang naka gedit. 
Thanks Bro. marami kasi akong naistallan ng 8.04 na yung mayari bumili ng sun cellular. para matulungan ko na rin.

llemm

---

### Post by jepong on 2009-01-11
basta sir may kailangan i-upgrade dun sa huawei. Kung may sun shop sa inyo eh ask nyo sila na linux pag-gagamitan nyo noong huawei. yung hausmate ko kasi eh naka-mac kaya nag tanong cya sa sun shop how gagana sa mac and sabi ng tao dun na uupgrade daw and pwede na sa mac and linux.

ask ko cya tonight ano pa ginawa nya ang post ko dito ulit.

---

### Post by llemm on 2009-01-12
Thanks Jepong, wait ko ung reply mo. Salamat talaga.

---

### Post by efrenefren on 2009-01-28
llemm, why don't you upgrade from 8.04 to 8.10. The modem will work even from the live cd. You just need to change the APN from minternet to fbband.

---

### Post by efrenefren on 2009-01-28
or if you cannot upgrade to 8.10, you can update your Network Manager applet and see if you can connect. What I have in mine is v0.7.0.

---

### Post by jepong on 2009-01-28
> **llemm said:**
> Thanks Jepong, wait ko ung reply mo. Salamat talaga.

Hi... sorry di na ako naka-reply. bsta nag-wwork na yung sun broadband sa ubuntu. gamit ko cya every night and mabilis compared sa globe visibility. mahina signal ng globe sa amin kaya intermitent.

---

### Post by efrenefren on 2009-02-08
The light on my modem is now green, how can you change it back to cyan?

I called sun broadband tech support for this and the agent told to change the network type from gprs to wcdma or hspda. but when i try to to edit the configuration there's i there is no way for me to change the network type.

Speed is very slow as of the moment. Be grateful to anyone who can help.

---

### Post by jepong on 2009-02-09
are you using **fbband** as the APN? that's the only configuration change I did.

---

### Post by llemm on 2009-02-09
> **efrenefren said:**
> llemm, why don't you upgrade from 8.04 to 8.10. The modem will work even from the live cd. You just need to change the APN from minternet to fbband.

I made it work na po. Pero nag upgrade talaga ako from 8.04 to 8.10. at napakadali lang talaga sa 8.10.

thanks to all of you guys.

---

### Post by Ryuichi on 2009-09-06
Pwede po humingi ng tulong? New ubuntu user po kasi ako, hindi po kc madetect ung sun broadband wireless prepaid modem ko... panu po un???

---

### Post by Jeboy on 2009-11-22
Hi, paano po configuration ng Huawei e1550 modem ng sun broadband for ubuntu 9.10 netbook remix os? Di kasi naddetect ung usb modem once plugged in.

Thanks

---

### Post by killer_d76 on 2009-11-22
try this link! [http://ubuntuforums.org/showthread.php?t=1307277]("http://ubuntuforums.org/showthread.php?t=1307277")

---

### Post by Jeboy on 2009-11-22
> **killer_d76 said:**
> try this link! [http://ubuntuforums.org/showthread.php?t=1307277](http://ubuntuforums.org/showthread.php?t=1307277)

In ubuntu 9.10 unr, [COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get install udev[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]extras [COLOR=Black]is not working[/COLOR]
[/COLOR][/COLOR]

---

### Post by jaceleon on 2009-12-21
Mga kuya, yung fbband na sinasabi niyo doesn't work for me talaga. Nakakaasar na po e. Bumili-bili pa ako ng Sun, e kahit anong gawin kong fix, format at kung ano-ano ay wala pa rin akong net via Sun E1550. Yung sa Sun Shop, suggest nila na switch daw ako Windows. Mga pang-asar sila!

Paano po to? Ginawa ko na fbband, upgrade ng firmware.... pero sh!t wala pa rin! Help po please.... dami ko na nabasa pati yung fix ni Kuya killer, pero wala pa rin. Me lilitaw na Setup para sa mobile broadband connection, tapos after configuring it for fbband, wala akong connection. Pag minternet, meron DAW connection, kahit wala naman akong net. Patulong na lang po.

---

### Post by kilosan on 2009-12-24
> **Jeboy said:**
> Hi, paano po configuration ng Huawei e1550 modem ng sun broadband for ubuntu 9.10 netbook remix os? Di kasi naddetect ung usb modem once plugged in.

Thanks

you have to install networkmanager.


> Mga kuya, yung fbband na sinasabi niyo doesn't work for me talaga. Nakakaasar na po e. Bumili-bili pa ako ng Sun, e kahit anong gawin kong fix, format at kung ano-ano ay wala pa rin akong net via Sun E1550. Yung sa Sun Shop, suggest nila na switch daw ako Windows. Mga pang-asar sila!

Paano po to? Ginawa ko na fbband, upgrade ng firmware.... pero sh!t wala pa rin! Help po please.... dami ko na nabasa pati yung fix ni Kuya killer, pero wala pa rin. Me lilitaw na Setup para sa mobile broadband connection, tapos after configuring it for fbband, wala akong connection. Pag minternet, meron DAW connection, kahit wala naman akong net. Patulong na lang po.

you may not be getting any 3G signal in your area, by default your modem is in 3G-only. you have to plug it first to a windows computer and set it to 3G-pref or 2G-pref.

---

### Post by jaceleon on 2009-12-24
Thanks sa advise. I manage to make the broadband work now. And it seems that the reason that the broadband doesn't work is because of the APN, fbband doesn't work with me, so I used the default APN which is minternet, then I used the cellphone para maactivate ko yung broadband. I am so thankful to you guys!

---

### Post by kilosan on 2009-12-29
> **jaceleon said:**
> Thanks sa advise. I manage to make the broadband work now. And it seems that the reason that the broadband doesn't work is because of the APN, fbband doesn't work with me, so I used the default APN which is minternet, then I used the cellphone para maactivate ko yung broadband. I am so thankful to you guys!

What exactly you did? I am helping my chatmate, she has the same problem, she can't connect if she used fbband but it connects if minternet is used but even if its connected there seems to be no internet in firefox.

---

### Post by brgenst on 2009-12-29
> **kilosan said:**
> What exactly you did? I am helping my chatmate, she has the same problem, she can't connect if she used fbband but it connects if minternet is used but even if its connected there seems to be no internet in firefox.n

Sa 9.10 karmic ganyan din sintomas na problema nang sa akin naka konek pero no internet, sa 9.04 jaunty kumo connect naman at may internet APN:minternet gamit ko, ayaw din APN:fbband.

Bumili ako ng Sun E1550 kaganina, una ko ginawa, sinak sak ko muna sa windows pc at nag load inquiry "BALANCE" at send to 2225 para ma activate, 1 day unlimited free, an kaso hanggang mamaya hating gabi 00:00 lang. Ineenjoy ko na nga yung 1 day free unlimited, sayang lang kasi hapon na ako nag simula hindi ko nasulit yung 1 day. Hindi kaya firmware issue ito? O dahil fresh intall palang yung 9.10 karmic ko at hindi pa na update?.

---

### Post by jaceleon on 2009-12-29
Just use minternet as your APN if you are are prepaid user. And also have some patience while pressing left click on network manager icon, then clicking Sun Cellular, kasi makikipagkulitan ka dyan ng mga around 15 times (sa kaso ko) to get a good area na makoconnect siya. Saka oras na connected ka na, e bihira ka ma disconnect.

For you kilosan, have you asked her to load it up? Load it using the ff. format

LOAD<space>code<space>5-digit code

then send mo na sa 2225. Use a cellphone in that. Then text Balance after a minute of sending that messege to 2225, then move that sim to that E1550 and plug it in the Ubuntu. Nalaman ko kasi na magiging connected ka pa rin on the network manager kahit wala kang load, wag mo nga lang asahan na may internet ka.

@brgenst

kaloko talaga yung balance message mo kapag kabibili mo lang. Don't worry about the one-day unli. If you activated your sim by 4:15 PM today, it will deactivate at 4:15 the next day. wala yan sa update sa Ubuntu.

---

### Post by brgenst on 2010-01-03
For Sun broadband wireless APN details here:
“fbband” for Plans 799, 649 and EasyBroadband;
“mbband” for Plan 1399; 
“minternet” for Prepaid

---

### Post by kilosan on 2010-01-03
still has same problem, its connected but no internet in karmic.

i tried it in jaunty and its working but it is not detected so you have to do this first.

e1550 in jaunty jackalope
```
sudo apt-get update && sudo apt-get install udev-extras
```

```
echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules
```

and you can firefox in jaunty. but not on karmic.

> then send mo na sa 2225. Use a cellphone in that. Then text Balance after a minute of sending that messege to 2225, then move that sim to that E1550 and plug it in the Ubuntu. Nalaman ko kasi na magiging connected ka pa rin on the network manager kahit wala kang load, wag mo nga lang asahan na may internet ka.

yes, its actually an activation issue, you have to balance inquiry so it will be activated at first time use. i also use wammu software to access the usb like a phone so i can balance in the laptop without removing the sim, it can make your sim faulty by repetitively removing and inserting it.

---

### Post by killer_d76 on 2010-01-09
here's the result of my Speedtest using my Sun USB Wireless broadband here in Lagro a few meters away from SM Fairview!

[IMG][[IMG]http://www.speedtest.net/result/677463675.png[/IMG]](http://www.speedtest.net)[/IMG]

---

### Post by igsen on 2010-01-12
Eto ang configuration ng computer ko. Gamit ko sun prepaid
Baka makatulong ito sa inyo.

---

### Post by manilaph on 2010-01-13
Sun Broadband question:

I understand that Smrtbro and Globe Tattoo are re-loadable using the pre-paid cards and the "value" will be stored (no fast expiration date).

Is this the same for Sun Broadband?

I just bought a Sun Broadband card and it says:
"Sun Broadband Php100 (12 hours) valid for 4 days".

What does this mean... what if I do not want to finish it in 4 days?

What if I use it on a Monday... then on a Friday? Will my friday surfing still have load?

Medyo malabo yata yon diba? Unlike Smartbro and Globe Tattoo... they don't tell you that it will expire in 4 days.

Please clarify.

---

### Post by jurusu on 2010-02-08
I was able to connect to internet using the network manager. I had no luck in installing the Sun software using Wine.

How do we send/receive text messages using this setup? The Sun Broadband software enables the user to perform cellphone functions aside from using the internet.

---

### Post by kilosan on 2010-02-08
> How do we send/receive text messages using this setup? The Sun Broadband software enables the user to perform cellphone functions aside from using the internet.

install the "wammu" software from ubuntu software center.
then keep pressing next
until you reach asking you the location of modem and put this:
**/dev/ttyUSB0**
if you get error, you need to find out your modem location, it can be in /dev/ttyUSB1 etc.

---

### Post by killer_d76 on 2010-02-09
@jurusu - even if you were able to install Sun Broadband software using Wine.. you may not able to use it,for some reason the connection get terminated.. i'll see if i can make it work... since I have no success in setting up wammu! :)

---

### Post by jurusu on 2010-02-11
Thanks kilosan and killer_d76.
@killer_76. Please update update us regarding your wammu experiment.

BTW, what sidebars are you using? Cool! How did you manage to install Sun software. I always have problems using Wine.

Now using karmic.

Sometimes it needs a few connection attempts to get the internet going.

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

### Post by blackheartnaz on 2010-12-21
hi guys, 

help naman po.
i have ubuntu 10.04 installed on my laptop.
been trying to make SUN broadband connection thru (Globe Broadband Stick - Huawei e1552). however, di ko mapagana. the broadband stick is open-lined already...

I tried installing

*linux-backports-modules-headers-lucid-generic*, 

restarted the laptop, but it still won't work.

anything i did not do right?

thanks!

---

### Post by tech-hero on 2011-01-17
> **blackheartnaz said:**
> hi guys, 
 
help naman po.
i have ubuntu 10.04 installed on my laptop.
been trying to make SUN broadband connection thru (Globe Broadband Stick - Huawei e1552). however, di ko mapagana. the broadband stick is open-lined already...
 
I tried installing
 
*linux-backports-modules-headers-lucid-generic*, 
 
restarted the laptop, but it still won't work.
 
anything i did not do right?
 
thanks!
 
Im not so sure of what happened to yours, but my SBW ZTE MF627 works out of the box for 10.04 LTS.

---

### Post by Ravskie on 2011-01-18
> **tech-hero said:**
> Im not so sure of what happened to yours, but my SBW ZTE MF627 works out of the box for 10.04 LTS.


Just asking usb-modeswitch install na ba ?

---

### Post by tech-hero on 2011-01-18
> **Ravskie said:**
> Just asking usb-modeswitch install na ba ?
 
Hindi na ako naginstall nun sir. i think, nakaconfigure na sya sa network manager. you just have to change some access point settings. pero aside from that, automatically detected as a wireless broadband modem sya.

---

### Post by Ravskie on 2011-01-19
> **tech-hero said:**
> Hindi na ako naginstall nun sir. i think, nakaconfigure na sya sa network manager. you just have to change some access point settings. pero aside from that, automatically detected as a wireless broadband modem sya.

pede po siguro in your case but there is other case that still need that especially yung kakainstall lang (maybe yung hindi pa naupdate yung kernel) there are 2 files na maconfigure if you install usb-modeswitch kasama yung usb-modeswitch_data.  :D

---

### Post by lozada1991 on 2011-01-29
Just a new linux user here.
i just wanna ask if huawie e153 is available for moonOS 4 neak.
And is there any difference in establishing the connection.

thanks

---

