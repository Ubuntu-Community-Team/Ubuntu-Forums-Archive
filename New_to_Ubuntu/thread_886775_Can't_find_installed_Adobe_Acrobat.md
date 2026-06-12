---
title: "Can't find installed Adobe Acrobat"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by RobHK on 2008-08-11
I downloaded the RPM package from the Adobe site. I followed some instructions I found on line to convert it to a DEB package. (Had to go into root.) Found the install package was owned by root so had to go back there, though I ran the package from my own desktop. (I do wish Ubuntu would treat me like a grown-up. XP let's me choose to have full admin rights.)

The package installed successfully but I can find no trace of it. It isn't in the menus. It isn't listed when I right-click on a PDF document. So how do I run it, ideally by default when I click on a PDF or as an Open With option when I right-click?

---

### Post by dca on 2008-08-11
You have to d/l the ".deb" version of Adobe Reader from website.  Should be listed after you select other OS from drop-down dealie.  Save it to desktop, after you can 'left-click' on file and select 'Install using GDebi installer'...

---

### Post by dca on 2008-08-11
If you properly installed the '.deb' version from Adobe website it shows under 'Applications -> Office' from main menu bar.

---

### Post by kansasnoob on 2008-08-11
> **RobHK said:**
> I downloaded the RPM package from the Adobe site. I followed some instructions I found on line to convert it to a DEB package. (Had to go into root.) Found the install package was owned by root so had to go back there, though I ran the package from my own desktop. (I do wish Ubuntu would treat me like a grown-up. XP let's me choose to have full admin rights.)

The package installed successfully but I can find no trace of it. It isn't in the menus. It isn't listed when I right-click on a PDF document. So how do I run it, ideally by default when I click on a PDF or as an Open With option when I right-click?

IMO that's the wrong way to go about it.

Just use the Medibuntu repos (for Hardy):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Add the GPG key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

NOTE: if other than Hardy select the proper repo here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then open Synaptic and "Reload" and install acroread:

[ATTACH]81149[/ATTACH]

---

### Post by kansasnoob on 2008-08-11
> **dca said:**
> You have to d/l the ".deb" version of Adobe Reader from website.  Should be listed after you select other OS from drop-down dealie.  Save it to desktop, after you can 'left-click' on file and select 'Install using GDebi installer'...

That will work just as well.

---

### Post by RobHK on 2008-08-11
> **kansasnoob said:**
> IMO that's the wrong way to go about it.

Just use the Medibuntu repos (for Hardy):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Add the GPG key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

NOTE: if other than Hardy select the proper repo here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then open Synaptic and "Reload" and install acroread:

[ATTACH]81149[/ATTACH]
Tried it but the installation failed. Said it wasn't a genuine Ubuntu package.

---

### Post by RobHK on 2008-08-11
> **RobHK said:**
> Tried it but the installation failed. Said it wasn't a genuine Ubuntu package.

Tried again and got this:

```
E: /var/cache/apt/archives/acroread_8.1.2-0medibuntu6.2_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
```

But I have already deleted usr/bin/acroread and rebooted.

---

### Post by SunnyRabbiera on 2008-08-11
You really dont need it anyway, as we have a native PDF viewer called evince pre installed.
But if you really want it you can just use the repositories.
There is medibuntu that has acrobat in its repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

after enabling it there is a tool called synaptic package manager that is used to install packages, typically you dont fish the internet for installer files like in windows, instead we use something called repositories.
To learn more visit this page:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also there is a reason why ubuntu is set up the way it is, actually its windows that treats people like kids by encouraging people to use the root account by default.
You are dealing with two very different security models here, in windows the mentality is "any idiot can use it, and if something goes wrong its on the users head"
In linux its something else entirely, the windows mentality is why its so insecure and full of viruses/ addware/ spyware /malware.
By enabling the root account by default windows makes the user vulnerable.

---

### Post by RobHK on 2008-08-11
> **RobHK said:**
> Tried again and got this:

```
E: /var/cache/apt/archives/acroread_8.1.2-0medibuntu6.2_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
```

But I have already deleted usr/bin/acroread and rebooted.

Another window has this in a pull down black window:
```

E: /var/cache/apt/archives/acroread_8.1.2-0medibuntu6.2_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu


Reading database ... 124583 files and drectories currrently installed.)
Unpacking acroread (from .../acroread_8.1-0medibuntu6.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archivs/acroread_8.2-0medibuntu6.2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread' whichis also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1-0medibutu6.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover.
```

---

### Post by WRDN on 2008-08-11
Rather than redownloading the debian package from the Adobe website/ Medibuntu repository, you could use the program, Alien (available in repo), to convert the rpm to a debian package, then install it.

---

### Post by RobHK on 2008-08-11
> **SunnyRabbiera said:**
> You really dont need it anyway, as we have a native PDF viewer called evince pre installed.
But if you really want it you can just use the repositories.
There is medibuntu that has acrobat in its repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

after enabling it there is a tool called synaptic package manager that is used to install packages, typically you dont fish the internet for installer files like in windows, instead we use something called repositories.
To learn more visit this page:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also there is a reason why ubuntu is set up the way it is, actually its windows that treats people like kids by encouraging people to use the root account by default.
You are dealing with two very different security models here, in windows the mentality is "any idiot can use it, and if something goes wrong its on the users head"
In linux its something else entirely, the windows mentality is why its so insecure and full of viruses/ addware/ spyware /malware.
By enabling the root account by default windows makes the user vulnerable.

Don't want to get into a lengthy discussion of this, but my reason for saying this is that I'm constantly having to sudo, open xfe as root or log in as root. Even a simple installation I can find the owner of the file is root and I can't open it. This gets frustrating.

I like using Linux, and I know it's made big steps in user-friendliness, but it still has some way to go before ordinary users will leave Windows for it. I'm optimistic it's heading that way though. (What will help people making the switch BTW is is people posting answers here indicate the GUI approach when there is one, even though for them the command is quicker.)

I do use Linux in preference to Windows most of the time. I've been into Linux for nearly a year so I'm familiar with repositories and Synaptic. But acroread wasn't in the repositories I had. Let's not digress though. We've each explained our viewpoint. Let's leave it there.

I'm trying to install from medibntu but this is the error I'm getting, due to my previous failed install.```


E: /var/cache/apt/archives/acroread_8.1.2-0medibuntu6.2_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu


Reading database ... 124583 files and drectories currrently installed.)
Unpacking acroread (from .../acroread_8.1-0medibuntu6.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archivs/acroread_8.2-0medibuntu6.2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread' whichis also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1-0medibutu6.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover.
```

---

### Post by SunnyRabbiera on 2008-08-11
> **RobHK said:**
> Don't want to get into a lengthy discussion of this, but my reason for saying this is that I'm constantly having to sudo, open xfe as root or log in as root. Even a simple installation I can find the owner of the file is root and I can't open it. This gets frustrating.

I like using Linux, and I know it's made big steps in user-friendliness, but it still has some way to go before ordinary users will leave Windows for it. I'm optimistic it's heading that way though. (What will help people making the switch BTW is is people posting answers here indicate the GUI approach when there is one, even though for them the command is quicker.)

I do use Linux in preference to Windows most of the time. I've been into Linux for nearly a year so I'm familiar with repositories and Synaptic. But acroread wasn't in the repositories I had. Let's not digress though. We've each explained our viewpoint. Let's leave it there.

I'm trying to install from medibntu but this is the error I'm getting, due to my previous failed install.```


E: /var/cache/apt/archives/acroread_8.1.2-0medibuntu6.2_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu


Reading database ... 124583 files and drectories currrently installed.)
Unpacking acroread (from .../acroread_8.1-0medibuntu6.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archivs/acroread_8.2-0medibuntu6.2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread' whichis also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1-0medibutu6.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover.
```

I would use sudo dpkg --configure -a to try fix it, or simply reboot.
Sometimes a reboot helps with this sort of thing.
As for your complaints about how Ubuntu and linux manages things with administration stuff, well for me its way better then windows as its SECURE.
Windows and its auto root system is a benefit and a curse at the same time, but its more of a curse as so much malicious crap is out there ready to attack it.
By separating the normal user and root Ubuntu and linux make a far better system.

---

### Post by starcannon on 2008-08-11
> **SunnyRabbiera said:**
> You really dont need it anyway, as we have a native PDF viewer called evince pre installed.
But if you really want it you can just use the repositories.
There is medibuntu that has acrobat in its repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

after enabling it there is a tool called synaptic package manager that is used to install packages, typically you dont fish the internet for installer files like in windows, instead we use something called repositories.
To learn more visit this page:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also there is a reason why ubuntu is set up the way it is, actually its windows that treats people like kids by encouraging people to use the root account by default.
You are dealing with two very different security models here, in windows the mentality is "any idiot can use it, and if something goes wrong its on the users head"
In linux its something else entirely, the windows mentality is why its so insecure and full of viruses/ addware/ spyware /malware.
By enabling the root account by default windows makes the user vulnerable.
+1, and if I remember rightly, acroread is available in the normal repositories, you don't need medibuntu for something like this (though you should get it anyway, its useful for many other things you will want).

Your first stop when looking for software should always be:
System->Administration->Synaptic Package Manager
The whole point of that utility is to make installing, using, and keeping software up to date as simple and painless as possible.

---

### Post by RobHK on 2008-08-12
> **WRDN said:**
> Rather than redownloading the debian package from the Adobe website/ Medibuntu repository, you could use the program, Alien (available in repo), to convert the rpm to a debian package, then install it.

As I explained in the original post, that is what I did, and where the problems started.

I don't need Acrobat. I'll stick with Evince.

---

