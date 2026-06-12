---
title: "[SOLVED] AVG will not download updates"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by unknown user on 2008-10-09
I have downloaded and installed the free version of AVG for Ubuntu from ([http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)) and all is well.  However, when I come to update the anti-virus database it is telling me that I do not have the permission to perform this act.Does anyone know why of had any experience with this?

I know that I do not need it, but I wanted to try it.

---

### Post by Kevbert on 2008-10-09
It may be the same as clamav.  You need to find out what command is used to run AVG.  You can do this by right-clicking on Applications and select Edit Menus.  You then need to find the AVG launcher program, right-click on it and select properties from this you get the command needed.
Now open terminal and enter
```
sudo *command*
```
This should give you the right privileges.
Out of interest, why are you using AVG ?  Linux Viruses don't exist in the wild and most antivirus programs only look for Windows viruses.  If you dual boot with Windows or share data files with windows programs then it's worth having antivirus software.

---

### Post by dhtseany on 2008-10-09
Good luck with this one. I too have installed AVG but it does nothing.

My reason for installing it was to make sure something I download on UB doesn't contain a virus that could screw up my 3 Windows boxes.

---

### Post by lisati on 2008-10-09
See [here]("http://ubuntuforums.org/showthread.php?t=889552") and [here]("http://www.avg.com/filedir/doc/AVG_7.5/LINUX_GROUP/AVG_Free_for_Linux/avg_afl_uma_en_75_2.pdf")

---

### Post by Nepherte on 2008-10-09
[http://ubuntuforums.org/showthread.php?t=889552](http://ubuntuforums.org/showthread.php?t=889552)

---

### Post by unknown user on 2008-10-10
I tried to sort this out yesterday, but got stuck at the Add your username to the avg user group point.  Am I right in thinking this is my username in the AVG License field?

---

### Post by Nepherte on 2008-10-10
> **unknown user said:**
> I tried to sort this out yesterday, but got stuck at the Add your username to the avg user group point.  Am I right in thinking this is my username in the AVG License field?
No, you have to do it in ubuntu itself through system > administration > users and groups. You can also do it in the command line:
```
sudo gpasswd -a yourusername avg
```

---

### Post by hyper_ch on 2008-10-10
are you sure you really need to run an antivirus on linux?

*Edit: yes, you know you don really need it*

---

### Post by gandaran on 2008-10-10
to update avg manually is very simple, just run the avg  gui as root
type in terminal sudo or gksu avggui, this opens a root gui where you can do everything including setting up automatic updates
just check if the run command is still **avggui**, I haven't used avg in a long time and the command could be changed.

---

### Post by unknown user on 2008-10-10
Cheers guys for your help, it works great

---

