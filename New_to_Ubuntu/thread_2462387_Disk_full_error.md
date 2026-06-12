---
title: "Disk full error"
date: 2021-05-19
forum: New to Ubuntu
---

### Post by chaos-resigned on 2021-05-19
A friend setup a custom ubuntu security system for my ip cameras. It's worked fine but suddenly it stopped working. I accessed the webmin and it says the entire 200gb drive is full. Now webmin wont even start. There isnt any reason that the disk should be full but as it appears to be so most commands are not working. I've tried to remove some files but I'm not sure what's ok to delete. Any advice how to proceed what be welcomed.

---

### Post by rsteinmetz70112 on 2021-05-19
Can you get to a terminal window?
If so run $ lsblk
That will list  your partitions and mount points. Post the output.

Usually something like this indicates the root partition is full, that usually means /tmp  or /var are full, although /home could also fill up with pictures from your cameras if they are being stored. 
Alternately you can try to boot into a live session using a USB stick or DVD and work from there.

---

### Post by GhX6GZMB on 2021-05-19
Sound like it's partitioned as just a / partition. Deadly for this kind of application.
Get a new friend. (just joking).

Opening a terminal window is done using Ctrl-Alt-T

---

### Post by yancek on 2021-05-19
Which security software are you using?  This kind of software will save images to a specific folder and image files can be large.  Is it set up as motion detect?  Is it set up to delete images after a specific time period?

---

### Post by ActionParsnip on 2021-05-20
Eugh webmin.

What is the output of:
```

lsb_release -a; uname -a; df -h; echo; df -i

```

Thanks

---

