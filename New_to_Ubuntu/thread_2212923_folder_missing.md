---
title: "folder missing"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by srinidhi2 on 2014-03-23
my music folder has suddenly gone missing ( and no, i haven't deleted it by mistake) . this is the second time that this has happened. does anyone know what might be the cause??  :confused:

---

### Post by Impavidus on 2014-03-23
A few suggestions: Was it on a separate partition/network storage that failed to mount? Ungraceful shutdown resulting in file system damage (check /lost+found)? Bad hard drive? Mounted something else at the location of the music directory? Script or cronjob automatically cleaning some directories?

---

### Post by mcse2000ca on 2014-03-23
I would go into your home directory first and press crtl and h to show your hidden files, maybe for some reason it is just hidden.

---

### Post by claracc on 2014-03-24
Perhaps you have copy something to the Music folder and you have changed the name of folder using "cp" or "mv" commands in console?.

Have you tried to use command ```
ls -la 
``` in your personal folder in order to see all the folders, hidden and not hidden?, perhaps your Music folder has been copied by accident in any of the other folders?. Or perhaps the name has been changed to music (no capital M)?

Also, how many users do you have?, as yo know from ubuntu filesystem, Music folder use to be:

```
/home/user_name/Music
```

Folders don't disappear by magic, please see [http://ubuntuforums.org/showthread.php?t=1704407](http://ubuntuforums.org/showthread.php?t=1704407) you will have to do something inadvertently.

---

### Post by srinidhi2 on 2014-03-25
I dont think its a problem related to mounting , but am not sure about the script or cronjob

---

### Post by srinidhi2 on 2014-03-25
there is one user on my ubuntu . And no it was never present as a hidden folder during both cases. Also i did not use the cp or mv command for the folder.

---

### Post by deadflowr on 2014-03-25
Check your trash.
Even though you might not have moved or copied the folder, it is still quite easy to inadvertently right click and select the option "move to trash".
Just a thought.

---

### Post by srinidhi2 on 2014-04-29
sorta found out what was going wrong . all the contents of my music folder were transferred to the /home/"usr"/.dc++/filelist . dunno how it happened

---

