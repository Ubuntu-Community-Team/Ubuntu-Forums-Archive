---
title: "Help! with creating a J2ME program using the http connectivity interface"
date: 2011-12-26
forum: Programming Talk
---

### Post by MRA91 on 2011-12-26
So this is what I have to do using the http connectivity interface:


1.Creating two threads – one for communication (receiving and sending) and the other (main) thread will be for interaction with the user. 

2.The main thread will make use of three midlet forms. The first form will ask for web page address (URL) and separately for a delimiter which will separate the words in the URL document, the third form will display the ratio of all symbols on the page and the number of occurrences of the delimiter specified
 
3.The second thread should perform http connectivity to the WWW, utilise the web page address supplied and connect to the appropriate web page and read its content, count all symbols on the chosen page, count the number of occurrences of the delimiter given as user input on the same form as the web page address, calculate the ratio between the two  and pass this information to the first thread to display.


[B]I have many questions but my main concerns are:

1. How to communicate using HTTP interface within a thread

2. What is a delimiter in the context above and how should it be          implemented[/B]

I've been thrown in at the deep end with little programming experience with this assignment. If anyone can share a similar example or answer my concerns I'd be more than happy. 

Thanks in advance.

---

### Post by ofnuts on 2011-12-26
> **MRA91 said:**
> So this is what I have to do using the http connectivity interface:


1.Creating two threads – one for communication (receiving and sending) and the other (main) thread will be for interaction with the user. 

2.The main thread will make use of three midlet forms. The first form will ask for web page address (URL) and separately for a delimiter which will separate the words in the URL document, the third form will display the ratio of all symbols on the page and the number of occurrences of the delimiter specified
 
3.The second thread should perform http connectivity to the WWW, utilise the web page address supplied and connect to the appropriate web page and read its content, count all symbols on the chosen page, count the number of occurrences of the delimiter given as user input on the same form as the web page address, calculate the ratio between the two  and pass this information to the first thread to display.


[B]I have many questions but my main concerns are:

1. How to communicate using HTTP interface within a thread

2. What is a delimiter in the context above and how should it be          implemented[/B]

I've been thrown in at the deep end with little programming experience with this assignment. If anyone can share a similar example or answer my concerns I'd be more than happy. 

Thanks in advance.
1) Have a look at the HttpConnection class and google for sample code around it
2) As I understand it, it is any string that the user enters (on the second form)

But what they call "symbols" isn't clear (cannot be same as "words" other wise the ratio computed will always be 1)

---

