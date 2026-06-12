---
title: "need help figuring out how to email log files. should be easy!"
date: 2010-09-25
forum: Programming Talk
---

### Post by gopher2x on 2010-09-25
folks i have a logfile that i would like to be notified via email when there is a certain occurrence of an event.
Right now i can monitor the file like this

tail -f /var/log/events.log | grep 2331

i will see only events from station 2331
now i have figured out command line email with sendemail


sendemail -f [email]src@email.com[/email] -t [email]dst@email.com[/email] -m test -s smtp.email.com:587 -o tls=yes -xu username -xp password -u Subject -m message 

I can specify the message body by
 -m "message",
 STDIN, 
or -o message-file=FILE

So how can i connect my grepped logs to this email. Needs to happen 24/7, and needs to happen as soon as the event occurs, no cron jobs every now and then...

i have tried 
tail | grep | sendemail 
but sendemail gives up waiting for the CTRL-D it...

any ideas??????

---

### Post by gmargo on 2010-09-25
See the **logcheck** package. [http://packages.ubuntu.com/lucid/logcheck](http://packages.ubuntu.com/lucid/logcheck)

---

### Post by Pyro.699 on 2010-09-25
Not sure if this will help or not...

[http://ubuntuforums.org/showpost.php?p=9848605&postcount=11](http://ubuntuforums.org/showpost.php?p=9848605&postcount=11)

It would be easy enough to call that script from a command and have all the information sent...

Just offering my suggestion ^^
~Cody

---

