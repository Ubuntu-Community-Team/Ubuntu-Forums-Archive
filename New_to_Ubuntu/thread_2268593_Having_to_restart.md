---
title: "Having to restart"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by Hankbonk on 2015-03-10
Having worked with Lubuntu 14.04 LTS for some months now, I started to get troubles : Or the screen turned all gray suddenly, while programs were still running (could still here the radio playing on Audacious) , or suddenly I couldn't enter text anymore in no input box while the mouse kept functioning, and I had to hardboot the system .  My PC is a HP Compaq DC 7700 SFF  Dual core D 945  3400 Mhz/ HDD 80Gb S-ATA / 1536 Mb DDR2 RAM .  It got so bad, having to restart more and more often, that I decided to fully reinstall the Lubuntu 14.04 from scratch, with the well known consequences as result .  Anyone any ideas ?

What does <Sysreq> + R,E,I,S,U,B exactly do,besides a quick reboot ?   The above problem starts to increase !!! 

What can I do, any ideas someone ?

[COLOR=#333333][FONT=Ubuntu]My System gets it too much, It's very frustrating to have to initiate this Sysreq sequence three or four times a day, if it's not more . Please look for a reason that my system gets stuck, and what is the full solution, so that I don't get that porbl[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]em no more ?[/FONT][/COLOR]:shock:

---

### Post by egeezer on 2015-03-10
I'm not sure what your "well-known consequences" are, unless you mean loss of data, need to reconfigure, etc.

But as for your need to hard stop, you should really use the Magic SysRq key method: hold down the Alt+SysRq keys and slowly run through the sequence R,E,I,S,U,B - after the B, your system will reboot (or if you want to shut it down, make the last letter o). For systems without a SysRq label on the key, it's the Prt Scr key.

Ubuntu distros all used to have this option natively, but if you want to see if yours has it, run
```
cat /proc/sys/kernel/sysrq
```

If it returns a 1, you're in business. If not, you can edit the file* /etc/sysctl.d/10-magic-sysrq.conf* to set it to 1.

I know this doesn't tell you what went wrong in the first place, but it will be of use to you in future difficulties.

Edited: Oops - I see you're using 14.04.  You will get a return of 176, I think - edit it down to 1, and it will work.

---

### Post by Hankbonk on 2015-03-17
The problem is starting to get increasing, read the first post please !

[COLOR=#333333][FONT=Ubuntu]My System gets it too much, It's very frustrating to have to initiate this Sysreq sequence three or four times a day, if it's not more . Please look for a reason that my system gets stuck, and what is the full solution, so that I don't get that porbl[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]em no more ?[/FONT][/COLOR] :shock:

---

### Post by kerry_s on 2015-04-05
sounds like your running out of ram to me. 1.5gb is not a whole lot these days, perhaps your tying to do to much at once.
what does lxtask monitor show you on usage ?

---

### Post by Vladlenin5000 on 2015-04-05
I wouldn't trust an old (must be very old) 80GB 2,5" disk with DOS games let alone an whole OS... Have you tested it already? You should...

---

### Post by v3.xx on 2015-04-05
When's the last time you opened it up and cleaned out the dust?

---

### Post by Hankbonk on 2015-04-06
[COLOR=#000000]kerry_s, I include this screenshot for you

[IMG]file:///home/henk/scrnshot_task_Manager.png[/IMG]

[/COLOR][COLOR=#000000]This is not a good post ! Please refer to post #12 for a good screenshot ![/COLOR]

[TABLE="width: 500"]
[TR]
[TD][IMG]file:/home/henk/scrnshot_task_Manager.png[/IMG][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by v3.xx on 2015-04-06
> v3.xx, I have never opened it up yet, do you really think that could help ?
We have one computer (a Dell) that never overheats to the point of shutdown, but when it starts running hot, weird things happen.  And in our case, a cleaning has worked.

There are of course other things to look at, but IMO its a good idea.

---

### Post by Hankbonk on 2015-04-09
Vladlenin5000, thanks for your reply : The system did at one point run a disk test when rebooting, and it turned out alright .  I this a good reply to your post ?

egeezer, thanks for your post .  I looked at the out coming of cat [COLOR=#000000][FONT=Ubuntu Mono]/proc/sys/kernel/sysrq, and it gave me a return code of 1 : Is that ok then ?  The Sysrq R,E,I,S,U,B has always worked, but I do not know what this SysRq sequence really makes the system do : Can you explain all of the Characters please ?[/FONT][/COLOR]

---

### Post by kerry_s on 2015-04-09
> **Hankbonk said:**
> [TABLE="width: 500"]
[TR]
[TD][IMG]file:/home/henk/scrnshot_task_Manager.png[/IMG][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

that's not good, you have 4 apps open & your using half your cpu & almost all your memory.
try opening the apps 1 at a time & see home much resource each is using, that way you can look for a lighter version.
maybe 1 of those apps is having issues cause i ran on 1gb & didn't see problems like that.
how much swap did you allocate ?

---

### Post by Hankbonk on 2015-04-13
Dear kerry_s, I don't know anymore how much SWAP I allocated, I'm sorry .

---

### Post by Hankbonk on 2015-04-14
Moderator, why have replies been removed from this thread ?

---

