---
title: "Jdic"
date: 2008-03-20
forum: Programming Talk
---

### Post by abds on 2008-03-20
Hi,

I am trying to use this library for loading a web page from within my java application. However I cant seem to get it working. When i try running the app it gives the following exception: 

org.jdesktop.jdic.init.JdicInitException: org.jdesktop.jdic.init.JdicInitException: Can't locate the native browser path!
        at org.jdesktop.jdic.init.JdicManager.initBrowserNative(Unknown Source)
        at org.jdesktop.jdic.browser.WebBrowser.<clinit>(Unknown Source)
        at Browser.jbInit(Browser.java:173)
        at Browser.<init>(Browser.java:69)
        at Browser.main(Browser.java:85)
Caused by: org.jdesktop.jdic.init.JdicInitException: Can't locate the native browser path!
        ... 5 more

I also get the same exception when I try running the demo.

Am using version 0.9.4 of the library and there doesnt seem to be any function allowing me to set the path.
Any ideas on what i might be doing wrong?

---

### Post by abds on 2008-03-20
Also if there might be another way of doing this please point me towards that. Any help would be greatly appreciated!!

---

### Post by Zugzwang on 2008-03-20
Hint: Often you get usable answers when just putting the error message into quotation marks and using google.

So in this case you could have googled for:
```
"org.jdesktop.jdic.init.JdicInitException: Can't locate the native browser path!"
```
(make sure to remove all parts that might refer to your own code).

As a result, you get: [http://forums.java.net/jive/thread.jspa?messageID=254969]("http://forums.java.net/jive/thread.jspa?messageID=254969") which contains the answer. :popcorn:

---

### Post by abds on 2008-03-20
Thanks! Tried what the thread said.. Got rid of the exception but its still not working... This time I get:

*** Jtrace: Executing /home/abasit/Desktop/jdic/mozembed-linux-gtk2
*** Jtrace: connecting ... 0
*** Jtrace: java.net.ConnectException: Connection refused
*** Jtrace: connecting ... 1
*** Jtrace: connected
*** Jtrace: Got event: type = 0 instance = 0
*** Jtrace: send data to socket: 0,0,</html><body></html>
*** Jtrace: Got event: type = 1 instance = 0
*** Jtrace: send data to socket: 0,1,46137361</html><body></html>
*** Jtrace: Exception occured when portListening: Connection reset by peer

tried googling it as you said but that didnt result in any helpful results... 

ideas?

---

### Post by abds on 2008-03-20
Right... so it seems that JDIC has a bug, so it does not support firefox. Any ideas on how i could go about doing this some other way. What I want to do is embed a web browser within my appliation, so i can load/display web pages.

---

### Post by lnostdal on 2008-03-20
looks like the browser has simply closed the connection .. nothing wrong with that, just deal with it on your end..

..handle the exception(s), and you should be ok AFAICT

---

