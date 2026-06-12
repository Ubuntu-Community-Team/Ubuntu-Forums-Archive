---
title: "PlaneShift"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by vlad1975 on 2008-05-27
I have installed PLaneshift succesfully but when i go to Application>Games and click on either the updated or the game nothing happens. can anyone help me?:popcorn:

---

### Post by kesman on 2008-05-27
Have you tried running the game from terminal to see any error outputs?

---

### Post by vlad1975 on 2008-05-27
Hi and thank you for reply..could you tell me what the comman to type on terminal please?

---

### Post by kesman on 2008-05-27
I'd guess
```

planeshift

```

if not, type plane and press TAB two times to see the alternatives.

---

### Post by vlad1975 on 2008-05-27
ok it says permission denied.

---

### Post by kesman on 2008-05-27
Alright, so your user doesn't have permissions to use the executable. Didn't the installer tell you to chmod the files after installing?

Did you read this:
[http://hydlaa.com/smf/index.php?topic=19389.0](http://hydlaa.com/smf/index.php?topic=19389.0)
it says you have to chmod +x the downloaded file and there's a bunch of other information too.

---

### Post by vlad1975 on 2008-05-27
The directory
/opt
is not writable by the current use

how do i set /opt and tell it that i am the current user?

---

### Post by kesman on 2008-05-27
You need to use sudo in front of the command to get root-users rights so you can write anything else than your /home

---

### Post by vlad1975 on 2008-05-27
ok i am sure i did it right this time
ed@ed-desktop:~/Desktop$ sudo chmod +x PlaneShift-v0.4.00-x86.bin
ed@ed-desktop:~/Desktop$ sudo ./PlaneShift-v0.4.00-x86.bin

ran thru the installation
permission 777
permission to ed

and i also created shortcut to desktop
i stall can run it and the icons on desktop is showing a padlock which i assume that i dont have acess to my own computer or this game

anyone can help me please?

---

