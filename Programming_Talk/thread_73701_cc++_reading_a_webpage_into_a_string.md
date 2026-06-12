---
title: "c/c++: reading a webpage into a string"
date: 2005-10-09
forum: Programming Talk
---

### Post by wellery on 2005-10-09
Does anyone know how to read a webpage from a given url into a string? So what I want is to end up with the html code in a string. I want to use c/c++.

---

### Post by dtfinch on 2005-10-09
I'm still a little new to Linux programming, so I don't know the "correct" way to do it, but here's an easy, risky way if you trust the url is not malformed:
FILE *fp=popen("wget --quiet -O - http://www.google.com","r") //pipe wget output to a file handle
... //then read fp like a normal file
pclose(fp); //close pipe

popen() is my new favorite function. wget can read the url from a file if you need it to be safer. It can also read from stdin, but popen doesn't support "rw".

---

### Post by wellery on 2005-10-10
That'll do the job. I was looking for a way to do without using a linux program such as wget. I know in java and vb you can use an xml reader to read a webpage into a string from a url. I was looking to do the same thing here. This will do for now however. Thanks

---

### Post by thumper on 2005-10-10
[QUOTE=wellery]That'll do the job. I was looking for a way to do without using a linux program such as wget. I know in java and vb you can use an xml reader to read a webpage into a string from a url. I was looking to do the same thing here. This will do for now however. Thanks[/QUOTE]
Well, if you really want to, open a TCP socket to port 80 of the site that you are wanting to connect to, push through the HTTP request (really quite small), and read the results that it sends you.

The problems with doing it this way is you then have to handle some of the HTTP internals yourself such as redirections, getting frame contents, and just hope that they don't use too much javascript to populate their page.

Or find an HTTP library that someone else has written that does all this for you.

---

### Post by jerome bettis on 2005-10-10
in python you can do

import os
text = os.popen("lynx --accept-all-cookies --dump <url>").readlines()

text will contain the actual text of the page minus the html crap.  for that to work you'll need to apt-get install lynx if it isn't already.  this is kind of a hack and won't work on windows machines etc but it's the easiest way of doing it.

---

### Post by monkeyking on 2005-10-13
Well he says that he want's it in c++ and without any linux progy's.
So I dont really see a solution in python depending on lynx as valid. ;)

---

### Post by wellery on 2005-10-13
I'm not sure if it's going to work but the solution i've got is to use libcurl from:

[http://curl.haxx.se/](http://curl.haxx.se/)

---

### Post by isandir on 2005-10-22
This can be done in C++.  I have a program that does something very similar.  What you need to do is open a socket to the webserver you want your html from.  Then send your get message and read what it sends back to you.  My program just sends the html out to my screen but you could store it in a string.

```
connect(sockd, (struct sockaddr *)&sin, sizeof(sin));
  FILE * readerc = fdopen(sockd, "r");
  FILE * writerc = fdopen(sockd, "w");
  fprintf(writerc, myMessage.c_str());  //mymessage is the get request
  fflush(writerc);
  
  char line[1000];
   char *s=fgets(line,999,readerc);
  for (int i =1;s != NULL;i++){
    printf("%s", line);
     s=fgets(line,999,readerc);
  }
```

Of course there is a lot of setup before this code, but once you have a open connection to a webserver thats all you have to do to get the html out of it.

---

