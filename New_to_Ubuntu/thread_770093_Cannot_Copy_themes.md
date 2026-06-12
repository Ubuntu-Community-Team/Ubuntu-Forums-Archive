---
title: "Cannot Copy themes"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by CosmicFlux on 2008-04-27
Hi,

I'm trying to copy a theme into the /use/share/themes directory from my Desktop but when I use:

**sudo cp Tango /usr/share/themes**

I get the message:

**cp: omitting directory 'Tango'**

Does anyone know what this means and what I have to do to get the directory copied?

Cosmic

---

### Post by talsemgeest on 2008-04-27
Yeah, it means that the directory 'tango' is not being copied. This is because when you copy like that it won't go into directories. You can change your command and it should fix your problem:

```
sudo cp -r Tango /usr/share/themes
```

---

### Post by CosmicFlux on 2008-04-27
Thanx!

I looked up the error message on Google (duh! Should have done that to begin with!)

It said the same thing and I now have the theme installed!

Cosmic

---

### Post by talsemgeest on 2008-04-27
Cool, glad I could help!

---

### Post by Perfect Storm on 2008-04-27
If you're in doubt, you can always use **man** and/or **--help** with the command you want to execute. **man** means manual and **--help** is obvious but it's a quickguide compared to **man** which go deeper with explainations etc.

example in your case:

```
man cp
```

```
cp --help
```

---

### Post by CosmicFlux on 2008-04-28
Yeah,
I also found out that **man -k <keyword>** lets you search through the commands for ones that perform tasks relating to the keyword...handy!

I love Linux!

Cosmic

---

