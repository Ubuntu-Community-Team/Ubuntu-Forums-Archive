---
title: "Trouble with htaccess"
date: 2013-03-29
forum: Programming Talk
---

### Post by uncleheinz on 2013-03-29
Hello,

I have some problems with htaccess.

Currently I have two separate files, one for localhost, one for the server.

Localhost version is here:
```

<ifModule mod_rewrite.c>
    Options +FollowSymLinks
    RewriteEngine On

    RewriteRule ^([^/\.]+)/?$ /onnevalgus/index.php?page_type=$1 [L,NC]
    RewriteRule ^pages/([^/\.]+)?$ /onnevalgus/index.php?page_type=pages&page_id=$1 [L,NC]
</ifModule>

ErrorDocument 404 /onnevalgus/index.php?page_type=404

```

And the server version:
```

<ifModule mod_rewrite.c>
    Options +FollowSymLinks
    RewriteEngine On

    RewriteRule ^([^/\.]+)/?$ /new/index.php?page_type=$1 [L,NC]
    RewriteRule ^pages/([^/\.]+)?$ /new/index.php?page_type=pages&page_id=$1 [L,NC]
</ifModule>

ErrorDocument 404 /new/index.php?page_type=404

```


However, this solution is quite inconvenient, so I decided to join them together as one single file.
I came out with following solution, but turns out it's not working properly:
```

<ifModule mod_rewrite.c>
    Options +FollowSymLinks
    RewriteEngine On

    RewriteCond %{HTTP_HOST} ^localhost
    RewriteRule ^([^/\.]+)/?$ /onnevalgus/index.php?page_type=$1 [L,NC]
    RewriteRule ^pages/([^/\.]+)?$ /onnevalgus/index.php?page_type=pages&page_id=$1 [L,NC]
    ErrorDocument 404 /onnevalgus/index.php?page_type=404

    RewriteCond %{HTTP_HOST} ^(www\.)mysite.com
    RewriteRule ^([^/\.]+)/?$ /new/index.php?page_type=$1 [L,NC]
    RewriteRule ^pages/([^/\.]+)?$ /new/index.php?page_type=pages&page_id=$1 [L,NC] # NOT WORKING!
    ErrorDocument 404 /new/index.php?page_type=404
</ifModule>

```

Take a look at the comment in the code: everything else seems to work, except that particular line. I just can't figure out where is the bug.

(Phrase *mysite.com* is replaces the actual domain name, but everyting else is identical with the original.)

---

### Post by SeijiSensei on 2013-03-29
If the two virtual hosts are defined in separate files under /etc/apache2/sites-available/ just put the appropriate code for each site in its corresponding virtual host definition file.

---

### Post by uncleheinz on 2013-03-29
Actually, this ***server*** is not a virtual host in my computer, it is actual server up in the web. And I don't have any access to it's configuration files.

Both .htaccess files for localhost and server work nice. Problem starts when I try to put them together into one single file.

---

### Post by SeijiSensei on 2013-03-29
Well, htaccess files are directory-specific.  They have to reside in the virtual host's DocumentRoot.  A request for one virtual server won't be seen by any others.  Essentially htaccess files just allow you to replace directives that would otherwise appear in a "<Directory>" container with the same directives in a file in the directory itself.

---

### Post by uncleheinz on 2013-03-29
I suspect there may be something wrong with the ***RewriteCond*** statemet.

Without RewriteCond:
```

<ifModule mod_rewrite.c>
    Options +FollowSymLinks
    RewriteEngine On

    RewriteRule ^([^/\.]+)/?$ /new/index.php?page_type=$1 [L,NC] # WORKS NICE
    RewriteRule ^pages/([^/\.]+)?$ /new/index.php?page_type=pages&page_id=$1 [L,NC] # WORKS NICE
</ifModule>

ErrorDocument 404 /new/index.php?page_type=404 # WORKS NICE

```


With RewriteCond:
```

<ifModule mod_rewrite.c>
    Options +FollowSymLinks
    RewriteEngine On

    RewriteCond %{HTTP_HOST} ^localhost
    RewriteRule ^([^/\.]+)/?$ /onnevalgus/index.php?page_type=$1 [L,NC] # WORKS NICE
    RewriteRule ^pages/([^/\.]+)?$ /onnevalgus/index.php?page_type=pages&page_id=$1 [L,NC] # WORKS NICE
    ErrorDocument 404 /onnevalgus/index.php?page_type=404 # WORKS NICE

    RewriteCond %{HTTP_HOST} ^(www\.)mysite.com
    RewriteRule ^([^/\.]+)/?$ /new/index.php?page_type=$1 [L,NC] # WORKS NICE
    RewriteRule ^pages/([^/\.]+)?$ /new/index.php?page_type=pages&page_id=$1 [L,NC] # NOT WORKING!
    ErrorDocument 404 /new/index.php?page_type=404 # WORKS NICE
</ifModule>

```

I still don't understand why that on line there is problematic while everything else works.

---

### Post by SeijiSensei on 2013-03-30
Because, as I said, only one virtual host will be associated with that file, and it will never see the other hostname you are trying to match with RewriteCond.  Just put separate files in the separate DocumentRoot directories.

---

