---
title: "Trying to parse URL variable to Bash Script using Flashgot Firefox Addon"
date: 2009-11-12
forum: Programming Talk
---

### Post by pluckypigeon on 2009-11-12
I'm trying to run a simple script from Firefox using Flashgot:

```

#! /bin/bash
sp-sc $1 8908 8909 & 
#TRYING TO SET $1 as URL Variable
sleep 5 && vlc http://localhost:8909

```

I am aware that there are better ways of starting sp-sc but once I can suss this out it will lead to some more useful things for me.

I set Flashgot to run my simple script but I can't seem to find a way to set the url link to a variable e.g $1

Any help, or comments, would be really appreciated.

---

