---
title: "change document root in lamp"
date: 2012-09-21
forum: Programming Talk
---

### Post by chuchi on 2012-09-21
Hi there!! I can not change the document Root in apache (LAMP). I follow the steps in [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual_Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual_Hosts).

I change the default "/www/var" to "/home/jesus/Dropbox/htdocs/" in the file "mysite" (copy of default).

But when I type the url: "localhost/index.html" I get the error message:

```

Forbidden

You don't have permission to access /index.html on this server.

```

And I am pretty sure index.html exists.

What's the problem??

Thank you very much!!

---

### Post by Lars Noodén on 2012-09-21
Have you checked that Other has read permissions to those directories?

```

chmod o=rx /home/jesus/Dropbox/htdocs/
chmod o=rx /home/jesus/Dropbox/
chmod o=rx /home/jesus/

```


Then you also need to have set [Directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory) permissions in Apache for the relevant virtual host's configuration file.

       
```

<Directory /home/jesus/Dropbox/htdocs/>
      Options Indexes FollowSymLinks MultiViews
      AllowOverride None
      Order allow,deny
      allow from all
</Directory>

```

---

### Post by chuchi on 2012-09-21
HI Lars Noodén!!! Now it works!!!! you are right, it was a permission problem!! Thank you very very much!!

---

