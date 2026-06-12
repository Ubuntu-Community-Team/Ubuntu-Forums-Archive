---
title: "cant delete a locked file"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by elijah dylan on 2012-08-24
tried everything i could to delete this file ..
it has a lock over it 
it has r-r-r permissions tried to change permissions not permitted 
tried to use nautilus to delete it again same answer not permitted 
please help gotta get rid of this junk file

---

### Post by spiky001 on 2012-08-24
Hi

It might be an idea to mention what this file is and where it is before deleting

---

### Post by elijah dylan on 2012-08-24
i was trying to do shell scripting its a .sh extension file 
in my home foder

---

### Post by elijah dylan on 2012-08-24
i am trying to delete this 1.sh file

---

### Post by spiky001 on 2012-08-24
Have you tried ```
sudo rm -v 1.sh
```

---

### Post by elijah dylan on 2012-08-24
operation not permitted

---

### Post by AlanR8 on 2012-08-24
Or.....

you could try it the graphical way with a small bit of terminal!

> sudo nautilus

Enter your password and the Admin or Root version of Nautilus will open.

Navigate to the file and delete!

Let us know.....

---

### Post by Cheesemill on 2012-08-24
> **AlanR8 said:**
> Or.....

you could try it the graphical way with a small bit of terminal!



Enter your password and the Admin or Root version of Nautilus will open.

Navigate to the file and delete!

Let us know.....

You shouldn't use sudo with graphical applications. Instead it should be:
```
gksudo nautilus
```

---

### Post by elijah dylan on 2012-08-24
i have tried that as well 
opened nautilus 
a box appears there i searched my respective file it was expected this time file will come up with no lock by its side but still there was lock on it and again operation denied popped up 
i think somehow i changed its permission and now cant undo them was trying octal codes with chmod 
and i think i did chmod 011 1.sh it is locked since then and tried to give it full excess or null excess but not letting me change  it anymore

---

### Post by alan21276 on 2012-08-24
what you've tried already should have worked......I'm thinking maybe a corrupt file.

I remember having those from my windows day's and proved neigh on impossible to remove.

Can you move it to another directory or a hidden folder perhaps....just to hide it away somewhere?

---

### Post by steeldriver on 2012-08-24
did you maybe set the file's attribute to 'immutable'? can you take a look with

```
lsattr 1.sh
```

---

### Post by elijah dylan on 2012-08-24
after doing that 
lsattr 1.sh 
gives me this output
----i--------e- 


and no i cant move it to any other dir either says access denied

---

### Post by steeldriver on 2012-08-24
OK so in order to remove it you will first need to remove the immutable attribute

```
chattr -i 1.sh
```

---

### Post by Bobhuber on 2012-08-24
> **elijah dylan said:**
> after doing that 
lsattr 1.sh 
gives me this output
----i--------e- 


and no i cant move it to any other dir either says access denied

sudo chattr -i 1.sh will remove the lock

---

### Post by elijah dylan on 2012-08-24
ok managed to delete it ..
thankss
 but would you mind telling how did i end up giving it immutable attribute and what does it means ?

---

