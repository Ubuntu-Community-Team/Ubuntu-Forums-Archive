---
title: "unlock root folder in the file manger"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Pd456 on 2012-01-12
I'm running Puredyne an ubuntu hybrid which is a bit different. 
 I want to unlock the root and have access to the disk in the file manager, I'm not worried about security since I'm the only one using the system.

 How do I do that?

 I remember it being very simple in Dyne:bolic.  It would be nice if It prompted me for the password in the file manager but unlocked is good.

Thank you.

---

### Post by Double.J on 2012-01-12
> **Pd456 said:**
> I'm running Puredyne an ubuntu hybrid which is a bit different. 
 I want to unlock the root and have access to the disk in the file manager, I'm not worried about security since I'm the only one using the system.

 How do I do that?

 I remember it being very simple in Dyne:bolic.  It would be nice if It prompted me for the password in the file manager but unlocked is good.

Thank you.

Hi there, if you want one time root access to nautilus (or whichever file manager you're using)

```

gksudo nautilus

```
nb if you're using KDE it'll be "kdesudo"

<snip - see [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) >
:)

---

### Post by lisati on 2012-01-12
There's a reason for things being the way they are in Ubuntu, please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Double.J on 2012-01-12
Apologies lisati, I came to Ubuntu from debian and SUSE where su is more common than sudoers, I didn't mean to breach forum policy, though I do ofcourse see the sense in this rule and will be more careful in future :-#

---

### Post by lisati on 2012-01-12
> **gnu/mirow said:**
> Apologies lisati, I came to Ubuntu from debian and SUSE where su is more common than sudoers, I didn't mean to breach forum policy, though I do ofcourse see the sense in this rule and will be more careful in future :-#

That's OK :)

---

