---
title: "PHP programming in User's Home Directory"
date: 2008-01-06
forum: Programming Talk
---

### Post by dwhitney67 on 2008-01-06
Hello,

I just purchased a book called "PHP, MySQL and Apache", and one of the issues I have about the book is that the author provides instructions for the reader to create files in the root-directory where Apache looks for content.  In my case, this is /var/www/html.

Thus using Firefox, I can open a file with the following URL:  [http://localhost/phpinfo.php](http://localhost/phpinfo.php)

I would like to continue with the exercises in the book, however when I attempt to create the PHP scripts within a subdirectory of my home directory, FF does not want to execute the script.  FF prompts me if I want to open the script with a text editor or save it.

If I place the script in /var/www/html, then FF deals with it like a charm.  I briefly played around with the httpd.conf file, changing the root-dir and what have you to the subdir in my home directory; then restarted the HTTPD service.  Still, it would not execute my PHP scripts within the subdir.

Is this a security feature of FF or is there a another configuration file that needs to modified?

---

### Post by jaakan on 2008-01-06
having Apache looking at a "User's Home Directory" IE: /home/"someuser" or /root/ is a bad idea. Did you check the permissions? 

 they should look something like this 
jaakan@AMD64:/var$ ls -aln
....
....
drwxr-xr-x  3 0  0 4096 2007-11-22 07:50 www

if you need to match the permissions
chmod  -R --reference=/var/log /var/www

---

### Post by dwhitney67 on 2008-01-06
Sorry, I did not mean to confuse you (or anyone else) to believe that my Apache installation is referencing the /root directory.  I meant the "document root" directory, which in my httpd.conf file has listed as:

```
DocumentRoot "/var/www/html"
```

I attempted to change the DocumentRoot to my home directory, so that I could experiment with PHP scripts and HTML, but I was unable to run the PHP scripts.

---

### Post by [h2o] on 2008-01-06
You could enable user directories (userdir module?) and then develop in your public_html directory of your user (or whatever you want to call it).
The Apache documentation is fairly straightforward when it comes to setting it up, just don't forget to make sure to enable script support in the userdir. Good luck!

---

