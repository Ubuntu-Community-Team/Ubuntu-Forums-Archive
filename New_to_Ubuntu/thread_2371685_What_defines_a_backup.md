---
title: "What defines a backup?"
date: 2017-09-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-09-17
Namely, what software is true backup software. I get into animated discussions regularly here and other forums about how I use rsync. Get plenty of people saying it's not a backup, but no one ever says what constitutes a real backup program. I can google a list, and if you post about it you get the same thing "not a backup".

So definitively, what is a  true backup program for linux. What can one use to get enterprise grade backups at home, versioned, incrementals, or whatever? I figure if I'm gonna do it it's about time I do it right instead of halfway.

---

### Post by oldfred on 2017-09-17
See TheFu's comments:
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)

But as a home user, I do use rsync to make a copy to another local drive. And my versioned backups are quarterly to DVDs of only the data I consider most important primarily grandkids photos, financial & some data. I do not encrypt as it all is local and also have versions on flash drives, so not as automatic or consistent as perhaps it should be per thread above. I have another set in ILL location so if hurricane in FL destroys place I still have a copy.
I do not back up any of the system, other than a few files with settings. But most of those are edited as part of my install script or have copies in /home as part of my "backup"/copy.

---

### Post by mastablasta on 2017-09-18
it should have versioning, be automated, have ability to backup on  another media (e.g. different disk) and it should be able to easilly restore data.

for example Duplicati, rdiff-backup, areca can all do that.

encryption is necessary if you are sending backups to external drive (e.g. cloud). otherwise it is not needed. 

it also helps if it is fast and doesn't use plenty of system resources. 

my experience - i imaged the OS every couple of months. image was made but there was no information that the data in imag eis actualyl degraded. finally the drive went bust, tried to restore and the image though good had bad data just like on the drive. in the end i did a clear install.

---

### Post by oldrocker99 on 2017-09-18
I have had great success using grsync. It does, however, say that it's 90% done when it's more like 65%. Nonetheless, it's my go-to backup program.

---

