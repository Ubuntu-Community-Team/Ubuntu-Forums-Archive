---
title: "Which directories/files to be backed up for reinstallation"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by flutti-tutti on 2008-05-18
Hi
I am new to Linux/Unix, and have basic questions regarding backup for re-installation.

In order to restore my (K)Ubuntu after re-installing Ubuntu and downloading updates and applications I selected, which directories/files should I backup to my CD or external HD?    

I also have VirtualBox where a particular localized Ubuntu is installed.  (My PC is standalone with a single user.)
 
Is there any application for this type of backup?  
Can HUBackup or Keeper restore (K)Ubuntu? 

Would applicate your suggestions.  Thanks
tutti

---

### Post by Vadi on 2008-05-18
What do you want to restore? Installed programs, or personal settings / data? If the latter - everything is stored in your home folder, so backing that one up will do the trick. As for programs, it just might be easier to reinstall them later as you need.

---

### Post by SOULRiDER on 2008-05-18
If what you want is personal files just backup your home folder. If you want to restore programs maybe APTonCD might be of help, but it may be a bit tricky to use...

---

### Post by flutti-tutti on 2008-05-19
Thanks for your replies.

What i am planning for backup is "personal settings/data".
After installing the KDE-desktop package to Ubuntu, (K)Ubuntu has been acting up, giving me the "white screen", when it cames back "Hibernation" or is switched to GNOME session.  I am not able to run GNOME-Ubuntu any more.

So, I am planning to reinstall Ubuntu and wants to save VirtualBox settings especially.

tutti 
PS: 
My system, consisting of ASUS M2A-VM, AMD Athlon64X2, 2GB RRAM and Ubuntu-64bits Hardy, previously worked perfectly.
  
Ubuntu Hardy is too great to give up, and I had to give up Ubuntu  v7 (on my old PC) 6 month ago.

---

### Post by jasong on 2008-05-20
Since I think we may have a similar problem,  I'm going to go ahead and post here.  If we end up not having the same problem, I humbly, and retroactively(if you'll allow that) offer my apology for hijacking the thread, and ask for a moderator edit.  Anyway...

After having Hardy Heron on my computer for about 1-2 months, I finally managed to figure out that the 64-bit version that is supposed to be for BOTH AMD and Intel is called AMD64.  I've come to this conclusion because that's what the link is called and it's been that way for WEEKS.

Anyway, I have a generic kernel, and I want to upgrade to the 64-bit Hardy Heron kernel while also transferring my settings, including the packages I've added.

Is there a HOW-TO I could use?  I'm sure it's a simple, though probably time consuming, process.

---

### Post by hyper_ch on 2008-05-20
you may want to backup

/home --> personal settings
/etc --> system settings
/var/www --> webfolder
/var/lib/mysql --> mysql DBs (but make mysql dump instead of copying the binary files)

---

### Post by flutti-tutti on 2008-05-20
jasong, thanks for your contribution

hyper_ch, thanks for your help.

tutti

---

