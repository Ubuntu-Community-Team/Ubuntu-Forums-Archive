---
title: "read system call."
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Ankitshah on 2012-06-14
Hello everyone,

I was wondering if there is any way to limit the user input to terminal during "read" system call.

When the canonical mode is deactivated (~ICANON) we can specify the minimum characters to be read by assigning c_cc[VMIN] a positive integer value.

But, can we do the same when canonical mode is activated ??

I am coding an application that ask the user for a username, i want to limit the username to 25 characters.

Thanks.

---

