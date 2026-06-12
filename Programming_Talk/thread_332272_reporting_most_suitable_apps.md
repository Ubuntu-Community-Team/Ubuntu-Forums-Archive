---
title: "reporting: most suitable apps?"
date: 2007-01-05
forum: Programming Talk
---

### Post by crofty on 2007-01-05
**The problem**
I am planning a project that will require collecting data (measurements and surveys) from many people and providing the data in a report. For each person there will be about 100 data points which are integrated into generic text to make up a 5 page report. The report for each person will be compiled into a large report. The data would be collected on a laptop or umpc.

**Solutions**
I imagine the data should be stored in a database and a form could be made to allow easy data entry on site. Once the data is in the database, how do I generate the report? My first thought was to use openoffice for the report. I already use mysql and OO for other tasks. I tried tinyreport but couldn't make it work.
Alternatively I found programs in java (which I don't know how to program) such as JasperReports. 

Am I missing an obvious solution?
Any direction appreciated.

Thanks,
JC

---

### Post by pmasiar on 2007-01-05
> **crofty said:**
> I imagine the data should be stored in a database and a form could be made to allow easy data entry on site. 

Entering data using browser and web-based app? Uploading files prepared on laptop to web server for processing? 

> Once the data is in the database, how do I generate the report? ...  I found programs in java (which I don't know how to program)...

Am I missing an obvious solution?

Obvious solution is - you need to make your own custom program to handle it all :-) 

Most people will agree than Python is the best choice as first language for this kind of task (Ruby close 2nd). 

Next step I suggest Django (python web app framework), IIRC all you need to do is (1) describe your database. Django will generate database, and create database entry forms. (2) write your SQL query to get data out, and process them via template to get HTML report.

This way you will have to learn Python, but Python is much easier than average language, and useful for other little (and big) tasks.

IMHO, YMMV. I looked into Django but never used in in production.

---

### Post by crofty on 2007-01-06
Thanks for the reply pmasiar.
While the idea of uploading to a server for processing is appealing, I'm not sure that a network connection will always be available on site. Could I collect data locally on the device and upload when back at the office?

I will look into django and python.
This seems to be a longer road than I had hoped!

Thanks,
JC

---

### Post by pmasiar on 2007-01-06
> **crofty said:**
>  Could I collect data locally on the device and upload when back at the office?

Sorry for confusing you with web-based application - I do tham for living, so most problems for me look like web-based apps. Sure, you can just collect your data on some memory medium, like USB stick, and copy them to the computer. It is your custom program - you can do whatever you want. Your solution will be even simpler simpler than mine :-)

If you do yous plain application as we did in old times before web, IIUC you have steps:

1) collect data on individual laptops in the field
2) when data collectors come back to office and connect to office LAN, copy files to central file repository
3) load data into database
4) process query, generate text files, print them.

All can be done old-fashioned plain way: command line scripts, text files. Python is very good at these tasks.

For database you can use either MySQL you said you are familiar with, or python comes with sqlite (SQL library, single user, with no server running - simpler to administer)

Good luck!

---

### Post by crofty on 2007-01-06
Can I use python to generate a formatted report using data from the database file once I get to step 4?
Thks,
JC

---

### Post by pmasiar on 2007-01-06
Sure. Read up on python formatting (% operator). Also, there are many templating modules for Python - certanly more than Python's reserved words :-)

Formatting is same as sprintf() in C, which is ultimatelly called. Python is nothing more (and nothing less :-) ) than your friendly no-sweat interface to C. :-)

RTFM to learn more: [http://docs.python.org/lib/typesseq-strings.html](http://docs.python.org/lib/typesseq-strings.html) etc.

---

