---
title: "Understanding programming directory sturcture"
date: 2007-09-23
forum: Programming Talk
---

### Post by cjnkns on 2007-09-23
I am at a bit of a lost about how to develop for a particular directory sturcture.
For example the hosting company I just set up shop with supports java 4 which is ok i guess.
But when I ftp to the servers I see a directory structure I am not familiar with


I see this

   /
    cgi-bin
    logs
    private
    public

Now the Faq's say that anything that i want the public to see meaning my web pages should go in the public folder.
But,how do i make this work with the standard java directory structure?

I am used to the standard as shown below but how would I get this to work with their directory structure? If I put WEB-INF in public won't everyone see it? 

index.html
page1.jsp
page2.jsp
WEB-INF
  classes
  lib

---

