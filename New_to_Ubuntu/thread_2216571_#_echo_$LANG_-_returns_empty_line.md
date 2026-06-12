---
title: "# echo $LANG - returns empty line"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2014-04-12
Hi all, 

my 

# echo $LANG 

returns empty line. How do I set it?

---

### Post by bapoumba on 2014-04-13
What does **locale** return ?

---

### Post by whitesmith on 2014-04-13
> **Marchello_Lippi said:**
> Hi all, 

my 

# echo $LANG 

returns empty line. How do I set it?Any line starting with a hash tag is interpreted as a comment. This will give you what you are after:```
echo $LANG
```

---

### Post by bapoumba on 2014-04-13
> **whitesmith said:**
> Any line starting with a hash tag is interpreted as a comment. This will give you what you are after:```
echo $LANG
```

Good point, I assumed they were in a root environment :)

---

