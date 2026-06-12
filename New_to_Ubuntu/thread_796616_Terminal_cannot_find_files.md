---
title: "Terminal cannot find files"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by arc0 on 2008-05-16
First day on Ubuntu.  I have tried to download a shell script from my broker
and then run it to install.  The broker advises using the command :
sh ./thinkorswim_installer.sh.

I have the file in my home and my desktop and I get the message that it cannot find the file.  I also have had the same problem installing bin files, though with a different command line.  Do I need to modify the command line to show a path, or run from a different directory?  Could use some help getting started.
Thanks

---

### Post by Oldsoldier2003 on 2008-05-16
> **arc0 said:**
> First day on Ubuntu.  I have tried to download a shell script from my broker
and then run it to install.  The broker advises using the command :
sh ./thinkorswim_installer.sh.

I have the file in my home and my desktop and I get the message that it cannot find the file.  I also have had the same problem installing bin files, though with a different command line.  Do I need to modify the command line to show a path, or run from a different directory?  Could use some help getting started.
Thanks

you need to be in the same directory. if you downloaded the file to your desktop you need to open the terminal and type cd Desktop then sh ./thinkorswim_installer.sh

---

### Post by arc0 on 2008-05-16
I think that I am in the same directory.

marc@marc-desktop:~$ sh ./thinkorswim_installer.sh.
sh: Can't open ./thinkorswim_installer.sh.

Am I missing some program to open this?

---

### Post by eldragon on 2008-05-16
> **arc0 said:**
> I think that I am in the same directory.

marc@marc-desktop:~$ sh ./thinkorswim_installer.sh.
sh: Can't open ./thinkorswim_installer.sh.

Am I missing some program to open this?

check that you are adding a last dot to the filename, that might be your problem.

try completin with [tab]
i would
```

$ sh ./think[tab]

```

---

### Post by Kevbert on 2008-05-16
RIGHT click the thinkorswim_installer.sh file on your DESKTOP and select Properties, then select the Permissions tab at the top, and ensure the 'Execute' check-box is checked towards the bottom where it says 'Allow executing file as program'. Close window.
Now double click on the file to run the script.

---

### Post by herbster on 2008-05-16
```
chmod +x thinkorswim_installer.sh
```

---

### Post by Oldsoldier2003 on 2008-05-16
for the record guys he doesnt need to chmod the script if he calls the shell... its mostlikely he was still leaving the extra "." at the end of the file name.

---

