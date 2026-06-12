---
title: "python input question"
date: 2008-02-02
forum: Programming Talk
---

### Post by Mr.popo on 2008-02-02
Why is it better to use int(raw_input("..")) than input("..").

cheers.

---

### Post by LaRoza on 2008-02-02
raw_input() will return a string. input() takes commands.

If you have a string, nothing bad can happen, and you can safely check it. input() will allow commands to be executed.

[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

User input is the hardest thing in programming to do. Users are...fickle.

In Python 3000, raw_input will be renamed "input()" and the current input() function will be no longer used in that way. You will have to use eval(input()) for the same effect.

---

### Post by Mr.popo on 2008-02-02
> **LaRoza said:**
> raw_input() will return a string. input() takes commands.

If you have a string, nothing bad can happen, and you can safely check it. input() will allow commands to be executed.

ok, thankyou.

---

### Post by LaRoza on 2008-02-02
> **Mr.popo said:**
> ok, thankyou.

I added more, including a link to an article on user input.

---

### Post by Mr.popo on 2008-02-02
Yeah, I saw. Thanks for the link.

---

