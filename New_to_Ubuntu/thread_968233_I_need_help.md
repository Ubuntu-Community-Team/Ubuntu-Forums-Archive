---
title: "I need help"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-11-02
when I type su in the terminal and them my password it says "su: Authentication failure" what am I doing wrong?

---

### Post by darkvampire on 2008-11-02
Did you set a root password? If not you can set/change it with:
> sudo passwd root
Just enter the password twice and that is your root password set.

---

### Post by adieb on 2008-11-02
But wait.

Ubuntu is following another strategie... There is no real root account. It is all done with "sudo".

So you just put a "sudo" before your commands and they are going to be executed with root-privileges.
If you really want to become root you can type "sudo -i" for example. Or "sudo bash" or similar

---

