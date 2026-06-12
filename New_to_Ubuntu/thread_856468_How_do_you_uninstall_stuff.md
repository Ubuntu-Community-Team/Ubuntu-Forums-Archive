---
title: "How do you uninstall stuff"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-11
Can someone just give me a run by on how to do it

thanks

:guitar:

---

### Post by snowpine on 2008-07-11
Hi Jimi, the easiest way is to use the "Add/Remove Programs" option that's in the Applications menu. The other methods are to use the Synaptic Package Manager in your System menu or the command line (sudo apt-get remove whatever).

---

### Post by finer recliner on 2008-07-11
if you installed it from the repositories using the command ```
 sudo apt-get install <application> 
```

you would remove it using the command ```
 sudo apt-get purge <application> 
```

---

### Post by aimpau on 2008-07-11
1. If you know the exact name of the program: w/o the brackets
```

sudo apt-get remove [name of program]

```

2. If not, or just want to browse through
Applications>>System>>Add/Remove

3. Thorough browse through with add'l options
Applications>>System>>Synaptic Package manager

---

### Post by jimi_hendrix on 2008-07-11
ok this paticular game has been giving me some trouble

see [http://ubuntuforums.org/showthread.php?t=853712]("http://ubuntuforums.org/showthread.php?t=853712")

and

[http://ubuntuforums.org/showthread.php?t=854145]("http://ubuntuforums.org/showthread.php?t=854145")

when i do either of those commands i get

vincent@vincent-laptop:~$ sudo apt-get remove PlaneShift
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package PlaneShift

also it doesnt show up in the add/remove application thing

---

### Post by aktiwers on 2008-07-11
Remember the Terminal is CasE-SenSitIve.

Try again with small letters:
```
sudo apt-get remove planeshift
```

If that does not work, try the <Tab> key on you keyboard. Like type in :
```
sudo apt-get remove plane<hit tab>
```

<tab> will autocomplete the word

---

### Post by mcduck on 2008-07-11
How did you install it in the first place? If you installed it with Ubuntu's package management tools (or using a .deb package) you can also remove it thwith the same tools. I recommend Synaptic, as it gives you a nice GUI where youc an searh for the package name.

If you used some other way you pretty much have to follow install/uninstall instructions that came with the program.

---

### Post by jimi_hendrix on 2008-07-11
> **aktiwers said:**
> Remember the Terminal is CasE-SenSitIve.

Try again with small letters:
```
sudo apt-get remove planeshift
```

If that does not work, try the <Tab> key on you keyboard. Like type in :
```
sudo apt-get remove plane<hit tab>
```

<tab> will autocomplete the word

my computer beeps when i hit tab

---

### Post by jimi_hendrix on 2008-07-11
> **mcduck said:**
> How did you install it in the first place? If you installed it with Ubuntu's package management tools (or using a .deb package) you can also remove it thwith the same tools. I recommend Synaptic, as it gives you a nice GUI where youc an searh for the package name.

If you used some other way you pretty much have to follow install/uninstall instructions that came with the program.

ok problem with that

there is an icon on my desktop saying "PlaneShift Uninstaller" the thing is i apparently installed this thing wrong (the instructions on the ubuntu website telling me how were in germen or something) and the game client, updater, and all the other apps that it installed belong to root...and i dont know how to become root ive been advised not to become root so basically i cant use the uninstall app...or the game which is why im trying to uninstall it

:guitar:

---

### Post by mcduck on 2008-07-11
> **jimi_hendrix said:**
> ok problem with that

there is an icon on my desktop saying "PlaneShift Uninstaller" the thing is i apparently installed this thing wrong (the instructions on the ubuntu website telling me how were in germen or something) and the game client, updater, and all the other apps that it installed belong to root...and i dont know how to become root ive been advised not to become root so basically i cant use the uninstall app...or the game which is why im trying to uninstall it

:guitar:

press alt-f2 and run "gksudo nautilus" to open the file manager as root. Then browse to your own desktop and try running the uninstaller.

(it's of course OK to use root privileges for tasks that require them, it's just that you shouldn't log in as root as that would make _everything _ you do and every program you run to use root permissions as well. So the idea is to use minimum force required for the task you are trying to do..)

---

### Post by jimi_hendrix on 2008-07-13
when i do that and i search "PlaneShift" it lags my computer and the program crashs

---

