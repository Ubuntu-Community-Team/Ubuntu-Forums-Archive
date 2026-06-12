---
title: "[SOLVED] Home partition problem"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by jon555 on 2008-10-27
I wanted to make one of my partitions home. I followed this tutorial 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 
but in this step
  Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
gksudo gedit /old/etc/fstab

ubuntu@ubuntu:~$ sudo cp /old/etc/fstab /old/etc/fstab_backup
cp: cannot stat `/old/etc/fstab': No such file or directory

Something went wrong and now I have copied home to that other partition, but I cant boot computer, it says no Home. 
(BTW, is it wright - on old partition it was Home/jon now on new it's jon shoul it be so? And should there be empty home directory on old one, should I delete it?)
How to make Ubuntu understand where my new home is?

---

### Post by francisc1701 on 2008-10-27
Boot the cd again and go straight to the part that says "Using the new partition". Starting from there redo everything and just ignore any message that says "not found" or similar, until you get to that ```
cp /old/etc/fstab /old/etc/fstab_backup
```. If you get the same error again then something really is wrong. If that command succeeds just follow the tutorial.

Yes, there has to be an empty /home folder on the old one, and the new one has to contain just /jon. Don't delete the empty /home.

---

### Post by jon555 on 2008-10-31
> **francisc1701 said:**
>  If you get the same error again then something really is wrong.  /jon. Don't delete the empty /home.

It I got the same error again, tries also other tutorials, didn't succeeded and reinstalled using just a empty fat 32 for backup purposes.  Thnx for help.

---

### Post by meindian523 on 2008-10-31
> **jon555 said:**
> I wanted to make one of my partitions home. I followed this tutorial 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 
but in this step
  Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
gksudo gedit /old/etc/fstab

ubuntu@ubuntu:~$ sudo cp /old/etc/fstab /old/etc/fstab_backup
cp: cannot stat `/old/etc/fstab': No such file or directory

Something went wrong and now I have copied home to that other partition, but I cant boot computer, it says no Home. 
(BTW, is it wright - on old partition it was Home/jon now on new it's jon shoul it be so? And should there be empty home directory on old one, should I delete it?)
How to make Ubuntu understand where my new home is?
That command expects you to substitute the path for the old fstab,which is /etc/fstab,and not copy paste that command directly.The actual command would thus be
```

sudo cp /etc/fstab /etc/fstab_backup
```
get it?Then you can follow the remaining steps as prescribed.

---

