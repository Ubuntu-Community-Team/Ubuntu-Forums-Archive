---
title: "Nautilus status bar."
date: 2013-04-28
forum: New to Ubuntu
---

### Post by frup on 2013-04-28
I notice that in 13.04 Nautilus no longer has a status bar.

How am I supposed to know how much space files within a directory take up and how am I supposed to know how much free space is remaining on the disk? After about 8 years of using linux I'm beginning to find Ubuntu damn confusing at times.

---

### Post by vanadium on 2013-04-28
Gnome devs perhaps considered this is information that you do not need all the time while you are just doing your daily work with data and files. If you want to know, do a Ctrl+A. The information appears in a yellow label at the bottom. To know how much a folder and underlying folders occupy, highlight the folder and press Alt+Enter (or right-click, properties - the latter can also be done from within the folder, right-clicking an empty space).

---

### Post by Frogs Hair on 2013-04-28
A few options here:   [http://askubuntu.com/questions/73160/how-do-i-find-the-amount-of-free-space-on-my-hard-drive](http://askubuntu.com/questions/73160/how-do-i-find-the-amount-of-free-space-on-my-hard-drive)

Archey:[http://www.distrogeeks.com/install-archey-in-ubuntu/](http://www.distrogeeks.com/install-archey-in-ubuntu/)

---

### Post by frup on 2013-04-30
Thanks for the info guys, I looked at some of those options, but the fact of the matter is that in my opinion I should be using one application to manage my files not many. 

I'll withhold from ranting about my complaint but I am really not impressed.

---

### Post by ktucker on 2013-05-04
I have been using Thunar recently to be able to see space available easily, but don't see how to customise columns in file lists (and see permissions, for an example of one of the trade-offs).

---

### Post by marko-palojarvi on 2014-02-02
One selected line in Nautilus and yellow label hide last line. Only unselect (shift+ctrl+a) make last line of the file list visible again. Still statusline is what I prefer in Nautilus because when scrolling long list yellow label is something what I do not want to see at all. Application preferences or dconf doesn't give me option to change this. Is there other ways to do it?

I found a post how to downgrading Nautilus (again I did it already in 12.10). I installed Nemo and found also Nemo's F3 for extra panel is very handy with Unity desctop combo ctrl+super+<arrow keys>.  Nemo has status bar by default. More info of downgrading:

[http://askubuntu.com/questions/360831/downgrade-to-nautilus-3-4-from-ubuntu-13-10-nautilus-3-8](http://askubuntu.com/questions/360831/downgrade-to-nautilus-3-4-from-ubuntu-13-10-nautilus-3-8)

---

### Post by Hyrr_Climaxx on 2014-11-04
Hi,

I had the same problem when upgrading form Ubuntu 12.04 to 14.04 - I missed the status bar that displayed the remaining free disk space, although you still have an overlay of disk usage for files when selecting the files ( Nautilus 3.10 ).

After I couldn't find any resource on the Internet that worked out of the box, I decided to code a minimal version of the status bar that showed the free disk space and I'll post a link here if anyone is interested:

[https://github.com/climaxx/Nautilus-Status-Bar-Replacement](https://github.com/climaxx/Nautilus-Status-Bar-Replacement)

You just copy the plugin in the plugins folder (see readme file for details).

Hope it helps. :)

---

