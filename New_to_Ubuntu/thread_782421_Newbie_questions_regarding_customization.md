---
title: "Newbie questions regarding customization"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by futureal2032 on 2008-05-04
Hi,
i am a Ubuntu Novice. currently i am very good at installing ubuntu on various systems and installing apps on ubuntu.

the problem is i want to remove some installed applications and customize my ubuntu installation so i only have apps that i require and frequently use. and some useful tools. so i want to remove the extra stuff. i tried doing it from add/remove applications. but it gives me many error messages. and i am afraid of accidently removing library files or dependencies. also i am not sure how it will affect other apps.

**so is there a way by which i can remove applications i dont want and still make sure that i have all the necessary things working fine?**

---

### Post by DrPppr242 on 2008-05-04
I'm pretty sure you can open a terminal and use 'sudo apt-get remove [package-name]' to remove unwanted applications.

---

### Post by agim on 2008-05-04
I am writing this from my first customized version of Ubuntu! At least the first one that works well. If you want to remove programs and add others to the .iso image, this is the page I followed.

Make sure you type everything correctly, otherwise you'll get to the end of it and have a "file not found" error, or something similar.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by sam_delta on 2008-05-04
removing programs from add/remove is fine, (as far as i know, unlike synaptic, add/remove only shows programs installed, no libs/dependencies)
theres an option in add/remove that will only display all installed apps,

just dont mess into removing packages from synaptic, as synaptic contains more specific things such as libs and dependencies so it is easier to mess things up with synaptic

sam

---

