---
title: "Update manager not showing upgrade option"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by flyfishingphil on 2012-05-01
I've been checking on the upgrade to 12.04 from 11.10 and have found that most places refer to the option in the Update Manager. No such action offered by the one in my laptop.

Any suggestions? Not "computer literate" when it comes to directions so please post for a "newbie" when giving answers. I will have additional questions, like how to save the address list in Thunderbird, before doing the upgrade once this is corrected.

---

### Post by Sidewinder1 on 2012-05-01
I believe that in Update Manager, under Settings there is a place to "tick" Show New Distribution Releases. Just "tick" (check it) it and it should then give you that option.

HTH,
Side

---

### Post by Frogs Hair on 2012-05-01
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
update-manager -d
```

---

### Post by flyfishingphil on 2012-05-01
Checked and the new distribution was set. Did the sudo update, upgrade and update-manager. Still nothing showing. 

Downloaded 12.04 and copied to dvd. Nothing happens when I click on the folders shown there when extracted.

Now totally confused!

EDIT: Went back in a checked folders on download of 12.04. They now open but don't see the opportunity to "test" it first. Will look for more info and see what I can find regarding the installation. Figure I can do a total backup to an external drive by pulling folders to it.

---

### Post by raziel09 on 2012-05-01
In update manager - settings - on the update tab does it show the option "Notify me of a new Ubuntu version" as "for any new versions"?

When you downloaded the iso file did you just copy the iso file onto a cd or did you use a burning tool such as brasero to burn it as a boot cd?

---

### Post by flyfishingphil on 2012-05-01
That was the one! Thanks. It was noted for "long term support". Reset and the upgrade is now showing on the Update Manager. 

Will give it a try and see if it goes OK. Will post results and let those helping know.

EDIT: 

That was a waste of time. Spent a little over 2 hours on the download of upgrades only to have it list a whole series of "Failed to download" regarding along list of "pool" items. No upgrade done. Maybe wait a couple of days and try again.

EDIT: 

Figured I'd give it another try and hit upgrade again. Jumped right in and started the upgrade, getting new packages at file # 1519. Completed loading the 1579 packages needed and continued with upgrade.

Noted during the upgrade a repetitive warning that read:

GTK-Warning Unable to locate theme engine in module_path: "Pixmap", at /usr/share/perl15/Debconf/FrontEnd/Gnome. pm and listed both line 97 and line 103.

Everything seems to be working fine, just a long time to do the entire process but part of that comes with the download speeds. Don't know if they are here or there but it dropped as low as 70Kbps.

Will mark this as solved and go figure out where everything is now.

---

### Post by isalovell on 2012-11-08
> **Sidewinder1 said:**
> I believe that in Update Manager, under Settings there is a place to "tick" Show New Distribution Releases. Just "tick" (check it) it and it should then give you that option.

HTH,
Side

This solved it, but not until I checked on the check box "Only notify me of available updates".

---

