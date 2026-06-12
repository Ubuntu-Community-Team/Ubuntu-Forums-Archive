---
title: "Bash Script Help"
date: 2009-07-23
forum: Programming Talk
---

### Post by CosmicFlux on 2009-07-23
Hey,

I'm playing around with scripting at the minute, and using the command line in general to gain a better understanding of Linux. 

I've had an idea to write a script to automatically log in via FTP to my website but I'm not sure how to get the script to wait for the USER and PASS prompts before entering that information. 

Any suggestions?


Cosmic

---

### Post by rbishop on 2009-07-23
Here is what I had from a previous script I was using.

```


HOST='xx.xx.xx.xx'
USER='username'
PASSWD='password'

ftp -nv $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
put $FILE
quit


END_SCRIPT

```

---

### Post by renkinjutsu on 2009-07-23
download and install `expect` from the repos

write a script that is interpreted with expect
#!/bin/expect (or wherever expect is)
spawn ftp
expect "text from the prompt"
send "username"
expect "text from the prompt"
send "password"


then save that as an executable file and reference to it in your script

---

### Post by dlmarti on 2009-07-23
> **CosmicFlux said:**
> Hey,

I'm playing around with scripting at the minute, and using the command line in general to gain a better understanding of Linux. 

I've had an idea to write a script to automatically log in via FTP to my website but I'm not sure how to get the script to wait for the USER and PASS prompts before entering that information. 

Any suggestions?


Cosmic

before you go too far, look at ncftpput and ncftpget in the ncftp package.

---

### Post by lensman3 on 2009-07-23
Try something like:

  ```
 (
   cat << EOF
From: $RETURNADD
Subject: $SUBJECT
To: $REC
EOF

cat $MSGFILE
   )  | $SENDMAIL -f $RETURNADD  $REC
```

This is a snippet that was the guts of a sendmail mass mailer.  The "here document" you have has to be first expanded by the shell.  In your case the $VALs don't get expanded.

Hope this helps (a little).

---

