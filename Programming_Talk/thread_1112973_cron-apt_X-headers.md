---
title: "cron-apt X-headers"
date: 2009-04-01
forum: Programming Talk
---

### Post by black-mamba on 2009-04-01
Hi,

We use a ticket system for our IT queries called OTRS.  Emails sent to
that system are placed in ticket queues.  OTRS reads X- headers in emails
as described here:

[http://dev.jasonpruim.com/otrs/doc/X-OTRS-Headers.txt](http://dev.jasonpruim.com/otrs/doc/X-OTRS-Headers.txt)

We would like to be able to configure cron-apt to place certain X- headers
in the notification emails it sends.  It will then send the email to the
OTRS system which will read those X- headers and act accordingly, eg
directly placing the ticket in a particular queue or whatever.

So how do I define arbitrary extra custom headers in /etc/cron-apt/config which get placed in the notification email.

Any help would be great,
Thanks.

---

### Post by PaulFr on 2009-04-03
cron-apt does not appear to support custom headers. The correct way to get this would be to make an enhancement request in Ubuntu Launchpad.

However, you can add this functionality if you are in a hurry and are willing to change a file called /usr/share/cron-apt/functions. If yes, then please try out the following steps:

1. Make a backup copy of the file right away :-)
```
sudo cp /usr/share/cron-apt/functions /usr/share/cron-apt/functions.orig
```2. Edit the file using something like **sudo <favorite_editor> /usr/share/cron-apt/functions**, making sure you replace <favorite_editor> by your favorite editor, like vi or pico or nano.

3. Search for the line containing the string **mail -s**. Change this line to ```
eval mail "$MAILHEADERS" -s "\"$SUBJECT\"" "$MAILTO" < "$MAIL"
```and save the file.

4. Now edit the /etc/cron-apt/config file and add the headers you want. For example, ```
MAILHEADERS="-a \"X-OTRS-State:New York\" -a X-OTRS-Priority:5 -a X-OTRS-Loop:True"
```5. Test by setting MAILON="always" and MAILTO to the email address of a real person who can check if the headers are being inserted properly. Then if it works, you can change it to the real OTRS address.

N.B. For any header that has white space in it, you will need to put a backslash and a double quote around it like I did for X-OTRS-State above. Since the $SUBJECT value also has whitespace, we wrapped it with backslash and double quote above. The "New York" is just to show you a possible value with spaces in it and how you handle it :-)

Good luck!

---

### Post by black-mamba on 2009-04-16
Hi Paul,

This has worked perfectly, thank you very much, it was causing me alot of problems.

This should really be included in the next ver of cron-apt as I'm sure there are other people using similar system in this situation

---

