---
title: "random missing files on external drive"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by PermNoob on 2012-08-19
I had an old PC, the mobo/processor died but I saved the HDD desiring its contents.  My new machine doesn't have an IDE slot, so I have the drive in an external firewire enclosure.  It turns up fine, but it seems about half the contents are missing. I am pretty sure the 160 gigs were totally full on the old machine, but now its half empty.  Also folders are missing files, seemingly at random.  I really don't want to loose this data.

Example:
I have a folder which contains a direct CD rip of a music CD.  If I open it, there are 9 files, but its a 13 track CD.  If I select and copy them all, they all go to the new machine.  If I select the parent directy and hit copy I get this message:

```
Error when getting information for file '/media/696067e8-ae6f-450f-870a-641c6b7bf06d/media/music/98/Music/She Wants Revenge/10 Someone Must Get Hurt.mp3': Input/output error
```

the important thing to note is track 10, which threw that error code, is NOT visible in the folder, IE it is one of the missing 4 files.  Checking "show hidden files/folders" does not reveal the missing files either.

please help!  this is very not good.

---

### Post by sandyd on 2012-08-20
> **PermNoob said:**
> I had an old PC, the mobo/processor died but I saved the HDD desiring its contents.  My new machine doesn't have an IDE slot, so I have the drive in an external firewire enclosure.  It turns up fine, but it seems about half the contents are missing. I am pretty sure the 160 gigs were totally full on the old machine, but now its half empty.  Also folders are missing files, seemingly at random.  I really don't want to loose this data.

Example:
I have a folder which contains a direct CD rip of a music CD.  If I open it, there are 9 files, but its a 13 track CD.  If I select and copy them all, they all go to the new machine.  If I select the parent directy and hit copy I get this message:

```
Error when getting information for file '/media/696067e8-ae6f-450f-870a-641c6b7bf06d/media/music/98/Music/She Wants Revenge/10 Someone Must Get Hurt.mp3': Input/output error
```the important thing to note is track 10, which threw that error code, is NOT visible in the folder, IE it is one of the missing 4 files.  Checking "show hidden files/folders" does not reveal the missing files either.

please help!  this is very not good.
STOP.
using the drive immediately - the more you use it, the harder it becomes to recover the data.

It looks like the HDD has suffered damage as well. You will want to run recovery software such as Spinrite, testdisk, .etc .etc

---

### Post by PermNoob on 2012-08-20
that is just one of those things you never want to hear. any more advice or details?  remember this is an external drive in an enclosure...

---

### Post by Wim Sturkenboom on 2012-08-20
As sandyd said, testdisk or similar utilities might do the trick. I think testdisk / photorec is in the repositories.

---

