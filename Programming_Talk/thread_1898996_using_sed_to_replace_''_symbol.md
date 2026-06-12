---
title: "using sed to replace '/' symbol"
date: 2011-12-22
forum: Programming Talk
---

### Post by vjd5023 on 2011-12-22
I need the sed command to replace a line of text that contains the forward slash symbol. This causes issues with the sed command because it seperates fields with the '/' symbol. This is the line of code I'm trying to replace with a null space

```
sed -e 's/{v/ CONTENT ( 2874):}//g'
```

Doing this just gives me an error. Anybody know a way to successfully do this?

---

### Post by Arndt on 2011-12-22
> **vjd5023 said:**
> I need the sed command to replace a line of text that contains the forward slash symbol. This causes issues with the sed command because it seperates fields with the '/' symbol. This is the line of code I'm trying to replace with a null space

```
sed -e 's/{v/ CONTENT ( 2874):}//g'
```

Doing this just gives me an error. Anybody know a way to successfully do this?

Yes, you can use any character instead of / to delimit the fields. For example sed -e 's#{v/ CONTENT ( 2874):}##g'

---

