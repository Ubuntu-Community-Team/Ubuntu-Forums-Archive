---
title: "Sneakily stealing my bandwidth"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-08-11
Hi all

I have a process somewhere that is sneakily using up my Internet Bandwidth. I have already read that it could be Update Manager, so I have set Update Check to Never. 
Is there anything else that could be downloading in the background? I have dropbox, so I have killed that process, and killed also the UbuntuOne daemon. 
Are there any utilities that can log, or display, process downloads?

Cheers
Glenn.

---

### Post by whatthefunk on 2013-08-11
The command "lsof -i" will show you what applications are currently using the network.  That should get you started.  Some other places that might be useful for you:
[http://askubuntu.com/questions/104739/which-applications-are-using-internet](http://askubuntu.com/questions/104739/which-applications-are-using-internet)
[http://askubuntu.com/questions/152093/how-do-i-find-out-which-program-is-using-internet-and-how-much](http://askubuntu.com/questions/152093/how-do-i-find-out-which-program-is-using-internet-and-how-much)

---

### Post by zealibib slaughter on 2013-08-12
you can try wireshark, there are some good guides online on how to use it.  It gives detailed information on what, who, when, where is it going/coming from, and how about every connection made through whatever port you specify. just saying you will be shocked at how many times in a minute you router asks for a who has an ip.

---

### Post by sandyd on 2013-08-12
try
```

iftop -PN
```
which will show you current connections and the port that is transfering data

You can then look the port up with
```

lsof -i :port
```

---

### Post by 3rdalbum on 2013-08-12
Why not start simple first? System Monitor will show you how much bandwidth is being used at any given time. It wont tell you what is using bandwidth, but if you are getting little or no bandwidth use you don't need to go further.

Update Manager should not use enough bandwidth to be a problem. It will download maybe 20 megs first go, and then a Meg or less each day when there are updates.

---

### Post by Senior_Buckethead on 2013-08-12
Yeah I agree entirely. System Monitor's great, and thats how I know if I have anything using bandwidth, by how many megs I have downloaded.

I wasn't convinced that Update Manager was the problem, but I thought I would eliminate it as a possibility as I went.

Shame there isn't a utility that real-time tracks any processes that are using bandwidth, that can tell you exactly how much they are down (or up)loading at any one instant.

I appreciate all the help, and now I have to go away and digest it all, probably returning with yet more questions...

Glenn.

---

### Post by whatthefunk on 2013-08-12
> **Senior_Buckethead said:**
> Yeah I agree entirely. System Monitor's great, and thats how I know if I have anything using bandwidth, by how many megs I have downloaded.

I wasn't convinced that Update Manager was the problem, but I thought I would eliminate it as a possibility as I went.

**Shame there isn't a utility that real-time tracks any processes that are using bandwidth**, that can tell you exactly how much they are down (or up)loading at any one instant.

I appreciate all the help, and now I have to go away and digest it all, probably returning with yet more questions...

Glenn.

In a terminal, type "lsof -i"  It does exactly that.

---

