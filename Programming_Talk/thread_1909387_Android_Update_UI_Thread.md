---
title: "Android Update UI Thread"
date: 2012-01-15
forum: Programming Talk
---

### Post by shashanksingh on 2012-01-15
An Activity of mine has created the UI.
I made a new thread which does some work, it has to do the work infinitely in intervals, and it was supposed to update the UI.

i.e, The thread searches for bluetooth devices and has to update the UI after every five seconds.

However, android gave me an error stating that I cannot edit the UI from any other thread apart from the one it was created in.

So how should I approach it?

Can I just make an infinite loop in onResume() of the Activity?

Is there any simple way my thread can just tell the Activity to "Update the UI"?

---

### Post by fct on 2012-01-16
You need to use a Service that runs in the background, and make the Activity listen for updates from the service so that it updates itself.

Check this tutorial:

[http://www.vogella.de/articles/AndroidServices/article.html](http://www.vogella.de/articles/AndroidServices/article.html)

---

### Post by fct on 2012-01-17
Ah, seems like it's not really necessary to use a Service:

[http://www.vogella.de/articles/AndroidPerformance/article.html](http://www.vogella.de/articles/AndroidPerformance/article.html)

---

