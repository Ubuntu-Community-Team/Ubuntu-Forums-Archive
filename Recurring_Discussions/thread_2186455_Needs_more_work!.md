---
title: "Needs more work!"
date: 2013-11-07
forum: Recurring Discussions
---

### Post by pgriffin2 on 2013-11-07
I didn't see a complaint department. So I posted here!  This hopefully somewhat constructive.


Until recently Windows XP was then main operating system I used. I used ubuntu 8.04 and 10.04 for years by remote login from my Windows computer without problem. Recently I purchased a System76 laptop with ubuntu 12.10 loaded on it. I am very pleased with the laptop. However, now that I am trying to do more, and using the default graphical gnome interface I feel that there is much lacking. All too many times I have to reboot because the menus disappear both on gedit and/or nautilus. I hear a lot of stuff about "newbies". I have been using computers since 1982 with my first sinclair and atari. Used a DEC Unix workstation in the early 90s. I think this is just an excuse for poor planning and lack of direction in the developer community. The basic software used by developers such as gcc and QT are extremely robust but from what I can see most other non-command line programs constantly are having problems. With each new version of ubuntu I see reports of something else breaking. There are constant problems with things in or not in default libraries that affect the installation of programs. I have never had a problem with any program using the Windows graphical interface! I understand and appreciate some problems developers have especially when they have to reverse engineer drivers etc. But I'm not talking about that. 


I am mainly interested in the tools like basic editors and file manager. When these don't work there are serious problems. I also do lots of things at the command line for those people who want to say "newbie". I get the feeling that the vocal users feel they have payed their dues and everyone else should. It appears that they don't care about graphical interfaces. This attitude is not only absurd but brings I can only believe a lackadaisical attitude on the developers. The software bundled with ubuntu should without question work without a problem! This is clearly not true. Why so many problems once you get to graphical programs? If the problems that exist have to do with drivers, which I doubt, some workable standards should be created to eliminate the problem. If the ubuntu community wants _more real people_ to use ubuntu there is much work to be done!


When I was working as an development engineer I know it was common for most engineers to want to work in the sandbox. Without their managers holding their feet to the fire there would never have been a real product. I'm sure there are no managers overseeing program development on ubuntu Linux. 


Finally, I think that the direction I saw on [http://www.itworld.com/](http://www.itworld.com/) for Linux 4.0 is most appropriate. "Linux 4.0 should have only bug fixes, no new features." Titled, "Linux creator Linus Torvalds wants comments on a proposal for an entirely bug-fixes and stability release in about a year."

Pete

---

### Post by wildmanne39 on 2013-11-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ajgreeny on 2013-11-07
Perhaps you would be happier and more satisfied with:-

[LIST=1]
[*]Another desktop environment; I use xfce 4.10 on Xubuntu 12.04 and it is rock solid.
[*]An LTS version rather than one of the interim versions; LTS versions always seem to be very stable and are supported for 3 yrs, or since 12.04 for 5 years.
[/LIST]

You say > The software bundled with ubuntu should without question work without a  problem! This is clearly not true. Why so many problems once you get to  graphical programs? If the problems that exist have to do with drivers,  which I doubt, some workable standards should be created to eliminate  the problem. If the ubuntu community wants _more real people_ to use ubuntu there is much work to be done!
Don't forget that ubuntu simply ships with applications from third party sources; very few are ubuntu or canonical developments other than unity, and as I don't use that I am not in a position to comment in detail about it.

---

### Post by Zill on 2013-11-07
pgriffin2:  This link might help explain things... [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by ian-weisser on 2013-11-07
> **pgriffin2 said:**
> [...]However, now that I am trying to do more, and using the default graphical gnome interface I feel that there is much lacking. All too many times I have to reboot because the menus disappear both on gedit and/or nautilus. I hear a lot of stuff about "newbies". I have been using computers since 1982 with my first sinclair and atari. Used a DEC Unix workstation in the early 90s. I think this is just an excuse for poor planning and lack of direction in the developer community. The basic software used by developers such as gcc and QT are extremely robust but from what I can see most other non-command line programs constantly are having problems. With each new version of ubuntu I see reports of something else breaking. There are constant problems with things in or not in default libraries that affect the installation of programs. I have never had a problem with any program using the Windows graphical interface! I understand and appreciate some problems developers have especially when they have to reverse engineer drivers etc. But I'm not talking about that. 

One of the wonderful elements of the Ubuntu community is that you can help quantify, diagnose, and fix both bugs and management issues.

I do hope you have run your menu bug to ground, and determined if it has been reported yet. If not, please report it - the developers cannot fix what they do not know about.

Do remember that members of the Ubuntu community work very hard to help users, to improve use cases, to triage bugs, to develop patches, to test patches, to test new releases, to backport patched software, to improve documentation, and many other important tasks. All of this work -and discussion about it- happens in the open, and sometimes it's not pretty. You're seeing the sausage get made.

Most developers *do* test their software before release. They *don't* capriciously remove vital functions. They *do* address reported bugs. They are rightly proud of their product. They are not, however, psychic (I think you can relate to that), and cannot predict how their software may be used outside of their tested use cases, on broken or incompatible hardware, with different or almost-compatible dependencies, with the settings changed strangely, or with some other process feeding bad input.





> **pgriffin2 said:**
> I am mainly interested in the tools like basic editors and file manager. When these don't work there are serious problems.
Agreed. The developers welcome volunteers to handle common support questions, improve documentation, triage bugs, help test releases, and liason to other projects and venues.


> **pgriffin2 said:**
> I also do lots of things at the command line for those people who want to say "newbie". I get the feeling that the vocal users feel they have payed their dues and everyone else should.
The former concern is addressed by the Ubuntu Code of Conduct. [http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)
Please report violations of the Code of Conduct that you discover in this forum.
Personally, I believe that -as a volunteer- I am willing to help others *if* they are willing to learn a little. Were I paid to provide support, then the vision of the employer would of course govern.




 > **pgriffin2 said:**
> The software bundled with ubuntu should without question work without a problem! This is clearly not true.
According to errors.ubuntu.com, and the most-reported bugs at launchpad.net, I disagree. Millions of copies of Ubuntu 13.10 have been downloaded. As of today, the most-reported bug in 13.10 is 2547 reports of a bug in hud...and a fix has just been released for it. As of today, 0.2% of (estimated) all 13.10 installs reported a crash or other apport-reportable bug. That's not all bugs...but look where the bug reporting percentage was three years ago or six years ago. Quality has *vastly* improved!

Really, if all the software was a buggy and terrible as you suggest, I doubt any of us would be here.


 > **pgriffin2 said:**
> Without their managers holding their feet to the fire there would never have been a real product. I'm sure there are no managers overseeing program development on ubuntu Linux.
Do visit the online Ubuntu Developer Summit next week ( [http://summit.ubuntu.com](http://summit.ubuntu.com) ) to meet those managers and discuss their plans for the next three months.


> **pgriffin2 said:**
> I think that the direction I saw on [http://www.itworld.com/](http://www.itworld.com/) for Linux 4.0 is most appropriate. "Linux 4.0 should have only bug fixes, no new features."
This has been suggested several times over the years. There are two big problems with it: Most upstream projects don't report to Ubuntu (or anyone else) and are going to continue developing at their own pace, and Canonical-based projects already have a transparent QA program and don't have big backlogs of bugs.

Really, do visit the online UDS and take a look at all the effort and planning going into quality, integration, and testing. I think you will be pleased to see how open and transparent the Ubuntu development process really is.

---

### Post by buzzingrobot on 2013-11-07
> **pgriffin2 said:**
> 
Finally, I think that the direction I saw on [http://www.itworld.com/](http://www.itworld.com/) for Linux 4.0 is most appropriate. "Linux 4.0 should have only bug fixes, no new features." Titled, "Linux creator Linus Torvalds wants comments on a proposal for an entirely bug-fixes and stability release in about a year."


Torvalds was talking about his kernel, not the entire Linux platform.   He has no role in application development and other userspace issues.

Your post implies a degree of centralized development management that does not exist in Linux. Applications are typically created and maintained by individual developers, in their own time and on their own dime.  Their adherence to design and coding standards and practices that may or may not be issued by any given distribution is entirely voluntary.  

Ubuntu, like other distributions, is primarily a packaging effort, gathering up code created elsewhere.  While Ubuntu releases follow a period of alpha and beta testing, there's nothing that flushes out bugs like a general release, as I'm sure you know. (You may have noticed that many Linux applications are released with version numbers like, "0.1" or "0.2".  Often, this is done to acknowledge that the developers had no effective way to get their new code tested other than releasing and asked for bug reports.)

 In addition, Linux distributions are reliant on all those application developers, as well as their users, to test their products against the alpha/beta releases.  If that does not happen, then bugs triggered by the new release can only be found after its release.

---

### Post by lykwydchykyn on 2013-11-07
> **pgriffin2 said:**
> 
If the ubuntu community wants _more real people_ to use ubuntu there is much work to be done!

Darn, I thought I was real...  and here's my velveteen all worn and threadbare.  Come on, nursury magic!

---

### Post by oldos2er on 2013-11-07
Moved to Recurring.

---

