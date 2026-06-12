---
title: "how can i run .bin in ubuntu"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by kasnrop on 2008-09-24
i have tried to run .bin file in GUI
it said that

Couldn't display /home/PPP/Desktop/monostack-1.1.16.1-linux-installer.bin

there is no application installed for this file type

and when i tried command in terminal like

chmod +x monostack-1.1.16.1-linux-installer.bin
chmod:cannot access ' monostack-1.1.16.1-linux-installer.bin' : no such file or directory

---

### Post by bruce89 on 2008-09-24
> **kasnrop said:**
> chmod +x monostack-1.1.16.1-linux-installer.bin
chmod:cannot access ' monostack-1.1.16.1-linux-installer.bin' : no such file or directory

./monostack-1.1.16.1-linux-installer.bin

You have to prepend the ./ thing to execute files in the current directory.

---

### Post by spiderbatdad on 2008-09-24
where is the file? If it is on your desktop, the command needs to include Desktop in the path: ```
sudo chmod +x ~/Desktop/monostack-1.1.16.1-linux-installer.bin
```
Then to run: ```
cd Desktop
./monostack-1.1.16.1-linux-installer.bin
```

---

### Post by TriSwords on 2008-09-24
> **kasnrop said:**
> chmod:cannot access ' monostack-1.1.16.1-linux-installer.bin' : no such file or directory

are you in the right directory?

---

### Post by kasnrop on 2008-09-24
very......thanx to all of you

---

