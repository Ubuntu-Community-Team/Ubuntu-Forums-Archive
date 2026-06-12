---
title: "[SOLVED] dos emulator"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by alpdo on 2008-09-16
hi everyon i installed dosemu using synaptic manager... but it wont run... what u could be possibly wrong ???? what should i do... ????:confused:

---

### Post by shoot2kill on 2008-09-16
any errors ???

what happens when you launch ```
dosemu
``` from the terminal ?

---

### Post by alpdo on 2008-09-16
when i tried to run it .... nothing happens... it just wont run....:(

---

### Post by shoot2kill on 2008-09-16
what heppens when you try to run it from terminal ???

does it not do anything? no error or message ???

---

### Post by alpdo on 2008-09-16
i only run it in application,,, system tools... i don't know how to run it on terminal

---

### Post by karlr42 on 2008-09-16
Applications->Accessories->Terminal Then type in the command!

---

### Post by alpdo on 2008-09-16
LOWRAM mmap: Invalid argument
Segmentation fault

---

### Post by shoot2kill on 2008-09-16
i get the same error.. i have to type

```

sudo dosemu

```
into the terminal.. then enter your password when prompted

---

### Post by karlr42 on 2008-09-16
Apparently(I only Googled), that's a bug in dosemu: [link](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/216398).
There's a workaround, which is 
> 

Permanent fix:

with root privleges edit /etc/sysctl.conf file; find the line that reads

    vm.mmap_min_addr = 65536

and change the number from 65536 to 0 (zero). Save and restart.

so, that'd be
```
sudo gedit /etc/sysctl.conf
```
and do as the rest says.
Hope it helps!

---

### Post by alpdo on 2008-09-16
tanks man.... :guitar:

---

### Post by alpdo on 2008-09-16
it work fine now after i edited and restarted my computer...

---

### Post by karlr42 on 2008-09-16
Cool, glad I could help, even if it was just by Googling :P

---

### Post by shoot2kill on 2008-09-16
I'm glad the foums could be of assistnace for you...

also, it would be apreciated when a problem is solved, for the topic to be labeled solved, this can be done via "Thread Tools" at the top of this page..

---

### Post by alpdo on 2008-09-22
okies

---

### Post by irw on 2008-11-25
> **karlr42 said:**
> Apparently(I only Googled), that's a bug in dosemu: [link](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/216398).
There's a workaround, which is 

Quote:
> 
Permanent fix:

with root privleges edit /etc/sysctl.conf file; find the line that reads

vm.mmap_min_addr = 65536

and change the number from 65536 to 0 (zero). Save and restart. 

so, that'd be
```
sudo gedit /etc/sysctl.conf
```
and do as the rest says.
Hope it helps!

What does this actually do? Are there security implications to this?

That file has this comment:> 
# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.

---

