---
title: "Creating new storage space on a second Hard Drive, permission denied to write to it?"
date: 2021-01-26
forum: New to Ubuntu
---

### Post by Swan_DB on 2021-01-26
I've gotten into "Disks" gui menu, where it appears I can edit partitions, edit file systems, others stuff, but I can't figure out why I can't just simply use GParted -> create partition -> then add a folder to that 500GB  Hard Drive (that is how simple Windows would be).  So...  do I need to explicitly set permission for my secondary drive to allow write privileges?

---

### Post by exploder on 2021-01-26
Just went through the same thing here, added another SSD to my system. I used gparted just like you but had no permissions to do anything. Root owns the drive... I simply used sudo nautilus and gave myself permissions on the drive.

---

### Post by Swan_DB on 2021-01-26
**[SOLVED]**
Literally just Right Clicked inside there (the storage location, for me it was my Other Location -> 500GB ), right click, went to properties, then permission tab, and there was "Owner" -> Me, and "Group"- > my username, and "others".

I just changed Group which was "my username" to be able to "create and delete"

> [COLOR=#000000]Root owns the drive... I simply used sudo nautilus and gave myself permissions on the drive.[/COLOR]
  How to TAG Exploder? ^^^^

Is doing sudo nautilus the same thing as what I did through the gui method?  Or did "give yourself permission" by making yourself root every time you use that storage space, as opposed to making the storage space a user level type of thing?  Or am I just not understanding and need to do more research?

edit:  I quit for today,, too tired.

---

### Post by grahammechanical on 2021-01-26
By opening the file manager (nautilus) through the terminal with the prefix sudo we use the file manager as root. Any folders or files we create or copy will be owned by root and we will have to change permissions to do more than access those folders and files when we are an ordinary user again.

Regards

---

