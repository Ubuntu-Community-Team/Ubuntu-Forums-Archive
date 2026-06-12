---
title: "Getting Apache web server to recognize phtml files."
date: 2008-09-30
forum: New to Ubuntu
---

### Post by ItecKid on 2008-09-30
Ok, so I installed the requisite apache and php programs from the package manager.  Apache works properly when I navigate to [http://localhost](http://localhost), but it seems to have trouble reading php files.  I downloaded a simple php file from the internet, and extracted it to the root/var/www folder, and named it blog.

However, when I attempt to navigate to [http://localhost/blog](http://localhost/blog), the system does not know how to open the phtml file; however, if I navigate to a specific directory in blog, such as index.php, the page loads properly.  However, in the sidebar, it displays the following warning:
```
file_put_contents(config/plugins/sidebar/Avatar.txt) [function.file-put-contents]: failed to open stream: No such file or directory in /var/www/blog/scripts/classes/fileio.php on line 76

```

I appreciate the help of anyone who can make sense of this.

---

### Post by zephyrcat on 2008-09-30
First, make sure that you installed php. If you did and the problem is just .phtml files, then look at the second post in this thread:

[http://ubuntuforums.org/showthread.php?t=277819](http://ubuntuforums.org/showthread.php?t=277819)

I think that might be the solution

---

### Post by ItecKid on 2008-09-30
Do I need to do something special to enable the 'AddType' command?  My terminal seems to think that it doesn't exist.

---

