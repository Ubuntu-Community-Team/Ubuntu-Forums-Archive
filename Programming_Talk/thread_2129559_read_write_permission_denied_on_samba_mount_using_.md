---
title: "read write permission denied on samba mount using smbfs"
date: 2013-03-26
forum: Programming Talk
---

### Post by AmbiguousOutlier on 2013-03-26
```
#!/bin/bash

sudo mkdir /mnt/mp3_music
sudo mount -t smbfs //berry/mp3_music /mnt/mp3_music
sudo chmod -R 777 /mnt/mp3_music 
cp ./test /mnt/mp3_music

```

result of cp

```
cp: cannot create regular file `/mnt/mp3_music/test': Permission denied
```

chmod doesn't appear to be working correctly *(by correctly, I mean my understanding of it)*, I only have read access.

If manually goto smb://berry/mp3_music/ I have full permissions but the bash script doesn't like this style of referencing a samba location.

---

### Post by AmbiguousOutlier on 2013-03-26
this worked.

sudo mount -t smbfs //berry/mp3_music /mnt/mp3_music **-o uid=rhys**

I shouldn't have been so eager to ask for help ;)

---

### Post by sanderj on 2013-03-26
> **RhysGM said:**
> this worked.

sudo mount -t smbfs //berry/mp3_music /mnt/mp3_music **-o uid=rhys**

I shouldn't have been so eager to ask for help ;)

Well ... you also gave the answer, so you're actually helping others! :)

---

