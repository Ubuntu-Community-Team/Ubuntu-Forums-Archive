---
title: "automount ntfs partitions by default"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by zavalita on 2008-08-22
Well, I' m willing to switch from my beloved, pirated copy of XP to some 'distro for newbbies' on the market,and I have some wonders about the friendliness of such a distro.
Is there any distro out there to fully or partly satisfy the following requirements ? 
1. Automount ntfs partitions BY DEFAULT (no need for command line writing) ?
2. Safe write (and read, of course) ntfs
3. Goood gaming with wine, even some old darlings like Counter Strike 1.6
4. Refresh rate recognition for my old Nokia CRT Professional (all the distros I've tried so far put me in the 75-85 hz scheme, but my screen can do 200 on XP, and I do get eye fatigue very easily). I dont' wanna buy an LCD just now.

I mention that I'm looking not only for free distros, and I can  pay some money to get the job done.

Thanx in advance, and I wish you all Linux boys only good times.

---

### Post by Dedoimedo on 2008-08-22
Hello,

1. Most distros.
2. "Safe" - define safe. But basically, yes.
3. Difficult to know unless you try.
4. You can manually reconfigure the refresh rate through xorg.conf.

Dedoimedo

---

### Post by Rolcol on 2008-08-22
Ubuntu is really friendly to new users as compared to some other linux distros.

1) I don't think you can get ntfs to mount by **default** but you can edit /etc/fstab (in a graphical text editor if you wish) to get the job done.  People would be happy to help you here to get that set up.
2) Read/write to NTFS has really improved and I don't think there are any problems with it. (I haven't ran into any myself except I had to force mount it a few times because I had to yank it out of windows without "Safely removing" it.
3) The gaming you would get from Wine would be the same regardless of Distro.  It plays some games (popular ones or old ones) but not all.  You can check the application database if your game's listed there.  [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Loaded.len on 2008-08-22
to fix the forcing bit, couldn't your fstab look like:

/dev/sdaX     /mnt/windows  ntfs-3g    defaults,force 0 0 

where X is the win partition number.

---

### Post by Bradtek on 2008-08-22
HowTo: Automount NTFS Drives

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by Liviu-Theodor on 2008-09-05
I never had any problems with ubuntu recognizing NTFS or FAT32 partitions, for both reading and writing. It never run into any issue. And I have a lot of HDD's to work with.

My nephew even made partitions with NTFS filesystems with the Ubuntu 7.10 live CD, on two PC's, and installed Windows XP on them, even though he does not know Linux at all. Windows never complained for not beeing able to read or write on ubuntu NTFS formatted partitions.

---

### Post by Liviu-Theodor on 2008-09-05
> **zavalita said:**
> Well, I' m willing to switch from my beloved, pirated copy of XP to some 'distro for newbbies' on the market,and I have some wonders about the friendliness of such a distro.
Is there any distro out there to fully or partly satisfy the following requirements ? 
1. Automount ntfs partitions BY DEFAULT (no need for command line writing) ?
2. Safe write (and read, of course) ntfs
3. Goood gaming with wine, even some old darlings like Counter Strike 1.6
4. Refresh rate recognition for my old Nokia CRT Professional (all the distros I've tried so far put me in the 75-85 hz scheme, but my screen can do 200 on XP, and I do get eye fatigue very easily). I dont' wanna buy an LCD just now.

I mention that I'm looking not only for free distros, and I can  pay some money to get the job done.

Thanx in advance, and I wish you all Linux boys only good times.

You could try "Ubuntu Ultimate Edition" or "Ubuntu Gamers Edition" (it is the same, but the author changed the name over time, so I don't know exactly the actual name. The original name was "Ubuntu Christmas Edition". Also, be prepared for a dvd download.

---

### Post by Archmage on 2008-09-05
Kindly note that there is not such thing as "save write NTFS", since even Windows isn't doing it perfectly.

---

