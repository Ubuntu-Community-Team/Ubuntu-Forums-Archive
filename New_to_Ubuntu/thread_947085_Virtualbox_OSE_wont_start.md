---
title: "Virtualbox OSE wont start"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-10-13
I just installed VBox OSE but when I run it i get the a critical error msg.. se attchment

I had Vbox running but want to get the OSE version running..

Anyone got any ideas..

---

### Post by dash86no on 2008-10-14
Hey,

Have you installed the appropriate kernel modules using synaptic? The problems I have had with virtual box were always due to two things:

1: Didn't have the appropriate kernel modules installed for my kernel
2: Didn't add myself to vboxusers: (usermod -G vboxusers -a youruser)

One thing i try is to start virtualbox as root and if it works then you know it's some kind of permissions problem you need to solve. 


the following may help you:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

---

### Post by Ducatiboy Stu on 2008-10-14
Did all that..still get the same error...

---

### Post by Gazneth on 2008-10-14
Looking at the error, it looks like you installed a version 1.3 over top of version 1.2  . Did you install this through a .deb file download? If you did you can look in the .deb and manually delete all references to the older install. I would probably do the same with the newer install also. Then I would recommend enabling the repository so it can be installed through Synaptic or even apt-get. Directions for this are on the website for virtual ox. Installing the program this way allows the package manager to handle all the details when a new version comes out.

---

### Post by Ducatiboy Stu on 2008-10-14
> **Gazneth said:**
> Looking at the error, it looks like you installed a version 1.3 over top of version 1.2  . Did you install this through a .deb file download? If you did you can look in the .deb and manually delete all references to the older install. I would probably do the same with the newer install also. Then I would recommend enabling the repository so it can be installed through Synaptic or even apt-get. Directions for this are on the website for virtual ox. Installing the program this way allows the package manager to handle all the details when a new version comes out.

I installed it thru ADD/Remove programs..

I could not find the .deb pkg on the VBOX site, only the .tar


I basically am wanting to create a shared folder so that i can transfer files between Linux and Win thru VBOX. Win being the guest..

---

### Post by biji on 2008-10-14
hi... i'm using virtual box personal edition.. maybe just the same way with ose version 
to rebuild kernel module just type:
/etc/init.d/vboxdrv setup

before that you shhould install kernel-headers

---

