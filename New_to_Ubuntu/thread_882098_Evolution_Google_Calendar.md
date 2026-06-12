---
title: "Evolution: Google Calendar"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by raccoonone on 2008-08-06
I'm trying to setup Evolution to sync with my Google Calendar. I added a new calendar in Evolution using the Google option. However, although I can see events on my calendar, if I try to add a new event in Evolution it appears and then disappears after I restart (and never appears in the web interface). Also Evolution started crashing somewhat randomly after I added the Google Calendar, so I had to remove it. Is there a guide that explains how to set this up? I looked at the GNOME site, but couldn't find anything.

---

### Post by lordadi on 2008-08-06
Hi,

I too had the problem (not the crashes though) but this is the way I did it:[GCaldaemon]("http://gcaldaemon.sourceforge.net/usage16.html"). I used the offline sync method and set the included script to run on login. That way I always get a synced calendar with google.:)


Cheers,



Lordadi.

---

### Post by raccoonone on 2008-08-06
Thanks. I found that too, but figured I try doing it just with Evolution since setting up Gcaldaemon looked a little complex. I think I'll just go with Gcaldaemon though, unless someone knows how to fix Evolution

---

### Post by lordadi on 2008-08-06
Hi,

Did you try the enable SSL box?


Cheers,

Lordadi.

---

### Post by lordadi on 2008-08-06
Hi,

I remember also trying this once, it may help. When you get your ical address from google calendar, you put it in calendars on the web and change the http:// to webcal://

Hope it helps,


Lordadi.

---

### Post by raccoonone on 2008-08-07
> **lordadi said:**
> Hi,

I remember also trying this once, it may help. When you get your ical address from google calendar, you put it in calendars on the web and change the http:// to webcal://

Hope it helps,


Lordadi.

That works, but the problem is that the calendar is read-only, and I'd like to have changes that I make locally sync'ed back to Google

---

### Post by lordadi on 2008-08-07
In that case, I can only recommend GCalDaemon.




Cheers,


Lordadi.

---

### Post by bsell on 2008-08-11
Uncheck the Alarm notification for Birthdays and Anniversaries in the Calendars and Tasks dialog in Preferences, then import your Google calendar. See [this Launchpad bug post]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/189810/comments/9") for more information.

---

### Post by raccoonone on 2008-08-11
That fixed the crash problem, but the calendars still aren't being sync'ed. if I add an event to Evo, it gets deleted after i restart

---

### Post by Ventiakan on 2008-09-07
Newbie question here.

I am trying to install gcaldaemon but the download file won't unzip. I get the message

checkdir error:  cannot create /usr/sbin/GCALDaemon
                 unable to process GCALDaemon/.

Something real obvious I haven't done, I guess.

---

### Post by bsell on 2008-09-07
> **raccoonone said:**
> That fixed the crash problem, but the calendars still aren't being sync'ed. if I add an event to Evo, it gets deleted after i restart

Sorry I didn't get back to you earlier. School has started and I'm usually pretty busy.

You have to allow your calendars in Evolution to be published. This is how it syncs with your Google calendars. Select this option from the menu bar. 

The only problem I have with syncing with my Google calendars is daylight savings time. Events times I add to any calendar synced with Google get changed when the calendars are synced.

---

### Post by fcastillo on 2008-12-04
I have exactly the same problem. I'm from Ecuador so my time zone it's -5. Everytime I add an event, evolution syncs it with Google 6 hours before. So evolution shows the time correctly but Google shows them 6 hours before, but the other way around it's ok (creating it in google and seeing them on evolution).
I've found some webpage with bugs about this, but I'm not sure if it's the same one, since a lot of people talk about daylight savings, and in Ecuador we don't have any at all.
I really need this functionality, if somebody can explain how to fix it?

---

### Post by t0n1 on 2009-01-29
Any solution found yet?

---

### Post by Brigrat on 2009-02-15
This is a really noob question, but desperate times call for desperate measures.  I really would like to get evo and google working in 2 directional sync.  the "embedded" links don't seem to work so I am trying to get gcaldaemon to work.  Down loaded to my "desktop/downloads" location and attempted to follow the instructions but get zip -pardon the pun...  here is the print from terminal in the instructions.  BTW how do you login to  ubuntu 8.10 as root???  I know that sudo achieves the same result.

1)GCALDaemon supporting a Java Virtual Machine (VM) such as found in Sun's JDK or JRE, version 1.5 or higher. This can be obtained for free from java.sun.com. You can verify your existing Java version with the following console command:

java -version

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing) 

2) Log on as 'root'.

3) Download the latest Linux-compatible ZIP file from SourceForge.net into your '/downloads' directory (or into your accustomed download directory). 

4) Unzip this archive under the '/usr/local/sbin' directory. If the '/usr/local/sbin' directory does not exists (for example you get a 'No such file or directory' message), there are two alternative ways; you can create this via 'mkdir -p /usr/local/sbin' command, or unzip GCALDaemon into the '/opt' folder. The '/usr/local/sbin' directory is recommended but not obligatory, so you can deploy GCALDaemon into any optional folder. If you would like to allow every users to use GCALDaemon, you may type 'chmod 777 /usr/local/sbin/GCALDaemon'. First change the group ownership and set the rights (replace 'groupname' to your user group): 

cd /usr/local/sbin
unzip /downloads/gcaldaemon-linux-1.x.zip
[unzip /downloads/gcaldeamon-linux-1.0-beta16.zip] added for notes only 

dan@dan-ubuntu:~$ cd/usr/local/sbin

bash: cd/usr/local/sbin: No such file or directory

dan@dan-ubuntu:~$ cd /usr/local/sbin

dan@dan-ubuntu:/usr/local/sbin$ sudo unzip /downloads/gcaldaemon-linux-1.x.zip

sudo: unable to resolve host dan-ubuntu

[sudo] password for dan: 

unzip:  cannot find or open /downloads/gcaldaemon-linux-1.x.zip, /downloads/gcaldaemon-linux-1.x.zip.zip or /downloads/gcaldaemon-linux-1.x.zip.ZIP.

dan@dan-ubuntu:/usr/local/sbin$ sudo unzip /downloads/gcaldeamon-linux-1.0-beta16.zip

sudo: unable to resolve host dan-ubuntu

unzip:  cannot find or open /downloads/gcaldeamon-linux-1.0-beta16.zip, /downloads/gcaldeamon-linux-1.0-beta16.zip.zip or /downloads/gcaldeamon-linux-1.0-beta16.zip.ZIP.

dan@dan-ubuntu:/usr/local/sbin$ 




chgrp -R groupname /usr/local/sbin/GCALDaemon
chmod -R g+w /usr/local/sbin/GCALDaemon
chmod 755 /usr/local/sbin/GCALDaemon/bin/*.sh

5) Setup finished - sign off, sign on conventionally, then test your configuration.

cd /usr/local/sbin/GCALDaemon/bin
./password-encoder.sh

6) If you see something similar to the line above, your installation has succeeded.

Your Google password: _
7) Press ENTER to quit from the encoder. Then you should read the setup guides about the synchronization. If you use Evolution, Rainlendar, KOrganizer or an iCal-compatible PDA/Mobile synchronizer (e.g. BitPim) read the guide about the file-based synchronization. If you use Kontact, Mozilla Calendar, Sunbird or Lightning read the guide about the HTTP-based synchronization. Some calendar applications ignore time-zone properties. When your local time-zone settings are incorrect your events may be off by one or more hours. To resolve this effect, please verify that the time-zones in your Google Calendar settings and in the OS / local calendar application are the same. If you have trouble with running, please read the next ('Install GCALDaemon into an arbitrary directory') chapter hereinafter, and verify the file paths in the config files.

---

### Post by Brigrat on 2009-02-17
Well I finally figured out the puzzle in the gcaldaemon problem and got all the information in the right spots, HOWEVER COMMA, the caledar still will not sync.  I saw something about publishing the calendar to get it to sync.  I'll keep everyone posted.
I did try the embedded google calendar setup, that method does not seem to bring in all of the dates and appointments. Soooo that method is on the back burner as well.  
If anyone has ideas to put in on this I will keep pounding on this issue as I ma anxious to divorce the last hold up of leaving MS wndws behind.  MY STUBBORN IRISH attitude is up.:-|

---

### Post by guille79es on 2009-11-20
You can do it easily with Caldav.
Follow this guide:
[http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird](http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird)

it works on both directions :D

---

