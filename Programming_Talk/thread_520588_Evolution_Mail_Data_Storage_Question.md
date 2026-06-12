---
title: "Evolution Mail Data Storage Question"
date: 2007-08-08
forum: Programming Talk
---

### Post by mavicus on 2007-08-08
SCENARIO--
I am running Ubuntu 7.04
Notably, I have installed Apache2, PHP5, mySQL, cURL, and the pre-installed Evolution mail client.
I have written a php script with the purpose of automating email account creation and setup on my webhost and in my evoution mail settings.
The script accepts a username for an email account through an html form. Then it:

1. Shuts down evolution processes and gconftool-2.
(I was unable to do this with the instructions on using "evolution --force-shutdown" because of a "cannot find display:" error, when   using php exec(), so instead I am using a series of exec() commands to run ps -A | grep evolution, parse the results for process IDs and then exec() with a kill command for each.
I can confirm that all evolution processes DO shutdown.
The gconftool-2 program does not appear to be running to begin with, but I exec("gconftool-2 --shutdown") and it doesn't throw any errors or other messages. I cannot find it with ps -A, unless I don't know what to look for, so I assume it is not running.

2. The script then modifies a couple text files and creates a couple directories and files inside the .evolution and .gconf folders. The list of files modified is as follows...
    modify: .evolution/mail/filters.xml
    create: .evolution/mail/config/et-expanded-mbox:_home_username_.evolution_mail_local#Inbox_accountname@domain.com
    create: .evolution/mail/local/Inbox.sbd/accountname
    create: .evolution/mail/local/Inbox.sbd/accountname.cmeta
    create: .evolution/mail/pop/accountname@mail.server.com
    create: .evolution/mail/pop/accountname@mail.server.com/uid-cache
    modify: .gconf/apps/evolution/mail/%gconf.xml

3. Finally, the script uses curl to login to my web host and create a matching email account and set the password.

Everything works beautifully, except that when evolution is started back up after this, the %gconf.xml file is being reverted back to the version before my changes are written to it.

MY QUESTION--
What is there that's still running that doesn't like me changing %gconf.xml?

Or, how have I missed gconftool-2 shutdown and what should I be looking for to confirm that it is shut down?

---

### Post by mavicus on 2007-08-23
UPDATE: Issue has been worked out.

The better way to accomplish this was to use gconftool-2 to insert the data rather than write to the files directly. This information came from the evolution-hackers mailing list.

---

