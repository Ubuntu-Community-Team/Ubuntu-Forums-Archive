---
title: "Enable Wireless po"
date: 2009-03-12
forum: Philippine Team
---

### Post by iLoveSade on 2009-03-12
Sorry if i have a new thread. The search is not showing me anything. please help naman po sa pagsetup ng wireless.

I've been in galeria yesterday in Burgerking and I was suppose to use a wifi connection there. I just realized when I opened my laptop that I am not using windows na nga pala. 

Please help po/. TY:(

---

### Post by jepong on 2009-03-12
i have been there before with a ubuntu 8.10 on msi wind. they have this very long wep key/passphrase sa burger king... ask mo lang sa attendant nila for that.

mas ok yung free wi-fi ng galleria at open for all. yun lang walang pwesto like benches man lang para comfy mag browse.

you can try sa robinsons pioneer minsan... medyo mabilis at wala amsyado tao.

:popcorn:

---

### Post by iLoveSade on 2009-03-12
Kuya eh pede niyo po ba ako mabigyan ng step by step on how to enable my wireless? Kasi yung option sa may icon ng network at the top eh di ko aman macheck. palagay ko eh drives ang wala. Dun sa mga tutorial na nakita ko eh sinunod ko na pero di pa rin. Anyway, Here's some info:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


Thank you! :D

---

### Post by Script Warlock on 2009-03-12
hmmmm halos parehas tayo ng rf chipset, baka hindi mo na enable ang rf..dba may pipindutin na fn+f_something? anu nga pala OS version gamit mo..i was using 8.10..

---

### Post by iLoveSade on 2009-03-12
Ubuntu Intrepid din po. Napagana niyo po yung sa inyo? can you teach me how please? :(

---

### Post by Script Warlock on 2009-03-12
yup auto naman lahat....wala akong ginalaw sa neo elan laptop...xcept lang sa lan kungmagkokonek ako sa inet shop ko..pero wireless, no sweat....works fine...

---

### Post by iLoveSade on 2009-03-12
Ok. I'll retry then. Other option is Globe Visibility :(

---

### Post by Script Warlock on 2009-03-12
anu nga pala output kung mag-dmesg ka

---

### Post by jepong on 2009-03-12
> **iLoveSade said:**
> Kuya eh pede niyo po ba ako mabigyan ng step by step on how to enable my wireless? Kasi yung option sa may icon ng network at the top eh di ko aman macheck. palagay ko eh drives ang wala. Dun sa mga tutorial na nakita ko eh sinunod ko na pero di pa rin. Anyway, Here's some info:


First cguro make sure na ON wifi mo. di ko alam paano mo gagawin. acer usually may sliding switch yan sa gilid eh.

tapos right click mo network-manager para uncheck and check mo yung enable wireless "something". or make sure pag-ON mo ng laptop mo eh activated na wifi.

then left click mo naman fromm time to time kung may nakukuha na hotpsot. then kung meron na ayun connect ka na.

i'm using kde na eh... i connect using knetworkmanager medyo magkaiba na paano connect sa hotspot.

---

### Post by kulahitatriboo on 2009-03-15
Yap baka off yong wifi...
Fearless ibex supports wifi and you don't need to configure anything except for the key you need to input it your self.

---

### Post by dodimar on 2009-03-15
> **iLoveSade said:**
> Kuya eh pede niyo po ba ako mabigyan ng step by step on how to enable my wireless? Kasi yung option sa may icon ng network at the top eh di ko aman macheck. palagay ko eh drives ang wala. Dun sa mga tutorial na nakita ko eh sinunod ko na pero di pa rin. Anyway, Here's some info:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS,
.........
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
**[COLOR="Red"][SIZE="4"]03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)[/SIZE][/COLOR]**
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


Thank you! :D

Detected naman ang wireless card mo... so meaning dapat gagana yan... baka naka disable lang.. check your laptop manual on how to enable the wireless...  I have the same wireless network card on a different laptop and it's working properly...

---

### Post by riclags on 2009-03-18
hi,

i have a quick question on wireless. when i try connecting to a home wireless network, and enter the passkey, the dialog box keeps displaying asking for the correct passkey/password all the time. after the first attempt, it converts the passkey/password i entered to random numbers which i think is caused by encryption.

question: WHY IS THIS HAPPENING?

i am sure that i entered the correct password/passkey because my friend (who's on xp) can connect. i have searched ubuntuforums and done what others have suggested to no avail.

hope someone here can help. thanks.

---

### Post by jeffimperial on 2009-03-18
> **riclags said:**
> hi,

i have a quick question on wireless. when i try connecting to a home wireless network, and enter the passkey, the dialog box keeps displaying asking for the correct passkey/password all the time. after the first attempt, it converts the passkey/password i entered to random numbers which i think is caused by encryption.

question: WHY IS THIS HAPPENING?

i am sure that i entered the correct password/passkey because my friend (who's on xp) can connect. i have searched ubuntuforums and done what others have suggested to no avail.

hope someone here can help. thanks.
Have you made *absolutely* sure that you're keying in the right password? You probably have so the next thing you might want to check is to open up your router settings page from your browser. Check out which kind of security protocol is in employ - WEP, WAP, WAP2, etc... and whether you're using the right encryption thingie - TKIP or whatnot. Check whether your wireless adapter's client software is "converting" that password the right way.

IMHO.

---

### Post by wersdaluv on 2009-03-18
> **riclags said:**
> hi,

i have a quick question on wireless. when i try connecting to a home wireless network, and enter the passkey, the dialog box keeps displaying asking for the correct passkey/password all the time. after the first attempt, it converts the passkey/password i entered to random numbers which i think is caused by encryption.

question: WHY IS THIS HAPPENING?

i am sure that i entered the correct password/passkey because my friend (who's on xp) can connect. i have searched ubuntuforums and done what others have suggested to no avail.

hope someone here can help. thanks.
Nangyayari yon pag mali ang password o masyadong mahina ang signal para makaconnect ka. Ganon talaga pag-mag-show password ka ng previously written password. Random numbers ang lumalabas for security purposes. 

Gawin mo na lang, show text mo na kaagad pag-i-type mo yung password for the first time para makita mo kung tama tina-type mo. Wag mo susubukan mag-connect ulit gamit network manager habang hindi mo pa sinasarado ulit o sinasagot yung dialog box na humihingi ng tamang password.

---

### Post by riclags on 2009-03-25
@ jeffimperial and wersdaluv

salamat sa mga input niyo. itry ko to when i get the chance. yung connection nga pala is WPA/WPA2 Personal. regarding sa TKIP at other config settings, d ko alam ano ibig sabihin nun. hehe. pde magpa explain? o saan ko makukuha yung dapat ilagay dun sa mga config na yun. sensya, bago lang ako sa ubuntu at wifi.

salamat.

---

### Post by daxumaming on 2009-03-25
> **riclags said:**
> i have a quick question on wireless. when i try connecting to a home wireless network, and enter the passkey, the dialog box keeps displaying asking for the correct passkey/password all the time. after the first attempt, it converts the passkey/password i entered to random numbers which i think is caused by encryption.

question: WHY IS THIS HAPPENING?

Happened to me recently after I upgrade my kernel. I fixed it by booting on another kernel, then rebooting back to the latest one.

---

### Post by riclags on 2009-04-09
hi guys.

i removed NM and installed WICD hoping na maka connect na ako sa wifi. so after ko mainstall ang WICD, punta ako sa merong wifi. unrestricted network so i thouhgt na makakaconnect na ako. after about a minute of "Obtaining IP address" na disconnect ako. no wifi.

nakakatawa is na-detect niya ang mga wireless networks pero ayaw mag connect -- kahit unrestriceted. im wondering kung drivers na ang problema nito o meron pa akong dapat gawin na config sa WICD.

any help appreciated. thanks.

---

### Post by Johnaray on 2009-04-09
> **iLoveSade said:**
> Ok. I'll retry then. Other option is Globe Visibility :(

Nakupo! Globe Visibility... not working on linux actually I also have that and ang naka install pa sa laptop ko now is SUSE linux.

Ito yung model ng aking Globe Visibility:
ZTE Model: MF626 HSDPA USB MODEM

Tumawag ako sa Globe at not supported daw. Only Window$ and Mac$ ang supported nila....grrrrr

About your main concern naman po I guess tama po advice ng mga Masters sa taas ^, malamang naka switch off lang wifi switch mo... that happen to me on my TOSHIBA SATELLITE L20 which is after I gave up I finally by accident switch the wifi switch at the front and SHAZAMMMM! Im on wifi!:guitar:

---

