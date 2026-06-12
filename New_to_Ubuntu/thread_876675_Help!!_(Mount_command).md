---
title: "Help!! (Mount command)"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by CC_Joe on 2008-08-01
Ok, so I did something dumb.

I was trying to mount a iso to a virtual drive. I couldn't find any programs to do it for me (alcohol 120 and daemon don't work with wine), but I saw a command that might work. So I used it without really knowing how it works... doh.

I typed ```
sudo mount -t iso9660 "Joy of Painting Season 2.iso" /home/joe -o loop
```

It didn't work how I envisioned.... it's doing something to my home directory. All of my folders in the directory are still there, but none of the content (In nautilus). And I'm getting periodic notifications from gnome about some sort of I/O operation involving the names of some of my documents.

And check this out:

```
joe@Snow-Crash:~$ ls
audio_ts  video_ts
```

That can't be good.


I'm reading man umount, but I can't figure out the right command to stop this thing. HELP!

Should I just restart my computer? Will I lose my data?

---

### Post by CC_Joe on 2008-08-01
I dont' think my data is gone... I had a movie open that's sitting in my home directory, and I can still play more of it. Phew.

So, anyone know how to stop a runaway mount operation?

---

### Post by InfinityCircuit on 2008-08-01
You should be able to just run "umount /home/joe"

---

### Post by CC_Joe on 2008-08-01
```
joe@Snow-Crash:~$ umount /home/joe
umount: /home/joe is not in the fstab (and you are not root)
joe@Snow-Crash:~$ sudo !!
sudo umount /home/joe
[sudo] password for joe: 
umount: /home/joe: device is busy
umount: /home/joe: device is busy

```

Hmm...

---

### Post by CC_Joe on 2008-08-01
I am the impatient type, and I really want to just restart my computer. Anyone think that'll kill my data?

---

### Post by roquefilipe on 2008-08-01
I don't think so. reboot should be fine. 

take a look at gmountiso to mount iso files

---

### Post by roquefilipe on 2008-08-01
sorry, double post

---

### Post by CC_Joe on 2008-08-01
Phew. data's still here. 

Thanks for the gmountiso tip, I'll look into it.

---

### Post by Bucky Ball on 2008-08-01
Have a look at the ID of the iso optical drive. It will be something like /dev/sdb or /dev/sdc1 or whatever. you then run the mount command using that, not try to mount the disk itself (although you can, I guess). Thus,

> sudo mount /dev/sdc1

... or whatever the optical drive might be called and work from there. :)

---

### Post by Bucky Ball on 2008-08-01
This thread may give you a few ideas ...

[http://ubuntuforums.org/showthread.php?t=875677](http://ubuntuforums.org/showthread.php?t=875677)

You can just run;

> sudo mount /dev/sdc1

... or whatever device name your optical drive has, and work from there. :)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

The last page is a reference; an idea to use it before running any commands or ask here. If you were to run an rm or rf, things could be dire!!! Ask away, that's what the forum's all about ... :)

---

