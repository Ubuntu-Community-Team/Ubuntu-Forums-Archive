---
title: "How not to use all the RAM"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by mosquetero on 2012-03-28
Hi!

I want to install Ubuntu in my PC again (4Gb of RAM) but for some reasons (mainly to check performance) I just want it to use 2Gb of RAM. Is there any way to restrict the RAM usage? As far as I know when any Linux version is installed it uses the whole RAM automatically.

Thanks

---

### Post by Paqman on 2012-03-28
Pull out one of the RAM sticks?

---

### Post by HermanAB on 2012-03-28
One way is to create a RAM Disk sized 2GB using tmpfs.

---

### Post by mastablasta on 2012-03-28
or you can also install it in vbox and give the virtual system "only" 2 GB ram.
 
btw performance with 2GB is fine and snappy.
 
the issue might be the GPU.

---

### Post by mosquetero on 2012-03-28
Thank you!

I cannot just pull the RAM sticks :(

I cannot use anything virtualized since I want to make some tests in a native LINUX.

tmpfs looks interesting I will investigate, thanks

---

