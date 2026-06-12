---
title: "How to use GCC?"
date: 2008-12-25
forum: Programming Talk
---

### Post by ashokmkd on 2008-12-25
I have c programming experience in windows but i am new to linux.
I installed Ubuntu 8.04 then made a sample.c in home directory and typed in terminal
-> gcc -c sample.c

output says stdio.h is not found.
similar is the case with all header files.
Shall i install some additional libraries?

---

### Post by wd5gnr on 2008-12-25
What does sample.c look like? Do you have a /usr/include/stdio.h? Have you installed the build-essentials package?

To compile a simple program like this you probably want:

gcc -o sample sample.c

But your command should have worked (producing sample.o which still needs linking).

---

### Post by ashokmkd on 2008-12-25
its a simple helloworld example i wrote for testing gcc. i haven't installed any packages. i searched the filesystem but stdio.h is not there.

---

### Post by croto on 2008-12-25
Probably you're missing the build-essential package, it provides compilers, headers, that you'll need to compile anything. To install type:
```

sudo apt-get install build-essential

```

for mor info check:[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by ashokmkd on 2008-12-25
thank you both. let me try it

---

### Post by monkeyking on 2008-12-25
consider using other compiler options like

-Wall this will turn on all warnings
-pedantic refused to compile "bad" code
-ansi follow the standard

---

### Post by slavik on 2008-12-25
Have you looked at the stickies? one of them contains a FAQ that tells you all of this and so much more.

---

