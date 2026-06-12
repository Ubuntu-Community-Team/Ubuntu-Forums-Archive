---
title: "php: how to check if a site is down and redirect..."
date: 2006-10-30
forum: Programming Talk
---

### Post by simone.brunozzi on 2006-10-30
Hi there,
I have a problem:

sometimes my website "Foo" is down;
the webdomain "Bar" point to another server, that is always up. On that server, however, I can't install the software I'm using on "Foo".
So, I use a redirect from the website root folder on "Bar" to the "Foo" directory.

When the "Foo" is down, I would like to redirect to a courtesy page, using php.
In other words, I need to write a PHP script that checks if a website is reachable and then, if not, redirects to a page.

Any help on that?

Thanks

---

### Post by nimrod_abing on 2006-10-30
> **simone.brunozzi said:**
> Hi there,
I have a problem:

sometimes my website "Foo" is down;
the webdomain "Bar" point to another server, that is always up. On that server, however, I can't install the software I'm using on "Foo".
So, I use a redirect from the website root folder on "Bar" to the "Foo" directory.

When the "Foo" is down, I would like to redirect to a courtesy page, using php.
In other words, I need to write a PHP script that checks if a website is reachable and then, if not, redirects to a page.

Any help on that?

Thanks

You can use the [fsockopen()]("http://www.php.net/manual/en/function.fsockopen.php") function. Set the timeout parameter to a reasonable value, say 10 seconds. If fsockopen() returns FALSE, then check errno and errstr and act accordingly on the results.

---

### Post by simone.brunozzi on 2006-11-07
Sorry for the late answer!

Thanks, it seems to work!!

Simone

---

