---
title: "[SOLVED] Idiot deleted his /tmp directory"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Ryutatsu on 2008-05-14
I'm ashamed to say so. I rm -r ed my /tmp drive thinking that it didn't have anything important (I needed some extra space real quick to render a video for a project). DOH! Now, hardly anything works. X included. Does anyone know how to quickly rebuild the /tmp directory?

---

### Post by jimv on 2008-05-14
Type this in a terminal:

sudo mkdir /tmp
sudo chmod 777 /tmp

then reboot


(If you can't get a terminal open, push control+alt+f1)

---

### Post by 505 on 2008-05-14
Just create a directory (with "sudo mkdir /tmp") and set the persmission:
sudo chmod 777 /tmp

---

### Post by DrMega on 2008-05-14
Can't you just start in recovery mode, then issue:

```

mkdir /tmp

```

I'm not sure if there are other files that need to be in there or not, but I would guess probably not. I suspect any program that needs it just assumes /tmp is there and then creates any temp files it needs.

---

### Post by Monicker on 2008-05-14
> **jimv said:**
> Type this in a terminal:

sudo mkdir /tmp
sudo chmod 777 /tmp

then reboot


(If you can't get a terminal open, push control+alt+f1)


He should also do 

```
sudo chmod +t /tmp
```

EDIT: A shorter way would be to just chmod it as 1777 from the start.

---

### Post by Ryutatsu on 2008-05-14
I can use the terminal, I put /tmp back. I'm not sure about the permissions though, I'll set them to 777 and see if that helps. Right now my programs are failing with write errors on tmp this could either be a permissions problem or that the files need to already be there, we'll see. I'll try chmod 777 and get back to you.

---

### Post by jimv on 2008-05-14
> **Monicker said:**
> He should also do 

```
sudo chmod +t /tmp
```

What does +t do?

---

### Post by Ryutatsu on 2008-05-14
ok, all's good. 777 did the trick. I suppose using sudo to rm changed the permissions. I wasn't expecting that. Thanks a lot for all of the help guys.

---

### Post by Monicker on 2008-05-14
The +t makes it so that only the user who created a file can delete it.  Its the default state for /tmp.

---

