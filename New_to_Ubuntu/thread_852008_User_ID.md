---
title: "User ID"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by ububaba on 2008-07-07
This must be the silliest question. How do I find my [COLOR="Magenta"]User ID[/COLOR]?

---

### Post by hyper_ch on 2008-07-07
If you are the first user created upon installation your UID is 1000

otherwise
```

cat /etc/passwd | grep USERNAME

```

---

### Post by sayakb on 2008-07-07
Err...
```
glade@Mean-Machine:~$ cat /etc/passwd | grep USERNAME
glade@Mean-Machine:~$ 

```So I can assume my UID is 1000?

---

### Post by t0p on 2008-07-07
Click on **System > Administration > Users and Groups**. Select your user name from the list, and click on **Properties**.  You'll find your User ID under the **Advanced** tab.

---

### Post by ububaba on 2008-07-07
> **hyper_ch said:**
> If you are the first user created upon installation your UID is 1000

otherwise
```

cat /etc/passwd | grep USERNAME

```

Thanks mate.

---

### Post by sayakb on 2008-07-07
Please mark the thread as solved..

---

### Post by decoherence on 2008-07-07
*echo $UID* works also

---

### Post by Vivaldi Gloria on 2008-07-07
Simplest is

```
id
```

---

### Post by hyper_ch on 2008-07-07
> **decoherence said:**
> *echo $UID* works also

> **Vivaldi Gloria said:**
> Simplest is

```
id
```

if you want the UID of the current logged in user ;)

---

### Post by t0p on 2008-07-07
This is one of the things I love about Linux... there always seem to be several ways you can do something.

---

### Post by Vivaldi Gloria on 2008-07-07
> **hyper_ch said:**
> if you want the UID of the current logged in user ;)

Then use

```
id username
```

---

### Post by hyper_ch on 2008-07-07
that's not geeky enough ;)

---

### Post by Vivaldi Gloria on 2008-07-07
> **hyper_ch said:**
> that's not geeky enough ;)

:-)

---

### Post by hyper_ch on 2008-07-07
I didn't know about the "id" command ;)

---

### Post by Vivaldi Gloria on 2008-07-07
> **hyper_ch said:**
> I didn't know about the "id" command ;)

Yeah, I understood that. Even the mighty Local Shadow Agent #1 has more to learn in the ways of linux. :-)

---

### Post by hyper_ch on 2008-07-07
there are still many things I have no clue about ;) I just like to pretend that I know everything ;)

---

