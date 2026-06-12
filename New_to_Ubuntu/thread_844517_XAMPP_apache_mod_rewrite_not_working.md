---
title: "XAMPP apache mod_rewrite not working"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by codeking on 2008-06-29
I'm trying to get mod_rewrite to work with Apache.  I used phpinfo();, and mod_rewrite is installed.  I set AllowOverride to All.  Here's a httpd.conf snippet:

```
<Directory />
    Options FollowSymLinks
    AllowOverride All
    #XAMPP
    #Order deny,allow
    #Deny from all
</Directory>

#
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#

#
# This should be changed to whatever you set DocumentRoot to.
#
<Directory "/media/Shared/Websites">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.2/mod/core.html#options
    # for more information.
    #
    #Options Indexes FollowSymLinks
    # XAMPP
    Options All


    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    #AllowOverride None
    # since XAMPP 1.4:
    AllowOverride All


    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>
```

---

### Post by nowshining on 2008-06-29
are u trying to add an htaccess file to individual directories?

---

### Post by codeking on 2008-06-29
nevermind, I fixed it

---

### Post by nowshining on 2008-06-29
well tell us the people of the world how u fixed it. :P and of course what u were trying to accomplish.

---

### Post by codeking on 2008-06-29
dumb mistake:  .htaccess is a hidden file so Ubuntu didn't copy it to the new directory

---

### Post by nowshining on 2008-06-30
ah, when i was running apache2 i couldn't never get the .htaccess file working so I use the main one.

---

