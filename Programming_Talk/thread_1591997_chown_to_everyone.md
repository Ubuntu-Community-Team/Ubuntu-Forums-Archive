---
title: "chown to everyone"
date: 2010-10-10
forum: Programming Talk
---

### Post by huangyingw on 2010-10-10
hello,
    Sorry for a naive and hurry question. I have struggled in nightmare with git permission these days. 
    I have checked that my local one has write rights to that remote samba share. So, the only remaining thing is the chown. And I remember that after running "chown -R huangyingw *", my local repository failed to push back.
    I have run chmod -R 777 in remote repository, but , still git prompts me no permission.
    So, I would like to run something like "chown nobody:nobody -R *" to grant the these repositories to everyone, but shell prompts me "invalid usergroup nobody".
    Could someone tell me how to "chown to everyone"?

---

### Post by luvshines on 2010-10-10
Well I don't really understand your question :)

But for chown, shouldn't it be:
```
chown nobody:nogroup -R <path>
```

---

### Post by huangyingw on 2010-10-10
> **luvshines said:**
> Well I don't really understand your question :)

But for chown, shouldn't it be:
```
chown nobody:nogroup -R <path>
```
Thanks, what I want is exact you provide. This correct me from the result of "nobody:nobody" from google..
Yes, even me , don't understand what I am saying. 
I just say a lot to describe whatever effort I have done to investigate my trouble...

---

### Post by luvshines on 2010-10-10
I was able to beat Google, Cool :guitar:

Gud that your issue is resolved, though it didn't make sense to both of us :P

**Newayz, do remember to mark it SOLVED**

---

### Post by huangyingw on 2010-10-10
> **luvshines said:**
> I was able to beat Google, Cool :guitar:

Gud that your issue is resolved, though it didn't make sense to both of us :P

**Newayz, do remember to mark it SOLVED**
yes, thank you all. My issue is still alive, I will continue to struggle with it. Welcome to help me in my later thread. I have to go to bed, for I have to work tomorrow:). I will continue at my leisure time.

---

