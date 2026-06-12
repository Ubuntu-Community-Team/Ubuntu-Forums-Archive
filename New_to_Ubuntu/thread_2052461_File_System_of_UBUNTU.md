---
title: "File System of UBUNTU"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by nachinew on 2012-09-03
Hi,

New to UBUNTU.

Please describe simple way how was the UBUNTU File System...

:D

---

### Post by MG&amp;TL on 2012-09-03
Ubuntu mostly uses the Filesystem Hierarchy Standard: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

Btw, "Ubuntu", not "UBUNTU". :)

---

### Post by nachinew on 2012-09-03
Thanks for your description.;)

---

### Post by Paqman on 2012-09-03
Do you want to know about how the system is structured (ie: what the various folders are) or do you want to know about the actual filesystem on the disk?

---

### Post by nachinew on 2012-09-03
> **Paqman said:**
> Do you want to know about how the system is structured (ie: what the various folders are) or do you want to know about the actual filesystem on the disk?

Both man ---- In simple way:p

---

### Post by Paqman on 2012-09-03
Ok, Ubuntu's default filesystem is called ext4. There are other filesystems you can use to format your drive if you want, but ext4 is a good default choice.

As for the structure of the actual Ubuntu system the basics you need to know are:

/home: where all your data and config settings are stored
/media: where removable devices like USB sticks automatically show up

Everything else is used by the system itself. You can browse it, but you can't make any changes without entering your password. This is so you don't accidentally mess up anything important.

---

### Post by nachinew on 2012-09-03
> **Paqman said:**
> Ok, Ubuntu's default filesystem is called ext4. There are other filesystems you can use to format your drive if you want, but ext4 is a good default choice.

As for the structure of the actual Ubuntu system the basics you need to know are:

/home: where all your data and config settings are stored
/media: where removable devices like USB sticks automatically show up

Everything else is used by the system itself. You can browse it, but you can't make any changes without entering your password. This is so you don't accidentally mess up anything important.

Ok Great, Proceed then...:KS

---

### Post by Lars Noodén on 2012-09-03
You can get an overview of which files go where by looking at [hier](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html).

---

### Post by nachinew on 2012-09-03
> **Lars Noodén said:**
> You can get an overview of which files go where by looking at [hier]("http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html").

Thanks man.

---

