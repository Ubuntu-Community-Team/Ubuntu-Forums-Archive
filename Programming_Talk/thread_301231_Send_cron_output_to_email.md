---
title: "Send cron output to email"
date: 2006-11-16
forum: Programming Talk
---

### Post by neoaddict on 2006-11-16
How would I send the output from my cron script to my email?

---

### Post by yabbadabbadont on 2006-11-16
Just print it to standard out (i.e. the console).  By default, all text output of cron jobs is emailed to the user to whom the crontab belongs.

---

### Post by neoaddict on 2006-11-16
How would I do that?  (Sorry, little new to scripting on Linux :( )

I'm root on my computer, and how do I set the email address for my account?

---

### Post by neoaddict on 2006-11-17
Bump.

---

### Post by dwblas on 2006-11-20
You setup the default when you install the mail program.  If you haven't done that already then install exim4 via synaptic or whatever.  Note that it will ask you questions like who to sent the default output to, so on second thought it might be better to apt-get install exim4.  It works fine for me.  The debian page is [http://pkg-exim4.alioth.debian.org](http://pkg-exim4.alioth.debian.org)

---

### Post by Jott on 2006-11-20
Thanks!

installing it now.

---

### Post by Jott on 2006-11-20
Ok, installed...um, how do I configure it?  It asked me what kind of a mail thing I wanted to use (I told it SMTP, thinking that then I could use my regular email address) but it never asked me what my email address was, or where my SMTP server was...am I missing something?

Thanks!

---

### Post by dwblas on 2006-11-20
It should have asked you where to send messages or root's e-mail.  Check /etc/aliases as I think it uses this file unless you say differently.  Add something to cron for testing, like an nist clock update, that will run periodically so you can see if it functions as you want.

---

### Post by Baji on 2006-11-25
I've got the same issue im quite lost here the exim4-config package only asks a question about the configuration type - like internet / smarthost.

after doing a dpkg-reconfigure exim4-config I was promted to enter more options, but still no default email adres to send to.

I've looked at /etc/aliases but all it says is root: user

help in getting the cron messages sent to email would be greatly appreciated

---

### Post by dwblas on 2006-11-25
Try putting MAILTO=username in the top part of your crontab file.  Then run something periodically to see what happens.  I didn't have any problems at all so I'm not sure what the problem is.  A second thought is to check /var/mail. /var/spool/mail and your home directory to be sure that it isn't being sent somewhere else.

---

