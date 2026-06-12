---
title: "Is this formatting correct for a crontab every first friday?"
date: 2018-05-15
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2018-05-15
Script being called. Have a couple acres with a few houses here. My server is the primary dns dhcp for the lan. Hence I need to notify when going down for any reason.

```
if [[ $(date +%d) -le 7 ]] ; then              
for email in $REBOOTNOTIFICATIONEMAIL ; do
  echo "To: ${email}
From: ${EMERGENCYEMAIL}
Subject: scheduled server upgrade & reboot


the server will recieve software upgrades and a reboot tonight around 10pm. internet connectivity may be on / off. expected downtime is 5-10 minutes." > /tmp/"$email".lock
    ssmtp "$email" < /tmp/"$email".lock
    rm /tmp/"$email".lock
  done
  echo "To: ${EMERGENCYEMAIL}
From: ${EMERGENCYEMAIL}
Subject: upgrade and reboot server tonight!

first friday night of the month run full-upgrade & reboot server" > /tmp/upgradeemail
  ssmtp "$EMERGENCYEMAIL" < /tmp/upgradeemail
  rm /tmp/upgradeemail
fi
```

Crontab entry

```
00 2 * * 5      /usr/local/bin/rebootnotice
```

Is this correct, both the $(date +%d) -le 7 and the crontab entry to get it to run first friday of the month?

---

### Post by yancek on 2018-05-15
Check the last post at the link below which appears to have exactly what you are looking for.

[https://www.linuxquestions.org/questions/linux-general-1/cronjob-to-run-a-command-at-first-friday-of-each-month-4175432886/](https://www.linuxquestions.org/questions/linux-general-1/cronjob-to-run-a-command-at-first-friday-of-each-month-4175432886/)

---

### Post by Tadaen_Sylvermane on 2018-05-15
seems to confirm I'm good to go. will know when / if I get the email in 2 or 3 weeks i guess. thank you for the link.

---

