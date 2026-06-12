---
title: "how to enable component call universe"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by hakimade on 2008-10-18
The terminal states "You will have to enable component called 'universe'" when I try to install java compiler

---

### Post by t0p on 2008-10-18
> **hakimade said:**
> The terminal states "You will have to enable component called 'universe'" when I try to install java compiler

I take it you tried to install java via an **apt-get** command in the terminal?

I think you need to enable the universe repository.  Though I thought it came enabled by default...  Anyway, easiest way is to go to **System > Administration > Software Sources**.  Under the **Ubuntu Software** tab, tick the box for **Community maintained Open Source Software (universe)**.

---

### Post by hakimade on 2008-10-18
the terminal state "sudo apt-get install udo"

---

### Post by stephanvaningen on 2008-10-18
> **hakimade said:**
> the terminal state "sudo apt-get install udo"
What T0p is explaining about the Software Sources is what you should do I think.

---

### Post by hakimade on 2008-10-18
Teminal state "bash:udo:command not found" when typed sudo apt-get install sun-java6-jdk

---

### Post by stephanvaningen on 2008-10-18
Then maybe the 's' did not come through?

---

### Post by t0p on 2008-10-18
> **hakimade said:**
> Teminal state "bash:udo:command not found" when typed sudo apt-get install sun-java6-jdk

LOL!!  You typed *udo* by mistake, instead of *sudo*.

Sorry for laughing... but that's damn funny!  Udo!  LMAO! :D

---

### Post by hakimade on 2008-10-18
the terminal state "sudo apt-get install udo"
then it teminal state "bash:udo:command not found" when typed sudo apt-get install udo

what do you think i can do

---

### Post by t0p on 2008-10-18
> **hakimade said:**
> the terminal state "sudo apt-get install udo"
then it teminal state "bash:udo:command not found" when typed sudo apt-get install udo

what do you think i can do

First, you need to update your package list.  Do this by typing in terminal:

```
sudo apt-get update
```

Next, type

```
sudo apt-get install udo
```

That *udo* threw me for a bit.  I thought it was a typo for *sudo*.  I didn't realize there's actually a package called *udo* til I checked.

Anyway, those instructions should sort you out.

---

