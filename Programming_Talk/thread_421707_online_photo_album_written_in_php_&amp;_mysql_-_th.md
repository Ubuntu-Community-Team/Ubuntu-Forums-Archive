---
title: "online photo album written in php &amp; mysql - thoughts?"
date: 2007-04-24
forum: Programming Talk
---

### Post by karellen on 2007-04-24
I'm posting it here as I think it's the most appropriate place
I want to make an online photo album (like google picasa web album or yahoo photos) in php as it seems me the easiest and suitable scripting language. basically I want that my application to be able to to the following things:
 - users login with username and password (multiple accounts)
 - user's ability to create albums, upload photos, organize photos into albums, tag pictures, rename, delete them etc
 - picture editing: resize, basic effects like black&white, sepia and so on (yahoo photos I think is the best example so far)

I know that I need a database backend for this (mysql I believe to be just right) and a domain, even if i believe I can run it locally, at least for a while. so, after you got a glimpse of what I intend to do, how hard do you think this is?
I have basc html and php knowledge and enough time and willingness to learn
any suggestion/advice is useful (links, howtos, tutorials, similar projects that you know, sources)

---

### Post by LaRoza on 2007-04-24
That seems like a good idea; however, as you will have people inserting data into MySQL, do you have enough knowledge or experience with the various security issues?

For a project like this, I would make a small web app and build on it. If you set your sights too high, you could easily be overwhelmed.

---

### Post by karellen on 2007-04-24
I know....I just want people to upload photos and manage their own albums. I found something usefull, a project named gallery2, I installed it on my local machine and I'll give it a try, maybe some good ideas will emerge from it...

---

### Post by aussiedini on 2007-04-24
You could also try coppermine.

---

### Post by karellen on 2007-04-25
I installed last night gallery2 on my machine. now I'm digging into the source code...:D

---

### Post by bvanaerde on 2007-04-25
It depends on what you want to achieve.
I think that, for what you're looking for, both Galler2 and Coppermine will do the trick.

---

### Post by karellen on 2007-04-25
I'm working on it....from what I've seen gallery is a complete application and pretty comprehensive...

---

### Post by dev_person on 2007-04-26
I've been using Gallery for more than a year now. Great application. There are a number of ancillary tools available for it as well for batch uploading or plugins to applications so it's a good platform to try a number of things.

---

### Post by ssodhi on 2007-04-26
Don't forget the AJAX!

:D
-Sanjay Sodhi

---

### Post by kwanbis on 2008-09-01
I'm sure it's a little too late, but [http://www.zenphoto.org/](http://www.zenphoto.org/) is much simpler than copernime or gallery2, and fully functional.

---

