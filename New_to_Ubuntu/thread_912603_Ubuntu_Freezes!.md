---
title: "Ubuntu Freezes!"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Mollusssc on 2008-09-06
Hi, 
First off, if there is already an answer to my question somewhere, i apologise but i couldnt find anything.

I installed Linux Ubuntu 8.04 off a live disc i received in the post. It successfully installed after the second try, i managed to get Ubuntu working once, and now it wont load past the splash screen. It loads just under 3 bars (ish) and wont do anything.

UPDATE: I unplugged my Belkin Network adapter whilst trying to load Ubuntu, and it started to load and do somesort of hard drive check i beleive. Well this failed as it was complaining about a "read only" file system.

Processor:
Intel Pentium D 2.8Ghz

Graphics Card:
Nvidia Geforce 8800GT

Feel free to ask if you want to know more about my system.

Thanks in advance.

---

### Post by Presto123 on 2008-09-07
The first error sounds like an issue with your display settings. Have you messed with the settings and set up the Nvidia driver?

I think that the best thing to do with a fresh install when you have an Nvidia card is to install it connected to the computer's (not the Nvidia's) onboard video card and then set up afterwards.

Second, I'm not sure. Would be best if you could post what the error is stating. This would help others help you troubleshoot your issues.

---

### Post by Mollusssc on 2008-09-07
Ahh ok. Ill fresh install whilst having my monitor plugged into the onboard chip and ill let you know how it goes.

Thanks

---

### Post by Mollusssc on 2008-09-07
I have clean installed it, and have gotten onto it, 1 problem down. 
Now i am having problems with NdisWrapper when i try to sort out my belkin F5D7051 wireless dongle, 
It comes up with the following:
> couldn't open bcmrndis.inf: No such file or directory at /usr/sbin/ndiswrapper-19 line 219

This happens after i type:
> ndiswrapper -i bcmrndis.inf
into a terminal.

Any help would be appreciated as i have tried countless solutions to no prevail.

Many thanks.

---

### Post by Presto123 on 2008-09-07
Ack...I'm sorry I didn't mean for you to DO a fresh install. I meant that that is how it usually works best for a fresh install. Next time, if this ever happens again, we have a command that will probably fix the display issue, but I wasn't sure of all of the details of your problem.

---

### Post by tangibleorange on 2008-09-07
> **Mollusssc said:**
> I have clean installed it, and have gotten onto it, 1 problem down. 
Now i am having problems with NdisWrapper when i try to sort out my belkin F5D7051 wireless dongle, 
It comes up with the following:


This happens after i type:

into a terminal.

Any help would be appreciated as i have tried countless solutions to no prevail.

Many thanks.

are you sure you're running the command from the directory which contains both the .inf file and .sys file?

---

### Post by Mollusssc on 2008-09-07
> **Presto123 said:**
> Ack...I'm sorry I didn't mean for you to DO a fresh install. I meant that that is how it usually works best for a fresh install. Next time, if this ever happens again, we have a command that will probably fix the display issue, but I wasn't sure of all of the details of your problem.
Lmao thats fine, it fixed it and i had only just installed it anyway, nothing was lost =)


> are you sure you're running the command from the directory which contains both the .inf file and .sys file?
Yes im sure, however i will check again now. I do hope it isnt as simple as a capital letter or something.

UPDATE: It kinda worked this time, BCMRNDIS.INF was located in etc/ndiswrapper/bcmrndis/ but the other files are not. I tried to copy and paste the missing files into the folder but it wouldnt let me due to permission restrictions. Anyone know how i can get around this?

---

### Post by Xiong Chiamiov on 2008-09-07
When typing things in a terminal, pressing tab will complete filenames for you.  That way, you a) save typing and b) know that the file actually exists.
```

ndiswrapper -i bcm[tab]

```

---

### Post by tangibleorange on 2008-09-08
I would copy the .inf file to your home directory or somewhere you have proper permissions. Make sure both the .inf file and .sys files are present, and run the install command from that directory.

---

### Post by Jammy4041 on 2008-09-08
In a terminal, type

gksudo nautilus

You will be prompted for your password, but then you could move the files in to the folder you want.

I hope this helps!

---

### Post by Mollusssc on 2008-09-08
> **Jammy4041 said:**
> In a terminal, type

gksudo nautilus

You will be prompted for your password, but then you could move the files in to the folder you want.

I hope this helps!
Thanks thats done it, but my wireless dongle still doesnt work >.<
I have the .inf and .sys files all in ndiswrappers/bcrmdnis folder but it just doesnt seem to recognise my dongle.

---

### Post by tangibleorange on 2008-09-08
what is the output of these commands:

```
ndiswrapper -l
lsmod | grep ndis
lshw -C network
```

---

### Post by Mollusssc on 2008-09-08
> **tangibleorange said:**
> what is the output of these commands:

```
ndiswrapper -l
lsmod | grep ndis
lshw -C network
```
Hi it comes up with:
[IMG]http://i36.tinypic.com/2cxfbj8.png[/IMG]

---

### Post by tangibleorange on 2008-09-08
hmm here's what i suggest:

```
cd ~/
mkdir ndiswrapper
cd ndiswrapper
gksu nautilus
```

now copy the .inf and .sys files to the newly made folder. when that is done, close nautilus, and use the same terminal to type:

```
sudo ndiswrapper -r bcmrndis
sudo ndisrapper -i bcmrndis.inf
ndiswrapper -l
```

---

### Post by Mollusssc on 2008-09-10
> **tangibleorange said:**
> hmm here's what i suggest:

```
cd ~/
mkdir ndiswrapper
cd ndiswrapper
gksu nautilus
```

now copy the .inf and .sys files to the newly made folder. when that is done, close nautilus, and use the same terminal to type:

```
sudo ndiswrapper -r bcmrndis
sudo ndisrapper -i bcmrndis.inf
ndiswrapper -l
```
Hi, It still comes up with "bcmrndis: invalic driver"
Thought i should add that sometimes Ubuntu will stop what its doing on some loading screens (Start up for example) and some codes i type into the termial and wont continue until i unplug the usb dongle.
Hope this is any clue.

---

### Post by tangibleorange on 2008-09-10
well the freezing is almost certainly a problem with the driver. all i can suggest is trying to find another set of .inf and .sys files for your dongle...

---

