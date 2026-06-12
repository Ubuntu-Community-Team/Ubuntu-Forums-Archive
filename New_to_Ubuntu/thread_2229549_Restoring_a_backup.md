---
title: "Restoring a backup???"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by amzolt on 2014-06-13
I'm a newbie to Linux---have 14.04 installed---created a new folder called "Backup" in the deja-dup folder---did a backup and it seems to be in the folder I created...

There are 48 .gpg files called "volumes" and a "signature" file --- all beginning with "duplicity-full"...

I checked "Restore" and there is a button there called "Forward" <--- Is that what begins a Restore??

Also, while the backup was running, I noticed that it looked like all the programs I'd installed were being backedup...

Is this true? --- Is a backup on Linux like what Windows users call a "Clone"?

Also, the scheduler for backups only has "daily" and "weekly"---If I choose weekly, how do I know which day of the week the backup will run or what time of day????

---

### Post by monkeybrain20122 on 2014-06-13
No, deja-dub does only file backup. To make a clone you need something like clonezilla or fsarchiver.

I would recommend fsarchiver if you are not using UEFI or gpt. It is easy to use, fast and a lot more flexible than sector by sector cloning tools like clonzilla. It is in the repo.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by amzolt on 2014-06-13
Thanks for the swift reply---I'd checked to be notified if anyone replied but I got now email of your reply, I just came back and looked at my post...

You say fsarchiver is "in the repo"---where is that?

---

### Post by amzolt on 2014-06-13
Also, can a Clone with fsarchiver be made on the same hard disk as the Linux installation???

---

### Post by amzolt on 2014-06-13
> **monkeybrain20122 said:**
> No, deja-dub does only file backup. To make a clone you need something like clonezilla or fsarchiver.

I would recommend fsarchiver if you are not using UEFI or gpt. It is easy to use, fast and a lot more flexible than sector by sector cloning tools like clonzilla. It is in the repo.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

So, MonkeyBrain, is the "Forward" button the way one starts a restoration of a backup?

Also, I assume the backup just replaces files and all the programs would be just as before???

---

