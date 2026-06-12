---
title: "Why does my Ubuntu slow down?"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by heehoo on 2012-03-15
It seems that about an hour after I'm on the screen goes black, then comes back on and is much slower. So much so, I have to restart the machine. I have Ubuntu 11.10 and it does this almost every time. Is there anything I can do to stop this? Any help would be appreciated.

---

### Post by royalprakash on 2012-03-15
**[SIZE=2]Disable unused startup programs.[/SIZE]**

[COLOR=#008000]**system -> Preferences -> Startup Applications**[/COLOR]
[COLOR=#008000]**and**[/COLOR]
sudo apt-get install preload

---

### Post by heehoo on 2012-03-15
Thanks, I couldn't find my preferences so I just entered the text in the terminal... much appreciated.

---

### Post by heehoo on 2012-03-15
The other problem I have is this - I visit a webpage that has a lot of text, and sometimes, the page freezes for a few seconds, then unfreezes but the comp is slower and I have to restart. I wonder why that is. :(

---

### Post by Peripheral Visionary on 2012-03-15
I'm having the same issue with Xubuntu, but I haven't said anything because I'm testing 12.04. It slows down over a few hours, and a reboot "fixes" it (temporarily). It seems that mere "up time" is all it takes to slow everything down.

---

### Post by heehoo on 2012-03-15
^^That's me in a nutshell. I just wish I could pinpoint what it is that's causing this. I like the system but don't want to have to downgrade because of it.

---

### Post by tbhatia4 on 2012-03-15
> **heehoo said:**
> It seems that about an hour after I'm on the screen goes black, then comes back on and is much slower. So much so, I have to restart the machine. I have Ubuntu 11.10 and it does this almost every time. Is there anything I can do to stop this? Any help would be appreciated.

which graphic card is there in your system???

---

### Post by madjr on 2012-03-15
Hardware Specs and how much ram you have please as you havent given us this info yet.

---

### Post by heehoo on 2012-03-15
2 gigs or ram, and I am guessing the hardware is Pentium 4 (?)

---

### Post by Peripheral Visionary on 2012-03-16
> **Peripheral Visionary said:**
> I'm having the same issue with Xubuntu, but I haven't said anything because I'm testing 12.04. It slows down over a few hours, and a reboot "fixes" it (temporarily). It seems that mere "up time" is all it takes to slow everything down.

**UPDATE:** Well as it turns out my efforts to install it while preserving a separate /home partition were the culprit. I think. A brand new installation giving it the entire drive may have solved the problem... I'll let y'all know tomorrow after this computer has had a few hours of up-time!

---

### Post by Rodney9 on 2012-03-16
Browsers are infamous for leaking memory.

Rodney

---

### Post by Peripheral Visionary on 2012-03-16
> **Rodney9 said:**
> Browsers are infamous for leaking memory.

One browser in particular, lol. I think I'll try some others on for size. Midori, Chromium, Opera, maybe even Seamonkey (I heard that's the old Netscape browser, resurrected by some folks at Mozilla).

---

