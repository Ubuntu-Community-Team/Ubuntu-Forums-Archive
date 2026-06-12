---
title: "Problems in ubuntu hardy"
date: 2008-06-14
forum: Philippine Team
---

### Post by ache109 on 2008-06-14
elow pu!!!

I'm a newbie in ubuntu... almost a week pa lng akong gumagamit nito, nalaman ko sya sa wikipedia... kaya naengganyo akong i dload at ipalit sa old n' crappy n winxp.. pero dun sa week na un, mejo merong mga problems and compatibility akong naeencounter e2 isa-isahin ko na..

Problem #1:
I'm playing games na kelangan ng support ng direct x... pede ko bng i-install un via wine at gagana na sya???

Problem #2:

I have a shutdown problem.(nagcmula nung ininstall ko ung wine) me lumalabas sa screen na sinasabing (scanning the boot scripts..etc) <attached pic file> tapos mamamatay nlng ung pc.. tapos when I press the shotdown button nag hahung up ung comp.. anung problema kaya nun?

Problem #3

Nabasa ko sa mga forums nyo dyan na hindi supported ng ubuntu ang YM... so i'd tried ung pidgin.. ok nanan sya pero nakakadetect ba sya ng web cam? kasi i'm planning to buy a web cam for my frends....

Problem 4#
Meron bang parang 'program files' folder ang ubuntu? hindi ko kasi mhanap ung root folder ng mga installed na apps sa ubuntu?

Problem 5:
Meron akong printer na HP Deskjet 3920 kaya lng nasira kaya hindi ko pa natetest sa ubuntu.. can I install it's drivers via wine at madedetect na sya ng system?

Problem 6:
Meron bang application ang ubuntu na pang convert ng video via firewire cable? kasi gamit ko dati eh pinnacle studio 8 kya lng malaki ung file kaya mabahal syang mag load...

Problem 7
Sa internet ako nakikinig ng radio para hindi mgastos sa kuryente. Kaya lng kailangan ng windows media player para gumana sya.. meron bang maiinstall na plugin para dun for firefox?

Un lang naman and sana maresolba nyo ang mga problems na yan kasi talagang nagdadlawang isip ako kung mag dual boot ako.. xempre ayoko nag bumalik sa

---

### Post by loell on 2008-06-14
i'm seeing that the real problem is #2 

if you are suspecting that wine is the culprit on your shutdown problem, can you uninstall then test if the shutdown problem goes away?

in the terminal, uninstall **wine**

```
sudo apt-get remove wine
```

then try to shutdown.

---

### Post by jsgotangco on 2008-06-14
from what I can understand from the very low quality of the pics, you have something in rc.local that intervenes with network manager on shutdown

---

### Post by dodimar on 2008-06-14
HP printer... di mo na kailangan mag install ng driver... most probably madedetect na siya ng Ubuntu at pwede mo na siya gamitin. Very compatible ang HP sa Linux.

Pidgin, i don't think pwede mong gamitan ng webcam, try kopete, may webcam support yan.

Windows Media Player addon for firefox is here [(click here)]("https://addons.mozilla.org/en-US/firefox/browse/type:7")

And yeah, those are not problems but more of inquiries..

For wine inquiries, you can check [http://winehq.org/](http://winehq.org/)



Cheers and enjoy your Ubuntu...

:guitar:

---

### Post by SHENGTON on 2008-06-14
Problem #1: You may want to check the game that you want to install [HERE](http://appdb.winehq.org/browse_by_rating.php) if it will work.

Problem #2: Same with loell suggested that you have to uninstall the "Wine".

Problem #3: I have a scanner here, I've tried installing the driver of it but no luck. It because my the driver of my scanner isn't supported by "Wine". You can purchase a webcam but make sure that it has a Linux driver on it. I think all drivers are not supported by Wine. Wine will only support if what's on their database.

Problem #4: You may want to check my existing topic --> [HERE]("http://ubuntuforums.org/showthread.php?t=795237&highlight=Program+Files+Ubuntu")

Problem #5: Just like problem #3.

Problem #6: As far as I know, Pinnacle is a video editing. Here are two applications which are equivalent to Pinnacle, Jashaka and Avidemux. Wala akong alam na video converter for Linux. All can I say is, download a Windows Platform software and install it since you have a Wine program.

Problem #7: You can use Rythmbox Music Player.

---

### Post by ache109 on 2008-06-14
> **jsgotangco said:**
> from what I can understand from the very low quality of the pics, you have something in rc.local that intervenes with network manager on shutdown

wla atang kinalaman ung wine dun something with the /etc/rc.local... he runs local boot scripts everytime I shut down... can you resolve this? thanks!!

---

### Post by ache109 on 2008-06-14
ung sa problem # 1 gumana naman ung game... kaya lang ang bagal ng interface nya because it's a 3d game,so i think that direct x will be the solution to the problem.. pero nd ata supported ng ubuntu un eh, may alam ba kayong substitute for the direct x?

dun sa shutdown check my other post...

ok na ung kopete.. itatry ko nlng ung webcam, (cguro bago ako bumili i'll ask you if supported ba ung webcam.

nahanap ko narin ung root folder ng nga installed apps ko

printer drivers??? no problem na pala eh,,

for the video converting??? mali pala ang kailangan ko pang video capture via firewire (sorry...):

and dun sa WMA plugin.... hindi supported ng wma ang linux so i'll try rythmbox..

so 4 out of 7 na kakulangan ay solved na!!!
if hindi ako nakahanap ng pang video capture.. cguro i'll be dual booting with winxp

---

### Post by loell on 2008-06-14
try to find out the content of /etc/rc.local 

```
cat /etc/rc.local
```


[Kino video editor , handles firewire]("apt:kino")

---

### Post by ache109 on 2008-06-15
> **loell said:**
> try to find out the content of /etc/rc.local 

```
cat /etc/rc.local
```


[Kino video editor , handles firewire]("apt:kino")

Kuya ganto lumabas when I entered this code:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing

Hindi ko sya magets?

---

### Post by ache109 on 2008-06-15
Saka me alam ba kayong image file ng ubuntu stickers na pinamimigay kapag nagpaship ka ng cd... at meron bang stickers ang ubuntu na katulad ung sa windows na me nakasulat "powered by winxp" na usually nakikita katabi ng intel logo sa mga laptops at branded computers (ung pre-installed ang winxp)

---

### Post by loell on 2008-06-15
> **ache109 said:**
> 
Hindi ko sya magets?

ibig daw sabihin walang laman yung rc.local mo  .. :)


so maaring hindi ito ang prolema..

---

### Post by Samhain13 on 2008-06-15
Problem #1: malabo. Kung gusto mo talagang maglaro, sa Windows na lang.

Problem #2: ...

Problem #3: install Kopete, may webcam support siya pang-Yahoo.

Problem #4: ang root directory ay "/". Kung saan naka-install ang mga program, depende kung sa program. Pero sa pagkakaintindi ko, kadalasan sa "/usr" siya inilalagay. Pero yung user configuration niya na sa "/home/userNameMo/.pangalanNgProgram"

Problem #5: sorry, no idea.

Problem #6: firewire? No idea also. Pero madami kang magagamit na media transcoders sa Ubuntu (kung na sa hard drive mo na yung movie files). Ang irerekomenda ko ay ffmpeg, pero command line tool siya. Depende sa format, puwede ka din mag-transcode gamit ang VLC (yung media player) pero hindi siya kasing bilis ng mga command line tools.

Problem #7: depende sa radio station. Subukan mo sa Rhythm Box: Music > New Internet Radio Station. May lalabas dun na dialogue box, hihingin niya yung URI ng stream na gusto mong kunin. Sa pagkakaalala ko, yun din yung inilalagay na address sa WMP.

Ayun! Sana nakatulong. :)

---

### Post by ache109 on 2008-06-15
Meron bang nakakaalam ng picture package? ayaw kasi mag install nun sa wine.. tanung ko lng kung me alternative para dun...

---

### Post by Samhain13 on 2008-06-16
Picture package?

---

