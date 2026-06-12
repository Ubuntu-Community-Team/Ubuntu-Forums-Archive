---
title: "Unmet dependencies"
date: 2017-06-28
forum: New to Ubuntu
---

### Post by baguk on 2017-06-28
Hi, I'm relatively new to Ubuntu admin. It is one of the downsides of Ubuntu that you need to be a techie to do almost anything outside the GUI such as installing printers. Until that is fixed Ubuntu, and Linuxm isn't going to make it mainstream. Can't understand why doing a basic function like installing a printer can be so cumbersome.

Just tried to install a Epson WF 3620 printer and followed the instructions at Epson, who could do a lot more for Linux imo,  and on this site and the instructions for installing from the downloaded .deb file just failed miserably. I now am left with an unmet dependency in the system. Trying to reverse what I did is, no surprise, not just reversing the commands as it refuses to do so.

How can I id and fix the unmet dependency? I did an apt-get -check and got> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 epson-inkjet-printer-escpr : Depends: lsb (>= 3.2) but it is not installed
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Unmet dependencies. Try using -f.


So I tried apt-get -f and failed so tried apt-get -f epson-inkjet-printer-escpr which failed the same way.

> E: Command line option 'f' [from -f] is not understood in combination with the other options.

Must be something simple to fix this. Can someone help?

---

### Post by QIII on 2017-06-28
Hello!

Whenever you download and attempt to install something from the web, you run the risk of missing dependencies.

Were I you, I would simply go to the GUI system settings menu and add a printer.

Just as an aside with regard to Linux not making it mainstream:  there are, by an order of magnitude, more devices running Linux than anything from Microsoft.  When will Linux win?  It already has.

But from where you are now, try using

```
sudo apt-get -f install 
```

as suggested.

---

### Post by CatKiller on 2017-06-28
```
The following packages have unmet dependencies.
 epson-inkjet-printer-escpr : Depends: lsb (>= 3.2) but it is not installed
```

I'm sure you won't need to install that .deb file, but if you did want to, it says what the problem is: you don't have lsb installed, which that package apparently depends on.

```
sudo apt-get install lsb
``` would install that.

---

### Post by again? on 2017-06-29
> **CatKiller said:**
> ```
The following packages have unmet dependencies.
 epson-inkjet-printer-escpr : Depends: lsb (>= 3.2) but it is not installed
```

I'm sure you won't need to install that .deb file, but if you did want to, it says what the problem is: you don't have lsb installed, which that package apparently depends on.

```
sudo apt-get install lsb
``` would install that.

...and it says so on the [Epson download page]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=55539&DSCCHK=5ef6ec128765534a989152269045f12fc58077f2") after you accept the terms of download.
> [Notice]
In order to install these drivers, you need to install LSB package (version 3.2 or later) beforehand.

Ubunbu:
# apt-get install lsb
**P.S. If you install gdebi (a GUI deb installer) and install debs with gdebi it will resolve dependencies.

---

### Post by baguk on 2017-06-29
Thank you all for the responses. I installed lsb and it worked fine.

QIII, By mainstream I mean the end users, the home users, not the number of servers inside data centres managed by people such as yourself. I see simple add on packages for peripherals being the final hurdle before Linux starts to grow with the home user and then when games start getting ported to it, without WINE, then it will be mainstream. I have to have a Windows system just to play my games.

CatKiller, Thank you again for your spot on advice. I must confess I though I had lsb but something else was wrong. I'm learning slowly.

guber2, I downloaded the .deb from a different site so I didn't see the notice from Epsom. I'll make a not of gdebi and if I am looking at installing more .deb I'll install it.

Thank you all again. Must confess I am impressed with the users on these forums.

---

### Post by CatKiller on 2017-06-29
I'm glad you got your problem fixed.

> **baguk said:**
> By mainstream I mean the end users, the home users, not the number of servers inside data centres managed by people such as yourself. I see simple add on packages for peripherals being the final hurdle before Linux starts to grow with the home user and then when games start getting ported to it, without WINE, then it will be mainstream. I have to have a Windows system just to play my games.

Linux is fine for normal users, and it's fine for experienced users. The problematic population is the Windows Power Users, because all the instincts that they've developed are wrong. For example, your printer wasn't working so you looked on the Internet for a driver file to download, which you assumed would be self-contained, because that's exactly what you'd do on Windows. You're not wrong to have developed those habits from years of using Windows, but it's the unlearning of them all that's painful and frustrating when you switch to something else. Because I've not used Windows in a very long time, I would have exactly the same feelings if I were to try to use it now, but I, too, used to be a Windows Power User and went through exactly the stage you're at now when I switched to Linux. For the record, the printer-driver-escpr driver is in the repositories, and installing from there would have resolved all the dependencies for you.

With regards to games, I have more Linux games in my Steam library than I'll ever get round to playing and even more from GOG and Humble Bundles. There are plenty of games developed for Linux, but it's no different than the Sony/Microsoft/Nintendo divide. If the games you actually want to play are only on a particular platform, then you use that platform.

Again, I'm pleased you got this issue fixed, and come back with any others. Good luck getting over the Power-User Hump! :)

---

