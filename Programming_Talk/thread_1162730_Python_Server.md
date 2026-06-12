---
title: "Python Server"
date: 2009-05-18
forum: Programming Talk
---

### Post by Darkade on 2009-05-18
Today I worked in a little python server to control my music over a webrowser (mostly at home with my iPhone) and it works pretty well.

It's the first time I use Python to program a web application, so it's not perfect :lolflag: I tough of doing it with PHP (wich I know kindda well check my site in my signature, 100% orignal PHP code) but I wanted to work with python :P

Anyway I do have a "problem" I want to display some icons but I don't know how to address the petition for an image, does anyone know how con I do that?
Well this is the working site (optimized for iPhone, since that's pretty much where I'll be using it) If it doesn't work probably I've closed the port (doing that in the morrow) or my Desktop is turned off (host it myself... thanks DynDNS) but I'm uploading my source code, in case it helps anyone or that can solve my doubt :D Thanks

[http://arcadelair.homelinux.net:4000/](http://arcadelair.homelinux.net:4000/)

---

### Post by Darkade on 2009-05-20
Bump :D

---

### Post by Darkade on 2009-05-20
Right after I bumped, the solution came to me! Change the MIME in the header. So I did some google research and found that the header I was looking for was image/png LOL

So here's the code, I'm uploading it and the CSS theme. Please test it, and let me know where can I improve. Keep in mind I'm a newbee to Python :P

But please please give me feed back on this :D:D

To run it just go into the folder and then run
```
python music-server.py
```

Server will run in your 4000 port so you can go to your browser and type [http://localhost:4000](http://localhost:4000)

CSS theme is optimized for iPhone, since that's where i'll be using this for the most part

:lolflag:

---

### Post by Darkade on 2009-05-20
And after that it was way to easy to add the rest of the icons, I think now I'm gonna improve on the CSS.

Version with icons attached

---

### Post by Darkade on 2009-05-20
And this is how it looks at the end :D

---

### Post by phrostbyte on 2009-05-20
Not bad, so you are using raw CGI? :)

For a simpler program I thinK CGI is much easier but if you want to make something more complicated web application in the future with python check this out

[http://www.djangoproject.com/](http://www.djangoproject.com/)

---

### Post by Darkade on 2009-05-20
Thanks :D I was actually tempted to use DJango but I tough it was way more complicated than I needed.
I use DJango when I followed a tutorial to setup a quick Offline Wikipedia. It works really great, but for some reason one of the dependencies wouldn't run in my laptop (wich is where I wanted to run it) [http://users.softlab.ece.ntua.gr/~ttsiod/buildWikipediaOffline.html](http://users.softlab.ece.ntua.gr/~ttsiod/buildWikipediaOffline.html)

Anyway that belongs in another thread

EDIT: BTW even after going trough all of that I still don't quite understand what's CGI. Could you explain further please?

---

