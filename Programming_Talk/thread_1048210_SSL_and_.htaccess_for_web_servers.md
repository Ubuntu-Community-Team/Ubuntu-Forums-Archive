---
title: "SSL and .htaccess for web servers"
date: 2009-01-23
forum: Programming Talk
---

### Post by HornedBeast on 2009-01-23
Hello,

I am trying to implement a rewrite script in my htaccess file.

I would like to create a rule as per the following.

IF
The page is either, checkout.php | carddetails.php | confirm.php | createorder.php | confirmation.php
Then make it [https://www.whatever.com/*thepage*.php](https://www.whatever.com/*thepage*.php)
ElseIF
Use [http://www.whatever.com/*thepage*.php](http://www.whatever.com/*thepage*.php)



Any ideas how to do this? My current .htaccess looks like this:

RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule (.*) http://www.whatever.com/404.php?page=%{REQUEST_URI} [R=301,L]
RewriteCond %{HTTP_HOST} !^www.whatever.com$
RewriteRule ^(.*)$ http://www.whatever.com/$1 [R=301,L]
AddType x-mapp-php5 .php



This picks up any 404s and takes them to the 404.php page

And the rest seems to make sure the page is always [http://wwww](http://wwww)

I assume this may also be important to the above question.

Andy information regarding the above would be apreciated.

Thank-you kindly.

Andy Barlow

---

