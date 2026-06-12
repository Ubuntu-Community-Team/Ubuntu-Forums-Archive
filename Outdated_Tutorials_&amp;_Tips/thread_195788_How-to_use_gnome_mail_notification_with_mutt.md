---
title: "How-to: use gnome mail notification with mutt"
date: 2006-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by magisterludi on 2006-06-13
I am annoyed of the lack of mail notification to be able to open always the right maildir if i got new mail. one can specifiy a command to execute if there is new mail, but there are no (documented parameters) for the command.

So i hacked a little ruby and bash scripts to get a magic "I always open the right mailbox for you" functionality.

You need to have ruby and mailcheck installed.

As command to execute if one gets new mail:
$HOME/scripts/newmail.sh:

```

touch $HOME/.mailReport.txt
mailcheck > $HOME/.mailReport.txt

```

and as command to execute if one wants to read the mail of the mailbox which has new mails:

$HOME/scripts/openMaildir

```

#!/usr/bin/ruby

report = File.open("$HOME/.mailReport.txt")
newmail = Array.new

report.each_line{ |line|
        if line.include? "new"
        print "Opening: "+line.split(" in ")[1]
        `gnome-terminal --geometry=100x50+250+50 -e "mutt -f #{line.split(" in ")[1]}"`
        `echo off >/proc/acpi/ibm/light` #_for thinkpads only_ if you have light notificaion
        end
}



```

have fun! share your thoughts

---

### Post by chanders on 2006-06-13
I must say... very nice clean solution. Wish I had seen it before. I however use mail-notification which does a pretty good job also

---

### Post by brk3 on 2010-07-07
Old thread but here's a similar/alternative way if people are interested:

```

#!/bin/bash

last=0
cur=0

while [ : ]
do
  mailcheck | grep new 2>&1 >/dev/null
  if [ $? -eq 0 ]
  then
    cur=`mailcheck | awk '{ print $3 }'`
    if [ $cur -ne $last ]
    then
      notify-send -i "/usr/share/pixmaps/mail-notification.xpm" "New Mail: $cur"
      last=$cur
    fi
  fi
  sleep 30 
done

```

---

### Post by Elric27 on 2010-10-12
Thanks for the script. It set me on track (I know very little) and edited it to get what I want.

```
#!/bin/bash

new_mail=0
last_sum=0 
maildir=" "

while [ : ];
do
  sum_mail=0

  mailcheck  | grep new 2>&1 >/dev/null
  if [ $? -eq 0 ];
  then

    maildir=`mailcheck | grep new | awk '{ print $NF }' \
    | sed 's/\// /g' | awk '{ print $NF }' \
    | awk '{ printf "%s ", $0 }' | sed 's/ /, /g' \
    | sed 's/, $//'`

    new_mail=`mailcheck | grep new | awk '{ print $3 }'`

    for N in `echo $new_mail`
    do
        sum_mail=`expr $sum_mail + $N`
    done

    if [ $sum_mail -ne $last_sum ];
    then
        if [ $sum_mail -eq 1 ] ;
        then
          notify-send -c email.arrived -u normal -i mail_new \
          "You have $sum_mail new mail:" "$maildir"
        else  
          notify-send -c email.arrived -u normal -i mail_new \
          "You have $sum_mail new mails:" "$maildir"
        fi
      last_sum=$sum_mail
    fi
  fi
  sleep 60
done
```

---

