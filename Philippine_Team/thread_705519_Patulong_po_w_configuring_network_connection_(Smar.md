---
title: "Patulong po w/ configuring network connection (SmartBro)"
date: 2008-02-23
forum: Philippine Team
---

### Post by youtin on 2008-02-23
Hello po! Super Newbie Linux and Ubuntu user here. Kakainstall ko pa lang kanina ng dual boot XP and Ubuntu  sa PC ko. Problem is, hindi po ako makaconnect sa net. I tried following the instructions dun sa kabilang Smartbro thread, pero hindi po pwede, kasi ang lumalabas lang, MODEM CONNECTION under** Network Settings**.

Hindi lumalabas yung **Wired connection** at ung isa pa (forgot what it is). Ibig sabihin ba nito hindi nadedetect ng Ubuntu yung hardware ko for internet connection? Tinignan ko sa Device Manager : **191 Gigabit Ethernet Adapter**. Vendor: [SiS]  If I'm not mistaken ito yung sa internet, right? Anong kailangan gawin para marecognize ng Ubuntu ang network connection? Hindi ako gumagamit ng router, direct sa canopy lang.

I hope you can help me out!

**[COLOR="Red"]EDIT: [/COLOR]**[COLOR="Blue"]New problem about connecting using new LAN card, mentioned at post below.[/COLOR] :!: :!: :!:

---

### Post by loell on 2008-02-23
lets try diagnose it.

sa command line / terminal, type mo.

```
ifconfig
```

at type mo din

```
dmesg | grep eth
```


then copy / paste mo ang output nang dalawang commands dito.

---

### Post by youtin on 2008-02-23
Thanks for the reply! :)

Ito po ang lumabas:

christine@christine-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

christine@christine-desktop:~$ dmesg | grep eth
christine@christine-desktop:~$

---

### Post by loell on 2008-02-23
tin, medyo malungkot  ang resulta :(

known issue na pala ito, na hindi magde-detect.

reference
> [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/181728](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/181728)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186666](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186666)


may solution naman eh, kaya nga lang.. 

either hintayin natin yung **Hardy heron** <-- the next ubuntu release, as it can detect the card.

**or**

compile tayo nang  kernel with the lan card fix

[http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6]("http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6")

heheh, you're new to this, so most likely you won't do this yet? 

another solution is, i know this is kinda lame, but how about purchasing a another cheap lan card? ;)

---

### Post by youtin on 2008-02-23
:( So sad...pero buti na lang at updated regularly ang Ubuntu so I don't have to wait _that_ long! I'm tempted to get another LAN card though. Mga magkano po yung ganun? Pero tutal 2 months na lang ang paghihintay...

Anyway, thanks sa link. Although Linux is mostly Greek to me, pag-aaralan ko ng mabuti yon para makagamit ng internet! Hehe..

Maraming salamat po talaga, **loell **! :KS

---

### Post by malleus on 2008-02-24
sir gamit ko surecom lancard, around 300 lang yata ngayon yun, ok naman walang problem sa internet connection both sa ubuntu and window$

---

### Post by youtin on 2008-02-24
Uy, OK, di naman ata ganon kamahal :) Thanks for the info, **malleus**!  This may be a stupid question, but can I have 2 lan cards installed? Sayang naman kasi yung SiS lan card ko.. onboard yata yun...

---

### Post by echo2knight on 2008-02-24
> **youtin said:**
> Uy, OK, di naman ata ganon kamahal :) Thanks for the info, **malleus**!  This may be a stupid question, but can I have 2 lan cards installed? Sayang naman kasi yung SiS lan card ko.. onboard yata yun...

Wala naman pong problema kahit 2 ang NICs ninyo. Just make sure that your SmartBro connection is properly connected to the new NIC and not that of SiS onboard NIC ninyo.

Hope this helps!!!

---

### Post by youtin on 2008-02-24
Nakabili na po ako ng 2nd LAN card, 350 petot :) Kaso yung Smart Bro e naka-configure sa SiS card! Although ngayon, dinedetect na ng Ubuntu yung LAN card ko (may option nang Wired Networks na lumitaw) pero di pa rin maka-connect. Kaya sinubukan ko muna sa XP. Kahit i-disable ko yung SiS sa Network Connections, ayaw pa rin pumunta ng internet connection sa new Edimax LAN card ko. Ang nakalagay lang, "Network cable unplugged". :( kakainstall ko lang ng driver. Ano po ang dapat gawin??

---

### Post by loell on 2008-02-24
nilagay mo na ba yung cat5 cable nang smartbro sa bagong lan card mo? 

**tulog muna ako ;)

---

### Post by youtin on 2008-02-24
:shock:....

Ni hindi ko man lang naisip yun! XD :lolflag:

Haha...ngayon ko lang napansin na meron na palang pangalawang saksaskan ng cable XD. Nyahaha... Thanks talaga! :D

Switching back to Ubuntu.. sana gumana din dun!

**EDIT:**

I'm now posting this using Ubuntu. Success at last!!! :D Maraming salamat po sa lahat, especially to Sir(?) Ma'am(?) **Loell **<3
I love Ubuntu already!!!!! :D

---

### Post by loell on 2008-02-24
:lolflag: bwahahah, kakatuwa naman.

---

### Post by paul_atreides on 2008-06-16
Hello guys saw this thread. Sadly hindi pa din supported ng ubuntu ang SiS191 ethernet adapter. Installed Hardy Heron 8.04 cannot detect adapter. Can anyone help me with this one?

---

### Post by ysNoi on 2008-06-17
I have Realtek RTL8139/810X Network Adapter here pero ok naman nung nag-install ako ng Hardy Heron....Smartbro user din ako....

Eto settings ko...

[IMG]http://i249.photobucket.com/albums/gg226/ysnoi_lacroxste/wirenetwork.png[/IMG]

@ paul_atreides, so ibig sabihin wala ka ring makita na Wired network connection Icon sa panel mo...? 

:popcorn:

---

### Post by ragadanga63 on 2008-06-17
How about buying another ethernet card?  You can get one for 150.00, second hand nga lang.  Tipidpc.com will be a good place to go.

---

### Post by king leoric on 2008-06-17
> **paul_atreides said:**
> Hello guys saw this thread. Sadly hindi pa din supported ng ubuntu ang SiS191 ethernet adapter. Installed Hardy Heron 8.04 cannot detect adapter. Can anyone help me with this one?

Kung ayaw mo naman mag baklas ng pc you, meron din network USB
mabibili sa CDR King :) Di ko nga lang sure how much pero marami ako nakikita :-) Hamo pag nakapasyal ako sa SM bukas post ko how much :lolflag:

Sino po naka pag try sa inyo ng USB LAN connection:confused:
supported naman siguro ng linux kasi USB naman eh :lolflag:

---

### Post by paul_atreides on 2008-06-18
Sadly buying another ethernet card is not really an option masyadong costly. I installed hardy heron sa 20 pc in our school dual-boot it with Windows. Lahat hindi recognized yung Sis191 nic.  Part kasi ng syllabus ko ay to introduce linux sa mga high school students. Excited pa naman ako na ituro sa kanila. I'm planning pa naman to stress that linux is better than windows. :lolflag: How can I make that point now? :confused: Natuwa pa naman ako sa kasi daling install compared sa earlier versions ng ubuntu. I'm going to give free cd copies pa naman sa mga students ko.

---

### Post by king leoric on 2008-06-18
> **paul_atreides said:**
> Sadly buying another ethernet card is not really an option masyadong costly. I installed hardy heron sa 20 pc in our school dual-boot it with Windows. Lahat hindi recognized yung Sis191 nic.  Part kasi ng syllabus ko ay to introduce linux sa mga high school students. Excited pa naman ako na ituro sa kanila. I'm planning pa naman to stress that linux is better than windows. :lolflag: How can I make that point now? :confused: Natuwa pa naman ako sa kasi daling install compared sa earlier versions ng ubuntu. I'm going to give free cd copies pa naman sa mga students ko.

:( too sad nga naman
I made some searching earlier and still a problem..
you can compile though 
[http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6) :)

---

### Post by loell on 2008-06-18
there too, seems to have an issue if you can successfully recompile the kernel driver, 

[http://ubuntuforums.org/showthread.php?t=801868&highlight=Sis191]("http://ubuntuforums.org/showthread.php?t=801868&highlight=Sis191")

but do compile one, atleast to be able to know first,  if this setup can work for you,

if it doesn't you can also try ndiswraper.

---

### Post by exkludge on 2008-06-20
> **paul_atreides said:**
> Sadly buying another ethernet card is not really an option masyadong costly. I installed hardy heron sa 20 pc in our school dual-boot it with Windows. Lahat hindi recognized yung Sis191 nic.  Part kasi ng syllabus ko ay to introduce linux sa mga high school students. Excited pa naman ako na ituro sa kanila. I'm planning pa naman to stress that linux is better than windows. :lolflag: How can I make that point now? :confused: Natuwa pa naman ako sa kasi daling install compared sa earlier versions ng ubuntu. I'm going to give free cd copies pa naman sa mga students ko.

why not use VirtualBox... make XP as your host OS.. and Hardy as guest OS... VirtualBox emulates a nic which is compatible to most OS including linux.

btw, you won't need to do a dual-boot at least at the moment if VirtualBox will work for your setup.

---

