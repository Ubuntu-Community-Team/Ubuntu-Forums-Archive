---
title: "How to open password protected folders on a raid using terminal"
date: 2015-08-23
forum: New to Ubuntu
---

### Post by blake12 on 2015-08-23
Hi all i have Ubuntu 15.04 Desktop which i used to recover my raid from an old Thecus NAS i had that failed. I successfully recovered the raid however there are some folders that i had password protected for a certain username and password to access. I am having a few issues trying to navigate with terminal to the directory to try and remove the username/password. Can anyone give me some pointers on how to remove the username/password or if i cannot remove it just login so i can copy the contents onto another hard drive to reformat the raid configuration on a new machine?

Thanks in advance.

Cheers
Blake

---

### Post by blake12 on 2015-08-23
Just on this i can get the directory of the Array i am trying to get to which is /media/blake/c41210ef-c90a-40ae-894b-69026db9dbbd and the device is /dev/mapper/vg0-lv0
when i try and change to the directory using 'cd' it says it cannot be found?

Now i did find out how to do it graphically with [COLOR=#000000][FONT=Ubuntu Mono]gksu nautilus[/FONT][/COLOR] which is great as it gave me access to the folders but the folders inside those folders have to be changed also which will make it extremely time consuming. Is there any easier way to change the folder and all the subsequent subfolders permissions?

---

