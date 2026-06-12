---
title: "automatic database filler script?"
date: 2011-10-18
forum: Programming Talk
---

### Post by tubunu on 2011-10-18
I am required to fill in an online database every single day at work with a topic. To do that, every single day I go online, log in with my name and password, select today's date in the calendar, and click on appropriate button to input my topic, then click Save. To make it easier, I already have a Word document with all the topics for each day, so I simply open Writer, copy and paste into a given text area and save. 

QUESTION: Can this mind-numbing task be turned into a script or a terminal command so that I could fill in a week's worth of topics with a click of a button? 

I assume it is doable, and I would like to ask for some pointers. What knowledge do I need to have in order to do that? I am willing to learn, but I don't know where I should start. I'm not even sure how to ask about this using the right terminology. Could I do it in Python, or would a shell script suffice? 

Thank you in advance.

---

### Post by Jonathan L on 2011-10-18
> **tubunu said:**
> I am required to fill in an online database every single day at work with a topic. To do that, every single day I go online, log in with my name and password, select today's date in the calendar, and click on appropriate button to input my topic, then click Save. To make it easier, I already have a Word document with all the topics for each day, so I simply open Writer, copy and paste into a given text area and save. 

QUESTION: Can this mind-numbing task be turned into a script or a terminal command so that I could fill in a week's worth of topics with a click of a button? 

I assume it is doable, and I would like to ask for some pointers. What knowledge do I need to have in order to do that? I am willing to learn, but I don't know where I should start. I'm not even sure how to ask about this using the right terminology. Could I do it in Python, or would a shell script suffice? 

Thank you in advance.

Hi

I'm guessing it's a web form you're filling in ... which means you're quite likely to be able to do it with creative use of [wget]("http://manpages.ubuntu.com/manpages/lucid/man1/wget.1.html") in a shell script.  You start by looking at the source of the page you have to fill out, and find the HTML <form ...>stuff</form>.  Read the --post-data section of the manual page for wget.  You could also consider [curl]("http://packages.ubuntu.com/lucid/curl").

If it's not a web page ... you'll have to tell us a bit more about it.

Can I ask what kind of mindless task it is?  Why do they want you to do it?

Hope that's of some use.

Kind regards,
Jonathan

---

### Post by oldfred on 2011-10-18
I have not used it but this sounds like it would help.

[http://en.wikipedia.org/wiki/Greasemonkey](http://en.wikipedia.org/wiki/Greasemonkey)

---

