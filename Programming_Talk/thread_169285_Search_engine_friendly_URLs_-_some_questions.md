---
title: "Search engine friendly URLs - some questions"
date: 2006-05-02
forum: Programming Talk
---

### Post by hagen00 on 2006-05-02
Hi

Some questions...

Currently my webpages are designed like this host.com/index.php?page=webdesign. That page then just gets included in my index page, preventing me from having to copy and pase code.

Question 1
Is it true that Google won't parse anything after the question mark after index?

If that is true then i will have to look at options of making my pages more search engine friendly. 

I've tried doing the following. 
- putting an .htaccess file into my root directory containing the following code
```
RewriteEngine On
RewriteRule ^index/(.*).php /index.php?page=$1
``` but then i get an error saying Forbidden, you do not have access to the server...

- I tried using the php explode function to get the page=design parameter but also with limited success. 

So second question
Is this even necessary for search friendly URL's and if it is, which is the preferred method. Mod_rewrite or something else. And if you can give me any tips on how to make this flaming thing work then that would be even more appreciated. 

Thanks

---

### Post by lnostdal on 2006-05-02
this isn't necessary; search-engines crawl links with ? in them too (like this forum!) :)

this is why GET-requests should not modify state; only POST-requests

---

### Post by hagen00 on 2006-05-03
Cool stuff, thanks for the advice. Will save me some work.

---

