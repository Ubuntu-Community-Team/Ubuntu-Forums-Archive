---
title: "how do i locate the folder path of a particular folder using terminal?"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2013-01-14
how do i locate any folder/file path via terminal in ubuntu 10.04?

---

### Post by john rosswrock on 2013-01-14
> **tojonukokhadush said:**
> how do i locate any folder/file path via terminal in ubuntu 10.04?

 you can use pwd command to see your current directory u r working in... or  visit the link below:  [https://help.ubuntu.com/10.04/basic-commands/C/files-directories-commands.html](https://help.ubuntu.com/10.04/basic-commands/C/files-directories-commands.html)

---

### Post by tojonukokhadush on 2013-01-14
ha ha! it was just witty ;-) silly me.
thanks a lot anyway.

---

### Post by tojonukokhadush on 2013-01-14
hey!! this was helpful only when i am already inside a folder! the problem is that- i know a folder name say "media". i now just want to know how to reach there or find its path and that too using a terminal!! any idea???

---

### Post by Abhinav Kumar on 2013-01-15
Hi
> **tojonukokhadush said:**
> hey!! this was helpful only when i am already inside a folder! the problem is that- i know a folder name say "media". i now just want to know how to reach there or find its path and that too using a terminal!! any idea???

Just type the following code in terminal

```

sudo find / -name media -xtype d | more

```
This will search for folder named media.

Regards,
Abhinav

---

