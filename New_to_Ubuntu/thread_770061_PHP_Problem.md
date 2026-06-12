---
title: "PHP Problem"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by twp_twm on 2008-04-27
Having installed XAMPP 1.6.6 i now find that i am unable to store php files into the htdocs folder /opt/lampp/htdocs  because i don't have the necessary permissions to save the file. Isn't there a way around this or would i have to use sudo everytime?

---

### Post by LaRoza on 2008-04-27
> **twp_twm said:**
> Having installed XAMPP 1.6.6 i now find that i am unable to store php files into the htdocs folder /opt/lampp/htdocs  because i don't have the necessary permissions to save the file. Isn't there a way around this or would i have to use sudo everytime?

This will make it yours:
```

chown $USER:$USER /opt/lampp/htdocs

```

XAMPP is only meant for testing, not production.

---

### Post by quinnten83 on 2008-04-27
you could probably change the owner of the folder so you could access it freely. Although I am uncertain what the consequence could be in this case.
Try

```
chown [new_owner] [folder]
```

perhaps that will work.

---

### Post by twp_twm on 2008-04-27
I am only learning PHP via XAMPP but big thanks for both replies and the code.

---

### Post by quinnten83 on 2008-04-27
> **twp_twm said:**
> I am only learning PHP via XAMPP but big thanks for both replies and the code.

i' dgowith bhodi'scode. i don't do syntax well.

---

### Post by twp_twm on 2008-04-27
Diolch yn fawr Quinnten

---

