---
title: "requesting http data?"
date: 2007-07-01
forum: Programming Talk
---

### Post by iwir3d on 2007-07-01
I am a Pascal programmer for the Windows Platform. Recently I have been learning C++ for Linux (ubuntu). I am having problems understanding how I could have my program request the data of a HTTP page or atl east make the webserver think I visited that url.

In Pascal I could do:
```
IdHTTP1.Get();
```

I think thats right.. Might be wronge tho been a while. I just need to visit the url for me.. =/

Any help or suggestions on what to google for are helpful because im a strong googler but after the first 3 hours of googling in the complete darkness of not knowing wtf to google for gets frustrating.

---

### Post by brooksbp on 2007-07-02
Correct me if I'm wrong anyone, but the most efficient and typical way of doing this is to use sockets.

You can create an application that establishes a TCP/UDP socket connection to a server and then transfer data via the HTTP protocol.

There are probably popular classes that manage TCP sockets for you when programming with the HTTP protocol.

I googled "http request c++".  A useful site that explains a lil more in detail: [http://www.cs.wustl.edu/~schmidt/cs544/socket2.html](http://www.cs.wustl.edu/~schmidt/cs544/socket2.html)

Hope that helped.

---

### Post by pmasiar on 2007-07-02
I cannot help you with C++ way to do it - C++ is not very user-friendly when handling text. But if you can switch languages, try python. [urllib](http://docs.python.org/lib/module-urllib.html) has  urlopen which just returns page for provided URL. Cannot be any easier IMHO :-)

---

### Post by winch on 2007-07-02
Take a look at [libcurl]("http://curl.haxx.se/libcurl/").

---

### Post by iwir3d on 2007-07-02
Well, c++ has been very easy to pick up its just some commands and syntax are different then the pascal I used to know. Thanks everyone for the help I will definatly look at all those options as well as google a bit more now that I have an idea what I am looking for.

---

