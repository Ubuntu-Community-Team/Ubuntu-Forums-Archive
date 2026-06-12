---
title: "Failed to execute child process &quot;su-to-root&quot;"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Wantingtolearn on 2008-11-03
Failed to execute child process "su-to-root" (No such file or directory)

Hey guys, I am new and just trying to learn...EVERYTHING.  But I guess that I need to learn the basics first.  I get the above message when I try to use wifi radar in Ubuntu 8.10, i am really not sure where to go from here.  I was having trouble with connectivity with Netowork Connections, and wifi radar worked for me with 8.04.  Any help would be great, thank you in advanced.

---

### Post by echo314 on 2008-11-03
Could you tell me what exactly it is you are doing that get that message? Are you entering some command? If so copy/paste it please.

---

### Post by Wantingtolearn on 2008-11-03
I am just clicking on the icon in applications/ internet/ wifi radar

---

### Post by Axis on 2008-11-03
Ok so the application is reading that back?

Try uninstalling it and reinstalling it through synaptic.
System -> Administration -> Synaptic Package Manager

---

### Post by Wantingtolearn on 2008-11-03
I tried the re installation that did not work.  Same error message.

---

### Post by Axis on 2008-11-03
I have found users with a similar problem. To fix it please do the following and post what you see here.

Right click the applications menu, and go to edit menus.
Then go through the menues to find the application you are trying to start.
Right click on that application and click properties.
After that please post here what is located in the box named "Command"

---

### Post by creistre on 2008-11-04
Hi,

I have been having the exact same problem on a clean and fresh install on 8.10.

Following your instructions the command reads:

su-to-root -X -c /usr/sbin/wifi-radar

---

### Post by moliones on 2008-11-04
I believe you need to install the 'menu' package to get that program.

```
sudo apt-get install menu
```

---

### Post by jdelcom on 2008-11-12
I was having the same problem, and I installed the menu as suggested. Now when I run wifi radar, it asks me for a password, and then NOTHING. If the application is running, I can't see where. If it's not running, what happened? I used wifi radar with other versions of Ubuntu without a problem.

Any ideas?

I already uninstalled and reinstalled WFR after the installation of menu.

thanks!

---

### Post by stephanvaningen on 2008-11-12
What about replacing the words 'su-to-root' with gksu using the menu-editor?

---

### Post by jdelcom on 2008-11-19
Nothing changed with gksu. Any alternative to wifi radar to look for wifi networks?

---

### Post by jdelcom on 2008-11-19
apparently there's another problem with the Atheros wifi cards. I'll check that and will come back if THAT solves the problem or not.

---

### Post by jdelcom on 2008-11-19
I changed the drivers from "support for Atheros 802.11 wireless cards" to "Support for 5XXX series of Atheros 802.11 wireless cards" and nothing. The wifi doesn't appear in the network icon left of the date, uninstalled and reinstalled wifi radar but it still doesn't work, neither changing su-to-root with gksu.

---

### Post by jdelcom on 2008-11-19
Ok, so it was a weird turnaround. My wifi card wasn't working properly. I finally made it work using this: [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

Now Wifi Radar is working. Haven' tried any network yet, will do when I get home.

---

### Post by andddlay on 2009-01-14
I would like to report my findings.  I got this same error.  I just successfully opened up Wifi-Radar, though, by doing these simple steps:

Open Terminal
Type "sudo wifi-radar"

Because I don't want to do this every time to run this application, I right clicked applications, clicked the internet tab on the left (where WiFi-Radar was saved), clicked properties, then typed "sudo wifi-radar" into the command line.

Easy enough!

---

### Post by conradin on 2009-12-30
Hi, I was having a similar issue with "Failed to execute child process "su-to-root" (No such file or directory)" via GSmartControl.
I used the code:
```

sudo apt-get install menu

```

And it works fine now. Thanks Guys!!:)

---

### Post by tobjai on 2010-10-24
> **Axis said:**
> I have found users with a similar problem. To fix it please do the following and post what you see here.

Right click the applications menu, and go to edit menus.
Then go through the menues to find the application you are trying to start.
Right click on that application and click properties.
After that please post here what is located in the box named "Command"


I have the same issue with an application called foomatic-gui. When I go to the box named "Command" (as instructed above) I find the following: 

su-to-root -X -c /usr/bin/foomatic-gui

Anyone able to help?!?

---

