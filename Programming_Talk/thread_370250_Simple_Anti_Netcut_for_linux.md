---
title: "Simple Anti Netcut for linux"
date: 2007-02-25
forum: Programming Talk
---

### Post by mohasr on 2007-02-25
netcut is an arp spoofing/poisoning program that can disconnect other people from the lan.

so , i've been suffering from disconnects because of netcut since they started using it ,
on windows there is a small tool called anti netcut that can fix the arp table and resume the network connection.

but on linux there isn't any (or at least I didn't find it) , so I made this small app to do the same job of anti netcut.

it is written in python , and can work under both linux and windows.

I'm a python beginner , so any help/criticize is happily welcomed , also any attempt to make a simple gui for it is also welcome .

just make sure to run is as root .

&#1601;&#1610; &#1571;&#1605;&#1575;&#1606; &#1575;&#1604;&#1604;&#1607;

---

### Post by mohasr on 2007-02-26
does no replyes means that something is wrong ?

is this the wrong section for such posts ?

if so , then what is the best section to post threads about user-made programs ? if any

and if this is it , do any one knows a better method to counter netcut ?  as a software solution ,not hardware , without flooding the network with arp requests/replies. 

thanks in advance

&#1601;&#1610; &#1571;&#1605;&#1575;&#1606; &#1575;&#1604;&#1604;&#1607;

---

### Post by osa_ega2 on 2007-02-28
how can i use this application in Linux

---

### Post by mohasr on 2007-02-28
hi osa_ega2

first save the file antiNetCut.py into your home folder

then open a terminal window:
Applications -> Accessories -> Termenal    ( if you are using Gnome )

and type the following command:

sudo python antiNetCut.py

and if you want to close it press Ctrl+C

---

### Post by canavaro5555 on 2007-03-12
thnx

---

### Post by maddog39 on 2007-03-12
lol, this is a funny but pretty sweet program. Could you explain what the heck netcut is. Im not sure if we have this problem in america since I've never heard of it before.

---

### Post by jdong on 2007-03-13
> **maddog39 said:**
> lol, this is a funny but pretty sweet program. Could you explain what the heck netcut is. Im not sure if we have this problem in america since I've never heard of it before.

It falls into the category of networking mischief. It is a class of techniques that tries to pollute your ARP cache in an attempt to cause your computer to contact the wrong routers (or just not know what to contact), effectively zapping your network access.

It's only a problem on local networks with a lot of michievious people

---

### Post by amaiko on 2007-12-21
Thanks mohasr for this program i'll try it and Viva Mansoura.
maddog39  be sure that you will never have the problem of netcut in USA :D simply because there's no line sharing in USA but in very rich country like Egypt where more that 20 persons in one network use 512 KB/s or at most 1 MB/s line you will find 15 of those 20 use NetCut and i'm writing this reply while i'm sure there's more that one trying to uses the NetCut with me.

---

### Post by kareematwy2004 on 2008-02-18
Alsalam 3alaykom , brother , I just wanted to ask 2 question , 
the first that my problem is changing the mac address of the gateway , is this application static it . 
and the second Is that application take high space from the memory ?

---

### Post by clever.netman on 2008-03-31
Thanks mohasr.

There is another one make by[ AhmedSoliman]("http://ahmedsoliman.com").
It make static arp entry and it is a shell script.:)

---

### Post by heikaman on 2008-03-31
you can also use arpspoof like this
sudo arpspoof -t "gateway ip" "your ip"
you'll have to install arpspoof first of course.
this will do the exact same thing, but nice work =D>

---

### Post by the prime on 2008-07-26
&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605;
hi mohasr i m writing in english just to let all people get some information though out the replies 
and about the script i was suffering from the same problem and i tried that script and i found that it is great and works fine 
thanks man that was a good move

---

### Post by abulmagd on 2008-08-01
The script antinetcut.py worked fine with Netcut but didnt work with other ARP poisoners like switch sniffer and winARPspoofer
sudo apt-get install arptables
sudo arptables -P INPUT DROP
sudo arptables -P OUTPUT DROP 
sudo arptables -A INPUT -s gateway_IP --source-mac gateway_mac -j ACCEPT
sudo arptables -A OUTPUT -d gateway_IP --destination-mac gateway_mac -j ACCEPT

---

### Post by mshtawythug on 2009-01-31
thanx man for this nice program but one question where can i download netcut for my ubuntu and one more thing do any one of u know a program name that works as a net cut but on wireless networks

---

### Post by zied_m on 2009-02-14
> **abulmagd said:**
> The script antinetcut.py worked fine with Netcut but didnt work with other ARP poisoners like switch sniffer and winARPspoofer
sudo apt-get install arptables
sudo arptables -P INPUT DROP
sudo arptables -P OUTPUT DROP 
sudo arptables -A INPUT -s gateway_IP --source-mac gateway_mac -j ACCEPT
sudo arptables -A OUTPUT -d gateway_IP --destination-mac gateway_mac -j ACCEPT
what do you mean by source-mac gateway_mac and destination-mac gateway_mac
could you please give an exampel
thanx

---

### Post by klabezo on 2009-08-26
&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605;

bro [mohasr]("http://ubuntuforums.org/member.php?u=74276") very nice work

but for some people its very hard to run the program every  time from the command line so it will be nice if you make a gui

i try to shear linux ubuntu for others but some thing like that is very hard for the beginners

thanks again 
[]("http://ubuntuforums.org/member.php?u=74276")

---

### Post by abulmagd on 2009-09-22
gateway_mac is is the gateway MAC address, both "--destination-mac" & "--source-mac" are switches

---

### Post by Mfissal on 2010-06-11
[B]Thanks mohasr . beautiful solution >

&#1571;&#1604;&#1601; &#1588;&#1603;&#1585; &#1610;&#1575; &#1576;&#1575;&#1588;&#1575;[/B]

---

### Post by iqbalhafidh on 2010-08-11
Nice app:popcorn:

---

### Post by WitchCraft on 2010-08-11
Great post ;-)
I think Outlook might just use that.

---

### Post by Jetset Funky on 2011-03-12
Simple aplication. Thanks...  :guitar:

---

