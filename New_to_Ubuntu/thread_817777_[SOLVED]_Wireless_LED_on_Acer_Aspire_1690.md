---
title: "[SOLVED] Wireless LED on Acer Aspire 1690"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Jacdeb6009 on 2008-06-03
I have an Acer Aspire 1692WLMi which uses the Intel PRO 2200 wireless card (on-board). I am running Feisty and generally have over the last month or so gotten everything to work (bluetooth I can't comment on at this time).

The wireless works.  The Acer has a switch on the front to turn the wireless on and off.  This also works. ("sudo lshw -C network" shows it being on or off, and the switch toggles this).

The problem (if you can call it that...) is that the LED does not switch on and off, and thus other than using the command above to query the system, or checking for the presence of a wireless network, there is no way of figuring out whether the wireless adapter is working or not.

The adapter works, as I have successfully connected to a number of networks, the LED not working is a nuisance.

I have checked out a number of threads, but still have no real idea how to get this working.

Has anybody with the same set-up managed to get this working?

---

### Post by chiefmanyrabbitguteat on 2008-06-06
Sounds like Bug #176090

Read through [https://bugs.launchpad.net/bugs/176090](https://bugs.launchpad.net/bugs/176090) to make sure, but I had to install linux-backports-modules, and it fixed this issue for me.

---

### Post by Jacdeb6009 on 2008-06-06
> **chiefmanyrabbitguteat said:**
> Sounds like Bug #176090

Read through [https://bugs.launchpad.net/bugs/176090](https://bugs.launchpad.net/bugs/176090) to make sure, but I had to install linux-backports-modules, and it fixed this issue for me.

Thanks,  I have looked at this but it appears to be aimed mainly at Hardy Heron... I am not keen to move from Feisty Fawn right now and I don't know that the backport will work for Feisty.

Will it work without breaking my installation?

---

### Post by hoatu on 2008-06-18
I know it's not a solution but you may like to know you're not alone. I have the same laptop as you and have had this problem on both Gutsy and Heron. The button hasn't lit up orange since my Windows days!

I'm still searching for a fix. If I find one I'll link it back here.

---

### Post by Jacdeb6009 on 2008-06-18
Thanks hoatu, I have not bothered to look any further. Since I don't make use of wireless networks too often, the method of querying the network setup is OK for now.

It would be nice to get it working, but there are more important things to do... :)

Please let me know if you come across something that works.

Thanks!!

---

### Post by ramjet_1953 on 2008-06-18
Hi, There!

It may be worth trying this, as it worked on my Acer TravelMate 4101.

1. Create a file called [COLOR="Blue"]ipw2200[/COLOR] in /etc/modprobe.d/

i.e [COLOR="Red"]sudo nano /etc/modprobe.d/ipw2200
[/COLOR]
2. Add this line to the file:

[COLOR="Blue"]options ipw2200 led=1[/COLOR]

3. Save the file and then re-boot.

Hopefully, you will now have a 'blinkin' LED'

Regards,
Roger :cool:

---

### Post by hoatu on 2008-06-19
Nice one Ramjet - this worked for me!

Hoatu.

---

### Post by Jacdeb6009 on 2008-06-19
Thanks Ramjet,

Works like a charm, need to see what happens when it connects, but I can now see whether the wireless is on or off.

Great help!! :D

---

### Post by gizmoarena on 2008-08-08
Doesn't work on Acer Aspire 4715Z :(

---

### Post by sonnygauran on 2008-09-05
> **ramjet_1953 said:**
> Hi, There!

It may be worth trying this, as it worked on my Acer TravelMate 4101.

1. Create a file called [COLOR="Blue"]ipw2200[/COLOR] in /etc/modprobe.d/

i.e [COLOR="Red"]sudo nano /etc/modprobe.d/ipw2200
[/COLOR]
2. Add this line to the file:

[COLOR="Blue"]options ipw2200 led=1[/COLOR]

3. Save the file and then re-boot.

Hopefully, you will now have a 'blinkin' LED'

Regards,
Roger :cool:

Just curious as to where you got these info... but no biggie. :D
thanks! :D

---

### Post by Bohdie on 2009-06-25
I found most of my hacks for the netbooks for arch and thinkpads. Here is a link for the ipw2200 led=1 (googled it also)

[http://www.thinkwiki.org/wiki/Ipw2200](http://www.thinkwiki.org/wiki/Ipw2200)

Hope it helps

---

