---
title: "fast cgi vs. PHP Precompiler"
date: 2008-01-23
forum: Programming Talk
---

### Post by yeehi on 2008-01-23
What is the difference between these things? 

Which PHP precompiler is the best to use?

---

### Post by jpeddicord on 2008-01-23
You can't really compare them; FastCGI is a way to *run* PHP/CGI apps, while a PHP precompiler/optimizer stores cached PHP files to speed things up.

FastCGI (or fcgid maybe) lets you run a PHP process in cgi mode, usually as a separate process from Apache. This enables you to do things such as suexec for execution, which basically means that you can run scripts as the same user they were made by. It's a major pain to configure though (suexec) so dedicate some time to it if you really want it.

A PHP accelerator/precompiler does just that: it precompiles your PHP files to that PHP doesn't have to at runtime. This is really only useful for high traffic sites; in most cases no accelerator is needed. I've heard good things about Turk MMcache, though I cannot vouch for it myself having not tried it.

Jacob

---

