---
title: "Script Help"
date: 2006-01-10
forum: Programming Talk
---

### Post by rbrugman on 2006-01-10
Hello,
I am in need of a script that runs once every minute, but I have no programming experience.  Here is what I need it to do:

Once per minute I need the script to check this internal page:
[http://192.168.0.50](http://192.168.0.50)

I then need it to check the resulting page for the words "not yet initialized".  If found, the script can end.

If not found, I need the script to run this command:
[http://192.168.0.50/reload.html?Status=&Change=Change](http://192.168.0.50/reload.html?Status=&Change=Change)

I also need it to send me an email when this happens.  Also, maybe a timeout in case my router goes down or something.


If anyone can help me out with this, I'd greatly appriciate it.

---

### Post by rbrugman on 2006-01-11
If someone could help I could even paypal a few dollars.  I'm in serious need of this script. 

Thanks,
Robert

---

### Post by darth_vector on 2006-01-11
you can write the script and then set up a cron job to run every minute. this will send you an email with the output of the script each time it is run.

---

### Post by thumper on 2006-01-11
I'd suggest a simple python script.  The httplib module has a class HTTPConnection.  This class has methods request and getresponse.
```
import httplib
conn = httplib.HTTPConnection('192.168.0.50')
conn.request('GET', '/')
r = conn.getresponse()
if "not yet initialized" not in r.read():
  conn.request('GET', '/reload.html?Status=&Change=Change')
  r2 = conn.getresponse()

```
**Note:** code is untested.  Path variables may not need initial '/' - I don't know.  There is emailing libraries too to do the emailing, but you should be able to add that without too much trouble.

---

### Post by rbrugman on 2006-01-11
Thank you for the script. I'm not familiar with cron (besides that it can run automated tasks).  I can tell if its working so I can help test it.  If you can help me get the emailing stuff working and the script works, I'll paypal you some money.  If only I had taken a programming class before I desperatly needed a script.

If you don't want to, the offer is open to anyone that can help me get a working script.


Thanks!!!

Robert

---

### Post by darth_vector on 2006-01-11
```
crontab -e
```
will let you edit your crontab. an entry like the following should do what you want

* * * * *  /full/path/to/script | mail -s "subject: output from script" myemailaddress@mydomain

---

### Post by ardchoille on 2006-01-11
I posted a crontab/cronjob how-to. you can see it here:

[http://www.ubuntuforums.org/showthread.php?t=102625](http://www.ubuntuforums.org/showthread.php?t=102625)

---

### Post by rbrugman on 2006-01-12
I have two other small things it needs to do.  I don't really care about it emailing me as much, but I would like it know how to get it to recheck if it loads the second URL.

Thanks,
Robert

---

