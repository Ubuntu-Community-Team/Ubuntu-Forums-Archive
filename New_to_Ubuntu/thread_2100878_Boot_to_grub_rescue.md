---
title: "Boot to grub rescue"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by jowze on 2013-01-03
Hello hello !

So after an install of Ubuntu, Lubuntu and a switch to pure Lubuntu, I take out the Boot CD. 
Booting to CD is my 3rd boot option, my second is a hard disk with free space, the 1st is the harddisk option I use to boot. 

Problem is, upon starting, its goes straight to "Grub Rescue" and doesn't boot to Lubuntu.
To make it boot, I need to press F11 and manually pick where to boot.

Any idea to how to prevent the computer from going to this grub rescue screen ?

Thanks !
Jo

---

### Post by Bashing-om on 2013-01-03
jowze; Hi !

See if this works;

Boot up your primary operating system (any 'buntu that is):
ctl+alt+t -> terminal:
in terminal run this command to update/(re)configure grub:
```
sudo update-grub 
```The use of sudo requires your pass word, no response back to the screen (security reasons)
[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by jowze on 2013-01-04
Hello !

Problem solved :)

Thanks

---

### Post by Bashing-om on 2013-01-04
jowze;

Great, pleased you are up.

Please mark this thread "solved" (thread tools), aides others seeking a solution, and assistant's time not looking at a solved situation.

[INDENT][INDENT][INDENT]happy ubuntu'n <== BDQ

[/INDENT][/INDENT][/INDENT]

---

