---
title: "Detect email delivery failure in bash script"
date: 2007-11-16
forum: Programming Talk
---

### Post by kunilkuda on 2007-11-16
Hi all,

I've been using bash script to maintain backup in some remote servers. Every day, the bash script will send me email, with backup as attachment. 

The problem is that the remote server's connection is not reliable (it uses dial-up connection..most of the time it works). So, how do I detect the email delivery failure in the script, in order to make another sending retry ?

I'm using ubuntu dapper and nail (/usr/bin/nail), and ISP's SMTP to relay my mail.

Thank you very much for your help

---

### Post by AlanMacdonald on 2007-11-20
I don't know much about the nail command you are using at all but you might get a different return status from it depending on success maybe?

So you could try 
```

result=`nail args.........`

```

 and then check on the value of $result.  Traditionally I guess it would be 0 on success and 1 otherwise but it might be a long shot.  Maybe the man page will say something about return values but my system does not have nail installed.

---

### Post by kunilkuda on 2007-11-20
Thanks Alan,

I've found the answer for this problem. 

The first problem with : ```
result=`nail args.........`
``` is that "nail" seems creating child process to send the mail. So, whether it's sent or not, you'll get success as return value (the error return value only happens if "nail" cannot create its child process).

Also, nail's child process will dump the error into stderr and dead.letter file, which is uncatchable using 
```
result=`nail args.........`
```

So, what I'm currently doing is :
[LIST=1]
[*]Make sure that the script waits until child process is done, using :
```
echo `nail args....`
```
[*]Use dead.letter file as a sign that the email delivery failed. If the script is done, and dead.letter file is found, it means that the deilvery failed.
[*]Second alternative to dead.letter : redirect nail's stderr to file
```
echo `nail args.... 2>result`
```
If the file is empty, it means email delivery was successful. Otherwise, it failed.
[/LIST]

---

### Post by geirha on 2007-11-20
If it fails to connect to the smtp server, it should return non-zero. Try the following with a mail you know will succeed and one that you know will fail
```
if nail args; then
  echo "nailed it"
else
  echo "failure"
fi
```

---

