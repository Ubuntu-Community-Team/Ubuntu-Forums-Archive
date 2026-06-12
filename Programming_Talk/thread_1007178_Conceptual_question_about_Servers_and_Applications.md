---
title: "Conceptual question about Servers and Applications"
date: 2008-12-10
forum: Programming Talk
---

### Post by Maratonda on 2008-12-10
Hello,

this is a very general question, and it probably tells you about my limited knowledge in this field. But that's ok!

Let's  say I have a machine with Ubuntu server on it, and it's setup so that it works as a server (i.e. it is connected to the internet, etc)

Now, let us say I install a given application on the server such that if I execute the following command

```
foo bar.pdf
```

it creates a pdf file.

So my question is, can I have a script that allows the users to execute this script from a simple PHP (or anything) page, so that, basically, they get the .pdf file created with the previous command?

Also, is it actually possible to install an application on a server very much like I can do in ubuntu?

---

### Post by tshrinivasan on 2008-12-10
1. If you can run in a command as a normal user, you can call it from php too.

see here,
[http://www.php-mysql-tutorial.com/qna/detail/php-execute-shell-command.php](http://www.php-mysql-tutorial.com/qna/detail/php-execute-shell-command.php)


2. ubuntu server also has the same package management system, apt-get.
so you can use it.

---

