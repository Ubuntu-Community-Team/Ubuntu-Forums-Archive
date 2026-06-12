---
title: "How to run setup.exe"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by jjstewart on 2012-01-28
I'm trying to run setup for e-Sword under Ubuntu.  It works in Win7.  In Ubuntu left click does nothing, right click offers a Open With Mono RunTime (Terminal), Open With Mono RunTime, Open With Archive Manager.  Neither of the RunTimes do anything.  The Archive Manager gives an error that says it can't find the data in the file to know what to do with it, which is understandable because this is a setup.exe and not a zip file.

In reading the help, it discusses using a Launcher.  I couldn't find one in Ubuntu, so I looked for one in the Software Manager.  I picked one and it put an icon at the left.  When I clicked it, it had an error box saying it lacked an object to run, but since it started with an icon, you don't just pass a file name to an icon.

I thought I remembered a Launcher, but when I read that I needed it, I couldn't find it.  Why do you need a launcher to run an executable?  Is that like a RUN command?

Thanks for any help you can give.

---

### Post by lisati on 2012-01-28
e-sword won't run "natively" with Ubuntu. To use e-sword with Ubuntu, you need to use "Wine". There are several threads relating to e-sword in the forum, e.g. [http://ubuntuforums.org/showthread.php?t=1524397](http://ubuntuforums.org/showthread.php?t=1524397) (I think e-sword has been updated since that thread was written, downloading add-ons is done within e-sowrd these days)

---

### Post by halitech on 2012-01-28
if you have an always on connection (ie cable or dsl) it might be easier to use the online version then trying to get e-sword running

[http://live.e-sword.net/app/](http://live.e-sword.net/app/)

---

### Post by lisati on 2012-01-28
p.s. There's also "Xiphos" available in the software centre that you might want to check out.

---

### Post by TheFu on 2012-01-29
e-Sword is a program designed to be used under a different operating systems, MS-Windows. If there isn't a native version compatible with Linux, then you'll need to try a different solution.

WINE is a program that provides a Windows-like interface for programs designed for that "other" OS. Sometimes programs work well, somethings programs work ok and other times programs do not work under WINE.  It appears that e-Sword works to some level using WINE according to the instructions here: [http://appdb.winehq.org/appview.php?appId=1341](http://appdb.winehq.org/appview.php?appId=1341) .  If you follow those instructions, your very likely to have an acceptable outcome.

The steps to use WINE are:
* install WINE on your system using your package manager.
* open a terminal and run `wine /full/path/to/setup.exe`
* follow the installation instructions.

There may be another option. [http://xiphos.org/](http://xiphos.org/)  which appears to be native Linux attempt that is compatible with e-Sword. There are instructions for Ubuntu here: [http://xiphos.org/download/debian-ubuntu/](http://xiphos.org/download/debian-ubuntu/) , but they appear to be old.  

I've never attempted to use any of these tools, except WINE, which I've used with some success and some failures.

---

### Post by 3rdalbum on 2012-01-29
You might be barking up the wrong tree here. There are plenty of Bible study programs that run natively in Linux. I haven't had a good look in the repositories yet but I believe you'll find some in Ubuntu Software Center.

I remember the name of one, Gnomesword, but I can't actually find it in the repositories at the moment.

My suggestion would be to look for the native software first, BEFORE trying to shoehorn an alien program into your Ubuntu.

And I believe there's an online version of E-sword too, that might be a possibility.

---

