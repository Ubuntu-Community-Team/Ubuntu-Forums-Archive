---
title: "regexp help"
date: 2009-08-13
forum: Programming Talk
---

### Post by Ascenti0n on 2009-08-13
I'm developing a small website, mainly html with some added PHP.

can someone tell me what the regexp is to delete the file extensions, ie ".php". Basically al my files end in .php and I don't want that showing on the URL.

While I'm asking, I'd also like to know how to change "index" to "home". I'm currently trying to learn regexp but I'm having trouble getting my head around it for some reason.

---

### Post by Mirge on 2009-08-13
You can make Apache parse .html files as PHP files, if you wanted to hide the PHP extension and instead use a .html extension.

In your .htaccess file:

AddType application/x-httpd-php .php .htm .html
AddHandler x-httpd-php .php .htm .html

If you are trying to use Apache's mod_rewrite, see:

[http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html)

If I'm totally off-base, provide more details please.

---

### Post by Ascenti0n on 2009-08-13
What I'm trying to do is strip the file extensions from the url, for example:

[www.domain.com/anypage.php](www.domain.com/anypage.php)

rewritten to

[www.domain.com/anypage](www.domain.com/anypage)

FYI, The only info that will be passed on the URI will be form data.

---

### Post by Mirge on 2009-08-13
> **Ascenti0n said:**
> What I'm trying to do is strip the file extensions from the url, for example:

[www.domain.com/anypage.php]("http://www.domain.com/anypage.php")

rewritten to

[www.domain.com/anypage]("http://www.domain.com/anypage")

FYI, The only info that will be passed on the URI will be form data.

[www.domain.com/anypage](www.domain.com/anypage) would be treated as a directory... the same as [www.domain.com/anypage/index.html](www.domain.com/anypage/index.html) (assuming index.html is your DirectoryIndex if using apache).

---

### Post by johnl on 2009-08-13
It sounds like you know this already but you can accomplish this with mod_rewrite.  Off the top of my head I can't come up with the exact regex you need, but something like this...

.htaccess (with mod_rewrite enabled)
```

RewriteEngine on

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^\./]+)$ $1.php

```

If the request doesn't mach an existing file or directory, and it consists of a string containing anything except a period or forward slash, translate that to <target>php

Keep in mind that we aren't translating "foo.php" to "foo", we are translating what the user types in or gets linked to ([www.example.com/foo](www.example.com/foo)) to the actual path to use to display the contents ([www.example.com/foo.php](www.example.com/foo.php)).  This is why it might seem 'backwards.'

Play around with it and see what you can come up with.

---

### Post by Ascenti0n on 2009-08-14
Your Regex worked a treat, even with commenting out the two conditions. I don't know what the conditions mean yet, but I'm going to set time aside to learn soon.

thanks

---

