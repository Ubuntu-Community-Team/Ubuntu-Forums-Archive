---
title: "Backup Possible?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by sewqyne on 2008-10-21
Hello. It was my first experience with linux and ubuntu. But I have to format my hard drive and reinstall operating systems. I will install the Ubuntu back again.:guitar: But is it possible to backup my current programs, configuration etc. and port it to the next Ubuntu that I will install? If possible please explain the case in human digestible form. I am not a geek 'cause.  

Thanks.

---

### Post by halitech on 2008-10-21
if you want something easy that will allow you to put everything back the way it is currently, look into remastersys. If you just want to back up files, use Brasero or k3b to burn them to cd/dvd

---

### Post by hyper_ch on 2008-10-21
you can backup your configurations and personal files... for that just backup the /home and /etc folder (don't forget there are many hidden files in there...)

To backup a list of all installed libraries run this command:

```

dpkg -l | awk '/ii/ { print $2 }' | tr '\n' ' ' > packages.txt

```
That will generate one huge line. Then you can delete the packes/libraries/applications you don't know.

Once you done that, on the new system, add all the repositories you had before then and just use that file list to download and install your prgorams again. Simple way would be to run
```

sudo apt-get install `cat packages.txt`

```

---

### Post by beercz on 2008-10-21
If you have an external hard disk that can be mounted then you can use rsync to backup to that.

---

### Post by Orange_and_Green on 2008-10-21
Hi,

I am working on a project that backs up the list of all your installed programs... care to check it out? (Follow the link in my signature).

:) Happy Ubuntu installing :KS

---

