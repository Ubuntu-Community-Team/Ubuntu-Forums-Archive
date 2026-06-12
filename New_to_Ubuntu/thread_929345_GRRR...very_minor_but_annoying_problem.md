---
title: "GRRR...very minor but annoying problem"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Alex J. on 2008-09-24
So, I recently tried to reinstall ndiswrapper because of some wireless problems. Think I fixed the wireless,** but the freaking ndiswrapper folder won't delete from my desktop. **
GRRRR. It's starting to annoy me. Everytime I click delete (from cmd line or from the gui) it says I don't have permission. I go into the permission section and I can't change it from "Owner: 1100 Group: 1100" and I can't change the permissions. 

It must be something insanely simple. Any help?:-x

---

### Post by Bakon Jarser on 2008-09-24
```
gksudo nautilus
```

Go to

File System > Home > 'your user name' > Desktop

and delete it there.

---

### Post by TriSwords on 2008-09-24
Does something like

```
 sudo chmod 777 ndiswrapper* 
```

or whatever in place of ndiswrapper

then trying to delete it work?

---

### Post by Alex J. on 2008-09-25
AHH!!! Finally....I'm such a noob. Thanks so much ^_^

---

