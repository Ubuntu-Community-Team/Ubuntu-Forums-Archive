---
title: "iso mount help quick!!!!!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by coolman121 on 2008-07-04
i wanted to "install" ***iso mount*** any version but from my newbish ways can not fdor the life of me find a way how to make it work on ubuntu hardy heron......... any suggestions ive tried sh, sudo, mount, dappen 777, even changing install.sh script (lines 1011-1034) ect..... all with out any results

---

### Post by 0x29a on 2008-07-04
Hi ya! Is your goal just to be able to mount an ISO under ubuntu? I suspect if you've been digging around in and .sh file you've already tried:
```

# mount -t iso9660 -o loop /path/to/image /mnt/mount_point

```

And this won't work? Sorry if you've gone down this road already. Just now installing 8.04.1 for the first time. This has worked for me on every distro I've ever used, including 7.04 and down, and many different SuSe versions.

Let me know.

Andrew

---

### Post by ramjet_1953 on 2008-07-04
Just install [COLOR="Blue"]gmountiso[/COLOR]

[COLOR="Red"]sudo apt-get install gmountiso
[/COLOR]

It has a nice GUI and is very intuitive.

Regards,
Roger :cool:

---

### Post by saratchandra on 2008-07-04
Try [this]("http://getdeb.net/app/AcetoneISO")

---

### Post by coolman121 on 2008-07-05
i dont want to use gmountiso or acetoneiso they both do not support dvxbxd (xbox code) whcih i would like to us ein the future besides isomount looks awesome compared....

---

### Post by coolman121 on 2008-07-05
hey does gmountiso support creation of iso images????? cause if uit does ill try it

---

### Post by coolman121 on 2008-07-05
thank you so much acetone iso is great even for conversion!!!!

---

