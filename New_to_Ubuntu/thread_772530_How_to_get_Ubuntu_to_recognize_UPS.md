---
title: "How to get Ubuntu to recognize UPS?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Chimmer on 2008-04-28
Hi,

I'm new to Ubuntu (and linux), I have Ubuntu 8.04 running with no problems so far. I think it's great and may not ever go back to windows! :)

One question I have:

I have a [Geek Squad UPS/Battery backup]("http://www.bestbuy.com/site/olspage.jsp?id=1122654249041&type=product") that I've been using on my WinXP system. Despite all the negative reviews about it, it's worked flawlessly.

Is there a way to get Ubuntu to recognize and monitor it? 

I've downloaded something called "APCUPSD Monitor" but when I launch it I'm not sure how to configure it to recognize my UPS. Is this possible or is there another method?

Thanks for any assistance!

---

### Post by Lonewolf321 on 2008-05-01
I had the same UPS working with my Ubuntu machine.  APCUPSD does not recognize the UPS due to it was built by CyberPower Systems i believe or at least the one i had was.  I used the the NUT (Network UPS Tool) along with knutclient to monitor my system.  I have since changed to a APC UPS on my linux machines and use the Gee Squad on my Windows machines.  I'm not sure if i still have my notes on setup or not.  I had a cpu failure and ended up trashing my file system so i had to a complete reinstall.  If you have any questions i will try and help.

Jeff

Registered Linux User#: 448571 [[http://counter.li.org/]](http://counter.li.org/])
Registered Ubuntu User #16698 [[http://ubuntucounter.geekosophical.net]](http://ubuntucounter.geekosophical.net])

Powered by Debian/GNU/Linux
by Ubuntu ver 8.04 Hardy Heron

---

### Post by Chimmer on 2008-05-01
If you could help me out, that would be great. I had pretty much given up on trying to get the UPS to work with Ubuntu. I had posted on various forums, spent most of a day researching things and still had no luck.

I just downloaded Knutclient and I think I have NUT installed (not sure though.)

I opened up Knutclient and now I need help configuring it. I thought that maybe it would detect the UPS on it's own but it doesn't appear to.

---

### Post by Lonewolf321 on 2008-05-01
Can't find my notes.  But you have to configure NUT first then knuclient.  Found an example on google/linux here's the address it might help [http://www.linux.com/feature/128099?theme=print](http://www.linux.com/feature/128099?theme=print)  it's a different unit being setup but it will help you understand what needs to be edited.  Hope that helps.

Jeff

---

### Post by Lonewolf321 on 2008-05-01
Here's another example, [http://www.uno-code.com/?q=node/126](http://www.uno-code.com/?q=node/126)  hope this helps, sorry i couldn't find my notes.

Jeff

---

### Post by Chimmer on 2008-05-01
Thanks for your help. I'll give it another shot this weekend, hopefully I can get things working.

---

### Post by Lonewolf321 on 2008-05-01
no problem.  Wish i could have been more help.  But the instructions on those pages should be able to get you where you want.  

Jeff

---

### Post by Chimmer on 2008-05-02
I got it working! I went to CyberPower UPS site and downloaded PowerPanel for Linux.

I can go into a console and get the status, etc. It reads it correctly.

The only thing I need now is some type of GUI so that I can monitor it on my desktop without having to type console commands. 

I don't think Knutclient will work for this, at least I haven't figured it out. I tried googling but didn't find anything.

Do you think KnutClient will work or do you think there is anything else out there?

Thanks!

---

### Post by OhioLen on 2008-09-15
I'm considering one of these Best Buy units, too. Did you ever find a GUI for that software?

---

