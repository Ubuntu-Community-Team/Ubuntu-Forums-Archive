---
title: "Python script is Emailing file before contents are written on it"
date: 2010-12-01
forum: Programming Talk
---

### Post by onitram on 2010-12-01
Hi. I can't seem to find any help on this. Admittedly, I am a major newbie with this stuff.
Any help would be greatly appreciated.

Basically, I'm copying a directory tree, and logging the actions of the script into a separate text file. I want to then email that text file with the contents in it. (i just want to email the contents of a file that is actually being written to during the script).

What seems to be happening is that the script isn't waiting for all the actions to happen sequentially. So it's emailing a blank file. But the file that is actually created in the script is not blank at all when I open it on the desktop - it contains everything that it should.

First I was utilizing subprocess Popen to just: cat log.txt|mail , but that subprocess wasn't waiting either. So I thought it was just the nature of subprocess to be running separately and not wait for previous commands.

I have tried to add a "time.sleep(120) or whatever to it and the delay doesn't help with this problem.

When I cut out all the copying directory stuff, and just email contents of a file on my desktop (ie using just the second half of the script) it emails me the file and all the contents to it. So i know the email part is correct, and i know the copying part is correct. So it means that it's a timing thing i think?

I know i could just do this simply in bash, but i'm trying to do it python :)

here's basically what i'm doing:



import os
import sys
import shutil
import time
import datetime
import tarfile
import subprocess
import smtplib
from email.MIMEMultipart import MIMEMultipart
from email.MIMEBase import MIMEBase
from email.MIMEText import MIMEText
from email import Encoders


today = datetime.date.today()
todaystr = today.isoformat()

#here's the log file being created from scratch

log = open('/users/Me/Desktop/logz' +todaystr,'w')

#here's me writing to that log file, which isn't showing up in the email

print >>log, time.ctime() 
print >>log, "Now executing backing up of the following:"

#make the destination folder of copied contents

os.mkdir("/Users/Me/Desktop/folder1" +todaystr)

dir_src = "/Users/Me/Desktop/quarantine/"
dir_dst = "/Users/Me/Desktop/folder1" +todaystr

#copying the directory. Ignore the missing indent under the "for"

for file in os.listdir(dir_src):
    print >>log, file #testing
    src_file = os.path.join(dir_src, file)
    dst_file = os.path.join(dir_dst, file)
    shutil.copytree(src_file,dst_file, ignore=shutil.ignore_patterns('*.flv','junkfiles'))

#still writing to the log here

print >>log, "location of local back up:"
print >>log, dst_file

print >>log, "Local Backup complete"
print >>log, time.ctime()

print >>log, "blahblah"


#using gmail to email rather than local, which i like

gmail_user = "me@gmail.com"
gmail_pwd = "PaSS"

def mail(to, subject, text, attach):
   msg = MIMEMultipart()

   msg['From'] = gmail_user
   msg['To'] = to
   msg['Subject'] = subject

   msg.attach(MIMEText(text))

   part = MIMEBase('application', 'octet-stream')
   part.set_payload(open(attach, 'rb').read())
   Encoders.encode_base64(part)
   part.add_header('Content-Disposition',
           'attachment; filename="%s"' % os.path.basename(attach))
   msg.attach(part)

   mailServer = smtplib.SMTP("smtp.gmail.com", 587)
   mailServer.ehlo()
   mailServer.starttls()
   mailServer.ehlo()
   mailServer.login(gmail_user, gmail_pwd)
   mailServer.sendmail(gmail_user, to, msg.as_string())
   # Should be mailServer.quit(), but that crashes...
   mailServer.close()


# sending the email with the attachment. It works, but the attachment has nothing printed to it. Yet the actual file on the desktop contains all the printed text on it.

mail("you@crapmail.com",
   "Monthly  Backup",
   "Please review the file  ",
   "/Users/Me/Desktop/logz" +todaystr)



that's it. any help would be great thank you.

---

### Post by apmcd47 on 2010-12-01
You don't appear to have a close statement for the log file. I would guess that python has buffered the output and not actually put it in the file when you email it. Try putting a close statement in and try again.

Andrew

---

### Post by DaithiF on 2010-12-01
close the file handle once you're done writing it and before emailing.  Whats happening is that the output is being buffered and until you call close (or flush() would do it too), nothing gets written to disk.

---

### Post by onitram on 2010-12-01
Thanks guys, that was it!

---

