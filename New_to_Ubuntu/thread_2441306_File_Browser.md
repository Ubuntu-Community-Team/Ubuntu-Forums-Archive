---
title: "File Browser?"
date: 2020-04-22
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2020-04-22
What is a file browser?

Is it like Microsoft's notepad or is it like their Windows Explorer?

lol...I really need something like a Ubuntu thesaurus or a Windows-Ubuntu/Ubuntu-Windows dictionary...rofl

Heck, maybe even both

---

### Post by guiverc on 2020-04-22
File Browser has many names, it was "File Manager" in early versions of windows, which became Windows Browser once the 'browser' became 'trendy' and Microsoft was accused of missing the boat (win95; where in 1994 the most popular software was Netscape Navigator or a Browser for the web, but windows 95 was released without an internet browser).

There are many File Browsers on Ubuntu, eg. `nautilus` (the default for GNOME & Unity desktops), `caja` (MATE), `thunar` (XFCE), `pcmanfm` (LXDE), `pcmanfm-qt` (LXQt), `dolphin` (KDE), etc.

Some documentation for Ubuntu does refer to it as file manager, eg. [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

Maybe helpful, I'll provide [https://help.ubuntu.com/stable/ubuntu-help/files-browse.html.en](https://help.ubuntu.com/stable/ubuntu-help/files-browse.html.en)

However I don't know how to usefully respond sorry.  Maybe someone else can.

---

### Post by wyattwhiteeagle on 2020-04-22
> **guiverc said:**
> File Browser has many names, it was "File Manager" in early versions of windows, which became Windows Browser once the 'browser' became 'trendy' and Microsoft was accused of missing the boat (win95; where in 1994 the most popular software was Netscape Navigator or a Browser for the web, but windows 95 was released without an internet browser).

There are many File Browsers on Ubuntu, eg. `nautilus` (the default for GNOME & Unity desktops), `caja` (MATE), `thunar` (XFCE), `pcmanfm` (LXDE), `pcmanfm-qt` (LXQt), `dolphin` (KDE), etc.

Some documentation for Ubuntu does refer to it as file manager, eg. [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

Maybe helpful, I'll provide [https://help.ubuntu.com/stable/ubuntu-help/files-browse.html.en](https://help.ubuntu.com/stable/ubuntu-help/files-browse.html.en)

However I don't know how to usefully respond sorry.  Maybe someone else can.

Thanks a bunch.

I was looking into coming up with a backup strategy that suits me, well I came across a post that included a link to the Ubuntu Recover Lost Disk Space...
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Under "Tips Before You Start", It includes the following...

```
**2. Deletions**. When deleting  folders/files from within a file browser such as nautilus remember that  the deleted folders/files are
moved to the Trash bin. Until you empty  the trash, these files will continue to use disk space. Use one or more  of these methods to 
permanently remove these files:

[INDENT]1. In a **file browser**, use SHIFT-DELETE to bypass the Trash bin.
[/INDENT]

```

I checked Google, Alternatives, Ubuntu Software...I even checked Gnome Help.

File Manager came up in the results for everywhere I searched, but the terms "Manager" and "Browser" seems to mean 2 different things. At least in my thinking anyway...lol

Again...thank you :)

---

### Post by cmcanulty on 2020-04-22
File Manager or File Browser is merely the list of every file and folder or directory on you computer. I has all the operating system files and all of your personal files. Your files are normally in the directory/home/username there you will find your pictures and all documents in subfolders like pictures, videos, etc. Some files are hidden and are usually system or user settings and can be displayed by finding the options list and saying show hidden files. Ubuntu user Nautilus file manager by default, xubuntu user thunar. other managers can be installed depending on your preference for the way the interface looks or operates.

---

### Post by ajgreeny on 2020-04-22
If you still want a thesaurus and/or dictionary have a look at artha; it's in the repos (for 18.04 at least) and is a super quick way to look for words etc etc.

If it's running you can highlight a word in any doc or web page etc etc, press Ctrl+Alt+W and the artha window will appear with info about that word and alternatives.

---

### Post by wyattwhiteeagle on 2020-04-23
> **ajgreeny said:**
> If you still want a thesaurus and/or dictionary have a look at artha; it's in the repos (for 18.04 at least) and is a super quick way to look for words etc etc.

If it's running you can highlight a word in any doc or web page etc etc, press Ctrl+Alt+W and the artha window will appear with info about that word and alternatives.

Watched a demo on youtube about Artha. Looks like something I should get. Thank you for sharing.

---

### Post by wyattwhiteeagle on 2020-04-23
Please correct me if I'm wrong, the correct order of doing things is...

```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove
sudo apt autoclean
```

---

### Post by ajgreeny on 2020-04-23
Yes, that's  about it!

You don't  tell us the context of your query but if youre upgrading from 19.10 to 20.04 you must also disable, preferably remove, any PPA repos you were using in 19.10 or you will end up with problems.

---

### Post by CatKiller on 2020-04-23
> **wyattwhiteeagle said:**
> Please correct me if I'm wrong, the correct order of doing things is...

```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove
sudo apt autoclean
```

That is the correct *order*, but you don't generally need to do all of those. 
```
sudo apt update
sudo apt upgrade
``` is generally sufficient. 

```
man apt
``` will give you all the details of what the options do, but the short & sweet is that *update* refreshes the list of available packages/versions to see if there's anything that can be upgraded; *upgrade* upgrades any packages that can be upgraded without removing any; *full-upgrade* upgrades any packages that can be upgraded, including removing packages to satisfy dependencies; *autoremove* removes packages that the package manager thinks you don't need any more; *autoclean* removes the local cache of packages that are no longer available; *clean* clears the local cache.

---

### Post by wyattwhiteeagle on 2020-04-23
> **ajgreeny said:**
> Yes, that's  about it!

You don't  tell us the context of your query but if youre upgrading from 19.10 to 20.04 you must also disable, preferably remove, any PPA repos you were using in 19.10 or you will end up with problems.

I just want to get things right instead of what I've done in the past which caused me to start all over again

---

