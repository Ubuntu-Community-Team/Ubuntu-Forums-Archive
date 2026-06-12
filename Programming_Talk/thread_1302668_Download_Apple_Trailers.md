---
title: "Download Apple Trailers"
date: 2009-10-27
forum: Programming Talk
---

### Post by EMCGFX on 2009-10-27
Here is the way to download apple trailers to watch offline with VLC ;)

Add this following code in .bashrc or .bash_alias files.

```
# Download Apple Trailers
alias qdl='wget -U QuickTime/7.6.4 '
```

( you can also change the version from 7.6.4, to newer one when its out)

Then use it like this;

qdl [http://movies.apple.com/movies/lionsgate/saw6/sawvi_h480p.mov](http://movies.apple.com/movies/lionsgate/saw6/sawvi_h480p.mov)

Note: The original link was without "h" in front of the 480p. You need to add that manually ;)

Here is the original trailer link;
[http://movies.apple.com/movies/lionsgate/saw6/sawvi_480p.mov](http://movies.apple.com/movies/lionsgate/saw6/sawvi_480p.mov)

Most of the trailers downloading very quick from 250kps up to 1mbps depending on your internet connection speed ;)

If I write a better function for this, I will post it here ;) Enjoy.

---

### Post by hachre on 2009-12-23
Thanks a lot :)

---

### Post by war59312 on 2010-01-20
Update:

Getting close...

From [http://linuxtidbits.wordpress.com/2009/08/30/download-apple-trailer-fix/](http://linuxtidbits.wordpress.com/2009/08/30/download-apple-trailer-fix/)

> #!/bin/bash
# atget - download trailers from Apple website

# Usage if no parameters given
if [ -z $@ ]; then
  echo " atget <apple-trailer-url>"; exit
fi

# Prepend 'h' before resolution to create a valid url
newurl=$(echo $@ | sed 's/_\([0-9]*[0-9][0-9][0-9]\)p.mov/_h\1p.mov/g')

# Change 'http://movies.apple.com/movies/' to 'http://www.apple.com/movies/' to create a valid url

# Download trailer and save to the desktop
wget -U QuickTime/7.6.2 "$newurl" -O $HOME/Desktop/${@##*/}Now if only i knew regex

No longer works.

Any ideas? I tried faking referer even but no luck.

I tried both of these:

> wget -U QuickTime/7.6.2 --referer=http://www.apple.com/trailers/lions_gate/sawvi/hd/ [http://movies.apple.com/movies/lionsgate/saw6/sawvi_h480p.mov](http://movies.apple.com/movies/lionsgate/saw6/sawvi_h480p.mov)

wget -U QuickTime/7.6.2 --referer=http://www.apple.com/trailers/lions_gate/sawvi/hd/ [http://movies.apple.com/movies/lionsgate/saw6/sawvi_480p.mov](http://movies.apple.com/movies/lionsgate/saw6/sawvi_480p.mov)Result was it downloading the html index page. :(

```
Resolving movies.apple.com... 65.222.174.35, 65.222.174.65
Connecting to movies.apple.com|65.222.174.35|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://www.apple.com/trailers/ [following]
--2010-01-20 20:21:24--  http://www.apple.com/trailers/
Resolving www.apple.com... 72.247.109.15
Connecting to www.apple.com|72.247.109.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24243 (24K) [text/html]
Saving to: `index.html

100%[======================================>] 24,243      --.-K/s   in 0.06s   

2010-01-20 20:21:24 (366 KB/s) - `index.html' saved [24243/24243]
```

---

### Post by hachre on 2010-01-21
```
wget -U QuickTime/7.6.4 http://movies.apple.com/movies/lionsgate/saw6/sawvi_h480p.mov
```

still works for me!

---

### Post by ron999 on 2011-05-03
> **hachre said:**
> ```
wget -U QuickTime/7.6.4 http://movies.apple.com/movies/lionsgate/saw6/sawvi_h480p.mov
```

still works for me!

Works for me too!
Thanks buddy.:)
```
wget -U QuickTime/7.6.9 http://trailers.apple.com/movies/independent/roadtonowhere/roadtonowhere-tlr1_h480p.mov
```

---

