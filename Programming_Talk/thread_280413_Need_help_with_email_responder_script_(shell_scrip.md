---
title: "Need help with email responder script (shell script?)"
date: 2006-10-19
forum: Programming Talk
---

### Post by smiley2billion on 2006-10-19
Hello all.  This may not be an Ubuntu specific question, but the people in this community are the smartest around, so I thought I'd ask here.

I'm looking for a way to do this:

A person sends an email to an email account.  The receiving email account automatically responds with an image pulled from a website and sends it back as an attachment to the original sender. What I'm looking to do is pull a dopplar radar scan from a site like weather.com.  All of their current radar images have a static name (the image gets updated, but the name stays the same).  It will be used at work when email is available but since we're behind a proxy, most web sites are not. I would like to be able to kick out an email and a few minutes later have a response with the latest dopplar image.

I realize what has to happen, but don't really know the process to do it.  It'd be nice to have something like givememyweather [at] gmail.com be the address that I have to send a message to.

I hope I made this clear enough, if someone reads this and has a question as to what I'm trying to accomplish, please feel free to ask.

---

### Post by cwaldbieser on 2006-10-20
> **smiley2billion said:**
> Hello all.  This may not be an Ubuntu specific question, but the people in this community are the smartest around, so I thought I'd ask here.

I'm looking for a way to do this:

A person sends an email to an email account.  The receiving email account automatically responds with an image pulled from a website and sends it back as an attachment to the original sender. What I'm looking to do is pull a dopplar radar scan from a site like weather.com.  All of their current radar images have a static name (the image gets updated, but the name stays the same).  It will be used at work when email is available but since we're behind a proxy, most web sites are not. I would like to be able to kick out an email and a few minutes later have a response with the latest dopplar image.

I realize what has to happen, but don't really know the process to do it.  It'd be nice to have something like givememyweather [at] gmail.com be the address that I have to send a message to.

I hope I made this clear enough, if someone reads this and has a question as to what I'm trying to accomplish, please feel free to ask.

Maybe you could have a program running on your home PC that scans your mailbox for subject lines like "send doppler image".  If it finds one, it could delete it and send the message to you.

You should be able to do this with command line tools and a little shell scripting, but I am not that familiar with non-interactive mail tools.  Here is a little python code that could get you started:

```

import mailbox
import time

mbox = mailbox.Maildir("Mail/inbox")
for msg in mbox:
    subject = msg.getheader("subject")
    if subject == "send doppler":
        #Code to get image from web site here-- use urllib
        #Code to send mail to your work address here.
        #Code to delete message from mailbox here.
    time.sleep(120) #Wait 2 minutes, try again.

```

There are a lot of blanks in this code-- I don't know offhand what the library calls are to do these, though I am fairly certain they are part of the standard library.  This code assumes that you have a POP3 client like KMail pulling down your mail every minute or so.  It also assumes a Maildir style mailbox, and it doesn't account for two programs writing to the mailbox at the same time, but I think it gets the basic idea across.

---

