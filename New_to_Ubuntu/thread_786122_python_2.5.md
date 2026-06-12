---
title: "python 2.5"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by AOZ on 2008-05-07
So the udpate manager ran automatically and saw that i needed a few updates. all of the updates except python2.5 and python2.5 minimal installed flawlessly.for some reason it cant find the packages for pythton 2.5. this is the error i receive:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.2-2ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.2-2ubuntu5_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-2ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-2ubuntu5_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]

could this have somethign to do with python 2.5 not beign compatible with the x86-64 ubuntu? (which i use). any help on this would be greatly appreciated as im eager to start learning and using python (any help on where to start that would also be greatly appreciated :)

Thanks in advance!

---

### Post by aheckler on 2008-05-07
The update worked for me and I'm on 64-bit. It looks like the servers went down for a second when you were updating maybe.

Try "sudo apt-get update && sudo apt-get upgrade" and see what that does.

---

### Post by ablinkin on 2008-05-07
have you tried to manually download the packages and install them?

---

### Post by AOZ on 2008-05-07
thanks aheckler that code did it

---

