---
title: "How to get root access"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by gnugen on 2013-04-25
Hello I have been using lubuntu 12.10 for a while, but how do you get root access? I cannot update MATE because of this. Or how do you go root, because MATE asks me if I am root(just to install one updated package).

---

### Post by lisati on 2013-04-25
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gnugen on 2013-04-25
Thank you. Will not be making a root account in a hurry now. Will Just use MATE as it is and not update it.

---

### Post by Impavidus on 2013-04-25
There's no reason not to update when you haven't enabled your root account. In fact, it's best to keep your root account disabled and update using sudo, exactly as explained in the link lisati gave you. *In concreto*, issue the commands```
sudo apt-get update
sudo apt-get upgrade
```and give your normal user password. Or use the GUI, but I don't know exactly how that works on Lubuntu or MATE.

---

