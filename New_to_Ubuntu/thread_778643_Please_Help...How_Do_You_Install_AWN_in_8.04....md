---
title: "Please Help...How Do You Install AWN in 8.04?..."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Foghornleghorn on 2008-05-02
I've entered this command from the Terminal but after update can't find any reference to AWN.

 sudo apt-get install avant-window-navigator

Thank you.
regards,
Foghornleghorn.

---

### Post by artir on 2008-05-02
sudo apt-get install awn-manager

---

### Post by Foghornleghorn on 2008-05-02
Thank you artir...but that didn't work this is the response i'm getting.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
awn-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

any other suggestions?
regards,
Foghornleghorn.

---

### Post by angry_johnnie on 2008-05-02
Then the problem is just that it's not being displayed in the menu.  Hit Alt+F2 and then type **avant-window-navigator** to see if it comes up.  If it does, just add it manually to your applications menu.

---

### Post by mozetti on 2008-05-02
I'm pretty sure AWN isn't part of Ubuntu's installation or repositories. You need find the AWN installation tutorial and follow those instructions.

It includes adding the additional repositories that have AWN and then installing AWN from those repositories.

---

### Post by El King on 2008-05-02
I'd recommend Cairo-Dock
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

AWN is buggy and unstable

---

### Post by reacocard on 2008-05-02
Guide: [HOWTO: functional eye-candy with Avant-Window-Navigator](http://ubuntuforums.org/showthread.php?t=762363)

That guide has AWN and all applets as well. After install, AWN can be launched from the Applications->Accessories menu.

---

### Post by atomkarinca on 2008-05-02
> **mozetti said:**
> I'm pretty sure AWN isn't part of Ubuntu's installation or repositories. You need find the AWN installation tutorial and follow those instructions.

It includes adding the additional repositories that have AWN and then installing AWN from those repositories.

It is now.

```
sudo apt-get install awn-manager
```

To start hit alt + f2 and type avant-window-navigator. Then if you want it to autostart just go System >> Preferences >> Sessions >> Add >> command: avant-window-navigator.

---

### Post by jjpertusch on 2008-05-02
> **El King said:**
> I'd recommend Cairo-Dock
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

AWN is buggy and unstable

I disagree, i started using AWN about a month ago and it's been rock solid.  So much so that I use it as my window selector instead of the 'task bar'.  I've run into a few problems where applets didn't work as they were supposed to, but awn never crashed when these acted up.


I've never used cairo, but im really into awn.  I used the guide in the link that reacocard posted, btw.

---

### Post by Foghornleghorn on 2008-05-02
Thanks all...i've now got it installed. I've tried to use the resize option but can't for the life of me get it to work.All i see is a transparent type box that can be moved around,but i can't do anything with it.:(

Thanks again,
Foghornleghorn.

---

### Post by JoyceBabu on 2008-05-02
I have installed AWN, but I can't find any option to autostart the program on login. How can I do that?

---

### Post by bilal.17 on 2008-05-02
you need compiz to be enabled for AWN to run, check if you have visual effects enabled in System->Appearance, last tab, and enable visual effects

---

### Post by Paqman on 2008-05-02
> **JoyceBabu said:**
> I have installed AWN, but I can't find any option to autostart the program on login. How can I do that?

System > Preferences > Sessions and add an entry that launches avant-window-navigator to the list.

---

### Post by the fish on 2008-05-02
oose@moose-desktop:~$ run compiz
bash: run: command not found
moose@moose-desktop:~$ sudo apt-get install awn-manager
[sudo] password for moose: 
moose@moose-desktop:~$ sudo apt-get install awn-manager
[sudo] password for moose: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  awn-manager: Depends: avant-window-navigator (>= 0.2)
E: Broken packages


Any ideas with this. help

---

### Post by Foghornleghorn on 2008-05-02
Thanks everyone...now working.:)

---

