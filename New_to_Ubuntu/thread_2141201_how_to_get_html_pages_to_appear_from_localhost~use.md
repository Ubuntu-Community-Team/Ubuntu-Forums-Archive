---
title: "how to get html pages to appear from /localhost/~username directory"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by Pvpicc on 2013-05-01
I have apache2 installed on Ubuntu Precise.  Right now localhost URL points to /var/www directory and it works correctly.  How do I setup a redirection to a user folder so that, if for example, the URL /localhost/~username/ was entered, it would display an html file stored in a subdirectory of that user?  Thank you.

---

### Post by pqwoerituytrueiwoq on 2013-05-01
edit [FONT=courier new]/etc/apache2/sites-enabled/000-default[/FONT] it is a symlink to [FONT=courier new]../sites-available/default[/FONT]
just replace ever [FONT=courier new]/var/www[/FONT] with [FONT=courier new]/home/$USERNAME/.public_html[/FONT]
then everything in that users [FONT=courier new].public_html[/FONT] will replace what is visible on [FONT=Courier New]/var/www[/FONT]

---

### Post by Derek Karpinski on 2013-05-02
[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

You probably can start with:

```
sudo a2enmod userdir
```

And adding yourself to www-data group.

---

