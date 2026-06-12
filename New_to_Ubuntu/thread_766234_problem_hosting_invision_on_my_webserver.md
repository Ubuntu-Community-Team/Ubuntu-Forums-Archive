---
title: "problem hosting invision on my webserver"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Dev'olution on 2008-04-25
This is a follow on from: [http://ubuntuforums.org/showthread.php?t=766214](http://ubuntuforums.org/showthread.php?t=766214)

my webserver is hosted at: [http://220.245.169.243/forums](http://220.245.169.243/forums)

any ideas as to why i am unable to do anything but see a trimmed down version of the forum itself... as i can't click anything :S

Ideas guys? :(

---

### Post by Xiong Chiamiov on 2008-04-25
How did you install it?  It looks to me like you're missing a css file or something's not going right server-side.

EDIT: clicking a link tried to connect me to localhost, which obviously won't work, as I'm not running apache right now.  You need to fix your links to connect to *your* server, not with hard links to localhost.  You'll notice that if you look the source, you'll see for example that it's trying to import the css file at [http://localhost/forums/style_images/css_2.css](http://localhost/forums/style_images/css_2.css) .

---

