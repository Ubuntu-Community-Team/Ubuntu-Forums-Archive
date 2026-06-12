---
title: "[PHP] Creating Graphs And Charts"
date: 2009-07-15
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-15
Hey,

So i have this data (in JSON format). It looks something like this:

```

{"AAA": "6",  "BBB": "15", "CCC": "19", "DDD": "10"}
{"AAA": "8",  "BBB": "26", "CCC": "29", "DDD": "32"}
{"AAA": "2",  "BBB": "12", "CCC": "15", "DDD": "64"}
{"AAA": "14", "BBB": "54", "CCC": "12", "DDD": "93"}

```

There is a time-stamp associated with each (which will be needed). The timestamps are formatted like this **2009-07-15 11:18:22** (**year-month-day hour:minute:second**).

Now, basically i need to create graphs and charts to represent the data given. The variables (eg: **AAA**) are stock names, and the data (eg: **6**) are their current values. These stocks are not real-world stocks, just stocks from a videogame. I add a new set of variables every 30 minutes, which is 48 sets per day, so it will ad up over time. I have a program running 24/7 to pump the data into the database.

So as you may have guessed what im doing, I need to organize the data that will show me trends, means, medians, highs, lows all the stuff you'd need to take a university level statictics class to know (I have taken the class). I've looked online for a graphing module for php, but couldnt really find one that had throuough examples for what im trying to do. Have you guys ever used google analitics? They give images like:
[IMG]http://i29.tinypic.com/2quixjr.jpg[/IMG]

They are quite detailed, the location where the blip is up saying the date and value was where my mouse was.

Anyways, thanks in advance
~Cody Woolaver

---

### Post by Reiger on 2009-07-15
IIRC PHP has a built-in JSON parser/object model. So that's part 1 of the problem solved.

Also, there is a strtotime() function which reads a time string and returns a UNIX time stamp. The date() function returns a formatted time string according to a UNIX time stamp and a format string. So that's part 2 of the problem solved.

Finally there are various image manipulating libraries which you can use for generating images; and/or you can try to use SVG.

---

### Post by Pyro.699 on 2009-07-15
I knew about **json_decode()**, i didnt know about **strtotime()**, but i still need a libary that someone here has used and have experience using it.

Thanks
~Cody Woolaver

---

### Post by Mirge on 2009-07-15
heh, strtotime() is great.

If you don't mind having the graph generating client-side, you could try using a [jQuery plugin called flot]("http://code.google.com/p/flot/").

---

### Post by Can+~ on 2009-07-15
It makes more sense to have the data rendered on the client side. There are simple HTML tricks that can be done, I remember seeing an article on digg.

[http://www.terrill.ca/design/vertical_bar_graphs/](http://www.terrill.ca/design/vertical_bar_graphs/)

After all, your server should crunch data and send it, the Browser provides a visualization of all that, why not just hand it the job of creating graphs?

---

