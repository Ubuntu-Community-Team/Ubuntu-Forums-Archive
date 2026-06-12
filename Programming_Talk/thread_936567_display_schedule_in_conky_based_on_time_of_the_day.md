---
title: "display schedule in conky based on time of the day"
date: 2008-10-02
forum: Programming Talk
---

### Post by nashrafeeg on 2008-10-02
i have written a small web scarping python script to grab my uni's time table and out put it to a file. the file is formated as bellow 
> 
MON,06-Oct-08|08:30 - 09:30|L1 - 7 TPM|CT050-3-3-PRMGT-L-1|S. MOHANARAJAH
MON,06-Oct-08|09:35 - 11:05|L1 - 7 TPM|CT050-3-3-PRMGT-T-1|S. MOHANARAJAH
MON,06-Oct-08|13:45 - 15:15|1-1:ROOM-2 ENT3|BM018-3-3-ENTM-T-1|DR RAMACHANDRAN S/O PONNAN
MON,06-Oct-08|15:30 - 16:30|1-1:ROOM-2 ENT3|BM018-3-3-ENTM-L-1|TEOH AH BAH
TUE,07-Oct-08|08:45 - 10:15|2-6:ROOM-3 ENT3|CT050-3-3-PRMGT-T-1|S. MOHANARAJAH
TUE,07-Oct-08|12:05 - 13:35|1-1:ROOM-2 ENT3|CT013-3-3-CSS-T-1|ANUSHIA INTHIRAN
TUE,07-Oct-08|13:45 - 15:15|1-1:ROOM-2 ENT3|BM018-3-3-ENTM-T-1|DR RAMACHANDRAN S/O PONNAN
WED,08-Oct-08|08:45 - 10:15|G-3:ROOM-2 ENT3|CT031-3-3-FWLAN-T-1|DAVID TAN GEI KAR
WED,08-Oct-08|11:00 - 12:00|G-3:ROOM-1 ENT3|CT013-3-3-CSS-L-1|ANUSHIA INTHIRAN
THU,09-Oct-08|08:45 - 10:15|G-3:ROOM-2 ENT3|CT031-3-3-FWLAN-T-1|DAVID TAN GEI KAR
THU,09-Oct-08|10:35 - 12:05|G-3:ROOM-1 ENT3|CT013-3-3-CSS-L-1|ANUSHIA INTHIRAN
THU,09-Oct-08|13:45 - 14:45|G-3:ROOM-2 ENT3|CT046-3-3-NWT-L-1|DAVID TAN GEI KAR
THU,09-Oct-08|16:00 - 17:30|G-3:ROOM-2 ENT3|CT046-3-3-NWT-T-1|NURUL HANIZA BINTI MOHTAR
FRI,10-Oct-08|08:45 - 10:15|2-6:ROOM-3 ENT3|CT046-3-3-NWT-T-1|NURUL HANIZA BINTI MOHTAR
FRI,10-Oct-08|11:00 - 12:00|2-6:ROOM-3 ENT3|CT031-3-3-FWLAN-L-1|DAVID TAN GEI KAR


i was wondering if any one can provide me with some tips how to display my next class location and subject code in conky based on the time 

regards
nash

---

### Post by unutbu on 2008-10-03
[PHP]#!/usr/bin/env python
from __future__ import with_statement

__notes__="""
http://ubuntuforums.org/showthread.php?t=936567

This script takes data like this:

TUE,07-Oct-08|08:45 - 10:15|2-6:ROOM-3 ENT3|CT050-3-3-PRMGT-T-1|S. MOHANARAJAH
WED,08-Oct-08|08:45 - 10:15|G-3:ROOM-2 ENT3|CT031-3-3-FWLAN-T-1|DAVID TAN GEI KAR
WED,08-Oct-08|11:00 - 12:00|G-3:ROOM-1 ENT3|CT013-3-3-CSS-L-1|ANUSHIA INTHIRAN
THU,09-Oct-08|08:45 - 10:15|G-3:ROOM-2 ENT3|CT031-3-3-FWLAN-T-1|DAVID TAN GEI KAR

and selects those lines whose interval contains the current date and time.
It prints those lines in this format:

[2008-10-03 06:45--08:15] G-3:ROOM-2 ENT3|CT031-3-3-FWLAN-T-1|DAVID TAN GEI KAR
[2008-10-03 08:00--09:00] G-3:ROOM-1 ENT3|CT013-3-3-CSS-L-1|ANUSHIA INTHIRAN

The variable 'delta' can be used to specify an amount of time to lookahead.
"""
__date__="2008-10-03"

import datetime

filename='/path/to/datafile'
delta=datetime.timedelta(hours=1)

today=datetime.datetime.today()
with open(filename,'r') as sock:
    for line in sock:
        parts=line.split('|')
        times=parts[1].split(' - ')
        begin_str="%s %s"%(parts[0],times[0])
        end_str="%s %s"%(parts[0],times[1])
        # 
        # See http://docs.python.org/library/datetime.html#strftime-behavior
        # to see how to build datetime format strings
        #
        begin_time=datetime.datetime.strptime(begin_str,'%a,%d-%b-%y %H:%M')
        end_time=datetime.datetime.strptime(end_str,'%a,%d-%b-%y %H:%M')
        if begin_time-delta<today and today<end_time:
            print ('['+
                   begin_time.strftime('%Y-%m-%d %H:%M')+
                   '--'+
                   end_time.strftime('%H:%M')+
                   '] '+
                   '|'.join(parts[2:])),
[/PHP]

---

### Post by nashrafeeg on 2008-10-03
thanks for the quick reply. with your code i have manage to get conky to display my class and location. 

just one more quick thing is their a possible way to dump this into the gnome alarm clock applet / widget so it goes off say 30 min before time :confused:

---

### Post by unutbu on 2008-10-03
I don't know how the gnome alarm clock applet works. There might be a way, but I don't know it.

Would you be interested in a way to make visual reminders using crontab and imagemagick?

---

### Post by nashrafeeg on 2008-10-03
that would be great too :) i would love to know how

---

### Post by unutbu on 2008-10-03
[list=1]
[*]Install imagemagick:```

sudo apt-get install imagemagick
```
[*]Optional: Install gqview. The instructions below assume you have gqview installed, 
but by editing the reminder.sh script below (in one spot) you can use whatever image viewer you prefer.```

sudo apt-get install gqview
```
[*]Save this in a file called reminder.sh:
[PHP]#!/bin/sh
touch ~/.reminder.sh-executed
viewer='gqview'
cd /tmp 
file=$(tempfile --suffix='.png')

bgColor='black'
fgColor='green'
fgOutlineColor='yellow'

convert xc:"$bgColor" -resize 840x525! -gravity "Center" -font Bookman-DemiItalic -pointsize "${2:- 150}" -fill "$fgColor" -stroke "$fgOutlineColor" -draw "rotate -25 text 0,0 '$1'"  $file && $viewer $file
rm $file[/PHP]
If you wish to use a different image viewer, simply edit the script, changing gqview to the appropriate command.
[*]Make the script executable:```

chmod +x reminder.sh
```
[*]You can run the script from the command line like this:```

reminder.sh 'Go to class!' 125
```
The number at the end controls the size of the font. If you put no number the default size is 150.

You should see an image like this:
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87175&stc=1&thumb=1&d=1223055870[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=87175&d=1223055870")

You can setup gqview so that by default it creates an image window that fills the whole screen (so that it is hard to ignore :))

Press 'q' to quit gqview.

[*]Now we hook it up to cron so we get a reminder:
```
crontab -e
```
Edit the file by adding a line like this:
```

15 13 * * 2  reminder.sh 'Go to class' 125

```
Save and exit. The machine will run the reminder.sh script at 13:15 on every Tuesday.

The format of the crontab line is this:

The 1st field represents minutes
The 2nd field represents hours, etc.
```

field          allowed values
-----          --------------
minute         0-59
hour           0-23
day of month   1-31
month          1-12 (or names, see below)
day of week    0-7 (0 or 7 is Sun, or use names)

```
To find out more about cron, type
```

man 5 crontab
```
or post if you have a question.
[/list]

---

### Post by nashrafeeg on 2008-10-03
is their way to auto add the reminders to cron tab once i get the time table from the web i am using this script to scrub my time table information  

[PHP]
#!/usr/bin/env python
from mechanize import Browser
from BeautifulSoup import BeautifulSoup
import re

timetable = open("timetable.txt","w")
mech = Browser()

url ="http://webspace.apiit.edu.my/schedule/intakeview_intake.jsp?Intake1=UC3F0$
page = mech.open(url)

html = page.read()
soup = BeautifulSoup(html)

#print soup.prettify()

table = soup.find("table", border=1)

for row in table.findAll('tr')[1:]:
    col = row.findAll('td')
    date = col[0].font.string
    time = col[1].font.string
    location = col[2].font.string
    subject = col[3].font.string
    lecturer = col[4].font.string
    record = (date, time, location, subject, lecturer)
    print  "|".join(record)
    print >>timetable, "|".join(record)
[/PHP]

cheers 
Nash 
ps: thanks for all the great help

---

### Post by unutbu on 2008-10-03
I don't have access to the url, so I haven't actually run this code to check it.

However, the only new idea here is writing a cronlines file. The cronlines file is just a text file which contains crontab lines.

You can update your personal crontab using the command```

crontab cronlines
```

So the idea is simply to mechanize the process of writing the cronlines file from within the script and then calling "crontab cronlines" at the end.

[PHP]#!/usr/bin/env python
from __future__ import with_statement
from mechanize import Browser
from BeautifulSoup import BeautifulSoup
import re
import datetime
import os

timetable = open("timetable.txt","w")
mech = Browser()

url ="http://webspace.apiit.edu.my/schedule/intakeview_intake.jsp?Intake1=UC3F0$"
page = mech.open(url)

html = page.read()
soup = BeautifulSoup(html)

#print soup.prettify()

table = soup.find("table", border=1)

today=datetime.datetime.today()
delta=datetime.timedelta(minutes=30)
cronfile='cronlines'
with open(cronfile,'w') as cron_sock:
    for row in table.findAll('tr')[1:]:
        col = row.findAll('td')
        date = col[0].font.string
        time = col[1].font.string
        location = col[2].font.string
        subject = col[3].font.string
        lecturer = col[4].font.string
        record = (date, time, location, subject, lecturer)
        line = "|".join(record)
        line=line.strip()
        print line

        #
        # Build datetime objects: begin_time, end_time, alarm_time
        #
        parts=line.split('|')
        times=parts[1].split(' - ')
        begin_str="%s %s"%(parts[0],times[0])
        end_str="%s %s"%(parts[0],times[1])
        begin_time=datetime.datetime.strptime(begin_str,'%a,%d-%b-%y %H:%M')
        end_time=datetime.datetime.strptime(end_str,'%a,%d-%b-%y %H:%M')
        alarm_time=begin_time-delta

        #
        # Filter lines; only print those near the current date and time
        #
        if alarm_time<today and today<end_time:
            print >>timetable, ('['+
                                begin_time.strftime('%Y-%m-%d %H:%M')+
                                '--'+
                                end_time.strftime('%H:%M')+
                                '] '+
                                '|'.join(parts[2:])),

        #
        # Write the cronlines file
        #
        cron_sock.write("%s %s %s %s %s %s\n"%(
                alarm_time.minute,
                alarm_time.hour,
                alarm_time.day,
                alarm_time.month,
                alarm_time.isoweekday(),
                "reminder.sh '%s' 25"%'|'.join(parts[2:])))


#
# Update your crontab
#
os.system("crontab cronlines")


[/PHP]

---

### Post by nashrafeeg on 2008-10-04
thanks it works :) :guitar:

---

