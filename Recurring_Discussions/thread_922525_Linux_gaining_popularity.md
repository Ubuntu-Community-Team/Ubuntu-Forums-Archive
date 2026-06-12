---
title: "Linux gaining popularity"
date: 2008-09-17
forum: Recurring Discussions
---

### Post by SpenceMakesSense on 2008-09-17
Windows has become so popular that it has so many viruses and security flaws and problems. It makes me worry what if Linux became so popular that people started making viruses and breaking through security. Completely defeating the purpose of why I use linux in the first place. I now were trying to convert people over but I do not want it to become as popular or even more popular than Windows

---

### Post by artir on 2008-09-17
Don't worry. Linux's Unix roots are strong. Unix (and so Linux) was designed as a net operating system, with security as a top priority feature, then the layers of UI, desktops etc were added.
Windows was born as a home operating system. They then added the (un)safety layers.

;)

---

### Post by ilrudie on 2008-09-17
Linux has much better security that Windows by design.  We don't have to rely on security by obscurity.

---

### Post by perce on 2008-09-17
I wouldn't be so optimistic. It is true that it is relatively hard to install a malware as root and compromise a system, but don't forget that it is also possible to install programs on your home directory, where they have access to all your files.

---

### Post by artir on 2008-09-17
Yep. Is easy to run rm -rf /home and nobody will stop you. You don't need to be root to do that.
Can we avoid that?
(Besides from the backups)

---

### Post by mihai.ile on 2008-09-17
I think that there is a false sense of security because the most important thing is my home, not my system files...
any dumb script can erase all that or do read/write/whatever...
I think that there should be a concern on people's accounts, not only system's files/etc.

---

### Post by aysiu on 2008-09-17
If the most important thing is your home, then you should do regular backups of your personal files.

The main concern with security shouldn't be files being erased. The main concern should be files being changed or added... and then the time it takes to clean up a breached system.

In this regard, Linux has Windows beat on two fronts: [list][*]It has a proper permissions system set up so if one account is compromised, you can quarantine or delete that account and not have to reinstall the whole system to have things working again.[*]Reinstallation isn't that big a deal. Within an hour, I can install and configure Ubuntu to be exactly the way I had it before. If I reinstall Windows, it can take me over five hours with many reboots and constant attention to get things back to the way they were. I also can't have a simple script that will reinstall all the programs I'd had installed before.[/list]

---

### Post by SpenceMakesSense on 2008-09-17
I do find it funny when using windows and I go to access folders it tells me I dont have permission to enter the folder. Then lets me continue to view and edit stuff inside it

---

### Post by ryaxnb on 2008-09-17
Linux is gaining popularity... but at a much smaller scale, and Linux is inherently much more secure. It's true, there will likely come a point when you need to worry about Linux security, but that's a long ways off, and anyway, you won't be putting antivirus on it, you'll be tuning up permissions and PolicyKit, the sudoers file, and SELinux controls.

Linux is currently at ~2-3% marketshare according to w3counter. Linux was at 1-2% marketshare. So Linux approximately went up by 1.5x the usage. However, Linux is still much lower in usage then OS X (8-10%) which has no major virus or malware threats. I estimate, based on the fact that Firefox started to get targeted at about 17% marketshare, that you need a minimum of 15% marketshare to get any significant targeting efforts at all. That's a long ways off from 3%.

However, in any case, Linux is simply much more secure when setup properly. If you keep the sudoers and PolicyKit settings properly, and enable SELinux for process protection if necessary, your Linux distro is far more secure than Vista. The lack of warnings that will pop up under sudo protection versus UAC means you're less likely in practice to accidentally OK a bad file.

Another critical difference is some programs in windows, notably setup programs, and outdated programs, actually require UAC approval. This occurs in some cases every time you launch them, getting you in the habit of clicking OK after launching a program icon. With Linux, no program really ever requires gksudo, except configuration tools. Almost everything that does normal tasks is ran as normal user. Only things in the "System" menu or launched from the command-line as root ("sudo su" or similar) are usually executed as root. This enforces the distinction between root and user.

Also, malware is unlikely to occur in the repos, and malware would never be allowed on the sources we usually get sources or debs from (sourceforge, getdebs, ppa) and would be quickly taken off.If you stick to the Ubuntu repos, you're perfectly safe. Even Sourceforge and Getdebs would work quickly to remove any malware.

Finally, it's worth noting that Linux has more than one distro. If you want to say that linux is getting more common and will be attacked, which Linux are you talking about? :) Some Linux distros will always be less popular, reducing the chances of getting hit.

Remember, even though malware can do a lot of damage in your home directory, it can't contact the internet very well, hide from detection, or become a worm or spreading virus that well within the comfort of your user, making it ineffective at spreading, keylogging, spamming, etc. without root priveleges, which of course are hard to get.

---

### Post by cardinals_fan on 2008-09-17
Malware infections are a direct result of user stupidity/ignorance.  The OS is irrelevant, although some have defaults that make it easier for the user to screw up.

---

