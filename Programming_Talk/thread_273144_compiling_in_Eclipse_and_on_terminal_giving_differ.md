---
title: "compiling in Eclipse and on terminal giving different results"
date: 2006-10-07
forum: Programming Talk
---

### Post by styracosaurus on 2006-10-07
I am working on a BitTorrent program for a class. I have been using whatever editor and compiler suits me at the moment, depending on where I am (home, school, labs on campus etc).

This afternoon I was stuck waiting for a TCP peer wire protocol message from a peer client, and when I compiled on the terminal using the JDK installed with "sudo apt-get install sun-java5-jdk" or something similar (definitely ver 5 though) I was not getting a response.

I have used Eclipse before, but it's slow on my machine, and I started it up and imported the source and tried it there and I was able to get a response. Eclipse's settings point to a JDK in my home folder that I downloaded from Sun, not the GNU compiler that is installed when you install it from Ubuntu's repositories.

THEN I tried to use the full path to Sun's "javac" and "java" on the command line and compiled the same source in a terminal and in Eclipse, and STILL got different results.

I am confused by this. Hopefully I was clear in the post, I am sorry if it is a little hard to understand. I just don't understand why they would still be different. I'm hoping someone who knows how to use Java or Eclipse much better than I do can illuminate this issue.

Thanks

---

### Post by firebadger on 2006-10-08
Eclipse uses its own compiler not the JDK's javac.  You can configure it's settings, for example 1.5 compliance, in Window>Preferences>Java>Compiler.

---

