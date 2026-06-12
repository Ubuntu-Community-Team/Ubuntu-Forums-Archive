---
title: "rewrite url contain dash wont rewrite"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by AskTell on 2011-10-29
this is what my rewrite currently looks like, it works for my other url but not  this one due to the dash ending the rewrite rule

       <IfModule mod_rewrite.c>
               Options +FollowSymLinks
               Options +Indexes
               RewriteEngine On
               RewriteBase /
               RewriteCond %{HTTP_HOST} ^foo-foo\.com$       
               RewriteRule ^(.*)$ http://www.foo-foo.com/$1 [R=301,L]       
               </IfModule>


running 10.04 desktop

---

### Post by satanselbow on 2011-10-29
I might be wrong but...

The dash could be being interpreted as a range divider - in the same way as [a-z] ... have you tried escaping the dash? 

```

foo\-foo

```

---

### Post by AskTell on 2011-10-30
okay found my problem but i need to repost it in another thread. i have  multiple copys of the same website running on different domains but the  dns manager available thru godaddy doesn't let me specify port so i need  a way of directing based on servername, how do i do that? i'll repost  this corrected question.

---

