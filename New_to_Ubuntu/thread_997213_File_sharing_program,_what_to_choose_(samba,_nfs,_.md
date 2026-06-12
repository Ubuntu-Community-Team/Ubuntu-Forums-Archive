---
title: "File sharing program, what to choose (samba, nfs, etc ?)"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-11-29
I would like to be able to share files between computers in my local network and I was wondering what file sharing programs would be recommended. Samba looks like the big one, but I also seen NFS, there might also be other so please recommend some. :)

---

### Post by fedex1993 on 2008-11-29
If you are using only gnu/linux computers in your local network use NFS, if you using windows mac or some else i would recommend samba. I use freenas for samba and nfs its easy to setup.

---

### Post by lswb on 2008-11-29
If you have windows computers on your lan samba is the way to go, if only connecting between linux or other unix-like systems sshserver & sshfs is very flexible and simple to set up

---

### Post by Xiong Chiamiov on 2008-11-29
NFS is for Linux-to-Linux sharing, Samba for Linux-to-Windows.  Although you *can* use Samba for sharing between Linux machines, it's slower and much more of a pain to setup.

[[nfs guides]("http://delicious.com/xiong.chiamiov/nfs")]
[[samba guides]("http://delicious.com/xiong.chiamiov/samba")]

---

### Post by Roasted on 2008-12-01
I don't mean to ask a dumb question but... I just have to. I thought I read something about Vista having NFS support. Is it in some way shape or form possible for Windows machines to work with NFS, even if advanced configuring is needed?

---

