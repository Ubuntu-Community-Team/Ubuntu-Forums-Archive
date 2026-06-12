---
title: "What is stored in a /home partition?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by psyoptic on 2008-10-31
What exactly is stored in a home partition? Is it just configuration settings or does it also keep data files (i.e. documents, pictures, saved files, etc.)?

Also, do you think 8 gb of /home space is enough if I plan on keeping all my data files on an external hard drive?

---

### Post by hyper_ch on 2008-10-31
/home folder is like the "Documents & Settings" folder on windows. All the user accounts, user data, user config files are stored there. For that reason, it is often recommended to make it a seperate partition.

I did for a while but don't do anymore.

---

### Post by psyoptic on 2008-10-31
> **hyper_ch said:**
> /home folder is like the "Documents & Settings" folder on windows. All the user accounts, user data, user config files are stored there. For that reason, it is often recommended to make it a seperate partition.

I did for a while but don't do anymore.

That's a great explanation! I'll be sure to allocate a reasonable (~8 gb) amount of space on a separate partition for it. Thanks again.

---

### Post by pansz on 2008-10-31
/home directory is different from Windows's "Document and Settings". It is the only directory writable by user. So, user's documents, music, videos, downloads, all and everything should go /home directory, it may be unwise to make it too small.

However, unless you are setting up a server, it is *unlikely* that you really need a separable /home partition.

The newest ubuntu installer can already handle user data well, it will preserve your /home directory and delete anything else when installing to a existing Linux system. So it is NOT NECESSARY to have a separate /home partition since the /home directory in your / root partition will be preserved anyway.

---

### Post by starcannon on 2008-10-31
10~20gb is more than sufficient for the root aka / 
However you can get by on as little as 4gb, and would probably find 8gb does the trick, I like to have a bit of room in my root partition for those times when I feel like trying everything out, so mines 20gb 

Amount of Ram * 2 = swap size

Rest to /home

Home is where the bulk of your storage needs will be centered. It is typically the largest partition on a standard install.

GL and have fun.

---

### Post by 3rdalbum on 2008-10-31
My /home is 139.9 gigabytes used. I realise that you're going to use an external hard disk for much of your user data, but if possible you should consider increasing your /home.

---

