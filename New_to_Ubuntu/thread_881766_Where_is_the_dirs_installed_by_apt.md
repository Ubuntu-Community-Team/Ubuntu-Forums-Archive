---
title: "Where is the dirs installed by apt ?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by gamont on 2008-08-06
Hello.

How i find the directories where an package installed by apt-get install put the files ?

thanks

---

### Post by Dedoimedo on 2008-08-06
Hello,

By running the which command, which <package-name>, like:

which httpd

You'll get the binary for the program.

By running system-wide search, you'll get all files:

cd /
updatedb
locate <package-name>

Cheers,
Dedoimedo

---

### Post by tuxxy on 2008-08-06
Depends on what appliation you are talkin, it could be lcoated in your/nome folder in a hidden dir if you mean install system files.

You could just locate the file you need by entering locate firefox for example

---

### Post by decoherence on 2008-08-06
In Synaptic, select the package you want info on and click the Properties button. Click the Installed Files tab and you'll see the location of all the files that were installed by that package.

---

### Post by Vivaldi Gloria on 2008-08-06
> **gamont said:**
> How i find the directories where an package installed by apt-get install put the files ?


Use the command

```
dpkg-query -L <package_name>
```

to get a list of installed files. See

```
man dpkg-query
```

for more info.

---

### Post by gamont on 2008-08-06
thanks for all.

---

