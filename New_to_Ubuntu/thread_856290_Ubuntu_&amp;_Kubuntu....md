---
title: "Ubuntu &amp; Kubuntu..."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by CERNYSMRT on 2008-07-11
well tried to install both.. got the same error for both..
spent 5+ hours researching among tens of thousands of threads 
users posted with problems....  these experiences have both made 
Windows XP look great.... sorry... but xp took less than 45 min to install.. and I had no errors or nothing.

I am not totally shut off to the linux thing.. and I would like to run it cause I am not that big of a fan of microshaft..

---

### Post by Inxsible on 2008-07-11
> **CERNYSMRT said:**
> well tried to install both.. got the same error for both..
spent 5+ hours researching among tens of thousands of threads 
users posted with problems....  these experiences have both made 
Windows XP look great.... sorry... but xp took less than 45 min to install.. and I had no errors or nothing.

I am not totally shut off to the linux thing.. and I would like to run it cause I am not that big of a fan of microshaft..So are you asking for help or just ranting?

If the former, then what are the errors that you got?

Did you follow the best practices for burning the CD images like 4x speed or less etc?

---

### Post by Canis familiaris on 2008-07-11
Calm down and describe what exact problems you are facing.

---

### Post by Cypher on 2008-07-11
Start with the LiveCD for Ubuntu or Kubuntu and see how things go first..this will give you an early indication of any issues that you might have to deal with..

Post the specific errors you got and we might help.

---

### Post by CERNYSMRT on 2008-07-11
It's the sata  i/o error message 

ata3:failed to indentify (I/O error err_mask=04)
ata3:failed to recover some devices
ata3.00: qc timeout (cmd 0exec)

and now i got to the prepare partitions gui menu and it shows nothing.

---

### Post by Xerp on 2008-07-11
Sounds like a hardware issue. Which drives and motherboard do you have?

---

### Post by avtolle on 2008-07-11
It sounds to me like use of a boot option is in order to try to get around the SATA issue. First, read this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) especially the part about how to add boot options on booting to install. Next, try this option: all_generic_ide to be entered on the boot line in the same manner as that used as an example in the link, and see if you can get around the error. Good luck.

---

### Post by Inxsible on 2008-07-11
> **Xerp said:**
> Sounds like a hardware issue. Which drives and motherboard do you have?Can't be since the op said that he installed XP on it unless he tinkered with the hardware between those two installs.

---

### Post by Xerp on 2008-07-11
> **Inxsible said:**
> Can't be since the op said that he installed XP on it unless he tinkered with the hardware between those two installs.

I've had systems with "quirks" that only show up under certain conditions.

---

