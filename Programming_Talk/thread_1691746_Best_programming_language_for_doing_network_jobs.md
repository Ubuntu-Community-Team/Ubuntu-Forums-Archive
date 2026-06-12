---
title: "Best programming language for doing network jobs?"
date: 2011-02-20
forum: Programming Talk
---

### Post by hakermania on 2011-02-20
Which is the best programming language (supported by Ubuntu (e.g. not VB)) for doing network jobs, such us logging into a website, uploading/downloading content, keeping cookies, etc?


Thanks!:)

---

### Post by MadCow108 on 2011-02-20
as networking is slow any very high level language with a good amount of libraries for this will be sufficient, e.g. python, perl, ruby, ...
I would not recommend lower level languages like C, C++, etc as you are just going to waste development time for little gain.

---

### Post by lisati on 2011-02-20
On a web page, I'd suggest HTML, PHP and MySQL. There's an example here: [http://www.plus2net.com/php_tutorial/content.php](http://www.plus2net.com/php_tutorial/content.php)

---

### Post by juancarlospaco on 2011-02-20
python

---

### Post by ve4cib on 2011-02-20
For website-related stuff your typical LAMP setup is usually the way to go; Linux, Apache, MySQL & Perl/Python/PHP.  That's certainly one of the most common approaches anyway.

An alternative (which does the same thing in the end) is to use Mono/C#, and ASPX.  ASPX does the same thing as PHP really, and your backend processing would be done in C# instead of Perl or Python (or more PHP).  It's certainly less common than a LAMP server in the Linux world, but it will also do the job.

Either one will do what you want, and there are lots of tutorials out there on how to do each one.  Most of the C#/Mono tutorials will be aimed more at Visual Studio/.NET/Windows/IIS development, but the concepts are easily translatable.  LAMP tutorials will be much more "do this, then do this, and now edit this config file like this" walkthroughs since you're already using Linux and (presumably) have Apache installed.

---

### Post by worksofcraft on 2011-02-20
> **hakermania said:**
> Which is the best programming language (supported by Ubuntu (e.g. not VB)) for doing network jobs, such us logging into a website, uploading/downloading content, keeping cookies, etc?


Thanks!:)

IMO Java was designed for this :)

---

