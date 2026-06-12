---
title: "Xubuntu 7.10 Shutdown problem"
date: 2008-03-16
forum: Philippine Team
---

### Post by dodimar on 2008-03-16
Installed Xubuntu 7.10,
Everytime I shutdown or restart, the system hangs and there is a never ending beep.

Help..

:confused:

---

### Post by Nhatz on 2008-03-16
Try mo mag-update baka maayos.
Astig! :guitar:

---

### Post by dodimar on 2008-03-16
fully update na siya.. pero ganun pa din...

---

### Post by Nhatz on 2008-03-16
Hmmmmm...... kasi sa laptop ko nman may problem sa startup... nag looping sounds sya... tapos pagupdate ko naayos na. hehehehe. :)
try mo mag shutdown sa terminal...
```
sudo halt -s
``` 
Astig!:guitar:

---

### Post by dodimar on 2008-03-17
yeah.. sa terminal okay siya..

pero ung ibang gagamit di marunong ng terminal..

parang babalik ako ng gnome nito ...

---

### Post by Nhatz on 2008-03-17
halos pareho lang nman ng gnome yun eh
hehehehe :)
Astig! :guitar:

---

### Post by dodimar on 2008-03-17
Bagal kasi ng gnome sa akin.. mas matulin ang xfce...

---

### Post by Nhatz on 2008-03-17
Ano ba specs ng box mo? hehehehe :)
Astig! :guitar:

---

### Post by dodimar on 2008-03-17
Specs ko.. check my signature...
mababa ang cache and video card...

---

### Post by Nhatz on 2008-03-18
ok nman specs mo ah... ok nga lang gnome sa P3 600 ko dati.
do some tweeking lang... remove mo mga stuffs na hindi mo masyado kailangan.
or kung gusto mo mabilis...Fluxbox. hehehe :)
Astig! :guitar:

---

### Post by ragadanga63 on 2008-03-18
As interim measure, you can create a script for shutting down your computer.  
1.    Open gedit.  Then on gedit, type the following command: "sudo poweroff" (quotation marks not included).  Then save on desktop as .txt file.

2.   Set executable permission.  Right-click on the text file you created, click on "properties".  On the dialogue box that appears, tick on "Allow executing file as program".

3.  Protect this file from being tampered with by other users. On the same properties dialogue box set access to "Read Only".

To shutdown, just double click on the file you created and click on Run in Terminal.   

The drawback of this method is that it will require the user's password.

---

### Post by sonnydoriginal on 2008-03-18
ayos na yos d2 . masaya ang kwentuhan. kaya chika lang nang chika. para di maubusan. mag-research:popcorn:

---

### Post by dodimar on 2008-03-19
I'll to tweak gnome.. pag nabagalan pa din ako.. fluxbox na ang gagamitin ko.. 

as for the shortcut, yeah, gusto ko din try, pero draw back kasi negative ang nagiging tingin sa Linux.

Currently experimenting with fluxbox and awesomewm..

Cheers..

---

