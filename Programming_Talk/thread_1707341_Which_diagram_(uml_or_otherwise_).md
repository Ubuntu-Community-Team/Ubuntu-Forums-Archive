---
title: "Which diagram (uml or otherwise ) ?"
date: 2011-03-15
forum: Programming Talk
---

### Post by Shpongle on 2011-03-15
Hi all , I have a server coded in python, theres a small script used to start it on the port and ip and set other command line args. Upon accepting a connection it starts a new thread. I extend the python threaded class and use a new thread for each new connection which then performs all of the required processing before closing the link. That class is the only class I have made

Im wondering what type diagram (uml or otherwise) would be best to represent the server. any suggestions ?

---

### Post by PaulM1985 on 2011-03-15
A system is generally better described using a series of diagrams rather than a single type of diagram.

A UML class diagram would be useful to see the different classes that work together in your system.  It can show the contraints between the relationships (one class can only contain 1:n instances of a different class etc), inheritance, methods that exist for the class and so on.

Class diagram examples:
[http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=class+diagram+example&aq=f&aqi=g3g-m2&aql=&oq=](http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=class+diagram+example&aq=f&aqi=g3g-m2&aql=&oq=)

A UML sequence diagram could show the flow of the application, showing which methods are executed in which order following an event.

Sequence diagram examples:
[http://www.google.co.uk/images?hl=en&q=sequence+diagram+example&wrapid=tlif130019153980310&um=1&ie=UTF-8&source=univ&sa=X&ei=OFl_TYSsOoSnhAePx62oBw&ved=0CCwQsAQ&biw=1259&bih=823](http://www.google.co.uk/images?hl=en&q=sequence+diagram+example&wrapid=tlif130019153980310&um=1&ie=UTF-8&source=univ&sa=X&ei=OFl_TYSsOoSnhAePx62oBw&ved=0CCwQsAQ&biw=1259&bih=823)

You may also like to include a workflow diagram to indicate what should happen, in what order, in more abstract terms.

Flow diagram example:
[http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=flow+diagram+example&aq=f&aqi=g1g-m9&aql=&oq=](http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=flow+diagram+example&aq=f&aqi=g1g-m9&aql=&oq=)

I think in your example class and sequence diagrams would be useful.

Paul

---

### Post by Shpongle on 2011-03-15
> **PaulM1985 said:**
> A system is generally better described using a series of diagrams rather than a single type of diagram.

A UML class diagram would be useful to see the different classes that work together in your system.  It can show the contraints between the relationships (one class can only contain 1:n instances of a different class etc), inheritance, methods that exist for the class and so on.

Class diagram examples:
[http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=class+diagram+example&aq=f&aqi=g3g-m2&aql=&oq=](http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=class+diagram+example&aq=f&aqi=g3g-m2&aql=&oq=)

A UML sequence diagram could show the flow of the application, showing which methods are executed in which order following an event.

Sequence diagram examples:
[http://www.google.co.uk/images?hl=en&q=sequence+diagram+example&wrapid=tlif130019153980310&um=1&ie=UTF-8&source=univ&sa=X&ei=OFl_TYSsOoSnhAePx62oBw&ved=0CCwQsAQ&biw=1259&bih=823](http://www.google.co.uk/images?hl=en&q=sequence+diagram+example&wrapid=tlif130019153980310&um=1&ie=UTF-8&source=univ&sa=X&ei=OFl_TYSsOoSnhAePx62oBw&ved=0CCwQsAQ&biw=1259&bih=823)

You may also like to include a workflow diagram to indicate what should happen, in what order, in more abstract terms.

Flow diagram example:
[http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=flow+diagram+example&aq=f&aqi=g1g-m9&aql=&oq=](http://www.google.co.uk/images?um=1&hl=en&biw=1259&bih=823&tbs=isch%3A1&sa=1&q=flow+diagram+example&aq=f&aqi=g1g-m9&aql=&oq=)

I think in your example class and sequence diagrams would be useful.

Paul

Thanks , I was opting to use a class diagram , but since I only have one class (a big one) I didnt think there would be much point.

I am familiar with the different types of diagrams , Im just trying to get an opinion on how best to represent it given the design. Thanks for your reply .

---

### Post by PaulM1985 on 2011-03-15
It sounds like a sequence diagram is probably more like what you would need.

Paul

---

### Post by Shpongle on 2011-03-15
Yeah , It may be the best way . Thanks Paul

---

