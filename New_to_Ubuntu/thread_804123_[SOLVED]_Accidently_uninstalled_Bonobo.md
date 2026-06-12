---
title: "[SOLVED] Accidently uninstalled Bonobo"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-05-22
I accidently uninstalled Bonobo and the other thing that comes with it, cant remember what its called.  How can I reinstall it (I have no panels so I cant see where the start/places/system/etc is but its still intact..Is this a hard fix?

---

### Post by PPAAUULL on 2008-05-22
Alt-F2 then you can click to see a list of apps and you can pick the terminal and type "sudo apt-get install (program)" to install whatever yoy want.

---

### Post by Master Grah on 2008-05-22
You can also use "sudo aptitude search (program)" if you can't remember what it's called.

---

### Post by Bubba64 on 2008-05-22
> **sox fan Matt said:**
> I accidently uninstalled Bonobo and the other thing that comes with it, cant remember what its called.  How can I reinstall it (I have no panels so I cant see where the start/places/system/etc is but its still intact..Is this a hard fix?

If you can get a terminal open type synaptic and look at the history possibly, and when I typed bonobo in the search it brought up libbonobo stuff.

---

### Post by PPAAUULL on 2008-05-22
Ya that is another option to just hit alt-f2 and type synaptic and then hit enter and you can do it the GUI way if that works better for you.

---

### Post by sports fan Matt on 2008-05-22
I couldnt get alt >f2..buty i could get into root from the recovery mode and I could also get in through recovery and select as root, then could I run a Sudo apt-get install bonobo?

---

### Post by PPAAUULL on 2008-05-22
Ya that might work but I am very surprised alt-f2 didn't work. Did you press them at the same time? a windows should popup called "Run Application"

---

### Post by sports fan Matt on 2008-05-22
Yeah I did...There is an error upon gnome starting but im not sure what it says, but i'll run upstairs and see what it says

---

### Post by sports fan Matt on 2008-05-22
the error states "couldnt register with bonobo activation server" error 3..Any ideas?

---

### Post by sports fan Matt on 2008-05-22
The wierd thing is the gnome desktop fires up, just that message appears and "nautilus cant be used" but its installed im pretty sure

---

### Post by sports fan Matt on 2008-05-23
Edit: I can now login failsafe to the terminal, so im wondering what command I must run to get the bonobo and the dependecies back..I tried a sudo apt-get install bonobo, and it says it cant find the package..

Thanks In Advance

---

### Post by Bubba64 on 2008-05-23
Have you tried sudo apt-get update then sudo apt-get dist-upgrade or regular upgrade, I don't know if the update system will recognize the missing file and suggest an install. When I ran bonobo in the synaptic search every thing came up as libbonobo try running that in a sudo apt-get install as well. I don't know how to give you a screen shot of this synaptic picture of libbonobo.

---

### Post by sports fan Matt on 2008-05-23
I havent..but I did discover this: e: package bonobo-activation has no instaliation candiate

---

### Post by sports fan Matt on 2008-05-23
Well, a sudo apt-get update updated things but since I cant see my gnome Panels to get to my start/system/places menus, I have no idea what was updated..everything works --except I cant see anything-(no gnome panels and alt f2 fails but recovery from boot works)

Why is this such a frustrating thing for me and if this seems easy at least to me, why cant I login to see my panels..Ive been at this 5 hours and im stumped:(

---

### Post by Bubba64 on 2008-05-23
> **sox fan Matt said:**
> Well, a sudo apt-get update updated things but since I cant see my gnome Panels to get to my start/system/places menus, I have no idea what was updated..everything works --except I cant see anything-(no gnome panels and alt f2 fails but recovery from boot works)

Why is this such a frustrating thing for me and if this seems easy at least to me, why cant I login to see my panels..Ive been at this 5 hours and im stumped:(

Did you try update then upgrade and also dist-upgrade. I don't know if these ideas will work I'm just checking. Also did you try sudo apt-get install libbonobo2 after the update if any thing is installed in terminal you would see it. you can also type history in terminal and see what has been done. Have you tried typing synaptic in the terminal which opens synaptic and searching with bonobo and also looked at the history in synaptic, the history may tell you what you removed, but I am not sure.

---

### Post by sports fan Matt on 2008-05-23
I solved it by just reinstalling Hardy cause everything with bonobo wasnt working, but I appreciate all the help! :) I had tried a dist upgrade and a upgrade and a libnobo2 but no avail but after a reinstall all is well..:)

---

