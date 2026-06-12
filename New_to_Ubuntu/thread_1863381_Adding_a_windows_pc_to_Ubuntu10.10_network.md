---
title: "Adding a windows pc to Ubuntu10.10 network"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by grey1beard on 2011-10-17
I have a desktop running ubuntu 10.10 (64 bit AMD) with a lan connection to my router. There is a wireless connection to a laptop also running 10.10, and a second wireless connection to a desktop running 8.04 LTS.

I have XP running on an old Dell laptop, which I need for printing on  a Ricoh gelprinter with a usb connection, and I'm thinking of getting a TomTom gps which is most simply updated via windows.

Can I get the windows machine to "safely" connect to the internet via my current network, without having to install AV software etc. on it ?

If the answer is yes, I'd be grateful for a link to any "how-to" on the subject, or instructions at "newbie" level.

My searches only find the reverse problem - adding ubuntu machines to windows networks.

---

### Post by egalvan on 2011-10-17
> **grey1beard said:**
> I have a desktop running ubuntu 10.10 (64 bit AMD) with a **lan connection to my router**. There is a wireless connection to a laptop also running 10.10, and a second wireless connection to a desktop running 8.04 LTS.

how many lan connections does that router have?
is it providing DHCP for your local lan?
is it providing internet for your local lan?

> I have XP running on an old Dell laptop, which I need for printing on  a Ricoh gelprinter with a usb connection, and I'm thinking of getting a TomTom gps which is most simply updated via windows.

Can I get the windows machine to "safely" connect to the internet via my current network, without having to install AV software etc. on it ?

If the answer is yes, I'd be grateful for a link to any "how-to" on the subject, or instructions at "newbie" level.

My searches only find the reverse problem - adding ubuntu machines to windows networks.

---

### Post by grey1beard on 2011-10-18
Hi egalvan,

> **egalvan said:**
> how many lan connections does that router have?
is it providing DHCP for your local lan?
is it providing internet for your local lan?

Only one of the four lan connections is being used.
Yes, and yes.

John

---

### Post by trozamon on 2011-10-18
You can just plug it in to the router or use wireless if it has it.

The articles you're finding about adding linux computers to windows networks all deal with advanced network stuff like Active Directory and similar such stuff. If you don't know what that is, you don't have it and it's not important.

Basically, just plug it into the router. That's neither "safe" nor "unsafe", it just is.

---

### Post by dixonstalbert on 2011-10-18
Hello

I understand you will be plugging the XP machine into a wired port on the router. 

If so, it will be the same as if was the only thing on the router. That is,
you can still:
   1. download and run viruses that will go through your whole network
   2. expose open ports that if you have open shares via samba will expose everything on your network.

Personally I have a old XP machine on my mostly ubuntu home network. My solution was:
   1. I set up 'user level' access with samba with good passwords so even if my XP machine is compromised they will have to work to get into my ubuntus

   2. the XP machine is older and slow and it is really slow with virus scanner running so I do not use one. What I did instead was backup partition with acronis (you could use free alternatives) to a external drive and accept the fact eventually one day it will be hacked and I will have to restore my backup copy.

  3. I try not do stupid stuff on XP machine. I do not get email on it. I do not run downloaded programs on it unless I am 100% sure where they came from. I do not go to shady websites on it. By doing this, I have never been hacked yet.(has been running without virus scanner for last 4 years)


If you want to try and get internet security via your ubuntus for your XP, you would have to buy and extra network card then hook XP to ubuntu machine. You could then run clamshell on ubuntu machine and learn the mysterious art of packet filtering etc. That would take some doing so I would not recommend it.

---

### Post by Morbius1 on 2011-10-18
>  Can I get the windows machine to "safely" connect to the internet via my  current network, without having to install AV software etc. on it ?No. You will have to install AnitVirus software and a firewall ( mostly to protect you from things going out of your Windows machine not in ).
>  My searches only find the reverse problem - adding ubuntu machines to windows networks.     In the context of this specific question there is no "Windows Network" or "Linux Network", there is only "The" network which is controlled by your router and all of the machines connected to it..

---

### Post by grey1beard on 2011-10-18
Thanks all for your replies.
Yes, I see now that I should have described what I had found as people running windows pcs, who then wanted to add a ubuntu machine to their existing network.
In my newbyness, I assumed that made a difference.

Dixonstalbert - more thanks for your spelled out reply.
My own usage will be similar, and my only need for it to be online is to update the proposed tomtom.
I shall have to tease out the nuggets in your points 1 and 2, but that will be a good exercise for the old brainbox.
Many thanks all,
John

---

