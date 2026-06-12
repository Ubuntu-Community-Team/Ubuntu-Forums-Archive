---
title: "gksudo cp throws out a file not found error"
date: 2009-11-09
forum: Programming Talk
---

### Post by kainalu on 2009-11-09
Hey everyone,

Im getting an error in a script while trying to cp using gksudo

```
gksudo "cp /home/$user_name/Desktop/Temp_aircraft_install_dir/* $FG_AC_DIR -r"
```

results in:

cp: cannot stat `/home/kainalu/Desktop/Temp_aircraft_install_dir/*': No such file or directory


The variables at the beginning of the file are correct, and I even tried absolutes to see if the variables were throwing a wrench, no luck. I want to actually do
Code:

~/Desktop/Temp_aircraft_install_dir/*

instead, but that throws even more problems out.

THANKS ALL!!!

---

### Post by John Bean on 2009-11-09
Inside the gksudo command you are root, and of course there's no such user in the /home subtree. The error reported is very confusing; I suspect it's not what it appears to be at face value.

---

### Post by spupy on 2009-11-09
> **kainalu said:**
> Hey everyone,

Im getting an error in a script while trying to cp using gksudo

```
gksudo "cp /home/$user_name/Desktop/Temp_aircraft_install_dir/* $FG_AC_DIR -r"
```

results in:

cp: cannot stat `/home/kainalu/Desktop/Temp_aircraft_install_dir/*': No such file or directory


The variables at the beginning of the file are correct, and I even tried absolutes to see if the variables were throwing a wrench, no luck. I want to actually do
Code:

~/Desktop/Temp_aircraft_install_dir/*

instead, but that throws even more problems out.

THANKS ALL!!!

Do you want to copy the "Temp_aircraft_install_dir" folder recursively? Try removing the * at the end.

---

### Post by sisco311 on 2009-11-09
try:
```
gksudo "bash -c 'cp /home/$user_name/Desktop/Temp_aircraft_install_dir/* $FG_AC_DIR -r'"
```

---

### Post by benj1 on 2009-11-09
why are you using gksudo

you should be using sudo for terminal apps, you also don't need to quote it

---

### Post by ikt on 2009-11-09
> **benj1 said:**
> why are you using gksudo

you should be using sudo for terminal apps, you also don't need to quote it

Indeed, from the manpage:

> gksu is a frontend to su and gksudo is a frontend to sudo.  Their primary purpose is to run graphical commands that need root without the need to run an X terminal emulator and using su directly.

---

### Post by spupy on 2009-11-09
> **benj1 said:**
> why are you using gksudo

you should be using sudo for terminal apps, you also don't need to quote it

> **ikt said:**
> Indeed, from the manpage:

I assume OP uses it for a script that he doesn't run from the terminal, but by clicking it/using a shortcut. In that case he will need gksu, even if using other terminal programs.

---

### Post by kainalu on 2009-11-09
The script calls dialog, and that is why I want a front end for sudo. It makes no sense to have the whole script as a  GUI except for when I need permissions. Also, I am trying to only copy the contents of  the directory, not the whole directory, as the directory is just a temp container for stuff to get un-tarred into and worked on before getting moved. 

The command:
gksudo "bash -c 'cp /home/$user_name/Desktop/Temp_aircraft_install_dir/* $FG_AC_DIR -r'"
Worked perfectly.


THANKS GUYS!!! :D:D:D

---

