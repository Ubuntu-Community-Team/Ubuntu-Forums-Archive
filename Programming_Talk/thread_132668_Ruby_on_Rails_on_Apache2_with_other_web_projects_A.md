---
title: "Ruby on Rails on Apache2 with other web projects: A tutorial/howto"
date: 2006-02-18
forum: Programming Talk
---

### Post by siennalizard on 2006-02-18
Hello all,
just done this and hope it will be useful to someone else. Basically, I wanted to use Ruby on Rails, but most of the tutorials want you to run the included WebBrick webserver to do it. I wanted to use apache2, since it was running already. I didn't want to completely dedicate my /var/www/ to Ruby, though, as there are a load of php projects in there. Here's how to do it without affecting them. This is good for Breezy, and probably won't be bad for anything else. Let me know if you can correct or improve these instructions.

Before we start on crux of the issue, install (via Synaptic or apt-get) packages ruby, rails, apache2, fastcgi.

Do all this in a root shell (be careful):
```
$ sudo -H -s
```

We're going to add a new virtual host in apache2, leaving the "default" settings there.

1) create a new virtual host file in /etc/apache2/sites-available
, maybe called "rails".
```
$ cd /etc/apache2/sites-available
$ touch rails

```

2) use your favourite editor to put what follows in that file. Change the document root to wherever you want to put your rails project. Change the server name to the address where you want to access your rails project:
```


<VirtualHost *>
    ServerName rails
    DocumentRoot /var/www/railstest/public/
    ErrorLog /var/log/apache2/error.log

    <Directory /var/www/railstest/public/>
        Options ExecCGI FollowSymLinks
        AddHandler cgi-script .cgi
        AllowOverride all
        Order allow,deny
        Allow from all

    </Directory>
</VirtualHost>


```

3) having set up this file, we then need to symlink to it from the sites-enabled directory. Let's do that now:

```
$ cd /etc/apache2/sites-enabled
$ ln -s ../sites-available/rails rails

```

4) In order to get the apache2 server to display this site when you access it, you've got to add this ServerName alias next to 127.0.0.1 in your /etc/hosts file, or your web browser is _not_ going to know where to go when you give it in your address bar. Here's the beginning of mine:

```

127.0.0.1 garnet rails

```

5) Now we're pretty well done (so long as I haven't left a step out). As finally, symlink fastcgi.load and rewrite.load from mods-available directory to mods-enabled in a similar fashion and restart your apache2 with:

```

$ /etc/init.d/apache2 restart

```

You should be ready. Close the root shell and follow any Rails tutorial to get yourself set up. To kick you off, get in your /var/www directory, and type:

```

$ rails railstest

```

I'm sure there are better ways of doing this, but this worked for me. I'll make edits to this tutorial as and when people come up against problems.

Cheers, guys.
J.

---

### Post by concept10 on 2006-02-18
Just another tip:  Add this to your /etc/apache2/apache2.conf  (at the bottom) for every Rails app running on FastCGI:

FastCgiServer /var/www/rails_app/public/dispatch.fcgi -idle-timeout 120 \
       -initial-env RAILS_ENV=production -processes 2

change RAILS_ENV=development  for development

---

