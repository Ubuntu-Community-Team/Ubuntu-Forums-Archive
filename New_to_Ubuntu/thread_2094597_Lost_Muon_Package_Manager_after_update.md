---
title: "Lost Muon Package Manager after update"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by sumethc on 2012-12-14
Hi there,

My system is Kubuntu 12.04 Precise running on a  dual-boot MacBook 3,1. Today after following instruction from  <http://ubuntuforums.org/showthread.php?t=1889034> regarding  additional software sources. I added "ppa:kubuntu-ppa/ppa" and  "ppa:kubuntu-ppa/backports" to the software sources in Muon Package  Manager and then update. 

Once the installation was complete I  reboot the system just to make sure. Well, my KDE is now version 4.9.4  and I have a few more applications added to the system. The problem is:  when I tried to launch Muon Package Manager to check the update history,  the application was nowhere to be found, neither was Muon Software  Center - its GUI counterpart. I believe the Update Manager was gone as  well.

So what was happening? I'm now left with no means to check  the update history or update. While I can search and find a way to use  terminal app, I feel much more comfortable doing it with the Muon  Package Manager. My question: Can I reinstall the Muon Package Manager?  If so, how? Is there a way to extract it from the live CD which I used  to install Kubuntu?

And how do I remove the 2 newly added sources  ["ppa:kubuntu-ppa/ppa" and "ppa:kubuntu-ppa/backports"] from my  system's software sources? Thank you for any help. I must confess this  is rather unnerving to have your software removed without explicit  permission.

---

### Post by MadmanRB on 2012-12-14
Yes you can re install muon.
I actually had this happen to me when upping to KDE 4.9 on 12.04 and probably is related to upping the KDE libraries.
just open up a terminal and input this:

sudo apt-get install muon
Its a terminal command I know but its easy enough to copy and paste.

---

### Post by sumethc on 2012-12-14
Wow, [MadmanRB]("http://ubuntuforums.org/member.php?u=1651197"),

You have saved me half a day of reinstallating the whole thing from LiveCD. Follow your instruction and I got the following output:

[INDENT]The following packages were automatically installed and are no longer required:
  plasma-active-data share-like-connect libqtwebkit-qmlwebkitplugin
  plasma-active-mobilecomponents share-like-connect-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmuonprivate1 muon-notifier muon-updater software-properties-kde
  update-manager-kde
The following NEW packages will be installed:
  libmuonprivate1 muon muon-notifier muon-updater
  software-properties-kde update-manager-kde
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 265 kB/293 kB of archives.
After this operation, 1,528 kB of additional disk space will be used.
[/INDENT]
I can't thank you enough for your quick response, without which I would have to go the reinstall route which is far from being pleasant. Really appreciate it. :D

---

### Post by sumethc on 2012-12-14
Pls forgive the typo: reinstallating. I was trying to change from "reinstalation" to "reinstalling" and didn't realize it at the time.

---

