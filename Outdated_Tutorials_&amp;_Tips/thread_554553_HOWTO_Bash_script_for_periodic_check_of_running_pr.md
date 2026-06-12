---
title: "HOWTO: Bash script for periodic check of running process (with mail warning)"
date: 2007-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by megadesign on 2007-09-19
Hi!

I wrote a small sh script for checking if particular process is running.

The script need to be started as "service" (./script &). If you want to start it as soon as Ubuntu is loaded, add line "/path/to/script/script.sh &" without quotes to /etc/rc.local.

When script is running, it periodically check if defined process name is up and running.

When checked process isn't found (crashed!), the script will send some warning e-mail to the defined address and will try to start that process again (check permissions to run process). This warning e-mail is send only once until process is again started.

If starting of the checked process is successful, e-mail with this info is send.

Save code bellow to some file and enable permissions for executing of that file.

```

#!/bin/sh

MAILSTOP=0                         # switcher for mail sending
CHECKINGPERIOD=20                  # in sec
MYEMAIL="me@myemail.com"           # where to send info

while [ 1=1 ];
do

    if [ ! "$(pidof httpd)" ]
    then
        if [ "$MAILSTOP" = "0" ]; then
            echo "WARNING! Apache crashed!" | mail -s "Apache crash." "$MYEMAIL"
            MAILSTOP=1
        fi
        /www/bin/apachectl start
    else
        if [ "$MAILSTOP" = "1" ]; then
            echo "Apache was successfully restarted." | mail -s "Apache restarted." "$MYEMAIL"
            MAILSTOP=0
        fi
    fi
    sleep $CHECKINGPERIOD

done

```

I'm using it for checking Apache web server every 20 seconds, so this process name (httpd) is in code above. For me, it send sms-email to my mobile phone. This all can be changed for your needs. I'm sure, it can do a big range of another things, but this is basic script, which fulfil my needs.

**Requirements:**
In Ubuntu 7.04 it requires installation of mail command, which is in package mailx. For example:

```
apt-get install mailx
```

Enjoy!

---

### Post by riotxix on 2008-03-17
Hi,

this had me perlexed for days. mail doesn't work, or give an error (unless I do it through my hosting company). Why? Because mail does not allow you to specify an smtp sever to relay your mail through, and unless you can go through the the grief of setting up you machine as a bonafide mail server, you're attempts will get rejected by the recepient as spam (without informing you).

Solution:
use nail, which does allow you to specify an smtp server to relay your mail through. You don't need to go through any sendmail config files.

[http://forums.fedoraforum.org/showthread.php?t=143690](http://forums.fedoraforum.org/showthread.php?t=143690)
"Rupert Pupkin"
<i>The problem with the standard 'mail' command is that it assumes that the machine it is running on is a full-fledged SMTP server. So unless you've configured your machine to be a bonafide mail server (or to act as an SMTP relay), then your mail will not go anywhere outside your machine (i.e. it will only work for addresses local to your machine, e.g. some_user@localhost). There is no way to specify an external SMTP server (like your ISP's) to use with the 'mail' command. That's why you're getting a dead letter.

If you want a command-line mailer that does support using an external SMTP server, then get nail from Fedora Extras. Nail supports specifying an external SMTP server. You can do this on a per-mail basis, like this:

nail -r "myaddress@something.com" -s "Some subject" -S smtp=some.smtp.server [email]info@company.com[/email] < msg.txt

or you can permanently set the SMTP server in your ~/.mailrc file (or /etc/nail.rc if you want to set it system-wide), which removes the need for using the "-S smtp=..." option on the command-line:

set smtp=some.smtp.server

See the nail man page for more details. In my opinion, no one should be using 'mail' anymore, nail is vastly superior."</i>

apt-get install nail

---

