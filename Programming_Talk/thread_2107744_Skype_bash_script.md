---
title: "Skype bash script"
date: 2013-01-22
forum: Programming Talk
---

### Post by Robbyx on 2013-01-22
I am trying to write a bash script that will send an email with the name of the person who is starting a chat in skype and also the content of the message.

From elsewhere I learn that the following script should load those items into variables, but I can not get the variables to show in the email. 

Should I be using the echo command in skype_logged_in.txt?

# command entered into skype notification for first new message
sh skype_firstchat.sh "%sname" "%smessage"


# skype_firstchat.sh
#!/bin/bash
ssmtp [email]a@b.co.uk[/email] < ./skype_notifications/skype_logged_in.txt 

#skype_logged_in.txt
To: [email]a@b.co.uk[/email]
From: [email]a@b.co.uk[/email]
Subject: $sname


$smessage

---

