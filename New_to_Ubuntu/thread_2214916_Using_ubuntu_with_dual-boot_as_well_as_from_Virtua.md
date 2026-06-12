---
title: "Using ubuntu with dual-boot as well as from Virtualbox"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by gopal4 on 2014-04-03
Hi!
I have already installed Ubuntu with dual boot with Windows 7 but I also want to use from VirtualBox from Windows 7 OS. BUT the main thing is I want both the Ubuntu installations - the one with separate boot and the other from VirtualBox to share common files i.e. I can access files of Ubuntu with dual boot from Ubuntu of VirtualBox and vice versa. Is it possible?

---

### Post by Double.J on 2014-04-03
Hi there!

Yup, it can be done. Virtual box allows shared folders between the windows host and the virtual guest.

your issue will be that windows doesn't like ext4. Writing to it is a no go.

best plan as I see it is using a shared NTFS partition for your data so that ubuntu install can use it, windows install can use it and ubuntu guest can access it through windows host.

Is that the kind of answer you're looking for?

jj

---

### Post by gopal4 on 2014-04-18
Thanks jj! That's one possible solution.

---

