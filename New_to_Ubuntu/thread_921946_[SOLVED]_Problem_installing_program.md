---
title: "[SOLVED] Problem installing program"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by mr wilson on 2008-09-16
I am attempting to install some linux software. When I run the installer I get this message:

```
Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/Mathematica/6.0:
> 

Error: Cannot create directory /usr/local/Wolfram/Mathematica/6.0.

You may need to be logged in as root to continue with this installation.

```

What can I do? How do I login as root?

Cheers

---

### Post by jemate18 on 2008-09-16
> **mr wilson said:**
> I am attempting to install some linux software. When I run the installer I get this message:

```
Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/Mathematica/6.0:
> 

Error: Cannot create directory /usr/local/Wolfram/Mathematica/6.0.

You may need to be logged in as root to continue with this installation.

```

What can I do? How do I login as root?

Cheers

You need to have root privileges to write/install..

type 
```
sudo [thenthecommandyouhaveexecutedtoinstall]
```

---

### Post by compnut41 on 2008-09-16
Search for in the synaptic Package manager under Systerm-->Administration.

Much easier than using the terminal.:)

---

### Post by mr wilson on 2008-09-16
Yeah I read I could do that - the only problem is, I didn't type a command to start installing the software, I just clicked on installer

---

### Post by karlr42 on 2008-09-16
You could try "sudo nautilus", then navigate to the installer and click then.

---

### Post by mr wilson on 2008-09-16
Cheers. That worked a treat.

---

