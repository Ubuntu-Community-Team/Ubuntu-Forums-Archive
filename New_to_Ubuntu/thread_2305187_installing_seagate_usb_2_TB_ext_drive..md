---
title: "installing seagate usb 2 TB ext drive."
date: 2015-12-03
forum: New to Ubuntu
---

### Post by netranger77jb on 2015-12-03
Hello newbie 

I have a Seagate 2 TB ext USB Drive how do I get Ubuntu to recognize it ?

Thanks

Jim

---

### Post by sudodus on 2015-12-03
Welcome to the Ubuntu Forums :-)

Normally Ubuntu recognizes external drives via USB.

- Is the drive brand new, or are there already files on the drive?

- What is the brand name and model of the drive?

I suggest the you run the ***following commands from a terminal window*** with the drive connected and 'powered on' and copy/paste the result to a reply here. Put the output text within code tags:

[noparse]```

line 1
line 2
...

```[/noparse]

to make it easier to read.

```

df

lsusb

sudo lsblk -fm

sudo parted -ls

```

---

