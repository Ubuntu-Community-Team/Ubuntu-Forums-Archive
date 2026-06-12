---
title: "Hard drive problem"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by kuraiitaki on 2012-08-28
I have two internal hdd's: one 160gb for operating system and one 1tb for storage. I also have two other people who use my computer who I've set up with standard accounts. One of my users  was trying to watch a movie from the storage hdd, but was unable to access said drive. When I logged onto my admin account, I could access the drive. Is this a permissions problem? How do I let my users access the drive? I'm hoping I don't need to make them administrators as they like to mess with things they shouldn't...

---

### Post by taras.kuzyo on 2012-08-28
run in terminal:
```
ls -l <path to movie>
```
and post here output

---

### Post by Naimar on 2012-08-28
sudo chmod 777 /media/usbhd/movie.avi (or whatever file)

---

### Post by kuraiitaki on 2012-08-28
Taras, will try when I get home and let you know. 
Naimar, when I tried sudo commands with the standard user, it gave me an error and said it had been reported.

---

### Post by cortman on 2012-08-28
> **kuraiitaki said:**
> Naimar, when I tried sudo commands with the standard user, it gave me an error and said it had been reported.

That's because your user was not in sudoers.
I doubt you need write/execute permissions simply to play a video file.

What exactly do you mean by "cannot access the drive". Does the drive show up in /mnt or /media, but they can't browse files in it? Or does it not show up at all?
It could be the way it's mounted.

---

### Post by kuraiitaki on 2012-08-28
> **Naimar said:**
> sudo chmod 777 /media/usbhd/movie.avi (or whatever file)

> **cortman said:**
> That's because your user was not in sudoers.
I doubt you need write/execute permissions simply to play a video file.

What exactly do you mean by "cannot access the drive". Does the drive show up in /mnt or /media, but they can't browse files in it? Or does it not show up at all?
It could be the way it's mounted.

They aren't even able to see that it is a part of the system. When I bring up a folder to nav, it's listed as a device on the left hand bar of the window just like bookmarks and other links, but when my other user brings up a window to nav to it, it just isn't there.

---

### Post by cortman on 2012-08-28
> **kuraiitaki said:**
> They aren't even able to see that it is a part of the system. When I bring up a folder to nav, it's listed as a device on the left hand bar of the window just like bookmarks and other links, but when my other user brings up a window to nav to it, it just isn't there.

[This link]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") should help you. See the section on Systemwide Mounting. Any questions, post back.

---

### Post by kuraiitaki on 2012-08-28
> **cortman said:**
> [This link]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") should help you. See the section on Systemwide Mounting. Any questions, post back.

This is what the commands it told me to run returned with:

```
kurix@HomePC:$ /usr/bin/udisks --mount /dev/disk/by-uuid/B0D4F9D5DF99E32
Mount failed: /dev/sbd5 is mounted
```

---

### Post by cortman on 2012-08-28
> **kuraiitaki said:**
> This is what the commands it told me to run returned with:

```
kurix@HomePC:$ /usr/bin/udisks --mount /dev/disk/by-uuid/B0D4F9D5DF99E32
Mount failed: /dev/sbd5 is mounted
```

First run

```
sudo umount /dev/sdb5
```

---

