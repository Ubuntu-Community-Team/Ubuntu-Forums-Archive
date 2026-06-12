---
title: "Clean URL's"
date: 2009-04-25
forum: Programming Talk
---

### Post by gjoellee on 2009-04-25
Hey, I am trying to get clean URL's on my website. I have tried to follow many tutorials, but it does not help.

Here is how my website is:
[www.example.com/index.php?c=about](www.example.com/index.php?c=about)

This is how I want it to be:
[www.example.com/about](www.example.com/about)

I need a secondary level of clean URL's as well:

Here is how my website is:
[www.example.com/index.php?c=about/ubuntu](www.example.com/index.php?c=about/ubuntu)

This is how I want it to be:
[www.example.com/about/ubuntu](www.example.com/about/ubuntu)

NOTE: I am using PHP and I use Apache


Thanks for any help...

---

### Post by simeon87 on 2009-04-25
You need to have mod_rewrite on your server. In the .htaccess file, you can add (if that file doesn't exist you can create it in the root directory of the website):

```

# Turing mod_rewrite on
RewriteEngine On

# Set the root directory as base directory
RewriteBase /

# The rewriting rules
RewriteRule ^about/ubuntu$ index.php?c=about/ubuntu
RewriteRule ^about$ index.php?c=about

```

You can also abstract from this by using regular expressions but let's try to get this working first ;)

---

