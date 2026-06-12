---
title: "%computername% equivalent"
date: 2008-06-30
forum: Programming Talk
---

### Post by Sub101 on 2008-06-30
I expect this is a very simple thing to do but I have been Googleing this for some time and can not find the answer.

All I want to do is include in a path the computer name, without being specific to the computer. So I use the program on any of my Ubuntu machines and it all works. I know in Windows %computername% works.  

Thanks for your help.

---

### Post by LaRoza on 2008-06-30
> **Sub101 said:**
> I expect this is a very simple thing to do but I have been Googleing this for some time and can not find the answer.

All I want to do is include in a path the computer name, without being specific to the computer. So I use the program on any of my Ubuntu machines and it all works. I know in Windows %computername% works.  

Thanks for your help.

```
~$cat /etc/hostname
```

In *nix, everything is a file.

---

### Post by TheEndIsNear on 2008-06-30
If you want to create a file with the machine name in it then you would use $HOSTNAME.

---

### Post by LaRoza on 2008-06-30
> **TheEndIsNear said:**
> If you want to create a file with the machine name in it then you would use $HOSTNAME.

Just figured that out as well.

I don't know what language you are using, but usually there is a "getenv" function for this.

---

### Post by Sub101 on 2008-06-30
Cheers. Going to use the $HOSTNAME I think. Thanks for your help

---

