---
title: "no network connection"
date: 2008-11-16
forum: Philippine Team
---

### Post by Script Warlock on 2008-11-16
any help...

got problem in connecting to internet though it has signal and can ping the ip given pero wala response kahit live cd at reformz wala pa rin connection but the hardware says he is connected to the network..

my setup is pldt modem papasok sa pc ko...the modem works good

what will i do pls send help asap:confused:

---

### Post by killer_d76 on 2008-11-16
can you ping a website like google?

here are the IP addresses that you could try pinging

google -      64.233.187.99      

              72.14.253.99

yahoo -     209.131.36.158

---

### Post by Script Warlock on 2008-11-16
sorry mga bros case closed......cable lang pala may sayad pero ang pinagtaka ko lang is bakit same cable na ginamit ko sa laptop ay gumagana pero kung gamitin ko na to sa pc wala.....tsk sa dami trabaho left and right di ko na toloy mapansin ang mga maliliit na bagay....hehehhee ty for your time

@killer_d76.......ty ha....ok na ba webcam mo?

---

### Post by killer_d76 on 2008-11-16
di pa din, badtrip nga eh.. pero di ko pa nata-try yung last suggestion ni Loell, i'll try it later when i get home.

---

### Post by Script Warlock on 2008-11-17
wew what is this a bug?....after setting-up sa network pagboot nagdefault ang settings ng network..i cannot use this 8.10 as my server to my inet shop kung palagi na lang ganito....

hello guys any work around?...very annoying

ok lang ba ang firestarter para sa firewall management? di pa kc ako marunong magkamay(cli) ng firewall eh....

---

### Post by kiminaiseah on 2008-11-21
go console or teminal

$ifdown -a

$cp /etc/network/interfaces /etc/network/interfaces.orig

$nano /etc/network/interfaces 

addline

auto eth0
iface eth0 inet dhcp #< if ur using dhcp proto on your network

or 

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.0.0 or 192.168.1.0 < OPTIONAL
broadcast 192.168.0.255 or 192.168.1.255 <OPTIONAL
dns-nameserver 208.67.222.222 208.67.220.220 < OPTIONAL

ctrl+o, to save

change value with your corresponding network ip alloc.

and..........

rm -rf /etc/resolv.conf <--- careful with rm -rf :D

nano /etc/resolv.conf

addline

nameserver 208.67.222.222
nameserver 208.67.220.220

ctrl+o, to save
 
then


$ifup -a


----

kindly add sudo every bash line heheh..

---

### Post by Script Warlock on 2008-11-21
yes it worked.....thank you bro....i'll use 8.10 for my lappy and the workstations on my inet shop but not for the server....

---

### Post by kiminaiseah on 2008-11-21
:D would u planning din ba i UNIX yung server u? :d

---

### Post by Script Warlock on 2008-11-21
gamit ko ngayon sa inet shop ko is ubuntu 8.04 desktop na ginawang server for the 8 workstations na 8.04 din lahat..

unix? dba ubuntu is unix-like parehas na siguro yan...pero if u mean na unix na server talaga na wala gui, yaiks....hirap pa nga ako sa cli still learning pa...

---

### Post by kiminaiseah on 2008-11-21
hehe btw. take note yung kanina.. kasi habang nabubuhay ka sa mundu ng debian yan ang easy way i troubleshoot ang network conf ng debian.. without using GUI... 

saka pla i dini-disable ko sa bootup yung NetworkManager. kasi nag-ooverwrite nya yung configuration ng /etc/network/interfaces

di ko lang sure kung existing to sa ubuntu hehehe. :d

i pinapalit ko sakanya mag run for bootup yung /etc/init.d/networking

but when u disable NetworkManager mawawala yung ICON mo sa desktop sa may taskbar yung networkmanager dun

---

### Post by Script Warlock on 2008-11-21
o nga naman debian based ang ubuntu...i'd like to have the details of what you said disable network manager na magover write during boot-up.

pls share your ideas on how you did this, i'm very interested

---

### Post by kiminaiseah on 2008-11-21
i was encounter this when i setting up 1 or our server @ vitro using fedora 9 sulfur.

at the first na setup ko na yung network using gui manger(network manager) but the problem when we restarted the 2U Clone Server, bumalik yung setup default network config which DHCP... i was thinking this before sa loob ng vitro, "grabe parang nasa loob ka ng ref sa sobra lamig.." thinking solution mga 3hrs.. then i notify 2 things ang nag cocontrol sa network manager lalo na pag mag gui ka 1. NetworkManager, 2. networking script,...
when NetworkManger start. it also trigger /etc/init.d/networking to start with own configuration made by NetworkManager.. well bugs e2 ng sulfur miski early fedora releases... so i reconfigure our server with debian etch headless configuration... without gui.. and i see di ko na nakita uli nag load nung NetworkManger.. and i conclude kasama sa package ng GNOME yung NetworkManager. no harmful nman kung i disable to basta medyo kabisado lang configuring network interface with commandline

---

### Post by Script Warlock on 2008-11-21
thats what happened too sa server ko na override ng default settings pag-reboot kaya nga nagtaka ako kc sa 8.04 ok naman ang takbo, still i prefer to use 8.04 para sa server ig inet shop ko becoz of stability. baka next release ng lts na lang ako mag upgrade sa server os.cguro naman next release ng ubuntu fix na to.

cge thanks sa nfo ha at sana mamalagi ka d2 sa ubuntu forum kahit nakadebian ka. becoz we need you as a brother of ubuntu..:KS

---

### Post by kiminaiseah on 2008-11-21
no need to remove from startup yung NetworkManager.. nag raRun na pla sya kay ubuntu as daemon... hehe nag install ako d2 sa XPC ko ng ubuntu 8.04 oki na performance nito haha.. compare sa 7.10

---

### Post by Script Warlock on 2008-11-21
yes ok sa 8.04 but 8.10 has the small problem...

sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback   <<<< eto ang makikita mo 

kahit nga modified mo na ang conf nya pagreboot awtz balik sa dating gawi well i was talking about ics ha...

---

### Post by kiminaiseah on 2008-11-21
yes thats what im saying. kasi may sariling tmp configuration yung NetworkManager...

---

