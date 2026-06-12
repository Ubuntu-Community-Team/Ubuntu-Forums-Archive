---
title: "Email to sms script, help needed."
date: 2010-11-10
forum: Programming Talk
---

### Post by msjones on 2010-11-10
Hi guys,

In need of help with a little script ive been working on. First some backstory.

I work for a law firm and one of our services is updating clients via sms. The sms is built using a word document and emailed to a generic sms user set up on the mail server. The script then runs removing the header information from the email, greping the message and number details and then echos is to the template to be sent to our service provider. The script is basic but works like a charm.

Heres the script:

```
#!/bin/sh
cd /home/sms/Maildir/new

case $# in
1) FILE=$1 ;;
*) echo "You need to select a file"; exit ;;
esac

CLINUM=`grep '^smssmssmsphoneno:.*.$' $FILE | sed 's/smssmssmsphoneno://' | sed 's/^0/44/' | sed 's/ //'`
MESSAGE=`grep '^Dear.*.$' $FILE`

ENDLINENO=`grep -n '^X-MimeOLE: Produced By Microsoft MimeOLE V6.00.3790.4721' $FILE | cut -d':' -f1 `

#Now build the sms message

echo To:**** > sms.$$
echo From:**** >> sms.$$
echo "" >> sms.$$
echo api_id:**** >> sms.$$
echo user:**** >> sms.$$
echo password:**** >> sms.$$
echo to:$CLINUM >>sms.$$
echo from:**** >> sms.$$
echo text:$MESSAGE >> sms.$$

#Send sms to clickatell and archive the message

cat sms.$$ | mail ****
mv sms.$$ /tmp/sms

```

The problem I am having is with this section:

```
case $# in
1) FILE=$1 ;;
*) echo "You need to select a file"; exit ;;
esac
```

The script only works when file is specified as that is the only way I know how to it. How do I get it work on file at a time, complete it then delete after sending and then move on to the next file in the directory?

If I can get this working I can add to CRON and leave it running.

Thanks in advance for any help, its really appreciated.

---

### Post by msjones on 2010-11-11
Sorted, this seems to have worked for me!

```
#!/bin/bash

DIR=/home/sms/Maildir/new
for i in `ls $DIR`
do
        echo "doing $i...."
        /home/utils/test_area/newsms.sh $i
        rm $i
done

```

---

