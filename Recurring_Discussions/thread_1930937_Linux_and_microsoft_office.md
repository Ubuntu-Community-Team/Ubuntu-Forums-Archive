---
title: "Linux and microsoft office"
date: 2012-02-24
forum: Recurring Discussions
---

### Post by skullbuntu on 2012-02-24
Hi. First of all I have to say that I am trying Ubuntu for the very first time and I love it. Although, its not really hard to love it becausewi I was really frustrated with windows and especially the fact that they want me to pay for support when it <snip> up. Anyway, just as a matter of discussion, I would switch to Linux full time if it was not for the fact that I *need *microsoft access and excel to work flawlessly (I handle a ton of data for corporate work so there is no room for me to lose data or risk incompatibility etc...) Anyone have any idea how long before we can use MS Office stuff on linux? How soon will this happen?

---

### Post by roelforg on 2012-02-24
First: swearing isn't allowed here.
Also: assuming the copy is legal (we can't give support to you if it isn't), use wine.
(Google it)

---

### Post by hotwax on 2012-02-24
you can use the equivalent office suite called libreoffice or openoffice

or

install wine and you can emulate ms office 2007 on linux

im not sure how compatible msoffice 2010 is on wine but you can look up the info at [http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

you can also use playonlinux instead of wine

---

### Post by samalex on 2012-02-24
I agree, Wine works rather well with most versions of MS Office, but you won't be able to use MS Access or Outlook, at least I've yet to get either of them to work.  But MS Word, Excel, PP, and even OneNote and Visio work rather well.

---

### Post by Old_Grey_Wolf on 2012-02-24
You can use PlayOnLinux to make using Wine easier. [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by roelforg on 2012-02-24
> **samalex said:**
> I agree, Wine works rather well with most versions of MS Office, but you won't be able to use MS Access or Outlook, at least I've yet to get either of them to work.  But MS Word, Excel, PP, and even OneNote and Visio work rather well.
May i suggest starting Outlook from the terminal and googleing the error? (usually a missing DLL; winetricks can solve those).

Sorry, couldn't resist.

---

### Post by gradinaruvasile on 2012-02-24
As soon pigs will fly. Or Microsoft releases a Linux version. I think the first is closer.

If you work in a Microsoft software driven environment and you worry about incompatibilities, use Windows (especially if you handle sensitive data). There is no other way. Microsoft software was designed to work on Windows. Period.
I dont know whats that big deal about the support - you can get free support on forums for Windows just as you get it for Linux. The difference is that most likely if you experience bugs, Microsoft wont give a flying %&$% about your report (they probably have millions to sift through) in contrast with Linux developers that, if reached (usually on mailing lists), might help you really fast in squashing bugs or implementing features.

Note: Microsoft Office can be run via Wine but you have missing features and stability issues.
Microsoft Office can be run via VirtualBox flawlessly, but in this case you actually need a full Windows license and you have to run that full Windows OS in a virtual environment, leading to severe memory and sometimes CPU usage overhead and kinda defeating the purpose of using another OS if you use the virtualized OS mainly.

I personally use Linux only for a few years now (except for some software testing cases where i run virtualboxed windows), but i work in tech support and i have no issues, actually its better than Windows because all its low level diagnosis and data manipulation tools (added bonus is the virtual invulnerability to viruses).
I never had issues (as in "doesnt bother me") with misaligned doc/docx or xls/xlsx docs when opened in openoffice because those are not vital documents to me (although as of lately most work quite well, especially xls/xlsx types, BUT i didnt use those macro heavy ones). The ones i really needed quite interestingly had never experienced any issues with. So there you have it, you can use Linux effectively, but not in your case.

---

### Post by Gremlinzzz on 2012-02-24
> **skullbuntu said:**
> Hi. First of all I have to say that I am trying Ubuntu for the very first time and I love it. Although, its not really hard to love it becausewi I was really frustrated with windows and especially the fact that they want me to pay for support when it <snip> up. Anyway, just as a matter of discussion, I would switch to Linux full time if it was not for the fact that I *need *microsoft access and excel to work flawlessly (I handle a ton of data for corporate work so there is no room for me to lose data or risk incompatibility etc...) Anyone have any idea how long before we can use MS Office stuff on linux? How soon will this happen?

I have no need for it but found this how too GL:popcorn:
[http://www.ubuntubuzz.com/2011/09/install-microsoft-office-2007-in-ubuntu.html](http://www.ubuntubuzz.com/2011/09/install-microsoft-office-2007-in-ubuntu.html)

---

### Post by Gone fishing on 2012-02-25
Crossover office will allow you to run MS Office including Access (2000 - 2003) 

[http://www.codeweavers.com](http://www.codeweavers.com)

---

### Post by 3rdalbum on 2012-02-27
Apple is having trouble with continuing to develop Mac OS X; it's just not flexible enough to change without breaking existing software. Especially on the security front - several big security issues simply can't be fixed without breaking every OS X program. Whereas Linux distros are constantly changing without problems, and in terms of security it's all designed correctly.

If Mac OS XI shifts architecture again to be based on a Linux kernel with Wayland, then we may well see Microsoft Office runnable on a standard Linux distro with a light smattering of reverse-engineered compatibility libraries. It wouldn't need to be as extensive a reimplementation as Wine.

I think in the near future we'll see Mac OS becoming a lot more like a standard Linux/BSD, but with a different desktop and a few different APIs. Apple just can't continue pumping resources into developing OS X and getting fewer and fewer stable features for their dollar.

---

