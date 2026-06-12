---
title: "Moving some / directories to a new hard drive"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by lilFunc on 2013-05-18
Hello.

I am using a small humble 32GB SSD. I only want it used for the booting of and some essential needs of the OS.

I have my /home on a different hard drive, and my / is on the SSD.

I just noticed I should have put /usr /opt and /etc on my third hard drive so that there isn't a chance of it running out of space...

I am a complete beginner without a GUI..so if someone could please hold my hand and help me through getting these moved to my third hard drive (which isn't mounted or partitioned yet) that would be totally awesome!

Thank you so much,
Jake

---

### Post by Irihapeti on 2013-05-18
I would think that 32GB is plenty big enough for the system, given that you've already got the /home directory elsewhere. That is, unless you're going to be installing an insane number of packages.

In my experience with restricted space for the system (4GB on an EeePC900), the main thing I have to watch for is a buildup of packages downloaded during system updates.

They are easy enough to remove periodically by entering the command

```
sudo apt-get clean
```

You can easily check the amount of space with the command
```
df -h
```

---

### Post by lilFunc on 2013-05-18
Oh, okay. I see that Ubuntu is much smaller than Windows (just switched today)..uh. Alright. Thanks! I see I have about 23GB left.

---

### Post by Irihapeti on 2013-05-18
You're welcome.

And welcome to the forums, by the way.

---

### Post by Paqman on 2013-05-18
+1 for cleaning out old packages. Old kernels and headers can chew up a lot of space too.

[Bleachbit]("apt:bleachbit") is quite a good tool for clearing out crud in a pretty safe, reliable way.

---

