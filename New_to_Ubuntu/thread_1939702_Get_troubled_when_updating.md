---
title: "Get troubled when updating"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by eduardo saxel on 2012-03-12
When trying to update with update manager I get this:

"Apply the following changes?
Warning
You are about to install software that cannot be authenticated!"

And then a list of the non authenticated software, the software to be upgraded and the software to be installed. At the bottom of this window there's an option for download packages files only.

What to do?

---

### Post by plucky on 2012-03-12
> **eduardo saxel said:**
> When trying to update with update manager I get this:

"Apply the following changes?
Warning
You are about to install software that cannot be authenticated!"

And then a list of the non authenticated software, the software to be upgraded and the software to be installed. At the bottom of this window there's an option for download packages files only.

What to do?

Open a terminal and post output for ```
sudo apt-get update
```

---

### Post by grahammechanical on 2012-03-12
Have you put any PPAs as software sources? Or, installed software by not using the Ubuntu Software Centre?

Software we install though the software centre is authenticated software. The other stuff is not and Update Manager is not going to take responsibility for it.

In the past we could click to accept the full download. Now, I think it just closes Update Manager. Well, it does for me. Just open Settings and remove the tick mark form any PPAs and then the authenticate download can proceed.

Regards.

---

