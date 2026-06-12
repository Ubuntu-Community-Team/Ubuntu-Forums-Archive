---
title: "General question for finding help online"
date: 2022-04-12
forum: New to Ubuntu
---

### Post by Jeff_Rockel on 2022-04-12
Greetings: I have used Ubuntu in the past and have a general knowledge of Linux. It has been several years since I have used Linux and am now using lubuntu 20.04. I realize the Linux mindset is very different than the W**dows mindset and as a programmer of old, I appreciate that. (Yes, I even know what the GNU acronym stands for.)

So here are three questions that I want to know how I should search for answers in the manual and in the forums:
1) I needed to format a USB drive but couldn't find a disk utility in the menus. All help pages said to find it there. But apparently gnome-disk-utility is not in 20.04. **How would I find that this utility is or isn't in this version?**
2) My Trash icon show "Trash (29 items)" on the desktop. When I open Trash, there are only two items there. [B]How would I search to learn why this discrepancy exists?
[/B]3) When I hover over an icon, I see a minus (-) symbol in the upper left hand corner. If I click on that symbol, it changes to a plus (+). **How would I search to find out what the symbol's function is?**
4) In trying to understand desktop icons, I found this "Open File Manager -> Click on “+ Other Locations -> Computer” and navigate to  “/usr/share/applications.” You will find many files with the “.desktop”  extension." In PCManFM-QT the file extension is not shown (as in W**dows-ouch!) but is represents in the Type column by "desktop configuration file". I looked in the lubuntu manual and don't see a way to get a simple listing (as I can in W**dows). **How would I search for a file manager that is more Linux like and displays the full file name?**

If you are still reading, I greatly appreciate your patience. Any help to get me into the Linux mindset would be awesome.

---

### Post by TheFu on 2022-04-12
As for why things are the way they are, that is usually due to history.  The current Lubuntu has some history for why they completely switch from using GTK+ toolkit to using Qt toolkit a few years ago.  Basically, they changed from using the GUI libraries that Gnome uses to using the GUI libraries that KDE uses.  With that change, many of the Gnome tools are being avoided to reduce the memory footprint.  20.04 Lubuntu is based on Qt, so most of the tools that should be included by default will be from the KDE DE family, not Gnome.  Programs that start with 'q' or 'gnome' will be less seen on LXQt (Lubuntu) and KDE (Kubuntu) systems.

1) Gnome has a habit of renaming programs to be simple - what-they-do.  Look for "Disks" in the menu.  OTOH, "Disks" seems to cause more issues that it solves. To avoid that, use **gparted**.  Gparted can partition, format, label, wipe, clone, pretty much everything except, mount.  

2) Trash.  That's extremely DE dependent. There are a number of different Trash implementations out there.  I don't use any, so cannot help.  Trash is a per-partition thing. So if you have multiple partitions, at the top level of the mount for that specific partition, there will be a .Trash/ directory.  The reason behind this is to avoid moving deleted files between different file systems, which can take a very long time for huge files. Use the trash delete function to have those removed files truly deleted ... or just disable trash and have automatic, daily, versioned, backups. then when you need to get a file back that 1-2 times every year, it is in the backups.

3) That's another GUI question and it is very specific to the DE being run.  Sorry. I cannot help.

4) That's another GUI question and it is very specific to the DE being run.  I don't know what you mean by "more Linux like". Care to explain clearer? If you want to search by filename, learn to use **locate**.  The name of the package has changed over the years. locate, mlocate, updatedb ... usually by running a command in a terminal, the package manager will suggest a package to install if it is missing. But **locate** has always been the end-user program name. It is very handy and available on all Unix systems - desktops, servers, whatever. It if extremely fast, since it uses an index.  If you need to find a new file, then 'find' is the only way I know to search with an amazing number of options to find just the file(s) we seek. Again, find is a CLI program and available on all Unix systems.

Don't fear the shell.  GUIs only provide 20% of the power in Unix. The other 80% is in the shell.  Plus, if you learn to do things in a shell, that knowledge works on any DE, desktop or server. You won't have to hunt/search for ways to do the same thing every 3 yrs when the GUI team gets bored and decides to revamp everything "just because."  That's all wasted time, to me.  I want to be productive and don't want the GUI limiting me or getting in the way.

BTW, I hadn't thought about the issues that you've ask too much before today. Good question.  If the answer isn't in the Lubuntu or LXQt manual, I bet there's an Lubuntu forum on a different website. It won't have the same amount of traffic we see here, but for LXQt questions, they will probably be more knowledgeable.  

There are a few active members here with Lubuntu knowledge. Hopefully, they will post too.  BTW, you should have picked a better thread title - "20.04 Lubuntu GUI questions" - that would have provided information that people with that specific knowledge would see and could respond better than me.  I expected, before ever reading the post, that you were looking for general 'where to find information about Ubuntu online'.  I was ready to say
* Look for domains with 'ubuntu' in the domain part of the name. Linux isn't specific enough, since, especially for the GUI, there are vast differences almost always.  At a shell, 90% of Linux is the same. It used to be higher, but Canonical has been pushing a different packaging system that hasn't caught on anywhere else - snap packages. I don't know if Lubuntu uses snaps or not. Soon, 22.04, there won't be much choice, since even Firefox will only be available as a snap package inflicted onto us.
* look based on the specific release version being used, since things change between releases. Answers for 22.04 and 20.04 and 18.04 are often very different. Of course, sometimes they are exactly the same, but if you haven't been active and know recent history, then it is hard to know which areas are the same and which are not.

That's probably enough for now.  Some other people should post with their answers. We all have different experiences, so they will probably have the GUI stuff better.

---

### Post by &amp;KyT$0P# on 2022-04-12
> **Jeff_Rockel said:**
> 1) I needed to format a USB drive but couldn't find a disk utility in the menus. All help pages said to find it there. But apparently gnome-disk-utility is not in 20.04. **How would I find that this utility is or isn't in this version?**

Run this command in Terminal -
```
apt-cache search gnome-disk-utility
```

If you prefer a GUI, it is possible to search for packages in either Synaptic or Muon if you have one of those installed.

(Personally I prefer to do actual formatting with GParted.  My use of gnome-disk-utility is limited to only viewing information.)

> 2) My Trash icon show "Trash (29 items)" on the desktop. When I open Trash, there are only two items there. **How would I search to learn why this discrepancy exists?**

Before searching I would start by making sure your file manager is showing hidden items when viewing trash.

> 3) When I hover over an icon, I see a minus (-) symbol in the upper left hand corner. If I click on that symbol, it changes to a plus (+). **How would I search to find out what the symbol's function is?**

Start with "[COLOR="#FF0000"]<name of the program where this occurs>[/COLOR] minus plus symbol" in your favorite Internet search engine.  If that doesn't get anywhere, tweak the keywords slightly (maybe try icon instead of symbol, try corner, try marker, etc) until you find a combination that finds a link that explains it.

> 4) In trying to understand desktop icons, I found this "Open File Manager -> Click on &#8220;+ Other Locations -> Computer&#8221; and navigate to &#8220;/usr/share/applications.&#8221; You will find many files with the &#8220;.desktop&#8221; extension." In PCManFM-QT the file extension is not shown (as in W**dows-ouch!) but is represents in the Type column by "desktop configuration file". I looked in the lubuntu manual and don't see a way to get a simple listing (as I can in W**dows). **How would I search for a file manager that is more Linux like and displays the full file name?**

I don't use a file manager for that.  I use [FONT=Courier New]ls[/FONT] command in Terminal.

If I wanted to search for such GUI file manager, I would boot a disposable/snapshotted VM of the same OS, then use any of the methods from my answer to your (1) to do a general search of the repositories for file managers, and actually install & try the ones I didn't already know.

---

### Post by GhX6GZMB on 2022-04-12
Let me chime in as longer-time Lubuntu 20.04 LTS user.
I expect the reason for using Lubuntu is due to the GUI. Otherwise you could just install Ubuntu-Server. Or?

So why do you insist on using Gnome applications? That makes no sense at all.

Lubuntu has a fine setup and infrastructure of all the useful applications that you'd need:
PCManFM-QT: file manager.
Muon: package manager.
Htop: task manager.
QTerminal: terminal.
Featherpad: text editor.
KDE Partition Manager: self explaining.
And so on. They're all in the Applications menu (lower left, blue button).

Forget the Gnome stuff, you're muddling things. Use the KDE tools together with the Qt additions and you'll be fine.

But I suspect the best solution is a complete reinstall with a fresh mindset.

Cheers.

---

### Post by guiverc on 2022-04-12
Lubuntu uses the LXQt desktop.

Using a utility such as `gnome-disks` which is a GTK3 application, would be inefficient and waste system resources.  As such Lubuntu uses a Qt5 utility called [KDE Partition Manager]("https://manual.lubuntu.me/lts/3/3.1/3.1.7/kde_partitionmanager.html")

If you have the RAM (ie. *sufficient resources to waste having multiple libraries/toolkits that do the same thing residing in memory at the same time*) you can add `gnome-disks` to your system & use it. If you just prefer `gnome-disks` as it's what you're used to, that's fine (*I use it myself on occasion*).

FYI:   In the past when Lubuntu used LXDE which was a GTK2 desktop; `gnome-disks` made sense as a GTK3 program made more sense than a Qt5 app; which is why releases up to Lubuntu 18.04 LTS used it. Lubuntu 18.10 & later though use LXQt & Qt5.

Re:trash  I cannot speak with authority as I know little about your machine; I wonder if it was items you removed whilst you had USB type removable drives inserted which can still be restored; when those thumb-drives are inserted your visible count will likely increase; but I usually remove files from terminal, or when I use GUI tools I always clean trash before ejecting/removing any external media.

File Managers is a personal choice.. The app `pcmanfm-qt` is the program which actually draws & handles much of the LXQt desktop (if you have any icons on the screen it's handling them, your wallpaper etc) thus it already resides in your machine memory when LXQt is running, even if you don't have it open as a file-manager.. Using it is *light* on resources (*given the desktop will use it anyway*).  There are a few Qt5 ones made for KDE that may make sense, but as they'll require KF5 (*KDE Frameworks which LXQt doesn't use*) you'll be using more RAM, eg. `dolphin`.   Myself I like `thunar` from Xfce but being GTK3 it's quite a resource hit.  You'll have to decide based on your needs & resources your box has (esp. RAM).

---

### Post by oldos2er on 2022-04-13
Use ```
apt search <keywords>
```, search in Synaptic Package Manager (I think that's installed by default on Lubuntu still), or at [https://packages.ubuntu.com/](https://packages.ubuntu.com/). 

Btw, Windows is not a dirty word here, no need to self censor.

---

