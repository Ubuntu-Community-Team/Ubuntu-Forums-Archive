---
title: "How to start a PHP server on Linux with one command"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by rablanken on 2014-05-16
```
cd ~ && sudo apt-get install php5 && php -S localhost:8000 && echo 'Hello World' >> index.html && firefox localhost:8000 &
```

It totally blew my mind how easy it is to make a server on Linux!

Translation for new terminal users:
> change to directory to "home" AND install php5 AND start a (local) php server on your local machine AND create a file called index.html which says "Hello World" AND open up your awesome new site with Firefox. :D

---

### Post by cincibluer6 on 2014-05-16
Thank you for this. I'm researching a program for work that needs to run via PHP (and on a server is fine) so this might help.
Bookmarked.

---

### Post by Habitual on 2014-05-16
> **rablanken said:**
> ```
cd ~ && sudo apt-get install php5 && php -S localhost:8000 && echo 'Hello World' >> index.html && firefox localhost:8000 &
```

It totally blew my mind how easy it is to make a server on Linux!

Translation for new terminal users:
:D

index.html?

---

### Post by rablanken on 2014-05-19
Hi there cincibluer6, no problem at all - have fun! :)

As to your question Habitual, index.html is a pretty standard name for the front page of a website. In retrospect, index.php may have been more appropriate since this is specifically for a PHP server.

In any case, if the file "index.html" doesn't already exist, it will be created =p

---

