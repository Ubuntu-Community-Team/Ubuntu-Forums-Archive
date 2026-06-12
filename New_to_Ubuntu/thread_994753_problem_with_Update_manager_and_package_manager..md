---
title: "problem with Update manager and package manager."
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Raut on 2008-11-27
Hi , i tried to install software repositories from medibuntu for adobe reader gave me some error.

now i am not able to open **update manager** or package manager.
there is a red coloured minus icon on my panel always 


**it gives Error:**


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--23:25:19--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'


i tried apt-get autoclean, also -f it gives the same error:

 
'E:Type '--23:25:19--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

i am using ubuntu 8.04

Plz help..

---

### Post by Xiong Chiamiov on 2008-11-27
Could you post the contents of your /etc/apt/sources.list please?

---

### Post by Raut on 2008-11-27
bash: /etc/apt/sources.list: Permission denied

---

### Post by Raut on 2008-11-27
what to do now??? plz help..

---

### Post by Xiong Chiamiov on 2008-11-27
Oh sorry, you need to **view** the file, rather than **execute** it, which is what you were doing.  You can use any of the following methods, although for this purpose I'd recommend the first.
```

gedit /etc/apt/sources.list
cat /etc/apt/sources.list
less /etc/apt/sources.list

```

When you get around to editing it, you'll want to use one of these two:
```

gksudo gedit /etc/apt/sources.list
sudo nano /etc/apt/sources.list

```

---

