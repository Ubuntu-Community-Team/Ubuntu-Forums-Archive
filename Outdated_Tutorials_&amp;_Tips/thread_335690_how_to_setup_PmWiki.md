---
title: "how to setup PmWiki"
date: 2007-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by ryu kun on 2007-01-10
I have been looking for a good personal wiki engine for some time. And now I am trying PmWiki. 

It is a PHP web application, so there has to be something that can support PHP and act as a webserver. It wasn't easy to find how to do that as it is not explained yet in its [official home page]("http://pmwiki.org/wiki/PmWiki/PmWiki"), I wanted to write this guide. Please be aware that I am not any close to being a guru of these things, I just managed to make it run. How did I? I'll explain it now.

1. Install PHP webserver support:

```
sudo aptitude install php5
sudo aptitude install apache2
```

2. Download your PmWiki from here: 
[http://pmwiki.org/wiki/PmWiki/Download]("http://pmwiki.org/wiki/PmWiki/Download")

3. Extract it to /var/www/pmwiki/

4. Point your browser to [http://localhost/pmwiki/pmwiki.php]("http://localhost/pmwiki/pmwiki.php")

5. As it needs a writeable wiki.d subdirectory, you should create one. How to make it and set correct permissions to it explained in the page you just opened. Just follow those instructions.

It should be done. Enjoy your brand new personal wiki! :)

---

