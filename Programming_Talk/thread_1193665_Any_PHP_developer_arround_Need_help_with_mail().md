---
title: "Any PHP developer arround? Need help with mail()"
date: 2009-06-21
forum: Programming Talk
---

### Post by kbb139 on 2009-06-21
I need help from someone who could run the PHP mail() function. Please tell me how exactly have you achieved that?
I have LAMPP 1.7, do I need something else??
I haven`t got domain, I`m using localhost to send the letters.

---

### Post by Reiger on 2009-06-21
Do you have a CLI environment for PHP set up (php-cli or php5-cli or something like that) ? If so you can use php -a to get an interactive PHP shell, which is nice as it allows you to do things like this:
```

php > mail('test@localhost', 'hello world!', 'it works!');
sh: /usr/sbin/sendmail: not found

```

And that may be where your problem is.

---

