---
title: "drive permission sudenly change to root for no reason"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by wawadave on 2008-10-26
i was transferring files from one computer to another. took a brake for lunch came back and tried again i cannot add any more files drive has 8 gigs free. permissions on all folder not say root and no way to change this.
some one accessing computer from net changing them???

only thing changed was me stopping nothing else.

---

### Post by scorchgeek on 2008-10-26
Try:
```
sudo chown [your username] [path to hard drive]
```

This will change the permissions of your hard drive back to you.

---

### Post by wawadave on 2008-10-26
Ok i got part of the problem fixed.
 the part that was fixed was i had created a new folder inside the shared folder. And i could see all files from here but could not transfer them here. i moved the folder on other computer into another folder that had been created before this networking session. then i could move the files to this ubuntu computer.

But that still leaves me wondering why all folder on the drive i,m transferring the files too all the permissions are set too root?
any way to change this?
thx

---

### Post by wawadave on 2008-10-26
we posted at the same time i will try and do what you suggested thx!!

---

### Post by dracayr on 2008-10-26
chown recursively: use the command scorchgeek gave you, just add an -R to it

dracayr

---

### Post by wawadave on 2008-10-26
Ok tried that no change
owner still root 
and file accesses still grayed out.

---

