---
title: "Multi-user PC sharing application data"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by m0ezp on 2008-05-27
My first post! After two weeks of learning and frustrations Ubuntu is growing on me but I'm still in the dark with file sharing between users on the same PC...

How can I install something and get each user to share data in that application? The examples I've hit so far are with DOSEMU and WINE where I want all to access the same virtual C drive.

---

### Post by sayakb on 2008-05-27
```
winecfg
```
Goto Drives tab and assign a common destination for drive C

---

### Post by hyper_ch on 2008-05-27
> **m0ezp said:**
> My first post! After two weeks of learning and frustrations Ubuntu is growing on me but I'm still in the dark with file sharing between users on the same PC...

Be more specific about what you want to do.

---

### Post by m0ezp on 2008-05-27
LinuxIsInnovation thanks for the Wine tip - I'll try a glass of that.

hyper_ch - A less DOS/Win example is Thunderbird where I want all the users to share a mail store. I put the mail store on a separate partition, created a folder and shared it.  All users can see the Thunderbird mail store but Thunderbird is always 'doing something'. I'm guessing that it's trying to open the local store and hitting some access difficulty but can't be certain.

---

### Post by hyper_ch on 2008-05-27
for thunderbird I would symlink the profile location in your home directory to the profile location onthe shared partition. What filesystem does that shared partition have?

---

### Post by m0ezp on 2008-05-27
Thanks. I'm also sharing the mail store with Win XP (which works ok) so it's a FAT32 file system. What does symlink do?

---

### Post by Wim Sturkenboom on 2008-05-27
Same as a windows shortcut.

---

### Post by hyper_ch on 2008-05-27
I'd say a windows shortcut is rather a launcher than a symlink.

[http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)

---

### Post by m0ezp on 2008-05-27
Thanks for the info. I'll have a play. Any issues using symlink with a FAT32 partition?

---

### Post by hyper_ch on 2008-05-27
You can link TO a FAT32 partition but you can't create a symlink on the fat32 partition. So you /home/user must not be on a fat32 partition.

---

