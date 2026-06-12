---
title: "Localhost LAMP on Ubuntu"
date: 2009-06-05
forum: Programming Talk
---

### Post by lstables on 2009-06-05
Hi all,

I just wondered if anyone can help me.
I have installed LAMP on Ubuntu but when i put my websites into the var/www and try and update the sites using jEdit the updates doesn't take place when viewing the url [http://localhost/mysite](http://localhost/mysite) in my browser.

Have I done something wrong ?
Yes I ALWAYS save before refreshing in browser

Thanks in advance
Lee

---

### Post by s.fox on 2009-06-05
Hi,

It could be a cache issue.  Try clearing it.  :)

-Ash R

---

### Post by Alias1407 on 2009-06-05
Follow the documentation to the letter...

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)


Also your webpages go in <lampp directory>/htdocs
create a new folder in here with...

```
sudo mkdir <lampp directory/htdocs/<name of folder>
```

Then give it permissions with...

```
sudo chown <your username> <lampp directory/htdocs/<name of folder>
```

Then goto your browser and go to http://localhost/<name of folder>


Of course replace <*> with proper names

---

