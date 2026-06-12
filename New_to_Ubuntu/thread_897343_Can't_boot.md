---
title: "Can't boot"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by roscal on 2008-08-22
Having problems booting my other machine.
Its been running Feisty for over a year, no problems.
Got home after work, machine seemed dead.
Thought the cat had hit the power button

Machine won't boot though.
Hangs at the loading screen.
The blue loading bar making it about 3/4 way through, then nothing.

Tried booting 7.04 live cd, hangs.
So, tried Gutsy, then Hardy live cd's , no luck.

I can get into the Bios, the machine powers up fine.
It just hangs on loading the OS.
I can't even upgrade it to anything, it just freezes.
I saw a message briefly that said 'No User Defined Window'
or something similar, it was so quick.

Any ideas anybody?
I'm really stumped, and would hate to loose whats on the machine.

Thank you, this is the first major prob I have had with running Linux. Hardware? PS maybe??

---

### Post by fmartinez on 2008-08-22
If you have a live CD you can boot to rescue mode and look at the /var/log files to see what error messages may have prevented it from booting up. You'll probably be able to use the live CD to rescue what ever information you may have just in case you need to reinstall.

---

### Post by tangibleorange on 2008-08-22
> **roscal said:**
> Having problems booting my other machine.
Its been running Feisty for over a year, no problems.
Got home after work, machine seemed dead.
Thought the cat had hit the power button

Machine won't boot though.
Hangs at the loading screen.
The blue loading bar making it about 3/4 way through, then nothing.

Tried booting 7.04 live cd, hangs.
So, tried Gutsy, then Hardy live cd's , no luck.

I can get into the Bios, the machine powers up fine.
It just hangs on loading the OS.
I can't even upgrade it to anything, it just freezes.
I saw a message briefly that said 'No User Defined Window'
or something similar, it was so quick.

Any ideas anybody?
I'm really stumped, and would hate to loose whats on the machine.

Thank you, this is the first major prob I have had with running Linux. Hardware? PS maybe??

When the system is booting, could you press Alt+F1 and then see which message it hangs on?

---

### Post by roscal on 2008-08-22
fmartinez:
 Thanks, yes I have several live cd's but they won't boot though.

tangibleorange :
I just tried booting and pressing Alt+F1.
First attempt, the blue loader bar went right to the end.
Then nothing, black screen.
Second attempt, same thing but now has message 
'Starting up...
Loading please wait...'
Its hung at that point.

No luck.
Anything else I can try?

---

### Post by eightmillion on 2008-08-22
Since you can't boot any live cd, it sounds like you have a hardware problem. Maybe try booting with only one stick of ram if you have two. Try them one at a time.

---

### Post by tangibleorange on 2008-08-22
> **roscal said:**
> fmartinez:
 Thanks, yes I have several live cd's but they won't boot though.

tangibleorange :
I just tried booting and pressing Alt+F1.
First attempt, the blue loader bar went right to the end.
Then nothing, black screen.
Second attempt, same thing but now has message 
'Starting up...
Loading please wait...'
Its hung at that point.

No luck.
Anything else I can try?

ok try opening up your /boot/grub/menu.lst:

```
gksu gedit /etc/grub/menu.lst
```

scroll down to the line that has the title of your ubuntu boot entry (should be at about line 130, it starts with title), and find the line just below it that starts with kernel (and is quite long). remove the word 'splash', save and then reboot.

hopefully it will now reveal where it is hanging.

---

### Post by roscal on 2008-08-22
My first thought was heat.
I have taken the cover off earlier and cleaned out what little
dirt was in there.
Didn't help though.
But maybe it is heat still?
Could it be  a dying power supply?
Or a failing hard drive maybe?
I'm stumped here, can't get it to go.
Can't boot live either.
Since it partially loads, i assume MB is ok.
I would think the HD is working also, or it wouldn't see anything
correct?

Help

---

### Post by eightmillion on 2008-08-22
Could be a dying power supply. I seriously doubt it's your hard drive since that wouldn't affect booting a live cd. Heat, as you said, could also be an issue, but ram or power supply seem most likely.

---

### Post by roscal on 2008-08-22
> **eightmillion said:**
> Since you can't boot any live cd, it sounds like you have a hardware problem. Maybe try booting with only one stick of ram if you have two. Try them one at a time.

Really?
I have 2 /512 sticks in it.
I will try that, maybe tomorrow if i have no luck tonight.

---

### Post by roscal on 2008-08-22
> **tangibleorange said:**
> ok try opening up your /boot/grub/menu.lst:

```
gksu gedit /etc/grub/menu.lst
```

scroll down to the line that has the title of your ubuntu boot entry (should be at about line 130, it starts with title), and find the line just below it that starts with kernel (and is quite long). remove the word 'splash', save and then reboot.

hopefully it will now reveal where it is hanging.

Thank you, but I can't get to a terminal if thats what you mean.

---

### Post by eightmillion on 2008-08-22
> Really?
I have 2 /512 sticks in it.
I will try that, maybe tomorrow if i have no luck tonight.
Yes, if one of your sticks of ram is failing, it could cause your computer to hang on boot. If you try them one at a time you should be able to determine fairly quickly.

---

### Post by roscal on 2008-08-22
When booting, 
I do get the initial screen where you choose your kernal to boot.
Also there is an option of 'memory test'(memtest 86), which I just ran.

I am running the test now, but have no clue what these
results mean.

---

### Post by eightmillion on 2008-08-22
memtest86 will run as long as you let it. [This link]("http://www.memtest86.com/tech.html") may help you figure out what you are seeing. It might be a good idea to let it run over night.

---

### Post by roscal on 2008-08-22
> **eightmillion said:**
> memtest86 will run as long as you let it. [This link]("http://www.memtest86.com/tech.html") may help you figure out what you are seeing. It might be a good idea to let it run over night.

Thank you eightmillion bubbles!
I ended up turning mem test off, didn't know it ran indefinatley.
Still no luck booting anything, not even live cd.
I will try removing ram as you suggested
when there is more light (tommorow).
If that doesn't work, I think to try a new PS?
I dunno....

---

### Post by eightmillion on 2008-08-22
> Thank you eightmillion bubbles!
Good to see another Trailer Park Boys fan! You should probably try replacing the graphics card also, if you can. I would try to take out as much hardware as I could and still be able to boot a system and work from there. Good luck!

---

### Post by roscal on 2008-08-22
I'm asking for help here, using my wifes XP machine.
Mine (the one with probs), is single boot Kubuntu Feisty.
2 -80 gig HD
1 Gig ram
128 mb AGP video card.
I love Ubuntu/Kubuntu and have been raving about it for so long.
This is humiliating...:(
I hate Windows, and want to get my own Linux back if possible..
Thanks all!

---

### Post by roscal on 2008-08-22
> **eightmillion said:**
> Good to see another Trailer Park Boys fan! You should probably try replacing the graphics card also, if you can. I would try to take out as much hardware as I could and still be able to boot a system and work from there. Good luck!


Yes, propane propane!
Thank you sir, I have another video card.. can try that also. 
I will do that, tomorrow in the morning light.
Now, its time for a rum and coke.
:)

---

### Post by roscal on 2008-08-22
Currently the machine is just hung with the blue loader scroll bar 3/4 of way across.
Also, the floppy's light is solidly on.
Don't know if this means anything?
I'm never getting to the 'username, password', window.

---

### Post by roscal on 2008-09-04
Solution?

**Motherboard was deep fried.**


(it was)

---

