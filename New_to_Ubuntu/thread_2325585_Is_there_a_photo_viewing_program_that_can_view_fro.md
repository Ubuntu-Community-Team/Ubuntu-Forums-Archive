---
title: "Is there a photo viewing program that can view from social media?"
date: 2016-05-23
forum: New to Ubuntu
---

### Post by chamerjr on 2016-05-23
I'm not new to Linux, but I'm definitely not experienced enough to know all the programs people like to use.  After a few hours of searching, I'm fairly certain a program like this doesn't exist.  I have a nice Samsung "Ultrabook" with a 128gb ssd.  I don't want to use up all the storage by syncing my pictures from FB, Google Photos, IG, etc.  Is there any photo/viewing application that will cache thumnails of the pictures from said social media sites?  Ideally, I would like it to cache the full picture then purge after a set limit (i.e. 1gb).  Is there any such application or am I SOL?  Thank you in advance.

---

### Post by TheFu on 2016-05-25
Think about what you are asking for a few minutes.

Social media sites want to control what you see and to that end, they make changes to the layout, ads, and content constantly to prevent "bandwidth hogs."  Some might also validate the referrer in the http requests to prevent us from seeing only the content we want without all the content THEY want our eyes too see.

So, if something like this does exist, it will need to be very much like a browser with full, complex, support of javascript, caching, 3rd party cookies (for ad networks), login support and OAuth2 support ... basically - it would need to be a browser or embed a browser inside the app window.

Twitter blocked all unapproved applications 1-2 yrs ago.

So - if this did exist, it would be constantly out of date and not working, since screen-scraping apps are notoriously hard to maintain.

BTW, files disappear from the social sites all the time.  Would be smart to have a local backup - it isn't like images use THAT much storage. A $50 USB drive would definitely be enough for almost everyone who isn't a professional photographer.  I have just under 22K photos online and they fit in 55G of storage.  Just sayin'.

> $ find . -type f -iname \*jpg | wc -l
21666
$ du -sh ~/www/gallery
55G     

---

### Post by chamerjr on 2016-05-25
> **TheFu said:**
> Think about what you are asking for a few minutes.  Social media sites want to control what you see and to that end, they make changes to the layout, ads, and content constantly to prevent "bandwidth hogs."  Some might also validate the referrer in the http requests to prevent us from seeing only the content we want without all the content THEY want our eyes too see.  So, if something like this does exist, it will need to be very much like a browser with full, complex, support of javascript, caching, 3rd party cookies (for ad networks), login support and OAuth2 support ... basically - it would need to be a browser or embed a browser inside the app window.  Twitter blocked all unapproved applications 1-2 yrs ago.  So - if this did exist, it would be constantly out of date and not working, since screen-scraping apps are notoriously hard to maintain.  BTW, files disappear from the social sites all the time.  Would be smart to have a local backup - it isn't like images use THAT much storage. A $50 USB drive would definitely be enough for almost everyone who isn't a professional photographer.  I have just under 22K photos online and they fit in 55G of storage.  Just sayin'.  Why do people online insist on trying to tell someone why they should NOT seek their proposed method based on someone else feels they should do.  I appreciate your suggestion, but it does not answer my question.  I easily have 50+ gb of photos.  Storing them on the local drive (128gb) ssd is not an option with all the productivity software, games, OS, etc eating up a good chunk of space.  Storing them on a removable drive means I must have that drive on me at all times to recall the pictures.  That's not including assuming everyone could afford the cost of one....not that it's an issue for me, but it speaks to my point about people making suggestions based on what they think, rather than trying to help the question asker by answering directly.  If a thumbnail were cached, it would only take up a few hundred MB for a large library, and if I wanted to view or download 100 or so pictures, it only should take up a few hundred megs to possibly a gig.  Then, when the program is exited or after a certain time limit, the full pictures cached would be freed.  It's a very convenient option for people with limited storage.  There are a few android galleries that do exactly what I propose, most notably Samsung's photo gallery.  If programs like Shotwell can upload to social media libraries, why is it so far fetched that it could view from said libraries?

---

