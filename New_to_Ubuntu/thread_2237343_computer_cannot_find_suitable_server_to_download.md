---
title: "computer cannot find suitable server to download"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by okkie on 2014-08-01
This is new to me and probably a stupid error.I am connected to the internet with Google but my computer cannot find server to help me install wine program. Pse help

---

### Post by Vladlenin5000 on 2014-08-01
Well... What exactly do you mean by "connected to the internet with Google"? Does it mean you can browse web pages? If so then how are you trying to install WINE?

---

### Post by okkie on 2014-08-01
I go to my software sources, select wine,circle arrow starts indicating installation and then stops and says 'server cant be found,check internet connection'

---

### Post by Vladlenin5000 on 2014-08-01
Try changing to the main server.

---

### Post by okkie on 2014-08-01
no go. I also have the newest beta version but will not install. Just tells me it contains untrusted packages.

---

### Post by Vladlenin5000 on 2014-08-01
So you AREN'T installing it from the software center?

---

### Post by ian-weisser on 2014-08-01
> **okkie said:**
> I am connected to the internet with Google

Please explain this clearly. We do not understand. What does it mean? Is it important?

> **okkie said:**
> I also have the newest beta version but will not install

Please explain more clearly and thoroughly. The newest beta version of *what*? You got it from exactly *where*?  You are trying to install exactly *how*?

You are not providing enough detail for us to be able to help you.

---

### Post by Rob Sayer on 2014-08-02
All of the above, plus I would strongly suggest you not use 3rd party sources (aka ppa's) to install anything if you don't really know what you're doing.  Just use the default repos (software sources in the install manager).

---

### Post by okkie on 2014-08-02
oK here we go. I now use a dongle for an internet connection which unfortunately hasn't or has, but cannot be detected by my system ,a program where I can go into and determine how much airtime or whatever else it might be called, I have available. I therefore accept that if I am connected to google, I am connected to the internet and can browse, download do updates and everything normal as I have been doing for many years now. If one can have a limited connection, that might be my problem and no one has ever told me about it.
This is how it started. I am a retired old man and for pleasure occationally gamble online without the trouble of driving long distances at night normally to get to a casino. 'Kings Chance Casino' recently upgraded their website, gave me a free thousand bucks bonus and I reloaded their new website which has to be opened by 'wine' obviously only to find that wine cannot open it. I then uninstalled wine to do a reinstall but unsuccessful. I then tried to download the latest 1.7 beta version of wine with the same result .
In conclusion,either I haven't got airtime although I can read mail, browse the internet etc and nobody has ever told me about the possible technical situation or something else.
Thanks for your assistance.

ps
My computer is up to date and I use synaptic as well from time to time if I feel like it

---

### Post by Vladlenin5000 on 2014-08-02
You're actually trying to use their software (for Windows) emulated trough WINE, not the website *per se*... By the way, there's an "Instant Play" option. Doesn't it work for you? I haven't tested, I can't but even if I could I wouldn't...

The thing about running Windows software in WINE is that most won't work at all, some will work partially - what you've been experiencing with the casino's software is eerily similar to iTunes, ie, it installs and runs but can't connect to the fruity store or even synchronize fruity devices - and finally a few games and productivity apps work acceptably.

It has nothing to do with internet traffic limitations or other factors. It simply is one of those that doesn't work.

---

### Post by Rob Sayer on 2014-08-03
"their new website which has to be opened by 'wine' obviously"

That is not only not obvious to me, it makes no sense to me.  Try Chrome.  It's better supported in linux.

---

### Post by Vladlenin5000 on 2014-08-03
Rob, read again my previous post (#10).
The OP is confusing the website with the client's software they have for download. The website isn't the problem, the Windows software is. The symptom is identical to iTunes in WINE: It installs and opens but can't connect to the fruity store (nor allows sync with fruity devices) so, basically, in the end it is nothing more than a glorified media player. In this case the casino's software seems to behave similarly which results in an useless piece of software.

---

### Post by okkie on 2014-08-04
I thank you once again and take note of everything,in fact I'm learning a lot. In summary there is nothing wrong with my internet connection and the problem lies with the casino's software which is not wine friendly as it has been for the last few years. I specifically mention this because from my first try to connect to various casinos years ago I have had no problems.What is peculiar now is that I cannot install wine from the software centre at all and also not from synaptic.The reason I use the latter from time to time is because it was recommended from years ago to do the 'things to do after installation' of an Ubuntu system and one gets used to using it and when I installed 13.04 it was recommended to install synaptic as a 'nice to have'.
Now back to my original problem, my computer will or cannot install wine at the moment for whatever use from any of the two sources and tells me to check my internet connection.
I get the impression that there is a clash or competition between the two sources which in the ubuntu spirit doesn't make sense but could be the case. What do you suggest? Thanks

---

### Post by ian-weisser on 2014-08-04
Software Center and Synaptic do not 'clash' or 'compete'. Both are merely different front-ends for the same package manager (apt), rather like different nozzles on a garden hose. They use the same sources, the same repositories, and the same package database.

Please open a Terminal window, try the following command, enter your password into the terminal when prompted, and copy/paste the ENTIRE output here within ```
 tags. The output may be quite long...to properly help you, we need it all.
[code]sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 3rdalbum on 2014-08-04
You are using Ubuntu 13.04? That's why you can't download any Ubuntu software. Ubuntu 13.04 is no longer supported and its software repositories have been taken down.

You need to upgrade to 14.04.

---

### Post by okkie on 2014-08-04
I thank you 3RDALBUM and ian. After sudo update/upgrade I had many failed packages to prove your point.
Now, without losing everything I've got can I upgrade to 13.04 and what is the best way to do it ?

---

### Post by Bashing-om on 2014-08-04
okkie; Hello;

As the original assistants are presently off-line, I will poke my nose into this.

The "best" way to upgrade is to back up your data, and do a fresh, clean install of 14.04.

Else there is a means to release upgrade from an End_Of_Life release, but it is not easy and the path is long and bumpy - a lot of bandwidth and time .
13.04 -> 13.10 -> 12.04 -> 14.04 to get to the current Long_Term_Support ( April 2019 ) release.
Release 13.10 is also End_Of_Life !

See:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
for the procedure to make those transitions.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by okkie on 2014-08-05
Thanks Bash, I will do the back-up and fresh install and give feedback.
Support appreciated.

---

### Post by 3rdalbum on 2014-08-05
> **okkie said:**
> Thanks Bash, I will do the back-up and fresh install and give feedback.
Support appreciated.

You can do a clean install without losing your files, actually. (It's still a good idea to back up anyway).

When you get to the point in the Ubuntu 14.04 installer where it asks if you want to erase a disk, install side by side etc, choose "Something Else". Click your Ubuntu partition and click Edit Partition.

Set the mount point to / from the drop down menu. Click okay.

If you already have a /home partition on 13.04, click it and click Edit Partition, and then change the mount point to /home.

Don't format any partitions. Click Forward and then click Continue when you are asked the big long confusing question!

Ubuntu will install, your existing files and settings will be saved. Your existing programs will be reinstalled at the end of the installation.

---

### Post by okkie on 2014-08-06
I started immediately after my last post and saved almost everything on dvd's exept about 20 gig music files.Pity I didn't wait.
Nevertheless new system is installed and now battling with Thunderbird as usual but things are looking good.
Whatever you do, enjoy! and thanks for the help

---

