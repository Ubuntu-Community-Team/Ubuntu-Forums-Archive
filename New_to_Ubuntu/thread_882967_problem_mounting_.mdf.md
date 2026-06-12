---
title: "problem mounting .mdf"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by nk91 on 2008-08-07
i have mounted a .mdf file using AcetoneISO2 and it is an autorun cd which requires super user privileges. how would i use terminal to access the file?

any help would be appreciated :)

---

### Post by eightmillion on 2008-08-07
Could you paste the ouput of the **mount** command, please.

---

### Post by scorp123 on 2008-08-07
BTW, in the repos there is this program: **mdf2iso** ... With it you could convert your *.mdf files into standard (ISO 9660) *.iso files which are easier to handle I guess.

---

### Post by nk91 on 2008-08-12
alright so i have converted it into an iso and mounted it in /media/cdrom0 yet have a problem running the cd because the permissions are set to root. is there any way i can change this?

---

### Post by eightmillion on 2008-08-14
nk91, just do this:
> sudo chown **YOURUSERNAME**:**YOURUSERNAME** /media/cdrom0
Make sure you change **YOURUSERNAME** to your actual username.

---

