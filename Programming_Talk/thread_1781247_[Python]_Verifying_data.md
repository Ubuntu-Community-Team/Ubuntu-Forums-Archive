---
title: "[Python] Verifying data"
date: 2011-06-13
forum: Programming Talk
---

### Post by ki4jgt on 2011-06-13
I'm going to have data coming from x untrusted sources. The data is supposedly the same, but the sources could have altered it in some way. To verify the data, the program needs to take the number of copies received and compare them. The program should take keep all the copies which are identical or the copies which have the most duplicates (even if just 2 out of X of the copies are duplicates the other 6 <all different> should be thrown out) How would I do this? Is there a function for this?

---

### Post by denarced on 2011-06-13
> **ki4jgt said:**
> I'm going to have data coming from x untrusted sources. The data is supposedly the same, but the sources could have altered it in some way. To verify the data, the program needs to take the number of copies received and compare them. The program should take keep all the copies which are identical or the copies which have the most duplicates (even if just 2 out of X of the copies are duplicates the other 6 <all different> should be thrown out) How would I do this? Is there a function for this?

This depends on what kind of data are you receiving and from where.
From another process? from TCP?

---

### Post by ki4jgt on 2011-06-13
```
It's from TCP/IP. I'm using sockets with threading and am connected to about 10 people at once. There's an IP access list. All other connections are refused.

Each bit of data could come from any of the 10 IPs even some twice. Each file has a table of SHA keys for other files which are related to that file. IOW, file A B C all form folder D. Naming scheme goes like this (each letter represents the SHA of that particular set of data D represents SHA of folder in it's entirety):

1:D
2:D
3:D

Each file, will have a file allocation table :-) LOL written within it, which identifies all the files which are related to the folder, so:

1:D's FAT would be:

1:A
2:B
3:C

all files in folder D would have the same FAT. As the program got more of folder D say it gets files 1 and 2, it would check them against each other. If mismatches were found, it would check them against 3, which ever two FATs matched, would be the one the computer kept. It would throw out the other file and try to find one which matched the FAT.
```

---

