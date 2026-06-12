---
title: "mod_rewrite is driving me mad..."
date: 2007-11-12
forum: Programming Talk
---

### Post by aks44 on 2007-11-12
Here's what I'm struggling with:

- My portal's root is (eg.) **/portal/**
- The portal's root contains a single "dispatcher" **index.cgi** (the rest of the code is located in a "Deny from all" directory)
- The portal's root contains a directory where static files are located  (**/portal/static/**)
- All rewriting stuff must be done in **.htaccess** files (my web host won't allow me any other config file)
- All errors go through the dispatcher index.cgi (**ErrorDocument xxx /portal/index.cgi**)
- If the user forgets the www. prefix it should be prefixed to the server name (in fact I guess I should use / compare with %{SERVER_NAME})
- Any access to an *existing* static file (**/portal/static/...**) must be done using plain HTTP (to remove some load from the server)
- Any other access (including error redirects) must be done over HTTPS (the dispatcher takes care of URL splitting, errors etc) because of
--- session cookies being SSL-only (the portal deals with personal information, no way I'll let a session cookie wander around in plain text)
--- use of "friendly" URLs

So far, I barely achieved anything but 500 errors (internal server error aka. .htaccess syntax error) or infinite redirections (which Firefox catches fortunately).

I read the mod_rewrite reference countless times to no avail, and numerous tutorials which didn't really help me. It seems I can't manage to wrap my head around that, even though I could probably recite by heart half of the mod_rewrite documentation I just can't "feel the magic". :(

So out of desperation I'm asking for help, with the hope that someone will put me on the tracks before I dump that ******* comp through the window...


Any help / tips are welcome. :)

---

### Post by aks44 on 2007-11-30
FWIW, I (finally!) managed to sort this out.

Just posting it in case someone may benefit from it.

```
Options -Includes -IncludesNOEXEC -Indexes -MultiViews
AcceptPathInfo Off

ErrorDocument 400 /portal/index.cgi
# Same for 401->417 and 500->505

RewriteEngine On
RewriteBase /portal

RewriteCond %{REQUEST_URI} ^/portal/static/
RewriteCond %{REQUEST_FILENAME} -s
RewriteCond %{PATH_INFO} ^$
RewriteCond %{HTTP_HOST} !^www\.domain\.tld$ [OR]
RewriteCond %{HTTPS} ^on$
RewriteRule .* http://www.domain.tld%{REQUEST_URI} [R=302,L]

RewriteCond %{REQUEST_URI} !^/portal/static/ [OR]
RewriteCond %{REQUEST_FILENAME} !-s [OR]
RewriteCond %{PATH_INFO} !^$
RewriteCond %{HTTP_HOST} !^www\.domain\.tld$ [OR]
RewriteCond %{HTTPS} ^off$
RewriteRule .* https://www.domain.tld%{REQUEST_URI} [R=302,L]

RewriteCond %{REQUEST_URI} !^/portal/static/ [OR]
RewriteCond %{REQUEST_FILENAME} !-s [OR]
RewriteCond %{PATH_INFO} !^$
RewriteRule .* index.cgi [L]
```

---

