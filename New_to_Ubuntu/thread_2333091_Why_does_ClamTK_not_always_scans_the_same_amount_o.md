---
title: "Why does ClamTK not always scans the same amount of files?"
date: 2016-08-06
forum: New to Ubuntu
---

### Post by xenon3 on 2016-08-06
The range is about 4,000 to 14,000 files in HOME folder virus scanned. What I mean 9,000 then 12,000 then 6,000 then 4,000 then 14,000 then 14,000 then 5,000 and so on

That is highly unlogical, is nondeterministic, I don't see the point why it should be a nondeterministic scan algorithm

---

### Post by yetimon_64 on 2016-08-06
I am not sure exactly how clam-tk works, but some AV scanners will use file hashes to determine what files are to be scanned. If the hash value of a file is changed or the file is new from the last scan then it is scanned however if a file has been previously scanned but has not changed (hash is the same) then it would be skipped. In such circumstances the number of files scanned will depend on the system usage of them and the scanned files figure can vary wildly as you note here. 

This may possibly explain how such strange scanning results can occur. Though as I noted earlier I have no idea about the actual workings of clam-tk itself.

---

### Post by xenon3 on 2016-08-07
> **yetimon_64 said:**
> I am not sure exactly how clam-tk works, but some AV scanners will use file hashes to determine what files are to be scanned. If the hash value of a file is changed or the file is new from the last scan then it is scanned however if a file has been previously scanned but has not changed (hash is the same) then it would be skipped. In such circumstances the number of files scanned will depend on the system usage of them and the scanned files figure can vary wildly as you note here. 

This may possibly explain how such strange scanning results can occur. Though as I noted earlier I have no idea about the actual workings of clam-tk itself.

Interesting :cool:

---

