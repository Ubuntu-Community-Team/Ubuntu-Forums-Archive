---
title: "Trouble running (or installing?) a program"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by cdlam on 2013-03-13
Hi I seem to be having problems running a program that I just installed. It's based on Python, which I have. I followed the fairly simple installation instructions found here: 
[http://weblogo.threeplusone.com/manual.html#download](http://weblogo.threeplusone.com/manual.html#download) 

Basically I ran:

```
sudo easy_install weblogo
```

And got this (not exactly, because I ran the above code again since I didn't copy what it said the first time):
```
Searching for weblogo
Best match: weblogo 3.3
Processing weblogo-3.3-py2.7.egg
weblogo 3.3 is already the active version in easy-install.pth
Installing transformseq script to /usr/local/bin
Installing weblogo script to /usr/local/bin

Using /usr/local/lib/python2.7/dist-packages/weblogo-3.3-py2.7.egg
Processing dependencies for weblogo
Finished processing dependencies for weblogo
chris@ubuntu:~$ 
```

```
/usr/local/bin
``` is definitely in my PATH, so shouldn't I just be able to enter ```
weblogo
``` into my terminal and get something?

When I try entering "weblogo" all that happens is the "chris@ubuntu:~$" goes away....

Semi/definitely confused. Any help is greatly appreciated, thanks!

---

### Post by KnownSyntax on 2013-03-14
Depending on what the application does, it may just be loading something and then either freeze (or run) and not return you back to the normal "chris@ubuntu:~$" text that you are used to seeing. I would suggest looking at the Python log files and any log files that this application does (if it produces any) to see what it's actually doing.

---

### Post by schragge on 2013-03-14
It seems when run without any parameters, weblogo expects sequence data on standard input. Try
```
weblogo --serve
```then open [http://localhost:8080](http://localhost:8080) in your web browser.

---

