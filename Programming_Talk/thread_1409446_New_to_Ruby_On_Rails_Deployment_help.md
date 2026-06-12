---
title: "New to Ruby On Rails Deployment help"
date: 2010-02-17
forum: Programming Talk
---

### Post by Rich78 on 2010-02-17
I've setup a simple static ruby on rails site on my mac which runs fine using webbrick.

I copied the entire structure over from my mac to my Ubuntu webserver to /var/www/sitename

setup permissions etc

the initial index.html page in public renders fine, but any other pages such as /gallery generate a 500 error displaying the "something went wrong page"

I've looked in all the /log files in the rails app directory such as development.log, production.log, server.log, test.log

All apart from development.log are empty, and development.log only has info relating to when I first developed the site a couple of days ago.

Apache log file has nothing to report of the error, so I have no idea where the error is being logged to to know what is wrong.

Any ideas?

I assume I can just copy a rails directory from one machine to the next?  I don't have to develop the app on the server?

Thanks.

---

### Post by crush304 on 2010-02-18
been a couple of years since i set up a rails server, i think a lot's changed since then so i can't give you any direct advice however, i'm fairly certain you can't just dump the files into your apache directory

here's a couple of links that might help get you in the right direction

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

[http://ryanbigg.com/2008/09/ubuntu-rails-apache-passenger-capistrano-you/](http://ryanbigg.com/2008/09/ubuntu-rails-apache-passenger-capistrano-you/)

---

### Post by Rich78 on 2010-02-18
Cheers, the dumping of the files was what I was wondering about.

---

