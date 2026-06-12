---
title: "wifi support for neo laptop. neet help!"
date: 2008-07-22
forum: Philippine Team
---

### Post by adredz on 2008-07-22
guys pano i enable ang wifi support ng neo laptop m72s ang model? wla kasi documentation sa website ng neo eh help naman..

---

### Post by VirtualEdgar on 2008-09-20
> **adredz said:**
> guys pano i enable ang wifi support ng neo laptop m72s ang model? wla kasi documentation sa website ng neo eh help naman..

Hi Bro adredz! I had the same problem two weeks ago with my Neo M3S laptop. Then I found a fix from this site...

[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312]("http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312")

Worked like a charm! Now I can use my wifi. Most likely you are also using Broadcomm adapter.

Hope this helps and good luck!

---

### Post by superpink99 on 2008-11-11
hello guys i have a neo laptop, its empriva i think, anyway i was also wondering if you could help me activate my wifi for ubuntu, i don't know what type of wifi my laptop uses but, is there a way i can solve this?

---

### Post by killer_d76 on 2008-11-11
go to System> Administration> Hardware Drivers.. tapos activate mo lang yung wireless driver then restart mo laptop mo!.. and thats it!.

---

### Post by adredz on 2008-11-11
aw nabuhay ang thread..:) i posted this to help out my friend, but in the end i opted to install XP on his lappy instead..noob pa kc u eh..

---

### Post by riclags on 2008-11-30
hi,

nice to know na merong pinoy flavor ang ubuntu forums. anyway, i just did a fresh install of ubuntu 8.10 on a neo empriva 540rvp laptop. everything seems to work fine...and it seemed to have enabled the wireless card.

so i turn it on using the network manager in the system tray(?) and sure enough, it found the wireless network in my friend's house. this was amazing because there was very minimal setup to be done.

excited as i was, there seemed to be a problem. i tried connecting to the wireless network and when i entered the password, a popup window displayed asking me to re-enter the password. i thought that i did it incorrectly the 1st time pero pag try ko ulit, still the same. tapos i noticed na ang password box has values changed to which i think is in hex.

i tried it about a dozen times more, making sure na correct ung password na ginagamit ko but still ayaw pa rin mag connect. labas pa rin ung popup window na please enter authentication key or password...

so i tried the password on my gf's laptop (running windows xp) and it connected to the wireless network flawlessly on the first attempt while in ubuntu, it kept asking me to re-enter the password.

please help.

not sure if this is relevant:
1) ubuntu seems to see the wireless network as WPA/WPA2 personal and i don't understand what it means.
2) my friend's wireless network setup is a PLDT DSL line which then connects to a linksys wireless router.

---

### Post by Script Warlock on 2008-11-30
i have a neo elan laptop bagong bili na 8.10 ang OS pero ang chipset na gamit is intel and the wifi works well...

---

### Post by riclags on 2008-12-01
> **boyet said:**
> i have a neo elan laptop bagong bili na 8.10 ang OS pero ang chipset na gamit is intel and the wifi works well...

hehe...maayo nga ni-work ni para sa imong laptop. maayong adlaw, fellow bisdak. naa pud ko sa cebu karon pero taga cdo ko. i see nga c adredz, taga-cdo. la lang...

:lolflag:

anyway, i keep wondering why ubuntu cannot connect to the wireless network when its detected and the password i supply is correct. i know i shouldn't compare but this is where windows wins for me. i am not a genius and would be quite biased since i have used windows more that i have ubuntu (linux in general), but it seems connecting to the internet is easier in windows.

this is not the first time i have used ubuntu (first time on a laptop, though), i even still have the free shippit cds of version 5.04 but, as i said, i find it hard to connect to the internet. back then, i had an old desktop which i installed ubuntu on. it was great since the speed was great and the GUI/desktop was decent given that it was a P2 desktop pc. but when i wanted to connect to the internet using the onboard lan card (which i bought separately), it was hell. i had to keep going online back and forth, asking around how to make it work. in the end, i gave up.

but i don't want to give up now, since i noticed that there have been dramatic improvements (especially with the hardware recognition)...but again, this issue with the wifi is becoming a bit of a problem.

---

### Post by Script Warlock on 2008-12-01
mao ba, bakasyon ka karon? unsa man mamasko? hehehhe

pero mas maayo kung ang 8.10 imong gamiton kay almost all hardware supported na..og daghan pod og workaround kung inkaso dili mogana out of the box

---

### Post by loell on 2008-12-01
> **riclags said:**
> i keep wondering why ubuntu cannot connect to the wireless network when its detected and the password i supply is correct. i know i shouldn't compare but this is where windows wins for me.

try deleting the wireless connection, and then input the password again.

if this doesn't solve the issue , you can also use ** wicd** a network manager alternative.

---

### Post by riclags on 2008-12-01
@boyet
nope, nag work ko diri cebu. uli ko cdo semana sa pasko

@loell
> try deleting the wireless connection, and then input the password again.

how do i delete the wireless connection? in NM?

i seem to have found this [link]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") in my mission to solve the issue but it isn't updated with the intrepid version of ubuntu. i'm not sure if it will work (re password nagging)...i'm not even sure i understand it. :???:

---

### Post by loell on 2008-12-01
> **riclags said:**
> @
how do i delete the wireless connection? in NM?

i seem to have found this [link]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") in my mission to solve the issue but it isn't updated with the intrepid version of ubuntu. i'm not sure if it will work (re password nagging)...i'm not even sure i understand it. :???:

yep,  right click NM -->  Edit Connections --> wireless TAB --> select Items on the list then delete them. ;)

redo the setup ( crosses finger) then hope it will work .:)

oh.. and the link you are reffering, won't be necessary since it was made when NM wasn't yet included in ubuntu by default.

---

### Post by CompFreak on 2009-02-02
need help with Neo eXplore X2, thanks

---

### Post by elav on 2009-06-05
Bis
Problema gyud ning Wifi sa Neo laptops (kun realtek ang chipset ini), dili mag-work sa linux. Nasulayan na nako ni, laptops ug mga desktop nga may realtek pci wifi cards. Ang pci wifi adapters sa CDRKing realtek usab ang chipset ug dili nako mapagana sa ubuntu (hardy, ibex, jaunty). May linux drivers man ang ubuntu para sa realtek apan pang 8180 lang (di ko sigurado) ang usual nga chipset nga magkaproblema mao ang 8185.
Nasulayan. 
...gamit ang linux drivers (CDRKing) -no go.
...ndiswrap -wala gihapon.

Basin may nakasulay na nga mapagana ning mga mananapa, paambita ko.:D

---

### Post by pogztimz on 2009-06-05
> **riclags said:**
> hehe...maayo nga ni-work ni para sa imong laptop. maayong adlaw, fellow bisdak. naa pud ko sa cebu karon pero taga cdo ko. i see nga c adredz, taga-cdo. la lang...

:lolflag:

anyway, i keep wondering why ubuntu cannot connect to the wireless network when its detected and the password i supply is correct. i know i shouldn't compare but this is where windows wins for me. i am not a genius and would be quite biased since i have used windows more that i have ubuntu (linux in general), but it seems connecting to the internet is easier in windows.

this is not the first time i have used ubuntu (first time on a laptop, though), i even still have the free shippit cds of version 5.04 but, as i said, i find it hard to connect to the internet. back then, i had an old desktop which i installed ubuntu on. it was great since the speed was great and the GUI/desktop was decent given that it was a P2 desktop pc. but when i wanted to connect to the internet using the onboard lan card (which i bought separately), it was hell. i had to keep going online back and forth, asking around how to make it work. in the end, i gave up.

but i don't want to give up now, since i noticed that there have been dramatic improvements (especially with the hardware recognition)...but again, this issue with the wifi is becoming a bit of a problem.

if the network is detected then we know for sure that you're wireless device is working fine. i concur to sir loell's suggestion that you install wicd as an alternative to Ubuntu's Network Manager since wicd is more stable than the default network manager (correct me if i'm wrong). if things still persists and you cant connect to a wireless network, then probably the  key you supplied is wrong or maybe the router on which you are trying to connect is not enabled to accept DHCP clients. if this the case then u should manually set the ip address, netmask and gateway on your computer.

cheers.. ;)

```
sudo apt-get install wiCD
```

---

