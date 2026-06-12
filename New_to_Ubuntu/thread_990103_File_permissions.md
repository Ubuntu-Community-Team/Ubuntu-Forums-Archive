---
title: "File permissions?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Guyon on 2008-11-22
When switching to 8.10 somehow my username got really messed up, so I decided to reinstall ubuntu. I have the iso saved on my hd but it's in the username that is messed up. I used terminal to move it into my directory, but it has a picture of a lock on the top right and an 'X' on the bottom right. I can't write it to a cd as of now because
"The file '/home/ellie/Public/ubuntu-8.10-desktop-i386.iso' is not a valid disc image."
I md5sum'd it and it matches.

---

### Post by taurus on 2008-11-22
Who owns the file?

```
ls -la /home/ellie/Public/ubuntu-8.10-desktop-i386.iso
```
You can change the ownership back to you, ellie, with

```
sudo chown allie:allie /home/ellie/Public/ubuntu-8.10-desktop-i386.iso
chmod 644 ~/Public/ubuntu-8.10-desktop-i386.iso
ls -la ~/Public/ubuntu-8.10-desktop-i386.iso
```

---

### Post by Guyon on 2008-11-22
> **taurus said:**
> Who owns the file?

```
ls -la /home/ellie/Public/ubuntu-8.10-desktop-i386.iso
```
You can change the ownership back to you, ellie, with

```
sudo chown allie:allie /home/ellie/Public/ubuntu-8.10-desktop-i386.iso
chmod 644 ~/Public/ubuntu-8.10-desktop-i386.iso
ls -la ~/Public/ubuntu-8.10-desktop-i386.iso
```

Thanks buddy, it worked. :)

---

### Post by jenkinbr on 2008-11-22
> **Guyon said:**
> Thanks buddy, it worked. :)
Please mark this as solved.

At the top of the page, click thread tools, and then click 'mark thread as solved'.

Have a great day!

---

