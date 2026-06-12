---
title: "Trying to send a non-interactive mail message from the shell"
date: 2009-06-16
forum: Programming Talk
---

### Post by Luke has no name on 2009-06-16
The man pages for mail and mailx weren't helping me find how to send a mail from the command line. I'm trying to set up a script that mails when it finds certain logs have been updated. I need a non-interactive command for that, and the perl install is too old to have net::smtp. (I'm setting this up on a Solaris 9 box).

Help, please!

---

### Post by stair314 on 2009-06-16
Your could try the smtplib and email.MIMEText modules in python: 

try:
                global fromaddr
                s = smtplib.SMTP('smtp.stanford.edu')
                s.sendmail(fromaddr, [to], message)
                s.quit()
        except:
                s.quit()
                raise

---

### Post by slavik on 2009-06-16
i've used the below in the past:

Cat textfile | mailx -s Subject [email]mail@domain.com[/email]

---

