---
title: "Can't Extract.... Anything, No Sound either"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by generalandrew on 2008-08-08
Well I could really care less about my sound problem right now, but I am having MAJOR issues extracting files.

I've tried to run various things over the past forty eight hours, with just about all of them resulting in this....

```

root@Andrews-Linux-desktop:~# tar xvfz xampp-linux-1.6.7.tar.gz -C /opt
tar: xampp-linux-1.6.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@Andrews-Linux-desktop:~# 


```

The above example was pulled from my attempt to extract the XAMMP package to the opt folder. So I tried to extract them without the console, and I can't even drag and drop it in there either!! Gives me an error, saying that there was an error extracting the files.

How ever, this isn't localized to just the XAMMP files. I've tried to run/extract a .run nVidia driver package with the same error as quoted above.

OH, by the way, this is a fresh install of the latest Ubuntu (8.4) on an AMD platform, though I chose the x86 variant.

Thank you, and any help is greatly appreciated!

---

### Post by philinux on 2008-08-08
You might need to use 

sudo tar

Since in a normal install /opt is owned by root.

---

### Post by dje on 2008-08-08
are you in the same directory where the files are located?
```
cd /path/to/dir/with/files
```

dje

---

### Post by markjensen on 2008-08-08
First, you don't 'extract' the nVidia .run file.  You just run it with a "sh", if I recall correctly.

I would guess that it cannot find the file, based on the first message.  Did you use tab auto-completion to let it fill in the file name for you?  (that would ensure that Linux sees the file where you think it is looking).  Alternatively, use a full path specification for the file, /path/to/filename.tgz

Hope that helps.

---

### Post by generalandrew on 2008-08-08
Wow, thank you all for your quick responses!

As to the first reply, I did try it with sudo in front, however I still receive the same message.

As for the other replies: all of the downloads I do are saved to my Desktop space, so I'm not exactly sure if that's the default location or not. I've yet to try running the command while including the directory information, so I'll try that.

Edit: apparently including the directory information is something rather important and shouldn't be left out lol : ). Coming over from a life time of Windows, minus DOS, the console is kind of daunting to me.

Thank you everyone for your help!

---

### Post by markjensen on 2008-08-08
Well, if you downloaded something as your user, and it appears you have a different account for root set up (instead of using sudo?), that might explain some of the problems, as they each have their own separate home, so would not share the same desktop.

(and please don't say you were downloading that file *as* the root user)

---

### Post by generalandrew on 2008-08-08
Lol, no, I wasn't root user when I downloaded those items.

---

