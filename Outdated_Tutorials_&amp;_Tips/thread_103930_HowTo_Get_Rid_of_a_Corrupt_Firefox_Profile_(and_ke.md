---
title: "HowTo Get Rid of a Corrupt Firefox Profile (and keep the bookmarks)"
date: 2005-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2005-12-15
It happens in Windows. It happens in Mac. And... it also happens in Linux (and Ubuntu, specifically). Sometimes, your Firefox profile gets corrupt. You can't launch Firefox. The pages look all weird. Maybe it was the extensions you installed. Maybe it was something else.

Bottom line: for whatever reason, you need to start anew.

First get the **Run** command going (Alt-F2), then type ```
firefox -safe-mode
``` Once Firefox launches up, go to Bookmarks > Manage Bookmarks > File > Export, and save bookmarks.html to your desktop.

Then, open a terminal...
In Breezy or Dapper, Applications > Accessories > Terminal
In Hoary, Applications > System Tools > Terminal
In Kubuntu, KMenu > System > Konsole

Type this command to back up your corrupt profile (just in case): ```
mv ~/.mozilla ~/.mozilla_backup
```

Finally, launch Firefox again (click on the icon). Go to Bookmarks > Manage Bookmarks > File > Import and get the bookmarks.html you saved before on your desktop.

---

### Post by pshnfry on 2006-04-29
There doesn't seem to be enough steps above, by "finally, launch firefox again..." do you mean re-install or just click the firefox icon?

---

### Post by aysiu on 2006-04-29
[QUOTE=pshnfry]There doesn't seem to be enough steps above, by "finally, launch firefox again..." do you mean re-install or just click the firefox icon?[/QUOTE] Sorry for being unclear. It means just click the Firefox icon. I've edited the original post.

---

### Post by ????? on 2006-06-10
I would also suggest that if you use Adblock (plus), TMP, Noscript, etc you would export those filters/settings/whitelists as well so you don't lose them.

---

### Post by aysiu on 2006-06-10
That's a good idea in theory, but I think (correct me if I'm wrong) that safe mode disables your extensions.

I always back up my Adblock and NoScript settings on a regular basis.

---

### Post by guine on 2006-06-20
I gave this a try because Ive been having troube with firefox crashing whenever I click links on certain sites and Im still having problems.  Do you have any other ideas of how to fix this?  Thanks.

---

### Post by ????? on 2006-06-20
Yes, extensions are disabled.. but you can still grab your adblock plus filters

Install adblock plus on the new profile, then copy the adblock plus filters (unsure of the location of adblock)

```
cp ~/.mozilla_backup/firefox/*.default/adblockplus/patterns.ini ~/.mozilla/firefox/*.default/adblockplus/patterns.ini
```

---

### Post by Psquared on 2006-09-19
Actually, just launching Gmail is causing FF to crash on my Linux box. It isn't the extension. Opera does not work well enough as a replacement as it can't handle hotmail very well.

---

### Post by fragos on 2006-09-29
Don't know if this is your proplem but, since 1.5.0.7 update, firefox has occasionally gotten a segment fault when starting and nothing happens on the desktop.  I've started it with "firefox www.google.com" when this occurs.

---

### Post by wog on 2006-10-01
Firefox just gives me a segmentation fault when I try to run it. Adding a first page for it to go to does nothing different. The "-safe-mode" switch doesn't keep it from crashing. Moving the .mozilla folder to backup doesn't change it. Uninstalling and reinstalling also doesn't change the result. It just seems to be dead.

---

### Post by fragos on 2006-10-01
I've run into that a few times since the last update.  Experimenting with the command line to see error messages I found that if I gave firefox an argument it would start and seemed to straiten itself out.  I used "firefox www.google.com" because I'm sure that's a good well formed site.

---

### Post by hackeron on 2006-11-18
hackeron@ubuntu:~$ firefox -safe-mode
Bus error (core dumped)

---

### Post by aysiu on 2006-11-18
> **hackeron said:**
> hackeron@ubuntu:~$ firefox -safe-mode
Bus error (core dumped)
I'm not seeing many solutions, but [a Google search of your error turned up about 35 results](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%22Bus+error+%28core+dumped%29%22+firefox&btnG=Search). A lot of BSD users, some Epiphany users, and a lot of stuff about building Firefox...

---

### Post by upinVermont on 2006-12-17
This post was just recommended.

Ever since Firefox installed Macromedia Flashplayer (which was the first time I used Firefox in Linux, which was at the first website, CNN, I visted) Firefox crashes without warning.

How do I simply *delete* the Mozilla profile? I'm trying to return Firefox to its pre-anything state.

(I have already tried re-installing via Synaptic Package Manager, to no avail.)

---

### Post by aysiu on 2006-12-17
```
rm -r ~/.mozilla
``` should delete the Firefox profile completely.

---

### Post by hackeron on 2006-12-21
Removing the mozilla profile makes firefox start again, but after a few minutes of use, Bus error (core dumped) again :(

Removing ubuntu-desktop and going to xubuntu-desktop solved the problem - moving back to ubunbu-desktop resurrected the problem - still trying to figure out what exactly is causing the problem.

---

### Post by hackeron on 2006-12-21
> **hackeron said:**
> Removing the mozilla profile makes firefox start again, but after a few minutes of use, Bus error (core dumped) again :(

Removing ubuntu-desktop and going to xubuntu-desktop solved the problem - moving back to ubunbu-desktop resurrected the problem - still trying to figure out what exactly is causing the problem.

Aha! -- I did 
```
apt-get remove ubuntu-desktop firefox-gnome-support
```
and presto, firefox starts again, now to figure out exactly what in firefox-gnome-support broke my firefox and why it worked before - I don't have any extensions installed or anything like that, hmmmm

---

### Post by Halfling Rogue on 2007-07-28
> **????? said:**
> I would also suggest that if you use Adblock (plus), TMP, Noscript, etc you would export those filters/settings/whitelists as well so you don't lose them.

Actually, I've found that Adblock Plus can crash Firefox too. I had it installed once, and had to remove it because it was keeping FF from opening at all. Once I got rid of it the problem stopped.

Although now I'm having problems with Firefox just closing itself with no error message at all. I've heard some talk that it might be the Flash plugin, but I'm not sure, especially because it didn't seem to start happening until after I updated my system via the Synaptic Package Manager (I just marked all upgrades and then let it run them). Might try getting rid of ubuntu-desktop as suggested above, though.

---

### Post by pmorton on 2007-11-12
I've just started experiencing the same problem. I've apt-get removed ubuntu-desktop and firefox-gnome-support. I've removed all add-ins; I've deleted ~/.mozilla, but firefox still keeps closing on me. Anyone got any further ideas?

---

### Post by fragos on 2007-11-12
I had this problem once -- it eventualy went away.  I did manage to get Firefox to start if I dragged a text file to the Firefox icon.  Firefox came up with the text file displayed and then worked for the rest of the session only.  I have no good explanation why this worked but it did.

---

### Post by someoneouthere on 2008-01-09
thank you so much!!!

---

