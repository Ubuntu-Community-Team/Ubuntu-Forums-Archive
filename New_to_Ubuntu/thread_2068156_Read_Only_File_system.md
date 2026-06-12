---
title: "Read Only File system"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by Edwardhai on 2012-10-08
Hello,

I have just re installed ubuntu 12.04 and it is read only file system.

I have used Ubuntu for a little while - my level of computer knowledge is pretty low - I do not understand a lot of the posts on this forum.

 - I realize I may have not yet given enough information for you to be able to help. I will fill in the gaps as I can, ask questions, and please, be patient with me!

thank you

Edward

---

### Post by cipherboy_loc on 2012-10-08
Can you open up a terminal? I don't quite recall how to open it on the latest 12.04 with unity (computer can't run unity), but once there, type in:

```

sudo mount

```

It will prompt you for a password (because sudo means run as an admin), and it will print some text to the screen. Copy and paste it back (Ctrl+Shift+C to copy from a terminal after highlighting, regular Ctrl+V to paste here) in code tags. This will show us which drives are currently mounted and specifically, which one is read only and is causing you problems. 

Also, paste the result of:
```

sudo fdisk -l

```

Once we determine which disk is giving you issues, we can figure out why it is giving you issues through the logs.

Thanks,
Cipherboy

---

### Post by audiomick on 2012-10-08
> **cipherboy_loc said:**
> Can you open up a terminal? I don't quite recall [COLOR="Red"]how to open it on the latest 12.04[/COLOR] with unity

Go to the dash (click on the Ubuntu logo in the top left corner) and type "terminal" in the search box. An icon should appear below the search box. Click on that.

---

