---
title: "mod python"
date: 2008-04-07
forum: Programming Talk
---

### Post by raddmadd on 2008-04-07
Hey guys, I'm having problems configuring mod_python with apache2.

When I go to the directory, say for instance localhost/asdf.py, it says the file cannot be found (Obviously the problem is that asdf.py does exist)

I followed this post:

[http://ubuntuforums.org/showpost.php?p=792999&postcount=3](http://ubuntuforums.org/showpost.php?p=792999&postcount=3)

So the files that I changed are as those files in that post.

I read around a bit and seems others have/had the same problem.  Any ideas?

EDIT:

Now when I browse, by doing this:

```

file:///var/www/asdf.py

```

A window comes up, asking me to download it; opposed to html files which are rendered.

---

### Post by smartbei on 2008-04-07
Well, when you browse using file:// it doesn't go through apache - it acts like a normal file browser. So it is not very surprising that doing that you get a download instead of an html page.

Does apache work for non-python files?

Post the relevant sections of your apache2.conf/httpd.conf.

---

