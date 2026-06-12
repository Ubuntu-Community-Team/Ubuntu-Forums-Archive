---
title: "not able to login"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by alaxander on 2012-06-18
hello
im not able to login into ubuntu admin...i type the password and hit enter, the screen goes black for a second and comes back to the login screen...im able to go into the guest account without any problem's..........btw i dont have a nvidia card ........was workin fine two hours earlier
im using ubuntu 12.04

thanks

---

### Post by kc1di on 2012-06-18
This may work remove the following It will be regenerated when you log in.

```
rm ~/.Xauthority
```

---

### Post by teward on 2012-06-18
> **kc1di said:**
> This may work remove the following It will be regenerated when you log in.
 
```
rm ~/.Xauthority
```
 
That will indeed fix your issue (I had this as well). This bug has existed since release, however I have not seen a bug report yet for dealing with this.

---

