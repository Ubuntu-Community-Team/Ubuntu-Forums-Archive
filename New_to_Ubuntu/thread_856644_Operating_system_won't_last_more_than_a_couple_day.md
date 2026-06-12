---
title: "Operating system won't last more than a couple days"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by PizzaWednesday7 on 2008-07-11
So i'm trying to run Ubuntu on my computer that was a windows machine to start with. A couple months ago Windows started freaking out about a new error like every other day and i'd have to do the system recovery thing and wipe the hard drive. Well after that the registry got corrupted and i couldn't really fix it so i installed Ubuntu instead. It worked great for a couple days and then something bad happened with the desktop and x server and a bunch of other stuff. And i didn't really know that much about what i was doing, and i don't now either, so i just did a clean re install from the disk. Well it worked for a couple days again then something goes wrong kind like it did with windows, and i've repeated this a couple times and having a new computer every third day is getting kinda annoying. And it's different stuff too, sometimes GRUB won't work or it'll go into a file system check thing and stop working  there or as soon as i log in some internal error thing. I don't think i'm picking up viruses  or anything, and clearing out the harddrive with each new installation should get rid of anything bad from the time before right? Is there anything i can do to make my computer more stable? Like a new hard drive or anything? Any help would be great, sorry if i'm being dumb.

---

### Post by Xerp on 2008-07-11
You're right - if you're using Ubuntu it won't be viruses. Sounds like you've got a hard disk going bad. Boot from the Ubuntu CD and install smartmon tools from synaptic.

This is their homepage:

[http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Run smartctl from the terminal to test all of your hard disk drives.

[http://smartmontools.sourceforge.net/man/smartctl.8.html](http://smartmontools.sourceforge.net/man/smartctl.8.html)

---

### Post by neurostu on 2008-07-11
So it sounds like you are experiencing failing hardware which could be the HDD having "Writing" issues... You could also be experiencing ram issues. I don't have enough hardware experience to know off the bat

One way to diagnose the problem is to always boot the LiveCD and then just mounting your HDD for longterm storage.

One great thing about booting the liveCD is if you keep getting the same problems you will know it isn't b/c of the media is corrupted and is probably some bigger hardware issue rather then a faulty HDD.  If you don't experience the issues buy or borrow a new HDD, install to that and see if the problem goes away.

---

### Post by |{urse on 2008-07-11
i'm thinking replace your ram or your hard drive and/or ribbon/sata cable or both. Could also be corrupt install maybe caused by (but not likely, if you didn't have errors during install) a bad cd/dvd drive or a bad ide ribbon/sata cable. could also be (most unlikely) a bad ide/sata controller on your motherboard.

lol.. sorry but that's the best text answer i can give you.

It would help if you posted the output of this command 

```
dmesg | tail
```

---

### Post by PizzaWednesday7 on 2008-07-11
Ok thanks for the help. First of all i tried to use the smartctl thing but i couldn't really figure it out, i tried to do the tests and stuff off the live disk but it said i didn't have permission? I dunno if i was doing the right thing or not but. Secondly heres the report thing you asked for 
ubuntu@ubuntu:~$ dmesg | tail
[  158.768080] wlan0: no IPv6 routers present
[ 1299.272441] wlan0: RX deauthentication from 00:13:10:0e:04:f2 (reason=7)
[ 1299.272447] wlan0: deauthenticated
[ 1300.269563] wlan0: authenticate with AP 00:13:10:0e:04:f2
[ 1300.270861] wlan0: RX authentication from 00:13:10:0e:04:f2 (alg=0 transaction=2 status=0)
[ 1300.270865] wlan0: authenticated
[ 1300.270871] wlan0: associate with AP 00:13:10:0e:04:f2
[ 1300.273032] wlan0: RX ReassocResp from 00:13:10:0e:04:f2 (capab=0x411 status=0 aid=4)
[ 1300.273036] wlan0: associated
[ 1300.273043] wlan0: switched to short barker preamble (BSSID=00:13:10:0e:04:f2)
ubuntu@ubuntu:~$ 

i hope thats right and helpful. I don't have problems running off the live disk so i'm thinking that it's probably my hard drive. Thanks again. Oh well i've got another question then i guess. If i was going to buy a new hard drive because i don't think the internal ones are that expensive, right?, is there anything i should know? Like does it have to be the same type and stuff? I don't know anything about it. Sorry

---

### Post by neurostu on 2008-07-11
There are two types of HDD's.  Sata and IDE.  If your HDD uses a older looking ribbon cable with 2 long rows of pins and the standard 4 pin milmax power connector( these a seen throughout your computer) then your HDD is IDE.

If the drive has two smaller L shape connectors then your HDD is SATA. 

Simply buy which ever drive meets your budget and GB needs but is of the same type as your current drive.

---

### Post by PizzaWednesday7 on 2008-07-11
ok thanks. doesn't sound too bad

---

