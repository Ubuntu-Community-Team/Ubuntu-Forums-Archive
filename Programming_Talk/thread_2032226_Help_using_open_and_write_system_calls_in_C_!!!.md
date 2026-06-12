---
title: "Help using open and write system calls in C !!!"
date: 2012-07-23
forum: Programming Talk
---

### Post by vikkyhacks on 2012-07-23
[B]void main()
{
write(open("a",1),"Hello",10);
}

[/B]

My teacher taught me this program ... He told me that read and write are system calls used directly from the header. But he did not tell me what the second and third arguments of the open() and write() calls mean..... I searched the internet but there they tell me something like O_RDWD or O_RD (... something) which requires headers. Please explain me the second and third arguments used  here with numbers....

---

### Post by MadCow108 on 2012-07-23
see:
man 2 open
man 2 write

the section 2 in manpages are system calls (see [http://linux.die.net/man/](http://linux.die.net/man/) for the other sections)

---

### Post by trent.josephsen on 2012-07-23
Your teacher sounds like a hack.

---

