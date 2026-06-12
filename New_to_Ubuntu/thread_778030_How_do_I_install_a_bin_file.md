---
title: "How do I install a bin file?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-01
Hi

How do I install a bin file?

---

### Post by Milos_SD on 2008-05-01
Open a terminal and cd to dir where is that .bin file and do this: 

sh nameoffile.bin

---

### Post by saskatchewan on 2008-05-01
It says "can't open GoogleEarthLinux.bin"

What am I doing wrong?

---

### Post by sisco311 on 2008-05-01
Right click on the file and select Open With Other Application -> Use Custom Command -> type "sh" (without the quotes) -> OK

or open a terminal and type
```
sh
```then type a Space and Drag and drop the file into the terminal window and press Enter(Return)

---

### Post by Monicker on 2008-05-01
> **saskatchewan said:**
> It says "can't open GoogleEarthLinux.bin"

What am I doing wrong?

I stole this from another thread.  ;)


[https://help.ubuntu.com/community/GoogleEarth]("https://help.ubuntu.com/community/GoogleEarth")

---

### Post by roachk71 on 2008-05-01
If that still doesn't work, the file permissions need to be changed to make the file executable:

```
 sudo chmod +x *filename*
```

---

### Post by saskatchewan on 2008-05-01
Excellent!!

Thanks

---

### Post by Tatty on 2008-05-01
google earth is in the repos.  I suggest you install from there, itll save much hassle.

---

