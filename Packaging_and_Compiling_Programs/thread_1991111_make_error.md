---
title: "make error"
date: 2012-05-30
forum: Packaging and Compiling Programs
---

### Post by rupeshkp728 on 2012-05-30
I have written a simple kernel module with only init and exit modules.
When I fire make command I get the following error:

```

make -C /usr/src/linux-2.6.32 SUBDIRS=/home/LDD/LDD_Practice modules
make[1]: Entering directory `/usr/src/linux-2.6.32'

[B]
/bin/sh: cannot create /home/LDD/LDD_Practice/.tmp_versions/ldd1.mod: Permission denied
[/B]
make[2]: *** [/home/LDD/LDD_Practice/ldd1.o] Error 2
make[1]: *** [_module_/home/LDD/LDD_Practice] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.32'
make: *** [default] Error 2

```

What might be the cause of it and how to resolve it?
FYI I have the root permissions.

---

### Post by kc1di on 2012-05-30
> **rupeshkp728 said:**
> I have written a simple kernel module with only init and exit modules.
When I fire make command I get the following error:

```

make -C /usr/src/linux-2.6.32 SUBDIRS=/home/LDD/LDD_Practice modules
make[1]: Entering directory `/usr/src/linux-2.6.32'

[B]
/bin/sh: cannot create /home/LDD/LDD_Practice/.tmp_versions/ldd1.mod: Permission denied
[/B]
make[2]: *** [/home/LDD/LDD_Practice/ldd1.o] Error 2
make[1]: *** [_module_/home/LDD/LDD_Practice] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.32'
make: *** [default] Error 2

```

What might be the cause of it and how to resolve it?
FYI I have the root permissions.
Who own the Home Directory?  it's not allowing make to create a file in that directory.

---

### Post by rupeshkp728 on 2012-05-30
Thanks kc1di for the reply.

I am able to create the folders and files in home manually through command or explorer as my user has root permissions.
I have created folder like LDD, LDD_Practice etc. and have files in them.

Is it that make is getting restricted?

---

### Post by Bachstelze on 2012-05-30
> **rupeshkp728 said:**
> 
I am able to create the folders and files in home manually through command or explorer **as my user has root permissions**.


What have you done? Only root should have "root permissions".

---

### Post by kc1di on 2012-05-30
> **rupeshkp728 said:**
> Thanks kc1di for the reply.

I am able to create the folders and files in home manually through command or explorer as my user has root permissions.
I have created folder like LDD, LDD_Practice etc. and have files in them.

Is it that make is getting restricted?
you may have to give permissions for make to be able to write to the folders. go to the folder right click on it scroll to properties and then to the permissions tab you will most likely find that under group admin is not included with write abilities.
hope that helps.

---

### Post by Bachstelze on 2012-05-30
> **kc1di said:**
> you may have to give permissions for make to be able to write to the folders. go to the folder right click on it scroll to properties and then to the permissions tab you will most likely find that under group admin is not included with write abilities.
hope that helps.

No, no, no, no, no. There should be no need to change any permission. If you need to, you are doing something wrong.

---

