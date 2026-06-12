---
title: "HOWTO: 'Mic Boost' Toggle Launcher"
date: 2006-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by chiefofthejojos on 2006-01-18
This HOWTO is for anyone you uses their microphone a lot and is frustrated with the long sequence of clicks required to turn the 'Mic Boost' on or off. I will show you a simple shell script that determines the current value of the 'Mic Boost' setting and toggles it.

First, you need to determine the numid of your 'Mic Boost' control. As far as I know, this id varies from installation to installation. If I am wrong, someone please let me know.
```
amixer controls | grep 'Mic Boost'
``` 
Now open your favorite text editor and paste in the following text:
```

#!/bin/sh
if amixer cget numid=17 | grep on; then
  amixer cset numid=17 off
else
  amixer cset numid=17 on
fi

``` 
and then replace all occurrences of 17 with your own numid. Save this text file wherever you like (this will be it's permanent resting place). Open a terminal and, after changing to the directory of the new file, make the file executable with the following command:
```
chmod a+x <filename>
``` where <filename> is the name of your file.

Finally, just make a launcher on the desktop or wherever that points to this file. Now if you ever want to turn on 'Mic Boost' quickly (for example: your receiving a call on the computer and you want to get the boost on before answering) all you need to do is run the launcher!

This was my first HOWTO and my first shell script ever so if it's awful please let me know.

---

### Post by ashmew2 on 2007-02-04
Thanks for the great thing man , I finally got my mic working on CS (with cedega ) .
 Thanks a Great Lot!!

---

### Post by adverb on 2007-03-27
that's totally awesome. thanks.

this also worked on my slackware box, for the record.

---

