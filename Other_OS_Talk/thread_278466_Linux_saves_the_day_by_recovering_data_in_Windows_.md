---
title: "Linux saves the day by recovering data in Windows servers"
date: 2006-10-16
forum: Other OS Talk
---

### Post by rbalfour on 2006-10-16
I am only posting the "FACTS" about Linux. Please click on the link to read more.

> 
I once ran into a case where there was critical data on a disk located on an external storage (SAN) device. A Microsoft utility called chkdsk had been run on the storage disk while it was connected to a Windows NT server. Then they connected the disk to then connected it to a Windows 2000 Server and ran the Windows 2000 version of chkdsk. Bottom line: Windows could not see the disk. We called in Microsoft engineers to look at it, but after a couple of weeks, we gave up and assumed the data was irrecoverable. At that time, there was nothing to indicate the data was corrupt, but it was most definitely inaccessible.

We puzzled over this for quite awhile and then a Linux admin had an idea. Why not hook up a Linux server to the storage array, mount the disk and do a block-level copy of the data to another disk? Well, it worked. We were able to copy the data to a new disk, configure Windows to see the new disk and all the data was intact. I have since used this method to recover data at other sites. While the causes differ, the problem is the same -- Windows is unable to see a disk that it once put data on. Linux, of course, knows nothing about Windows security, so that isn't a problem, and doing a block-level copy just copies raw data. 


Read the WHOLE story here -> [http://searchwinit.techtarget.com/originalContent/0,289142,sid1_gci1223128,00.html?track=NL-372&ad=567960&asrc=EM_NLT_636107&uid=5755103]("http://searchwinit.techtarget.com/originalContent/0,289142,sid1_gci1223128,00.html?track=NL-372&ad=567960&asrc=EM_NLT_636107&uid=5755103")

Now this has to be one of the smartest IT Manager!

---

