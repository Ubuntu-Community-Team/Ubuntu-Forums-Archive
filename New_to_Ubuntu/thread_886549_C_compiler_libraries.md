---
title: "C compiler libraries?????"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Windy Peaks on 2008-08-11
Ladies and Gentlemen Of the Forum:

I have downloaded many different C programming programs for the Application window and not one of them recognize the header files.
Example #include <stdio.h> or #include <stdlib.h>

Has anyone figured out how to load the header libraries into their C compiler ???

Thanks in advance
Windy

---

### Post by sharks on 2008-08-11
install gcc

[http://www.codecoffee.com/tipsforlinux/articles/18.html](http://www.codecoffee.com/tipsforlinux/articles/18.html)

search for compile c in linux on google.

---

### Post by Oldsoldier2003 on 2008-08-11
> **Windy Peaks said:**
> Ladies and Gentlemen Of the Forum:

I have downloaded many different C programming programs for the Application window and not one of them recognize the header files.
Example #include <stdio.h> or #include <stdlib.h>

Has anyone figured out how to load the header libraries into their C compiler ???

Thanks in advance
Windy

You might want to install build-essential, these essential libraries and programs are not installed by default on Ubuntu.

```
sudo apt-get install build-essential
```

---

### Post by sharks on 2008-08-11
forgot to say that.......

---

