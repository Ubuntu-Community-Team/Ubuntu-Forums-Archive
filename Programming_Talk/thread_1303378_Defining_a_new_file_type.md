---
title: "Defining a new file type"
date: 2009-10-28
forum: Programming Talk
---

### Post by gnepets on 2009-10-28
I am looking into defining a new file type for use in a specific application.  What I want to do specifically:

create a zip file with a structure like
zip
:package.xml  //to describe the contents and what to do with them
:<directory>  // 0 or more times
:<file>  // 1 or more times

Questions:
1) do I have to assign a new MIME type to have only a given specific program handle this, or does file extension affect this in a given way?
2) would a different mime type affect a library like libgsf recognising this as a zip file?
3) do you know of a way to change mime types, googling has given me few answers, mostly drowned out by problems with mime type associations?

If you could answer one or all of these questions I would very much appreciate it, until that time I will continue searching.

Regards,
Stephen.

---

### Post by 0cton on 2009-10-28
First of AFAIK most MIME types are detected by their [magic number](http://en.wikipedia.org/wiki/Magic_number_(programming)) and not by their extensions! 
but you don't need to assign it a new MIME type, a MIME type is needed to identify it , usually via a network so you can choose with program can handle the file (ex a video is for totem if a site return the mime type etc)
You create your own file, and you just open and handle it with your program, usually in Linux/Ubuntu, files are recognized by their magic number as well (rename an .mp3 to a .jpg for example) so it will be by default recognized as a zip, you can either change the MIME type/magic number (not recommended) I would recommend a new file association instead.
2) a mime type can affect programs that will try to open it as they won't recognize the magic zip number/signature and will think it's not a zip
3)according to wikipedia.org is PK\003\004 hex: 50 4B 03 04 (just open in a hex editor :P) beware if you change it to a non-registered MIME browsers won't be able to accurate open it (in case you want to stream for example not your Case I assume)
Nevertheless I would recommend not changing it :)

---

### Post by gnepets on 2009-10-28
> **0cton said:**
> First of AFAIK most MIME types are detected by their [magic number]("http://en.wikipedia.org/wiki/Magic_number_%28programming%29") and not by their extensions! 
but you don't need to assign it a new MIME type, a MIME type is needed to identify it , usually via a network so you can choose with program can handle the file (ex a video is for totem if a site return the mime type etc)
...
files are recognized by their magic number as well (rename an .mp3 to a .jpg for example) so it will be by default recognized as a zip,
so you can handle files based on MIME+extension, but still allow it to be opened in an archive program? (that would be even better in my circumstance, but file type assosciations will have to work on linux, windows and max os x.  not sure what I have to do in this case)
> **0cton said:**
>  Nevertheless I would recommend not changing it :)
I am glad to have your recommendation, I did not understand what MIME types were a couple of hours ago :).

regards,
Stephen.

---

