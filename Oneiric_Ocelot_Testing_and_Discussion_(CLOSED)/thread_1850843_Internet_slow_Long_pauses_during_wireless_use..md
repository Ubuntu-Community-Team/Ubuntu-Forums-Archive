---
title: "Internet slow/ Long pauses during wireless use."
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2011-09-27
**[COLOR="Red"]SOLVED WITH KERNEL LINUX 3.0.0-15-generic[/COLOR]**

Before I begin, IPv6 IS disabled. Running :
```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```
gives me 1 . I will also note that I use wireless 100% of the time when using ubuntu and that this problem does not occur in Windows.

This problem has been around since I first started using Ubuntu with 8.04. If I remember correctly, it disappeared with 10.10 but reappeared in 11.04 and now 11.10.

The problem is that whenever I use the internet while I am surfing, even with a 100% signal strength the internet just has a sudden pause. This pause could last for 2-3 minutes and is very frustrating. 

By pause I mean that though im connected, whenever I try to enter a new website, it is almost as if the network just stops/fails to load a page and then after 2-3 minutes, it goes back to behaving well.

The strange thing is that while this is going on, I could have a radio stream on and the stream or download sometimes dont suffer the same fate. The download/stream still runs even though a webpage fails to load for 2-3 minutes.

How can I finally solve this issue once and for all?

**[COLOR="Red"]SOLVED WITH KERNEL LINUX 3.0.0-15-generic[/COLOR]**

---

### Post by empty_spaces on 2011-09-27
What wireless chipset do you have? Is it Atheros, by any chance?

---

### Post by SushiR on 2011-09-27
Same here. I've got this one
```
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

It uses "ath9k" as module.

---

### Post by empty_spaces on 2011-09-27
If you have ath9k, you can try the following threads.
[http://ubuntuforums.org/showthread.php?t=1740056](http://ubuntuforums.org/showthread.php?t=1740056) **(Check instructions in post #4)**


Or read through this for more help.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176)

---

### Post by tjeremiah on 2011-09-27
mines is :

```
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Subsystem: Intel Corporation Device 1050
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fa000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945


```

**[COLOR="Red"]SOLVED WITH KERNEL LINUX 3.0.0-15-generic[/COLOR]**

---

### Post by tjeremiah on 2011-09-27
> **empty_spaces said:**
> If you have ath9k, you can try the following threads.
[http://ubuntuforums.org/showthread.php?t=1740056](http://ubuntuforums.org/showthread.php?t=1740056) **(Check instructions in post #4)**


Or read through this for more help.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176)

in the second link, I fount no solution.

**[COLOR="Red"]SOLVED WITH KERNEL LINUX 3.0.0-15-generic[/COLOR]**

---

### Post by cariboo on 2011-09-27
Why is everyone giving the op solutions for Atheros chipsets, when his system has an Intel wireless device, check the signature, and the output of lspci he posted.

---

### Post by empty_spaces on 2011-09-27
> **cariboo907 said:**
> Why is everyone giving the op solutions for Atheros chipsets, when his system has an Intel wireless device, check the signature, and the output of lspci he posted.

I did not see his signature, and I very clearly asked if he had Atheros in my first reply, and clearly stated that I was providing instructions for ath9k in my second reply, which was meant for SushiR. The lspci was posted later.

Sorry for trying to help.

---

### Post by cariboo on 2011-09-28
> **empty_spaces said:**
> I did not see his signature, and I very clearly asked if he had Atheros in my first reply, and clearly stated that I was providing instructions for ath9k in my second reply, which was meant for SushiR. The lspci was posted later.

Sorry for trying to help.

I have no problem with you trying to help, but before offering a solution, it might be best to know what type of hardware the poster is using, instead of just posting a link and hoping it will help solve the problem.

The best way to help is to make sure you have enough information from the original poster in order to answer the question, if enough information isn't included, please help the poster determine the best way to supply that information.

---

### Post by empty_spaces on 2011-09-28
> **cariboo907 said:**
> I have no problem with you trying to help, but before offering a solution, it might be best to know what type of hardware the poster is using, instead of just posting a link and hoping it will help solve the problem.

The best way to help is to make sure you have enough information from the original poster in order to answer the question, if enough information isn't included, please help the poster determine the best way to supply that information.

Which is why I asked the OP if he had Atheros.
Before the OP replied, another member posted that he was facing the same issue with Atheros, so I provided the links.

I'm done.

---

### Post by SushiR on 2011-09-28
empty_spaces, the links helped. Thank you very much!!!

---

### Post by empty_spaces on 2011-09-28
> **SushiR said:**
> empty_spaces, the links helped. Thank you very much!!!

Glad I was able to help :)

---

### Post by tjeremiah on 2011-09-28
im sorry for the confusion but can anyone else help with this issue? Its been a real pain for years.

**[COLOR="Red"]SOLVED WITH KERNEL LINUX 3.0.0-15-generic[/COLOR]**

---

### Post by effenberg0x0 on 2011-09-28
Years? That's tough dude.

Check [https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/621265) . It's a known bug. Looks like its some sort of interrupt conflict with other device.

1. Some users managed to come to a fix (see #353 in the link above). The procedure is well explained. I'd give it a try. 

2. People mention that using ndiswrapper and the windows driver is also an alternative. If you wanna try it, you might want to read [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) .

I'd go with 2 first, because it is easier.

Regards,
Effenberg

---

### Post by tjeremiah on 2011-10-06
> **effenberg0x0 said:**
> Years? That's tough dude.

Check [https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/621265) . It's a known bug. Looks like its some sort of interrupt conflict with other device.

1. Some users managed to come to a fix (see #353 in the link above). The procedure is well explained. I'd give it a try. 

2. People mention that using ndiswrapper and the windows driver is also an alternative. If you wanna try it, you might want to read [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) .

I'd go with 2 first, because it is easier.

Regards,
Effenberg
neither worked and with ndiswrapper, when using new or the driver that is suggested, I get an error/wrong driver selected (version 10.1.0.13 / w39n51.inf file).

**[COLOR="Red"]SOLVED WITH KERNEL LINUX 3.0.0-15-generic[/COLOR]**

---

### Post by cariboo on 2011-10-06
I've found that most Windows 64-bit wireless drivers don't work with ndiswrapper, the one Windows only wireless device I have, I can only get it to work when running a 32-bit version with the Windows 32-bit drivers.

---

### Post by Quackers on 2011-10-06
I must admit that over the last week or so browsing the web through my wireless internet connection is much slower than it used to be. I think there was an update that caused it, but that could just be my imagination.
I'm using Intel Pro 4965 AGN.

---

### Post by tjeremiah on 2011-10-06
> **cariboo907 said:**
> I've found that most Windows 64-bit wireless drivers don't work with ndiswrapper, the one Windows only wireless device I have, I can only get it to work when running a 32-bit version with the Windows 32-bit drivers.

Well, I dont know what to do and the problem appears to be getting worst. I've dl'ed pretty much most of the new drivers for my card and some old and none of them worked. Tried 32bit and 64bit and nothing. I'll keep digging.

**[COLOR="Red"]SOLVED WITH KERNEL LINUX 3.0.0-15-generic[/COLOR]**

---

### Post by ronacc on 2011-10-06
several years ago when I tried to get a 64 bit driver working on my laptop with a broadcom card I had to try many different combinations of ndiswrapper and drivers to get it to work , try compiling a newer/different version of ndiswrapper .

---

