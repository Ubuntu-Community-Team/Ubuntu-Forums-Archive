---
title: "Backup Finished. Could not back up..."
date: 2013-01-19
forum: New to Ubuntu
---

### Post by MyTinFoilHat on 2013-01-19
I'm attempting to backup my system's /etc and /home folders (as well as a few others). I have the backup password protected, to an external HD (WD 500GB) using &quot;Backup&quot; in 12.10's System Settings (&quot;Duplicity&quot;?).  Everything appears to have gone well to my novice eye (I can see many, many serialized .gpg volumes when I browse the external drive), but I can't be 100% sure if the backup got everything I might need if I have a huge sys problem, including GPG keys, etc. I encountered the following message at the end of the backup process:  ```
 Backup Finished. Could not back up the following files. Please make sure you are able to open them.  /etc/.pwd.lock /etc/NetworkManager/system-connections/Black_Wool Network /etc/NetworkManager/system-connections/R0WE5 /etc/NetworkManager/system-connections/kwfront /etc/apparmor.d/cache/lightdm-guest-session /etc/apparmor.d/cache/lightdm-remote-session-freerdp /etc/apparmor.d/cache/lightdm-remote-session-uccsconfigure /etc/apparmor.d/cache/sbin.dhclient /etc/apparmor.d/cache/usr.bin.evince /etc/apparmor.d/cache/usr.lib.telepathy /etc/apparmor.d/cache/usr.sbin.cupsd /etc/apparmor.d/cache/usr.sbin.tcpdump /etc/apt/trustdb.gpg /etc/at.deny /etc/cups/ssl /etc/cups/subscriptions.conf /etc/cups/subscriptions.conf.O /etc/default/cacerts /etc/fuse.conf /etc/group- /etc/gshadow /etc/gshadow- /etc/mtab.fuselock /etc/passwd- /etc/ppp/chap-secrets /etc/ppp/pap-secrets /etc/security/opasswd /etc/shadow /etc/shadow- /etc/ssl/private /etc/sudoers /etc/sudoers.d/README /etc/ufw/after.rules /etc/ufw/after6.rules /etc/ufw/before.rules /etc/ufw/before6.rules /home/MTFH/.cache/unitydashlegalseen
```  I'd like a little nudge/help to understand what I'm potentially doing wrong (or what I could be doing better). Are these items, in fact, backed up? Is there merely a warning to check them (and how do I do that)? ...or, have I encountered a larger issue.  Thanks in advance.

---

### Post by mapes12 on 2013-01-19
What _exactly_ are you trying to backup? If it's your system files then there are easier solutions. If it's your personal stuff in /home then again there are easier solutions.

---

### Post by brusegadi on 2013-01-19
I suspect the files you were unable to backup are **owned by root** and you may not be allowed to read them (some files owned by root are readable by any user.)  

Backing those up may not be worth it.  For example, if you want to back up a set of ufw rules, you may be better off creating a script that produces those rules and backing up the script.  I advice this because the internal representation of the rules is more likely to change than the way the user inputs such rules.  Good luck.

---

### Post by MyTinFoilHat on 2013-01-19
> **mapes12 said:**
> What _exactly_ are you trying to backup? If it's your system files then there are easier solutions. If it's your personal stuff in /home then again there are easier solutions.

 I want to backup all of my personal docs, pics, etc (/home) as well as my sys config (/etc, right?). I also want to insure that I have GPG Keys, passwords, etc. backed up also.

---

### Post by MyTinFoilHat on 2013-01-19
> **brusegadi said:**
> I suspect the files you were unable to backup are **owned by root** and you may not be allowed to read them (some files owned by root are readable by any user.)  

Backing those up may not be worth it.  For example, if you want to back up a set of ufw rules, you may be better off creating a script that produces those rules and backing up the script.  I advice this because the internal representation of the rules is more likely to change than the way the user inputs such rules.  Good luck.

Funny that you mention this because I initially supposed that one of the reasons for enountering this might be somethig akin to their being 'in use' or root priveledges. Considering that I was using the GUI, I'm wondering if there's a CLI method using sudo...  I have zero experience in creating scripts. This seems a bit daunting given that I'm a complete and utter novice still.

---

### Post by mapes12 on 2013-01-19
There are a zillion ways to do this. It all depends on personal preference. I keep all my stuff on a separate partition and back it up to another machines HDD using Grsync. Then, to make sure I have an exact copy of my system I back it up using Remastersys. Remastersys will backup all the things you mention and make an exact copy of your system exactly how you have tweaked it. Both apps are GUI. No command line stuff to bother with.

---

### Post by cmcanulty on 2013-01-19
for system files open grsync with terminal command
```
gksudo grsync
```

---

### Post by MyTinFoilHat on 2013-01-19
> **mapes12 said:**
> There are a zillion ways to do this. It all depends on personal preference. I keep all my stuff on a separate partition and back it up to another machines HDD using Grsync. Then, to make sure I have an exact copy of my system I back it up using Remastersys. Remastersys will backup all the things you mention and make an exact copy of your system exactly how you have tweaked it. Both apps are GUI. No command line stuff to bother with.

 Lucky for all of us, I adapt easily. All I need is one or two sound, reliable, and safe options out of that zillion. LOL. I definitely want/need to backup as exactly as possible because, as you mentioned, I've tweaked my system -to what I refer to as &quot;Goldilocks Standard&quot; (juuuuust right).  ;)

---

### Post by MyTinFoilHat on 2013-01-19
> **cmcanulty said:**
> for system files open grsync with terminal command
```
gksudo grsync
```

 ...then what should I expect? (I've never used this before).

---

### Post by Zill on 2013-01-19
> **MyTinFoilHat said:**
> ...All I need is one or two sound, reliable, and safe options out of that zillion...
You may like to take a look at [luckyBackup]("http://luckybackup.sourceforge.net/").  While it is primarily GUI based it *can* be run via CLI, which is useful for scheduled backups when logged out.  It can also be run as the superuser, making the backing up of root-owned folders (such as /etc) easy.

The application is based on rsync, minimising the updating necessary to maintain the latest backup.  It also saves snapshots so that earlier backups can be restored if required.

Recommended. :-)

---

### Post by cmcanulty on 2013-01-19
the command 
```
gksudo grsync
```
just opens grsync but with sudo privileges so system files will backup otherwise they will create error of no permission

---

### Post by MyTinFoilHat on 2013-01-19
> **cmcanulty said:**
> the command 
```
gksudo grsync
```just opens grsync but with sudo privileges so system files will backup otherwise they will create error of no permission

Oh, neat! Thank you very much. I think I'll also have a go at Remastersys, as mapes12 suggested, too.

---

### Post by cmcanulty on 2013-01-20
I love grsync. It gives you details by clicking on details arrow, if backup fails so you can go to that file and fix it usually goes without a hitch.

---

### Post by BlinkinCat on 2013-01-20
> **cmcanulty said:**
> I love grsync. It gives you details by clicking on details arrow, if backup fails so you can go to that file and fix it usually goes without a hitch.

Hi,

Looking over the guide and can't see the "details" arrow - can you fill me in ?

Cheers - :)

---

### Post by cmcanulty on 2013-01-20
it will show up when you start the backup it actually says rsync output, but at end if there are errors it says details (I don't have a bad file right now to check) see screenshot

---

### Post by BlinkinCat on 2013-01-20
Oh, I see and understand - thanks very much for that - :P

---

