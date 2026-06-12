---
title: "php sitemap generator"
date: 2014-01-13
forum: Programming Talk
---

### Post by chuchi on 2014-01-13
Hi there!

 

 I am a newbie regarding sitemaps. I have to develop a sitemap for my website, which is developed in PHP and using URL rewritting. So for example, when the user requests [www.mywebsite/myaccount](www.mywebsite/myaccount), Apache Server is rewritting to [www.mywebsite/user.php](www.mywebsite/user.php).
 

 Besides, there are no .html files, all is developed in php files like “header.php”, “footer.php” etc..
 

 How can I implement a sitemap generator in php?
 

 I have searched in the web but found nothing.
 

 Thanks a lot!

---

### Post by tgalati4 on 2014-01-13
Have you tried:

tgalati4@Mint14-Extensa ~ $ apt-cache search linkchecker
linkchecker - check websites and HTML documents for broken links
linkchecker-gui - check websites and HTML documents for broken links (GUI client)
linkchecker-web - check websites and HTML documents for broken links (web client)
w3c-linkchecker - tool to verify the links in a web page are still valid


[http://manpages.ubuntu.com/manpages/precise/man1/google-sitemapgen.1.html](http://manpages.ubuntu.com/manpages/precise/man1/google-sitemapgen.1.html)

[http://code.google.com/p/sitemap-generators/wiki/SitemapGenerators](http://code.google.com/p/sitemap-generators/wiki/SitemapGenerators)

---

