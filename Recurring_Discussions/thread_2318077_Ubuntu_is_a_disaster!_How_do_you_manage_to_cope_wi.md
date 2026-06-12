---
title: "Ubuntu is a disaster! How do you manage to cope with it?"
date: 2016-03-22
forum: Recurring Discussions
---

### Post by sanssadness on 2016-03-22
I've been using Ubuntu for some time now, and I can't help but notice the endless plethora of problems I'm faced with. Most (but not all) are non-fatal, and the rest are simply annoying. Here are a few examples.

There was a MAC address cloning bug that still remains unfixed. It makes you unable to spoof your MAC address when you're connecting to a hotspot.

On a newer computer, I got no sound even though everything appeared to be working correctly. Nothing was muted in alsamixer, and the hardware obviously has no problems (it works perfectly in Windows). Ubuntu 14.04 and ubuntu 16.06 both failed. I tried to install the latest Alsa driver, but even though a help page clearly said there was supposed to be a .deb file, there wasn't. I tried to compile the tar.gz's extracted contents, and it errored out with a bug so obscure not even Google could find anything about it. See this post for details: [http://ubuntuforums.org/showthread.php?t=2317724&p=13459144#post13459144](http://ubuntuforums.org/showthread.php?t=2317724&p=13459144#post13459144)

In response to the sound problem, someone suggested trying 16.04 beta. A sensible suggestion; perhaps Skylake motherboards are too new. But then, Startup Disk Creator, when used on Ubuntu 14.04 to create a bootable USB drive for Ubuntu 16.06, makes the disc unbootable. I saw people reporting this bug from at least 4 years ago, and it's still not fixed for some reason!

I had to burn the image to a DVD to get it to work. When I finally managed to do this, the installation hung at the purple screen. nodemoset didn't fix it.

Disks, a program included by default with Ubuntu, frequently runs into problems when formatting disks.

On Ubuntu 12.04, dragging icons to the desktop results in a lock icon on them. You then have to change the ownership of the file in order to even get it to run. The casual user who just finds a shortcut on the dash and then drags it to a more easily accessible spot would never think to try this! On Android you drag an icon out, and it just works! You wouldn't need to manual to read (not that there is one for Ubuntu) to figure out how to unlock those icons.

Desktop icon arrangement, compared to Google or even Android, is stupefyingly unintuitive. There's no grid to line up to, and the icons don't stop at the places you've dragged them to. Half a decade later? Same problem.

These are only a few of the numerous problems I've run into. And this is on 12.04 and 14.04; stable versions of probably the most wideless used Linux distro. I am not fond of Windows, but I have to get my work done, and these problems aren't helping when I can't fix one even after wasting a week of time Googling for solutions. There's no official reference to turn to for those problems; just experienced users who seem to have spent even more time than I have poking and prodding at every aspect of the operating system until they find a solution. How I wish there was a book that had all the answers. I don't care how gigantic it is. I would read it if it was a panacea. How do they do it? I could grow old just fixing the most basic problems. Yet these users seem to have read every man page in existence.

I could list countless other problems that I've encountered over the years. These few don't even begin to do justice to the frustration I've endured; the countless man-hours I've wasted trying to fix the most simple of problems just to get my work done. Just when I think I've found some stability - some peace of mind - with an LTS version, I either need a new computer or a new version is released, and the nightmare begins all over again. My blood pressure has probably risen 20 points just from the problems of the last 3 days; is it really too much to ask just to get my speakers to play sound?

Yet there appears to be a thriving community of users. Unless some massive Skynet is faking these posts, hypertension and frustration have apparently not yet wiped out Ubuntu users. So how do the rest of you manage?

---

### Post by vasa1 on 2016-03-22
> **sanssadness said:**
> I've been using Ubuntu for some time now, ...
But you've posted in the New to Ubuntu section. Didn't have to read further. Your title says it all. Good luck.

---

### Post by sanssadness on 2016-03-22
"New" is a relative word. Experience level varies widely depending on how much time you can set aside from your life to learn every obscure facet of the os. And that's assuming the bugs don't kill you from sheer frustration first. This distro markets itself as user-friendly, so one would expect better.

---

### Post by ian-weisser on 2016-03-22
You have chosen to participate in an enormous open-source project. We expect you to...participate. To help improve the software and the project itself.
You are not our customer. We are not your vendor. We are fellow participants - your peers.

Your help to triage, patch, test, review, document, support, or otherwise participate to solve these issues is very welcome.

---

### Post by sanssadness on 2016-03-22
The last time I reported a bug (the MAC cloning one) was years ago, and the problem still wasn't fixed the last time I checked, even though many posters confirmed the bug. The download link asks for donations: Is that not a form of participation too?

All I want is a stable work environment; one free of major problems. I understand that might be too much to ask for a "new" new user, but I gave Ubuntu a few years, working around the minor problems wherever possible. I think I've done my part.

---

### Post by 1clue on 2016-03-22
@sanssadness,

Did you report the bug to a bug database, or did you complain about it on a forum?  Developers don't generally get their task list from a forum.

Drivers generally come from upstream. Some distros do a lot of driver work, others take upstream and some contributions by the distro users themselves.  In the case of upstream, adding a bug here doesn't really change anything.  You would need to go upstream for that.

Canonical spends a lot of time tweaking the user experience for *buntu, but bleeding edge hardware is, through the nature of Open Source, a bit light on support.

Linux and all the free/open source software typically installed with it is NOT commercial, meaning there is nobody overseeing the entire software base and coordinating development.  Each software package has its team, some have commercial support and some have a guy who's tired of waiting for a driver who gives it a whirl. Some have hardware vendor support and others do not. As a general rule, people installing any Linux distro need to investigate the hardware support before they buy the hardware. If being a developer or a tester is not appealing to you, then choose vendors who cooperate with Open Source or who provide their own drivers for Linux.

While there is much financially backed software development for Linux, there is a profound base of coding by volunteers who are neither paid nor intent on providing a commercial-quality product. Generally the volunteers want to make it work for their personal use case, not everyone else's.

---

### Post by sanssadness on 2016-03-22
I reported it to Launchpad. It's a duplicate of this bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752)

Years later, the status is still confirmed. I get it, Ubuntu isn't  commercial. But programming isn't my area of expertise. My involvement  with Ubuntu is as a working professional rather than an enthusiast with  endless amounts of free time to fix any problem at will, so I can't  really write a driver that would solve the problems of a few thousand  people even if I would love to volunteer some free time; it's just not  my field.

I get it. Ubuntu isn't commercial. Nobody is getting paid to help me get  it to work. But there's no "bug bounty" feature. I can't pay for a  specific bug to get fixed. People donate, but not for their specific  problem; just to help the project overall. And I might do more to help  the project if the basics were at least working properly. I'm not a fan  of Windows. In fact, I hate it. But it at least helps me get my work  done. When I spend days on end just to get sound to work properly, it's  time I will never get back.

Imagine you had a friend or neighbor  who was computer literate but doesn't have the time to fix major  problems when they pop up. They support the open source philosophy, but  they need something that just works. How would you make the case to them  that Ubuntu is the right solution?

---

### Post by papibe on 2016-03-22
Not a support thread. Moved to **Ubuntu, Linux and OS Chat**.

---

### Post by mastablasta on 2016-03-23
This Will go into recurring soon probabbly.

> **sanssadness said:**
> 
There was a MAC address cloning bug that still remains unfixed. It makes you unable to spoof your MAC address when you're connecting to a hotspot.?
Obviously not enough people are annoyed by this bug. or perhaps there is a workarround?!

> 
On a newer computer, I got no sound even though everything appeared to be working correctly. Nothing was muted in alsamixer, and the hardware obviously has no problems (it works perfectly in Windows). Ubuntu 14.04 and ubuntu 16.06 both failed. I tried to install the latest Alsa driver, but even though a help page clearly said there was supposed to be a .deb file, there wasn't. I tried to compile the tar.gz's extracted contents, and it errored out with a bug so obscure not even Google could find anything about it. See this post for details: [http://ubuntuforums.org/showthread.php?t=2317724&p=13459144#post13459144](http://ubuntuforums.org/showthread.php?t=2317724&p=13459144#post13459144)


Buy Linux certified hardware to avoid such issues.There is also Linux preloaded hardware available.

> 
In response to the sound problem, someone suggested trying 16.04 beta. A sensible suggestion; perhaps Skylake motherboards are too new. But then, Startup Disk Creator, when used on Ubuntu 14.04 to create a bootable USB drive for Ubuntu 16.06, makes the disc unbootable. I saw people reporting this bug from at least 4 years ago, and it's still not fixed for some reason!

Solution is simple - do a md5sum check if all is good, use another USB image "bruner". plenty to go arround.

> 
I had to burn the image to a DVD to get it to work. When I finally managed to do this, the installation hung at the purple screen. nodemoset didn't fix it.

Again looks lke unsupported hardware. or bad install. or bad image?!

> 
Disks, a program included by default with Ubuntu, frequently runs into problems when formatting disks.
Isn't gparted used for formatting?!

> 
On Ubuntu 12.04, dragging icons to the desktop results in a lock icon on them. You then have to change the ownership of the file in order to even get it to run. The casual user who just finds a shortcut on the dash and then drags it to a more easily accessible spot would never think to try this! On Android you drag an icon out, and it just works! 

Desktop icon arrangement, compared to Google or even Android, is stupefyingly unintuitive. There's no grid to line up to, and the icons don't stop at the places you've dragged them to. Half a decade later? Same problem.


You are not supposed to have icons on Ubuntu desktop, but in launcher. and even there only the most used ones. for the rest  - Dash is there.  desktop is supposed to be emtpy. which is why you ran into trouble. if you want the classic widnows desktop experience try Kubuntu, Xubuntu or Mate & Cinnamon desktops instead. there also a few others arround

> 
You wouldn't need to manual to read (not that there is one for Ubuntu) to figure out how to unlock those icons.

Now that's a terrible thing to say:
 community made manual: [https://ubuntu-manual.org/](https://ubuntu-manual.org/)
+
ubuntu wiki: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
+
official documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
+
there is Cannonical support available

> **sanssadness said:**
> 
 Imagine you had a friend or neighbor  who was computer literate but doesn't have the time to fix major  problems when they pop up. They support the open source philosophy, but  they need something that just works. How would you make the case to them  that Ubuntu is the right solution?

i would get them to buy a linux certified PC or a Linux preloaded PC if they wanted to use Linux. those tend to just work. and not much issue son those to solve.

---

### Post by buzzingrobot on 2016-03-23
If I had a friend who made an honest and informed effort to use Ubuntu, or any other distribution, and found it lacking, I'd suggest that friend consider Windows and OS X as the only other viable alternatives.  Yes, it's nice when things "just work".  Often, however, they don't, on any platform.

---

### Post by sammiev on 2016-03-23
> **buzzingrobot said:**
> If I had a friend who made an honest and informed effort to use Ubuntu, or any other distribution, and found it lacking, I'd suggest that friend consider Windows and OS X as the only other viable alternatives.  Yes, it's nice when things "just work".  Often, however, they don't, on any platform.

+1 

Always said, use what works for you.

---

### Post by neu5eeCh on 2016-03-23
In my experience, any Linux OS has more bugs and challenges than either Windows or Apple.

However, there *are* bugs in Apple and Windows software. (I was just visiting a used bookstore having problems with their accounting software. A free-lance tech support technician was there. The store owner was getting billed by both the technician *and* the software maker--probably all added up to well over two hundred dollars. This was on Windows.) The difference is that over the years I've been able to resolve 99 out of a 100 bugs via web-searches and with help from the "Linux" community. With Apple and Windows, one either relied on a Knowledge Base, which frequently didn't solve the problem, or one had to _pay a company to solve *their* *own* bug_. Think about that. There's the up front cost of software and then the customer is milked for "software development". It's a great system if you're the company.

One of the reasons I switched to Linux is that more and more companies (Microsoft and Apple namely) were no longer supporting their products without a credit card number. I felt like I was being ripped off.

So, when I read posts like yours I don't feel much sympathy. Pick your poison. Use Windows or Apple if you like. When you run into a bug, give 'em a call and have your credit card ready.

---

### Post by coldraven on 2016-03-23
+1 for VTpoet 
Don't forget that windows 10 costs money and comes with no useful utilities, not even a game of Solitaire.

---

### Post by PaulW2U on 2016-03-23
> **sanssadness said:**
> I've been using Ubuntu for some time now, and I can't help but notice the endless plethora of problems I'm faced with. Most (but not all) are non-fatal, and the rest are simply annoying.
yep, I have a list too. 
> **ian-weisser said:**
> You have chosen to participate in an enormous open-source project. We expect you to...participate. 
ian-weisser, that music to my ears. :)

Don't complain. Help fix it!
> **mastablasta said:**
> This Will go into recurring soon probabbly.
I've stopped saying that as I've been proved wrong much too often. :)
> **VTPoet said:**
> In my experience, any Linux OS has more bugs and challenges than either Windows or Apple.
And there are documented procedures for **anyone** to help fix those bugs.
> **coldraven said:**
> Don't forget that windows 10 costs money and comes with no useful utilities, not even a game of Solitaire.
I don't know about that but despite the thousands of bugs that are reported to be in Ubuntu and its flavours I still have something that is has cost me nothing and is very usable on all of my my four laptops (and many other items of hardware previously).

---

### Post by QIII on 2016-03-23
Moved to Recurring.

---

### Post by 1clue on 2016-03-23
> **sanssadness said:**
> I reported it to Launchpad. It's a duplicate of this bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752)

Years later, the status is still confirmed. I get it, Ubuntu isn't  commercial. But programming isn't my area of expertise. My involvement  with Ubuntu is as a working professional rather than an enthusiast with  endless amounts of free time to fix any problem at will, so I can't  really write a driver that would solve the problems of a few thousand  people even if I would love to volunteer some free time; it's just not  my field.

I get it. Ubuntu isn't commercial. Nobody is getting paid to help me get  it to work. But there's no "bug bounty" feature. I can't pay for a  specific bug to get fixed. People donate, but not for their specific  problem; just to help the project overall. And I might do more to help  the project if the basics were at least working properly. I'm not a fan  of Windows. In fact, I hate it. But it at least helps me get my work  done. When I spend days on end just to get sound to work properly, it's  time I will never get back.

Imagine you had a friend or neighbor  who was computer literate but doesn't have the time to fix major  problems when they pop up. They support the open source philosophy, but  they need something that just works. How would you make the case to them  that Ubuntu is the right solution?

You can, however, find the specific package that has the problem and get an email.  You can contact the upstream project and discuss ways to get the bug fixed, and offer your bug bounty that way.

You can find someone on odesk, get them to code a patch and submit the patch to upstream, or just keep it yourself.

There are a lot of options here. Some of them require money and others do not.  If nobody who is developing is interested, find a way to get their interest.

---

### Post by Bashing-om on 2016-03-23
@; sanssadness; Et al .

I run old hardware, and have installed 'buntu on many other old hardware systems for clients.
I have never had a problem. I discontinued Windows with XP service-pack 2 - and have never looked back. In ubuntu, applications maybe not as polished as that of say Windows, but - gets the job done .

In my opinion, ubuntu is a system, and if one remains within that system there are no problems. Get out of the system and it is on you to "make it work " . Bleeding edge hardware is a collaboration between the hardware manufactures and commercial interest to satisfy the demands of the buying public - generally proprietary. Open source, we use what is available.

[INDENT][INDENT]that's my story, and I am sticking to it
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2016-03-23
> There was a MAC address cloning bug that still remains unfixed. It makes you unable to spoof your MAC address when you're connecting to a hotspot.
I reckon that 99% or more of Ubuntu users have never had a need to spoof a MAC address.  If this is the kind of problem that you think makes Ubuntu (or indeed any Linux distribution) a "disaster," you must spend your time with a very different set of computer users than I do.  I, too, am a professional, and I'm in that 99%.

---

### Post by Geoffrey_Arndt on 2016-03-23
And it would have been nice for the OP to advise he is not even using the Unity desktop in the first place, and to update readers that sound issue was hardware malfunction.    

Let me reiterate - - especially for former Windows "Power Users" . . who have by far the hardest time transitioning to Linux - -  if you really want an "apples to apples" comparison of Windows & Ubuntu . . . . just get it pre-installed on a machine designed and tested for Linux.   My System76 Galago Ultra Pro laptop has zero issues with Ubuntu (and the last thing I want on my desktop are icons - - if I already have all I need in the Launcher - - which is a perfect solution IMHO).

---

### Post by sanssadness on 2016-03-24
[QUOTE=Geoffrey_Arndt]And it would have been nice for the OP to advise  he is not even using the Unity desktop in the first place, and to update  readers that sound issue was hardware malfunction.    

Let me reiterate - - especially for former Windows "Power Users" . . who  have by far the hardest time transitioning to Linux - -  if you really  want an "apples to apples" comparison of Windows & Ubuntu . . . .  just get it pre-installed on a machine designed and tested for Linux.    My System76 Galago Ultra Pro laptop has zero issues with Ubuntu (and the  last thing I want on my desktop are icons - - if I already have all I  need in the Launcher - - which is a perfect solution IMHO).[/QUOTE]

To be honest, I don't even know what the Unity desktop is. If I did and it was relevant, then yes, I should have mentioned it. The sound issue wasn't hardware malfunction. I still have it on Ubuntu 14.04, though testing on 16.04 beta reveals that it was fixed there. So most likely a software problem.

I understand and respect your position on desktop usage. But the fact remains that there are users who do use icons on their desktop. On your iPhone or Android, would you want to go through multiple steps just to open your most frequently used apps, or would you like to have them handy on the desktop?

[QUOTE=VTPoet]In my experience, any Linux OS has more bugs and challenges than either Windows or Apple.

...
One of the reasons I switched to Linux is that more and more companies  (Microsoft and Apple namely) were no longer supporting their products  without a credit card number. I felt like I was being ripped off.

So, when I read posts like yours I don't feel much sympathy. Pick your  poison. Use Windows or Apple if you like. When you run into a bug, give  'em a call and have your credit card ready.[/QUOTE]

Are you an  enterprise user? I use Windows as an individual, and I never even knew  Microsoft provided support to be honest. Windows had bugs, but just like  you, I found Ubuntu had more (if that's what you meant by Linux OS).  Don't get me wrong. I don't particularly like Windows. But it doesn't  have unfixable bugs that affect me to the degree Ubuntu does. That's why  I have no choice but to use it until I find a solution.

I posted  here because there seem to be many happy people in the community, and  I'm wondering how they managed to cope with all the problems. Is it  because they spent more time than me with Ubuntu? That their needs are  different? That they are more tolerant of problems like no sound?

---

### Post by mastablasta on 2016-03-24
> **sanssadness said:**
> 

Are you an  enterprise user? I use Windows as an individual, and I never even knew  Microsoft provided support to be honest. Windows had bugs, but just like  you, I found Ubuntu had more (if that's what you meant by Linux OS).  Don't get me wrong. I don't particularly like Windows. But it doesn't  have unfixable bugs that affect me to the degree Ubuntu does. That's why  I have no choice but to use it until I find a solution.


you are probably mistaking the OS bugs with driver bugs. Cannonical is responsible for the OS part, but manufacturers provide the drivers.  
in a same way Windows is responsible for OS, while manufacturers there are responsible for drivers. last very serious bug in windows OS was also caused by driver. an NVidia was supposed to fix some bugs and improve performance instead it locked windows 10 in reboot loop that was hard to get out of. and not long ago before that there was a windows update that bricked the OS. in the end it wasn't the OS that made it but the combination of antivirus software and specific windows update. users had to hold the update until antivirus software maker released a patch.

here most issues in your case have to do with drivers, so you should be saying why don't the hardware makers provide good drivers for Ubuntu. probably cause 1 % is using Linux desktop and they usually don't give much about Linux users.

servers are another matter as most new (if not all) consumer and business grade servers are Linux certified and manufacturers make sure they work well in Linux. I am running two such hardware that was made with Linux server in mind and no issues at all.

---

### Post by Geoffrey_Arndt on 2016-03-24
Quote:

"I posted  here because there seem to be many happy people in the  community, and  I'm wondering how they managed to cope with all the  problems. Is it  because they spent more time than me with Ubuntu? That  their needs are  different? That they are more tolerant of problems like  no sound?"

.....................................................................................................................................................................

It's statements like the above that get "under the skin" (e.g., irritate) Ubuntu and Linux desktop users.   Just because of _your_ experience with a couple PC's (based on your prior threads), to "imply" that is the norm, and that Linux users are "long-suffering" martyrs for the "cause" (running Linux) . . is naive at best & arrogant at worst.    If that were the case, desktop Linux use would have died-out at least 10 years ago.  Of at least 10 PC's (desktops and laptops) that I've personally owned (since 2003) . . NO major issues on any (HP's, Compaq's, Acer, Lenovo's & Sys76).    I could go into more detail, but you get the point.

And as others have written, Linux only accounts for between 1 & 3 percent of the whole consumer desktop PC market . . . with no kickbacks or other incentives going back to the OED's, OEM's as is the case with Windows based hardware.   So, rather than **retrofit a Windows designed PC** for Ubuntu . . . consider getting Linux friendly hardware next time you're in the market.    No more "nomodeset" or other workarounds to do . . or UEFI machinations . . . nice!

Lastly, as a final thought . . . it really does make a difference to know what DE (desktop environment) you're running.   Not knowing is akin to saying "not sure if I'm on Win7 or Win10 . . ." . . . . . . . hallo??

---

### Post by 1clue on 2016-03-24
+1 for what Geoffrey_Arndt just said.

I guess I'm fixated on this mac spoofing bug and why it's so important for a regular user on a hotspot. I can't imagine why anyone would care if you have your original mac address. The only practical uses I can think of are for easy replacement of autoconfigured hardware, and that's only likely in an enterprise environment, and then only for wired scenarios. So this feature linked to a wifi hotspot seems to me like a highly unlikely edge case.

Considering how long this bug has gone without a fix, I imagine the developers in question also see it as a highly unlikely edge case and so have not put any effort into fixing it. Maybe you could point out your use case in the bug report and get more interest from the dev team?

---

### Post by vasa1 on 2016-03-24
> **PaulW2U said:**
> ...
I've stopped saying that as I've been proved wrong much too often. :)
...
Maybe you should push for a */dev/null* section ;)

---

### Post by 1clue on 2016-03-24
Can we dispense with the personal attacks from everyone please?

My agreement with Geoffrey_Arndt was in the content of what he was saying, not with personal insults.

The idea of "coping" with Ubuntu or that it or any other distro are "disasters" as indicated by the topic of this thread is a bit insulting as it is, but understandable for someone who is frustrated.

Nobody is painting a fake picture. Linux works well on compatible hardware for what most people use it for.  It's the nature of the beast that some hardware is not supported and that some rarely-used functionality is not well supported.  I and others here have pointed out several options on how you can fix this.

It's true that Linux has a learning curve, especially if your use case is outside that of a normal user. I can't recall anyone saying otherwise. It's not for everyone.

Drivers:  Most Open Source drivers are bundled into the Linux kernel. Some hardware has both Open Source and proprietary drivers. Sometimes the proprietary driver is better, sometimes not. That's a bit of a moving target especially with newer hardware.  Sometimes with older hardware you need to limit your driver version to support the older card.

---

### Post by howefield on 2016-03-24
Closed for the time being.

---

