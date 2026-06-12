---
title: "Update notification"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by ajaykumar.b on 2011-11-09
Hi 
I am using kubuntu 11.10.I am not getting update notification when the updates are available . Can you please help me to get the notification.

Thank you
Ajay

---

### Post by Silent Warrior on 2011-11-09
I have to confess I don't use any update notification in KDE... But you installed from a Kubuntu CD/DVD, then? Maybe you should double check that a package with a name like update-manager-kde is installed. Or have they switched to Muon? PackageKit? Hm, I guess it might pay to start Muon up and see if you can find any such settings. Also check that you are indeed supposed to get notifications - I've seen settings that look like certain updates (security) are set to be automatically installed whenever they become available, nothing specific said about notifications.

---

### Post by CryptoPaul on 2011-11-09
Kubuntu 11.10 does indeed now use muon.

The relevant settings within muon package manager are to be found under:

Settings -> Configure Software Sources -> Updates -> Check for Updates / Frequency

Settings -> Configure Muon Package Manager -> Notifications


There is also a bug relating to update notifications:

[https://bugs.kde.org/show_bug.cgi?id=285435](https://bugs.kde.org/show_bug.cgi?id=285435)

---

### Post by FuturePilot on 2011-11-09
Got the same problem here.

---

### Post by Denver Dave on 2011-11-10
Not same, but similar.  I'm waiting for the 8.0 Firefox and Thunderbird installs.  Don't know how to see if they are available other than keep trying to install from command line.

Haven't tried to install for a day, might be there.  I have the 8.0 on XP and Window 7.

---

### Post by FuturePilot on 2011-11-10
> **Denver Dave said:**
> Not same, but similar.  I'm waiting for the 8.0 Firefox and Thunderbird installs.  Don't know how to see if they are available other than keep trying to install from command line.

Haven't tried to install for a day, might be there.  I have the 8.0 on XP and Window 7.

There's always a little bit of a delay between when Firefox is released to the time they make it into Ubuntu. It takes time to package and test them. Give it a few days.

---

### Post by Denver Dave on 2011-11-10
No problem with the delay, I understand, I prefer it be done right rather than over.

My question is is there someplace to view whether the update to Thunderbird and Firefox 8.0 are ready for ubuntu?

Also there are several methods of update:

- download from Mozilla site and install
- do the terminal commands to update
- use the update program
- something called resource.list which may or may not relate to the above.

Learning ubuntu and curious how above are related.

I can wait - no pressing need, just curious.

Thanks.

---

### Post by enteon on 2011-11-14
[Bug]("https://bugs.kde.org/show_bug.cgi?id=285435") fixed in muon 1.2.3.
Now begins the waiting game. :popcorn:

---

### Post by Kubischbuntu on 2011-11-20
Do you mean Muon Version 1.2.3? If so how do you get this? Also i hade a look at the Muon web site and it doesnt look like 1.2.3 is there???:confused::confused:

---

### Post by enteon on 2011-12-04
Muon 1.2.3 will be a future release. For now there is a snapshot in the git repository with the version number 1.2.65.

Fortunately these packages are already in the 12.04 "precise" repository. Simply update your system, then add the precise main repository temporarily, update package list, upgrade muon-notifier and ONLY muon-notifier, remove the precise repository again.

I just did that but don't know yet if it does the trick, will have to wait for some updates to arrive.
If you don't know how to replace packages that rendered your system unbootable, DON'T DO THIS!

edit: it works fine after you make sure that apt-get update is regularly executed. I added it in KDE's system settings task scheduler module (as root of course) to be run every day. It's just a frontend for cron so you could use any other way to modify crontab.

---

