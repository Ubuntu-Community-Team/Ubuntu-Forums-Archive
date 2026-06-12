---
title: "my external ubuntu HD"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by hmiersch on 2015-03-09
hi. i used to boot ubuntu from an external HD until a failed update made that partition unusable. so i installed ubuntu on my internal HD and i'm running gparted on the problem HD. assuming it recovers the partitions, how can i make that HD bootable again, preferably without losing any data?

---

### Post by v3.xx on 2015-03-09
> how can i make that HD bootable again, preferably without losing any data

Can you first backup your data using your new install (FileManager) to access the ext drive.

Also a bad update/upgrade does not necessary mean a partition problem.

---

### Post by hmiersch on 2015-03-09
i tried "attempt data rescue" in gparted, and it couldn't find anything. that HD appears to be unformatted / unpartitioned. i guess this means those files are gone, right? or is there anything else i can try?

---

### Post by v3.xx on 2015-03-09
If you wish to try recovery software

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by hmiersch on 2015-03-15
i know it took me a while but i've used testdisk to recover the files i wanted from that bad partition. but now when i try to do anything with those files (like delete the duplicates) ubuntu tells me that i'm not the owner and refuses to cooperate. so what can i do about that? (those files are on my ubuntu disk).

---

### Post by v3.xx on 2015-03-16
Sounds like your just about there, good show :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+owner+of+file+in+terminal&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+owner+of+file+in+terminal&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2015-03-16
You probably have to make sure you are the ower and have permissions.

Did you copy to another partition or are they in your /home?
You may just need chmod or chown commands on partition, folder or just the files.

       [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by hmiersch on 2015-03-18
The files were recovered from that failed partition on the external HD and saved in my home folder which is on my internal HD. 

I think I had to use sudo from my admin account, and my theory is that that's why the files were owned by root. But chown fixed that. Now I can move them where they belong, and remove the duplicates that appeared out of nowhere...

---

### Post by v3.xx on 2015-03-18
Sounds like you got it.  A lot of people are not so lucky.  Maybe time for you to consider a backup plan.  And just so happens 'oldfred' has input on that too :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup+oldfred&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup+oldfred&sa=Search&cof=FORID:9)

Don't forget
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

