---
title: "Super Server Setup Help"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Ceephis on 2008-07-01
Dear Friends,

I wanted to concede that I definitely need help insetting up my server.  I have been reading how to's and most everything I can get my hands on in the beginner sticky's (Thanks again some stuff I just learned I will try to use to fix one of my questions)


Here Is my equipment

1. 3 500gb drives
2. 1.8 Ghz computer
3. 1.5 gigs of ram.
4. 2 routers before hitting DSL Internet connection (Linksys and 2 link)


Here is what I want 
1. I want to set Ubuntu in DESKTOP mode and the drives in EVMS mode (so that I have 1 terabyte of space and redundancy)
2. To set up a web server that can handle multiple sites (I have DynDNS account I have no Idea how to use it or set it up.)
3. I can not figure out how to access/add files to my var/www/html.  I have installed Lamp but I cant get to manage (I am used to web based admins for...) mysql, phpbb, or any other programs like a picture sharing page or a blog.

Can any of you help me with this?

Thank you so much for your time and help it is so very appreciated.

Peter

---

### Post by hyper_ch on 2008-07-01
(1) Install the desktop os - no clue about raid configuration for your drives... but there should be plenty of info out there

(2)Once the desktop is installed, setup the "webserver". I suggest to follow the perfect howto by falko for Ubuntu Hardy Server --> [http://www.howtoforge.com](http://www.howtoforge.com) (install also ispconfig to have multiple website hosting)

---

### Post by Ceephis on 2008-07-01
Thanks I found the super server  setup by falko  I think I will try it and maybe jump into the deep end with no GUI (server edition)

Peter

My questions about DynDNS and EVMS still stand to anyone out there who can help.

---

### Post by hyper_ch on 2008-07-01
there's a dyndns client in the repos... no clue how to configure it... I prefer no-ip.com

---

### Post by jamesrfla on 2008-07-01
I just did a forum on making my own server and this might help.
[http://ubuntuforums.org/showthread.php?t=844409](http://ubuntuforums.org/showthread.php?t=844409)

---

### Post by Ceephis on 2008-07-01
WOW I am liking no-IP.com 

a little more lenient that DynDNS, I'll see if it will work for me.

Do you or does anyone you know pay for any accounts at no-IP.com?
I am interested to hear if there are benefits to upgrading.

WOW thanks for helping me kill off so much in one day.

Peter

---

### Post by hyper_ch on 2008-07-01
no, not paying for no-ip... just once every 3 months login again there...

the ubuntu client is called: noip2

```

sudo apt-get install noip2

```

---

