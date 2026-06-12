---
title: "New to Lubuntu ... internet issue"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by Homeroast on 2012-06-09
First, I am new to Linux systems generally, and Lubuntu specifically.  I'm not a techie just a fascinated user willing to learn an alternative OS and hopefully be educated in the process.  

I have this old IBM Thinkpad sitting around so I decided to put Lubuntu on it to see if I could get some life out of it.

I'm using it from LiveCD right now, but if everything goes well, I'll wipe the hard drive and make it a permanent installation.

When I was at work, I fired it up from the LiveCD and everything worked fine.  I was able to access the internet with the Chromium browser, and things were great.

However, when I get it home, and do the same thing, it won't connect to the internet.  I have a wireless modem that all my other computers access just fine - but not the Lubuntu machine.

Any suggestions?

If it matters,here are my system specs:

2002 IBM 
Pentium (R) IIII 2.80 GHz
504 MB of RAM, 2.79 GHz
34.4 total hard drive capacity

Thanks so much!

---

### Post by Rex Bouwense on 2012-06-09
That is wierd.  Have you enabled wireless and networking?  Does your computer see your network?  Try hooking it up with an ethernet cable to see if you can get on the Internet with a wired connection.
By the way welcome to the forums.

---

### Post by Homeroast on 2012-06-09
Thanks Rex,

How do I enable wireless and networking?

I'll try a wired connection ...

Best wishes,

H

---

### Post by Rodney9 on 2012-06-09
> **Homeroast said:**
> Thanks Rex,

How do I enable wireless and networking?

I'll try a wired connection ...

Best wishes,

H

Menu / Settings / Network Connections   , see screen-shot

Are you using the same dongle at work and home ?

Run > sudo apt-get update after plugging in your wired coneection


For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by Homeroast on 2012-06-11
Update:

I thought I'd do a permanent install on this machine since there really isn't anything on it I want.  I also was thinking it would be a bit easier to have the OS installed and then get the needed updates for the wireless issue.  (I'm guessing I was wrong about that.)

Anyway, about 10 minutes into the installation a box popped up and said an error occurred because it couldn't read the CD or perhaps the hard disk was faulty.  It also suggested I take the CD out and clean it.

So I took the CD out and cleaned it, but the machine would not reboot.  I get a black screen with a blinking cursor in the upper left hand corner.

I have no idea what to do next.  Any suggestions?

---

### Post by Rex Bouwense on 2012-06-11
OK.  Since it booted before from the CD before and everything was working at one location or another, shut the computer down.  Now boot it back up with the CD and see if it will boot.  If it does try Lubuntu without installing once again.  You will be running it from the CD.

---

### Post by Homeroast on 2012-06-12
I went back to square one and made a fresh install.  It turns out the original CD had errors on it.  I put in a new CD, checked it (no errors found), and installed Lubuntu 12.04.  Everything looks great and I like what it is doing so far.  

However, I can only access the internet with a wired connection.  

How do I get Lubuntu to connect via wireless connection?    I go to the VPN wireless connection screen and nothing is there. I'm using a Trendnet wireless adapter if that helps.

I know I'll get through this learning curve.  

Best wishes to all!

---

### Post by Rex Bouwense on 2012-06-12
I don't think that you want to connect to a VPN.  Left click the Internet icon on the task bar.  That will identify any wireless networks that are available.  Locate yours and click on it.  You may have to do that more than once.  If your wireless network is protected by a password, you will be asked to provide that password before you can connect.
Since you already connected to the internet wirelessly with the Live CD, I think that we can assume that you do not need to download a driver.

---

### Post by Homeroast on 2012-06-12
Thanks Rex!  That helped.  I'm up and running on the wireless.  I really appreciate you pointing this newbie in the right direction!

Best wishes to you!

---

### Post by Rex Bouwense on 2012-06-12
Glad to be of assistance and welcome to the Linux family.

---

### Post by drawkcab on 2012-06-12
Welcome!

---

### Post by Homeroast on 2012-06-12
Thanks.  Everyone here has been awesome and so helpful.

---

