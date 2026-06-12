---
title: "[SOLVED] Taking data of a hDD when Ubuntu has god bad"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by unknown user on 2008-12-01
[FONT="Tahoma"]I have tried to install 8.10 and it did not work and now I can not load the desktop. (If you are thinking of any kind of upgrade, please make sure you back up your data).

I have another HDD (or can boot from the live disk), all I want is a few files from the desktop and my emails & contacts from my Thunderbird. 

Does anyone konw the paths for these files so I can get them out and then re-install 8.10?[/FONT]

---

### Post by Her Ghost on 2008-12-01
Your Thunderbird files should be in:

/home/username/.thunderbird    (i.e. it will be hidden)

your desktop files are in:

/home/username/Desktop

---

### Post by unknown user on 2008-12-01
Thanks for this, I will have a look at it tonight when I get back from work and get the files.
With the emails, I am hoping it will be a simple case of taking the file from the old system and putting it direct into a new system?

---

### Post by jimmy the saint on 2008-12-01
I would recommend backing up your entire /home/user directory.  That way, your customized setting for your software will be saved as well.  It saves me a lot of time when upgrading.  Also, you may want to look at haveing a seperate partition as your /home.  that way, you don't have to worry about transfering it every time you upgrade

---

### Post by Her Ghost on 2008-12-01
Yes this should be how it works.  I think (not tried it yet, but need to soon - I have my thunderbird folder on a usb stick a the moment) you just dump the settings folder in your new /home/username/ folder and either 1. it just finds it, or, perhaps more likely, 2. you tell it to import.

I will post how I go on with it when I get round to doing it.  Maybe tonight.

---

### Post by unknown user on 2008-12-01
[FONT="Tahoma"]This sounds like it is just what I need and hopefully all emails/contacts will be there.

If I installed the new 8.10 on a new hdd and then imported my old /home/user directory, would this bring all my old settings from my old system to my new one without me having to mess about with the settings?[/FONT]

---

### Post by unknown user on 2008-12-01
I have found these files all OK but they are locked, how can I get into these files that are locked?

---

### Post by ncanna1 on 2008-12-01
> **unknown user said:**
> I have found these files all OK but they are locked, how can I get into these files that are locked?

Locked, as in you don't have permission to access?  You could try to change ownership of the files to your new user.

---

### Post by unknown user on 2008-12-01
Hiya yes sorry theya re locked and say that I do not have permission. I have tried to put them on my usb but not allowed to.

Sorry how would I change the permission to my new user?

---

### Post by unknown user on 2008-12-03
[FONT="Tahoma"]I rebooted the system and then created the second account again and then was asked for a password when I put the flash pen in, this allowed me to access the pen fine.

I have now installed a fresh copy of 8.10 and forgot about my old version and imported my emails, contacts and desktop all fine. I was surprised at how easy it was to tell you the truth.

I now just have to set up the new system the way I had my old one and all is good in the world. However, I will know for next time to take a backup of my home/(username) file just in care.[/FONT]

---

