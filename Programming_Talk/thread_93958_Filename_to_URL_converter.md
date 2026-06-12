---
title: "Filename to URL converter"
date: 2005-11-23
forum: Programming Talk
---

### Post by fourchannel on 2005-11-23
I have a ton of mp3's on my server. And I like to listen to them at work by streaming them off the system.

For 3k of songs, clicking and choosing each one gets really old.

However most mp3 players take a M3U file, i.e. a file that has the http location of each and every single mp3 on the system.

Here's how I set it up...

you need awk or a clone installed for the script to work.

lets say my apache server hosts out of the directory    /var/www/
so I want to find all the mp3's in the webserver directory and then set them up for totem, winamp, Media player, etc to play them.

```

find /var/www/ -iname *.mp3 -print

``` 
and that craps out this nice list such as this one:

/var/www/music/A Perfect Circle - 01 - The Package.mp3

2 most important things are, you have to get rid of that "/var/www/" and replace it with "http://my.domain.com/" and you have to get rid of those spaces and convert them to %20

this code i set up does most of the URL replacements for you.

it takes standard input and then redirects to standard out.

so what i would use is this:

```
find /var/www/ -iname *.mp3 -print | URL_PROGRAM > /var/www/playlist/PLAYLIST.m3u
``` 

and it would give me links like this:

```

http://my.domain.com/music/A%20Perfect%20Circle%20-%2001%20The%20Package.mp3

``` 

  and a file to open with Totem, or Winamp

```

http://my.domain.com/playlist/PLAYLIST.m3u

``` 

modify it how you need to. right now the code does NOT replace the starting directory, but just uncomment it and place it before the rest of the code, and set up your apache's directory and your domain and it will make it for you.

```
#!/bin/bash

# this shell script takes standard input text and converts it to an acceptable URL.
# 
#
# 

# replaces dir with a placeholder  http://URL/
#uncoment this and set it up for your webserver if you have one, then pipe it 
#right to the rest of the code
#awk '{gsub("/var/www/","http://URL/");print}' | uniq

awk '{gsub("%","%25");print}' | uniq |awk '{gsub("#","%23");print}'| uniq | awk '{gsub(" ","%20");print}' | uniq | awk '{gsub("&","%26");print}' | uniq | awk '{gsub(":","%3A");print}' | uniq | awk '{gsub(";","%3B");print}' | uniq | awk '{gsub("<","%3C");print}' | uniq | awk '{gsub("=","%3D");print}' | uniq | awk '{gsub(">","%3E");print}' | uniq | awk '{gsub("@","%40");print}' | uniq | awk '{gsub("`","%60");print}' | uniq | awk '{gsub("{","%7B");print}' | uniq | awk '{gsub("}","%7D");print}' | uniq | awk '{gsub("~","%7E");print}' | uniq | awk '{gsub(" ","%20");print}' | uniq


``` 

Only use with adult supervision

---

### Post by Roptaty on 2005-11-23
```

#!/usr/bin/env python2.4
import urllib
import sys


for file in sys.stdin:
  file = urllib.pathname2url(file[:-1])
  print file.replace('/var/www', 'http://www.mydomain.com'); 

```

---

### Post by fourchannel on 2005-11-23
>  #!/usr/bin/env python2.4
import urllib
import sys


for file in sys.stdin:
  file = urllib.pathname2url(file[:-1])
  print file.replace('/var/www', 'http://www.mydomain.com');   
damn. You win.

but really, thanks man. That is so much easier and lighter to work with.

---

