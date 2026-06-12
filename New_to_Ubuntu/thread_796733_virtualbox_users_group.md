---
title: "virtualbox users group?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Benbow on 2008-05-16
How do i add myself to the "virtualbox users group"?

---

### Post by shifty_powers on 2008-05-16
```
 sudo adduser username vboxusers
```

obviously just change username for your actual, well, username ;)

---

### Post by Oldsoldier2003 on 2008-05-16
> **shifty_powers said:**
> ```
 sudo adduser username vboxusers
```

obviously just change username for your actual, well, username ;)

edit: had command dyslexia, adduser will indeed work, grumpy old farts like me may also use

```
sudo usermod -aG vboxusers <username>
```

---

### Post by bubba_169 on 2008-05-16
The GUI route would be "System->Administration->Users and Groups", click the unlock button if you are not root, click manage groups, find vboxusers group in the list, highlight it then click properties. You can then tick your username to become part of this group!

I think you have to logout and back in again before it will recognize the change...

---

### Post by shifty_powers on 2008-05-16
> **Oldsoldier2003 said:**
> nope. 

he might try ```
sudo usermod -aG vboxusers <username>
``` though :)

well it worked for me so :P

---

### Post by Oldsoldier2003 on 2008-05-16
> **shifty_powers said:**
> well it worked for me so :P

lol yeah it does. My apologies I'm so used to useradd which definitely will NOT work :)  I'll edit the above posts to reflect my other way to skin the cat.

---

### Post by shifty_powers on 2008-05-16
heh, we're all guilty of things like that sometimes ;)

---

