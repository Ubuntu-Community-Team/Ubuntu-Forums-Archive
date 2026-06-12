---
title: "Help!!! How to run a .run file ???"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by ovimunt on 2008-08-10
Hi,

I've just donwloaded the ATI drivers file **ati-driver-installer-8-7-x86.x86_64.run** but I don't know how to run it.... :o(  Any ideas?

By the way, I've tried **chmod 755 ati-driver-installer-8-7-x86.x86_64.run** but it doesn't look like it did anyhting so I still can't run it.

Thanks

---

### Post by maybeway36 on 2008-08-10
In the terminal:
```
sudo ./ati-driver-installer-8-7-x86.x86_64.run
```

---

### Post by Bodsda on 2008-08-10
chmod changes permissions, it doesnt run programs.

---

### Post by SFBuzz on 2009-05-07
sudo sh ati-driver-installer-8-7-x86.x86_64.run

Good luck, however. I'm using an ASUS M4A78-E mobo and trying to get sound to work... All I see is

[FONT=Courier New]Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

More research to do....
[/FONT]

---

### Post by TheNosh on 2009-05-07
maybe i'm just dumb or remembering wrong... but i'm pretty sure you just right click the .run file and got to properties, then go down to the option that (i think) says "allow file to run as program" and check the box. then it should run when you double click it

---

### Post by starcannon on 2009-05-07
```
chmod +x ./some_file_name.run
sudo ./some_file_name.run
```

---

