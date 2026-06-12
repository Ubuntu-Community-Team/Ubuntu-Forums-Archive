---
title: "dialog inputbox - a default input value"
date: 2013-02-18
forum: Programming Talk
---

### Post by sebastian.s on 2013-02-18
Say i want to create a simple inputbox like this:

```
dialog --inputbox "Please enter a hostname" 10 60
```Is there a way to get a default value already filled in the input field? Say i would like it to say "ubuntu" in the input field. Thanks in advanced :smile:

---

### Post by schragge on 2013-02-18
It's the fourth parameter
```

dialog --inputbox "Please enter a hostname" 10 60 ubuntu

```

---

### Post by sebastian.s on 2013-02-18
> **schragge said:**
> It's the fourth parameter
```

dialog --inputbox "Please enter a hostname" 10 60 ubuntu

```

A that was simple. i should have figured that out myself ](*,)Anyway really appreciate your help.

---

