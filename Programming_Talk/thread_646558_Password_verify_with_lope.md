---
title: "Password verify with lope"
date: 2007-12-21
forum: Programming Talk
---

### Post by coskierken on 2007-12-21
Can anyone help me with this?  I want to use the following code to enter my sudo password and loop until the correct password is entered.  

```
PASSWORD=`zenity --title='Password' --text='Please enter your password' --entry`
```

---

### Post by engla on 2007-12-21
I'm sorry to go against your plan, but can't 'gksu' do what you want in this case for you? (gksu should be used like sudo, it opens a window where you put in your password).

---

### Post by coskierken on 2007-12-21
Thanks Engla, but I don't want to use gksu in this case.

Any other ideas about how I can use this code to loop until the correct password is entered?

thanks

---

### Post by coskierken on 2007-12-21
bumping

---

### Post by geirha on 2007-12-22
I'd have to agree with engla. gksu/gksudo is much better to use as they steal focus from everything else. Here's such a loop using gksudo: 
```
while ! gksudo cat /dev/null; do
  echo "nope"
done
echo "authenticated"

```

You can achieve something similar with zenity, but I must stress that using gksudo is a lot safer.
```
while ! zenity --entry --hide-text| sudo -S cat /dev/null >/dev/null; do
  echo "nope"
done
echo "authenticated"

```

---

