---
title: "press s to skip mounting or m for manual recovery"
date: 2016-05-25
forum: New to Ubuntu
---

### Post by Knorksen on 2016-05-25
Hello it's another one of this threads.

For installing plasma-systray-legacy I added an Ubuntu 16 rep to Ubuntu 12.
This was stupid and initiated a huge package update.
After that I wasn't able to use sudo anymore.
Any command sudo ... resulted in an instant prompt of: 3 incorrect password attempts.
Without even asking for a password.

I booted into recovery mode and tried to fix it with sudo apt-get -f install, the repair packages option,..., this failed and afterwards I couldn't boot up the system anymore:
Unable to mount media/OS press s to skip mounting or m for manual recovery.

/etc/fstab
> 
UUID=106EDFF66EDFD318 /media/OS ntfs-3g defaults 0 0
UUID=ac2ada2f-ee87-4533-a345-07d8b5f36603 / ext4 defaults 0 1
UUID=9b9296b7-3f2a-4c84-bb7b-3cc800e19844 /home ext4 defaults 0 2
UUID=53465589-62c7-44b2-b7ed-be67dfe055b5 swap swap sw 0 0
UUID=68df4492-5867-4172-9e6c-0e42b49202f6 /media/HDzwo ext4 defaults 0 2


blkid
> 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="5450-4444" TYPE="vfat" PARTUUID ="95f3cb95-01"
/dev/sda2: LABEL="RECOVERY" UUID="EAF6DD80F6DD4E07" TYPE="ntfs" PARTUUID="95f3cb95-02"
/dev/sda3: LABEL="OS" UUID="106EDFF66EDFD318" TYPE="ntfs" PARTUUID="95f3cb95-03"
/dev/sda5: UUID="ac2ada2f-ee87-4533-a345-07d8b5f36603" TYPE="ext4" PARTUUID="95f3cb95-05"
/dev/sda6: UUID="9b9296b7-3f2a-4c84-bb7b-3cc800e19844" TYPE="ext4" PARTUUID="95f3cb95-06"
/dev/sda7: UUID="53465589-62c7-44b2-b7ed-be67dfe055b5" TYPE="swap" PARTUUID="95f3cb95-07"
/dev/sdb1: UUID="68df4492-5867-4172-9e6c-0e42b49202f6" TYPE="ext4" PARTUUID="000737d1-01"


mount -a
> 
mount: according to mtab, /dev/sda3 is already mounted on /media/OS


Maybe someone has any idea how this may be fixed?

---

### Post by oldrocker99 on 2016-05-25
It appears that your system is badly hosed. Backing up your /home folder and reinstalling from scratch is the best of your options, IMHO.

---

### Post by ajgreeny on 2016-05-25
> **oldrocker99 said:**
> It appears that your system is badly hosed. Backing up your /home folder and reinstalling from scratch is the best of your options, IMHO.
Looks as if that might be needed, I admit, but what happens if you remove (or comment out) the first line in your fstab file which seems to be the problem mount?
If you can do so try booting (to recovery again if needed) and then run command ```
mount
```

---

### Post by Impavidus on 2016-05-25
The partition you can't mount appears to be an ntfs (Windows) partition. You don't need that for booting Ubuntu, you can skip it. It may be dirty. In that case Ubuntu won't mount it until Windows has fixed it. Better not to mount Windows OS partitions rw anyway.

But your sudo problem suggests there's more going in. Bad idea to add Ubuntu 16.04 repos to Ubuntu 12.04. Better just install 16.04.

---

### Post by Knorksen on 2016-05-26
Thanks a lot for all your answers I will try this soon.
I'd really like to fix this.

Actually the only possibility I see, being a beginner, is try to solve all dependencies in recovery mode (because sudo doesn't work), what do you think?

Guess just removing the rep and run apt-get wouldn't be a solution, right?

---

### Post by Impavidus on 2016-05-26
Disabling the xenial repos and downgrading everything to precise takes a long time and may not work. The xenial versions of software may have changed files to xenial versions, which the precise version of the software may not be able to handle.

Anyway, 12.04 is an old release by now, approaching end-of-live. You have to move on to 14.04 or 16.04 within a year. You could as well do that right now. Create a live disk, backup your documents,wipe the drive and perform a clean install.

---

### Post by Knorksen on 2016-05-26
Yes there's another one using this system so I wanted to save his installations.
I tried editing the fstab but aftert that the boot up just stopped at the point the message was appearing before.
I think I will install a new version on a new partition so the other user still has acess to the files of the old system.

---

