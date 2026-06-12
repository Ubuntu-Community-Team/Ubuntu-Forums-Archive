---
title: "quick mod_rewrite question"
date: 2006-03-30
forum: Programming Talk
---

### Post by Kurt` on 2006-03-30
Hi,

I want to make a URL for viewing a site member's profile as follows: site.com/profile/Username/

However, I want site.com/profile/Username <- without the trailing / to redirect to the one WITH the trailing slash first.

Here are the rules I was trying:

RewriteRule ^profile/(.+)?$ /profile/$1/ [R]
RewriteRule ^profile/(.+)/?$ /site/entry.php?page=profile_name&name=$1

I do realize that .+ will match the trailing "/" (if present), so the first rule naturally causes a redirection loop.

Is there a simple way for the first rule to check if there is a trailing slash?

Thanks

---

