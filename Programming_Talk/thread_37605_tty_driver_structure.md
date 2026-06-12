---
title: "tty_driver structure"
date: 2005-05-27
forum: Programming Talk
---

### Post by daniminas on 2005-05-27
Hello..

on a tty_driver struct, exit the field write:

int write(tty_driver, char buff, int conut) (or something like this)...

Reading the tty_driver.h, there says about write():
'The buffer message can come form a kernel space or form a user space...'
¿how can i know when come from a kerner or user space?... ¿it's clare?...  i am really conffusse

Thanks verry much

Danielle

---

### Post by daniminas on 2005-05-28
nothing?

---

### Post by toojays on 2005-05-28
I think what it means is that it depends on the tty which is open. If the tty has kernel level drivers, then the message will come from kernel space. But if the tty is a virtual device provided by a userspace program, the message will come from userspace.

Of course, this is just a guess. I don't know if there are any userspace ttys in practice.

From your application's point of few, it doesn't matter whether the message is from kernelspace or userspace, does it?

---

### Post by daniminas on 2005-05-31
Yes matter because is for a communication 'thing' connected in the serial port... something like a modem, but it doesn't.. i will poste the code where i've the problem and where i have to know forme who come the 'data',,

Thanks for your answer.

---

