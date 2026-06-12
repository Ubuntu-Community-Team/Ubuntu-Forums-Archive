---
title: "Out of disk space but actually have plenty"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by manekineko2 on 2012-05-04
I was trying to gunzip a largish file, big_file.gz is about 5GB, and according to file roller the contents is a single file about 4GB.

It's failing due to disk space issues even though I have a ton of free space.

```
$ gunzip ./big_file.gz

gzip: ./big_file.txt: No space left on device
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              50G   26G   21G  56% /
none                  498M  232K  497M   1% /dev
none                  502M  252K  501M   1% /dev/shm
none                  502M  208K  501M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
Projects              466G  299G  168G  65% /mnt/projects

```

Anyone have any advice on what is going on here?

Ubuntu also popped up a warning, and then I ran the Disk Usage Analyzer:
[IMG]http://i.imgur.com/6Aas2.png[/IMG]

If it makes a difference, I'm running Ubuntu 10.04 inside of a VirtualBox image. /mnt/projects is a VirtualBox link to a folder on my host OS.

---

### Post by Cheesemill on 2012-05-04
Try unmounting /mnt/projects and seeing if there is anything remaining in the directory.

---

### Post by manekineko2 on 2012-05-04
> **Cheesemill said:**
> Try unmounting /mnt/projects and seeing if there is anything remaining in the directory.

Here is the updated df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              50G   26G   21G  56% /
none                  498M  232K  497M   1% /dev
none                  502M  264K  501M   1% /dev/shm
none                  502M  208K  501M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
```

Manually entering /mnt all I see are empty mount points.

---

### Post by ajgreeny on 2012-05-04
How is it that a 5GB archive contains only one file which is just 4GB?

Something does not compute properly with that statement; where did the extra 1GB go to?

I do not use any virtualbox OSs on my machine, so I have no idea if that has any bearing on the problem, so will leave that to others.

---

### Post by manekineko2 on 2012-05-04
> **ajgreeny said:**
> How is it that a 5GB archive contains only one file which is just 4GB?

Something does not compute properly with that statement; where did the extra 1GB go to?

I do not use any virtualbox OSs on my machine, so I have no idea if that has any bearing on the problem, so will leave that to others.

I thought that was strange myself, but chalked it up to the fact that in weird scenarios, compressing files can actually increase the final size.

That said, that's a good avenue of further thought, maybe I'll try this same file in another OS's unzipper.

---

### Post by lisati on 2012-05-04
> **manekineko2 said:**
> I thought that was strange myself, but chalked it up to the fact that in weird scenarios, compressing files can actually increase the final size.

One of life's apparent mysteries. I don't claim to be an expert on file compression - some of the approaches are over my head - but suspect that the file didn't lend itself well to the particular compression methodology that ended up being used.

---

### Post by CharlesA on 2012-05-04
Run this in any case:

```
du -hi
```

---

### Post by manekineko2 on 2012-05-04
Okay, mystery solved!

Turns out the packed size reported by the .gz was incorrect. File Roller said 4.0GB and 7zip in Windows said 4,253,224,534 bytes.

Turns out actual size of the contents was 25GB!

---

### Post by CharlesA on 2012-05-04
> **manekineko2 said:**
> Okay, mystery solved!

Turns out the packed size reported by the .gz was incorrect. File Roller said 4.0GB and 7zip in Windows said 4,253,224,534 bytes.

Turns out actual size of the contents was 25GB!
Wow, that's some nice compression!

---

