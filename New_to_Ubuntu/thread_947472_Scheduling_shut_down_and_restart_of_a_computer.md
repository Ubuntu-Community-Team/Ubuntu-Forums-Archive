---
title: "Scheduling shut down and restart of a computer"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by korasdad on 2008-10-14
I will prefice by stating that I'm a novice. I unsuccessfully searched the forum to see if this was answered before so here goes.

I would like to schedule a home media and print server that runs Ubuntu to turn itself off and on at specific times of day so as to save energy and wear on the machine. Example, on at 3 pm when everyone gets home, off at 11 pm when everyone is in bed. 

Ideally, I could just have some mechanism to shut down and startup without my intervention. I've can configure the machine to go into a low energy state. The machine will successfully go into a low energy state but it doesn't seem to 'wake up' when needed.

The computer consists of an Asus M2N-MV motherboard, AMD be-2400 processor, 2 gb ram, and WD 750 gb green drive.

Is this a hardware issue or something I can do with Ubuntu?

Any help or direction to other threads and/or websites will be appreciated.

Regards, KorasDad

---

### Post by Sarmacid on 2008-10-14
I'm not sure how to set it to turn on, but to turn it off at a time, use crontab

```
sudo crontab -e
```

Add a line with the time and command you want, for example

```
00 23 * * * /sbin/shutdown -P now
```

That will make it shut down every night at 11 p.m.

---

### Post by Orange_and_Green on 2008-10-14
If your BIOS supports it, you could use Wake On LAN to start it up automatically. Here's a link:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

You could use cron on another computer that is permanently on (or that you know will be working at three o'clock) to schedule for a magic packet to be automatically sent to the print server at three.

---

### Post by DrMega on 2008-10-14
To wake it up again you may be able to schedule it in your BIOS depending on your BIOS version and motherboard.

---

### Post by Kellemora on 2008-11-11
Hi KD

This may or may not be of any help to you, but.

A BIG number of years ago I worked at a newspaper.  Both for safety and security reasons ALL the power to the workstations outlets were cut off at exactly 6:30 pm.  This means everything was without power.  (People would leave heaters, coffee warmers and who knows what else on, clock radios even!)

We had a program that ran on the mainframe that did a full shut down of each terminal at 6:15PM except for the computers in the galley room.  That way each workstations computer was shut down safely and off when the main power kicked out.
However, each computer was set in the bios to restart on power up.  

We had a rather large intermatic timer that would power down and power up the newsroom.  It was a quiet as a morgue in there at night when the power went down.  But funny as heck to be there when the place powered up.  You could hear every single computer go through it's boot up cycle.

Using that analogy, perhaps you could use a timer on your computer that cut the power about 15 minutes or more after it powered down on it's own, then when the power is restored the next day, you could set the bios so the computer boots up on power on.

Now I do realize that some motherboards that only works on if it shut down due to power failure, not being purposely shut down through the software.  So it may not work on some computers.

I purposely have all of my computers here except the server set to stay powered off in the event of a power failure.  Upon getting power, the server will power up on it's own and be ready when the other machines are switched back on to provide them with the start up data they need.

In other words, where there's a will, there's relatives, hi hi.....

TTUL
Gary

---

