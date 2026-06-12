---
title: "After programs it was software, then applications-apps, now it is snaps ?"
date: 2022-08-19
forum: New to Ubuntu
---

### Post by Innernet on 2022-08-19
This thundersomething about email that I do not use and others; if I want to uninstall; is not on the 'A' briefcase for installed 'Ubuntu software' ; if I go to the 9 dots at bottom right, it shows but cannot choose to uninstall; If I go to the 'new' Snapswhatever; cannot find uninstall.   What is this trend in inconsistencies ?
Plug-ins, add-ons, extensions, apps, snaps... can it be made more complex ? 

How do you manage to deal with all them ?

---

### Post by mikewhatever on 2022-08-19
Yeap, it is somewhat complex, and you forgot themes, daemonds, dependencies and freakiing microcodes.:lolflag:

C'est la vie.

---

### Post by grahammechanical on 2022-08-19
If you are using Ubuntu 22.04 open Ubuntu Software and find Thunderbird. At present it is an Editor's Choice so it should be easy to find. On the Thunderbird page next to the box that says Permissions is a red square with the white outline of a rubbish bin. Click on it. There you will get an option to uninstall the Thunderbird snap packaged version. 

Regards

---

### Post by TheFu on 2022-08-19
> **Innernet said:**
>  Plug-ins, add-ons, extensions, apps, snaps... can it be made more complex ? 

How do you manage to deal with all them ?

Canonical decided that we all needed to use Snap packages, if they are available and has been defaulting many tools to use that package system, without asking.  Many people don't like snap packages for a number of reasons, some valid, some not-so-valid. Those people typically would remove the entire snap subsystem and are careful about the source of any software installed.  If they see that is it a snap, they they either don't install it or remove it.

As for why Canonical is pushing snaps?  They have their reasons, but my tin-foil-hat wearing person doesn't believe every reason has been aired.

So, there are these types of software on Ubuntu:
* APT / Deb packages  - this is the normal packages we've used since the 1990s. Redhat has something similar in the RPM packages. Arch Linux has something similar.
* Snap packages - this is Canonical's package once, run anywhere, under constraints, not overrides allowed, packaging that was originally created for Ubuntu Phone.
* Flatpak packages - this is backed by Redhat as their package once, run anywhere, with some constraints, but local constraint overrides are possible.
* AppImages - This is a community created package once, run anywhere, with no constraints packaging.
* Source code - the old TGZ files.  These should probably be avoided by people new to Linux.

There are a few other things, like PPAs, which allow 3rd party software distribution to be included with the normal APT patching/updating. This can be dangerous, since the software in the PPA could be used to install nefarious items. Only use trusted PPAs from reputable people and reputable teams.

Most software that Canonical ships as a snap package can be found as a PPA or via some other non-snap package for installation.  Thunderbird, firefox, chromium are the main snap-only things in the Ubuntu 22.04 world, but there are certainly others.

How do we keep it all straight?  Time and experience.  I patch my systems weekly, using the CLI (not any GUI).  I find this provides more control and clearer information/feedback.  Also, it keeps non-APT/deb package stuff far away from my systems.

Snap packages get updated as needed.  The default settings are to check for updates 4x a day, but we can change that to other values. I have it set to once a week, on Saturdays only.  I don't want software automatically updating, ever.  I've been left with broken systems when it was inconvenient a few times. Having to fix an issue on a Tuesday morning when I have deadlines is unacceptable.  Pushing updates to the weekend is a compromise, but still not ideal.  There is no way to completely disable snap package updates, short of blocking access using a firewall. I find this extremely frustrating, but suspect that most end-users don't mind.  

Also, there are 3 versions of every snap package on our systems by default. This can be changed to two, but not 1, unfortunately.  As part of my weekly patching script, I have a snap-cleanup script that removes extra snap package versions.

I don't have the same knowledge about flatpaks, but suspect there is an easy way to update them or prevent updates. Redhat thinks that the local admin should actually have control over their own systems. Imagine that?

AppImages don't auto-update.  Some AppImages have an update capability or an "update available" notice, so we know one is possible. I look for updates in the few AppImage programs I use monthly.

Snaps are still the exception for packages in Ubuntu.  Most other distros have not decided to use Snap packages.  Linux Mint decided against snaps completely, even with a strong tie to Ubuntu as their upstream distro.  Of course, Ubuntu has made adding the snap subsystem possible for all the major Linux distros. 

Same applies for flatpaks. 

AppImages are really just a self-contained program, libraries, startup script, and environment variable management tool, so it doesn't need much special care.  In the 1990s, we'd have startup scripts to set environment variables so we could run multiple different versions of software on the same system. Nothing too new with appimages.

---

### Post by pantazi on 2022-08-20
TheFu said "I have a snap-cleanup script that removes extra snap package versions."   

You supplied that script in a reply to me a while back and it has proved useful, thanks,

[COLOR=#000000]







[/COLOR]

---

### Post by TheFu on 2022-08-20
> **pantazi said:**
> TheFu said "I have a snap-cleanup script that removes extra snap package versions."   

You supplied that script in a reply to me a while back and it has proved useful, thanks,

I stolen it from someone else, somewhere.  Mine just outputs the commands to be run. Others directly run the commands.  Since I snagged that script, it has been generating commands that aren't bad, so I should just let it run the commands directly.  In my script, that runs the script, that runs the script, I have it pass the resulting commands into an admin shell. ;)  Lots of scripts calling other scripts around here.

Anyway, happy to share general purpose scripts like that, but google will easily find them and better scripts too.

---

