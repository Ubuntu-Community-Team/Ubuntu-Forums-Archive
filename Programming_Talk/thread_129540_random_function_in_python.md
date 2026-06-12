---
title: "random function in python"
date: 2006-02-14
forum: Programming Talk
---

### Post by diffuser78 on 2006-02-14
I want to use random function but looks like this is not as trivial as in C or java.

I tried using whrandom class and randint method in it but Eric gave a message that its been deprecated.

I wat to assign a random value between say 0 and 100. I do the following. But get an error. What is the correct way of doing it.

```

x = int(math.random() * 100)

```

Thanks

---

### Post by WelterPelter on 2006-02-14
random.randint(0,100)

---

