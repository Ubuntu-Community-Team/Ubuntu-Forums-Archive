---
title: "Crypt required"
date: 2018-02-27
forum: New to Ubuntu
---

### Post by Phil Binner on 2018-02-27
Hi
I have been using TrueCrypt on both Windows and Ubuntu (some time ago), but now it is not supposed to be secure.  It does not even seem to be available on XUbuntu any more.  I have searched for a different Crypt, but without luck, possibly because the word Crypt always seems to bring up other security offerings. A bit like looking for plumbing fittings online and being offered porn.

Can anyone suggest crypt software that will support maintaining a Crypt on a network drive.

---

### Post by ubname on 2018-02-27
Don't know about the network drive but veracrypt is maintained version:

[https://www.veracrypt.fr/en/Home.html](https://www.veracrypt.fr/en/Home.html)

---

### Post by Phil Binner on 2018-02-27
I tried veracrypt already.  It's not recognised in the software install program. I tried your download and unzipped it to downloads.  When I try to open any of the files I get the error "invalid byte sequence in conversion input".

Perhaps I need to add another repository to software and updates.  If so, how is that done.

---

### Post by deadflowr on 2018-02-27
> Perhaps I need to add another repository to software and updates. If so, how is that done.
Yes
here:[https://launchpad.net/~unit193/+archive/ubuntu/encryption]("https://launchpad.net/~unit193/+archive/ubuntu/encryption")
It gives you the exact instructions on how to add the repo.
After you add the repo, following the instructions, veracrypt will either show in the Software center(maybe?) or you can just run
```
sudo apt install veracrypt
```

---

### Post by Phil Binner on 2018-03-05
That did it. Thank you.

---

### Post by Phil Binner on 2018-03-05
Just one more thing.  I've never worked out how to change the thread title to "solved".

---

### Post by oldos2er on 2018-03-05
Under Thread Tools at the top of the page, click the drop-down menu, 'Mark this thread as Solved.' Thanks!

---

