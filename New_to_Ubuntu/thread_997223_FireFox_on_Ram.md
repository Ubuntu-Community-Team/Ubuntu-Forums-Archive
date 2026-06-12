---
title: "FireFox on Ram"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Oliver.BS on 2008-11-29
How do I get Firefox to run on Ram ?

---

### Post by damis648 on 2008-11-29
What exactly do you mean? Do you want Firefox to load into RAM from a CD or something and run it from there without a storage medium?

---

### Post by Oliver.BS on 2008-11-29
I want Firefox to run using ram instead of my HDD I just want to see if it works quicker than people say.

---

### Post by damis648 on 2008-11-29
If this is just to see if it is faster, let me tell you now: it is. Alot faster. As far as options go if you wanted to try it would be:
You could download and boot up Puppy Linux. This distro runs entirely from RAM, and you could use Firefox there. As far as your own installation, you would have to mount the ramdisk as / somehow... I think there's a kernel option you need to for that too, you would have to compile it yourself. This would have to be done because just Firefox cannot stay in RAM. I suppose maybe you could move the binaries to the ramdisk and use symlinks to get there... kinda a rough solution though. Here is a gentoo guide: [http://forums.gentoo.org/viewtopic-t-296892-highlight-ramdisk+copy.html](http://forums.gentoo.org/viewtopic-t-296892-highlight-ramdisk+copy.html) , though for Ubuntu probably not very applicable. If anyone wants to try it would be interesting.

---

### Post by Oliver.BS on 2008-11-29
The very reason why I thought I would ask.I think I will let it run from my HDD its not slow I just like to play around with stuff.

I am still upset I carnt over clock my Dell :(

---

### Post by binbash on 2008-11-29
Gentoo howto is old + gentoo's structure is a lot different than ubuntu.I am also looking for a guide for ubuntu.

---

### Post by damis648 on 2008-11-29
> **binbash said:**
> Gentoo howto is old + gentoo's structure is a lot different than ubuntu.I am also looking for a guide for ubuntu.

Of course, as I said not very applicable. But, I might be a starting point for anyone that wants to undertake this.

---

### Post by snowpine on 2008-11-29
One tweak you can experiment with is mounting your /tmp folder to ram instead of to the HD. I notice an improvement on my eee pc with sites like Youtube.

Type this command:
```
gksu gedit /etc/fstab
```

Then add the following lines to the bottom of the file:
```
tmpfs     /var/log       tmpfs     defaults,noatime        0 0
tmpfs     /tmp           tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp       tmpfs     defaults,noatime        0 0
```

Save the file and reboot.

Let me know if that works for you!

---

### Post by binbash on 2008-11-29
i know tmpfs, i tried it a couple of years ago on gentoo.But without running firefox's libs at ram, it is not very useful.

---

