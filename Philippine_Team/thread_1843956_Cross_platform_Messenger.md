---
title: "Cross platform Messenger"
date: 2011-09-14
forum: Philippine Team
---

### Post by ihazpower on 2011-09-14
Hi guys!
Im new to this community forum and a newbie user of Ubuntu 10.04
I just wanna ask if what could be the best free lan messenger that i can use with 2 operating systems, the windows and ubuntu..

And one more thing, i installed the playonlinux on my unit but i cant make this particular program run on the system. that program (online game) was on wine db..

Any help would be so much appreciated..thank you

---

### Post by kvarley on 2011-09-14
> I just wanna ask if what could be the best free lan messenger that i can use with 2 operating systems, the windows and ubuntu..

Install [Pidgin]("http://www.pidgin.im") from the Ubuntu Software Centre. Go to Accounts > Manage Accounts and add a Bonjour account. Bonjour is a LAN based chat protocol available for Windows/Linux/Mac which requires no server instance. This is probably going to be the option which suits your needs the best. On the Windows client you will have to install the Bonjour services seperately, the following explains why and where to get them from: [http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#CanIuseWindowsPidginforBonjour]("http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#CanIuseWindowsPidginforBonjour")

> And one more thing, i installed the playonlinux on my unit but i cant make this particular program run on the system. that program (online game) was on wine db..

What is the particular online game?

---

### Post by ihazpower on 2011-09-14
> **kvarley said:**
> Install [Pidgin]("http://www.pidgin.im") from the Ubuntu Software Centre. Go to Accounts > Manage Accounts and add a Bonjour account. Bonjour is a LAN based chat protocol available for Windows/Linux/Mac which requires no server instance. This is probably going to be the option which suits your needs the best.

What is the particular online game?

Oh..imma try that tomorrow in the office..
the game is tantra sir..ive been working on it for about 2 hrs but with no avail...

and also does Ubuntu 10.04 support switchable graphics adapters (Intel GFX adapter&ATI Radeon)?I have an MSI CX420 laptop and it works perfectly fine while i still haven't installed the dedicated video adapter (ATI Radeon). after updating the gfx adapter, the screen went black after booting up.. :(

---

### Post by kvarley on 2011-09-14
> the game is tantra sir..ive been working on it for about 2 hrs but with no avail...

If you read some of the entries on the wine appdb it gives some info on what settings to use in order to play the game. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6388&iTestingId=24449]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6388&iTestingId=24449")

> and also does Ubuntu 10.04 support switchable graphics adapters (Intel GFX adapter&ATI Radeon)?I have an MSI CX420 laptop and it works perfectly fine while i still haven't installed the dedicated video adapter (ATI Radeon). after updating the gfx adapter, the screen went black after booting up.. :(

You mean multiple video outputs and graphics cards? It sure does! How did you install the ATI driver? On the grub boot manager menu on boot go into recovery mode and choose the option which lets you reset x/xorg server. That will let you restore the config to the default and let you log back in to a graphical session.

After that is done try installing the graphics drivers by hitting Alt + F2 and in the Run Application dialog run:

> jockey-gtk

That's a GUI application which will let you install additional drivers, it's the easiest way to get graphics drivers installed on Ubuntu.

---

### Post by kiminaiseah on 2011-09-14
cross platform ba?

use meebo, browser base, 

miski ilang taon mo gamit, hindi nabubura ang history, meron ka ibedensya 

hahaha

---

### Post by ihazpower on 2011-09-14
pde kasi gumamit ng YM and other messengers pag meebo sir.. dapat ung nasa lan o vpn lng :) hehe

---

### Post by kiminaiseah on 2011-09-14
> **ihazpower said:**
> pde kasi gumamit ng YM and other messengers pag meebo sir.. dapat ung nasa lan o vpn lng :) hehe

messenger lang ba? 

baka naman pwde yan sa IRC hahaha gawa kayo private room 

hindi lang personal message, chat room pa

---

### Post by tech-hero on 2011-09-14
as far as I know, UBUNTU doesn't support Switching Graphics (from Discreet to Integrated and vice versa) yet.

You can only use one. either use the Integrated or the Discreet. You can't use the switch button for Switching GFX. That was 8mos ago. I don't know how did this thing progress so far. :)

---

### Post by tech-hero on 2011-09-14
Another thing, If you want to run something in Wine, make sure that you have at least twice the minimum requirement for that. It'll surely take more resources in linux to get the same performance you have when you run those programs for MS. So if those programs have native linux ports, or compatible linux (Open Source) software, prioritize them first. Make the use of Wine as the last resort :p

---

### Post by kiminaiseah on 2011-09-14
> **tech-hero said:**
> as far as I know, UBUNTU doesn't support Switching Graphics (from Discreet to Integrated and vice versa) yet.

You can only use one. either use the Integrated or the Discreet. You can't use the switch button for Switching GFX. That was 8mos ago. I don't know how did this thing progress so far. :)

kung hindi ako nag kakamali i already done this thing.. 

graphic switching, 

you have to manually change gdm config and restart the service. 

dun sa project ko dati na multiseat

---

### Post by ihazpower on 2011-09-15
> **kvarley said:**
> How did you install the ATI driver? 

I used the update manager to install the driver sir.. then after restarting the screen went black after booting..

---

### Post by ihazpower on 2011-09-15
> **tech-hero said:**
> as far as I know, UBUNTU doesn't support Switching Graphics (from Discreet to Integrated and vice versa) yet.

You can only use one. either use the Integrated or the Discreet. You can't use the switch button for Switching GFX. That was 8mos ago. I don't know how did this thing progress so far. :)

i googled the issue and i read that the integrated gfx ONLY can run the ubuntu(thats what they said)..but i still doubt that..
i preferably have to choose the discreet one kung pede lng naman magamit...



P.S. most of the terms na nsasabi d2 sa forum d q pa po malaman kng ano un.. bago lng po ako sa ubuntu hehe

---

### Post by tech-hero on 2011-09-15
I have no experience with that yet. But on my occasion, I have this intel processor which has an integrated graphics processor, and an ATI discreet GPU. I have no actual button to switch between though. Was able to install the discrete GFX just by installing third party drivers. I think, the only way to select between the two is through the BIOS. Try to look for the graphics processor option on your BIOS if you can enable the discreet one. Then install the driver.

---

### Post by ihazpower on 2011-09-15
thanks for helping me out guys..the ati radeon now is working.. :) hehe

next to figure out is: how to make this online game runnin on my system and the lan msgr.. :D
thanks a bunch sir!

---

### Post by tech-hero on 2011-09-15
good job!

---

### Post by ihazpower on 2011-09-16
> **tech-hero said:**
> good job!

salamat sir!

di q magagawa to kng walang 2mutulong d2..salamat talaga... 
hehe

---

### Post by tech-hero on 2011-09-16
> **ihazpower said:**
> salamat sir!

di q magagawa to kng walang 2mutulong d2..salamat talaga... 
hehe
eh pano ba talaga ginawa mo?

---

### Post by ihazpower on 2011-09-16
> **tech-hero said:**
> eh pano ba talaga ginawa mo?

sinunod q mga payo nyo :D

---

### Post by tech-hero on 2011-09-18
ano dun?

---

### Post by ihazpower on 2011-09-25
> **tech-hero said:**
> ano dun?

ung sabi nyo po na sa bios..meron 2 option dun..SGA & PA(not sure sa mga option, nkalimutan q na)..hehe

---

### Post by tech-hero on 2011-09-26
> **ihazpower said:**
> ung sabi nyo po na sa bios..meron 2 option dun..SGA & PA(not sure sa mga option, nkalimutan q na)..hehe
alright. gets ko na. :) nice to know na ok na yun sayo! kaso hindi sya ganun nakakasave ng battery since, yung discrete GPU ang gamit mo.

---

### Post by ihazpower on 2011-09-28
> **tech-hero said:**
> alright. gets ko na. :) nice to know na ok na yun sayo! kaso hindi sya ganun nakakasave ng battery since, yung discrete GPU ang gamit mo.
ok lng sir..nirekta q laptop q..knuha q battery para d masira..heavy user ako :D :popcorn:

---

### Post by tech-hero on 2011-09-28
Hindi ka ba naOOC dahil parang useless na yung GPU switch button mo?

---

### Post by ihazpower on 2011-09-28
oc sir?
d q alam jargon n yn..overclock?hehe

---

### Post by tech-hero on 2011-09-28
nao- Obsessive Compulsive kako. haha. yung hindi ka mapakali dahil walang purpose yung GPU switch button mo habang nasa linux ka.

---

### Post by JCyberinux on 2011-09-29
about pala sa OC, hindi pa ba talaga supported ng Ubuntu ang Overclocking??? :D pasensiya mga guys ha matagal akong nawala hehehe...

---

### Post by ihazpower on 2011-09-30
> **tech-hero said:**
> nao- Obsessive Compulsive kako. haha. yung hindi ka mapakali dahil walang purpose yung GPU switch button mo habang nasa linux ka.

aah..haha di naman sir ah..hahaha display lng un..yun nga laptop q e my bluetooth na button eh..wala lng BT dongle..haha :) dun ako na-oOC :D

---

### Post by tech-hero on 2011-10-02
> **ihazpower said:**
> aah..haha di naman sir ah..hahaha display lng un..yun nga laptop q e my bluetooth na button eh..wala lng BT dongle..haha :) dun ako na-oOC :D
haha nice nice! congrats sa bago mong OS. attend ka din ng release party :)

---

### Post by ihazpower on 2011-10-02
> **tech-hero said:**
> haha nice nice! congrats sa bago mong OS. attend ka din ng release party :)

san ko mkkta announcemnt nyan sir?

---

### Post by tech-hero on 2011-10-03
> **ihazpower said:**
> san ko mkkta announcemnt nyan sir?
hintay hintay ka lang dito sa forum, may magccreate din ng thread pag buo na ang plano. kaya lagi ka dapat active :)

---

### Post by ihazpower on 2011-10-04
> **tech-hero said:**
> hintay hintay ka lang dito sa forum, may magccreate din ng thread pag buo na ang plano. kaya lagi ka dapat active :)

ah ok sir! :D

---

### Post by ihazpower on 2011-10-13
guys up q lng ito regarding lan messenger..
di pa supported ng lucid ang linpopup? :(

---

### Post by Script Warlock on 2011-10-13
> **ihazpower said:**
> guys up q lng ito regarding lan messenger..
di pa supported ng lucid ang linpopup? :(

gamit ka na lang ng pidgin pwede yan as LAN messenger.

---

### Post by ihazpower on 2011-10-13
> **Script Warlock said:**
> gamit ka na lang ng pidgin pwede yan as LAN messenger.

hehe nhihihrapan ako magsetup sir ng jabber.. :) imba kasi mga employees samin eh..nakasanayan n kc nila ung winpopup na pagstartup ng system nila naka online na agad messenger..hehe

kinakapa q p lng sir pidgin..im currently trying ekiga

---

### Post by Zeta-K on 2011-10-13
Kung hindi ako nagkakamali, lahat kayo ay nagsasalita in ..na Filipino?Bakit?

---

### Post by ihazpower on 2011-10-14
> **Zeta-K said:**
> Kung hindi ako nagkakamali, lahat kayo ay nagsasalita in ..na Filipino?Bakit?

offtopic sir?bkt?

---

### Post by tech-hero on 2011-10-14
> **ihazpower said:**
> offtopic sir?bkt?
wala bang option ang pidgin na during startup magrun na sya? yung empathy kasi meron :)

---

### Post by zeroseven0183 on 2011-10-14
> **tech-hero said:**
> wala bang option ang pidgin na during startup magrun na sya? yung empathy kasi meron :)

Meron. Add mo yung Pidgin sa Startup Applications.

---

### Post by tech-hero on 2011-10-15
> **zeroseven0183 said:**
> Meron. Add mo yung Pidgin sa Startup Applications.
I mean, automatic sign in? possible kasi na magrun nga during start up pero baka naman hindi automatic sign in.

---

### Post by zeroseven0183 on 2011-10-16
Yes, automatic sign-in din. Anong protocol ba? Sa Yahoo at IRC, Ok.

---

