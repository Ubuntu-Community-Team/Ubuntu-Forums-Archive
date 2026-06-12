---
title: "virus protection for ubuntu"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by stephenbp on 2008-04-23
What anti virus software is available to use on ubuntu 7.10?

---

### Post by schnauzer93 on 2008-04-23
You don't need any :)

---

### Post by Monicker on 2008-04-23
> **stephenbp said:**
> What anti virus software is available to use on ubuntu 7.10?

ClamAV is an open source virus scanner which you can install. There are may be others.

Are you running a file or mail server?  That is only time I have felt a real need to run anti-virus on a linux machine.

---

### Post by SunnyRabbiera on 2008-04-23
Right, but clam is targeted at windows drives and mailservers.
Honestly there are no real viruses that have any effect on your system.
Most viruses you might see listed for linux wont work without root access and root is disabled by default in ubuntu thus rendering them pretty much harmless.

---

### Post by Wiebelhaus on 2008-04-23
> **schnauzer93 said:**
> You don't need any :)

This man speaketh truth , but if you must - [Clam]("http://www.clamav.net/")you can find it in add/remove.

---

### Post by Dr Small on 2008-04-23
> **sx66gns said:**
> This man speaketh truth , but if you must - [Clam]("http://www.clamav.net/")you can find it in add/remove.
+1

There is no need for an AntiVirus, as it only reads the signatures of Windows binary viruses, and since they can not infect Linux, there really is no reason to have one.

Dr Small

---

### Post by stephenbp on 2008-04-23
My computer is setup as a lamp server.  I am planning on using it to learn and develop apache, php5 and mysql.  The computer will be for development only.

---

### Post by Monicker on 2008-04-23
> **Dr Small said:**
> +1

There is no need for an AntiVirus, as it only reads the signatures of Windows binary viruses, and since they can not infect Linux, there really is no reason to have one.

Dr Small

Actually, there are linux trojans and viruses which clamav will detect.  I've come across several on the Undernet IRC network.  :)

---

### Post by aparigraha on 2008-04-23
just set up a firewall through iptables and you'll be fine.

[http://ubuntuforums.org/showthread.php?t=159661]("http://ubuntuforums.org/showthread.php?t=159661")

---

### Post by SunnyRabbiera on 2008-04-23
well for that yeh clam might be best for you if you have a windows share.
The viruses probably wont touch Ubuntu but it certainly helps the windows bit.

---

### Post by rouge568 on 2008-04-23
Viruses? What are viruses? We have no viruses. Repeat: None. 

Because people are mentioning it, ClamAV is the main antivirus for linux, but you don't need it. Why? Because there are no viruses for linux. *Clam searches for Windows viruses* so that you don't accidentally pass them on to people with a lesser system. 

The only way to get a virus is to try and run a Windows virus using special software. Beware that the virus will still probably not work - see [_here_]("http://www.linux.com/articles/42031").


edit: is it viri?

---

### Post by SunnyRabbiera on 2008-04-23
> **Monicker said:**
> Actually, there are linux trojans and viruses which clamav will detect.  I've come across several on the Undernet IRC network.  :)

Yeh but its not nearly as common.

---

### Post by SOULRiDER on 2008-04-23
You can install AV software, but it will only scan for windows viruses...

---

### Post by schnauzer93 on 2008-04-23
> **rouge568 said:**
> The only way to get a virus is to try and run a Windows virus using special software. Beware that the virus will still probably not work - see [_here_]("http://www.linux.com/articles/42031").

This is why WINE hasn't reached version 1.0 yet - What's Windows compatibilty without viruses?

---

### Post by Tatty on 2008-04-23
> **Monicker said:**
> Actually, there are linux trojans and viruses which clamav will detect.  I've come across several on the Undernet IRC network.  :)

afaik, there have been less than 100 viruses ever produced for linux, most of these have only existed in a lab as proof-of-concept software.  And none of them will work on a modern linux install as they have been patched out of existance.

It is possible/probable that at some point in the future someone will manage to write a new virus for linux.  But no doubt it will get spotted quickly and  linux will be patched against it in a very short time.

No anti-virus can protect against things which have not yet been created though ;)

---

### Post by Paqman on 2008-04-23
> **rouge568 said:**
> Viruses? What are viruses? We have no viruses. Repeat: None. 


That's actually not correct. [There are linux viruses](http://en.wikipedia.org/wiki/Linux_Virus). They just don't present a threat to a desktop machine that's worth worrying about.

---

### Post by Monicker on 2008-04-23
> **Paqman said:**
> That's actually not correct. [There are linux viruses](http://en.wikipedia.org/wiki/Linux_Virus). They just don't present a threat to a desktop machine that's worth worrying about.

Good link. The linux RST virus is referenced there, the name of which had slipped my mind previously. That one is very common with the script kiddies on the irc networks.  If you get any type of file from them, most of the time it will be infected with RST.

---

### Post by rouge568 on 2008-04-23
> **Monicker said:**
> Good link. The linux RST virus is referenced there, the name of which had slipped my mind previously. That one is very common with the script kiddies on the irc networks.  If you get any type of file from them, most of the time it will be infected with RST.

Ah, but RST, as well as the rest of these viri needs to be run with root access. You should always watch what you do with 'sudo', especially if you don't know the source well (Read: flashy, suspicious, or obscure sites, plus any site with popups).

---

### Post by Dr Small on 2008-04-23
> **rouge568 said:**
> Ah, but RST, as well as the rest of these viri needs to be run with root access. You should always watch what you do with 'sudo', especially if you don't know the source well (Read: flashy, suspicious, or obscure sites, plus any site with popups).
It doesn't always take that approach with Social Engineering + sudo.

---

### Post by Can+~ on 2008-04-23
Good practices when using your local lamp:

-Restrict the permitted users to the localhost and local network, everything else is denied, you can config that on apache2.
-If you're behind a router, better.
-Create two accounts on MySQL, the root one, and a less powerful one, which actually access the data but can't do massive tasks like dropping a table.
-Configure the file permissions right!

But the best thing, is live behind a router, you can take some liberties about security, but for learning purposes, I suggest trying to build a strong security.

---

### Post by nicedude on 2008-04-23
I installed Clamwin anti virus first thing, since I have Windows files on a partition :-)

Other than that you don't need, it's like asking if you need a bullet proof vest when your made of titanium.

---

### Post by rodneyaltam on 2008-04-30
Bro;

If you use your linux as a file server and mail server then you need to install antivirus for protection. Coz some are coming from Windows. If you have window clients in your network sharing access to the file server then you need to install an AV to protect your windows clients not the Ubuntu clients. The virus programs created on Windows can't affect the Ubuntu system which is Unix based. I have encountered one in my file server a virus file in the drive but it wasn't running. It is just there for display....

Hehhehehehe

---

### Post by hyper_ch on 2008-04-30
> **rodneyaltam said:**
> If you use your linux as a file server and mail server then you need to install antivirus for protection. 
I have that but I don't have antivirus installed ;)

---

### Post by Dr Small on 2008-04-30
Why should we be responsible for protecting the Windows Users from viruses?
Maybe if they are plauged with enough of them, they will turn to Linux.

---

### Post by rodneyaltam on 2008-04-30
Well for me it is the job of the IT Administrator to make sure that windows and linux work in his environment. If everything goes well then it means you are doing your job as an IT. But we are planning on shifting to Ubuntu Linux. But this won't be very easy because most of the programs the users used in our company are window based. We are still planning on how to totally deploy to Ubuntu Linux.

---

### Post by bodhi.zazen on 2008-04-30
> **rouge568 said:**
> edit: is it viri?

It is viruses.

[http://linuxmafia.com/~rick/faq/plural-of-virus.html](http://linuxmafia.com/~rick/faq/plural-of-virus.html)

> **schnauzer93 said:**
> This is why WINE hasn't reached version 1.0 yet - What's Windows compatibilty without viruses?

That is not entirely true. Wine is an emulation layer and some of the same protections in a linux system are active in wine. Wine is proactive re: security.

The "take home message" with wine is two fold :

1. Do not run wine as root.

2. If you get a virus it should only affect your ~./wine. You need to check that there is no link outside of your ~./wine (check links in ~./wine/dosdevices).

[http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html](http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html) 

> **rodneyaltam said:**
> Well for me it is the job of the IT Administrator to make sure that windows and linux work in his environment. If everything goes well then it means you are doing your job as an IT. But we are planning on shifting to Ubuntu Linux. But this won't be very easy because most of the programs the users used in our company are window based. We are still planning on how to totally deploy to Ubuntu Linux.

You *may* want to run antiviurs on a *nix system that server as a mail or file server to Windows boxes, but, IMO, you still need antivirus and anti apyware on your Windows box(es).

---

