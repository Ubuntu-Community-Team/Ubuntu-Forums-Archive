---
title: "(K)ubuntu - Full tutorial"
date: 2007-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Dedoimedo on 2007-06-06
Hello,

I have written a step-by-step text and image tutorial of (K)ubuntu Linux 6.06 Dapper Drake.
The tutorial includes partitioning, basic configurations, setting up of network, sharing, graphic cards, package management, and more.

I think it is very suitable for new Linux users.

I wrote it some time ago, but all the concepts still apply.

[http://www.dedoimedo.com/computers/install_kubuntu.html](http://www.dedoimedo.com/computers/install_kubuntu.html)

Best regards,
Dedoimedo

---

### Post by rich.bradshaw on 2007-06-06
Don't use <br> use <p> and </p> at the beginning and end of each paragraph. <br> is a line break, <p></p> describes a paragraph.

"The     latest distribution 6.06 is called Dapper Drake."

Perhaps better to say that the version is made up of two parts, the first number corresponding to the year, and the second number meaning the month. Dapper Drake 6.06 was therefore released in the 6th month of 2006. You will want to install the newest stable version you can, so blah blah blah etc...

This way it doesn't matter that the tutorial will get old, it will still make sense.

Don't encourage people to use Automatix without them knowing the risks. In Feisty Automatix is redundant, everything can be installed via adept/add/remove programs.

Envy is a better way to install graphics drivers for nVidia or ATI - [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Dedoimedo on 2007-06-06
Hello,

Thanks for the feedback.
I have written this one some 10 months ago. It might some polishing.
I am considering adding update section to each of the tutorials.

Regarding the html, I have divided different sub-topics with titles rather than paragraphs save for the code examples.

Thanks again,
Dedoimedo

---

### Post by rich.bradshaw on 2007-06-06
Yeah, it looks good though, clear explanation etc.

Might want to add about restricted-extras etc. Instead of using Automatix, you could give cli to install codecs, flash, java, ntfs-3g etc, all these are in repositories now.

Beryl/Compiz could get a mention - a lot of people seem to not get that emerald is only for gnome, and that aquamarine is it's equivalent in KDE.

A bit showing the network transparency in Konqueror might be nice as well: i.e. you can type [ftp://someaddress](ftp://someaddress) and it will work seamlessly.

Top KDE apps such as amaroK, K3B, etc might be good as well.

How to change from Ubuntu to Kubuntu (psychocats link possibly) would be good.

Lot's of suggestions, but don't let that distract from the fact that it's a clear and complete article.

---

### Post by Dedoimedo on 2007-06-06
Hello,

I have another article called A (cool) list of Linux tools (it's there under computer software & security), where Amarok, K3B and other apps are mentioned. Kind of delivering Linux in small bits ... :) Makes for an easier transition that way. But I will definitely update the article with the suggestions you mentioned + due credits.

I do not think Beryl is for people installing a Linux distro the first time. It's a beta and could cause some damage. Not something a new user should experience on his/her first day.

Thank you for your suggestions.

Best regards,
Dedoimedo

---

### Post by Dedoimedo on 2007-06-15
Hello,

Following advice by people here and via email, I have changed and updated the article.

Here's the changelog:

- Added explanation regarding article's validity over time
- Added comparison between KDE and GNOME environments
- Added mini table of contents with links to major chapters in the article
- Added sub-titles for major chapters in the article
- Added command to backup xorg before installation of graphic card drivers
- Added envy script as option for installation of graphic card drivers
- Added links to Edgy and Feisty Starter Guides
- Added links to psychocats.net and Kubuntu Desktop Guide
- Added links to some of my other Linux articles (including Linux command line tutorial)
- Added chapter about transition from Windows to Linux, with tips about codecs, java and flash
- Added chapter about most common KDE applications, with brief introduction to the most popular ones

- Fixed minor spelling mistakes
- Fixed minor phrasing and semantics errors

Enjoy,
Dedoimedo

---

### Post by KrazyPenguin on 2007-06-15
Have you tried [www.UbuntuGuide.org](www.UbuntuGuide.org) ???

Lots of people, translators , etc.

You might want to join ( I did) and add some stuff to it.

What Ubuntu really needs is a startup Tutorial which can be included on the livecd to show users visually how to set up their Ubuntu Box.

Also, I would like to see something like UbuntuGuide but broken down into pages with step by step images.

Anyway, keep up the good work ;-)

---

### Post by Dedoimedo on 2007-06-15
Hello,
Thanks for the feedback. I'll definitely check the participation at UbuntuGuide.
Cheers,
Dedoimedo

---

### Post by dkaddict on 2007-06-16
Hi,

Great guide m8. It may hellp my mother to take the plunge and stick the Kubuntu Edgy live cd I gave her into her cd drive:popcorn:

A suggestion for useful info.

It took me ages to work out how to enable the hot plugging of my USB devices. After a couple of months, I gave up trying. Kubuntu would read them if I had plugged before booting up my notebook so I resigned to having to shut down, plug, and boot. By chance, however, I came across a post about APCI and the /boot/grub/menu.lst. I tried the 'noapic' option (I had seen stuff about APIC or APCI in a 'dmesg' output and put 2 and 2 together) and my devices all worked exactly how they did in Windows.:KS

Later on, I got a wireless router. My built in wireless card, however, wouldn't work with the 'noapic' option. I had another look for /boot/grub/menu.lst options and noapic etc and found the 'irqpoll' option. Bingo. With 'irqpoll' I had wireless and USB. Well happy about that m8!!!:cool:

Ok, I managed to sort this out with a bit of perserverance and luck. My mother and others like her, however, would have a nightmare trying to figure such a dilemma. Personally, I feel that there is a need for a well written how2 with regards to this 'noapic' 'irqpoll' thing. Maybe you can add it to your guide? 

Am I suggesting something which is too rare an occurence, and/or, over complicated for a newb guide? I myself am a new linux user so wouldn't dream of posting how2s here.

peace

dk

---

### Post by Dedoimedo on 2007-06-16
Hello,

First, anything you managed to solve and post it - will help someone else. So you should do it.

Second, the idea of the several tutorials I've written is to get people started, nice and easy, and get working with Linux. The goal is to get them going - but they must continue from there.

It might be frightening to some new users to start playing and editing the grub menu. I do have a separate grub post that I'll upload in a few weeks.

Thanks,
Dedoimedo

---

### Post by dkaddict on 2007-06-18
Nice one,

I will try to make a post explaining how I solved the USB/APIC problem. If I leave anything important out or anything like that I'm sure someone will put me right.

Take it easy m8

dk

---

