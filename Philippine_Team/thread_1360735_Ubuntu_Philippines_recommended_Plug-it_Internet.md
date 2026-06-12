---
title: "Ubuntu Philippines recommended Plug-it Internet"
date: 2009-12-21
forum: Philippine Team
---

### Post by brgenst on 2009-12-21
Philippine Ubuntu users, can you recommend me a good Plug-it Internet?
One that works good in Ubuntu with the ability to select 3G/2G signal. 
What network and modem model? software support?

---

### Post by killer_d76 on 2009-12-21
I'm using Sun Cellular Wireless Broadband it comes with Huawei E160 HSDPA 3G USB modem and it is automatically recognized by Ubuntu 9.04 and 9.10 speed is fast too!.

---

### Post by Samhain13 on 2009-12-22
Using the same dongle as Killer. But it's for Globe Tattoo. Speed is fine in our area (Manggahan, Pasig).

[edit]

Sorry, I just checked. My dongle is a Huawei E1152. Auto-detected in Karmic. Also got it to work in Hardy.

---

### Post by pinoyskull on 2009-12-23
Huawei E220 also is a autodetected in Karmic, any network

---

### Post by brgenst on 2009-12-23
So it's recommended what ever network is used, as long as the model is Huwawei E***.
I think i'll go for Sun, since I heard the other networks always replace their modem models dozens of time.

---

### Post by kilosan on 2009-12-23
sun broadband usb kit is choice for CCS laptop machines that runs ubuntu and suse in the 2010 elections.

---

### Post by killer_d76 on 2009-12-23
brgents,

sun cellular signal and speed is really good here in Fairview area... and with regard to the type of USB modem that they issue, my wife's sister recently applied for a post-paid Sun wireless broadband and she got an E220 USB modem.

---

### Post by jaceleon on 2009-12-24
I would really recommend Sun Broadband on a Huawei E1550. It gives me decent net speeds, somehow a bit of a hassle to use on Ubuntu for the first time, but later on it is so easy! The speed are what matters to me. I am in Tondo (Merry Christmas nga pala!) on vacation, so I use my Sun, and it is so COOL in terms of speed, in comparison to SmartBRO and Globe Tattoo. And unlimited net use on 1 day for only P 50 is a nice feature for people like me who are so stingy :lol:. Kaya eto, nakakabuff pa ako ng youtube while downloading a doujinshi game worth 200MB.

---

### Post by Samhain13 on 2009-12-24
I tried PLDT WeRoam last night (some ZTE model). I wouldn't recommend it. The modem is auto-detected but I can't figure out how to make it play nice with either Network Manager or wvdial. So... stick with the Huawei modems. (Of course, if you can get WeRoam/ZTE to work, I'd be grateful if you can share how you did it. Hehehe!)

Merry Christmas!

---

### Post by kilosan on 2009-12-24
i think that is the purpose of this topic, so linux users wont be misguided into purchasing products in the future that wont work on linux.

we should have official recommendation for products. and i also recommend SUN.

---

### Post by Samhain13 on 2009-12-26
> **kilosan said:**
> i think that is the purpose of this topic, so linux users wont be misguided into purchasing products in the future that wont work on linux.

we should have official recommendation for products. and i also recommend SUN.

It's not a question of IF a product works. Its a question of HOW the products can be made to work. :)

---

### Post by dodimar on 2009-12-28
> **kilosan said:**
> i think that is the purpose of this topic, so linux users wont be misguided into purchasing products in the future that wont work on linux.

we should have official recommendation for products. and i also recommend SUN.

We can't recommend any specifics here... if your talking about the hardware, you could recommend and upon recommendation, also post how you can make it work for different providers. Because it isn't the same for all locations.

Recommended Plug-it internet:
first, check which one has a better offering on your area (by asking people who are already using Smart / Globe / Sun / PLDT etc. on your area).

second, check which one has a working modem in linux or if there's a way to make it work.

Don't let the telcos choose for you, you have the right to test if their product is working for you.

Edit:

BTW, Sun has a VERY unstable reception (going high to total lose of signal) here in my place...

---

### Post by aljoriz on 2009-12-28
In case of Smart bro prepaid, I heard that black usb dongle works on karmic though I have not personally tried it.  Can anyone vouch for it?

---

### Post by pepe machine on 2009-12-29
> **aljoriz said:**
> In case of Smart bro prepaid, I heard that black usb dongle works on karmic though I have not personally tried it.  Can anyone vouch for it?

yup!! thats what im using right now. :P

---

### Post by stormsurge on 2009-12-31
> **aljoriz said:**
> In case of Smart bro prepaid, I heard that black usb dongle works on karmic though I have not personally tried it.  Can anyone vouch for it?

Yup! I use Smart Bro. For me, I'll go for Smart. Its because they have a better coverage than the competitors. They have better signal in more areas.

---

### Post by brgenst on 2010-01-03
Do i need to upgrade the firmware of sun e1550?. The Sun firmware update in their website is dead.
But i like Sun's P50 1day unlimited. And it's easy to load it with other Suns cellphone.

---

### Post by aljoriz on 2010-01-04
Quick ? lang mga kapatid. 

I'm running on UNR 9.10, borrowed a co-workers usb dongle both globe and smart bro.. when making connections anong setting ba gamit? 

Internet connection or WAP?

Tried connecting using tattoo may signal kaso walang data transfer fail nyaahahahha

---

### Post by manilaph on 2010-01-11
The Smartbro (white) Huawei E156C works out of the box.

Just need to configure the APN to "smartbro" and remove passwords and only use PAP uncheck everything else.

The Globe Tattoo Huawei E1552 works out of the box.

Just need to configure the APN to "http.globe.com.ph" and remove passwords if any and only check on PAP.


I cannot seem to make my Sun Broadband Huawei E1550 to work.

In short,

I can recommend using the Huawei E156C of Smartbro and the Huawei E1552 of Globe Tattoo.

---

### Post by manilaph on 2010-01-11
> **aljoriz said:**
> Quick ? lang mga kapatid. 

I'm running on UNR 9.10, borrowed a co-workers usb dongle both globe and smart bro.. when making connections anong setting ba gamit? 

Internet connection or WAP?

Tried connecting using tattoo may signal kaso walang data transfer fail nyaahahahha

maybe you are using the wrong APN.

please check the APN and make sure it is "http.globe.com.ph" instead of "internet.globe.com.ph"

the default "internet.globe.com.ph" is for post-paid accounts.

---

### Post by manilaph on 2010-01-11
> **brgenst said:**
> Do i need to upgrade the firmware of sun e1550?. The Sun firmware update in their website is dead.
But i like Sun's P50 1day unlimited. And it's easy to load it with other Suns cellphone.

i haven't gotten my Sun's Huawei E1550 to work also. unlike the Huawei versions of Smartbro and Globe Tattoo which were easy to configure.

the strange thing though is that I was able to make Sun's Huawei to work on Sabayon 5.1 easily.

I will try again to get my Sun Broadband to work in Ubuntu 9.10.

---

### Post by Amidala03 on 2010-03-25
> **jaceleon said:**
> I would really recommend Sun Broadband on a Huawei E1550. It gives me decent net speeds, somehow a bit of a hassle to use on Ubuntu for the first time, but later on it is so easy! The speed are what matters to me. I am in Tondo (Merry Christmas nga pala!) on vacation, so I use my Sun, and it is so COOL in terms of speed, in comparison to SmartBRO and Globe Tattoo. And unlimited net use on 1 day for only P 50 is a nice feature for people like me who are so stingy :lol:. Kaya eto, nakakabuff pa ako ng youtube while downloading a doujinshi game worth 200MB.

     Hi badly need help. Just installed ubuntu 9.1 last nyt. My  Sun Broadband Huawei E1550 is working na but gsm lang ung signal. Hw can I change the signal 2 3G/hsdpa?

---

### Post by sasayins on 2010-03-25
I think you should call Sun for a tech support for this kind of issue. I heard they will setup some particular range for your signal. Or your area doesn't have any 3G/HSDPA signal.

---

### Post by jaceleon on 2010-03-25
By default (sa pagkakaalam ko) it is just fine. As in pagkainstall mo ng Ubuntu at pagkasaksak ng modem na SUN e it works? It should kasi trying it on live CD Sun is working.

BTW, lahat ng broadband providers (wired and wireless) me problem kasi nga lumindol sa Taiwan, thus our underwater lines somehow got damaged and is being repaired. expect slow speed from any broadband providers. Narinig ko lang po to from my boss.

PS, it doesn't have to be configured to work like that. As far as I know, it automatically do the switchings itself (like in Windows, it automatically switches to WCDMA and HSDPA).

---

### Post by vaustvest on 2010-03-25
> **Amidala03 said:**
> Hi badly need help. Just installed ubuntu 9.1 last nyt. My  Sun Broadband Huawei E1550 is working na but gsm lang ung signal. Hw can I change the signal 2 3G/hsdpa?

the only easy way is use a windows pc, set it to 3g pref instead of 3g only. you can visit internet cafe or a friend to fix it there.

---

### Post by sasayins on 2010-03-26
> **vaustvest said:**
> the only easy way is use a windows pc

-1 :-(

---

### Post by ben_10 on 2010-04-01
im using globe wireless broadband. its working good @ my place :o

---

### Post by itagomo on 2010-04-04
[HELP] [FONT=Trebuchet MS]
gumagamit ako ng UnliSurf with Smart(with my n6120c as the modem) but it can't download files with the Synaptic Manager.
But it can browse websites with Firefox.
[/FONT]

---

### Post by johnarcews on 2010-04-04
I'm also using Sun Broadband mabagal sya minsan pero sulit narin

---

### Post by sasayins on 2010-04-04
> **itagomo said:**
> [HELP] [FONT=Trebuchet MS]
gumagamit ako ng UnliSurf with Smart(with my n6120c as the modem) but it can't download files with the Synaptic Manager.
But it can browse websites with Firefox.
[/FONT]

Sa tingin ko, malaking files ang dina-download mo sa synaptic kaya nagta-timeout minsan ang session ng downloading or you need to update your sources sa synaptic.

---

### Post by itagomo on 2010-04-06
> **sasayins said:**
> Sa tingin ko, malaking files ang dina-download mo sa synaptic kaya nagta-timeout minsan ang session ng downloading or you need to update your sources sa synaptic.

Lahat ng dinodownlowd ku 'Failed to fetch'.
Di naman ata ganun kalaki un mga files, eh sa Firefox nkkdownlod naman ng big files(mga 30-40mb, big na un, hEHe).
Pag ina-update ko with Update Manager, ganun din.

---

### Post by sasayins on 2010-04-06
Sa tingin ko meron kang broken repository sa sources mo.

---

### Post by jepong on 2010-04-06
> **johnarcews said:**
> I'm also using Sun Broadband mabagal sya minsan pero sulit narin

i have a SBW prepaid... i notice parang nag idle cya.

---

### Post by nirvblakr on 2010-07-18
Hi!  I just installed UNR 10.04 in my Fujitsu netbook and I inserted my Suncellular Huwawei E1550.  What settings should I use in the edit connections (IPV4 settings,Mobile Broadband, PPP Settings)  so it would work?  I just inserted the USB dongle and the green light just keeps on blinking.  How long does it take for you to connect after inserting the dongle.  TIA

---

### Post by aljoriz on 2010-07-19
> **nirvblakr said:**
> Hi!  I just installed UNR 10.04 in my Fujitsu netbook and I inserted my Suncellular Huwawei E1550.  What settings should I use in the edit connections (IPV4 settings,Mobile Broadband, PPP Settings)  so it would work?  I just inserted the USB dongle and the green light just keeps on blinking.  How long does it take for you to connect after inserting the dongle.  TIA
Have you installed usb-modeswitch? If not go to Terminal and type:

sudo apt-get install usb-modeswitch
(enter you password)

---

### Post by nirvblakr on 2010-07-19
> **aljoriz said:**
> Have you installed usb-modeswitch? If not go to Terminal and type:

sudo usb-modeswithc
(enter you password)


I cannot install the usb-modeswitch through terminal.  It says command not found.  I installed it instead using synaptic.  It works like a charm.  Thanks so much! 

BTW, do you have any link for instructions to unlock the Huwawei E1550? TIA ;)

---

### Post by aljoriz on 2010-07-19
my bad the command was actually:

sudo apt-get install usb-modeswitch

My mistake!  as for the unlocking code try symbianize.com and search for their unlock code generator.

---

### Post by nirvblakr on 2010-07-20
> **aljoriz said:**
> my bad the command was actually:

sudo apt-get install usb-modeswitch

My mistake!  as for the unlocking code try symbianize.com and search for their unlock code generator.

OK! Thanks again! Just found this forum very helpful specially for us Pinoys using Ubuntu.

---

### Post by ben_10 on 2010-08-04
i'm new around, but im using globe broadband 3g not the wired. its performance quite fine.

---

