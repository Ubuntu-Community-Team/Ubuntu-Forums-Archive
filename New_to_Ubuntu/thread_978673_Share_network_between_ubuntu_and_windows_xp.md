---
title: "Share network between ubuntu and windows xp"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by JohnnyMalakian on 2008-11-11
Hey again, ppl!

I think this problem has been posted already in the forum, but since I can't find it, here goes:

I'm using Ubuntu 8.04 with a DSL modem internet connection, and I'm using a crossover cable to connect to a Windows XP Pro computer. I can get file sharing to work, it is ok, but I still couldn't figure out nor find how to enable internet connection sharing between both PCs.

Keep in mind that I'm still a bit newb in this "IPs configuring" thingies and such lol xD.

Thanks in advance.
Stay cool!
[[[[]]]]/***** :popcorn: :guitar:

EDIT: Please bear in mind that I'm looking for a solution without buying routers and such xP

---

### Post by phidia on 2008-11-11
You want the windows computer to share internet with your linux computer through the crossover cable? If that's not what you want please be more specific.

There are networking guides at the Ubunti wiki [here]("https://help.ubuntu.com/community/NetworkDevices").

---

### Post by JohnnyMalakian on 2008-11-11
I have the modem connected on the Ubuntu PC, and I access the internet easily. What I want is to be able to access to the internet on the Windows XP computer, in other words, I want to share my internet connection to the Windows pc, 'cause I can't access the internet on that one.

---

### Post by superprash2003 on 2008-11-11
easy way to go is through firestarter ( install via synaptic) .it has ICS(Internet connection sharing) feature.. if that doesnt work, do it the command line way [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by JohnnyMalakian on 2008-11-11
I tried Firestarter, but it always gives me the error of "eth0 not ready". Any clues? Thanks for the quick replies, btw! ;)

---

### Post by JohnnyMalakian on 2008-11-11
anyone..? :(
The "eth0 is not ready" error is bugging me lol.

(sorry for the double-post)

Cheers!

---

### Post by irpapabear on 2008-11-11
just a shot in the dark...if you have the two machine connented via crossover. and no DHCP server is present. you must asign IP's and such.
hope tiz helpz :)

---

### Post by JohnnyMalakian on 2008-11-11
How and where do I assign them?
Sorry for being noob at this xD

Cheers!

EDIT: I'll probably be more specific at what I'm experiencing.

I have Firestarter installed. I added a static IP to my cable connection (instead of roaming mode) in the networks manager.

Then, when I start Firestarter, I defined "eth0" for Local, "ppp0" for the Internet and it has "nas0" as Unknown. Whenever I start Firestarter, it now gives me the "Unknown error occurred"... Believe me, this is getting on my nerves lol. At first, when I had my cable connection on network manager set as roaming mode, Firestarter would give me the "eth0 is not ready" error, but now what appears is what I've just told.

I've googled the world over for a solution but I haven't found any that fixed my problem.

Just to remember: I'm trying to share an internet connection (DSL Speedtouch USB modem) from Ubuntu Hardy TO Windows XP Professional via a crossover cable. File sharing is OK, the problem is getting internet on the XP.


Any help is always appreciated!
Thanks a bunch
[[[[]]]

---

### Post by JohnnyMalakian on 2008-11-11
Anyone? :P

---

### Post by superprash2003 on 2008-11-12
read this, [http://ubuntuforums.org/showthread.php?t=234068](http://ubuntuforums.org/showthread.php?t=234068) post 3

---

