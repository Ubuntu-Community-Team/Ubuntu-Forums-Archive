---
title: "How do I make a plugin for a php app?"
date: 2006-08-09
forum: Programming Talk
---

### Post by Peter Mount on 2006-08-09
Hello

I'm currently following a tutorial for developing blog software in php i.e. from the book "Blog Design Solutions".

I'd like to learn how to develop plugins for the php blog later on. What tutorials on the web should I look at?

My web host uses php4.3.11, mysql 4.0.24-standard and apache 1.3.34. On my computer I installed php4.x, mysql 4.1 and apache 2 with the help of the guide at:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Thanks

---

### Post by Kurt` on 2006-08-09
Maybe you can link to the tutorial in question, or elaborate on what a "plugin" is for a PHP script?

Do you mean a reusable section of code that you can include_once() or require_once() ?

---

### Post by Peter Mount on 2006-08-09
> **Kurt` said:**
> Maybe you can link to the tutorial in question, or elaborate on what a "plugin" is for a PHP script?

Do you mean a reusable section of code that you can include_once() or require_once() ?

Hi

The tutorial is in the book that I mentioned, "Blog Design Solutions". 

About the term "plugin", it was a term that somebody I know used to describe part of what they are doing. I don't know how to implement that so that's why I need to ask about it.

Thanks

---

### Post by [h2o] on 2006-08-09
Or check the wordpress sourcecode to see how they implement theirs. They use "hooks" which you can attatch your plugins to. Really smart actually :)

---

### Post by Peter Mount on 2006-08-09
> **'[h2o] said:**
> Or check the wordpress sourcecode to see how they implement theirs. They use "hooks" which you can attatch your plugins to. Really smart actually :)

Thanks for suggesting that. I guess it wouldn't hurt for me to try my hand at making a plugin for WordPress.

Have a good day

---

