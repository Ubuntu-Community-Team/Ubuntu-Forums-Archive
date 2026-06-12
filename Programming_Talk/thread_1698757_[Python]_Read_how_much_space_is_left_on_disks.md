---
title: "[Python] Read how much space is left on disks"
date: 2011-03-02
forum: Programming Talk
---

### Post by Tompalaz on 2011-03-02
Hi

I'm making a python script that will check how much space there is left on the specified harddrives and if it's equals or is below 2GB left it will send a heads up email.

However, I'm not sure how I should do this:

Say there is three disks or partitions I want to monitor

DISK0 = "/"
DISK1 = "/dev/sdb2"
DISK2 = "/dev/sdb5"

Should I put these into a array or am I totaly off track?

ARRAY = (DISK0, DISK1, DISK2)

I'd like to monitor these disks and then if one or more of the disks have less than 2GB left it should print out the disk(s) to a variable.
Then it will send the email.

The mailing part is all done, so far it prints 
Alarm: #Less than 2 GB Free Space on ARRAY# on " + SRV + "\nTime of Event: "+ HOUR + ":" + MINUTE
(the array is just a placeholder for now)

Any ideas?

You should know I'm new to Python :)

Thanks!

---

### Post by Shpongle on 2011-03-02
yea a list will work fine for it

[http://docs.python.org/tutorial/datastructures.html](http://docs.python.org/tutorial/datastructures.html) 


you can use the os module to get the size.

see here

[http://ubuntuforums.org/showthread.php?t=961505](http://ubuntuforums.org/showthread.php?t=961505)

Im fairly new to it myself , well I have a few months but im self taught also.

---

### Post by Tompalaz on 2011-03-03
Thanks for your answer.

I'm already using os.statvfs. It seems it cant handle more than one argument. That is, I cant do os.statvfs("/dev/sda1","/dev/sda2") or use a variable with more than one value.

Currently I have this, but it only takes one disk.
> 
[...]

MON0 = '/dev/sda3'
MON1 = '/dev/sda4'

MON_ARRAY = (MON0, MON1)

LIMIT = 8376

MONITOR = os.statvfs(str(MON0))

for disk in MON_ARRAY:
	if disk <= LIMIT:
		print disk, "not OK", HOUR,":",MINUTE
	else:
		print disk, "is OK", HOUR,":",MINUTE

output=(MONITOR.f_bavail * MONITOR.f_frsize) / 1048576 
print "Disk ", disk, output, "MB"


[...]


Is there a way to insert two values in os.statvfs() or is there another function I can use?

---

### Post by Zugzwang on 2011-03-03
> **Tompalaz said:**
> Is there a way to insert two values in os.statvfs() or is there another function I can use?

There's a logical error in your line of thought: You don't need to get the statistics for more than one disc at once. Just move the call to os.statvfs() into the "for disk in MON_ARRAY:" loop and call os.statvfs() on "str(disk)".

---

### Post by Tompalaz on 2011-03-03
Thank you, I'm not sure how you to do it though.

Do you mean
> for disk in MON_ARRAY:
	if disk >= LIMIT:
		os.statvfs(str(MONITOR)) 
		output=(MONITOR.f_bavail * MONITOR.f_frsize) / 1048576 
		print H,":",M,":",S, " Partition", disk, "- not OK on", SRV,",", output, "MB left on disk"

Edit: I think I got it!
> for disk in MON_ARRAY:
	if disk >= LIMIT:
		MONITOR = os.statvfs(str(disk)) 
		output=(MONITOR.f_bavail * MONITOR.f_frsize) / 1048576 
		print H,":",M,":",S, " Partition", disk, "- not OK on", SRV,",", output, "MB left on disk"

	else:
		print disk, "is OK", HOUR,":",MINUTE

---

### Post by Tompalaz on 2011-03-04
Hmm, my for loop will always print out that the disk is OK even though it's below the limit.

This is the whole script:
> #!/usr/bin/env python
# -*- encoding: utf-8 -*-

import smtplib, os, socket, statvfs
from time import localtime, strftime


# 				CONFIGURE HERE				
SERVER = "smtp.bahnhof.se"						
PORT = '' # If left blank port 25 is assumed.	
 				Mail						
SEND_FROM = 'monitor@company.com'					
SEND_TO = ['user@company.com']				
#Monitor	
MON0='/'								
MON1='/home'								
MON2=/tmp'
MON_ARRAY = (MON0, MON1, MON2) 					
#				Limit in MiB
LIMIT=2048;									
# 				END OF CONFIG	

#Define current Time as Fri, 04 Mar 2011 08:47:10
TIME = strftime("%a, %d %b %Y %H:%M:%S", localtime())

#Get servers hostname to variable
SRV = str(socket.gethostname()) 

for disk in MON_ARRAY:
	if (disk < LIMIT):
		STATUS = "- is not OK on "
		MONITOR = os.statvfs(str(disk)) 
		
		SPACE_LEFT=(MONITOR.f_bavail * MONITOR.f_frsize) / 1048576 #MiB 
		print  TIME,"Partition",disk,STATUS,SRV,"\n",SPACE_LEFT,"MB left on disk"
				
		MSG =  TIME,"Partition",disk,STATUS,SRV,"\n",SPACE_LEFT,"MB left on disk"
		smtpserver = smtplib.SMTP(SERVER, PORT)
		smtpserver.ehlo()
		# Uncomment smtpserver.starttls if server using TLS
		#smtpserver.starttls()
		smtpserver.ehlo
		# Uncomment smtpserver.login() if login is required
		#smtpserver.login('username', 'password')
		
		HEADER = 'To:' + str(SEND_TO) + '\n' + 'From: ' + str(SEND_FROM) + '\n' + 'Subject:Auto Alert - Low disk space on ' + SRV + '\n' 
		print HEADER
		MAIL = HEADER + str(MSG)
		
		smtpserver.sendmail(SEND_FROM, SEND_TO, MAIL)
		print 'Done!'
		smtpserver.close()

	elif (disk > LIMIT):
		STATUS = "- is OK on "
		print TIME, disk, STATUS, SRV
		
	else:
		print """
		A serius problem detected with the script.
		Please check what mount points you monitor and check that they're in the MON_ARRAY aswell.
		"""


---

### Post by Tompalaz on 2011-03-04
I fixed it.

Error in the for loop
> for disk in MON_ARRAY:
	MONITOR = os.statvfs(str(disk)) 
	SPACE_LEFT=(MONITOR.f_bavail * MONITOR.f_frsize) / 1048576 #MiB 
	if (SPACE_LEFT < LIMIT)

---

### Post by Tony Flury on 2011-03-04
Can i suggest you post your python code in CODE tags (click the #) in the toolbar - as you know indentation is important in python, and it can be difficult to decipher the actual meaning of a swathe of code when the indentation has been stripped out.

In regards to your specific issue : you testing do the disk < LIMIT check before you call MONITOR = os.statvfs(str(disk)) 
You are also currently comparing the name of the disk against your size limit - which has to be wrong

I think your loop should be : 

```

for disk in MON_ARRAY:
    # Moved this here
    MONITOR = os.statvfs(str(disk))
    SPACE_LEFT=(MONITOR.f_bavail * MONITOR.f_frsize) / 1048576 #MiB

    # Changed this - used to be disk < LIMIT
    if (SPACE_LEFT < LIMIT):
        STATUS = "- is not OK on "
        print TIME,"Partition",disk,STATUS,SRV,"\n",SPACE_LEFT," MB left on disk"

        MSG = TIME,"Partition",disk,STATUS,SRV,"\n",SPACE_LEFT," MB left on disk"
        smtpserver = smtplib.SMTP(SERVER, PORT)
        smtpserver.ehlo()
        # Uncomment smtpserver.starttls if server using TLS
        #smtpserver.starttls()
        smtpserver.ehlo
        # Uncomment smtpserver.login() if login is required
        #smtpserver.login('username', 'password')

        HEADER = 'To:' + str(SEND_TO) + '\n' + 'From: ' + str(SEND_FROM) + '\n' + 'Subject:Auto Alert - Low disk space on ' + SRV + '\n'
        print HEADER
        MAIL = HEADER + str(MSG)

        smtpserver.sendmail(SEND_FROM, SEND_TO, MAIL)
        print 'Done!'
        smtpserver.close()

    elif (SPACE_LEFT > LIMIT):
        STATUS = "- is OK on "
        print TIME, disk, STATUS, SRV

```

I have not tested this.

---

### Post by Tompalaz on 2011-03-04
Hey, thanks.

I changed all those things as I posted the new for loop, and it works like a charm!

Sorry for using qoute, I know I can use the code tag, though, I thought it only worked for shorter lines, such as sudo apt-get install geany.

Anyways, thank you all for your help!

---

### Post by Tompalaz on 2011-03-04
Hey.
One last question :)

Is it possible to print variables from a tripple qouted variable?
Like:
```
MSG =  """
[TIME] Mountpoint MOUNT STATUS HOST \n\n SPACE_LEFT MB left on disk
"""
print MSG

```

---

### Post by Tony Flury on 2011-03-04
> **Tompalaz said:**
> Hey.
One last question :)

Is it possible to print variables from a tripple qouted variable?
Like:
```
MSG =  """
[TIME] Mountpoint MOUNT STATUS HOST \n\n SPACE_LEFT MB left on disk
"""
print MSG

```

Try using the format method (rather than +)

[http://docs.python.org/release/2.6.6/tutorial/inputoutput.html#fancier-output-formatting](http://docs.python.org/release/2.6.6/tutorial/inputoutput.html#fancier-output-formatting)

---

### Post by Tompalaz on 2011-03-04
Thanks!
```
        html = """\
        <html>
          <head></head>
          <body>
                <p><b>WARNING!</b>
                   <br>Low diskspace left on mount {mount} on {host}
                   <br>Space left: {space_left} MB.
                   <br>Time of Event: {time}
                </p>
          </body>
        </html>        """.format(mount=MOUNT, host=HOST, space_left=SPACE_LEFT, time=TIME)
```
This worked perfect!

I must say, when I started with this I didn't know any python. 
Thanks to you guys I've learnt alot!

---

