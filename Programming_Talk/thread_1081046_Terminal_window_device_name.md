---
title: "Terminal window device name"
date: 2009-02-26
forum: Programming Talk
---

### Post by c.pergiel on 2009-02-26
I have a simple C program that runs in a terminal window and processes input from stdin.
I want to talk to the user (printing and getting keyboard input) even if stdin is redirected to a file.
I'm thinking I need a device name. Does anyone know what that name would be?
"console" doesn't work, and neither does "/dev/console".
I can compile and run the same program in a DOS box under windows using the name "con".

---

