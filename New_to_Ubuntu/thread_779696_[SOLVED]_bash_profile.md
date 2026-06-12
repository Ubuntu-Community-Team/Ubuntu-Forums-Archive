---
title: "[SOLVED] bash_profile"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by inter-m on 2008-05-02
hi
im trying to learn some scripting... and now i reached a point were im suposed to make an alias in the .bash_profile... i cant find that file for some reason... is it the same as the .bashrc... i also tried creating .bash_profile in my home dir and i edited in my alias but nothing seems to take place... i would like for someone to point into the right direction... thank u in advance...
K.H.

---

### Post by glennric on 2008-05-02
Aliases are usually put in .bashrc
They won't take effect immediately.  You will have to close the terminal and reopen it.

---

### Post by noynac on 2008-05-02
Please delete

---

### Post by glennric on 2008-05-02
> **noynac said:**
> Please delete

What?

---

### Post by inter-m on 2008-05-02
> **glennric said:**
> Aliases are usually put in .bashrc
They won't take effect immediately.  You will have to close the terminal and reopen it.

thanx for the info... but im still confused on the .bash_profile... and i tried closing the terminal and opening it again but nothing took effect...

---

### Post by olejorgen on 2008-05-02
.bash_profile is only read at login
.bashrc is read whenever bash is opened, so you want to put your aliases there.

If you put them in .bash_profile, my guess is that they'll only work in the shell where you logged in from. (or not at all)

---

### Post by inter-m on 2008-05-02
> **olejorgen said:**
> .bash_profile is only read at login
.bashrc is read whenever bash is opened, so you want to put your aliases there.

If you put them in .bash_profile, my guess is that they'll only work in the shell where you logged in from. (or not at all)

thanks....
the alias work in the .bashrc after i relogged in... but didnt work with the .bash_profile... so ill stick with the .bashrc... thaks all...

K.H.

---

### Post by noynac on 2008-05-02
> **glennric said:**
> What?

I meant to say please delete my posting. It duplicated the previous posting.

---

### Post by ABX323 on 2008-05-02
You can make temp alias on the fly with the alias="command some args" just for that bash session in the CL.

---

