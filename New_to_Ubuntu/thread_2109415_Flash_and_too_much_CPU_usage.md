---
title: "Flash and too much CPU usage"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by kenxdeath on 2013-01-27
HI i just got Lubuntu on a old computer that i'm working on because ubuntu is to slow on this computer. for some reason my computer is using to much cpu usage. i download task manager to see whats using of my cpu but i can't find anything. when i open chrome it say that i'm using 100% of my cpu but task manager saying that i'm using only 26% and every time i try to play a flash game or do mulitple on chriom it crashs. even on idle my cpu usage is 6%-9%.plz help

---

### Post by Frogs Hair on 2013-01-27
Look at the requirements for Flash on Linux and see if your hardware supports it .  [http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

---

### Post by rrich1974 on 2013-01-27
if you use google chrome, try too use flash 11.2 not flash 11.5 from chrome. 

in my machine, pepper flash eats much more cpu than system flash.

---

### Post by kenxdeath on 2013-01-27
will it does it for fire fox too. i think i meet requirements. i have a AMD Athlon(tm)64 processor 3800+ clocked at 2.4 ghz. application will spike up to 100% and then spike down.

---

### Post by frank604 on 2013-01-27
can you install htop 
```
sudo apt-get install htop
```
run it and prss 'F6' which is the "sort by" key.  then on the left hand side a new menu comes up and highlight 'cpu%' and press enter.
now everything is sorted by cpu usage.  write down the 'command' category of your highest cpu using package

for example, I realized that apport was taking 60% of both my cores.  I disabled apport and all is fine now.

it helps as a reminder of what is really going on underneath the hood.

---

### Post by HiImTye on 2013-01-27
CPU% isn't a good indicator of a programs' performance, or rather, is a good indicator of positive performance. a good program will peak the processor until it's done, and then drop down again. a better indicator is *CPU Time*. to monitor CPU time use ps
```
ps -e | grep *program*
```
replace *program* with the command for the program. do this when you load a program, and a few minutes afterwards, and you can get a better picture of the apps' performance.
in regards to Chrome crashing if you load multiple tabs, I would remove any extensions that might be causing you problems, and undo any advanced config changes you made in *about:flags*

---

### Post by frank604 on 2013-01-27
Let me clarify.  I use htop to see if a process is running in the background without my knowledge.  For example, I didn't know apport would take such a huge chunk of cpu.  Just a reporting tool right but it was hogging for awhile and I was wondering why my netbook was sluggish for unknown reasons.

Just for my own learning, how does measuring cpu time measure an app's performance?  When I run 'ps -e | grep chromium' I get 
21321 ?    00:00:01 chromium-browse
There are a few of these.  I then open facebook, cnn, youtube, etc and have 5 tabs open. Then I rerun the ps code and the output is
21321 ?    00:00:15 chromium-browse

How to read?

---

### Post by HiImTye on 2013-01-27
that means that it has used 1 second and 15 seconds, respectively, of CPU time. if it is using multiple cores, that will double (or more) the CPU time.
here's some more info on what CPU time is:
[http://en.wikipedia.org/wiki/CPU_time](http://en.wikipedia.org/wiki/CPU_time)
you can use this to sort by CPU time to get a better idea of what is taking how much time
```
ps -e --format=time,pid,user,comm | sort
```

---

