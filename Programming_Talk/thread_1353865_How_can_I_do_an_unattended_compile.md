---
title: "How can I do an unattended compile?"
date: 2009-12-13
forum: Programming Talk
---

### Post by NFblaze on 2009-12-13
Hey, just got a quick question on unattended compiling. 

So the default compile order is 

1) *./config*
2) *make*
3) **sudo*** make install*

Well, if I'm not at my PC how can I make sure it automatically knows the password for step 3?

I've tried

*./config ; make ; sudo make install ; read "mypassword"* 

once but that didnt work.

Thanks for any help

---

### Post by Physical Hook on 2009-12-13
[LIST=1]
[*][COLOR=gray]./configure [/COLOR]not [COLOR=gray]./config[/COLOR][COLOR=black].[/COLOR]
[*]If you don't know the password, what's the point of asking for it with *read* ?
[/LIST]

---

### Post by sisco311 on 2009-12-13
```
sudo bash -c "\
su **username** -c ./configure && \
su **username** -c make && \
make install"
```

---

### Post by NFblaze on 2009-12-14
Thank you very much sisco311, I will try to test this out. Thanks again for posting something helpful.

---

