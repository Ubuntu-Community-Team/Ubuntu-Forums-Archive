---
title: "Java/Flash based Webcam viewer?"
date: 2007-10-07
forum: Programming Talk
---

### Post by Peter1234123 on 2007-10-07
Does anyone know how I would go about making a Java/Flash app. that can communicate with a webcam directly, so someone could view the webcam, by going to an IP/Port...if anyone knows how to do this, or even source would be appreciated :)....I will be very grateful. Thank you.

---

### Post by Ramses de Norre on 2007-10-08
For java: your webcam probably sends out a jpeg stream which you can easily manipulate. Look at [JMF](http://java.sun.com/products/java-media/jmf/index.jsp) (Java Media Framework) and especially the javax.media package for useful classes.

For making it a webapp you'll want to use a servlet that outputs the jpeg's.

[This](http://www.mutong.com/fischer/java/usbcam/) is something I found about a guy that tried to do something similar, his source is on the site.

---

