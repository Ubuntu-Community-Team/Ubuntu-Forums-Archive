---
title: "mountvol.exe in windows?"
date: 2008-08-07
forum: Other OS Talk
---

### Post by garuhhh on 2008-08-07
hi!
i dual boot with ubuntu hardy and vista, my documents are on a third partition.i don't usually shutdown, rather, use hibernate on both OS. 

problem: files are not updated when i go from ubuntu to vista. i need to restart to see changes i made in ubuntu.

i have no problem going from vista to ubuntu, unmounting and re-mounting the volume updates my files (changes made from windows). doing that in vista (using mountvol.exe) doesn't update the drive contents, i need to restart the pc!! restarting takes a lot of time.. :(

to unmount volume in vista, i do this..
```
mountvol d:\ /D
```
to re-mount volume in vista, i do this..
```
mountvol d:\ \\?\Volume{6c5120e7-e745-11dc-8d8e-806e6f6e6963}\
```

BUT, files are not updated.. am i doing it wrong? or is there another way to update my files without restarting?

---

### Post by garuhhh on 2008-08-08
bump..

---

### Post by garuhhh on 2008-08-12
bump..bump..

---

### Post by kdorf on 2008-08-12
The problem is likely that you're hibernating. A hibernating operating system wouldn't expect the files to change at all while it's sleeping.

You really should probably just shutdown.

But in Windows Explorer you can press F5 to refresh. If you load any files that were already changed the changes should carry over.

---

### Post by garuhhh on 2008-08-14
ah yes...i do use hibernate, instead of the time consuming restart/shutdown. besides, i like to see all my windows/applications untouched when i get back to them, especially if i'm working on a project or something.

i have no problem with hibernate in ubuntu, coz i can unmount a drive, then re-mount it and everything on my drive is updated, even if i was doing something on windows while ubuntu is asleep (hibernated)

that's not the case with windows..unmounting, then remounting doesn't do a thing.. F5 in windows explorer doesn't do a thing either :confused:

anyone having similar problems with me?

---

