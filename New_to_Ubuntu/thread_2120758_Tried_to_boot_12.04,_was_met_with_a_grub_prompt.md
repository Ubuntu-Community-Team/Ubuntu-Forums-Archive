---
title: "Tried to boot 12.04, was met with a grub prompt"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by androideka31 on 2013-02-27
I installed 12.04 via wubi about a month ago, loving it, etc. I booted Windows to retrieve my files and delete the partition, and when I tried to boot back into Ubuntu, I was met with a black screen and a grub> prompt. Before I booted Windows, I had tried to download skype, and APT was having some sort of problem with i386 or something. Unfortunately, since I can't get in to root, I can't show you the problems I was having. Does anyone know what I can do to boot into Ubuntu? Having to use Windows after Ubuntu is the worst.

Thanks!!

---

### Post by Sef on 2013-02-27
Wubi is simply a file in Windows. 

> booted Windows to retrieve my files and delete the partition,

What partition did you delete?

Did you install Ubuntu on a separate partition?

---

### Post by androideka31 on 2013-02-27
Sorry, I should have been specific. I didn't delete any partitions. I think by default wubi created a partition for 12.04, right?

---

### Post by JLeon85 on 2013-02-27
I would make a live CD or USB of the Ubuntu Secure Remix, and then boot into that and run boot repair. If it turns out Ubuntu was deleted then at least you'll have an install disk at the ready. 

[https://help.ubuntu.com/community/LinuxSecureRemix?action=show&redirect=UbuntuSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix?action=show&redirect=UbuntuSecureRemix)

---

### Post by androideka31 on 2013-02-27
Thanks! I'll give that a go.

---

### Post by Impavidus on 2013-02-27
> **androideka31 said:**
> Sorry, I should have been specific. I didn't delete any partitions. I think by default wubi created a partition for 12.04, right?
No, it created a virtual partition. It won't be present on a list of partitions you can get using any disk management tool.

But if you didn't delete a partition, what then did you do?

Anyway, posting a boot info report from boot repair won't harm.

---

### Post by androideka31 on 2013-02-27
> I would make a live CD or USB of the Ubuntu Secure Remix, and then boot into that and run boot repair. If it turns out Ubuntu was deleted then at least you'll have an install disk at the ready. 

OK, ultra noob here... Could you be a little more specific? I haven't quite mastered the terminology and methodology.

---

### Post by androideka31 on 2013-02-27
> But if you didn't delete a partition, what then did you do?

I didn't do anything other than check my skype messages, browse the internet, and try to back up my Windows files, but Windows auto-updated during the night and cancelled the backup.

---

### Post by androideka31 on 2013-03-01
Update: uninstalled Ubuntu, reinstalled and decided not to mess around with skype. Thanks for the help!

---

