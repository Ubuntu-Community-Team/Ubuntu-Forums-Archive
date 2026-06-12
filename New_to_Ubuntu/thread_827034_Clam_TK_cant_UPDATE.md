---
title: "Clam TK cant UPDATE"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by balachandarlinks on 2008-06-12
When i want to update its signatures it says
   ***_You must be root to install updates._***
 
           What to do........
                   Help me please.......

---

### Post by hyper_ch on 2008-06-12
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tomatz on 2008-06-12
> **balachandarlinks said:**
> When i want to update its signatures it says
   ***_You must be root to install updates._***
 
           What to do........
                   Help me please.......



To run it as root, open a terminal and type:

```
gksu clamtk
```

Enter your password and enjoy ;)

---

### Post by davidvan on 2008-12-10
> **Tomatz said:**
> To run it as root, open a terminal and type:

```
gksu clamtk
```

Enter your password and enjoy ;)

Been in the technical industry for 21 years.. and I feel like I'm a junior tech again as I learn linux (ubuntu)..

.. I did a search and found the answer, right here..
many thanks..

---

### Post by Tomatz on 2008-12-11
> **davidvan said:**
> Been in the technical industry for 21 years.. and I feel like I'm a junior tech again as I learn linux (ubuntu)..

.. I did a search and found the answer, right here..
many thanks..

Thats ok :)

**gksu** basically allows the application to run as root *(clamtk runs the gui)* and as clam needs to write the virus definitions to the root of the filesystem, you need to be root to update.

Of course if your running any application as root **be very careful**. As you could cause **perminent damage**.

_BTW_

```
gksu 
```

Opens the nice little gnome password dialogue.

```
sudo
```

Prompts for a password in the terminal
 


;)

---

