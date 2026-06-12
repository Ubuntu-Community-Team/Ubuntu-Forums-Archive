---
title: "What clogs up ?"
date: 2018-07-31
forum: New to Ubuntu
---

### Post by Innernet on 2018-07-31
Hi.
Lately been leaving the compfuser in sleep mode instead of shutting off.
After several sessions on the web,  things start to slow down, unresponsive, Firefox crashing, like cumulative slow-down.

The typical first misbehavior is a very delayed response to keyboard; that disappears after properly cycling power, it recovers its 'normality'.  Restart does not cure it, 'recovering' pages as were at the end of previous session does not cure it.

What clogs up ?  How to clear the clog ?  Any way to avoid it ?

---

### Post by DuckHook on 2018-07-31
14.04 has been out of support for three months (I'm going by the info in your profile). Perhaps the problem is due to you no longer getting updates? If so, I highly recommend you upgrading to a current supported version.

To begin chasing down such problems, there are usually a few things one can do:
[LIST=1]
[*]Look at your logs
[*]Look at what is happening in *top/htop*
[*]Open FF from a terminal and see what errors are generated while surfing
[*]Is it due to a memory leak from invoking sleep? How does the rest of your system respond? You can track free memory with the command:```
watch free -h
```
[/LIST]

---

### Post by Innernet on 2018-07-31
Thank you. Did not know 14.04 support ended.  
Will take action.  Had not done the upgrade because by some reason, my 64bit laptop got 14.04-32bit installed 4 years ago and seems hurdles are in the way to upgrade to 18.04 64bit from my current flavor.

---

### Post by DuckHook on 2018-07-31
> **Innernet said:**
> Thank you. Did not know 14.04 support ended.My bad. Apologies. It doesn't end until April 2019. I misread that as 2018. Trusty is still in support, so you should still be getting updates. That is almost certainly not the problem. Try the other items I suggested.

---

### Post by HermanAB on 2018-08-01
Don't poke around in the dark.

Run 'top' to see what is going on, then use 'kill' to stop whatever should not be running.

---

### Post by Innernet on 2018-08-04
Thank you, knowledgeable gentlemen.

For a 'general' or 'experts' forum, that may be fine.
But in a beginner's place; the "Run top"  and "use kill" assume the beginner knows what you are talking about.
Where the hell is "Run top" ; "top/htop" ?  Do I open the terminal and type "Run top" ?

Running Ubuntu since 5.10, I still come to the beginners forum for doubts, and too often find responses aimed to knowledgeable users.  Am not as sharp, knowledgeable and bright as you.  Can you elaborate, please ?

Edited: Tried to upgrade to 18.04 a couple of days ago. Twice.  Got nothing after installing.  Blank.  Stuck after a couple of brief ASCII-looking messages while initializing.  Used the same 18.04 disc that installed fine in other computer. :cry:

---

### Post by HermanAB on 2018-08-04
Well, we assume that a beginner wants to learn and knows how to use google and knows how to read man pages.

So, we give you a little clue to point you in the right direction and then wait for the next question.

$ top

---

### Post by mastablasta on 2018-08-06
> **Innernet said:**
> 
Where the hell is "Run top" ; "top/htop" ?  Do I open the terminal and type "Run top" ?
Running Ubuntu since 5.10, I still come to the beginners forum for doubts, and too often find responses aimed to knowledgeable users.  Am not as sharp, knowledgeable and bright as you.  Can you elaborate, please ?


Terminal is one of the applications. you can search for it in the applications menu. when it opens, you would then just type in top.

alternatively there should be a system monitor application installed. you can run that, sort applications by CPU usage and then kill the one that is clogging up the resources. just make sure it is not a system application. you can then also investigate what is occupying up the CPU or RAM.

System monitors: [https://www.omgubuntu.co.uk/2011/11/5-system-monitoring-tools-for-ubuntu](https://www.omgubuntu.co.uk/2011/11/5-system-monitoring-tools-for-ubuntu)

System Monitor and the terminal based top are pre-installed. htop is a nicer top with more information but has to be installed form software center. the CLI based apps are there for when the graphical interface fails or sometimes they can provide better, more detailed information. they are the tools that are used on large server farms, so they are quite robust and conservative compared to desktop monitors aimed more at home users.

---

