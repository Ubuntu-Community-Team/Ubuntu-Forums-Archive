---
title: "Login incorrect"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Stephen_A on 2008-04-30
Just a quick one. I've just installed 7.10 and am getting 'Login incorrect' at the prompt. I'd appreciate any suggestions. 

Thanks

---

### Post by swoll1980 on 2008-04-30
caps lock maybe? or maybe it was on when you set it up? Ubuntu is case sensitive

---

### Post by Stephen_A on 2008-04-30
Positively not. Just running setup again.

---

### Post by coolaj86 on 2008-04-30
You must have mistyped your password or user name.

When you first turn the computer on and you see "Loading GRUB in X seconds..." hit ESC and choose to boot into 'rescue mode'

then 
```
grep '100' /etc/passwd
```
you should see the 'short name' of your user in there on the second line followed by an ':x' and then the 'long name' a bit further down.

then
```
passwd $SHORTNAME
```
and choose a new password

make sure that you log in with your short name and not the long name. It's case-sensitive.

---

### Post by Stephen_A on 2008-04-30
Thanks for going to the trouble of giving this information. I'll give this a try.

---

### Post by coolaj86 on 2008-05-01
and by $SHORTNAME I didn't mean for you to actually put $SHORTNAME, but rather the short form of your user name, fyi. Sorry if I confused you by that.

---

### Post by Stephen_A on 2008-05-01
fyi. Sorry if I confused you by that.[/QUOTE]

No you didn't confuse me. Thanks for the clarification anyway.

---

