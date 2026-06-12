---
title: "trying to upgrade to hardy heron"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by fignig on 2008-09-13
so i was trying to upgrade to hardy heron from my dapper drake cd that i recieved from ubuntu. but it seems that i can't read anything now. everything from the terminal to synaptic package manager the font has changed to little boxes. and i can't read any of them, b/c i don't speak box. i'm trying to figure out how to change all the fonts to w/e or what i need to do to resolve this problem, b/c i kept getting errors when i was trying to upgrade, and it was focused around the fonts. can anyone help me? i'm still on dapper drake, and i was trying to install a burner so i could just d/l the .iso of hardy heron and just install it from a cd. 

btw what is the best program in the repositories or w/e to burn bootable iso images? btw i'm using dapper drake, not hardy heron.

---

### Post by k33bz on 2008-09-13
The only thing I can suggest is a clean install.

The reason I suggest this is, yes the upgrading is easy, and for alot of different people and computers it actually works flawlessly.  But for a few others upgrading can turn into a complete nightmare. I learned the hardway twice now. :)

---

### Post by wolfen69 on 2008-09-13
> **k33bz said:**
> The only thing I can suggest is a clean install.

The reason I suggest this is, yes the upgrading is easy, and for alot of different people and computers it actually works flawlessly.  But for a few others upgrading can turn into a complete nightmare. I learned the hardway twice now. :)

i agree. do yourself a favor and do a clean install. back up your files and format that baby. but that's just my humble opinion.

---

### Post by fignig on 2008-09-13
there's no way to change my font to normal? i'm trying to install a program so i can burn the hardy iso to a cd so i can just install it from the cd. i just need a program in the repositories, something easy to install, sudo apt-get install w/e. i need a program name, and a way to change my font so i can read my terminal/synaptic

---

### Post by k33bz on 2008-09-13
o ok, I am sorry I misuderstood you.

You should be able to go here

SYSTEM> PREFERENCES> APPEARANCE> 

and there is a FONT tab there, you should be able to change it there.

---

### Post by lordadi on 2008-09-13
try ```
sudo apt-get install k3b
``` if you dont mind KDE apps, b/c this burner is, I believe, the best.

Unfortuately, can't help with the font issue.

Lordadi.

---

### Post by k33bz on 2008-09-13
Oh and i dont know about the best, everything is really based on personal preference  I personally love Brasero for burning anything.

---

### Post by fignig on 2008-09-13
> **lordadi said:**
> try ```
sudo apt-get install k3b
``` if you dont mind KDE apps, b/c this burner is, I believe, the best.

Unfortuately, can't help with the font issue.

Lordadi.

i just reinstalled so i just needed the burning program. is that k3b easy to use?

---

### Post by Sef on 2008-09-13
> i just reinstalled so i just needed the burning program. is that k3b easy to use?


It's fairly easy.  But I use Gnome Baker, but so is Brasero.  They both are in Add/Remove.  Just make sure to set Add/Remove to 'All Available Applications'.

Best to try them all out and see what you what you like best.

---

### Post by kansasnoob on 2008-09-14
Brasero is almost foolproof!

```
sudo apt-get install brasero
```

But, it should be there in Hardy, then again with the upgrade I'd follow that command with:

```
 sudo apt-get -f install
```

---

### Post by kansasnoob on 2008-09-14
> **Sef said:**
> It's fairly easy.  But I use Gnome Baker, but so is Brasero.  They both are in Add/Remove.  Just make sure to set Add/Remove to 'All Available Applications'.

Best to try them all out and see what you what you like best.

True! So many choices! So little time:(

---

