---
title: "is there a restore point in ubuntu?"
date: 2010-08-17
forum: Philippine Team
---

### Post by Jinxzs on 2010-08-17
hi guys

i just want to know if there is a restore point in ubuntu like in  windows, i want to install ubuntu, one of our pc in office since its  just for paperworks cause their main problem is viruses and i think it  can help them if i install and teach them how to use ubuntu. before i  do. i want to know if there is some kind of restore point in ubuntu, 

it could help me a lot to maintain the said pc.

--

---

### Post by dFlyer on 2010-08-17
Simple answer - No. Just make sure you backup your data files. I've been using linux for the past 15 plus years and only needed to restore linux one time when my hard drive failed on one of my laptops.

---

### Post by antoniomiguel on 2010-08-17
15 years yet only once you did a restore. Interesting!  Another reason to stick with Ubuntu :)

---

### Post by kidsodateless on 2010-08-17
Yeah just back up your data ,you might want to use user friendly Pybackpack to make your restore point :) [http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html](http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html)

---

### Post by Bonster on 2010-08-17
Pro Tip: seperate the / from the /home, saves alot of trouble

---

### Post by enhu on 2010-08-17
most computers of today supports usb to boot, you probably have to try it first.

---

### Post by adgaps on 2010-08-18
as others have said, just regularly backup your files... 

since it's just for paperworks, your system won't probably have some really serious problems, unless you do something that'll make it pretty messed up. just remember to be careful in using 'sudo' coz its misuse can spell disaster to your system...

other than that, try a Live CD/USB first.. then, if you feel it's gonna be ok in your pc, then you can finally install ubuntu...

well, good luck and enjoy you ubuntu experience! :)

---

### Post by killer_d76 on 2010-08-19
wow 15years of using Linux?!.. astig!!!! yep lesson learned the hard way of making backups hahaha.. yep no restore point in Linux bro, simply because you will never need one! and speaking of back-up check this out [LOOK HERE FOR BACKING-UP INSTALLED APPS]("http://aptoncd.sourceforge.net/") might save you a lot of time in installing/downloading those apps when you re-install ubuntu on other pc!

---

### Post by carl97 on 2011-09-14
> **dFlyer said:**
> Simple answer - No. Just make sure you backup your data files. I've been using linux for the past 15 plus years and only needed to restore linux one time when my hard drive failed on one of my laptops.

I have been using Linux (Ubuntu) for 8 months and had to restore Linux from scratch 15 times !! Please give us noobs some simple way of being able to undo a previous action.

We all like to update, tweak etc but even just a simple issue of Updating Firefox rendered it defunct, uninstalling and reinstalling firefox did not work. So back to Reinstalling Linux from Scratch. 

Rather than doing a full backup surely they must be software that can simply take a snapshot ! like most other OS.

---

### Post by tech-hero on 2011-09-14
Using it for about a year now, and updating didn't cause me any trouble. You may be tweaking a lot of the system files. As far as I know, the updates provided by UBUNTU are the most stable ones as long as you just ticked the "important and recommended" updates. :)

BTW, restoring could be an issue in UBUNTU whenever we tweak some of the system files. I remember before that I almost broke my system good thing that i saved backups.

---

### Post by DarkZhadow on 2011-09-17
> **Jinxzs said:**
> hi guys

i just want to know if there is a restore point in ubuntu like in  windows, i want to install ubuntu, one of our pc in office since its  just for paperworks cause their main problem is viruses and i think it  can help them if i install and teach them how to use ubuntu. before i  do. i want to know if there is some kind of restore point in ubuntu, 

it could help me a lot to maintain the said pc.

--

Kung multiple stations ang kailangan mong i maintain, I would suggest using CloneZilla: [http://clonezilla.org/](http://clonezilla.org/) para siyang Norton Ghost / Acronis True Image ng windows. Pwede kang mag create ng initial IMAGE ng ubuntu, save it sa network folder, then use clonezilla to restore to original settings.

To backup naman yung documents / files, you can try Deja Dup Backup [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup) very easy to configure, simple and effective, pwede mo rin gawan ng schedule for automatic backup.

So in summary: CloneZilla to create image of the OS, Deja Dup Backup for the docs.

---

### Post by savanny1976 on 2012-05-02
> **DarkZhadow said:**
> Kung multiple stations ang kailangan mong i maintain, I would suggest using CloneZilla: [http://clonezilla.org/](http://clonezilla.org/) para siyang Norton Ghost / Acronis True Image ng windows. Pwede kang mag create ng initial IMAGE ng ubuntu, save it sa network folder, then use clonezilla to restore to original settings.

To backup naman yung documents / files, you can try Deja Dup Backup [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup) very easy to configure, simple and effective, pwede mo rin gawan ng schedule for automatic backup.

So in summary: CloneZilla to create image of the OS, Deja Dup Backup for the docs.

Yes, there is...Download "Ubuntu Tweak" , open it.  Look for "Recovery"do snap shot. That will be your restore point. 
To restore open Ubuntu tweak-recovery-restore. that's it!!!

Thanks.

---

### Post by teshnabrown on 2012-07-13
15 years without a need to restore is good but they thats the everyday case, as such they should provide this feature. A week ago i install ubuntu 12.04, and right now I am about to do reinstall as from yesterday it just keeps crashing for no apparent reason. It was working fine the day before;  so there...a case where system restore would be the BEST solution as I have already configured the environment to my likings.

---

### Post by neehs on 2012-07-15
> **savanny1976 said:**
> Yes, there is...Download "Ubuntu Tweak" , open it.  Look for "Recovery"do snap shot. That will be your restore point. 
To restore open Ubuntu tweak-recovery-restore. that's it!!!

Thanks.
... hindi ko sya makita sa Ubuntu Tweak 0.5.14 (Natty)

---

### Post by Script Warlock on 2012-07-16
pwede na siguro remastersys or resync gamitin pang system backup after install at configure sa system.

---

### Post by Pinoy Tux on 2012-07-17
> **Script Warlock said:**
> remastersys
Remastersys FTW!

Ito ang ginagamit ko para makagawa ng updated ISO with my tweaks and customizations.  Ang daling makapag-restore ng complete and updated system.  Only takes as much time as an ordinary installation of Ubuntu from scratch (typically within 20 minutes).

---

### Post by 6wires on 2012-07-18
Yes, of course, you may supply this command to install some additional tools from sources.

**sudo apt-get install backintime-common backintime-gnome **


> **Jinxzs said:**
> hi guys

i just want to know if there is a restore point in ubuntu like in  windows, i want to install ubuntu, one of our pc in office since its  just for paperworks cause their main problem is viruses and i think it  can help them if i install and teach them how to use ubuntu. before i  do. i want to know if there is some kind of restore point in ubuntu, 

it could help me a lot to maintain the said pc.

--

---

### Post by JCyberinux on 2012-09-20
yan din natanong ko before ako mag-switch on ubuntu, kung may backup/recovery plan ba? hopefully, meron naman... as suggested by other members, just used that is convenient to you. 

May na-encountered na ako problems in terms of maintenance lalo kapag walang backup or recovery. In windows hindi ko ginagamit yung system restore point nila, norton ghost or acronis. About sa ubuntu, lagi ako ng babackup particularly kapag may bagong updates, before may inupdate ako sa system after the reboot, hindi na gumana yung ubuntu system may error lumabas. that's the recovery came in handy. :D

---

### Post by Kelicula on 2013-09-11
Has anyone heard of deja-dup? I just totally screwed up my Ubuntu 3.10 by attempting to install nVidia drivers and "restoring" to an earlier backup date, totally fixed. Go to Dash and type deja-dup. Install it if you don't already have it, then quickly make a backup.

---

### Post by oldfred on 2013-09-11
Closed, necromancy. Old thread closed.

---

