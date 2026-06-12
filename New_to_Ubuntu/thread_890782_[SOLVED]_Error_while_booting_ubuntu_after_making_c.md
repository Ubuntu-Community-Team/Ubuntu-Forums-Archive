---
title: "[SOLVED] Error while booting ubuntu after making changes in drives through vista"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by SandyM on 2008-08-15
HI!!!  this is the second time I am crippled by this problem. I used to have three NTFS (vista) , one Ext3 (linux) and one swap(Linux) drive and due to some reasons I created three more NTFS drives through Arconis disk director 10 in Vista. This did'nt created any problem for me. 
The problem started when I merged two drives in vista to retain 4 NTFS drives.
I didn't do anything with Linux Drives but later when I restarted my PC to load Linux I started receiving error messages and any click redirect me to grub menu.

PLEASE HELP.

---

### Post by wolfen69 on 2008-08-15
> I didn't do anything with Linux Drives but later when I restarted my PC to load Linux I started receiving error messages and any click redirect me to grub menu.could you be more specific as to what is wrong?

---

### Post by Too Late on 2008-08-15
What error messages is grub giving? It seems that grub is setting a wrong partition as the root partition.

You can try to boot by selecting the correct menu entry with arrow keys, and then press 'e' key (not enter). Find the line where it reads eg. "root (hd7,7)" (or whatever numbers) and try to change that last number, which is probably wrong. If that works (you can boot), you have to edit the /boot/grub/menu.lst file so that you don't have to edit that thing every time you boot.

---

### Post by MarkieB on 2008-08-15
no longer participating in ubuntuforums.org

---

### Post by SandyM on 2008-08-15
> **Too Late said:**
> What error messages is grub giving? It seems that grub is setting a wrong partition as the root partition.

You can try to boot by selecting the correct menu entry with arrow keys, and then press 'e' key (not enter). Find the line where it reads eg. "root (hd7,7)" (or whatever numbers) and try to change that last number, which is probably wrong. If that works (you can boot), you have to edit the /boot/grub/menu.lst file so that you don't have to edit that thing every time you boot.
U are right I was able to boot by changing the number of my hard disk but I was unable to edit grub file as saving any changes need root priviledges which I don't have. 
Please tell me how to save changes

---

### Post by Paqman on 2008-08-15
> **SandyM said:**
> 
Please tell me how to save changes

Just open the file using sudo (if you're using a CLI text editor like Nano) or gksu (if you're using a graphical text editor like Gedit). It'll prompt for a password after which you'll have root privileges while you're in that file.

---

### Post by SandyM on 2008-08-15
> **Paqman said:**
> Just open the file using sudo (if you're using a CLI text editor like Nano) or gksu (if you're using a graphical text editor like Gedit). It'll prompt for a password after which you'll have root privileges while you're in that file.
This is not working for me as I tried terminal as well as alt+f2.

---

### Post by Too Late on 2008-08-15
It should work, if you're using Ubuntu. So, in terminal, type:
```
gksu gedit /boot/grub/menu.lst
```
or
```
gksudo gedit /boot/grub/menu.lst
```
(does the same thing)

---

