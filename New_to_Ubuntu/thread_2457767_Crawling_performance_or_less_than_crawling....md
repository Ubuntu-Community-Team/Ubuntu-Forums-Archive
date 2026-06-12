---
title: "Crawling performance or less than crawling..."
date: 2021-02-08
forum: New to Ubuntu
---

### Post by Innernet on 2021-02-08
Greetings.

It happens whenever it wants, perhaps a couple of times a week.:confused:

To get a response from mouse, or keyboard, or anything several _minutes _must pass.   For the third time I noticed that it coincides with the presence of the "Software update"  "icon circle A" popping at the bottom tray.
Opening such, it peddles to install a "security update"  to which I have repeatedly said NO.  Today was a something like 173KB.  I did **not** install trying to find settings to forbid it. I prefer the risk of whatever not-installed 'security' than dealing with an unresponsive machine.

**How to forbid to even check** for the existence on any critical or not security or not updates ?  Today I prepared my lunch waiting for the compfuser to react.  It even went to Firefox browser **by itself ** stuck begging for cookies approval from Canonical when I was using Opera, making things much worse.  Like the denial of installing is done only on Firefox.  Both browsers open = shortcircuit?

I do not see anywhere how to stop the automatic push for whatever the system wants to do.  The settings show no option to stop that 'security' updates,  On 18.04 I was able to stop every update.
If it is a good thing to update, it happens in the worst possible way :  stops all from responding and does NOT tell the user what is happening, if anything is happening at all.  Confirmed 'Livepatch' is disabled, never engaged 'Snap' either.
The message "Software updates are available, do you want to install now ?"  is missing the NO or NEVER button.

[ATTACH=CONFIG]287929[/ATTACH]

By the way; besides the 'circled A' there is a 'coat hanger', a 'carton with a globe' and a 'shopping bag' icons all related to Software.  Why that many ?  Would it be better a single one and show 4 choices when opened ?


Edited...  Closed all the 'updates' icons and applications;  everything is back to normal speed.

---

### Post by ajgreeny on 2021-02-08
What you are seeing is I believe the result of your system using the ***unattended-updates*** package to do exactly what it says; it updates any security packages that have available updates with no action from the user, ie, unattended.

For most users this is a great idea, removing from them the need to check for updates and then run the update process for packages that are deemed important to maintain the system's security.
However, should you wish to stop this occurring, and take on the onus of running the updates daily yourself, you can do so by uninstalling the unattended-upgrades package, but please, from then on, make sure that you take seriously the responsibility you have placed upon yourself to keep your system fully updated very often, if possible every day that you use it.

---

### Post by CatKiller on 2021-02-08
> **Innernet said:**
> To get a response from mouse, or keyboard, or anything several _minutes _must pass.  
That sounds like out of RAM.

---

### Post by ajgreeny on 2021-02-08
> **CatKiller said:**
> That sounds like out of RAM.
Good point! It could also be that.

What hardware do you have?
Show us the output of ```
inxi -Fzx
```

---

### Post by Innernet on 2021-02-08
Out of RAM... :shock:  perhaps when the 'software updater' jumps in; because without it, everything runs well.

[ATTACH=CONFIG]287930[/ATTACH]

---

### Post by CelticWarrior on 2021-02-08
```
sudo **apt** install inxi
```
- Obviously -.

---

### Post by Innernet on 2021-02-08
Obviously for the experts and knowledgeable.  This is the **beginners** forum.

[ATTACH=CONFIG]287931[/ATTACH]

---

### Post by CelticWarrior on 2021-02-08
Please post code, not screenshots.
Use the Go Advanced button instead of quick reply, then press "#" and paste inside.
The main problem here is the parts missing. We still don't know the amount of memory it has. However, we know it's a Presario CQ57 that, according to the official [specifications]("https://support.hp.com/uy-es/document/c03151649") it has (originally) only:
> [COLOR=#000000][FONT=HPSimplifiedLight]SDRAM DDR3 de **2 GB** (2 DIMM)[/FONT][/COLOR]
So, unless upgraded, 2GB is notoriously insufficient nowadays. There are already people saying that 4GB isn't enough...So, yes, what you're reporting is consistent with lack of RAM and, as consequence, lots of swapping in a old 5400rpm HDD.

---

### Post by Innernet on 2021-02-08
Unable to attach a second image of the terminal with the rest of the report. 

Copied and pasted:


 ```
IF: enx00e04c682bd3 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 149.05 GiB used: 25.74 GiB (17.3%) 
  ID-1: /dev/sda vendor: Toshiba model: MK1652GSX size: 149.05 GiB 
  temp: 36 C 
Partition:
  ID-1: / size: 145.71 GiB used: 25.74 GiB (17.7%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 45.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 226 Uptime: 4d 7h 19m Memory: 1.73 GiB used: 1.08 GiB (62.6%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 
externet@externet-Presario-CQ57-Notebook-PC:~$
```

---

### Post by CelticWarrior on 2021-02-08
Again, please use code tags as explained before. Do NOT attach images.

Nothing else to add to the previous post but this [https://ubuntuforums.org/showthread.php?t=2441906&p=13951436#post13951436](https://ubuntuforums.org/showthread.php?t=2441906&p=13951436#post13951436) has been suggested before and ignored. Vanilla Ubuntu (with Gnome) is too much for that old machine, especially if it has only 2GB RAM.

Honestly, I don't know what you're complaining about.

---

### Post by Innernet on 2021-02-08
'Notoriously insufficient' is major words !   Will then have to check availability of bigger RAM that my machine can accept.

Was typing when your instruction 'please post code, no screenshots' showed up.  Did not see it on time, sorry.  The instruction to transfer the terminal contents to the attachments manager was unknown to me.  Will use it in the future.
Thanks.

---

### Post by CelticWarrior on 2021-02-08
According to the specifications it supports up to 8GB DDR3 (2x4GB) (~50USD). I wouldn't make such investment but it's your computer, your decision.

---

### Post by Innernet on 2021-02-09
Thank you.
SOLVED.   After 16 years operating Ubuntu, migrated to Lubuntu 20.04.  All smooth fast sailing... for now until I goof somewhere.

---

### Post by CelticWarrior on 2021-02-09
Lubuntu with LXQt requires less memory than Ubuntu with Gnome thus leaving more memory for the running programs. Also less demanding of the graphical subsystem thus contributing to a *snappier *experience. It isn't however a solution for the memory limitation as that is only solvable with more memory. Many programs, especially web browsers, need now a lot more more RAM than they did a decade or so ago.

---

### Post by Innernet on 2021-02-09
Thank you Celtic Warrior.
I will prefer in the future to get a new compfuser instead of just upgrading the memory in my old one.  Will see how Lubuntu behaves in the next weeks; so far has the very fast, simple behavior of ten+ years ago Ubuntu flavor that has been hurdling more every year even my ultralean usage.
Finding a modern machine that fits me will be another task.  Optical drive built in; no fan/no heat; removeable hard drive; ethernet port...

---

### Post by ajgreeny on 2021-02-09
Great news! I'm glad you got this sorted out and can again use the computer.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by blackbird34 on 2021-02-11
I'll just add my two cents: I used to have a Compaq Presario CQ56 (almost identical, Celeron processor, 2GB RAM). GNOME is too much for that processor so I installed XFCE instead, but KDE (Kubuntu) would probably be OK too. 

You could install an extra 4GB RAM stick and an SSD and it would be a major improvement for peanuts (probably less than €50)

---

