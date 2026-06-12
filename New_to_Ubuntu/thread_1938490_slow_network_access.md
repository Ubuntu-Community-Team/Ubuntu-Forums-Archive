---
title: "slow network access"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-09
I just finished installing 11.10, and so far everything seems OK, except...my network access seems pretty slow. First off, it takes about 15-30 seconds after booting for the connection to complete, and then, downloads are slow.

I started a 23MB download, and was taking some time, so I went to my Mac (on the same LAN, using the same modem, etc.) and started the same download there. It finished well ahead of the Ubuntu download. 

I also have Windows 7 installed on the same box as 11.10, and network access under 7 is fine, so I think I can rule out a hardware problem. Any ideas why this might be happening?

Thanks.

---

### Post by d4m1r on 2012-03-09
How fast is your connection and are you using an ethernet cable or wireless?

If it is wireless, please post the make and model of the wireless card.

---

### Post by mzimmers on 2012-03-09
According to speakeasy.net, my download speed to my Mac is 11.57 Mbps.

I can't run speakeasy on Ubuntu, because the version of Firefox that came with it doesn't have the right version of Flash. I tried downloading two versions of Flash, but I haven't figured out how to install them yet. They're just directories that I think need to be put somewhere.

But, I did notice that the downloads were averaging about 300Kbps.

Oops...I forgot to explicitly mention that both connections are Ethernet.

---

### Post by mzimmers on 2012-03-09
I got Flash installed and ran speakeay. It says my download speed is about 5.5 Mbps, so about half the speed I'm getting on the Mac.

But, that doesn't tell the whole story. I'm also getting a lot of timeouts on trying to load pages, and there's just a ton of latency to the network connection. 

This borders on unusable; any suggestions?

EDIT:

Interestingly enough, the upload speed reported by speakeasy is incredibly slow; it's taken over a minute to complete the test. This might be a red herring, but I just thought I'd throw this bit of information out there.

---

### Post by d4m1r on 2012-03-09
> **mzimmers said:**
> I got Flash installed and ran speakeay. It says my download speed is about 5.5 Mbps, so about half the speed I'm getting on the Mac.

But, that doesn't tell the whole story. I'm also getting a lot of timeouts on trying to load pages, and there's just a ton of latency to the network connection. 

This borders on unusable; any suggestions?

EDIT:

Interestingly enough, the upload speed reported by speakeasy is incredibly slow; it's taken over a minute to complete the test. This might be a red herring, but I just thought I'd throw this bit of information out there.

Who is your ISP? You seem to be getting a whole bunch of different results....try downloading:

```
http://cachefly.cachefly.net/100mb.test
```

Your previous speed of 300kps = only 2.4mbps download. As for a speedtest, I'd recommend speedtest.net. Also, please post your network card info (if it is a desktop, post your motherboard make and model, if it is a laptop, give us the make and model of it). Ubuntu is a little screwy when it comes to internet settings, but only for people using wireless usually...

---

### Post by mzimmers on 2012-03-10
ISP is AT&T UVerse; I'm using a 2Wire modem.

Motherboard is an ASRock Z68M-ITX/HT. I'm using whatever networking is built into that.

Am I supposed to do something with the 100MB download, or was I supposed to time it?

According to speedtest.net, my Mac is getting 7.50 Mbps download; the Ubuntu box 2.70. But again, there seems to be something very wrong with the upload on the Ubuntu; it was flashing "connecting" for like 30 seconds before the test began. Also (like speakeasy) the test doesn't end cleanly; after reporting essentially the same upload rate at the start, the test doesn't end, but the rate gradually declines.

This almost sounds like some kind of protocol error on the uplink, doesn't it?

EDIT: just rebooted the box with Windows 7; speedtest.net reported 10.82 Mbps download and upload consistent with the Mac.

---

### Post by mzimmers on 2012-03-10
Any additional information that I can supply? I'd like to try to remedy this before I go forward. Thanks.

---

### Post by SuaSwe on 2012-03-10
Is anything else on the system slow as well as internet? Have you checked the System Monitor to see if the computer is suffering high CPU/memory usage that might cause the whole thing to be slow, and not just the internet?

A little look-round also generated [this community post]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") about disabling IPv6; not sure how relevant it is to whatever release you're on but could be worth a looksie!

You could also take a look at [this link]("http://ubuntuincident.wordpress.com/2011/12/15/wired-network-speed-is-very-slow/") where the problem turned out to be with driver<>kernel interaction.

---

### Post by mzimmers on 2012-03-10
Thank you for the suggestions; I'll start looking at them.

I'm still learning my way around the file system...how do I go about finding the System Monitor?

Thanks...

EDIT: I just looked at the post regarding IPv6; according to the directions contained therein, IPv6 is not enabled on my system.

EDIT 2: Success! The second link you posted turned out to provide the cure. I just ran speedtest.net and my download speed is on par with the Mac, and my upload speed test terminates normally. THANK YOU, SuaSwe! This is a big help.

---

