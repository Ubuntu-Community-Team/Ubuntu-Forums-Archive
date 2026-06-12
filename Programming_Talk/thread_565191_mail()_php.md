---
title: "mail() php"
date: 2007-10-02
forum: Programming Talk
---

### Post by spur on 2007-10-02
Is there a way to check if  mail is being sent from a script (php)?
I have installed sendmail and I don't get any error messsages and I can't see sendmail in usr/bin.
That is where it says it is when I run my info.php file. (phpinfo()).

---

### Post by Compyx on 2007-10-02
How about sending mail to an account you own? On my system the sendmail binary is located in /usr/sbin, not /usr/bin.

---

### Post by spur on 2007-10-02
Thanks. I looked there and it was not there so I uninstalled sendmail and reinstalled. It is now there. That is a link to '/usr/lib/sm.bin/sendmail'.

---

### Post by spur on 2007-10-02
Still not actually sending e-mails and general slow down of internet connection. Any clues?

---

### Post by mssever on 2007-10-02
Can you send mail from the command line? ```
echo "test message" | mail -s "My subject" your@email.com
```

---

### Post by spur on 2007-10-03
I get 'mail command not found'

---

