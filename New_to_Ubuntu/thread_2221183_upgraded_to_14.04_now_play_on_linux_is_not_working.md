---
title: "upgraded to 14.04 now play on linux is not working"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by mushroom08 on 2014-05-01
it tells me that "PlayOnLinux is unable to find 32bits OpenGL libraries" and that wine is no longer installed when i tryed reinstalling wine in the terminal i got this

mushoomstamp@Mushroom-Empire:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

help ](*,)

---

### Post by mushroom08 on 2014-05-05
bump

---

### Post by Un_Known on 2014-06-15
i have a "PlayOnLinux is unable to find 32bits OpenGL libraries" too.
installed POL and wine yesterday, it appeared to work fine at first when i appeared to successfully install need for speed world. the login interface opened, i typed in details, and the text was like weird arabesque script,but did let me log in.
when u login with need for speed world,just before you get its main viewer interface, it will download various updates and so on.
well, it gets so far,then loses connection.
soon after i attempted to install a program called rebirth (music production software) it thought i hadnt wine installed, then i attempted to run need for speed world again,and began to get that "PlayOnLinux is unable to find 32bits OpenGL libraries" notice, and now it's useless.

am actually getting tired of ubuntu after a week of hardly anything working properly, and too much time being taken up trying to install things to install things .......... and it might work....

back on issue, it needs things that are obsolete, even though it ran for two hours apparently fine.
iwish i could be more technical here,but i'm tired and fed up.

---

### Post by Rob Sayer on 2014-06-16
Sometimes things get buggered when you do a release upgrade.  Especially when you have a lot of untrusted ppas, a common noob mistake.  Which is why I do a clean reinstall instead.

I can't offer that much advice on wine (which playonlinux is just a front end for).  But I know it has serious limitations.

See this ...

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=20659&iTestingId=59988](https://appdb.winehq.org/objectManager.php?sClass=version&iId=20659&iTestingId=59988)

... and maybe you'll realize it isn't ubuntu's fault when a windows app fails in wine.  Wine just isn't that good ...

---

### Post by Drakkenn on 2014-06-16
I would check in /etc/apt/sources.list and make sure you comment out everything that is not standard. Save that, from there at the command line : sudo apt-get install -f. This will go out and try to fix any broken dependencies for your install. Then try and install wine again, and see if it catches the 32bit libs.

---

### Post by squakie on 2014-06-16
I would add to that:

- try deleting your playinlinux and wine installations first - saving, of course, the files you need

- then try installing again from the current repos

---

