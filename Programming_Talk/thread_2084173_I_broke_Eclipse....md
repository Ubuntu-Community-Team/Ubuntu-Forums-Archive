---
title: "I broke Eclipse..."
date: 2012-11-14
forum: Programming Talk
---

### Post by Thunder7102 on 2012-11-14
Well, intelligent me, knowing little to nothing about programming, decided that updating is always good so I updated Eclipse. To my own sadness, I quickly came to realize that afterwards, I believe Eclipse detached itself from Java's SDK (or that is my own theory) and now has no idea how to compile or execute my programs (or read them for errors). I cannot Run any code I have made in the past (which is not all that advanced anyhow). 

So far, I have tried running Eclipse -clean and uninstalling and reinstalling, but to no avail. Any ideas? If there is a quick and easy fix, I'd be really happy. I am new to Java programming and Eclipse at the same time so thats...never a good combination.

---

### Post by 3v3rgr33n on 2012-11-14
When you go to Preferences, is Java listed in the panel on the left edge?

---

### Post by Thunder7102 on 2012-11-14
> **3v3rgr33n said:**
> When you go to Preferences, is Java listed in the panel on the left edge?

I see: 

[LIST]
[*]General
[*]Help
[*]Install/Update
[*]Run/Debug
[*]Team
[/LIST]

---

### Post by kevinharper on 2012-11-14
I broke mine too.

I was "doing something to my Android" and all of the sudden Java was no longer listed on the left hand side. I have everything that I need installed, I can't create a Java project to save my life, though. 

To everyone else's defense, made so many modification and tried so many things to get the Android DK to work that I have no clue what I did that broke it. I figure all will be good when I update to Ubuntu12.10 in about a month.

Currently running Eclipse on XP via Virtual Box.

---

### Post by r-senior on 2012-11-15
Eclipse is a great IDE but IMHO it's approach to plugins is a mess and always has been. This is why subscriptions like MyEclipse exist. Netbeans is much better with plugin compatibility (even if they aren't always as good) but doesn't look great on GTK. 

I just avoid the problems by downloading SpringSource Tool Suite (which is a custom Eclipse ostensibly for Spring Development but has the "right" plugins for general Java and Java EE). Even then, I use a backdated version (2.9.2) because the "modern" user interface on the later versions is slow. I also "install", i.e. unpack the archive, it in my home directory somewhere because I don't find it works well as a repository install, not that I've tried recently.

Anyway, I digress. The point is that Eclipse plugin dependencies are problematic, not just for beginners.

If Eclipse has lost its reference to a JDK, the section in Preferences (Window | Preferences) to check is as shown on the attached screenshot. (The search box at the top is a good way of finding things in the preferences hierarchy).

---

### Post by danthemanvsq on 2012-12-10
I have the same problem except my breakage came after I checked out a project from my repository. After completing the checkout I lost all syntax highlights on my text editor and upon investigation lost the connection with Java. I tried reinstalling even deleting the .eclipse folder and the workspace but still no luck. Please let me know if you find a solution.

---

