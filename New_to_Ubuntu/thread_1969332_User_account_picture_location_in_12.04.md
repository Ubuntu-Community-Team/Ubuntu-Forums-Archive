---
title: "User account picture location in 12.04"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by Savellla on 2012-04-29
While going through the setup process, I used my webcam to take a user picture for my account.
Does anyone know where I could locate this file? As the title says, I'm currently running 12.04.
Thank you!

---

### Post by Baldrick_NZ on 2012-04-30
Hi Savella,

It's in your Home folder. You'll need to go view/hidden files to see it though.

It's called ".face" (without speech marks ofcourse).

---

### Post by MestreLion on 2012-05-21
> **Baldrick_NZ said:**
> Hi Savella,

It's in your Home folder. You'll need to go view/hidden files to see it though.

It's called ".face" (without speech marks ofcourse).

Not in 12.04.

User face icons are in **/var/lib/AccountsService/icons**

One 96x96 png file per user.

But you can (as root) edit the file **/var/lib/AccountsService/users/<yourusername>**
and change the **Icon** entry:

```
[User]
XSession=ubuntu
XKeyboardLayouts=
Background=/usr/share/backgrounds/contest/precise.xml
Icon=<any image file, defaults to /var/lib/AccountsService/icons/<yourusername>
```

---

### Post by bvanaerde on 2012-06-03
Does this mean it's not yet possible to add the profile pictures without the terminal? I couldn't find it in the settings.

---

### Post by bvanaerde on 2012-06-03
Ahh, found it. Just had to click on the image placeholder of the account. :)

---

### Post by neo1691 on 2012-12-09
> **bvanaerde said:**
> Ahh, found it. Just had to click on the image placeholder of the account. :)

Thank you!! This reply of yours saved me too! :D

---

