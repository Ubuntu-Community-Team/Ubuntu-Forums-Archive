---
title: "Live CD Boot takes 15+min - And then freezes in desktop."
date: 2011-12-06
forum: New to Ubuntu
---

### Post by noobtube on 2011-12-06
Hey Everyone,

After searching the forum and using google.
I just had to make a post.
I am very sorry if i missed something and wasting your time sorry.

My Windows was Dieng and i was tired of it not running nice.
Then i found ubuntu and i was very pleased with it.
I could run the live CD and recover everything i needed! SO COOL!

But then i tried the GParted because i wanted to intall ubuntu on it because i like it so much.
But after i did that. The CD take more then 15 min too boot :( And then it just freezes when i try to do anything.

In Gparted i did FAT32. (maybe should not done that)

Sometimes i can get iin the console thingy right before it freezes.
So i thought maybe i can type something there?

This is what i get at start of Live CD
timeout: 'sbin/blkid -o udev -p /dev/sda'

And then VERY LONG Wait time. and it boots up and then freezes when i try to view HDD.

---

### Post by beew on 2011-12-06
Definitely NOT Fat32 or NTFS. Use ext4.

---

### Post by critin on 2011-12-06
> In Gparted i did FAT32. (maybe should not done that)Run the live CD again, from the desktop choose install ubuntu.  Choose the same partition it is now on.  Let the installer do the format--if it asks you to decide which format, choose ext4.   Install over the current ubuntu.

> My Windows was Dieng and i was tired of it not running nice.
Then i found ubuntu and i was very pleased with it.

Did you install over windows or did you keep windows?  If you installed over windows its even easier--just install it again.

---

### Post by noobtube on 2011-12-06
Well the thing is...
It freezes in install :$

---

### Post by DapperMe17 on 2011-12-07
It could be as simple as your LiveCD just being corrupt.  

Do this...re-download your ISO (check the md5sum if you know how to to that) and then burn it at the slowest possible speed. 

Then give it another shot!

:popcorn:

---

