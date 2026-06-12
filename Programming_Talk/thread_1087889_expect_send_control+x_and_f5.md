---
title: "expect: send control+x and f5"
date: 2009-03-05
forum: Programming Talk
---

### Post by jure1873 on 2009-03-05
I'm trying to make an init script for a program that doesn't have one. It's got a captive user interface so I wanted to do it in expect. Start the menu, press down twice, send ctrl+x, send f5, wait for it to print complete.

Now the problem is that I don't know how to send special caracters - ctrl+x or f5?

---

### Post by geirha on 2009-03-05
In the terminal you can represent a special character by first hitting Ctrl+v. So do:
```
echo -n '**^X**' | hd 
```
The **^X** which I've marked with bold above, is made by hitting Ctrl+v followed by Ctrl+x. The hd (hexdump) command will print its hex value which is 18.

That means you can send that character from expect with something like ```
send "\x18"
```

Do the same for F5, which produces 5 bytes (it's an escape sequence, 1b is ESC) "\x1b\x5b\x31\x35\x7e"

---

### Post by jure1873 on 2009-03-13
Thank you!!! :)

---

