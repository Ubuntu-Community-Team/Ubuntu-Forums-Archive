---
title: "Where fo Program Files go?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by YoB1U1N1T1U on 2008-07-16
In Ubuntu/Linux, if I install a program (From .deb installer file) where do all the program files go?

I installed the encryption software truecrypt, but i only see a pdf help file in the directory after installation. 

Help
Thanks!

---

### Post by iaculallad on 2008-07-16
> **YoB1U1N1T1U said:**
> In Ubuntu/Linux, if I install a program (From .deb installer file) where do all the program files go?

I installed the encryption software truecrypt, but i only see a pdf help file in the directory after installation. 

Help
Thanks!

Try using the locate terminal command to find that application:

```
locate truecrypt
```

---

### Post by sdennie on 2008-07-16
If you can't find them in the menu, things are generally named the same as the package name.  Try:

```

which truecrypt

```

If that doesn't work, this should tell you all the binaries a package installs:

```

dpkg -L truecrypt | grep bin/

```

---

