---
title: "[SOLVED] Moving /home?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-04-30
I currently have a single HDD on my 7.10 machine with the entire file system there.  I want to add a 2nd HDD to it and mount it at /home.

Since /home currently exists on the file system, I assume mounting a new drive at /home would not be "a good thing".  I also assume that I will need to mount the new disk elsewhere and copy the files from the existing /home to the new /home and then (somehow) delete or unmount the existing /home and remount the new /home.

I am a bit fuzzy on how to do this while the system is running without breaking things into little pieces.

(I feel like such an idiot...) ](*,)

---

### Post by Perpetual on 2008-04-30
[This should]("http://www.psychocats.net/ubuntu/separatehome") help you.

---

### Post by mikeyphi on 2008-04-30
In your situation I would consider saving all the personal data and installing 8.04 to two partitions, / and /home. There are considerable problems in moving your /home partition but the previous suggested guide is good.

---

### Post by H.Callahan on 2008-04-30
Actually, it seems pretty straight forward.  I hadn't thought of using the Live CD to do this, though.

---

