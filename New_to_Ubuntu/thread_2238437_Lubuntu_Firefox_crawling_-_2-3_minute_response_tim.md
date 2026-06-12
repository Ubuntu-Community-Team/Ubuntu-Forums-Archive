---
title: "Lubuntu Firefox crawling - 2-3 minute response time"
date: 2014-08-07
forum: New to Ubuntu
---

### Post by Pidge66 on 2014-08-07
Brand new to linux desktop. 

Laptop: Acer TravelMate 2480-2551 running Windows XP with 2 partitions of 20 GB each.

First I followed some blog to clean up my XP and create space. But in the process (e.g. uninstalling IE) I may have corrupted networking and Chrome stopped working.

Nevertheless, I tried to install Ubuntu 14.04.1 LTS 32 bit from DVD drive.  The Ubuntu screen stayed forever. With some keys pressed, I saw a bunch of **repeating **error messages about I/O error...[fail].   Also remember seeing "starting modem connection manager" that keep failing.  I tried to start over again and basically with similar outcome and was **not **able to finish installing.

Next I installing Lubuntu 14.04.1 (intel x86) instead. Better outcome.  Was able to complete the installation. Connected to wifi also.  However, the moment I started Firefox. Lubuntu froze.  I rebooted and tried again. Google search took 2-3 minutes to return and most of the time connection timed out.  The display looked awful as well, feeling like looking at 80's PC.

Q: Does Lubuntu interact with Windows XP? I was shocked when installation asked if I want to use the XP Media Center Edition!!
Q: How come installation never asked me which partition to install?!
Q: How do I go about addressing the networking issue?  (or is it something else)

Am I installing the right Ubuntu for my OLD laptop?  I have one more strike.  Please help!

---

### Post by Jesse_Campton on 2014-08-08
Welcome to Ubuntu Forums
Pidge66, Lubuntu is a light weight version of Ubuntu, there is also an even lighter distro called puppy linux (puppylinux.org). IMO, most linux based distros by default are not flashy, such as you might find using a Windows platform. Linux on the other hand is very customizable, there are many options to customizing your flavor to look the way you want. Moving on, is Lubuntu right for you, well only you can decide that. Sometimes, programs need a little work or you need to use an alternative program or just update the program to make it more stable. Ubuntu is not brand new of course, but is community driven, with that said please feel free to post any problems you might be having to these forums for help. Now, as for your Firefox problem, (Google is your friend) please have a look here: [http://ubuntuforums.org/showthread.php?t=2228285](http://ubuntuforums.org/showthread.php?t=2228285) . You may choose to install Chromium or Google Chrome to see if that helps.

---

### Post by Pidge66 on 2014-08-08
Thanks Jesse for responding.  I have some good news.  I happened to want to plug into the **ethernet **instead of **wifi**.  Voila!  Web pages started to become responsive.  I switched back to wifi at the same spot (next to the router) and it also worked fine!  I went back to my room, and the problem came back.   So my conclusion is SOMEHOW Lubuntu's wifi driver seemed inferior and requires high signal level in order to function.  2.5 bars out of 4 wouldn't work.  3 bars or more would.

As far as display, it got better too after I got the networking going.  It's as though software update / configuration were pending until internet connection is established in order to finish.

Finally, I was able to install Chrome. 

If all I want is browsing the web, is Lubuntu all I need?

Anyways, so that's 3 good news today :)  I still have open questions in my post, but now I am in much better shape.  I will probably repost some of my questions (and new ones) in a separate thread because the title of thread is no longer relevant.

---

### Post by Jesse_Campton on 2014-08-08
Yes, for browsing the web you can use Lubuntu or any of the many distributions that are available. Glad to see you were able to fix your issue today. Cheers

---

### Post by Rob Sayer on 2014-08-09
You may have caused problems in windows by trying to uninstall IE, though I certainly sympathize with wanting to get rid of that piece of garbage.  The problem is that Internet Explorer is part of Windows Explorer (which is also really why IE is so insecure) so yanking it is NOT trivial.  But that wouldn't affect the actual wireless adapter hardware, so I think that's a separate issue.

Fortunately, wired connections are more standardized and virtually always work in linux even if there are configuration issues with the wireless.

The issues you had when installing may have been caused by using wubi, which is not  recommended for later ubuntu versions.  I've never used wubi myself.   But otherwise you seem to have a working installation.

As far as the wireless goes, if you're having problems with that start a new thread in the wireless section with the following:

Open the terminal and enter

```
sudo lshw -C network
```

and copy and paste the output in your post.  It'll take a minute to display the info.  Wrap code tags around it so the people can read it more clearly.  There are *real* experts here on this forum but they're unpaid ...

---

### Post by Pidge66 on 2014-08-11
Bob, thanks for your response.  I actually used a live-DVD, not WUBI (I had to look up this acronym!)

Your point about uninstalling IE is a lesson learned; luckily without serious loss.

I will take your suggestion and pursue my wifi problem.  Currently I am electronically shackled to within 10 feet of my wifi router!

---

