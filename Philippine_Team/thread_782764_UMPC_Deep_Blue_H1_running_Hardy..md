---
title: "UMPC Deep Blue H1 running Hardy."
date: 2008-05-05
forum: Philippine Team
---

### Post by echo2knight on 2008-05-05
Repost ko lang at natatabunan.


Like I said before, just recently purchased a Deep Blue H1 UMPC.

I booted a live USB Hardy. It booted fine. Only, the resolution is 640x480. Having problems in changing it to its native 800x480 (VGA is based on S3 Chrome9 HC IGP). One more thing, di rin nagwork yung wifi nya at modem(Realtek RTL8187B Wireless and Agere Systems HDA Modem, respectively). Anyway that I can install the said drivers in ubuntu?

Isa pang tanong, H1 is based on VIA C7-M Esther 1000Mhz processor, supported na ba ng hardy yung mga features ng processor na to, like hardware security, and the likes?

Up and running sya under windows XP, my desktop is run by Hardy and I dont really want to return to using it. If only I can make the said hardware and features run in Hardy, then no more looking back to windows for me.

Help me mga guys. Also, is there someone out here who also owns or uses this umpc, kindly give me naman some feedback re your ubuntu installations.

Marami pong salamat!!!!

---

### Post by killer_d76 on 2008-05-05
i've been facinated with small computers and modifications, and 1st on my wishlist is EEE PC by Asus, i've been following this site for a quite sometime now while i'm saving up some cash to buy me one, here check out this site : [http://forum.eeeuser.com/viewforum.php?id=43](http://forum.eeeuser.com/viewforum.php?id=43)
 they were able to install Ubuntu on EEE PC, perhaps you could try if this should work on your Blue PC :-k

---

### Post by NakedSnake on 2008-05-06
Deep Blue? yan ba yung model ng PC na kinalaban si Kasparov sa chess?
I dunno if Im sure, si Karpov ba o si Kasparov. basta, parang narecall ko na yung name ng pc na lumaban sa chess grandmaster.

sorry po kung off topic reply ko.

---

### Post by pendletone on 2008-05-06
> **NakedSnake said:**
> Deep Blue? yan ba yung model ng PC na kinalaban si Kasparov sa chess?
I dunno if Im sure, si Karpov ba o si Kasparov. basta, parang narecall ko na yung name ng pc na lumaban sa chess grandmaster.

It was Gary Kasparov. Natalo siya sa isang chess-playing computer named Deep Blue. Mga 1997 ata nangyari yun.

---

### Post by baliwski on 2008-06-06
has anybody come up with a resolution to this problem?
Is it possible to get the drivers from the linpus installation which comes with the H1?

---

### Post by daxumaming on 2008-06-18
The driver page is here: [http://www.ilikeblue.net/support_drivers.htm](http://www.ilikeblue.net/support_drivers.htm)
it's in rar though, so better download unrar. Also, since I haven't personally checked, i'm not sure whether the rars contains source (which you'll have to compile) or binary drivers.

One more thing, because I still haven't gotten my hands on one of this beauties, I don't know if the drivers would work at all with Ubuntu - although I hope it does.


UPDATE:
forget this post, those rars on the driver page are windows drivers.

---

### Post by exkludge on 2008-06-20
> **echo2knight said:**
> Repost ko lang at natatabunan.


Like I said before, just recently purchased a Deep Blue H1 UMPC.

I booted a live USB Hardy. It booted fine. Only, the resolution is 640x480. Having problems in changing it to its native 800x480 (VGA is based on S3 Chrome9 HC IGP). One more thing, di rin nagwork yung wifi nya at modem(Realtek RTL8187B Wireless and Agere Systems HDA Modem, respectively). Anyway that I can install the said drivers in ubuntu?

Isa pang tanong, H1 is based on VIA C7-M Esther 1000Mhz processor, supported na ba ng hardy yung mga features ng processor na to, like hardware security, and the likes?

Up and running sya under windows XP, my desktop is run by Hardy and I dont really want to return to using it. If only I can make the said hardware and features run in Hardy, then no more looking back to windows for me.

Help me mga guys. Also, is there someone out here who also owns or uses this umpc, kindly give me naman some feedback re your ubuntu installations.

Marami pong salamat!!!!


@echo2knight

you can check this page.. its a mini pc using via esther proci and installed with ubuntu.

[http://ztechshop.net/computers/miniseries/](http://ztechshop.net/computers/miniseries/)

---

### Post by daxumaming on 2008-06-26
> **exkludge said:**
> 
[http://ztechshop.net/computers/miniseries/](http://ztechshop.net/computers/miniseries/)

this one's cute, but there's now way i'm bringing that to a park lugging a monitor and a car battery - which is Deep Blue's purpose.

but come to think of it, this is exactly the footprint im looking for for my server, minus the expensive price tag.

UPDATE:
Ok, it's official, i want this! So back to the OP's question... has anyone tried running Hardy on this beauty?

I'll be using this primarily for Web Dev stuff, and later Java dev. But I guess my main concern is, can it run my porn stash? I plan on installing Xubuntu Hardy.

---

### Post by echo2knight on 2008-06-29
> **daxumaming said:**
> this one's cute, but there's now way i'm bringing that to a park lugging a monitor and a car battery - which is Deep Blue's purpose.

but come to think of it, this is exactly the footprint im looking for for my server, minus the expensive price tag.

UPDATE:
Ok, it's official, i want this! So back to the OP's question... has anyone tried running Hardy on this beauty?

I'll be using this primarily for Web Dev stuff, and later Java dev. But I guess my main concern is, can it run my porn stash? I plan on installing Xubuntu Hardy.

Yes. I've tried running hardy on this little baby of mine. Okay naman sya. Its fast. Problems are, I cant seem to configure it to its native reso of 800x480, its defaulted to 640x480; the wifi and the modem, plus the sound coming from the speakers are very low even with max volume, compared to when installed with winXP.

Maybe its just me, or maybe its my 'nix learning that is insufficient to configure such a device.

Other than that, this baby is performing quite fine.

---

### Post by daxumaming on 2008-06-29
arrggghhh, i'm surprised that Hardy's having a hard time auto-configuring this device. too bad, i was planning on buying it within the next two weeks. oh well, i guess i'll save up for an eee pc 900 instead. but then again, who knows, i do love hacking...

---

### Post by Tomatz on 2008-06-29
To get your screen resolution set up correctly. Open a terminal and type:


```
gksu displayconfig-gtk
```


Then select the appropriate resolution (your gpu should be listed there also) ;)

---

### Post by geobz on 2008-07-25
Hi guys,

I'm also sort of having the same problems. I installed Hardy on a redfox wizbook800 naman. I dont have the modem problems...yet, but I cant see the bottom of the desktop. Actually i tried the fix from  the eeeuser site but its telling me that i have the wrong chipset and it only works on intel.

I also installed ubuntu netbook remix but it's still the same. Mukhang lumala pa nga kasi ang bagal na niya when i'm in the desktop. Parang maghahang laptop ko anytime soon.

Hope you guys could help us.

---

### Post by loell on 2008-07-25
naku, pasensya na , pang atom lang pala ang netbook remix, di ko yun napansin spec. :(

reinstall mo na lang ang ubuntu, try na lang nain i-fix yung bottom panel.

---

### Post by clintcan on 2008-08-03
Peace!

Mga bros,

Deep Blue H1 is just one of those notebooks based on Quanta IL1 specs (although it looks similar to via nanobook specs also).

You can download linux drivers here (this is based on the notebook One A110 - looks like Blue H1, and drivers are practically the same):

[http://service.one.de/download/index.php?direction=0&order=&directory=NOTEBOOKS/ONE_A1xx/Linux%20Drivers](http://service.one.de/download/index.php?direction=0&order=&directory=NOTEBOOKS/ONE_A1xx/Linux%20Drivers)

Here's the One A110 disassembled:

[http://www.a110wiki.de/wiki/One_A110](http://www.a110wiki.de/wiki/One_A110)

and the descriptions on how to install drivers for the H1 components:

[http://www.a110wiki.de/wiki/A110_Hardware_Status](http://www.a110wiki.de/wiki/A110_Hardware_Status)

Pwede pa maka install ng compiz dito :)

[http://www.a110wiki.de/wiki/LCD](http://www.a110wiki.de/wiki/LCD)

This wiki was made by a Debian developer who purchased this umpc recently (since ubuntu is basically debian, instructions here are interchangeable). Btw, interesting enough, as OT, the generic windows driver for vx800 graphics in the viaarena site lets you run windows in the lcd screen to resolutions up to 1024x768 (although it looks bad due to the small screen).

Btw, I'm writing this from my Deep Blue H1.

Clint

---

### Post by echo2knight on 2008-08-04
HEHEHEHE!!! Sa wakas... nakita ko rin ang solusyon sa mga problema ko!!!!

Many thanks pare..... :)

Now, can anyone help me with the blue stannum....

Intel HDA built-in sound card... up to now wala akong sound...

Hehehehe!!! Salamat ulit sa tulong!!!

---

### Post by clintcan on 2008-08-04
You may want to update your kernel (or downgrade) or alsa, or do the instructions stated here:

[https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/21847](https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/21847)

snd-intel-hda modules are in my experience one of those kernel modules that often needs tweaking (my neo laptop for example uses the snd-intel-hda module and I had to downgrade my kernel/alsa to make it work).

---

### Post by JazonEsti on 2008-09-20
Guys, any updates? The price has dropped to less than 10K Pesos. I think this one's great for the road warrior.

---

### Post by echo2knight on 2008-09-21
> **JazonEsti said:**
> Guys, any updates? The price has dropped to less than 10K Pesos. I think this one's great for the road warrior.

Less than 10K, really? Where have you seen this? Coz' last time I checked in cyberzone, this baby still costs 17.5K.

Saan mo nakita bro? Makabili ulit, panregalo, hehehe :)

---

### Post by JazonEsti on 2008-09-21
Nakita ko sa isang ad, at na-verify ko rin sa official site.

[Click here](http://www.ilikeblue.net/products/umpc.htm)

---

### Post by jeffery99 on 2008-09-21
confirmed. as in. bumili ako last night sa villman. moa. i got the blue h1 xp home edition. maganda siya. cute. looks very professional.may libreng sbs 350 speaker pa. yung malaking speaker. got it for 11490 ( xp.edition )

---

### Post by JazonEsti on 2008-09-21
How's the screen? Readable ba?

---

### Post by echo2knight on 2008-09-26
> **jeffery99 said:**
> confirmed. as in. bumili ako last night sa villman. moa. i got the blue h1 xp home edition. maganda siya. cute. looks very professional.may libreng sbs 350 speaker pa. yung malaking speaker. got it for 11490 ( xp.edition )


Grabe naman ang ibinaba. For just barely 6 months, 10K na lang. I bought mine for 18K, 6 months to pay. Binabayaran ko pa nga sya e. :( Well, anyway, mas marami ng makakaafford ng UMPC.

---

### Post by JazonEsti on 2008-09-26
Kamusta naman? No problems pag Hardy heron?

---

### Post by echo2knight on 2008-09-26
> **JazonEsti said:**
> Kamusta naman? No problems pag Hardy heron?

Di ko pa natry using Hardy, I installed XP because of driver issues. Wala pa lang akong time para subukan yung suggestion ng isang ubuntite dito. I encountered no problems using XP. Very readable sya, hassle lang pagbrowse dahil 800x480 lang resolution nya.

---

### Post by JazonEsti on 2008-09-26
Got it. Thanks!

---

### Post by baliwski on 2009-06-12
Obviously mukhang luma na thread na ito. But maybe I can get some help here. I have an old H1, which I want to revive with Ubuntu.
I'm thinking of changing my current XP, and hopefully find something that will make it run faster.
Has anybody had success in using this? I also will be using it with Sun Broadband. 
I'd apprecite anybody's feedback with this mix. Medyo madugo kasi mag reinstall ng XP. I make several partitions in my tiny 40GB drive to make it work a little quicker

---

