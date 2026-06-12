---
title: "Where are windows partitions mounted from BY DEFAULT"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by outsider-dave on 2014-02-05
Hola,

I'm trying to figure out where my windows partitions are getting mounted from by default? (in /media/<user>/)
I'd like to change some settings (owner override, etc), but I can't seem to find where they are getting mounted during boot. Not in /etc/fstab.
If I can't specify settings for it fstab style, how do I avoid mounting it so that I can mount it in fstab?

Oh, and it's ubuntu saucy.

Thanks!

---

### Post by vitz_3 on 2014-02-05
Hi there, welcome to the forums!

You can find what is currently mounted to the file system by running;
```
mount
```
You can check where your windows ntfs partitions are mounted by running;
```
mount | grep -i ntfs
```
The pipe "|" grep part simply takes the output of the mount command and searches for the string ntfs while ignoring upper or lower case.
If you don't see an ntfs partition mounted in the output then it's simply not mounted. We'll get that part sorted but first do you mind checking if you can find it with those commands?

Cheers

---

### Post by Bashing-om on 2014-02-05
outsider-dave; Hi ! My welcome to the forum .

See vitz_3's last.

As well, it is udev that rules;
see:
```

man udev

```
Then if there is an entry in the /etc/fstab file, "fstab" takes precedence.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2014-02-05
If you're running Windows 8, they are NOT mounted -- and will NOT be -- as long as Fast Startup is enabled in Win8 (which it is by default). That is a new form of Windows hibernation that keeps the partitions mounted even when you're not in Windows.

---

