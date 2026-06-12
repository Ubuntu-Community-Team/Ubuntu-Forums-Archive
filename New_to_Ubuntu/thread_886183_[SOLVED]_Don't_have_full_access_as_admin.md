---
title: "[SOLVED] Don't have full access as admin"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by JohnDorian on 2008-08-10
My account is an admin account.  I'm able to add/remove programs and browse throughout the file structure.  However, today I received several error messages that seem to indicate I don't have full write/update/change access.

I'm unable to save files to any location other than the desktop(see attached)  When trying to quarantine files that appeared in klamAV I was given a different error (see attached).

I checked my permissions and confirmed I have admin.  Below is output from id <user name> in the terminal.

uid=1000(brainey) gid=1000(brainey) groups=1000(brainey),4(adm),6(disk),20(dialout),21(fax),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),39(irc),44(video),46(plugdev),60(games),100(users),103(syslog),105(scanner),107(fuse),109(lpadmin),114(admin),121(clamav)

Thanks

---

### Post by mikewhatever on 2008-08-10
First, to deal with root owned files, you need to obtain root privileges, which aren't used by default. To get simple root access to files, open nautilus with gksudo nautilus.

About clam message (first picture), I wouldn't mess with it. It looks like the file in question is part of the kernel module for an ATI graphics card. Don't be surprised to get a black screen if you quarantine it.

---

### Post by JohnDorian on 2008-08-10
Thanks.  I'll take your advice re: clamav

Regarding the other - I've always been able to download files from the internet, email, etc and place them in whatever folder I like.  My wife's account, which is not an admin account, is able to do this.

---

### Post by HotCupOfJava on 2008-08-10
Also, even if you are ROOT (which you never really are with Ubuntu), not all files have write permission. If you are an administrator you can use the shell to change the permissions for individual files or directories, but I would advise against it unless you REALLY know what you are doing.

---

### Post by mikewhatever on 2008-08-10
> **JohnDorian said:**
> Thanks.  I'll take your advice re: clamav

Regarding the other - I've always been able to download files from the internet, email, etc and place them in whatever folder I like.  My wife's account, which is not an admin account, is able to do this.

That shouldn't be the case. Every user has full access within his/her home folder, but not outside it. If your wife can write to / by default, something is very wrong with the system. You may want to check the permissions of the Documents folder with <ls -l /home/brainey.
If brainey is your wife's username, you shouldn't be able to write to her home without root privileges.

---

