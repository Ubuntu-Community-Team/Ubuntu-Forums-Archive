---
title: "where is my download?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by fredfelter on 2008-10-18
Man, this is a discouraging setback on my quest to ¨master¨ Ubuntu/Linux
I´m trying out some apps so I can use my  Garmin GPSr to connect to my laptop and view satellite and map data. So far I´ve been unsucessful getting 2 other apps to see the GPSr so I thought I´d go to the gold plate program GPSBabel and try it. I found it in the Package Manager and it seemed to download without a hitch. Now I can´t find it anywhere. Going back to Synaptic it assures me it is installed (in Utilities - universe?) but a Search for Files brings up nothing.
This is so frigging frustrating I can hardly stand it - probably something really stupid on my part.
Thanks for any clues.

---

### Post by nhasian on 2008-10-18
first in a terminal type

```
sudo updatedb
```

then you can use the locate command like this:

```
locate Babel
```

another command you might find useful is apropos like this:

```
apropos gps
```

apropos searchs the manual page names and descriptions

---

### Post by cariboo on 2008-10-18
You could always open Synaptic highlight the package then go to Properties-->Installed files.

Jim

---

### Post by fredfelter on 2008-10-18
Thanks nhasian but all I found with the locate Babel was an Open Org doc I have on my DT that has the word GPSBabel in it, As for the apropos I got a list of 10 or so items, none of which was GPSBabel

And thanks to you cariboo907. Here is what I found (I tried to copy and paste but couldn):
   /usr/bin/gpsbabel
   /usr/share/doc followed by a bunch of html items
   /usr/share/man/man1/gpsbabel.1.gz

With all the html stuff I guess it looks like a web app instead of an installed one but where is it located?

---

### Post by nhasian on 2008-10-18
i think the locate command is case sensitive.  thats why it didnt find /usr/bin/gpsbabel because we were searching for Babel.  

looks like you found where gpsbabel was installed though in the /usr/bin directory :)

you can just type gpsbabel to run it, or you can make a menu shortcut for it.  

also you can read the manual for it with

```
man gpsbabel
```

---

### Post by scragar on 2008-10-18
you should be able to run it:
```
gpsbabel
```
things in /urs/bin are executables, things in /usr/share are documtentation(```
man gpsbabel
```)

---

### Post by fredfelter on 2008-10-18
Wow, I just learned a new to me) concept tonite. Thanks again to scragar, nhasian and cariboo907.

---

### Post by nhasian on 2008-10-18
great!  i'm glad we can help.  if we helped you resolved your problem, please dont forget to click the thank button, and to close the thread if your question is resolved :)

---

### Post by fredfelter on 2008-10-18
Before I close I´d like to ask where I would go to see the ¨/usr¨ directory, where gpsbabel is located. It doesn´t seem to be a part of my personal files. Apparently it lies in the root directory. I tried ¨cd /¨ but nothing happens for some reason. Is there some way to display the entire hard drive file hierarchy?

---

