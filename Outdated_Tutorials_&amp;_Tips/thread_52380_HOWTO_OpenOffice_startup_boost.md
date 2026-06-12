---
title: "HOWTO: OpenOffice startup boost"
date: 2005-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by drigloi on 2005-07-27
OpenOffice is usually blamed for slow startup times. The 2.0 version of this great software shows some improvements in this field too but here's is a HOWTO on speeding up the OO.o 1.1.x line. This is based on a linuxjournal.com article.

1.
```
sudo gedit /opt/oostay
``` 

2. paste this to oostay:
```
#!/bin/bash
# Restart ooffice -quickstart every time it exits
instances=`ps ax | grep -e -quickstart | grep -v grep | wc -l`

if [ $instances == 0 ]; then
    while true; do ooffice -quickstart ; done
else
    exit 1
fi
``` 

3. make it Xecutable by
```
sudo chmod a+x /opt/oostay
``` 

4. launch gnome-session-properties and the script to the automatically launched programs. So: "/opt/oostay" priority: 50

---

### Post by Mr Frosti on 2005-07-27
Wow, I barely see the splash logo before the program launches. Phenominal speed increase, great HOWTO!

---

### Post by varunus on 2005-07-27
Another way to increase OO.org speed:

Open up OO writer, go to tools->options->memory
Increase the graphics cache ram, I upped mine to 64 for "Use for OO.org" and 5 for "memory per object"

Loading times will increase dramatically.  (20 seconds to 7 seconds on one computer I've used)

---

### Post by drigloi on 2005-07-27
[QUOTE=varunus]Another way to increase OO.org speed:

Open up OO writer, go to tools->options->memory
Increase the graphics cache ram, I upped mine to 64 for "Use for OO.org" and 5 for "memory per object"

Loading times will increase dramatically.  (20 seconds to 7 seconds on one computer I've used)[/QUOTE]

You must have read the same article too  [-X   ;-)

---

### Post by Mr Frosti on 2005-09-08
I have used 'oostay' for  a while, and I have noticed that the System Monitor reports my CPU usage at 100%. I have found the culprit to be this scipt. Once I end that process, my CPU immedietly jumps back down to 0-5% usage. 

Does any have any ideas why this is happening?

---

### Post by Ali_Taimur on 2005-09-08
[QUOTE=drigloi]OpenOffice is usually blamed for slow startup times. The 2.0 version of this great software shows some improvements in this field too but here's is a HOWTO on speeding up the OO.o 1.1.x line. This is based on a linuxjournal.com article.

1.
```
sudo gedit /opt/oostay
``` 

2. paste this to oostay:
```
#!/bin/bash
# Restart ooffice -quickstart every time it exits
instances=`ps ax | grep -e -quickstart | grep -v grep | wc -l`

if [ $instances == 0 ]; then
    while true; do ooffice -quickstart ; done
else
    exit 1
fi
``` 

can you tell me how to do this in kubuntu
thanks

3. make it Xecutable by
```
sudo chmod a+x /opt/oostay
``` 

4. launch gnome-session-properties and the script to the automatically launched programs. So: "/opt/oostay" priority: 50[/QUOTE]
can you tell me how to do this is kubuntu

---

### Post by myha on 2005-09-09
First edit file with kate not gedit:
```
sudo kate /opt/oostay
``` 
Paste the code to new file and save it.
Add execute bit.

Then go to ~/.kde/Autostart
```
cd ~/.kde/Autostart
``` 
make new file named oostay
```
kate oostay
``` 
And paste this inside:
```
#!/bin/bash
/opt/oostay
``` 
This should be it!

Edit: Forgot to say to add x bit:
```
sudo chmod +x ~/.kde/Autostart/oostay
```

---

### Post by myha on 2005-09-12
[QUOTE=Mr Frosti]I have used 'oostay' for  a while, and I have noticed that the System Monitor reports my CPU usage at 100%. I have found the culprit to be this scipt. Once I end that process, my CPU immedietly jumps back down to 0-5% usage. 

Does any have any ideas why this is happening?[/QUOTE]
I seem to have the same problem.... 100% CPU usage all the time, even when no oo program running...   :???:

---

### Post by woifi on 2005-09-12
have you tried ooqstart-gnome or oooqs-kde?> Description: OpenOffice.org QuickStarter applet for GNOME 2
 This applet preloads the OpenOffice.org program to make it launch faster
 when needed.


---

### Post by EasyUwe on 2006-05-16
[QUOTE=drigloi]OpenOffice is usually blamed for slow startup times. The 2.0 version of this great software shows some improvements in this field too but here's is a HOWTO on speeding up the OO.o 1.1.x line. This is based on a linuxjournal.com article.
[/QUOTE]

thx for the instruction! does this work with folloing versions as well?

Ubuntu 5.10
and OpenOffice2
???

Thx
Uwe A.

---

### Post by skippy81 on 2006-05-20
Sorry for the necromancery, but here is an effective way of increasing startup time:

In options go to "Java" and untick the box.  Doing this appeared to make a massive difference.  Since i'm running 64bit dapper I dont actually have JVM installed anyway, I can only assume that office was wasting time looking for it.  

I believe I found this tip originally on wikipedia, I didn't expect it to work as well as it did :cool:

---

