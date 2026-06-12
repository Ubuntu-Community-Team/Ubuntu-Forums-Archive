---
title: "Ubuntu 8.04  - the Hardy Heron HELP--SLOW"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Rob2008 on 2008-05-25
HELP

Very pleased with my new Ubuntu 8.04
                - the Hardy Heron

But have just noticed that everything is running VERy sloooow :(

And things starting to crash :(

Is there any checks i can do to see why its running very slow ?

Total new to linux help needed

Thank You

Rob

---

### Post by sayakb on 2008-05-25
Can you provide your PC config? Plus, what do you mean by "things are starting to crash"?

---

### Post by misfitpierce on 2008-05-25
What exactly is crashing on you? 
Also what do you believe to be running slow... little more detail please.

---

### Post by Rob2008 on 2008-05-25
pent 4 1gb ram etc

Was working fine but lots of programs running slow now ie:

pdf viewer, most applications web working fine and fast

---

### Post by phoenix_abhi on 2008-05-25
What ? crashing ?

---

### Post by Inxsible on 2008-05-25
> **Rob2008 said:**
> pent 4 1gb ram etc"etc" LOL.

You can reboot, etc  ;) (Sorry couldn't resist !! )


How do you think we will guess what etc is ????

---

### Post by sayakb on 2008-05-25
As I understand, the programs you mentioned take some time to open up for the first time, but are loaded a bit faster when loaded consequently. Since you have a GB of RAM, try this:
```
sudo apt-get install preload
```

---

### Post by Rob2008 on 2008-05-26
> **Inxsible said:**
> "etc" LOL.

You can reboot, etc  ;) (Sorry couldn't resist !! )


How do you think we will guess what etc is ????



Yeah deserved that :)

Ok:-

Intel Pentium 4 CPU 2.60GHZ 1gb mem (memory 751.1mb)

using Ubuntu 8.04

Programs  working slow are:

archive manager
VLC


thanks

---

### Post by sayakb on 2008-05-26
Did preload make any difference?

---

### Post by philinux on 2008-05-26
Open a terminal and use

top

see whats hogging your cpu and memory then post back.

---

### Post by Rob2008 on 2008-05-26
i think preload may of helped a little is there away of configuring it?

Heres my screenshot of my top.

---

### Post by sayakb on 2008-05-26
You don't need to configure preload. What it does it that is caches the most used apps on the disk so that it can be quickly executed the next time you open it. You would notice the difference after some considerable amount of time of regular and vigorous usage.

---

### Post by sayakb on 2008-05-26
What are use running on the VirtualBox? And are you burning a CD/DVD at this moment? Close unnecessary apps which you don't need.

---

