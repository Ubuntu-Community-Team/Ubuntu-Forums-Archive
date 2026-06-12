---
title: "Cannot connect via ethernet - Broadcom"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by schmaven on 2012-12-15
I am new to Ubuntu, but familiar with computers.  Have always wanted to use linux instead of Windows.  Just got a used laptop (Dell Latitude D610) with Ubuntu 11.10 already installed.  

I am unable to connect to the internet at all, either wired directly to the router, or wirelessly.  I really just want the wired connection to work, then I can figure out the rest more easily.  Currently plugged directly into the router.

NetXtreme BCM5751 Gigabit Ethernet PCI Express

I see some grayed out options: 
Wired Network
device not managed                   
Wireless Networks
device not ready (firmware missing)

It looks like installing the right firmware would solve the problem.  I have found commands that will get an Ubuntu machine to download the right firmware - but can't seem to find where to get it with windows.

Right now, I have a second computer to access the web and can transfer files via CDRW.

What do I have to do to connect successfully using an ethernet connection directly to the router?

---

### Post by sandyd on 2012-12-15
> **schmaven said:**
> I am new to Ubuntu, but familiar with computers.  Have always wanted to use linux instead of Windows.  Just got a used laptop (Dell Latitude D610) with Ubuntu 11.10 already installed.  

I am unable to connect to the internet at all, either wired directly to the router, or wirelessly.  I really just want the wired connection to work, then I can figure out the rest more easily.  Currently plugged directly into the router.

NetXtreme BCM5751 Gigabit Ethernet PCI Express

I see some grayed out options: 
Wired Network
device not managed                   
Wireless Networks
device not ready (firmware missing)

It looks like installing the right firmware would solve the problem.  I have found commands that will get an Ubuntu machine to download the right firmware - but can't seem to find where to get it with windows.

Right now, I have a second computer to access the web and can transfer files via CDRW.

What do I have to do to connect successfully using an ethernet connection directly to the router?
hmm
that card should work with tg3, can you try running
```

sudo modprobe tg3
```
in the terminal?

---

### Post by DuckHook on 2012-12-16
You mention that the OS came preinstalled. Therefore, don't know what previous owner did or made wonky.

My recommendation as follows:

Rather than diagnosing holes from an unknown past install, if you have no important data on the machine, then burn Lubuntu 12.04 and install. The D610 is a low-end laptop for today's OSes (I have the even earlier D600) that, unfortunately, are limited by their Pentium M CPU to the 3.2.x kernel. 3.5.x kernel will only run on PAE capable CPU, so *buntu versions 12.10 and higher will not run on our decrepit laptops.

If you have anywhere from 1 to 2 GB of RAM, another choice is Xubuntu, which will run quite well with that much memory. More than 2 GB will allow you to run Ubuntu proper adequately, but I would be very surprised if you have so much memory. Overall, I prefer Lubuntu for my ancient machines because they run so much faster that they feel re-invigorated.

If you have important data, I still recommend 12.04 install after proper backup. The new install will likely recognize the card immediately and give you another few years of support. Lubuntu 12.04 is not LTS, so you may wish to try Xubuntu for that reason alone.

P.S.

You are guaranteed to have further problem with wireless because your machine uses old broadcom chipset. Solution exists and is not too difficult, but let's get wired working first. Wireless solution much easier to solve once you are connected by wire. For preview of problem/solution see [here]("http://ubuntuforums.org/showthread.php?t=2094547"). No need to fret about that one yet. As said, let's get wired working first.

---

### Post by schmaven on 2013-01-08
Great point.  I'm downloading and installing a fresh OS now.

---

