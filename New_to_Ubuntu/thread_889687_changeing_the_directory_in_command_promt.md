---
title: "changeing the directory in command promt"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Orfintain on 2008-08-14
I'm trying to install a bin file

from the command promt and I need to change the directory I'm in, what is the command to do so ? (something like cd XXXX and dir /p (from dos) would useful thanks)

---

### Post by null byte on 2008-08-14
Use **cd**.

---

### Post by meindian523 on 2008-08-14
```
cd /path/to/directory
```
Use the man pages and the appropos command.To find out more about apropos,type ```
man apropos
```

---

### Post by finer recliner on 2008-08-14
```
cd /path/to/directory
```

---

### Post by Orfintain on 2008-08-14
Thanks guys , / (=/=) \  , also it's case sensitive, and cd starts you at root each time not the directory you're in , but it got it now (:

---

### Post by meindian523 on 2008-08-14
nopes,cd starts you at your home directory,/home<username> unless you are running as root,which is a security nightmare.

---

### Post by LowSky on 2008-08-14
here was something that always bugged me

Microsoft operating systems use \ for paths
While everyone else uses / including the WWW

So annoying

---

### Post by finer recliner on 2008-08-14
> **LowSky said:**
> here was something that always bugged me

Microsoft operating systems use \ for paths
While everyone else uses / including the WWW

So annoying

the windows command prompt will take either slash now, but it would still like \ to be the correct one.

---

### Post by TheMaxzilla on 2008-08-14
> Microsoft operating systems use \ for paths
While everyone else uses / including the WWW

Keyword: Microsoft

---

### Post by meindian523 on 2008-08-14
Recurring discussion at hand.Mods,please close the thread.

---

### Post by Orfintain on 2008-08-14
I don't think i'm running in root ... It just took me a second to realize that if i'm in the home forlder and what to change to desktop i have to type cd home/user/desktop not cd/user/desktop

---

### Post by null byte on 2008-08-14
> **Orfintain said:**
> I don't think i'm running in root ... It just took me a second to realize that if i'm in the home forlder and what to change to desktop i have to type cd home/user/desktop not cd/user/desktop
If you are in the home folder, simply type **cd Desktop**.
To get the current directory, type **pwd**.

---

