---
title: "shell script"
date: 2006-09-04
forum: Programming Talk
---

### Post by Zagor Te Nej on 2006-09-04
Hi!

I got a very simple question. This is a situation: I made a simple shell script for connecting to the internet (ADSL) and every time I want to connect   to net, shell script ask me for password in terminal window. Is there a way to insert password into shell script? I asking this because of my wife and son. They don't like typing passwords :roll: 

Thanks in advance, Z

Ubuntu 6.06 LTS
Kernel 2.6.15-26-386

---

### Post by x64Jimbo on 2006-09-04
Why do you need a script? You're not on dialup - shouldn't you be connected automatically?

---

### Post by Zagor Te Nej on 2006-09-04
No, because connection on system boot didn't work and I don't know why (I'm not linux administrator or programmer). In pppoeconf seems that everything is OK but when system starts you cannot surf. That is why I need a script.

---

### Post by cwaldbieser on 2006-09-04
> **Zagor Te Nej said:**
> No, because connection on system boot didn't work and I don't know why (I'm not linux administrator or programmer). In pppoeconf seems that everything is OK but when system starts you cannot surf. That is why I need a script.

Maybe you could make your shell script run at the end of the boot up process.      The man page for "update-rc.d" should give you some background info.

---

### Post by x64Jimbo on 2006-09-04
Can you post the script that you're running? Also, I have the feeling that all this would be solved if you had a router between you and the modem. If you have one of those, you'll be in good shape.

---

### Post by ifokkema on 2006-09-06
If all else fails, and you turn out to need a script in the end either way, you can try the 'expect` package to generate a script that sends the password automatically.

---

### Post by %hMa@?b&lt;C on 2006-09-06
i wrote a guide for your exact predicament
[http://ubuntuforums.org/showthread.php?t=183062](http://ubuntuforums.org/showthread.php?t=183062)

---

