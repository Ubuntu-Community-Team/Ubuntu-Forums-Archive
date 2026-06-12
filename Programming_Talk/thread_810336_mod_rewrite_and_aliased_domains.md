---
title: "mod_rewrite and aliased domains"
date: 2008-05-28
forum: Programming Talk
---

### Post by ad_267 on 2008-05-28
This isn't about Ubuntu or programming as such but I haven't had much luck elsewhere and I'm hoping someone can help me out with this. If there's a better category for this then please move it.

I'm building a website that is hosted with godaddy and has many aliased domains. The website uses url rewriting with mod_rewrite. This is my .htaccess file at the moment.

```

Options -Indexes
Options +FollowSymLinks

RewriteEngine On
RewriteBase /

# Redirect aliased domains
RewriteCond %{HTTP_HOST} !^.*domain.com$ [NC]
RewriteRule ^/?(.*)$ http://www.domain.com/$1 [R,L]

# If a file is requested
RewriteCond %{REQUEST_FILENAME} -f
RewriteRule ^(.*)$ $1 [L]

# With language variable
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z][a-z])/index.php?(.*)$ index.php?$2 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z][a-z])[/]?$ index.php?lang=$1 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z][a-z])/(.*)[/]?$ index.php?lang=$1&category=$2 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z][a-z])/([a-z_\-]+)/([^/]+)[/]?$ index.php?lang=$1&category=$2&title=$3 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z][a-z])/([a-z_\-]+)/([^/]+)/([^/]+)[/]?$ index.php?lang=$1&category=$2&title=$3&commentspage=$4 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z][a-z])/([a-z0-9_\-]+)/p_([0-9]+)[/]?$ index.php?lang=$1&category=$2&articlespage=$3 [L]

# Without language
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?category=$1 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z_]+)/([^/]+)[/]?$ index.php?category=$1&title=$2 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z_]+)/([^/]+)/([^/]+)[/]?$ index.php?category=$1&title=$2&commentspage=$3 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([a-z0-9_\-]+)/p_([0-9]+)[/]?$ index.php?category=$1&articlespage=$2 [L]

```

What I would like is that if the website is accessed from any of the aliased domains then the url is not redirected to the hosted domain but stays on that aliased domain so that it is the aliased domain that shows up in the users address bar.

But if I remove this:
```
# Redirect aliased domains
RewriteCond %{HTTP_HOST} !^.*domain.com$ [NC]
RewriteRule ^/?(.*)$ http://www.domain.com/$1 [R,L]
```
Then I get a 500 internal server error when trying to access the site from any of the aliased domains.

Can anyone point out what's going wrong?

Cheers,
Adam

---

