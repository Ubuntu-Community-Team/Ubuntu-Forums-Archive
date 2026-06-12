---
title: "A project called &quot;panic-button&quot; ?"
date: 2006-11-22
forum: Programming Talk
---

### Post by neoflight on 2006-11-22
i dont know if this is the right place for this...

I have a project in mind... its called say "panic-button"... [actually its  the 'recovery' !!! :)]. what it should do is to revert all the config files to their factory settings. my objective is to have that included in the installation cd. 

so one just boot from the cd or just insert and an option pops up "panic-button" ...:cool:  (we know that when we insert the installation disc on a working ubuntu system, we could open the package manager --updates etc.)

once you hit that (panic-button) then **ONLY** the default (factory provided) **"configuration"** files are restored in their appropriate places. it doesn't change the user installed stuff. This way one can avoid reformatting or completely reinstalling the OS. or even backporting or upgrading libs...

i confess: 
is it available already? i dont know. 

[i dont know whether selecting the upgrade option while in the same version does that or not... never tried it...]

how can i make this one? in python/c++ and a gui ?

now trying to do some research....

any thots.

mods: if this already exists please feel free to delete this post ](*,)

---

### Post by foxylad on 2006-11-23
Depends which config files you are talking about. Usually system programs store their settings in /etc, so you could do a new install, and then just back up /etc (tar -xzf etc.tgz /etc).

User applications can also store stuff anywhere in home directories, usually with file names starting with "." so they are hidden. These are harder to back up because they can be located almost anywhere.

---

