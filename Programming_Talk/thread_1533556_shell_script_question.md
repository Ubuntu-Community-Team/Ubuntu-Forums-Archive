---
title: "shell script question"
date: 2010-07-18
forum: Programming Talk
---

### Post by learnbash on 2010-07-18
Hello folks,

I have a file like

```

mydomain.dd 2010-08-02
newdomain.dd 2010-09-05
dddp.dd 2010-10-05

```
above are domain list with expired date, how i can make script that will check each domain and its associated expired date if it is 30 or less then display alert that xyz domain will be expire on this date otherwise dont do anything else.

Please help

---

### Post by DanielWaterworth on 2010-07-18
This is pretty simple in Python, assuming format is "year-month-day"

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(date[0], date[1], data[2])
        if date - datetime.date.today() < datetime.timedelta(30):
            print domain
```

---

### Post by learnbash on 2010-07-18
> **DanielWaterworth said:**
> This is pretty simple in Python, assuming format is "year-month-day"

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(date[0], date[1], data[2])
        if date - datetime.date.today() < datetime.timedelta(30):
            print domain
```

Thanks i run your script i got below error.

```


Traceback (most recent call last):
  File "aa.py", line 11, in <module>
    date = datetime.date(date[0], date[1], data[2])
NameError: name 'data' is not defined


```

---

### Post by DanielWaterworth on 2010-07-18
sorry, that's a typo, it should be date. This should fix it:

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(date[0], date[1], date[2])
        if date - datetime.date.today() < datetime.timedelta(30):
            print domain
```

---

### Post by learnbash on 2010-07-18
> **DanielWaterworth said:**
> sorry, that's a typo, it should be date. This should fix it:

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(date[0], date[1], date[2])
        if date - datetime.date.today() < datetime.timedelta(30):
            print domain
```

not working.

```

#python aa.py domain.txt 
Traceback (most recent call last):
  File "aa.py", line 11, in <module>
    date = datetime.date(date[0], date[1], date[2])
TypeError: an integer is required


```

---

### Post by DanielWaterworth on 2010-07-18
ha, maybe I should have tested this first =P

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(int(date[0]), int(date[1]), int(date[2]))
        if date - datetime.date.today() < datetime.timedelta(30):
            print domain
```

---

### Post by learnbash on 2010-07-18
> **DanielWaterworth said:**
> 
ha, maybe I should have tested this first =P


only domain showing not showing expire date

---

### Post by DanielWaterworth on 2010-07-18
change the last line to "print line" instead of "print domain" and the white-space matters.

---

### Post by learnbash on 2010-07-18
> **DanielWaterworth said:**
> change the last line to "print line" instead of "print domain" and the white-space matters.

Thanks, i need to add one thing it also tell the 5 days left for particular domain expiration.

---

### Post by DanielWaterworth on 2010-07-18
I hope this is what you meant:

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(int(date[0]), int(date[1]), int(date[2]))
        if date - datatime.data.today() <= datetime.timedelta(5):
            print 'important: less than 5 days for' + line
        elif date - datetime.date.today() <= datetime.timedelta(30):
            print line
```

---

### Post by DaithiF on 2010-07-18
in bash, something like:
```
threshold=$(( 60 * 60 * 24 * 30 ))
now_seconds=$(date +%s)
while read domain expiry
do
    expiry_seconds=$(date -d $expiry +%s)
    seconds_till_expiry=$(( expiry_seconds - now_seconds ))
    [[ $seconds_till_expiry -le $threshold ]] && echo "Domain $domain expires on
 $expiry"
done < somefile
```

---

### Post by learnbash on 2010-07-18
Thanks, But it is giving error. Actually lets suppose if 30 days left for domain expiry then it shows that domain, but when daily i run script it tell me that 30 days left, 29 days left, i mean till last day it show that how much days for domain will be going to expire.

```

Traceback (most recent call last):
  File "aa.py", line 12, in <module>
    if date - datatime.data.today() <= datetime.timedelta(5):
NameError: name 'datatime' is not defined


```

---

### Post by DanielWaterworth on 2010-07-18
I'm constantly mistyping data for date. Is this right?

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(int(date[0]), int(date[1]), int(date[2]))
        delta = date - datetime.date.today()
        if delta <= datetime.timedelta(30):
            print "%idays to go for '%s'" (delta.days, line)
```

---

### Post by learnbash on 2010-07-18
Now
```

Traceback (most recent call last):
  File "aa.py", line 14, in <module>
    print "%idays to go for '%s'" (delta.days, line)
TypeError: 'str' object is not callable

```

---

### Post by DanielWaterworth on 2010-07-18
I've actually tested this one.

```
import datetime, sys

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(int(date[0]), int(date[1]), int(date[2]))
        delta = date - datetime.date.today()
        if delta <= datetime.timedelta(30):
            print "%idays to go for '%s'" % (delta.days, line[:-1])
```

---

### Post by DaithiF on 2010-07-18
Hi, since your handle is 'learnbash', I'm assuming bash is of some interest to you, so heres an updated bash version which includes your other requirements:
```
days_30=$(( 60 * 60 * 24 * 30 ))
days_5=$(( 60 * 60 * 24 * 5 ))
days_1=$(( 60 * 60 * 24 ))
now_seconds=$(date +%s)
while read domain expiry
do  
        expiry_seconds=$(date -d $expiry +%s)
        seconds_till_expiry=$(( expiry_seconds - now_seconds ))
        days_till_expiry=$(( seconds_till_expiry / days_1 + 1))
        if [[ $seconds_till_expiry -lt 0 ]]; then
                echo "Too late, Domain $domain expired on $expiry"
        elif [[ $seconds_till_expiry -le $days_5 ]]; then
                echo "Important, Domain $domain expires in $days_till_expiry days on  $expiry (less than 5 days)"
        elif [[ $seconds_till_expiry -le $days_30 ]]; then
                echo "Domain $domain expires in $days_till_expiry days on $expiry"
        fi
done < testfile

```

---

### Post by learnbash on 2010-07-18
Thanks. Is it possible i can email output from python to [email]admin@example.com[/email]

---

### Post by kaivalagi on 2010-07-18
> **learnbash said:**
> Thanks. Is it possible i can email output from python to [email]admin@example.com[/email]
[http://docs.python.org/library/smtplib.html](http://docs.python.org/library/smtplib.html)

---

### Post by learnbash on 2010-07-18
smtp is already configure, just need to sent i dont python , can please help

---

### Post by DanielWaterworth on 2010-07-18
```
import datetime, sys, smtplib

if len(sys.argv) != 2:
    print "usage: %s filename" % sys.argv[0]
    sys.exit(1)

output = ""
with open(sys.argv[1], 'r') as f:
    for line in f:
        domain, date = line.split(' ')
        date = date.split('-')
        date = datetime.date(int(date[0]), int(date[1]), int(date[2]))
        delta = date - datetime.date.today()
        if delta <= datetime.timedelta(30):
            output += "%idays to go for '%s'\n" % (delta.days, line[:-1])

smtpObj = smtplib.SMTP('smtp.blueyonder.co.uk') # change this to your isp's smtp
# uncomment the next line if you need to login
# smtpObj.login('username', 'password')
smtpObj.sendmail("from@example.com", ["admin@example.com"], output)
```

---

### Post by learnbash on 2010-07-18
Thanks getting error.

```

File "emaildomain.py", line 4
    print "usage: %s filename" % sys.argv[0]
        ^
IndentationError: expected an indented block
[root@server1 domain-checking]# python emaildomain.py 
  File "emaildomain.py", line 4
    print "usage: %s filename" % sys.argv[0]
        ^
IndentationError: expected an indented block

```

---

### Post by DanielWaterworth on 2010-07-18
I forgot to add code blocks, but I've edited, try copying and pasting again.

---

### Post by learnbash on 2010-07-18
subject is blank, how to add subject?

---

### Post by learnbash on 2010-07-18
Thanks i am able to resolve that by using

```


msg = MIMEText(output)
msg['To'] = email.utils.formataddr(('Recipient', 'new@example.com'))
msg['From'] = email.utils.formataddr(('Author', 'new@example.com'))
msg['Subject'] = 'Domain Expiry notice'

server = smtplib.SMTP('mailserver.domain.com'')
server.set_debuglevel(True) # show communication with the server
server.sendmail('new@example.com', ['new@example.com'],msg.as_string())
server.quit()


```

---

