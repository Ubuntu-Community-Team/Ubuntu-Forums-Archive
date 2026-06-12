---
title: "How to build software in Ubuntu"
date: 2006-03-01
forum: Programming Talk
---

### Post by msfox99 on 2006-03-01
I have a clean install of Breazy.  I am trying to get my wireless adapter working, so I downloaded the WPA supplicant.  It requires me to do a "make."  When I do this it is not recognized.  I found imake on the system, which I think is a new version version of make, but I have to enter the complete path to imake to get it to execute.  Then it can't find gcc.

Are there some paths that need to be set up?  How do I do this.

Thanks for any help.

---

### Post by wylfing on 2006-03-01
Try this:
```
sudo apt-get install build-essential
```

---

### Post by msfox99 on 2006-03-01
Thanks for the reply.  Does this require an Internet connection (don't have the wireless working yet)?  I have a connection on another machine that I can move files from using a flash drive.

---

### Post by engla on 2006-03-01
That package and its dependencies are on the install cd

Use synaptic, use "Add cd" if the install disc is not already in the repositories and then you can search for build-essensial, mark for installation and apply

---

### Post by msfox99 on 2006-03-01
Thanks guys.  I tried build-essential and it installed no problem.  Didn't need to "Add cd."  I am good to go now.  (For now...)

---

### Post by moberry on 2006-03-02
Its _highly_ possible you might have to do a couple more commands before it will build.

As long as you use *nix. NEVER forget these 3 commands

./configure
make
(sudo) make install

those are pretty generic in the linux world.

---

### Post by Arkaniad on 2008-01-01
:guitar: I have way too many computers for my own good. I have the following-

Dell Dimension 4550 (far from factory hardware)
IBM Think pad 365e
Dell Inspiron 7000
and a Compaq Proliant4500


Currently at the moment, i am installing Ubuntu 7.10 on the Inspiron. I use a Belkin 11mbps usb wireless adapter, which i am positive i have only the windows drivers for. Can somebody help me get it properly configured in Ubuntu???

:confused:i am completely new to Ubuntu but decently familiar with dos and know windows like the back of my hand.

---

### Post by LaRoza on 2008-01-01
> **Arkaniad said:**
> I have way too many computers for my own good. I have the following-

Dell Dimension 4550 (far from factory hardware)
IBM Think pad 365e
Dell Inspiron 7000
and a Compaq Proliant4500


Currently at the moment, i am installing Ubuntu 7.10 on the Inspiron. I use a Belkin 11mbps usb wireless adapter, which i am positive i have only the windows drivers for. Can somebody help me get it properly configured in Ubuntu???

i am completely new to Ubuntu but decently familiar with dos and know windows like the back of my hand.

Any particular reason you found a thread over a year old and asked an OT question?

You will get better results in another forum.

---

