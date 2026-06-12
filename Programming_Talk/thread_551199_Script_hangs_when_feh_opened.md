---
title: "Script hangs when feh opened"
date: 2007-09-14
forum: Programming Talk
---

### Post by Omega2Four on 2007-09-14
Hey,
I'm trying to make a simple script that will grab an image from the web, display it in feh and automatically update that image every 5 mins.  So far it works as far as getting an image when its new, but when I run it it will hang in feh until I manually close the feh window, then it will sleep the assigned time and do it again like I want to..the only problem is I want feh to stay open and the image to automatically change in the program...here is the code..plllease help!

```
#!/bin/sh



while wget -N http://image.weather.com/web/radar/us_btv_closeradar_plus_usen.jpg

do 

wget -N http://image.weather.com/web/radar/us_btv_closeradar_plus_usen.jpg

	
feh us_btv_closeradar_plus_usen.jpg

sleep 10 #I'm using this just so I dont have to wait 5 mins while testing, doesnt matter it hangs at feh anyway


done
```

-Greg

---

### Post by slavik on 2007-09-14
the way scripts work is you issue a command and wait until it finishes, then go on to the next command, normally, when running programs, they finish when they exit/quit.

what you may do involves some special program behavior, iow. if feh is already running the new instance of feh has to tell the original feh session that there is a new image to be displayed (this is how media players can add stuff to the playlist isntead of creating a second player).

---

### Post by kerry_s on 2007-09-14
that scripts not right for what you want, i'm not on linux, so can't test.

---

### Post by kerry_s on 2007-09-14
okay, you should really use "man feh" or "feh -h"

from that it looks like this will work->

```
#!/bin/sh
feh -G -R 300 http://image.weather.com/web/radar/us_btv_closeradar_plus_usen.jpg

```

---

