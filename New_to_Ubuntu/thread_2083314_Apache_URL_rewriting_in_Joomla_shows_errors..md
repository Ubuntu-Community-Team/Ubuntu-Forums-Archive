---
title: "Apache URL rewriting in Joomla shows errors."
date: 2012-11-12
forum: New to Ubuntu
---

### Post by Kev261266 on 2012-11-12
Hi,

I've recently installed lamp on ubuntu 12.10 so I can develop Joomla websites on localhost, before uploading them to a live site.

Everything seems to be working fine, I have lamp set up so that joomla 2.5.7 installs with no pre check errors.

The one problem I cannot get round is when I set the Joomla backend/administration, seo section to "use url rewriting"

I followed all the joomla instructions i.e. change htaccess.txt to .htaccess and enabled the apache mod rewrite in the terminal.

I've also tried fresh installs and not made any changes to the htaccess.txt file and I always get the same error. as explained below.

In a perfect world enabling the joomla url rewrite would cause a site address like this:
localhost/site1/index.php/about-us

to display as this:
localhost/site1/about-us

I've had this working on many sites in the past using windows xp, however in Ubuntu I get an error:

NOT FOUND The requested URL site1/ about-us was not found on this server Apache/2.2.22 (Ubuntu) Server at localhost Port 80.

can anyone advise what's going wrong or more likely, what I'm doing wrong.

Thanks in advance.

---

### Post by pkadeel on 2012-11-12
> **Kev261266 said:**
> Hi,

I've recently installed lamp on ubuntu 12.10 so I can develop Joomla websites on localhost, before uploading them to a live site.

Everything seems to be working fine, I have lamp set up so that joomla 2.5.7 installs with no pre check errors.

The one problem I cannot get round is when I set the Joomla backend/administration, seo section to "use url rewriting"

I followed all the joomla instructions i.e. change htaccess.txt to .htaccess and enabled the apache mod rewrite in the terminal.

I've also tried fresh installs and not made any changes to the htaccess.txt file and I always get the same error. as explained below.

In a perfect world enabling the joomla url rewrite would cause a site address like this:
localhost/site1/index.php/about-us

to display as this:
localhost/site1/about-us

I've had this working on many sites in the past using windows xp, however in Ubuntu I get an error:

NOT FOUND The requested URL site1/ about-us was not found on this server Apache/2.2.22 (Ubuntu) Server at localhost Port 80.

can anyone advise what's going wrong or more likely, what I'm doing wrong.

Thanks in advance.
You need to enable mod_rewrite. It is not enabled by default.
```

sudo a2enmod rewrite
sudo service apache2 restart

```

---

### Post by Kev261266 on 2012-11-12
I did enable mod rewrite, I've just entered that command again in the terminal and it states

module rewrite already enabled

---

### Post by pkadeel on 2012-11-12
Can you post the .htaccess file portion which relates to this redirection.

---

### Post by Kev261266 on 2012-11-12
Hi,

This is the code that is in the file htaccess.txt. So I've not edited this in any way and I've not renamed it to .htaccess yet.

I've also been told that the code

```
RewriteBase /

```

should be changed to 

```
RewriteBase /mysite
```

but this produces the same error.

```
##
# @package        Joomla
# @copyright    Copyright (C) 2005 - 2012 Open Source Matters. All rights reserved.
# @license        GNU General Public License version 2 or later; see LICENSE.txt
##

##
# READ THIS COMPLETELY IF YOU CHOOSE TO USE THIS FILE!
#
# The line just below this section: 'Options +FollowSymLinks' may cause problems
# with some server configurations.  It is required for use of mod_rewrite, but may already
# be set by your server administrator in a way that dissallows changing it in
# your .htaccess file.  If using it causes your server to error out, comment it out (add # to
# beginning of line), reload your site in your browser and test your sef url's.  If they work,
# it has been set by your server administrator and you do not need it set here.
##

## Can be commented out if causes errors, see notes above.
Options +FollowSymLinks

## Mod_rewrite in use.

RewriteEngine On

## Begin - Rewrite rules to block out some common exploits.
# If you experience problems on your site block out the operations listed below
# This attempts to block the most common type of exploit `attempts` to Joomla!
#
# Block out any script trying to base64_encode data within the URL.
RewriteCond %{QUERY_STRING} base64_encode[^(]*\([^)]*\) [OR]
# Block out any script that includes a <script> tag in URL.
RewriteCond %{QUERY_STRING} (<|%3C)([^s]*s)+cript.*(>|%3E) [NC,OR]
# Block out any script trying to set a PHP GLOBALS variable via URL.
RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
# Block out any script trying to modify a _REQUEST variable via URL.
RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
# Return 403 Forbidden header and show the content of the root homepage
RewriteRule .* index.php [F]
#
## End - Rewrite rules to block out some common exploits.

## Begin - Custom redirects
#
# If you need to redirect some pages, or set a canonical non-www to
# www redirect (or vice versa), place that code here. Ensure those
# redirects use the correct RewriteRule syntax and the [R=301,L] flags.
#
## End - Custom redirects

##
# Uncomment following line if your webserver's URL
# is not directly related to physical file paths.
# Update Your Joomla! Directory (just / for root).
##

# RewriteBase /

## Begin - Joomla! core SEF Section.
#
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
#
# If the requested path and file is not /index.php and the request
# has not already been internally rewritten to the index.php script
RewriteCond %{REQUEST_URI} !^/index\.php
# and the request is for something within the component folder,
# or for the site root, or for an extensionless URL, or the
# requested URL ends with one of the listed extensions
RewriteCond %{REQUEST_URI} /component/|(/[^.]*|\.(php|html?|feed|pdf|vcf|raw))$ [NC]
# and the requested path and file doesn't directly match a physical file
RewriteCond %{REQUEST_FILENAME} !-f
# and the requested path and file doesn't directly match a physical folder
RewriteCond %{REQUEST_FILENAME} !-d
# internally rewrite the request to the index.php script
RewriteRule .* index.php [L]
#
## End - Joomla! core SEF Section.

```

---

### Post by pkadeel on 2012-11-12
have you uncommented the RewriteBase directive in your actual .htaccess after changing it to /mysite

---

### Post by Kev261266 on 2012-11-12
Yes, I did that too.

---

### Post by pkadeel on 2012-11-12
Before starting to log the rewrite requests, do another check as advised in joomla comments by commenting the
Options +FollowSymlinks
and try accessing the file by normal url

---

### Post by Kev261266 on 2012-11-12
I commented out options +followsymlinks

But still get the same error.

However, I can access the page if I manually type in the url, using the index.php in the address.

---

### Post by Kev261266 on 2012-11-12
I ran the Joomla forum post assistant (see attached), and it seems I have a few Apache modules and extensions missing. Could this be causing the problem?

---

