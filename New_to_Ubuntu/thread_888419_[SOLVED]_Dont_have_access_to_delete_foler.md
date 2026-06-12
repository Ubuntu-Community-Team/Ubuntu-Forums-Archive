---
title: "[SOLVED] Dont have access to delete foler"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Pioneer5000 on 2008-08-13
I dragged a folder from a disc onto my desktop. Now that i want to delete the folder and the files inside it, it wont allow me and it wont allow me to move it either stating i don't have permission. I'm guessing i have to use a sudo command to delete it but i dont know what it is. Can someone help me out please?

---

### Post by jw5801 on 2008-08-13
Try: ```
sudo rm -rf ~/Desktop/<Folder you want to delete>
```

Be careful with 'sudo rm -rf' however, as it's used to recursively (delete everything in a subdirectory, in this instance) without prompting, and using root permissions.

You could also change it so that you own the folder, then you can do what you like with it:
```
sudo chown $(whoami):$(whoami) -R ~/Desktop
```

---

### Post by nothingspecial on 2008-08-13
You could also use nautilus 

```
gksudo nautilus
```

This gives you root access to your entire file system so remember to close it after you`ve finnished.

---

### Post by hyper_ch on 2008-08-13
because you dragged it from a cd onto your desktop it's read-only. change permissions accordingly.

The same happens on windows as a CD is "ready-only".

Besides running something as root should be done as seldom as possible. In that case it's not remotely necessary to run nautilus as root.

---

### Post by jw5801 on 2008-08-13
So to do that, run:
```
sudo chmod -R a+rw ~/Desktop/<folder-name>
```

---

### Post by mcduck on 2008-08-13
No "sudo" needed. Files copied from CD or DVD are read-only, but owned by the user, not root.

So simple "chmod -R a+rw ~/Desktop/DIRECTORY" will do the trick.

---

### Post by Pioneer5000 on 2008-08-14
Thanks for the replies guys!

---

