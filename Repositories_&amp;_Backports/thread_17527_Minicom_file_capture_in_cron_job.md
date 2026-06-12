---
title: "Minicom file capture in cron job"
date: 2005-03-01
forum: Repositories &amp; Backports
---

### Post by firstbishop on 2005-03-01
Our switchboard outputs phone call data to the serial port of a dedicated Ubuntu box. I am running minicom on that machine and it picks up the incoming data very nicely and captures to a file, which is periodically parsed by a PHP script and the resulting information written to a MySQL database.

My problem is that using the "minicom -C capturefilename" option means that the file is only updated when I exit from minicom. I haven't been able to find a way to update on an ongoing basis as call data is received from the switchboard.

I have tried running a bash script from a cron job which shuts down minicom and restarts it at 2 in the morning. Although the script runs fine when I test it, for some reason when cron executes the script, I get a whole lot of strange stuff appearing in both the capture file and the email detailing what the cron job has done (For example, the minicom window itself is captured, along with a host of what look like control characters or something). 

Is there any reason why a script would behave so differently when executed by cron, as opposed to execution from the command line?

Another alternative I have tried is to simply type cat -v /dev/ttyS1 > phonedata.
That would seem to me to be the most elegant solution, but, although the file is opened, no data is written to it by that command.

Am I missing something obvious here?

I'd really appreciate any pointers. Thanks

Mike

---

### Post by trampolando on 2006-12-12
very interesting...
I have the same problem... any one can help us?

Do you know if there's a way to read and write to serial port directly with php?
thanks

Riccardo

---

### Post by harrysales on 2008-02-22
Ive got this dilema and discovered that if minicom is running the contents of the file are human readable. I am now looking at stty which I think sets up the com port. I think minicom sets up the port when it runs.

---

### Post by harrysales on 2008-02-22
Right sussed it.
Logon to the ubuntu box with two shells
In shell1 enter the command 
stty -F /dev/ttyS1 -a 
and record it maybe by 
stty -F /dev/ttyS1 -a > /home/$user/doc
Then in shell2 start mincom. 
Then go back to shell1 do the same 
stty -F /dev/ttyS1 -a 
thing and compare the results.
I found that this page was very helpfull
[http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds5/stty.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds5/stty.htm)
You can change the settings one by one.
There is a usefull tip that if you enter the command 
stty -F /dev/ttyS1 sane 
the settings are reset to a default configuration and I intend to do a script that will compare the current config to the minicom config then if there is a difference use the sane command to get to default config and then bring it back to minicom config.

I hope this makes sense.
I will use cron to run
/bin/cat /dev/ttyS1 > /home/$user/file
periodically and chop up the file with php cgi

I must confess I have done this so I can continue in the morning.

---

