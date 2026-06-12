---
title: "copy a file from win host to Xubuntu guest"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by bobby84 on 2013-05-15
i have win 7 x64 host 
Virtualbox with xubuntu vm

have installed guest additions.
i have enabled "shared clipboard"( works for text), and "drag and drop ", both "bidirectional"
In "settings""shared folders" i have "machine and transient "folders empty. 
I don t understand the "shared folders "help info.
All i want is get a file from the win host into the vm. ( place it on the desktop or into docs folder)
TIA

---

### Post by steeldriver on 2013-05-15
You need to add the folder to VirtualBox via the 'Devices --> Shared folders...' menu (or the folder icon on the bottom bar) and then add yourself to the vboxsf group in the VM. After that the folder should mount as /media/sf_*foldername*

---

### Post by pootan on 2013-05-15
Have you installed the Extension Pack from this page?

Also consider online storage like gmail, etc and using a USB drive or stick as a temporary workaround to transfer the file until you get it working. 

[URL="https://www.virtualbox.org/wiki/Downloads"]https://www.virtualbox.org/wiki/Downloads



[/URL]

---

### Post by bobby84 on 2013-05-15
Thanks for your help ,got it working now.
cheers

---

### Post by bobby84 on 2013-05-15
> **pootan said:**
> Have you installed the Extension Pack from this page?


[URL="https://www.virtualbox.org/wiki/Downloads"]


[/URL]

No, i&#314;l look into it

---

