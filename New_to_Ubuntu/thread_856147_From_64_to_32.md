---
title: "From 64 to 32 ?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by natman on 2008-07-11
I currently have a 64 bit kubuntu working, things for the most part are fine, bar flash in firefox ( works but every so often doesnt ) and other times i see a .deb for 32 but nothing for 64, generally im always having to ask " and will it work under 64 bit?" and im kinda sick of it by now. My question is, can i move from 64 back to 32 without hassel or is it best to do a reinstall. I have a seperate home partition, but will there be program files that have data from 64 not very happy to work with a 32?
Any advice?

---

### Post by Elfy on 2008-07-11
From what I've read you have to reinstall. Could be wrong but don't think I am :)

---

### Post by philinux on 2008-07-11
> **natman said:**
> I currently have a 64 bit kubuntu working, things for the most part are fine, bar flash in firefox ( works but every so often doesnt ) and other times i see a .deb for 32 but nothing for 64, generally im always having to ask " and will it work under 64 bit?" and im kinda sick of it by now. My question is, can i move from 64 back to 32 without hassel or is it best to do a reinstall. I have a seperate home partition, but will there be program files that have data from 64 not very happy to work with a 32?
Any advice?

You can only go back to 32 bit by reinstalling. The config files in home are mainly text files so should be no/minor if any problems there.

---

### Post by natman on 2008-07-16
So if i reinstall Kubuntu 32, and my /home has a whole bunch of firefox,amarok,etc 64bit file whats going to happen, do i just create a new .mozilla and .amarok and start over or will everyone just play ball? Is it worth the trouble?

---

### Post by oldos2er on 2008-07-16
Why not just run the 32-bit program(s) under your 64-bit Ubuntu?

---

### Post by natman on 2008-07-16
Like i said in my top post, some things just dont work, and im getting sick of it.

---

### Post by txcrackers on 2008-07-17
Yes, you'll need to archive your /home directory and store it off-disk somewhere (burn to DVD, whatever).

I'm assuming you used the default disk-partitioning, so when you install the 32-bit, select the custom partitioning and set aside a nice chunk of your disk for /home. That way when you want to (re-)install, you won't *have* to back up your /home (you **should**, just as a precaution).

---

