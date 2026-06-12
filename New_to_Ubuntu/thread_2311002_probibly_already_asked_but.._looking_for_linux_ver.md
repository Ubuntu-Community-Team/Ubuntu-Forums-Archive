---
title: "probibly already asked but.. looking for linux versions of programs"
date: 2016-01-23
forum: New to Ubuntu
---

### Post by freakna on 2016-01-23
sorry, im new and sorta bin walking in circles on the forum. ive noticed key words that would work on microcough don't work on linux.
 im looking for security programs. most important is a government wipe. DiD 5220.22-m (ECE) standard. firewall and virus program.
then spider software.. this may be called something different now. ive bin using the same program since 1995. now since i think about it, everything i use is from the 90's.

im very paranoid person and always dealing with hostile foreign entity's so i just need security up and working,  then ill learn everything else my self. 

oh and before i transfer linux from my dvd drive to permanently on HDD.. are drivers universal? am i gonna need to save them or will ubuntu just automatically copy them over?

---

### Post by lisati on 2016-01-23
*Thread moved to **New to Ubuntu**.*

---

### Post by grahammechanical on 2016-01-23
> are drivers universal? am i gonna need to save them or will ubuntu just automatically copy them over?

That I can answer. The other stuff, I have no idea what you are talking about.

Windows device drivers do not work on Linux. In most cases drivers are part of the Linux kernel. On machines with the latest hardware we should be using the latest version of Ubuntu because it uses the latest Linux kernels. In this way we stand the best chance of having drivers already compiled for our hardware.

We are able to run Ubuntu in a Try/Live session and so we can test out and see if all the hardware works before we install. One area that might cause a problem would be with a driver for any wireless adapter.

In Ubuntu there is a utility called Additional Drivers. That will search the Ubuntu repositories for proprietary video drivers and a wireless driver if we need one. And then install it for us.

The default video driver in Ubuntu is an open source video driver but through Additional Drivers we can install a proprietary video driver that might give a more satisfactory experience. And we can test all this in a Ubuntu live session.

Regards.

---

### Post by Mark Phelps on 2016-01-23
For "wipe" programs, read through the Wiki page linked here:  [https://en.wikipedia.org/wiki/Darik's_Boot_and_Nuke](https://en.wikipedia.org/wiki/Darik's_Boot_and_Nuke)

Good Luck

---

### Post by Geoffrey_Arndt on 2016-01-24
Additionally, unless you're running a server, there is no need for AV program in desktop Linux.   A small percent of Ubuntu users may run Clam AV, but that's to protect other windows users on the same machine, or just Windows users that are receivers of email from you.

The Linux firewall (iptables) is already part of the base system, but you may want to install GUFW (is in Ubuntu Software Center) . . . then you'll have to activate it and set up custom rules.    The default security settings in Ubuntu are pretty complete though (e.g., the Linux file permission structure, use of sudo, etc.).

Lastly, please define "Spider" software for us . . . are you talking about search engines on browsers, or for automated bots that crawl the web looking for certain data strings?

---

### Post by ian-weisser on 2016-01-24
> **freakna said:**
> most important is a government wipe. DiD 5220.22-m (ECE) standard.
Boy, that sure is living in the 90s. That was written in the floppy era, and superseded very long ago.
Your favorite search engine will happily tell you the current best-practices for non-recoverable data disposal.

---

### Post by freakna on 2016-01-24
to everyone, thanks for the help. lots of good info. the spider program. yes,  bot crawler is what im looking for.

lol.. yep, you can call me old school. i like my 90's programs. every time i try something new, i just find so many problems, maybe i should stop dissecting everything. ignorance is bliss right?

---

### Post by JOHN_ELLIS on 2016-01-24
Like it has been said above, to test your drivers, hardware, internet connection and so on try the live cd first and check to make sure everything works.

As for Anti virus, i'm with you on that one, I like to scan my files and make sure nothing is there that shouldn't be and I know that Linux systems are generally safe but it can't hurt to be sure right. So I installed Clam TK. It's pretty basic but it runs a scan of the folders and files on your pc, if any infections or threats are found it brings them up in a list, giving you the location of the files it also gives you the options to either quarantine the files or delete them.

Im not sure about bot crawlers but you can get programs like wireshark that show data packages coming through your network,

Cheers

John

---

### Post by deadflowr on 2016-01-24
There's a 3rd party add-on/extension for Ubuntu's file manager called nautilus-wipe.
It adds a wipe function to the right click options in the file manager.
So you can either wipe a particular file away, or wipe the available diskspace.
The default is a two pass with random.
But you can set a another option if you choose.

You can install it with
```
sudo apt-get install nautilus-wipe
```
You will need to quit and restart nautilus(Ubuntu's file manager) for it to take affect.
A simple logout works as well to achieve that.

---

### Post by freakna on 2016-01-24
the drivers, i cant be leave how easy that was. i didnt have to do anything while microsoft had a heart attack lol. i think im up and running for the most part. just gotta track down flash plug in and figure out how to get my biometric scanner active.. these names people come up with. but im all good :-)

---

### Post by Geoffrey_Arndt on 2016-01-25
OK,  here's a link with many of the recommended tweaks to do after installing ubuntu:     [http://www.noobslab.com/2015/10/top-things-and-tweaks-to-do-after.html](http://www.noobslab.com/2015/10/top-things-and-tweaks-to-do-after.html)  

Note that the above link will take care of things like flash installer, etc.    

Especially note that AV programs are generally a waste of time in consumer desktop linux.   Only shows Windows executables anyway (which will not run in Linux, but will give many false positives.)

Re the web bot crawler . . . . what did you have in windows and how did you use it (for what purpose)?

---

