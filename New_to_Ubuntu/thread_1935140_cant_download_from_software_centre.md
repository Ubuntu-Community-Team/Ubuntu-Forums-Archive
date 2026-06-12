---
title: "cant download from software centre"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by albert s on 2012-03-03
have had a search and dont really see anything the same, so hope you kind folks can help me,
I cant download anything from the software centre,
tries to start then I get an error saying I have no internet connection,
Im using Ubuntu 11.10 64bit and Firefox 10.0.2,
I have run 
```
sudo apt-get update
```
I get a load of stuff back but I think this is the bit you folks will need, it comes at the very end
```
Fetched 468 B in 0s (469 B/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://gb.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```
hope someone can help me ,
thanks, Albert.

---

### Post by Cheesehead on 2012-03-03
> **albert s said:**
> then I get an error saying I have no internet connection

Please tell us the complete and exact error message you are receiving.

---

### Post by albert s on 2012-03-03
Failed to download package files
Check your internet connection

it pops up in a box in the middle of the screen.

---

### Post by pootan on 2012-03-03
I've been getting those same errors today on and off for the first time in a few years, for what it's worth. Retrying it a few times allows me to download.

---

### Post by albert s on 2012-03-03
Ive been getting this since getting this 'new' computer and loading 64bit on it, my older PC running 34bit LTS is fine,
Ive never been able to download anything from the software centre on this PC,
about 3months now.

---

### Post by oldos2er on 2012-03-03
Try [http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13](http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13)

---

### Post by albert s on 2012-03-04
@ oldos2er

website currently offline

:confused:

---

### Post by lechien73 on 2012-03-04
Hmmm...it sounds like corrupted list files. I solved this problem on a friend's computer by doing the following:

```
sudo apt-get clean 
sudo rm -r /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial 
sudo apt-get clean
sudo apt-get update
```

---

### Post by albert s on 2012-03-04
what does that do [lechien73]("http://ubuntuforums.org/member.php?u=1031904") ?
Im always worried when someone posts code with ** rm ** as part of it.

---

### Post by albert s on 2012-03-04
5 [SIZE=4]*********[/SIZE] to lechien73 :KS:KS:KS:KS:KS
that worked perfectly,
thanks a lot,  :D

---

### Post by lechien73 on 2012-03-04
Great stuff :)

All the **rm** command does is remove the corrupted lists files. You then recreate the directory tree and create the lists and lists/partial directories.

apt-get then recreates the list files.

Glad it worked - I really should explain commands a bit more!

---

### Post by albert s on 2012-03-04
no worries lechien73, 
I did a bit of digging and searching and figured out it was safe,
I dont know a great deal , but I do know some commands with** rm** can be very dangerous,
and end up with a very empty HDD if I get it wrong.
again, thanks very much, if I could Id buy you a pint of the black stuff.  :D
BTW, Im originally from Co Antrim.  :D and I much prefer HARP,  :o

---

### Post by jerwilkins on 2012-03-20
Thanks lechien73! Worked like a charm!

---

