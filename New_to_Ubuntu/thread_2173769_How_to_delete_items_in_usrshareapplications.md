---
title: "How to delete items in usr/share/applications"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by SpazCool on 2013-09-11
I'm trying to use Synaptic to delete some packages of an erronously installed plugin. But, whenever I try to boot syaptic using the terminal using ```
synaptic &
``` I am greeted with a popup message that informs me that I don't have administrative privileges. It still allows me to view the repositories or packages or whatever they're called, I'm new to Ubuntu sorry, and it even lets me "mark for deletion/removal." Unfortunately, all I can do is mark the items for deletion, I am not allowed to actually do anything more. 

So, wondering if I installed synaptic incorrectly I looked for its launch icon and found that I have two "Synaptic Package Manager" icons in usr/share/applications. Both icons will open Synaptic, but only one will prompt me for my password. So I endeavored to delete the one that didn't ask for my password. But, yet again, I am not allowed to edit the contents of this folder! I right click any of the items in /applications and I see "move to trash" as an option but it is greyed out. 

I am at wit's end here. I am really new to Ubuntu and I have had nothing but problems; this website has become something of second home this past week.

So, I would love to be able to:

1) delete the packages I so desire using Synaptic

2) delete the files and apps from usr/share/applications

What should I do?

---

### Post by TheFu on 2013-09-11
Try
**gksudo synaptic $**

---

### Post by qamelian on 2013-09-11
To run it from the terminal, add sudo to the beginning of your command:
```
gksudo synaptic &
```

This will escalate your permissions allowing you to uninstall the packages you want to get rid of.

---

### Post by vasa1 on 2013-09-11
@The Fu, can you please explain what the "$" does in "gksudo synaptic $"? I've used "&" at the end of a command but didn't encounter "$" so far.

---

### Post by TheFu on 2013-09-11
> **vasa1 said:**
> @The Fu, can you please explain what the "$" does in "gksudo synaptic $"? I've used "&" at the end of a command but didn't encounter "$" so far.

It tells you the userid that THIS command should be run with.
**$** - means any userid
**#** - means root

Neither of these symbols should be included in the entered command.  When you read books about UNIX/Linux programs, these are the common way to easily tell the reader which account is needed for a specific command.  For lots of instructions, using 2-3-4 different accounts is needed, so the instructions need a concise way to denote that.
[B]
New Linux users should NOT be running the latest and newest release unless it is an LTS release.[/B] Check my sig for the reasons.

---

### Post by grahammechanical on 2013-09-11
When I open Synaptic Package Manager from the Dash I am asked to put in my password. That gives Synaptic administrator permissions. And I can mark packages for Reinstallation, Removal, and Complete Removal. Then after making my choice the Apply button becomes active and if I click Apply the action will take place. I have given Synaptic my Administrator approval for doing so when I put in my password.

You are opening Synaptic from the terminal but it is loading without administrator approval. But you should not need to run Synaptic from a terminal. It is best to install and remove applications using the Ubuntu Software Centre. That utility will not only install/remove applications (bin or binary files) but also the libraries that the application needs. Libraries and binary files are called packages because they are packaged to run on a Debian Linux OS. Repositories or Software Sources are the servers that Ubuntu Software is stored on. These servers are both the source of Ubuntu software and the repository of Ubuntu software. That is why those names are used.

I also have two Synaptic icons in usr/share/applications. So, what? The actual applications (what in Windows would be called exe files) are not in /usr/share/applications/ anyway. 

I have two icons there for Software and Updates and also two icons for Files (File Manager - Nautilus) and two for Printers (and I do not have a printer), two for Online Accounts, two for Rhythmbox and finally two for Ubuntu One. There are they for a reason. I do not worry about it. And I am not having any problems.

Have you not stopped to think that the things that you are desparate to do are the things that are causing you to have problems? Be ready to re-install. That is often the simplest and easiest way of putting right a mess. I am about to do it with a Ubuntu 13.10 installation that will not load to a desktop no matter what I try. There comes a point when we waste time trying to fix things when it is much easier to re-install.

Regards.

---

### Post by SpazCool on 2013-09-11
TheFu: Thanks, your command line gave me the access I wanted.  

grahammechanical: I may just do a reinstall, again; I originally had 13.10 on here but it was buggy as all hell and I never used it.   

But, to be honest, I haven't done too much to this install to mess it up...I think. I've only installed 2 programs, Skype and Astril-VPN, and both of those work splendidly.   The persistent problems for me have been printer drivers and Adobe Flash Player. I was hoping, perhaps naively, to delete whatever I had installed for both of those and start anew.   

If I can't get them working by the week's end I'll probably switch to a different distro. I have Xubuntu on an old netbook and I experience absolutely zero problems with that install/setup.  Thanks everyone for the help and ideas.

---

### Post by Jonathan Precise on 2013-09-12
Try:

```
synaptic-pkexec
```

to use synaptic. This uses the program "pkexec" to ask for a password.
If it fails, you probably have an ubuntu version less than 11.04. Those are EOLs.

Remove adobe-flashplugin or flashplugin-installer. Then re-install the printer drivers

---

