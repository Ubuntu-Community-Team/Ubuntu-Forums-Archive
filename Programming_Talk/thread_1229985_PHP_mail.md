---
title: "PHP mail"
date: 2009-08-02
forum: Programming Talk
---

### Post by desperateone on 2009-08-02
I have this code;

```

<html>
  <head>
    <title>Mailer</title>
  </head>

  <form method="post" action="mailer.php">
    Email1: <input name="email1" type="text"><br>
    Email2: <input name="email2" type="text"><br>
    Email3: <input name="email3" type="text"><br>
    <textarea name="message" rows="15" cols ="80"></textarea><br>
    <input type="submit" value="Send">
  </form>
</html>

```


```
<?php
  $email1 = $_POST['email1'];
  $email2 = $_POST['email2'];
  $email3 = $_POST['email3'];
  $messg = $_POST['message'];

  $fin1 = mail($email1,
              "Email test",
              $messg);

  $fin2 = mail($email2,
              "Email test",
              $messg);

  $fin3 = mail($email3,
              "Email test",
              $messg);

  echo "Sending the message ($messg) to three guys<br>";
  echo ($fin1 ? "1 Done<br>" : "Not done :(<br>");
  echo ($fin2 ? "2 Done<br>" : "Not done :(<br>");
  echo ($fin3 ? "3 Done<br>" : "Not done :(<br>");
?>
```


It tells me that it's sent, but the mail never reaches the recipient. I don't really know what's going on, any help is useful.

---

### Post by Dill on 2009-08-02
Do you know which [Mail Transfer Agent]("http://en.wikipedia.org/wiki/Mail_transfer_agent") you're using? I believe it's normally Postfix or Exim on an Ubuntu system. Try

```
ps aux | grep postfix
ps aux | grep exim
```

And see which one, if any, is running.

If PHP is telling you the mail has been sent, the problem may be with the MTA. Find which MTA you're using and check out the log files immediately after trying to send mail. For instance, my Exim logs are in /var/log/exim4 . Here is part of my Exim *mainlog* after successfully sending mail:

```
TCDBSANDBOX:/var/log/exim4# tail mainlog
2009-08-01 22:19:24 Start queue run: pid=9273
2009-08-01 22:19:24 End queue run: pid=9273
2009-08-01 22:49:24 Start queue run: pid=9297
2009-08-01 22:49:24 End queue run: pid=9297
2009-08-01 23:19:24 Start queue run: pid=9358
2009-08-01 23:19:24 End queue run: pid=9358
2009-08-01 23:22:42 1MXSao-0002Qz-42 <= www-data@tcdb.ath.cx U=www-data P=local S=578
2009-08-01 23:22:43 1MXSao-0002Qz-42 => satherdy@grinnell.edu R=dnslookup T=remote_smtp H=ipfilter2.grinnell.edu [132.161.10.132]
2009-08-01 23:22:43 1MXSao-0002Qz-42 -> tc@grinnell.edu R=dnslookup T=remote_smtp H=ipfilter2.grinnell.edu [132.161.10.132]
2009-08-01 23:22:43 1MXSao-0002Qz-42 Completed
```

You should find your MTA logs and do a little investigation...

Cheers,
Dill

---

### Post by desperateone on 2009-08-03
Well, I was using postfix, it was not running, so I want to turn it on, but...
```
[$] ps aux | igrep post
jeremy     31280  0.0  0.0   3236   868 pts/1    S+   12:00   0:00 grep -i post
[$] sudo postfix start
postfix/postfix-script: starting the Postfix mail system
[$] ps aux | igrep post
jeremy     31362  0.0  0.0   3236   864 pts/1    S+   12:01   0:00 grep -i post
```

---

### Post by desperateone on 2009-08-03
Heh. I decided to do random things and apt-got sendmail (even though I have done it yesterday, successfully). And now it works. Weird.

---

