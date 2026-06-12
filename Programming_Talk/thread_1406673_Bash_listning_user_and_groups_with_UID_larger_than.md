---
title: "Bash listning user and groups with UID larger than N question"
date: 2010-02-14
forum: Programming Talk
---

### Post by terrrorr on 2010-02-14
Hi you all,

I was wondering is there any proper way to list all users/groups which UID/GID is larger than N value with bash. As you all know Ubuntu uses default value 1000 and larger to new users/groups and therefore it would be nice to list all users but leave all system accounts/groups "alone". 

If some one wants to know why... well I have colleagues which are more familiar with graphical interfaces (Read Windowzzz).

Thanks for advance

---

### Post by DaithiF on 2010-02-14
not sure about 'proper way', but this would do it:
```
cat /etc/passwd | awk -F':' '{ if($3 >= 1000) print $0 }'
```

---

### Post by terrrorr on 2010-02-14
Thank you very much. Works like a charm. I'll just have to learn more about awk. \\:D/

---

### Post by DaithiF on 2010-02-14
[FONT=monospace]i realised i'm guilty of a useless use of cat here, this is better
[/FONT]```
awk -F':' '{ if($3 >= 1000) print $0 }' /etc/passwd
```[FONT=monospace]

[/FONT]

---

