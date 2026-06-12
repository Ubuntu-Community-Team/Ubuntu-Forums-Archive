---
title: "Need help installing a *.bin file"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by vbsudharsan on 2012-03-30
So!
1. I changed the "allow exectuing " from properties.
2. used chmod to change permission, currently the permission is -rwxr-xr-x-
3. then i executed using ./filename.bin
there is no response after that! what should i do?

---

### Post by oldos2er on 2012-03-30
Post moved to its own thread.

---

### Post by TeoBigusGeekus on 2012-03-30
> **vbsudharsan said:**
> So!
1. I changed the "allow exectuing " from properties.
2. used chmod to change permission, currently the permission is -rwxr-xr-x-
3. then i executed using ./filename.bin
there is no response after that! what should i do?

Well, it's been installed.

---

### Post by idoitprone on 2012-03-30
> **vbsudharsan said:**
> So!
1. I changed the "allow exectuing " from properties.
2. used chmod to change permission, currently the permission is -rwxr-xr-x-
3. then i executed using ./filename.bin
there is no response after that! what should i do?

usually when you install a bin file it prompt for you password? Did it do it?
If not, then it may need root permissions

```
sudo ./filename.bin
```if it did then it probably installed

---

### Post by jerome1232 on 2012-03-30
The question is, where did you get your binary and what is it supposed to do?

Unless we know it's expected behavior, we can't really tell you if it worked or not.

---

