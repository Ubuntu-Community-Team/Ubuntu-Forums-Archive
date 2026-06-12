---
title: "Have no permission on drive???"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Nemo0075 on 2008-11-14
Hello again,

  Thanks to all that helped me set up my second drive and get it formatted and partitioned.  It would seem that I have run into a bit of trouble again.  I can mount the drive, I just can't do anything else.  I can't create folders or copy files.  When I check permissions, owner is root, group is root.  What do I do?

---

### Post by Eisenwinter on 2008-11-14
Try this:
```
sudo chmod -R 777 <mount point of the drive>

Example: sudo chmod -R 777 /Music/
```

---

### Post by Duck2006 on 2008-11-14
To mount linux partitions.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

To mount windoze partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by taurus on 2008-11-14
Why not just change the ownership from root to your login name instead of running chmod -R 777?

Assuming your login name is nemo and you mount that partition to /media/share. run

```
sudo chown -R nemo:nemo /media/share
ls -la /media/
```

---

### Post by Nemo0075 on 2008-11-14
> **taurus said:**
> Why not just change the ownership from root to your login name instead of running chmod -R 777?

Assuming your login name is nemo and you mount that partition to /media/share. run

```
sudo chown -R nemo:nemo /media/share
ls -la /media/
```

That worked like a charm!  Thanks! :)

---

### Post by Eisenwinter on 2008-11-14
> **taurus said:**
> Why not just change the ownership from root to your login name instead of running chmod -R 777?

Assuming your login name is nemo and you mount that partition to /media/share. run

```
sudo chown -R nemo:nemo /media/share
ls -la /media/
```
Well, you taught me something new here. :lolflag:

---

### Post by Nemo0075 on 2008-11-14
> **Duck2006 said:**
> To mount linux partitions.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

To mount windoze partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I really tried to understand this tutorial but it was like reading Chinese to me:lolflag:  I am still noob although I have been using Ubuntu for over a year now.  Thanks though, maybe one day I will get it.

---

