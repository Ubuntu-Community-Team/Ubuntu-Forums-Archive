---
title: "can U attach a command to a folder?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by tropdoug on 2008-08-26
Is it possible to attach a launch command to a folder? 

what I have is an nfs share mounted in /mnt/share  I have a launcher on the desktop to mount the share (I do not want an auto mount) 

I have a folder  ~/Desktop/Share symbolically linked to /mnt/share

What I would like (cos it's for my partner) is for her to be able to double click the folder and 
a) the share will mount 
b) Nautilus will open the share so that all she sees is the opened folder containing the files she can share. 

Alternatively if this could be done by adding an item to the Places menu that would do it too. 

Thanks in advance

---

### Post by Too Late on 2008-08-26
> **tropdoug said:**
> b) Nautilus will open the share so that all she sees is the opened folder containing the files she can share. 

```
nautilus file:///mnt/share
```

---

### Post by Dougie187 on 2008-08-26
I don't know if his answer was clear or not. But if you put that command into your launcher already made, but after the share is mounted. Then it will mount the share, and then open nautilus with the path that you were looking for. You can also change the icon of the launcher to be a folder if you want, and name it the folder name. That way it will be transparent to your partner (thought it might take a second longer to open then a normal folder).

---

### Post by tropdoug on 2008-08-26
this is the launcher command

gksudo "mount 10.1.1.5:/mnt/share /mnt/lapshare"

that opens the dialogue to put the passwrod into and then mounts the share.

putting your command on the end as:-

gksudo "mount 10.1.1.5:/mnt/share /mnt/lapshare" nautilus file:///mnt/lapshare[FONT=monospace]

doesn't seem to do anything I think that I must be mssing something? 


[/FONT]

---

### Post by Too Late on 2008-08-26
Generally, you must separate multiple commands with a command separator. Usually, it's a "&&" (without quotes). A semicolon might also work. However, I don't know how these would work in a desktop launcher. I hope they will work. So, it should look something like this:
```
gksudo "mount 10.1.1.5:/mnt/share /mnt/lapshare" && nautilus file:///mnt/lapshare
```

---

### Post by tropdoug on 2008-08-26
getting nearer :-) 

the command works from the terminal, but from the desktop launcher it briefly flashes the GUI and then nothing. Interestingly from the terminal no GUI comes up for the password but nautilus opens and I can access all the files.?

---

