---
title: "pidgin"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by texas.chef94 on 2008-07-12
New to Linux, new to Ubuntu and first post to forum. I researched documentation and found nothing that mirrors my concern. Using program manager I loaded pidgin brought to the desk top double clicked nothing. 
Went to applications internet+pidgin same results. Would appreciate any suggestions, or leads to documentation that might correct this inability to access. I am 76 and having an absolute ball with ubuntu 8.04.

Allen Meyers
Retired Chef
Texas

---

### Post by overdrank on 2008-07-12
> **texas.chef94 said:**
> New to Linux, new to Ubuntu and first post to forum. I researched documentation and found nothing that mirrors my concern. Using program manager I loaded pidgin brought to the desk top double clicked nothing. 
Went to applications internet+pidgin same results. Would appreciate any suggestions, or leads to documentation that might correct this inability to access. I am 76 and having an absolute ball with ubuntu 8.04.

Allen Meyers
Retired Chef
Texas

Hi and welcome, could you start pidgin in the terminal and post any errors?
The terminal is located under applications, accessories.

---

### Post by Dr Small on 2008-07-12
So, you are saying, that pidgin is not launching?
Maybe we should see what the error output is.

Open a terminal, Applications > Accessories > Terminal and type in the terminal:
```
pidgin
```

If it spits out any errors, please post them here in [noparse]```

```[/noparse] tags.

Thanks,
Dr Small

---

### Post by Dutch70 on 2008-07-12
is it not showing up in the upper right hand corner, cause after you load it, you have to click on the little pidgin icon on the right to see anything. it should be a little green circle, covering a piece of paper or something.

---

### Post by bab1 on 2008-07-12
From the terminal try ```
ps -ef | grep pidgin
```

If a line shows with the process OTHR that the grep pidgin, then pidgin is running.

There should be an icon near the calendar and the little greeen icon for shutdown/logoff.

---

