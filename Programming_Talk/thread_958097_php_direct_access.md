---
title: "php direct access"
date: 2008-10-25
forum: Programming Talk
---

### Post by aaronp on 2008-10-25
Hi all,

I'm currently writing a website for someone which is completely written in Flash (with AS2).
I want to create a call to a php file which will insert values into a mysql database using the AS2 sendandload function.
This is all ok for me but what I am trying to avoid is anyone being able to bypass the Flash movie and insert records into my database by using the php file directly.

Assuming someone can easily decompile the swf file they would be able to see the full URL of the php file that inserts data into the db and would also see all the right parameters to use to make the php script work and simply type the right stuff directly into their browser to insert data. Am I correct?

If so, how do I prevent this sort of thing from happening?

I am reading about sessions etc. but because Flash is downloaded and run locally on the client side I'm not sure if this is an option.

thanks
Aaron

---

### Post by drubin on 2008-10-25
You were right flash is HIGHLY decompile able. 

When the flash file is downloaded you can pass a session var to the flash file.

This would not be so secure as once you have a session it is easy to write scripts and pass that session to the php file. The only idea would be to require them to first login to use your application. then track the inerts on the server side based on their logged in session and only allow logged in members to insert into the db.

I do have a question if you will not be allowing them to hit the url directly what is stopping them from hitting the flash button a few times?

---

### Post by aaronp on 2008-10-25
thanks drubin
you make a good point that i didn't really think of. it would be quicker for them just to use my flash site to continually submit to the database rather than using a url to do it over and over again!
i guess i just need to make sure they cant inject anything malicious and forget about the remote possibility that someone would want to fill up my mysql db table!

---

### Post by drubin on 2008-10-25
You could also get the users IP address and only allow one submission from that IP..?

**EDIT:** Another simple way of stoping people from just inserting stuff into your site would be to use POST over GET. Although this is just as easy while writing scripts It would stop the standard users that would just use their browser.

---

### Post by aaronp on 2008-10-26
yeah thanks, i am using post.

now that I think about it, the same issue exists if someone looks at the source of a normal html page with a form that posts variables to a php file.
they have the variable names, they have the php url and essentially could use this to insert into the database much easier than decompiling the swf file to obtain the same information.
not ntirely sure what i was worried about!

---

### Post by drubin on 2008-10-26
Yes that is true, that is why most of the **good** site will make use of server side checks to see that users have only posted the aloud amounts with in the allowed time spam and from different ip's. Just a simple way of doing it. :)

---

### Post by aaronp on 2008-10-26
thanks drubin.
Can you point me to any tutorials that I can use to learn how to implement these server side checks?

thanks
Aaron

---

### Post by drubin on 2008-10-26
> **aaronp said:**
> thanks drubin.
Can you point me to any tutorials that I can use to learn how to implement these server side checks?

thanks
Aaron

Going to have to get back to you on this... I have pretty much worked it out alone the way from having people break things during testing.... :)

But I do have something you can read about programming that will help you down the line. [http://norvig.com/21-days.html](http://norvig.com/21-days.html)

---

### Post by aaronp on 2008-10-26
thanks again drubin.
That link is very true! 
I've been programming for about 8 years now so am reasonably accomplished in porgramming concepts and specific languages like Java, Python, VB and a bit of C/C++ (if I can remember it from uni!) but am fairly fresh to web-dev so it is pretty exciting sinking my teeth into some of these new concepts and some of the power that php/mysql offers with a pretty easy learning curve (so far...)

---

