---
title: "RoR - &quot;something went wrong&quot; - apache2, passenger, debian, mysql"
date: 2010-01-14
forum: Programming Talk
---

### Post by Fittersman on 2010-01-14
Hi all,

I originally posted this on the ruby on rails forums, but got no reply, so hopefully someone here can help me out. (summary at bottom if post is too long).

To start, I'm very new to ruby on rails, I've read numerous guides (the best and most comprehensive is probably this one: [http://hackd.thrivesmarthq.com/how-to-setup-a-linux-server-for-ruby-on-rails-with-github-and-phusion-passenger](http://hackd.thrivesmarthq.com/how-to-setup-a-linux-server-for-ruby-on-rails-with-github-and-phusion-passenger)). So far I have installed apache2, mysql, ruby, rails, and passenger on my debian install. I have configured passenger already.

I can't seem to find the source of my latest problem though.. I try to navigate to my ruby on rails application on my apache2 server, click the "about your application's environment" button, but I get the standard "Something went wrong" message.

I haven't quite been able to figure out what environment I'm working in, but I can only assume it's development since I ran "rake db:create" and it created the development database.

My log files are all empty, (everything in myApp/log/ folder is 0KB).

I just can't seem to figure out what the problem is.. I did read one post on a blog though that says something along the lines of "passenger starts in production mode by default and you must edit a passenger.conf file for your applications to work in development" - I could not find such a passenger.conf file (he gave a location of /etc/apache2/other/passenger.conf). I also searched my hard drive for the passenger.conf file, but no luck.

I'm really not sure where to go with this, If someone could tell me where I can find some log files that might describe the error, that would be great. As of right now, all I really have for information is that "something went wrong" message, which is not very helpful.

Oh, and if I use the WEBrick server (script/server) and click that same "about your application's environment" button, everything seems to run fine. It's just something to do with apache2 and passenger I think...

summary:
- log files in myApp/log are all empty
- working in development environment (to the best of my knowledge)
- WEBrick server works fine and I do not get the "something went wrong" message.
- trying to run apache2, mysql, and passenger on a Debian linux system
- Can not find a location that logs the actual error

---

