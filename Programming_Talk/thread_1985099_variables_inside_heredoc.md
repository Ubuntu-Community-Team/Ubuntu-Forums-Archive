---
title: "variables inside heredoc"
date: 2012-05-22
forum: Programming Talk
---

### Post by woodson2 on 2012-05-22
I currently use this message to send e-mails in a script but I would also like to save the output of this code to a file as well while preserving the variables. What's the easiest way to accomplish this?


```
#Sending mail notification
when=`/bin/date`
/usr/sbin/sendmail -t >2 <<-EOM
Subject:User access disabled.
From:testuser@test.com
To:$EMAIL
User $USERNAME has been disabled.


Regards,
$variable Support.
EOM
```

---

### Post by trent.josephsen on 2012-05-22
What do you mean by "while preserving the variables"?

Could the **tee** command be what you're looking for?

---

### Post by matt_symes on 2012-05-23
Hi

What about saving to the file and then sending that file ? (not as an attachment though)

```
#Sending mail notification
when=`/bin/date`
cat <<-EOM > filename
Subject:User access disabled.
From:testuser@test.com
To:$EMAIL
User $USERNAME has been disabled.


Regards,
$variable Support.
EOM

/usr/sbin/sendmail -t < filename
```

I have not tested this so i don't know if it works.

Kind regards

---

