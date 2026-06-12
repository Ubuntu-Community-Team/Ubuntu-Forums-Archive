---
title: "Connecting w/cable router"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by eyehatehippies on 2008-08-30
I have an older eMachine that i saved from the clutches of microsoft. I fully downloaded Ubuntu 8.04. 

I am trying to connect it to my already existing and working cable internet router (through Comcast). I tried calling Comcast and asking for my username & password that i used to get online through them, and they acted like i was asking them what the square root of cake was. Can anyone assist me on this? I have AIM and have the Ubuntu comp connected to this one via a KVM switch. So if you can hop on AIM and walk me through it i can jump from tower to tower as we go. 
Thanks in advance for ANY and all help!
](*,)

---

### Post by ellgor on 2008-08-31
Hi,
 This might sound simple, but it solved my problem after months of trying this and that, ready, SWITCH the router off for a minute then connect back up, the explanation I got was that the router needs to forget the old settings and take on the new, hope this is of help.

Regards, Ellgor.

---

### Post by oldsoundguy on 2008-08-31
I just plug in the Cat5 to the router and boot up.  As long as your primary computer is on line, the new one will go on line (be it Linux or Windows or Mac).  I do it all the time when I repair stuff for friends.  I put in a 3Com card and just plug it in (I use a model of card that has universal drivers as far back as Win95).  Saves me having to deal with their modem or whatever and makes getting on line for scans easy.

BUT, as mentioned, you MAY have to do a reset, but I have never had to do so. (I have Comcast, also)

And they will give you NO help on a router .. after all, it is NOT their equipment and their responsibility ends at the modem.

---

### Post by eyehatehippies on 2008-08-31
It's connected with Cat5 right now. So you're saying if i d/c the power and reconnect it should sense the router and "automatically configure itself"?:-k

---

### Post by pi.boy.travis on 2008-08-31
> **eyehatehippies said:**
> "automatically configure itself"?:-k

If your router is set up for DHCP then yes, it should automatically assign IP addresses.

---

### Post by nicedude on 2008-08-31
That may work and also if that doesn't then you may want to look on the back of the router and see if there is a tiny reset button hole. If so you may have to stick a paperclip in it and hold for 20 seconds so the router resets back to factory defaults. 

Hope you get it going and glad you ditched MS

---

### Post by pi.boy.travis on 2008-08-31
You can configure your router's advanced settings by typing its local IP into any browser.  The config options vary greatly, but maybe you could find something useful in there?

Hope this helps.

---

### Post by dhughes on 2008-08-31
Just restart the network, on each system (reboot the other computer if it's Windows...I guess), in a Terminal window do this

 ```
sudo /etc/init.d/networking restart
```

 It'll take about one second. If not try the unplugging of the router although I usually power off everything and turn it on in the order it comes from the ISP; cable modem, router and then computer - waiting a minute or two for each to stabilize.

---

### Post by eyehatehippies on 2008-09-02
> **nicedude said:**
> That may work and also if that doesn't then you may want to look on the back of the router and see if there is a tiny reset button hole. If so you may have to stick a paperclip in it and hold for 20 seconds so the router resets back to factory defaults. 

Hope you get it going and glad you ditched MS

It's a battle right now. I have 2 computers. A hyped-up PC for gaming & an older eMachine i'm learning Linux on. If there was a way to run uber-nerdy MMOs using WINE on Linux then i would do a full conversion, but alas i don't think that's possible without a whole host of driver problems as far as i know.

---

### Post by eyehatehippies on 2008-09-02
Thank you everyone! It's up & running (the internet), so now its just a matter of learning the system as i go. I already configured Evolution Mail for my Gmail account and figured out Pidgin, just gotta keep checking out all the bells & whistles. :grin:

---

### Post by pi.boy.travis on 2008-09-02
> **eyehatehippies said:**
> Thank you everyone! It's up & running (the internet), so now its just a matter of learning the system as i go. I already configured Evolution Mail for my Gmail account and figured out Pidgin, just gotta keep checking out all the bells & whistles. :grin:

Awesome!  Welcome to Linux.

Also, please mark your threads as solved when your problem has been resolved.

---

