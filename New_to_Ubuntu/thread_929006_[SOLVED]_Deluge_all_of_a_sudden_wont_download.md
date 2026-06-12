---
title: "[SOLVED] Deluge all of a sudden wont download"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-09-24
I started up Deluge today to download the Vendetta Online client and noticed that my Tracker Status for all torrents is "Alert: Connection refused (HTTP code=-1, times in a row=3)"

Yesterday my torrents were working fine. Ive tried torrents from different trackers as well. The only changes to my system were the Firefox updates released this morning.

My network health is now saying "No incoming connections" and when I try to test my port in the prefs it always says the port is closed. I do have the ports randomized, I have it set to encrypt stream and I run my tracker announce through Tor (which I've also tried to turn off with no results).

Something else weird, since I started typing this post, the network health has been switching from OK to "No incoming connections" but even when I try to update the tracker while the health is OK I still get the Connection Refused error.

This same thread was in the archives but no solution was posted.

---

### Post by kostkon on 2008-09-24
> **HittingSmoke said:**
> I started up Deluge today to download the Vendetta Online client and noticed that my Tracker Status for all torrents is "Alert: Connection refused (HTTP code=-1, times in a row=3)"

Yesterday my torrents were working fine. Ive tried torrents from different trackers as well. The only changes to my system were the Firefox updates released this morning.

My network health is now saying "No incoming connections" and when I try to test my port in the prefs it always says the port is closed. I do have the ports randomized, I have it set to encrypt stream and I run my tracker announce through Tor (which I've also tried to turn off with no results).

Something else weird, since I started typing this post, the network health has been switching from OK to "No incoming connections" but even when I try to update the tracker while the health is OK I still get the Connection Refused error.

This same thread was in the archives but no solution was posted.
There is a possibility that the tracker is temporarily down.

---

### Post by HittingSmoke on 2008-09-24
> **kostkon said:**
> There is a possibility that the tracker is temporarily down.

Well like I said I've tried several different torrents that all use different sites and trackers, including ones that report on their site to be up and running. I highly doubt that four different unrelated trackers are all down and giving me the same error message

I also just tried rebooting as well as resetting my router with the same results.

---

### Post by Furonne on 2008-09-24
Hey! i've had a similar problem.

I too received a http error towards the tracker, i've tried several speed tests and they show my downstream has been cut by half and upstream seems normal so i can't really understand why deluge won't seed above 9KB/s?  My isp is virginmedia and they can expect a sharp call tomorrow.

However! just today i realised that all this time i've been installing deluge for i386 platform.. but the thing is i have a pentium 4 which i think is x86 architecture doh! so no wonder my installs are acting up.

This means because i've been very busy throughout the transition to ubuntu linux that i'll most probably have to reinstall, and my anonymous feedback which i enabled in deluge had been all for nothing.

---

### Post by ThrobbingBrain66 on 2008-09-24
> **Furonne said:**
> Hey! i've had a similar problem.
However! just today i realised that all this time i've been installing deluge for i386 platform.. but the thing is i have a pentium 4 which i think is x86 architecture doh! so no wonder my installs are acting up.


You've been using the correct Deluge package. x86 = 386, 586, 686, ...

---

### Post by Furonne on 2008-09-24
This is why i'm too scared to leave beginner talk :)  i'll just keep on reading until i learn the basics thanks and bye for now.

---

### Post by HittingSmoke on 2008-09-25
> **Furonne said:**
> Hey! i've had a similar problem.

I too received a http error towards the tracker, i've tried several speed tests and they show my downstream has been cut by half and upstream seems normal so i can't really understand why deluge won't seed above 9KB/s?  My isp is virginmedia and they can expect a sharp call tomorrow.

However! just today i realised that all this time i've been installing deluge for i386 platform.. but the thing is i have a pentium 4 which i think is x86 architecture doh! so no wonder my installs are acting up.

This means because i've been very busy throughout the transition to ubuntu linux that i'll most probably have to reinstall, and my anonymous feedback which i enabled in deluge had been all for nothing.

lol yea he's right, i386 is x86.

I still cant find a solution to this. I've gone on my favorite tracker's IRC and talked with some experts and no one has any idea what could be going on.

---

### Post by HittingSmoke on 2008-09-25
Well today I started it up to try and tinker some more and it's downloading but I still get the No incoming connections problem and my torrents wont seed. So the announce comes back OK but I cant share.

This is the most confusing thing I've ever dealt with. Cant find a single problem or solution and nothing I do makes a bit of difference.

---

### Post by ThrobbingBrain66 on 2008-09-26
> **HittingSmoke said:**
> Well today I started it up to try and tinker some more and it's downloading but I still get the No incoming connections problem and my torrents wont seed. So the announce comes back OK but I cant share.

This is the most confusing thing I've ever dealt with. Cant find a single problem or solution and nothing I do makes a bit of difference.

What version of Deluge are you running?  Have you tried updating to the latest using the repositories from the deluge website?

EDIT: [https://launchpad.net/~deluge-team/+archive](https://launchpad.net/~deluge-team/+archive)

---

### Post by HittingSmoke on 2008-09-28
> **ThrobbingBrain66 said:**
> What version of Deluge are you running?  Have you tried updating to the latest using the repositories from the deluge website?

EDIT: [https://launchpad.net/~deluge-team/+archive](https://launchpad.net/~deluge-team/+archive)

Deluge repos? No I just installed what ever is the latest version of deluge-torrent in the ubuntu repos.

Thanks, Ill give that one a try but since it started out of the blue one day I have a feeling its either my ISP or some unseen network problem.
I havent been able to get into my router because I forgot what pass i set in it so I'm gonna try bypassing it directly to my modem and see if that might fix it.

But thats going to have to wait for later, right now I need sleep. Frat parties really suck the life out of ya.

---

### Post by HittingSmoke on 2008-10-23
I'm gonna mark this as solved. Found out it was Tor after all and Deluge wasnt properly turning off proxies when I unchecked them in the prefs. It seemed to fix itself after an upgrade.

The Tor issue is what seems to be an unresolved problem that I've also had on Windows installs so its neither related to Deluge or Ubuntu specific, I just couldn't tell because it was still working via my browser and I didn't have Vidalia running with it to show me the error message.

---

