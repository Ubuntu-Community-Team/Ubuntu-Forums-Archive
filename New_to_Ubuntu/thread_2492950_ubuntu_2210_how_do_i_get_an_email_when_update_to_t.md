---
title: "ubuntu 22/10 how do i get an email when update to the system download and install"
date: 2023-11-28
forum: New to Ubuntu
---

### Post by rpereg on 2023-11-28
Helloi want to get an email when 'system update and install on my system .

Enable Ginger*Cannot connect to Ginger* Check your internet connection
 or reload the browserDisable in this text fieldRephraseRephrase current sentenceEdit in Ginger×

---

### Post by TheFu on 2023-11-28
I'm confused and don't understand the question.
Please ask specific questions, if you want specific answers.  Exactly what "system update"?  What "install"?

If a GUI gets used for updates/installs, I don't have a clue.

If you setup an MTA like postfix correctly and use cron to schedule updates, then when the cron-job finishes, all output will be emailed to the account on the system who ran the cron-job.
I suspect there's a way to forward local email using an MTA to an external email account, but since I've been running email servers, including my own, since the mid-1990s, I don't know how.  

I don't know of any way to get snap package updates to provide notifications.  I guess someone could create a script to compare packages installed yesterday with packages installed today, perhaps every morning at boot or 5am and have that output emailed somewhere.  


You could google for setting up gmail to work with postfix.  That's the only way I know to get cronjob output to external email accounts. Obviously, gmail is just 1 external email type.  Since SMTP is a standard protocol, it should be possible to setup other providers too.  Also, many ISPs will block outbound SMTP on port 25 (which is what MTAs use), so you'll need to use their email relay server.

BTW, support for 22.10 ended last June. No more response until you move to 22.04, 23.10 or 24.04 which are the currently supported releases.  Best not to install non-LTS releases.

---

### Post by MAFoElffen on 2023-11-28
After you migrate to something supported, where you can install something or get updates, then we can talk. 

Right now, nothing is going to work, because you are not getting any updates of any kind, right?

---

### Post by ian-weisser on 2023-11-28
If Ginger cannot connect to the network, then you may not be receiving the email anyway.

---

