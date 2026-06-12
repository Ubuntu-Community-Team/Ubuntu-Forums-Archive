---
title: "Cannot send email with sendemail"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by kitama on 2013-02-18
[LEFT]I am a newbie and have a few questions.

If I send an email through my gmail account I get the following error message:

     Code:
     server sendmail [15257]: ERROR => ERROR => SMTP-AUTH: Authentication to smtp.gmail.com: 25 failed. 
How do I send an e-mail:

     Code:
     sendEmail -f [EMAIL="username@foo.com"]username@foo.com[/EMAIL] -t [EMAIL="destination@foo.com"]destination@foo.com[/EMAIL] -u "Message title" -m "The body of the message" -s smtp.gmail.com:25 -xu username -xp password 
Should I replace [EMAIL="username@foo.com"]username@foo.com[/EMAIL] with my own email address and [EMAIL="destination@foo.com"]destination@foo.com[/EMAIL] with that of the recipient?

And what do I fill in at: -xu username and -xp password? My gmail  account details or something else? Can someone give an example, thanks!

Sorry, for my bad English.

See also the following thread:

[http://ubuntuforums.org/showthread.php?t=1127478](http://ubuntuforums.org/showthread.php?t=1127478)
[/LEFT]

---

### Post by martynfigu on 2013-02-18
Hi KITAMA.

If you're using Thunderbird, try it:

- EDIT>ACOUNT SETTINGS
- OutGoing Server

In GOOGLE MAIL (smtp.gmail.com)
- EDIT

In PORT you have to change to 587.
Verify Conection Security if its in STARTTLS
And verify your username.

[email]username@gmail.com[/email]


I hope you have solved your question.

[ ]'s

---

