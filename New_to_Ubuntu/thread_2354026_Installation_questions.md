---
title: "Installation questions"
date: 2017-02-27
forum: New to Ubuntu
---

### Post by natesnape on 2017-02-27
Hello Ubuntu team,

First I would like to thank you all for Lubuntu, I successfully installed it alongside Windows 10 an it's way faster than my previous OS, my question is that when I first try to install the OS, it ask me if I want to install the updates and to install additional software, I choose to opt out of those options, I was able to find how to install updates, however how do I install those additional software? Do I need to access the Ubuntu app database to do that?

---

### Post by Bucky Ball on 2017-02-27
Welcome. You may not need the additional software. The additional software was third-party proprietary software which you may or may not need or want.

Firstly, is everything working as it should? Your wifi is fine and screen resolution okay? Do you have any special video card? If it's working, all is working fine using the open-source drivers. That may be all your going to need. If not, check if there is anything else for hardware, go to 'Additional Drivers' and let us know what you see, if anything.

To know if there is anything you should be installing for software best to know details of the machine you are using. Mostly GPU and wireless card. But as mentioned, if it ain't broke ...

As for third-party codecs, etc., try installing ubuntu-restricted-extras and that should cover most of it.

---

### Post by oldrocker99 on 2017-02-27
Installation of software can be done several ways, from the terminal:```
sudo apt install [packagename]
```

The Lbuntu Software Center (which should be preinstalled) is the best way for a beginner. It shows categories and gives a brief description of each package.

---

### Post by QIII on 2017-02-27
Hello and welcome to the Forums!

We are all quite happy to receive a "Thank you" now and again, but we can't take credit for Ubuntu or Lubuntu.  This is a volunteer user Forum.  We, including the Staff, are all volunteer users just like you and not employed by Canonical.

Besides, rather than "Thank you" we'd much prefer pastries and chocolates.  :)

---

### Post by Bucky Ball on 2017-02-27
> **QIII said:**
> We are all quite happy to receive a "Thank you" now and again, but we can't take credit for Ubuntu or Lubuntu.

Besides, rather than "Thank you" we'd much prefer pastries and chocolates.  :)

^^^
And this. :)

---

### Post by RobGoss on 2017-02-27
You can also use synaptic package manager, it's a faster way to install software. If everything is working as it should I wouldn't worry about the third-party software it's presented to us at the beginning of all installations so we don't  have to do it later

---

### Post by natesnape on 2017-02-27
I'm using an NVIDIA Graphic card, and would want to play some games on my old PC, like Darkest Dungeon, and Borderlands 2, do I still need to install the proprietary drivers, and if yes, are the drivers inside the "Additional Drivers" the one to use? The PC is connected via wired so I'm good with my network, I haven't tested the sounds yet though, the main reason why I didn't choose those options and installed it alongside my windows 10 is because I want the fastest way to install Lubuntu, once everything is good I might remove Windows 10 completely and just stick with just Lubuntu.

> **QIII said:**
> Hello and welcome to the Forums!

We are all quite happy to receive a "Thank you" now and again, but we can't take credit for Ubuntu or Lubuntu.  This is a volunteer user Forum.  We, including the Staff, are all volunteer users just like you and not employed by Canonical.

Besides, rather than "Thank you" we'd much prefer pastries and chocolates.  :)

If your from the Philippines mate, and near my locations, I can give you some chocolates. :)

> **Bucky Ball said:**
> As for third-party codecs, etc., try installing ubuntu-restricted-extras and that should cover most of it.

Yep, I think that's the one.

---

### Post by poorguy on 2017-02-28
I have found this always helped me to finish a new installation of Lubuntu.

[https://sites.google.com/site/easylinuxtipsproject/first-lubuntu](https://sites.google.com/site/easylinuxtipsproject/first-lubuntu)

---

### Post by natesnape on 2017-02-28
> **poorguy said:**
> I have found this always helped me to finish a new installation of Lubuntu.

[https://sites.google.com/site/easylinuxtipsproject/first-lubuntu](https://sites.google.com/site/easylinuxtipsproject/first-lubuntu)


Thanks mate! You're a life saver.

---

### Post by poorguy on 2017-02-28
> **natesnape said:**
> Thanks mate! You're a life saver.
You are welcome. ;)

---

### Post by natesnape on 2017-02-28
[HTML][/HTML]> **poorguy said:**
> You are welcome. ;)

The same guide works with 16.10 right? I'm just going to look at the installed apps to be sure. :)

---

### Post by Bucky Ball on 2017-02-28
> **natesnape said:**
> [HTML][/HTML]

The same guide works with 16.10 right? I'm just going to look at the installed apps to be sure. :)

Just a note: Why 16.10? If you have no good reason for installing it, go for a long-term support release, 16.04 LTS. 16.10 is out of support in the middle of this year at which point you will need to install 17.04. Non-LTS releases are interim releases and have nine months support, effectively putting you on a six monthly upgrade cycle. Boring. 

LTS generally very stable and five years support (three for Lubuntu and Xubuntu), Lubuntu 16.04 LTS supported until April 2019.

For what it's worth ... good luck. ;)

PS: Some of the stuff on that guide link is definitely non-essential. ;)

---

### Post by mörgæs on 2017-02-28
Yes, Lubuntu is in so slow development that 16.04 is close to 16.10. I expect the guide to work for both. 
Every new Lubuntu release has bug fixes as main focus, not introducing new functionality.

---

### Post by natesnape on 2017-02-28
> **Bucky Ball said:**
> Just a note: Why 16.10? If you have no good reason for installing it, go for a long-term support release, 16.04 LTS. 16.10 is out of support in the middle of this year at which point you will need to install 17.04. Non-LTS releases are interim releases and have nine months support, effectively putting you on a six monthly upgrade cycle. Boring. 

LTS generally very stable and five years support (three for Lubuntu and Xubuntu), Lubuntu 16.04 LTS supported until April 2019.

For what it's worth ... good luck. ;)

PS: Some of the stuff on that guide link is definitely non-essential. ;)


When I first got a glimpse of Lubuntu the version on it's main page is the 16.10, that's what I downloaded. All the features inside 16.04 are included inside 16.10, and the upcoming 17.04 correct? I'm pretty new to this and I'll gladly accept all help and answers.

---

### Post by poorguy on 2017-02-28
The tweaks in the guide should work for any Lubuntu 16.XX distro.

I would as others have already suggested to go with Lubuntu 16.04 LTS as support is for 3years.

Also not every tweak needs to be used.
I sent that as a guide for "installing ubuntu-restricted-extras" as was suggested by BuckyBall.

I suggest only using the tweaks that are necessary and not every tweak in the guide is always needed.
Just make sure you understand the tweaks that you think you want to apply before applying them.

---

### Post by poorguy on 2017-02-28
Here is a link to Lubuntu 16.04 LTS iso download.

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

---

### Post by natesnape on 2017-02-28
> **poorguy said:**
> Here is a link to Lubuntu 16.04 LTS iso download.

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)


I have that link, but thank you for providing it to me. :)

I think I'm good with the latest release, I was using Windows since Windows XP and I'm used to downloading updates every now and then, Upgraded my XP to 7, then to Window 10. It's just that my PC is an Old Machine a Dual core with 4GB or RAM, hence the reason why I installed Lubuntu, so I'm good with updating every 6 to 9 months if it's just a matter of doing the software update thing on the desktop, still a lot to learn though.

---

### Post by poorguy on 2017-02-28
Here is another link you may find useful.

[https://linuxjourney.com/](https://linuxjourney.com/)

---

### Post by natesnape on 2017-02-28
> **poorguy said:**
> Here is another link you may find useful.

[https://linuxjourney.com/](https://linuxjourney.com/)

Thanks again mate!

Another thing about installation of OS, I've installed Lubuntu alongside windows 10 on my C drive, I also have a a D drive, what I want to do now is to format my D drive to EXT4, transfer my Lubuntu on the D drive, and keep my windows 10 on my C drive, is that possible without reinstalling the OS itself?

---

### Post by mörgæs on 2017-02-28
> **natesnape said:**
> I think I'm good with the latest release, I was using Windows since Windows XP and I'm used to downloading updates every now and then, Upgraded my XP to 7, then to Window 10. It's just that my PC is an Old Machine a Dual core with 4GB or RAM, hence the reason why I installed Lubuntu, so I'm good with updating every 6 to 9 months if it's just a matter of doing the software update thing on the desktop, still a lot to learn though.

16.10 is definitely a good choice but I recommend a fresh install (not an online upgrade) when [support]("https://en.wikipedia.org/wiki/Lubuntu#Releases") runs out.

---

### Post by natesnape on 2017-02-28
> **mörgæs said:**
> 16.10 is definitely a good choice but I recommend a fresh install (not an online upgrade) when [support]("https://en.wikipedia.org/wiki/Lubuntu#Releases") runs out.

Why is that?

---

### Post by mörgæs on 2017-02-28
You already have my opinion at hand: Second link in my signature.

---

### Post by poorguy on 2017-02-28
> **natesnape said:**
> 
 					[IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **mörgæs** 					[[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13613955#post13613955") 				
 				16.10 is definitely a good choice but I recommend a fresh install (not an online upgrade) when [support]("https://en.wikipedia.org/wiki/Lubuntu#Releases") runs out.


Why is that?
An online upgrade can be problematic where a fresh install most of the time will install and run without problems although problems can happen with fresh installs. No guarantees.

---

### Post by natesnape on 2017-02-28
> **poorguy said:**
> An online upgrade can be problematic where a fresh install most of the time will install and run without problems although problems can happen with fresh installs. No guarantees.

If I do a fresh install I'll loose all my installed apps right?

---

### Post by RobGoss on 2017-02-28
> If I do a fresh install I'll loose all my installed apps right

Yes, but they should be pretty simple to reinstall them I would just make a note of the ones you use the most and just install them again

---

### Post by natesnape on 2017-02-28
> **RobGoss said:**
> Yes, but they should be pretty simple to reinstall them I would just make a note of the ones you use the most and just install them again

That's a bit odd, that might be the reason why most of you guys recommends the LTS version.

---

### Post by Bucky Ball on 2017-02-28
> **natesnape said:**
> That's a bit odd, that might be the reason why most of you guys recommends the LTS version.

Not completely. LTS releases are generally more stable. They are around for a lot longer and therefore that is only logical. Recommended for any situation where you can't afford or have downtime; i.e. work computer (production machines) and any machine that must be stable and reliable. Interims can be a tad 'experimental'.

Whatever might be the case in Windows-world, the latest is NOT always the greatest here. There's really not much difference between 16.04 LTS and 16.10 (apart from the extra support). You will not be updating interim releases, you will be upgrading the OS, as in replacing 16.10 with the next. Net upgrades, as mentioned, can be problematic, especially if your machine is a long way from 'vanilla', i.e. you have added PPAs and drivers, etc ...

Good luck.

---

### Post by natesnape on 2017-02-28
> **Bucky Ball said:**
> Not completely. LTS releases are generally more stable. They are around for a lot longer and therefore that is only logical. Recommended for any situation where you can't afford or have downtime; i.e. work computer (production machines) and any machine that must be stable and reliable. Interims can be a tad 'experimental'.

Whatever might be the case in Windows-world, the latest is NOT always the greatest here. There's really not much difference between 16.04 LTS and 16.10 (apart from the extra support). You will not be updating interim releases, you will be upgrading the OS, as in replacing 16.10 with the next. Net upgrades, as mentioned, can be problematic, especially if your machine is a long way from 'vanilla', i.e. you have added PPAs and drivers, etc ...

Good luck.

Thank's for the info, I'm using Lubuntu right now, and have followed the steps on [https://sites.google.com/site/easylinuxtipsproject/first-lubuntu](https://sites.google.com/site/easylinuxtipsproject/first-lubuntu) on how to install ubuntu extras, I was able to do the process up to [COLOR=#006000][FONT=monospace]sudo dpkg-reconfigure libdvd-pkg [/FONT][/COLOR] and my name on the terminal appeared, however when I tried to click the link on how to install JAVA, my PC froze, I waiting for 10 minutes and nothing happened? Restarted my PC, installed JAVA, however I want to know if there's a way to check if those other items where installed, restricted and playing encrypted DVD's, can I run those command again to try and install them?

My bad, Tried to rerun the commands and everything was installed correctly, I hope. Had an issue with Nvidia as well, tried to install the graphics driver from Additional Drivers, and after I restarted my PC my resolution was 640x480, did a quick googling and was able to resolve it via re-running the installation via the command line. I was able to install Chrome, and Spotify, tried to install Midori as well but the videos are not working will look on that later, so far so good.

---

### Post by RobGoss on 2017-03-01
> That's a bit odd, that might be the reason why most of you guys recommends the LTS version.

As mentioned the** LTS** releases are the ones with the longest support with that said, for anyone coming to Linux as a new user and installing let's say **16.10,** and having to upgrade a few months down the road can be problematic so we just try to save you the trouble of having to do that

---

### Post by sudodus on 2017-03-01
I suggest that you start from Lubuntu 16.04.1 LTS, the first point release (the .1 in the version number). It has the same kernel series as the original 16.04 LTS (the xenial or 4.4 series), it is debugged and polished, and needs less updating and upgrading. An alternative is Lubuntu 16.04.2 LTS (with the yakkety or 4.8 kernel series). The application program versions are pretty much the same in these two point releases. 16.04.2 LTS needs even less updating & upgrading after installation. Try them live, and install the one that works best with your computer.

---

### Post by Bucky Ball on 2017-03-01
Don't know what you're trying or what's on the link, but

```
sudo apt install lubuntu-restricted-extras
```

... is generally all that is needed. Where is the problem when you run that command?

---

### Post by natesnape on 2017-03-01
> **sudodus said:**
> I suggest that you start from Lubuntu 16.04.1 LTS, the first point release (the .1 in the version number). It has the same kernel series as the original 16.04 LTS (the xenial or 4.4 series), it is debugged and polished, and needs less updating and upgrading. An alternative is Lubuntu 16.04.2 LTS (with the yakkety or 4.8 kernel series). The application program versions are pretty much the same in these two point releases. 16.04.2 LTS needs even less updating & upgrading after installation. Try them live, and install the one that works best with your computer.

Thanks! How do I download the 16.04.2 version, all I can get is the 16.04.1 LTS one.

> **Bucky Ball said:**
> Don't know what you're trying or what's on the link, but

```
sudo apt install lubuntu-restricted-extras
```

... is generally all that is needed. Where is the problem when you run that command?

Yep everything is good now, I hope, cause when I tried the command again it said no updates, that means that the restricted-extras were all installed correct?

---

### Post by sudodus on 2017-03-01
> **natesnape said:**
> Thanks! How do I download the 16.04.2 version, all I can get is the 16.04.1 LTS one.

This general link brings you 'everything': [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

In particular, see this link: [cdimage.ubuntu.com/lubuntu/releases/16.04.2/release](http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/) and scroll down ...

***Edit:*** check with the string in the file MD5SUM at the same link.

---

### Post by natesnape on 2017-03-01
> **sudodus said:**
> This general link brings you 'everything': [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

In particular, see this link: [cdimage.ubuntu.com/lubuntu/releases/16.04.2/release]("http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/") and scroll down ...

***Edit:*** check with the string in the file MD5SUM at the same link.

Thank you mate! You're a life saver.

Day 5 and everything seems to be running fine, just encountering random screen freezes, where I can't do anything with the screen but the mouse pointer is working, not sure if that's an issue with my Graphic card.

---

### Post by Bucky Ball on 2017-03-02
> **natesnape said:**
> ... encountering random screen freezes, where I can't do anything with the screen but the mouse pointer is working, not sure if that's an issue with my Graphic card.

You should probably mark this thread as solved (see last link in my signature at the bottom of this post) and post a new thread with a descriptive title and find out. I would call that a problem.

Good luck. ;)

---

### Post by natesnape on 2017-03-03
Marking this thread as solved, thanks peeps!

---

