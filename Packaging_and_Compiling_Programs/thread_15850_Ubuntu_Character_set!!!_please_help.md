---
title: "Ubuntu Character set!!! please help"
date: 2005-02-17
forum: Packaging and Compiling Programs
---

### Post by twig on 2005-02-17
Hi, im making a program with realbasic 5.5 for Ubuntu and i have a problem with it recognising the return carridge character. i`m making the program for ubuntu on a windows machine, and windows uses the ascii code "13" for the carridge return button, if anyone knows what it is for ubuntu please mail me at [email]anthonyarde@mail.com[/email]
or at [email]anthonyarde@gmail.com[/email]
thanks Anthony.

---

### Post by TheFifth on 2005-06-30
[QUOTE=twig]Hi, im making a program with realbasic 5.5 for Ubuntu and i have a problem with it recognising the return carridge character. i`m making the program for ubuntu on a windows machine, and windows uses the ascii code "13" for the carridge return button, if anyone knows what it is for ubuntu please mail me at [email]anthonyarde@mail.com[/email]
or at [email]anthonyarde@gmail.com[/email]
thanks Anthony.[/QUOTE]
 I don't know if you still need the answer to this question as you asked it so long ago, but in RealBasic you should use the 'EndOfLine' keyword to add a carriage return to a string.

For example:

a = "hello" + EndOfLine + "there"

This way RealBasic will use the correct codes dependant on if it is running on Windows or Linux and you do not need to check what the host OS is.

Hope this helps.

---

