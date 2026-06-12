---
title: "1st major encouter with LINUX and Ubuntu"
date: 2009-05-06
forum: Philippine Team
---

### Post by joshua.solidum on 2009-05-06
1st encounter with LINUX and Ubuntu

  Way back mid 2007 when I visited a co- worker and aided him with for a desktop 

assembly project(he was then on a way the build his own desktop with cheaper parts as 

possible).
He consulted me for parts and some network adapters this and that.He asked me if 

theres a network adapter that supports roaming mode,cheap and with a 3 to 5 years 

warranty.I gave him the list from that I know(linksys and netgear).But really didnt 

bother why he did ask for roaming capabilities or such.The next day I came back to 

check him quite surprised me,well he already got internet access,but he was not 

subscribe to any ISP nor even on any dial up,I found out he was  doing a piggy back 

on his next door neighbors wifi(and he is still doing it till now without the real 

owner knowing a single thing!!),I then wondered how he did it since it was secured 

with a WPA encryption and way back then the only program I knew to crack such wifi 

encryption is the WEP CRACKER(a bootable program) but it will not work if you have 

WPA as a encryption,he then showed me the trick,the computer is actually equip with 

air hack and air snorrt he then showed me how it works.I said cool well gave me the 

program and I will install it on my computer,he said it wont work with windows.Way 

back he aleady got Suse installed up and running.He gave me the CD for the LINUX Suse 

along with the magazine called Linux Format along also with another linux live cd
Ubuntu feisty fawn.But realy didnt bother about it,I dont want to mess with a system 

that Im not familiar or installed that OS and Im comfortable with the WEPcracker that 

I got.But then I read the walkthrus inside the mag and even watched the videos about 

troubleshooting and installation process,quite easy its like installing windows.


  That didnt catch my interest thou but when my cousin purchased a second hand 

desktop running in the older pentium model,barely its a barebook computer without OS
he than asked me if I do got a cd for windows xp or alike or if we can purchase an 

OEM XP for lower cost or even get the pirated version,I said none all I got is a 

linux OS given to me,We tried installing Suse and it works,he is contented about 

it,since he just want the basic open office and paper works stuff.(Thats My first 

success with LINUX!!).
But we didnt bother to join any LUG's(linux user group) since we have some ideas 

already where to get help and what to do if in case the OS would crash(luckily it 

didnt )my cousin then was used to joining forunms at [www.LinuxHelp.net](www.LinuxHelp.net) and we really 

dont have problems with the computer so we didnt bother at all!,,But we managed to 

get an account from sourceforge.net,,for some interesting software of course.)





Another shot on Linux came to me when I was looking for a network resource book for 

Cisco in a local book shop,when I stubbled to a book entitled  LINUX BIBLE 2007 

authored by Christopher Negus, its a great buy for only 350 pesos, a 900 plus page 

book that gives almost complete guides and everything about Linux from installation 

to administering ,from programing to gaming,,plus it comes with 2 disc with 16 

different LINUX distribution..(BINGO!!!!) I didnt wasted any time and did purchased 

the book
and when I got home ,immediately I tried to run the disc
it comes with major linux distribution including 

knoppix,slackware,fedora.ubuntu.suse,
redhat,damn small linux,linspire,gentoo,and some other distro inluding the famous 

security tool BACKTRACK(which already comes with airhack and air sniff) and it also 

comes with all of the links to download drivers and resources needed.


A year and a half past since then.But Ubuntu Hardy Heron is some how  quite a 

challenged,I got the disc as a freebe from and australian mag called PC USER 

australian..the disc also comes with a vmware player and a opensource vmware machine 

shop,its meant for installing Ubuntu as a virtual machine,wow so I can run my Vista 

and this Os at the same time!!Well I may gave it a try since I also need a mirror OS

(back up) and I may need to  install and run programs compatible only with Linux,
As instructed by the disc and the mag,,Have a copy of the Ubuntu iso 1st and burn it 

on a disc, and you will have a live disc , then install the vmware machine shop then 

the vmware player.So I followed the instruction,unfortunately it didnt work at 1st I 

got the error unable to find image ,then the 2nd attempt was less successfull I 

managed to have the Ubuntu installed as a virtual machine but I dont have internet 

access on it!? but the host computer which is vista got internet still working fine
very odd!I made some diagnostic like setting the ubuntu adapter to NAT to roaming but 

it didnt work,I did check the ip on the vmadapater but I m getting no connectivity
but wireless internet on the host (vista) still works.I also wondered if its alright 

to have a single vmadapter ,but I have 2 nic cards 1 for lan and 1 for wlan?! I 

though I got a busted disc.

I then decided to email pc mag 1st since I got the disc form them,I got a quick 

respond but with little help since they will not be liable for any damage and since 

it is licensed as freeware GPL,but they gave me some trouble shooting steps,one who 

memailed me was an au ubuntu user,which the gave me instructuion about launchpad

(didnt have a clue about that,when he gave me the  au,forum site of ubuntu)
So I did sent an email to ubuntu and the au forum,,some even emailed me personaly and 

said that they have the same problems and how they got it resolve(thanks to them)

So I followed the steps
.They suspected its about incompatibility,so I ran a new test since I have the live 

disc of Ubuntu hardy I tried running the OS as a live disc without hard drive 

installtion by simply booting fro the live disc!
Bingo!! Got the problem,theres an error messgae at the top right hand corner saying 

that my drivers are not supported for the wireless,I figured out I my need to install 

compatible drivers in my case it will come from madwifi since the adpater is from 

atheros,But it doesnt make sense,its a virtual OS so it will be dependent on the host 

which is vista.I the decided to upadte the drivers on the host computer,got it 

updated and I did run the ubuntu live disc,same message.! One thing crossed my mind
generic driver issues on windows! since most windows OS already comes with generic 

drivers that  may have cause the device to recognise the generic not from the orignal 

manufacturer,I consulted the store where I purchase the computer(since its still in 

warranty),they forwared my concern to the direct company that supports the HP 

brand,with some 5 mins talk with the tech he is convince its a driver issue he then 

tried to disable the wlan card but eneded up in with the famous BLUE SCREEN OF DEATH

(BSOD)memory dump.ok so we need a uninstaller,a registry cleaner and the manufacturer 

driver,the tech smiled and told me a the truth its a product known issues for your 

computer model!We can fix it but your computer had to stay for 2 days since we will 

request the resources first at the HP HQ.

So the computer was fix  after 2 days,I also asked the tech to gave me some drivers 

and utilities for HP,he gave it including some inf's but with the disclaimer we 

cant help you with the linux! agreed


Now Im back to square one,Again I reinstalled vmware machine shop.and the vmware 

player then run mouned the live disc
It works!!

also I now have 2 vmadapters now I got it wmadapter 1 will integrate with the LAN and 

vmadapter 2 will integrate with the WLAN(wifi),,its like an ICS(internet connection  

sharing in windows)

I then run a complete test to check if I got the entire packege installed
even trie the totim player and sooner I have a parokya ni edgar video in flv playing
Also I did check the virtual terminals(we can access it by key combinations 

crtl+alt+f1 thru f6,)
And of course my favorite: telnet (you may have the idea why)

it works now.And just when I though its over I found 1 minor problem,usb and card 

integration,times it will display on ubuntu times not 
somehow its no integrating well with the vmmachine.
Well thats fairly easy I just started the service for mass storage device on the host 

windows machine,and it works.I also started some services for the vmware

And to wrap it up I made some tweaks for the firefox in my ubuntu 
I simply typed "about:config" in the address bar and added some stuff including the 

layout and some stuff that will enable me to load the page much faster


Wheww wow after almost 3 days I got it working,one challenging installation.A very 

rewarding task!

Since then I got no problems with the Ubuntu .Im also glad that they will support Ubuntu hardy heron LTS with 2011 frame,Still Im worried with there fast pace cyle.

How about you guys!?

---

### Post by eilu on 2009-05-06
tl;dr
meron kang synopsis?

---

### Post by Nhatz on 2009-05-07
Ako napanaginipan ko.. then yun nag try ako maglinux. hehehe :)

ASTIG!!! :guitar:

---

### Post by guitar_man on 2009-05-07
Anak ng penguin ang haba...



pero ok kwento mo...parang ganun din yung sa akin,sa mga cracking din ako nagsimula...tapos ilang books na nabasa ko at lagi nila sinasabi na kailangan ko daw ng GNU/Linux para sa mga programs ng gagana sa craking,..
Ayon...Fedora core 5 ang una ko ginamit at sa simula ay takot din ako kasi baka hinidi gumana ang mga hardware.
Noong ko gamit para ako may bago kompyuter...tapos napanood sa youtube yung UBUNTU beryl VS. Vista Aero...lumuwa ang mata ko sa effects...Parang pinataoob ang effects ng vista sa burn effects palang..
Binigyan ako ng copy ng ubuntu ng dabarkads ko pero hindi ko ginagamit...nalaman ko na pwede pala magpadeliver ng libre at natuwa ako sa offer ng ubuntu na yun....
Isipin mo nalang sa ka makakakit ng libreng delivery nglibreng OS,,
Dun nagsimula ang ubuntu adventures ko..

---

### Post by wersdaluv on 2009-05-07
Wow thesis. Hehe. Ako, nakita ko sa stumbleupon tas sabi ko gusto ko ng sariling OS na completely tailored for my needs. I was thinking of something more radical than what I have now but my present desktop isn't too bad.

---

### Post by Script Warlock on 2009-05-07
ako rin nagsimula sa crack store d2 sa cebu and the first time i sighted redhat sa rack nila at naging curious ako about it. napadpad ako sa distro watch dun kami nagkita ni ubuntu and we live happily everyday. nagselos na nga mrs ko kc mas love ko daw OS ko kaysa kanya hahaha more time kc ako sa ubuntu, nakaka-adik.

---

### Post by pinoyskull on 2009-05-08
natuto ako dahil kailangan sa work, hehehehe

---

### Post by kingkalag on 2009-05-08
linux..ubuntu.? gumagamit na ako ng linux bago pa lumabas ang ubuntu, I didnt really get into using ubuntu until 3 years just before gutsy was released alam ko kasi ang una kung home server is named gutsy-gibbon some of you probably named your server as "server1" I named mine under its release code name. OSX at PClinuxOS pala ginagamit ko before bago ako nag fulltime sa linux and ubuntu, gumagamit parin ako ng windows just to use Autocad, what I mean by fulltime is Im using linksys router with linux dd-wrt, macbooks are running ubuntu, my house we have 4 desktops, 2 servers"hardy and heron" running on ubuntu and a windows that can only be open using ubuntu terminal server kasi walang monitor.  :)

---

### Post by joshua.solidum on 2009-05-09
hehehe how come I forget a 3 days installation,,grabe..actually kung ako  medyo marami rami naring na experince sa computers
so far yan yung 3rd na pinaka tough na installation nang isang OS na naranasan koh..2nd cguro nung e telnet ko ang isang mirror rackmount server at by crook na access namin!(another long story)hehehehe

---

