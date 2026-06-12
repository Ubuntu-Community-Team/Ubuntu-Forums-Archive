---
title: "Make Rainlendar lite show your Google Calendar entries"
date: 2009-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by bademeister on 2009-12-06
Here is how to pull your google calendars into rainlendar lite:

First thing you'll need is to find out the private ical address of the Google calendars you want and put it into a file, I called mine  icals.txt ;) To find the address go to Google calendar, click on settings, click on calendars, click on the calendar you want (if you have several) , scroll all the way to the bottom where it says "Private Address" and then click on the green ICAL button. It will show you an address, copy that into your ical file. Put the name of the calendar in front of it, followed by a colon and a space. So my first entry in the file looks like this (all one line)
```
Paul: http://www.google.com/calendar/ical/paul.koerbitz%40googlemail.com/private-XXXXXXXXXXXXXXXXXXXXXXXXXXXX/basic.ics
```
Repeat this for all the calendars you want to show up in rainlendar.

Ok, now for the hacking:  create the following python script:
```

#!/usr/bin/env python
"""Downloads calendars in ical format.

Takes two arguments:
first	: location of file containing the ical URLs.
second: directory where the ical calendars should be saved"""

import os
import sys
import re
import urllib

icals = open(sys.argv[1])

for line in icals:
	nextical = re.search('(.*):\s+(.*)',line).groups()
	outfile = os.path.join(sys.argv[2],nextical[0]+".ics")
	urllib.urlretrieve(nextical[1],outfile)

```

and save it (I called mine get-icals.py) and make it executable:
```
chmod +x get-icals.py
```. 
What this does is that it goes through the file with your ical urls, splits each line at the first colon (that's why you should save them in the form ```
name: [http://.](http://.)...
```), gets each ical file from google, and saves them as name.ics in a path specified by the second argument given to the script. So you want to call it like so
```
get-icals.py /path/to/icals.txt /path/to/output/
```

Once you called the script, the calendar files from google should be in the directory you specified and you can import them in rainlendar (right click on it -> Options -> Calendars -> Add ... -> locate the .ics files). Be sure to change the "Monitor changes" option to "Yes", otherwise this exercise would be quite useless ;). I also changed "Read only" to "Yes" to remind myself that this "syncing" is one-way only, from Google to rainlendar (if you want two way, you would have to get the pro version, I suppose).

Ok, now to actually keep rainlendar synced, you have basically two options. Either hook the python script to a scheduler (I used cron) or create a launcher for the script and call it (click on it) whenever you want to sync. For cron I used (good post on cron [here]("http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/"))
```
$sudo crontab -e
```
and entered
```
0 * * * * /home/paul/bin/get-icals.py /home/paul/.icals/icals.txt /home/paul/.icals/
```
which makes cron update the icals every 60 which is sufficient for my not so rapidly changing schedule ;).

also posted on [my blog]("http://paulkoer.wordpress.com/2009/12/06/make-rainlendar-show-your-google-calendar-entries/").

Enjoy!
Paul

---

### Post by ebruzzone on 2010-02-22
Hi! this is a great tutorial. I am a bit stuck on the part

> gets each ical file from google, and saves them as name.ics in a path specified by the second argument given to the script. So you want to call it like so
Code:

get-icals.py /path/to/icals.txt /path/to/output/




where should we include this? on the get-icals.py file? :confused:

thanks!

---

### Post by bademeister on 2010-07-07
> **ebruzzone said:**
> I am a bit stuck on the part

where should we include this? on the get-icals.py file? :confused:


Hey,
sorry for taking so long, somehow I don't get informed anymore when somebody replies to my threads... I guess I should turn it back on again.

As to your question: you need to change the arguments passed to the script (not the script itself) to your directories form wherever you call it.

So suppose you just want to create a desktop launcher, and everything (get-icals.py, icals.txt and the files to download) should be / go into the folder */home/YOURUSERNAME/Icals/*, then do the following:

Right click on you desktop
Select *"Create Launcher"*
Type *"Update Rainlendar"* into the Name field 
Into the command field put *"/home/YOURUSERNAME/Icals/get-icals.py /home/YOURUSERNAME/Icals/icals.txt /home/YOURUSERNAME/Icals/"*
And click *"OK"*
(Do not type the " " only what is in between)

Clicking on the launcher should then initialize the update process.

kind regards
Paul

---

