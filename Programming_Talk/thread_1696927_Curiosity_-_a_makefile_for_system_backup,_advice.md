---
title: "Curiosity - a makefile for system backup, advice?"
date: 2011-02-28
forum: Programming Talk
---

### Post by copb.phoenix on 2011-02-28
Hi all!

Being one of those people keen to the "bleeding edge", but not one with much RAM to run virtual machines inside of, I find myself usually about every 6 months with a broken system. Desiring a fully portable and reasonable way to transfer data from installation to installation (and between virtual machines later), I opted to zip files with a Makefile.

It looks like this, and has only had an hour of research into it. I'm new to Make, but this functions fine for me:
```

###############################
# Experimental backup makefile
###############################

###############################
# Variable declarations
###############################

# folders to backup
bootD = /boot/
DesktopD = ~/Desktop/
diaD = ~/.dia/
DocumentsD = ~/Documents/
DownloadsD = ~/Downloads/
mozillaD = ~/.mozilla/
ProgsD = ~/Progs/
sysLogsD = /var/log/
TemplatesD = ~/Templates/

# files to deliberately exclude
DownloadsX = *.iso

# files to output
bootO   = ./root/boot
DesktopO   = ./root/home/Desktop
diaO = ./root/home/.dia
DocumentsO   = ./root/home/Documents
DownloadsO   = ./root/home/Downloads
mozillaO = ./root/home/.mozilla
ProgsO   = ./root/home/Progs
sysLogsO = ./root/var/log
TemplatesO   = ./root/home/Templates

# programs to use
zipP = zip

# program flags
zipF = -porX --filesync --log-append --log-info --logfile-path ./logs/zip.txt
zipFX = --exclude

# shebang requirements
shebangR = boot Desktop dia Documents Downloads mozilla Progs sysLogs Templates
###############################
# Declare Phony Targets
###############################
.PHONY: shebang

###############################
# Targets ~ eg, files to backup
###############################
boot:
	$(zipP) $(zipF) $(bootO) $(bootD)
Desktop:
	$(zipP) $(zipF) $(DesktopO) $(DesktopD)
dia:
	$(zipP) $(zipF) $(diaO) $(diaD)
Documents:
	$(zipP) $(zipF) $(DocumentsO) $(DocumentsD)
Downloads:
	$(zipP) $(zipF) $(DownloadsO) $(DownloadsD) $(zipFX) $(DownloadsX)
mozilla:
	$(zipP) $(zipF) $(mozillaO) $(mozillaD)
Progs:
	$(zipP) $(zipF) $(ProgsO) $(ProgsD)
sysLogs:
	$(zipP) $(zipF) $(sysLogsO) $(sysLogsD)
Templates:
	$(zipP) $(zipF) $(TemplatesO) $(TemplatesD)

#################################
# shebang should attempt to build everything
#################################
shebang: $(shebangR)	

#################################
# All, which does(nothing) for now
##################################
all:

```

This is stored at ~/Backups/makefile on my system.


My questions are,

Is there a better way to write this script?

Are there logs and system files that might be useful post-mortem of a broken system that I'm missing?

Is there a better way to nicely and neatly package my personal files to be extracted "as needed" into new installs?

Thanks in advance!

---

### Post by ibuclaw on 2011-02-28
> **copb.phoenix said:**
> 
Is there a better way to nicely and neatly package my personal files to be extracted "as needed" into new installs?

Thanks in advance!

I just go with a separate /home partition, then all settings are retained across re-installations (just login and all looks like how it was before ... with the exception to a few missing applications).

Reinstalling applications ... A nice trick I've found that I keep in the bikeshed.

```

dpkg --get-selections > installed_packages.list

```
Generates a list of all installed packages on your system (to be ran before reinstalling).

```

sudo dpkg --clear-selections
sudo dpkg --set-selections < installed_packages.list

```
Marks most packages for deinstallation, then sets all in the list for installation (to be ran after reinstalling).

```
sudo apt-get dselect-upgrade
```
Installs / Removes packages as needed per the above configuration you just set.


By the way, you can put this at the top of the makefile, then rename it anything you want, and it'll still work.
```

#!/usr/bin/make -f
SHELL = bash

```
Regards

---

### Post by copb.phoenix on 2011-03-01
> **ibuclaw said:**
> I just go with a separate /home partition, then all settings are retained across re-installations (just login and all looks like how it was before ... with the exception to a few missing applications).
> **copb.phoenix said:**
> ...Desiring a fully portable and reasonable way to transfer data from installation to installation (and between virtual machines later), I opted to zip files with a Makefile...Is there a better way to nicely and neatly package my personal files to be extracted "as needed" into new installs?

Unfortunately, I'm not always interested in reinstalling every single program that I have leftover configuration for, not necessarily wanting to get rid of the config files "just in case", and not always on the same hard drive or machine. I do use that solution in virtual machines (it makes a whole lot more sense, I will admit), but it's not practical for when I need things to be quickly ready to go and portable, as well as maintained if the system breaks.

Scratch that ~ the original files are self-maintaining, but still I'd prefer moving a single compressed file stream over the ~4000 currently in my ~/Progs/ folder for all my projects and scraps of reusable code. Not to mention artwork folders and so forth that are sorted and maintained religiously.

> **ibuclaw said:**
> 
Reinstalling applications ... A nice trick I've found that I keep in the bikeshed.

[code omitted, see original post ~/cx]


I actually like that for tracking what I'm installing alongside memory usage for custom builds and etc on systems, not to mention that a list is good in case you remember that you had this wonderful app, but, oh, what was it named? I usually use a personal list (base.txt) to install a minimalist system, actually, from a minimal net/command line install.

> **ibuclaw said:**
> 
By the way, you can put this at the top of the makefile, then rename it anything you want, and it'll still work.
```

#!/usr/bin/make -f
SHELL = bash

```
Regards

That code ~ chmod the executable bit and treat like shell script, or does what? I know what SHELL variable does, but what in the world is the first line?

---

### Post by ve4cib on 2011-03-01
Out of curiosity why use a makefile instead of just setting up something like rsync?  It seems to me like that would be better-suited to your purposes, unless I'm missing something.

---

### Post by ibuclaw on 2011-03-01
> **copb.phoenix said:**
> That code ~ chmod the executable bit and treat like shell script, or does what? I know what SHELL variable does, but what in the world is the first line?

Lookup shebang. :)

It calls the interpreter (make) on the file.

---

### Post by copb.phoenix on 2011-03-02
> **ve4cib said:**
> Out of curiosity why use a makefile instead of just setting up something like rsync?

1) Make is a tool. I'm not at all foreign to the fact that I'm using it unconventionally, but saying that rsync is for backups and make is for making things is like saying that Linux is for free software advocates and Macs are for people who are artists with little interest in computer diagnosis/repair. (generally true? Debatable, but often presented as true)

2) I am limited on disk space and broke. Compression is a must ~ not to say that there isn't a function to handle that as part of rsync, but when I really only care about the backups after the system is dead in most cases ~ with the exception of three folders - chat logs, code scraps, and personal photos ~ it becomes the second question: How do I do this in a way that's fairly portable and wastes the least space? (again, not to bash rsync but a snippet of experience with make was enough to tell me it would suffice).


> **ibuclaw said:**
> Lookup shebang. :)


This starts at "How could anyone versed in English near Americans not..?" and ends at "Haha, really? I've always know them as 'crunch' and 'bang'. " That's awesome, and useful to know.

> **ibuclaw said:**
> It calls the interpreter (make) on the file.

Hm. After reading some Wikipedia and a few standard writeups, it essentially means that I treat it like a shell script: Flip the executable bit, throw in whatever program I want to open/interpret/etc it with, and then run the file itself.

I've never messed with #! before, but I've always seen it and wondered what it was for, exactly... That it's general case is just another testament to both AT&T and Berkeley's brilliance in devising useful features and implementing them.

Thanks very much!

---

