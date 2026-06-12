---
title: "Networking"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-23
I currently have two Ubuntu servers setup, let's say one is ip1 and the other is ip2. I am currently in the office where the ip1 server is present and therefore I can download and view folders/files quickly and easily, but the other office where ip2 is located half way around the world and takes me forever/endless hours to download files - is there a way for ip1 to be constantly connected to ip2 and have the files from ip2 transferred over to ip1 automatically as a direct copy so that I am able to view it more quickly and efficiently?

---

### Post by sp0nge on 2008-07-23
I'm just getting into these waters myself, but wouldn't you be able to sftp into ip2 from ip1 to create your connection? I don't know if this would address your download speed, but at least you'd be connected.

---

### Post by Xerp on 2008-07-23
Yes. Use rsync :)

---

### Post by waterrr on 2008-07-23
resync?

are further explainations possible?

---

### Post by dca on 2008-07-23
How are you getting these files from overseas?  Samba share or FTP???  Should all the data stored on these servers be in synch or are we talking about certain directories?  Would it be easier to set up on samba share directory should synch up once every night?  You can use 'rsync'...  I don't know, lots of options available.

---

### Post by dca on 2008-07-23
You can set-up a 'cron' job so that way the rsynch happens automatically at a certain time when both offices are not accessing particular directory.

---

### Post by dca on 2008-07-23
cron = [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)
     [http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/custom-guide/cron-task.html](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/custom-guide/cron-task.html)
 
rsynch = [http://www.ss64.com/bash/rsync.html](http://www.ss64.com/bash/rsync.html)
    [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

---

### Post by waterrr on 2008-07-23
i can access ip2 just through adding a network onto my personal pc, it's a ftp over there

---

### Post by Xerp on 2008-07-23
[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

[http://transamrit.net/docs/rsync/](http://transamrit.net/docs/rsync/)
[http://www.fredshack.com/docs/rsync.html](http://www.fredshack.com/docs/rsync.html)

---

### Post by waterrr on 2008-07-23
how do I install rsync?

---

### Post by dca on 2008-07-23
Who is the sys admin for this server?  I believe it's installed by default on Ubu Server, if not then whoever admins would need to 'sudo apt-get install rsync' at CLI...

---

### Post by waterrr on 2008-07-23
I got confused thinking the Ubuntu distro didnt have it (typo) thanks for the help

---

### Post by dca on 2008-07-23
No prb, good luck!  Using a syncing app is a lot easier than trying to figure out how to turn two boxes on either side of the planet into a 'high availability linux cluster with fail over and load balancing' yadda yadda....:)

---

### Post by waterrr on 2008-07-24
From the link [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/) it says to use these following command lines to use rsync itself
```
rsync --verbose  --progress --stats --compress --rsh=/usr/local/bin/ssh
      --recursive --times --perms --links --delete \
      --exclude "*bak" --exclude "*~" \
      /www/* webserver:simple_path_name

```

but I get confused on what /www/* is suppose to be along with webserver and simple_path_name...whoever wrote this tutorial sort of fudges it in the end...

---

### Post by waterrr on 2008-07-24
still need help

---

### Post by waterrr on 2008-07-28
anybody?

---

