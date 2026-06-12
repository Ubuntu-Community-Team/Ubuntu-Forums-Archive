---
title: "mounting usb drive"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by paknott34 on 2008-07-26
Hello all,

New to Ubuntu and I think its Great!  It worked fine for me the first day but now I cannot access my music / etc. that is on my portable drive - it says cannot mount... any ideas?

---

### Post by wishyjr on 2008-07-26
at a guess it could be a permissions thing, try typing this in a terminal:

```
sudo mount -a
```

while the drive is plugged into your computer, see if that does anything.

---

### Post by bumanie on 2008-07-26
An exact error message would be handy. If you have happened to have had it in a windows computer and not 'safely removed' correctly, ubuntu sees the device as still in use and won't mount it. If this is the case, plug it back into windows and remove it correctly; If that's not the case - cut and paste the error message and post it on the forum.

---

### Post by richg on 2008-07-26
Hi All

I have a file in the Trash that I cannot delete. I think it has something to do with permissions. I get an error message when I try to empty the Trash. I am beginning to think it has been caused by saving my files as Root when I ran a different OS. I just transfered all my files from a backup external hard drive when I started running Ubuntu 8.04. I have not found a simple fix for this issue yet.
Any thoughts? Thanks.

Rich

---

### Post by bumanie on 2008-07-26
> **richg said:**
> Hi All

I have a file in the Trash that I cannot delete. I think it has something to do with permissions. I get an error message when I try to empty the Trash. I am beginning to think it has been caused by saving my files as Root when I ran a different OS. I just transfered all my files from a backup external hard drive when I started running Ubuntu 8.04. I have not found a simple fix for this issue yet.
Any thoughts? Thanks.

Rich

You should have made a separate thread as your issue and the original poster's problem are in no way related. If you make a new thread, someone will try and help - your premise, by the way could be correct.

---

### Post by TBOL3 on 2008-07-26
I'm guessing you like GUIs?  Well, then first, take the item out of the trash, and put it in, say the home folder.  Then, press F2, and type in gksudo nautilus.  Go to /home/[your user name].  Select your file, and press Shift+Delete.  Hit yes, and it should be gone.

BTW, I think that there is a faster way to do it, but I don't know, sorry.

Edit:  I'm sorry, would you like me to remove my writing?

---

### Post by richg on 2008-07-26
> **richg said:**
> Hi All

I have a file in the Trash that I cannot delete. I think it has something to do with permissions. I get an error message when I try to empty the Trash. I am beginning to think it has been caused by saving my files as Root when I ran a different OS. I just transfered all my files from a backup external hard drive when I started running Ubuntu 8.04. I have not found a simple fix for this issue yet.
Any thoughts? Thanks.

Rich

Sorry for this post. I had two browsers open for Ubuntu forums and I put the question in the wrong browser.

Rich

---

