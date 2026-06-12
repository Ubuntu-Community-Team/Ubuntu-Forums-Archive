---
title: "When a PHP error makes you blink twice...."
date: 2007-09-02
forum: Programming Talk
---

### Post by jdong on 2007-09-02
Well, made a little typo in my network's iptables frontend on my gateway, and got this message back from PHP:

```
Parse error: unexpected T_PAAMAYIM_NEKUDOTAYIM in /sites/lanadmin/iptables.php line 44
```


I just woke up and was caught quite startled by the message.... first thing I went to do was check all my locale settings to make sure I wasn't in Hebrew or something.

Seriously, would it have killed them to call it T_DOUBLE_COLON? :lolflag:

---

### Post by darsu on 2007-09-02
Well, I think I read somewhere that Python 3 will have Unicode variable names. If it's indicating a trend, we may be headed for interesting times in terms of error messages.

---

### Post by Wybiral on 2007-09-02
lol, [Paamayim Nekudotayim](http://en.wikipedia.org/wiki/Paamayim_Nekudotayim).

I agree, "double colon" seems like a more logical solution to naming it. That's actually the first time I've ever seen it called that (and I use it constantly in C++).

---

### Post by jdong on 2007-09-02
Interestingly, looking at PHP's source code, the token parser totally understands T_DOUBLE_COLON... just I guess they kept T_PAAMAYIM_NEKUDOTAYIM there as a joke :)

That must be a startling error to get for a php newcomer :D

---

### Post by pmasiar on 2007-09-02
> **darsu said:**
> Well, I think I read somewhere that Python 3 will have Unicode variable names. If it's indicating a trend, we may be headed for interesting times in terms of error messages.

For Py3K libraries, standard stays ASCII only, and english only, so no worries -)

---

