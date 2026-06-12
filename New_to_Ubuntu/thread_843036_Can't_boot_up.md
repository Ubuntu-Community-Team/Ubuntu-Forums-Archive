---
title: "Can't boot up"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-27
I can't boot up Ubuntu because when I try, I get the low graphics mode pop up, and I can't do anything after that. My system just freezes if I try to do anything. I can't even get on live-cd.

I was wondering if i could go into recovery mode and use commands to try to fix this. Maybe download an old version for the grub menu, or reconfigure some files..anything?

---

### Post by buntunub on 2008-06-27
boot into safe mode and when you get to the command prompt type:

```
dpkg-reconfigure xserver-xorg
```

When your done with that, reboot, and you should be good to go.

---

### Post by adobrakic on 2008-06-27
I've tried this before, but I just tried it again. It does nothing. After I reboot, I get the pop up again. I don't understand what the problem is, Windows runs fine.

Is there maybe a windows program that works like GParted, so i can format Ubuntu? I've been trying to fix this all day and to be honest I think if I reboot my computer one more time it's going to explode.

---

### Post by st33med on 2008-06-27
Do you know your graphics card? If not, boot into safe-mode and type:
```
lspci
```
and post here.

---

### Post by adobrakic on 2008-06-27
Yes, I have a s3 Prosavage ddr. I tried manually entering it in the low graphics mode popup, but it doesn't have the exact one listed. Even if it did, when i press "OK" on the screen, nothing happens. Only "Close" works.

I'll try to post what lspci gives me, but I'll have to write it down, so it might take a little.

---

### Post by adobrakic on 2008-06-27
I get a list of things when I type that in, but what I think you're looking for specifically is:

```

1:00.0 VGA Compatible Controller: S3 Inc. [Prosavage8 KM266/KL266]

```

---

### Post by adobrakic on 2008-06-28
anddddddddddddddddddd bump

---

