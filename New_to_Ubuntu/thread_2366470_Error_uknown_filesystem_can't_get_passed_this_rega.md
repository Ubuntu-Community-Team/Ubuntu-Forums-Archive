---
title: "Error: uknown filesystem can't get passed this regardless of known fixes."
date: 2017-07-18
forum: New to Ubuntu
---

### Post by drakeuno on 2017-07-18
Hello I'm new to ubuntu (only used mate once or twice). I got this system yesterday and when I try to boot it gives me error: unknown filesystem. 
I went to google with this and tried the most common solution that everyone suggested.
 Using "ls" to get my partitions (hd0) , (hd0,msdos6) , (hd0,msdos5) , (hd0,msdos4) , (hd0,msdos3) , (hd1) , ((hd1,msdos1)
I used set boot=(hd0,msdos6) , set prefix=(hd0,msdos6)/boot/grub , insmod normal this is where I get "error: unknown filesystem." 
I tried it this with every single partition and all of them gave me the same error. 
I decided to make a live rescue cd which gave me this [http://paste.ubuntu.com/25117253/plain/](http://paste.ubuntu.com/25117253/plain/)

Thank you for your time. I hope I posted in the correct forum and provided sufficient info.

---

### Post by deadflowr on 2017-07-18
Well, if you had an Ubuntu OS installed, it's gone now.
Your choices are to either try running some forensics like testdisk:
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

or,
Just scrap it and do a reinstall.

---

### Post by yancek on 2017-07-18
You have two ntfs (windows) partitions, what are those?  Just data or do you have some version of windows?
The ls command you refer to isn't going to provide any kind of solution, it just 'lists" information hene the 'ls'.
If the windows partitions are not data but a windows install, did you do any updates on it recently?
I'd agree that there doesn't seem to be any sign of any Ubuntu install.

---

