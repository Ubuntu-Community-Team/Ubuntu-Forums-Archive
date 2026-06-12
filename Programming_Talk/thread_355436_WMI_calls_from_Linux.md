---
title: "WMI calls from Linux"
date: 2007-02-07
forum: Programming Talk
---

### Post by etank on 2007-02-07
I was wondering if it is possible to make wmi calls to a Windows machine (2000, XP, 2003, etc.) from a Linux workstation. I would like to be able to do this with Python, Perl or Ruby if possible. I have done some searching and have come up empty so far. 

My goal in this is to be able to pull data (installed software, bios data, shares, etc.) from machines on my network and then store that data in a database. Then I can build a web based frontend to be able to view and search the data. I know that it is possible to do this from a windows machine but I would really like to be able to do it from Linux.

Thank you for any help you can provide.

---

### Post by etank on 2007-02-08
bump

---

### Post by lnostdal on 2007-02-08
[http://en.wikipedia.org/wiki/Windows_Management_Instrumentation](http://en.wikipedia.org/wiki/Windows_Management_Instrumentation)

You might be able to get hold of it using DCOM/SOAP. There seems to be some ports of DCOM to other platforms out there.

Or.. if you already know how to do this on Windows you can write a client running on Windows that does the calls for you then transmits the results to your Linux-computers. 

Or.. you could use SSH to transmit the result (from stdout):

```

lars@ibmr52:~$ ssh nostdal.org ls
%backup%~
BACKUP
dina-backup-description.lisp
dina-backup-description.lisp~
getenv.lisp
getenv.lisp~
mounts
notes.txt
programming
public_html
reply.gif
rmfasl
symbolicweb-conf.lisp

```

..returns the result of running `ls' on `nostdal.org' (you'll find a ssh-server for Windows via cygwin).. .. i suppose there are many ways of doing this

---

### Post by bunabattoir on 2007-02-14
I believe wmi calls would require the Win32 python extensions, and those are Windows only. :(

---

### Post by etank on 2007-02-14
That was what I was afraid of.

---

### Post by diogobira on 2007-03-31
It's possible to do what you want.... You will have to search for a kind of WMI client for windows and for a command line tool to request WMI data using a XML based message.. I recommend you to use the following links to do this:


- WMI Mapper for HP Systems Insight Manager at
[http://h18023.www1.hp.com/support/files/server/us/download/21071.html](http://h18023.www1.hp.com/support/files/server/us/download/21071.html)
(It works for other machines, not only HP!)

and 

- OpenPegasus at
[http://www.openpegasus.org/](http://www.openpegasus.org/)

after installing OpenPegasus on the Linux machine you will have a command line tool called wbemexec. With this tool you will be able to send WMI requests for windows systems running the WMI Mapper...

Good Luck....

---

### Post by kish on 2008-02-29
That sounds promising
Thnx

---

### Post by felimwhiteley on 2008-08-15
sudo aptitude install wmi-client

:-)

Example of usage is;

wmic -U DOMAIN/administrator%password //10.99.92.9 "Select * from Win32_Service"

Lists all services, the first line it spits back is the fields whihc you can use this SQL like langauge on to filter so to see only the names of the services installed we'd do:

wmic -U DOMAIN/administrator%password //10.99.92.9 "Select Name from Win32_Service"

Or Name and State:

wmic -U DOMAIN/administrator%password //10.99.92.9 "Select Name,State from Win32_Service"

Or for jsut one service in this case the UPS service:

wmic -U DOMAIN/administrator%password //10.99.92.9 "Select Name,State from Win32_Service where name='UPS'"


Hope this helps, this is only in Hardy as far as I'm aware.

Félim

---

### Post by felimwhiteley on 2008-08-15
In fact the language that wmic client uses is like SQL because it's called WQL and a referance for it is here:

[http://msdn.microsoft.com/en-us/library/aa394606(VS.85).aspx](http://msdn.microsoft.com/en-us/library/aa394606(VS.85).aspx)

---

