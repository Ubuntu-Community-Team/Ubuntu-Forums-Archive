---
title: "Rsync large files onto NTFS?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Twizzle on 2008-06-15
Are there any issues with using rsync onto a Samba mounted NTFS drive other than permissions?

I have a server with an NTFS disk in it (that I also access from an XP Media Portal setup), and currently am trying to use rsync to backup my media collection.

I have a number of folders (Photos, Music, and Video) on my Ubuntu desktop and my script is set up to sync with the same folders on my server. The Photos and Music work just fine but the videos are causing me a problem.

Every time I run the script, it copies all the videos over again even though they are already there.

My permissions are set the same for each folder and I am using:

```
-rWv --delete-after 
```

as my options.

---

### Post by Twizzle on 2008-06-15
I have also tried the:
```
 --modify-window=1
```

option but it still does not work. :(

---

