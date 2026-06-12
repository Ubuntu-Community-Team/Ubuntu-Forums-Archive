---
title: "Skype freezing and taking over 100% of CPU"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-01-12
Hello everyone

I think I'm getting better at this Ubuntu stuff - so thanks for all your help so far!

Today I bring you an issue with Skype and I'm on Ubuntu 11.10.

Version: skype:i386 2.2.0.35-0oneiric2

I downloaded it from the Ubuntu Software Centre and it installed fine. I included the Indicator support for Qt (sni-qt).

On my main Ubuntu machine I find that randomly Skype will freeze. Sometimes this is instantly, sometimes it takes about 30 mins, sometimes 4 hours later... no real way of telling when it will freeze at least.

The only way to close and restart the application is using System Monitor and killing the process (end and other options do not work). When I go to kill the process, I find it is taking anywhere between 140% and 160% of the CPU. I'm not sure how it can take over 100% but fair play to it for trying. It's not a processor issue because I'm running an Intel Core 2 Quad CPU Q6600 @ 2.40GHz and it usually only operates at around 4-11% CPU usage. Memory is 3GB and usually only running at around 1.1GB anyway. These usage figures are from typical use (multiple firefox tabs...Libre writer open... maybe banshee too etc)

I find it happens most frequently if I'm using voice and video chat, less often if I'm using one or the other and even less so if I'm just using normal text - but it definitely has happened with all three of these combinations.

I've tried a reinstall but there has been no change.

Any help would be great.

Thank you all kindly.

---

### Post by mastablasta on 2012-01-12
> **Drowz0r said:**
>  
I downloaded it from the Ubuntu Software Centre and it installed fine. I included the Indicator support for Qt (sni-qt).
 
.
 
Qt is usually needed in KDE or for KDE applications. I though Skype is GKT+ based.
Anyway try to remove it and install the deb file found on Skype website.

---

### Post by Drowz0r on 2012-01-13
Hey there

Thanks for your reply. I went to the skype website and went to download on the Linux stuff and saw debian and ubuntu software available. I downloaded skype for 11.04 (which seems to work on 11.10 stuff - like my HP printer things do) This one had a .deb installer.

It seems to not be freezing at the moment, though the CPU goes between 104 to 60%. An improvement but still seems high? This is when using webcam both ways, voice chat one way and of course typing.

Is zat normalz?

---

### Post by Rainbow_Dash on 2012-01-13
> **Drowz0r said:**
> Hey there

Thanks for your reply. I went to the skype website and went to download on the Linux stuff and saw debian and ubuntu software available. I downloaded skype for 11.04 (which seems to work on 11.10 stuff - like my HP printer things do) This one had a .deb installer.

It seems to not be freezing at the moment, though the CPU goes between 104 to 60%. An improvement but still seems high? This is when using webcam both ways, voice chat one way and of course typing.

Is zat normalz?

It's not really normal. Is it persistently at 60% or does it just randomly spike to that on occasion?

---

### Post by Drowz0r on 2012-01-13
Persistently at a minimum of 60% with spikes to 104% and sometimes kinda "shaking" at like 70% (between 60-80%ish)

Though I've been on it solid since I installed it like you said a few hours ago and it didn't crash once.

---

### Post by Drowz0r on 2012-01-15
Just tested for another night. Started freezing again but still at a lesser frequency. It was the same on my 32 bit Linux machine. :(

---

### Post by Drowz0r on 2012-01-27
Fixed it with this:

[http://www.youtube.com/watch?v=N1pmM8l4H_s&feature=g-like&context=G26e39b9ALTyFobwACAA](http://www.youtube.com/watch?v=N1pmM8l4H_s&feature=g-like&context=G26e39b9ALTyFobwACAA)

---

### Post by BlakJakNZ on 2012-02-23
Sat thru the above video to find out that it's using the 'partners' repo's and reinstalling Skype from there.

Not sure how this will fix this problem (which I also have); i'm using the downloaded package (from skype.com) which I today verified is infact current. I also have this problem intermittantly and it's frustrating. I'm running Ubuntu 10.10 at the moment, 64 bit arch.  Skype has caused me to have to wait up to 40 minutes to get sufficient control of my machine back to save my work, before now.  I have Skype rigged to load when I login, and yesterday morning it caused me to have to task to a console and run 'pkill -9 skype' to get control back.
A few mins later I started skype manually and all behaved as expected.
I realise Skype 2.2x is 'beta' but it's good to report these problems in case a fix does become known?  At this stage i'm writing it off to buggy code from Skype (i've also had skype randomly die in the middle of the day for no apparent reason).  Nothing appears in syslog or anywhere else useful, either...

---

### Post by Drowz0r on 2012-04-01
> **BlakJakNZ said:**
> Sat thru the above video to find out that it's using the 'partners' repo's and reinstalling Skype from there.

Not sure how this will fix this problem (which I also have); i'm using the downloaded package (from skype.com) which I today verified is infact current. I also have this problem intermittantly and it's frustrating. I'm running Ubuntu 10.10 at the moment, 64 bit arch.  Skype has caused me to have to wait up to 40 minutes to get sufficient control of my machine back to save my work, before now.  I have Skype rigged to load when I login, and yesterday morning it caused me to have to task to a console and run 'pkill -9 skype' to get control back.
A few mins later I started skype manually and all behaved as expected.
I realise Skype 2.2x is 'beta' but it's good to report these problems in case a fix does become known?  At this stage i'm writing it off to buggy code from Skype (i've also had skype randomly die in the middle of the day for no apparent reason).  Nothing appears in syslog or anywhere else useful, either...

Yeah with Microsoft buying out Skype I'm not sure if it will continue to work for Linux either :c

---

