---
title: "How To: &quot;easily&quot; read offline email backed up to a Maildir directory"
date: 2011-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2011-07-31
So, is your gmail account filling up? Mine was so I set about backing it all up. I used the excellent getmail program:
```
sudo apt-get install getmail4
``` and followed the nice tut here:
```
http://www.mattcutts.com/blog/backup-gmail-in-linux-with-getmail/
``` scroll down through the comments to find the script that prevents multiple instances of getmail running.



Anyway, I chose to go the Maildir route > many files as opposed to one big one, so now I have a folder stuffed with 6GB of email I can't easily read or search.

Fortunately I am running a server install of Ubuntu 10.04 LTS and chose the postfix/dovecot options at installation - but have done nothing with them since then. I have also installed webmin for http access to the server.

**So you'll need a server install, postfix and dovecot, and webmin all up and running, with your mail archive somewhere on the server.**



This is where it gets to the "easily" bit. ;)

[LIST=1]
[*]Fire up **Webmin** through your browser, open up the **Servers** section and click on **Read User Mail**.

[*]You'll see a list of possible mailboxes, but below this is a small dialog suggesting: **"Read Mail In File"** with a text entry box and a file browser button.

[*]Click on the text entry button and browse to your mail folder - you only need to select the main folder (the one that contains new/cur/tmp). Click OK in the file selection dialog and then click on the "Read Mail In File" button.

[*]You should see all your mail and be able to read them in email format and open and save attachments and / or delete emails.
[/LIST]

Now back to gmail to delete the old and crufty, safe in the knowledge that you can access any email you have deleted. The benefit for me was not having to run another email client which would want to "download" the email again!

I guess this will work with an mbox file as well?

Hope this is useful for someone, I couldn't find much on google about how to read a Maildir directory, but Webmin had the answer.

EDIT

I have also found a java applet - JavaMailDir - but can't get it to work - yet

---

