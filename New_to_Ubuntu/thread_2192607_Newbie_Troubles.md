---
title: "Newbie Troubles"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by oddfuturetdw on 2013-12-08
I installed Ubuntu and have been loving it.It's a great OS but I've had a few problems.(Ubuntu 12.04 32Bit)

1.Installing programs downloaded from Firefox
I don't know how to install downloaded programs.
For Example:I download WinRAR and It's in my downloads 
but the archive manager doesn't do anything.
2.Ubuntu Software Center install
Every time I try to install an app from the USC,
I will flash the download bar but then it will disappear and
go back to saying "Install."

3.Synaptic Package Manager
I click it from the "Dash Home" and nothing happens.
I've been trying to uninstall some programs but I can't 
due to this problem.When I try to uninstall programs 
from the USC,nothing happens.

Other then those problems,I've had a great time on Ubuntu.
Great Features,interface,and just looks clean.:)

---

### Post by DuckHook on 2013-12-08
Hello oddfuturetdw and welcome to Ubuntu and the forums.

To answer your questions:

1. You cannot run WinRAR in Linux. It is a Windows program and will not work in Linux without very special and complicated workarounds. But in any case, you do not need it. It performs a very simple task and you can use Linux programs that do the same job. I recommend that you read the following to get a better idea of the way Linux works and the differences between Linux and Windows.

"Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

2. Have you updated your operating system since you have installed it? Please open a terminal and copy/paste the following commands into the terminal```
sudo apt-get update && sudo apt-get dist-upgrade -y
```Then try installing your programs from the repositories using Synaptic or Ubuntu Software Center.

A general user should never install any program from outside of the repositories. Installing programs from third-party sites is one of the reasons that Windows is a virus playground. This is covered in the websites that I have linked to . I highly encourage you to read through them as part of your introduction to Ubuntu.

---

### Post by Frogs Hair on 2013-12-08
Should you need to extract an rar package  you can install unrar from the software center . There are compression tools as well including rar and 7zip. These programs don't have a GUI ,but  the extract and compress options are displayed in the context / right click menu when a folder or package is selected.

---

### Post by asus-user on 2013-12-09
> **oddfuturetdw said:**
> 
I don't know how to install downloaded programs.
For Example:I download WinRAR and It's in my downloads 
but the archive manager doesn't do anything.

When you deal with a different Operating System, this means that the programs what you used to work with will differ.
Ubuntu programs and applications are different than windows, you the way you install it is also different. that's why ".exe" files do not work on ubuntu as they work on windows, and ubuntu use another system of installing programs. (ps. Ubuntu can execute .exe files using a windows emulator like wine)
The best way to install any program is to use Terminal, first update the repository using this command:
```

sudo apt-get update

```
and then if the repository for the program you want to install is there:
```

sudo apt-get install <program name>

```
else you need to know it and add it.

> **oddfuturetdw said:**
> 
Every time I try to install an app from the USC,
I will flash the download bar but then it will disappear and
go back to saying "Install."

3.Synaptic Package Manager
I click it from the "Dash Home" and nothing happens.

Make sure that you have an administrator password, and try again.
When **Synaptic **is opened it asks first for an administrator password. and sometime earlier there was some reports that it doesn't start and the auth window does not open.
see: 
[http://ubuntuforums.org/showthread.php?t=1989865](http://ubuntuforums.org/showthread.php?t=1989865)

try to run it from Terminal with the command:

```
gksu synaptic
```

Report any errors/messages you get here.

---

### Post by oddfuturetdw on 2013-12-09
Syanpatic problem solved,thanks!I would download Unrar,but I can't download anything from the USC
I'll click install but it will only show the download bar for a quick second and then disappear showing install again.

---

### Post by DuckHook on 2013-12-09
> **oddfuturetdw said:**
> ...I would download Unrar,but I can't download anything from the USCYou can download *unrar* using Synaptic.> I'll click install but it will only show the download bar for a quick second and then disappear showing install again.I'm puzzled. You appear to have a very odd setup. Software Center should work out of the box on a pristine install. Have you done anything unusual to your installation since it was initially installed? Have you changed any settings, activated the root account (you shouldn't), or run any scripts using *sudo*?

---

### Post by mastablasta on 2013-12-10
i think Ark is a good GUI compressed files manager. it is for KDE though...

---

### Post by Impavidus on 2013-12-10
There could be something wrong with the package management system. Run```
sudo apt-get update
sudo apt-get upgrade
```and post the output (in [code] tags, if you please). It may give us a meaningful error message.

---

### Post by thatredbird on 2013-12-10
This could just be a Lubuntu thing but when I install I have to click an install button, then I have to get the package by clicking another button? I wonder if that's similar on Ubuntu, and if that's the hold up.

---

