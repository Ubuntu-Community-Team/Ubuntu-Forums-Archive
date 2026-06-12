---
title: "chmod'd /usr and nothing is working"
date: 2015-12-17
forum: New to Ubuntu
---

### Post by malaka2 on 2015-12-17
Hi,

I am new to ubuntu and I have accidentally changed permission of /usr recursively by **sudo chmod 777 -R /usr**. And now nothing works...please help

Thanks

---

### Post by newbie-user on 2015-12-17
I'd recommend reinstalling Ubuntu. Otherwise, looking at my machine, a lot of the stuff in /usr has 755 permissions.

---

### Post by QIII on 2015-12-17
I am generally loathe to recommend reinstalling -- I call that blasting off and nuking 'em from orbit.

Yours is one of the very few times I do think that nuking is the best, or perhaps only, choice.

So I also recommend a reinstall.

But first: did you create a separate /home partition?

---

### Post by malaka2 on 2015-12-17
Thanks, The thing is I haven't  created a separate home partition.....

---

### Post by sandyd on 2015-12-17
We can still recover the files on your system even though it is not bootable.

Do you have somewhere (i.e. usb/external hard drive/etc) to place the files in your home folder?

If so, you can access your home folder via a livedvd/usb and copy the files before reinstalling.

---

### Post by malaka2 on 2015-12-17
Thank you so much.....

---

### Post by HermanAB on 2015-12-18
Re-installing is quicker than fixing that.  Otherwise, you could make a virtual machine on another machine using the same version of Linux, then copy the whole /usr over from there with scp - that amounts to even more work though.

---

