---
title: "Weird Graphical Glitches on Ubuntu 13.1?"
date: 2013-12-15
forum: New to Ubuntu
---

### Post by Remember2Wipe on 2013-12-15
So I installed Ubuntu several days ago and I'm loving it so far. However, there is one issue I've been having. 
Ubuntu has some graphical glitches on my PC that are a bit odd. I've tried taking pics of a couple of them but they always stop as soon as I take a snap shot. I was able to get one minor one though as you can see in my attachments. What it seems to be doing is the borders of windows and almost being sucked into the top left of the screen. They're seemingly pulled off of the actual window and stretched to the top left. Weird. Also, sometimes my launch sidebar things (I'm new :/) flicker really fast and sometimes disappear for no apparent reason. The program most affected it seems is the terminal. When I move it, it always gets this big gray blob in the middle and sometimes half of it'll disappear for no reason and I have to click it again for it to come back. It's not cleanly cut in half either. Really jagged.

I'll try to get a better pic for you guys if I can.

Thank in advance

---

### Post by Remember2Wipe on 2013-12-16
Anyone? :(

---

### Post by monkeybrain20122 on 2013-12-16
> What it seems to be doing is the borders of windows and almost being  sucked into the top left of the screen. They're seemingly pulled off of  the actual window and stretched to the top left. Weird.
That is a feature, not a bug, known as the global menu. :) I find it weird too, but somehow some people are convinced that this is a great feature since the Mac has it. I have no idea since I have never used a Mac. :)

I think there are ways to disable it on a per application basis but you will have to google for it or wait for someone else to tell you. It used to be really easy to remove it but because of unrelated changes in gnome if you do it now the whole menu will be missing from gnome applications like Nautilus (File) and Evince (document viewer) because now their menus are detached from the main windows and stick to the top bar by design.

---

### Post by Remember2Wipe on 2013-12-16
Sure it's not a bug?

Got a better pic

---

### Post by monkeybrain20122 on 2013-12-16
Ok the background does look like a glitch. What is your graphic card? What graphic driver do you use?

---

### Post by Remember2Wipe on 2013-12-22
Sorry I'm a bit late. Haven't touched this computer in a while and kinda forgot about this issue.

Graphics card? AMD.

Driver? No idea.

How would I go about checking for driver?

Ran a command I got from googling how to check. Here ya go if you need more info:
 > lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G]

---

### Post by monkeybrain20122 on 2013-12-22
Install the proprietary driver. This guy seems to have same problem and get it fixed by installing fglrx
[http://ubuntuforums.org/showthread.php?t=2195012](http://ubuntuforums.org/showthread.php?t=2195012)

---

### Post by Remember2Wipe on 2013-12-24
Obvious noob here. How do I know which package to install and how do I install .tar files?

I get that their archives like .rar and .zip files but how do I install from them? It doesn't look like there is any file to run the install within it

---

### Post by Remember2Wipe on 2013-12-24
Read me from installer
[http://pastebin.com/t1uaXty8](http://pastebin.com/t1uaXty8)

Did the first part running the sudo apt-get command. Don't know what to do now

---

### Post by Remember2Wipe on 2013-12-30
Final bump

---

### Post by QIII on 2013-12-31
Why not just install the driver in the repo?

```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

```
sudo amdconfig --initial
```

Reboot.

---

### Post by Remember2Wipe on 2014-01-02
So I created a thread a while back and it's officially dead now because I had a lot going on and wasn't able to check it for a while, but I did narrow down my problem. [Link if interested]("http://ubuntuforums.org/showthread.php?t=2194014")

I apparently need to install an fglrx driver (what?) for my graphics card. 

Read the other thread for more info but I'll give a quick summary here.

The issue is pic related. That happens, windows disappear, the sidebar sometimes flash very quickly.

[ATTACH=CONFIG]249131[/ATTACH]


Guy in other thread asked me what graphics card I used and I ran a command to find it:
> lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G]

He then answered: 
> Install the proprietary driver. This guy seems to have same problem and get it fixed by installing fglrx
[http://ubuntuforums.org/showthread.php?t=2195012](http://ubuntuforums.org/showthread.php?t=2195012)

All of my what?


Two questions now basically.

Which driver do I install from the [AMD website]("http://support.amd.com/en-us/download")? I'm pretty sure about this one but I just want to be sure I'm downloading the right one.

Also, this should be easy, how do I install from  .tar.gz files? This is what one of the drivers I've downloaded comes in. 

Thanks in advance

---

### Post by deadflowr on 2014-01-02
Is that the right thread you linked.
It's only been two days since QIII posted.
Far from dead.

---

### Post by QIII on 2014-01-02
Merged, in fact.

---

### Post by Remember2Wipe on 2014-01-03
I think this fixed it. I'll give it an hour or two though.

Thanks and sorry about creating another thread. Didn't see another page was added to the original thread:D

Be back in an hour to close thread if all goes well

---

### Post by Remember2Wipe on 2014-01-03
Calling it fixed. Thank you

---

