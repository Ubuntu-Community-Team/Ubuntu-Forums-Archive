---
title: "Read-only external HDD. Please Help."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Godofgrunts on 2008-04-23
My friend is using a live CD to run 7.04 to recover some files and to put them on an external harddirve. However, when I try to copy the files over, it tells me it is read-only. I tried changing the permissions and unmounting and remounting it. Apparently, I didn't remount it with read and write files on it... Please help.

If it helps, it is /media/disk-1

---

### Post by SunnyRabbiera on 2008-04-23
Copy over using what, the live?
can you be a bit more specific?

---

### Post by Godofgrunts on 2008-04-23
Sorry. I'm trying to copy files from a the hard drive in his laptop onto an external hard drive. When I do, it says "You do not have permission to write to this folder." I'm not sure how to fix this. I can't eject or unmount the drive either. It says "cannot eject". And when I try to take files out it says it is read-only.

He's using a Ubuntu 7.04 from the Live CD.

---

### Post by SunnyRabbiera on 2008-04-23
hmm, is his hard drive encrypted or something?

---

### Post by Godofgrunts on 2008-04-23
Not that I know of. It was working on windows.

BTW I can pull files off of it. Now... I ran some code from [here]("http://ubuntuforums.org/archive/index.php/t-244611.html") and I can pull files off now.

---

### Post by ace007 on 2008-04-23
Is the hard drive formatted in NTFS.  Meaning is it the default windows file system?

If it is Ubuntu before 7.10 doesn't write to NTFS.  You must install ntfs-3g.

```

sudo apt-get install ntfs-3g

```

Or use a 7.10 of 8.04 LiveCD

---

