---
title: "advice needed on java/php/email project"
date: 2006-04-06
forum: Programming Talk
---

### Post by amit1947 on 2006-04-06
First of I would like to say that Ubuntu is awesome! I've been reading these forums for a while without posting before but I needed some advice and I know this place is filled with unusually intelligent people so here goes :) 

I am trying to develop an emailer java application that can send emails daily by reading data from a remote mySQL database (each row in the email table has a send-out date) that runs on our host's webserver. Currently a PHP script is sending out these emails and requires a browser to activate this process, but somethings going wrong with it and it often fails some how before sending all the emails out (maybe the browser is closing prematurely?). I decided to completely side step this problem by developing a java app to run automatically every day (crontab) and send out the emails on the office server, I am using the javaMail API through the hosts smtp server. The problem is that the webserver's mySQL server does not allow remote connections (i can not connect using the java mysql connector) so I think the only way to communicate with the database is through a PHP script. I creatd a PHP script that reads the data from the database, email message, subject line etc. and then generates text that it sends to the java app via URLconnection. The java app parses this text and sends out the proper emails, do you think this is a good route to take or is there a better way? 

Thanks in advance for any advice!

---

### Post by sphinx on 2006-04-06
Ok, I'm going to assume you are unable to run your Java app on the same machine as the database. However you are able to run whatever PHP app you'd like on the database machine. Please correct me if these are wrong because they impose constraints that make this a lot harder than it could be.

With those assumptions made, the solution you have outlined is probably ok. I would change one thing though. I would have the Java app initiate the connection and have the PHP script do nothing more than serve up the emails to send in whatever text format you have created.

This way, you can have the Java app query the PHP script, get the text, create emails and send them. After reading your post again, this might even be what you were trying to say anyway.

Then if you'd want to go further you could have the Java app post all the emails it has sucessfully sent back to a PHP script so it could update the database to keep track of what emails have been sent.

---

### Post by amit1947 on 2006-04-06
hey Sphinx, thanks a lot for the reply. I've done exactly what you've said, my java application queries a PHP script for the database info and then proceeds to send emails. The constraints you assumed were correct. Is there any constraint on the size of the text (in terms of memory) that the java gets back from the PHP script in one connection "session" ?

---

### Post by amit1947 on 2006-04-06
Oh yeh I forgot to ask another Ubuntu related question. How can I add the CLASSPATH for a java application for Crontab to find? I think its a different location than for the typical console config files.

---

