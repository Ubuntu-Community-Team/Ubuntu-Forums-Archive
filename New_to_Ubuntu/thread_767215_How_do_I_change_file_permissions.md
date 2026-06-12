---
title: "How do I change file permissions?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by SegaFan on 2008-04-25
I'm transfering some files I have backed up on CD from an old computer (a mac), but for an unknown reason some of the files have their owner set as root when I try to access them on my Ubuntu PC (these are all photos I took with my camera and imported to the mac with iPhoto). I suspect this is something to do with iPhoto (or macs in general) being awkward. The only way I know how to view or even move them is by using sudo on the command line. Can I change the file ownership, or would it just be easier to go back to the mac and resave everything and transfer it again?

---

### Post by Calash on 2008-04-25
From the command line you can run something like

sudo chown user|group file

---

### Post by sam_delta on 2008-04-25
change their owner

type 

```
 sudo chown <user name> /filepath/file 
```

to change the ownership of everything in a folder

```
 sudo chown <user name> /folder/* 
```

let us know how it goes

sam

---

### Post by SegaFan on 2008-04-25
That works, thank you. :)

---

### Post by sam_delta on 2008-04-25
no problem , glad it works, enjoy ubuntu

---

