---
title: "Are there any disavantages of not having a separate home partition?"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by Viva on 2011-11-08
I've always installed ubuntu with a separate home partition, but I installed without one on my laptop. Are there any serious disadvantages of this? Upgrading is not a problem for me since I back up and reinstall everything or upgrade it directly in ubuntu.

---

### Post by TeoBigusGeekus on 2011-11-08
Not really - you just copy your home folder somewhere before you upgrade/reinstall and you're perfectly ok.

---

### Post by Rex Bouwense on 2011-11-08
None that I have run into since I have all of my data and pictures backed up with flash drives.  It has been said that if you have a separate home and do a lot of tweaking to your computer and happen to break something serious, you can do a fresh re-install without having to screw with your data.  I'm sure someone on these forums will come up with a serious disadvantage.

---

### Post by dFlyer on 2011-11-08
None that I know of, either way is fine, just keep a current backup of your home folder regardless if it's separate or not.

---

### Post by Frogs Hair on 2011-11-08
I use Ubuntu One for storing home folder items at installation time . I just login to Ubuntu One and copy my folders to the new installation . 

If something were to go wrong those folders can be retrieved .  File Sync keeps the folders updated when new items are added .

---

### Post by Viva on 2011-11-08
Does having a separate home partition make ubuntu faster? What about security?

---

### Post by vanadium on 2011-11-08
It won't make the system (noticeably) faster or slower.

In terms of security: if the data partition breaks, the system partition is not and vice versa. With one single partition, it is all or nothing.

This consideration would be important for a large server system. It is of practically no importance for a desktop system, though.

On a small drive, I would favour a single partition install in order to use space most efficiently, and for not having to decide on beforehand how much space to allocate for system and how much for user data.

On a larger drive, I like the convenience of a separate home. On a fresh install, this allows you to keep your user data in place, avoiding the need to re-copy your data (I am renaming my old home, and after installation, move the user data - not the settings - from my old home to the new one).

Single most important thing, though: have a (very) good backup of your user data on a separate medium. Operating systems change every six months and are downloaded for free. Your personal data, once lost, is lost for ever. All else hardly matters.

---

### Post by oldfred on 2011-11-08
While I often recommend a separate /home to new users to make a clean reinstall easier, I do not have separate /home but separate data partitions. My /home folder is only about 1GB and most of that is .wine with Picasa. So I can easily backup /home.

But this works for me on my desktop with multiple drives and multiple installs of Ubuntu. I can share data easily but you cannot share /home.

---

### Post by jerrrys on 2011-11-08
I have multiple drives and multiple installs and do the same as oldfred.

I also like to play and tweak and found Virtualbox good for this, may work for you

---

### Post by mannequin on 2011-11-08
I think that a separate /home partition is good simply for re-installing Ubuntu (or other distros) every 6 months.  It saves you from having to restore it from a backup every time.

A good thing about not having one, though, is that it makes you backup every 6 months if you are like myself and want the most shiny updates all of the time.  :)

-M.

---

### Post by vanadium on 2011-11-08
> **mannequin said:**
> I think that a separate /home partition is good simply for re-installing Ubuntu (or other distros) every 6 months.  It saves you from having to restore it from a backup every time.
-M.
I do not agree and would rather second oldfred:
[quote=Oldfred]
I can share data easily but you cannot share /home.
[/quote]
This also applies to a new version of your favourite distribution. There is no guarantee that configuration files of your previous version will be compatible with the new version you install (although it probably will be > 99.5% OK).

That is why I rename my home: "vanadium -> vanadium_old". Then, I let my fresh install create its own "vanadium" home directory. I then move my user data over from vanadium_old to vanadium. This gives me fresh configuration data, yet spares me from having to copy all data again from the backup.

---

