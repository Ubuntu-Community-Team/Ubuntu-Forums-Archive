---
title: "Python Help on bug fix :)"
date: 2009-12-30
forum: Programming Talk
---

### Post by Mrcwolff on 2009-12-30
```

from time import strftime
import smtplib

today = strftime("%Y-%m-%d")
file={"member@yahoo.com":"2009-12-30", "member@gmail.com":"2009-12-31"}

for i in file:
  if file[i] == today:
     SERVER = "localhost"

     FROM = "admin@yahoo.com"
     add = i
     address = [add]
     TO = address 

     SUBJECT = "Happy Birthday!"

     TEXT = "This message was sent for birthday."

     message = """\
     From: %s
     To: %s
     Subject: %s

     %s
     """ % (FROM, ", ".join(TO), SUBJECT, TEXT)

     server = smtplib.SMTP(SERVER)
     server.sendmail(FROM, TO, message)
     server.quit()
 
  else:
     pass

```

It's auto emailer for people having birthday. And script triggered by cronjob:
```
blah**** python /home/blah/blah/birthday.py(it will run everyday once)
```

the test email address in dictionary isn't getting email. Please take a look at this script
thank you in advance.
@Marc

---

### Post by Mrcwolff on 2009-12-31
got it working but
from:
to: 
subject:    areas empty yet appears inside the message.
Got me bugging like hell.
any ideas?
thanks

---

### Post by Bodsda on 2010-01-01
I dont know much about the smtp library, Try adding some print statements in there to make sure the variables contain the expected data.

I dont mean to be rude, but did you pull this code from a book or other resource? Perhaps you could supply the original source, then we can take a closer look.

The code itself seems quite messy, there is a few pointless variables

---

### Post by Mrcwolff on 2010-01-02
multiline string got extra step?
the code is mine and messy i know :)
point the extra varaible for me please
i need it to be dynamic, later mysql gonna be playing here.
to address should be a list, if that what you pointing.
i think i got header or body issue.
---------------------------------------------
update:
so i got cronjob result emailed to myself and got error saying mimetext, mimemultipart is missing in python module
kkkk so hoping that mimewriter is still there.



import MimeWriter

  message = StringIO.StringIO()
  writer = MimeWriter.MimeWriter(message)
  writer.addheader('Subject', ' Happy Birthday! ') 
  writer.startmultipartbody('mixed')

  part = writer.nextpart()
  body = part.startbody('text/html')
  body.write('<html>')
  body.write('<b>birthday!</b>')
  body.write('<br><br>')
  body.write('<p><font size="3"> messagee: </font></p>')
  body.write('<h2 style="color:black">')
  body.write('ding</h2>')
  body.write('<p><font size="3"> test. </font></p>')
  body.write('</html>')
  writer.lastpart()
  smtp = smtplib.SMTP('localhost')
  smtp.sendmail('a@mail.com', 'a@yahoo.com', message.getvalue())
  smtp.quit()
will try this sample.

---

### Post by Mrcwolff on 2010-11-10
This auto email is on demand but I couldn't find anything on the internet so I am posting functional one.
This one checks dates with today's date, if matched by the list, will proceed to email everyone in the list.
Many people have asked this, so here it is:
```

import MimeWriter
import smtplib 
import StringIO
from time import strftime


# Add email addresses here in the list.
# Example: "email@domain.com","email@domain.com"

emails=["email","email", etc . . .]
 
# Add dates you need on below list.
events=["11-13","11-22", etc . . .]

today = strftime("%m-%d")

for e in emails:
	for d in events:
		if d == today:
			sender = "admin@usarmy.gov"
			recv = e
			zahia = StringIO.StringIO()
			writer = MimeWriter.MimeWriter(zahia)
			writer.addheader('To', recv)
			writer.addheader('From', sender)
			writer.addheader("Subject", "Hello World")
			writer.addheader('MIME-Version', '1.0') 
			writer.startmultipartbody('mixed')
			part = writer.nextpart()
			body = part.startbody('text/html')
                        body.write('Bunch')
                        body.write('of')
                        body.write('html')
                        body.write('should be ')
                        body.write('here')
                        writer.lastpart()
			smtp = smtplib.SMTP('localhost')
			smtp.sendmail(sender, recv, zahia.getvalue())
			smtp.quit()
		else:	
			pass

```

---

### Post by abhilashm86 on 2010-11-10
Hey when i look at this code, i've a few queries 
```

emails=["email","email", etc . . .]
 
 
# Add dates you need on below list.
events=["11-13","11-22", etc . . .]
```

Your program checks for events date, then it index to emails [] array, if i'm right.Isn't it better to use a tuple datastructure like

```
[(date, email), (, ), (, )]
```,

since an error in indexing can be a disaster!!


Can we import birthdates from facebook, google calenders and push them onto tuple?? If not above method, are you manually including everyone's birthdate and email??

---

### Post by Bodsda on 2010-11-10
I would suggest that a dictionary approach would be best here. Have the emails as the key and the dates as the value, then lookup the values to get a list of emails whose birthday match todays date.
 
Some help on dictionary lookups. [http://www.daniweb.com/code/snippet217019.html](http://www.daniweb.com/code/snippet217019.html)
 
Hope this helps someone,
Bodsda

---

### Post by abhilashm86 on 2010-11-10
> **Bodsda said:**
> I would suggest that a dictionary approach would be best here. Have the emails as the key and the dates as the value, then lookup the values to get a list of emails whose birthday match todays date.
 
Bodsda

yes Bodsa, thats a efficient data structure for this email purpose. I remember key-value pair and dictionary interrelated!! thanks:)

---

### Post by Mrcwolff on 2010-11-13
@Abhil
Hi,
Yes it is being put manually at this time.
But future plan is fetching it from joomla database. 
So dic, tuple or list not that important issue.
@bodsda
Maybe you could tell me how to access joomla database and put in my code?
That would make my dream come true :) hehehehe.
Or anyone who can manage this will be doing a great community work and betterment of human kind :) LOL

---

### Post by Bodsda on 2010-11-26
> **Mrcwolff said:**
> @Abhil
Hi,
Yes it is being put manually at this time.
But future plan is fetching it from joomla database. 
So dic, tuple or list not that important issue.
@bodsda
Maybe you could tell me how to access joomla database and put in my code?
That would make my dream come true :) hehehehe.
Or anyone who can manage this will be doing a great community work and betterment of human kind :) LOL
 
Joomla is built with php on top of a MySQL database, so assuming you know where the database lives, you can access it using the python mysqldb api 
[http://www.kitebird.com/articles/pydbapi.html](http://www.kitebird.com/articles/pydbapi.html)
 
Bodsda

---

### Post by ziekfiguur on 2010-11-26
> **Bodsda said:**
> I would suggest that a dictionary approach would be best here. Have the emails as the key and the dates as the value, then lookup the values to get a list of emails whose birthday match todays date.


Why not have the date as a key and a list of names as a value, that way you need only one lookup.

---

