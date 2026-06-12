---
title: "Bash script that email when condition is met, problem with number of mail sent"
date: 2017-11-22
forum: Programming Talk
---

### Post by loonatic22 on 2017-11-22
Hi, 

I have create a simple bash script that check if a file has been updated in the last 10min.

I ran the script trough a cronjob which is running fine, the problem is the number of emails sent once the condition is met. The cron run every 5min.

I need a way to stop the mail process if some emails already been sent this day.

Here is the code that i got so far.

```
#!/bin/bashHOME=/home/gen
LOGNAME=gen
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
LANG=en_US.UTF-8
SHELL=/bin/sh
PWD=/usr/local/gen/icon_voix_core_p/
NOW="$(date) | cut -b 1-10"
LAST="cat /usr/local/gen/icon_voix_core_p/pq_file_date.temp"
if [ "$NOW" != "$LAST" ]; then
        echo "$NOW" > /usr/local/gen/icon_voix_core_p/pq_file_date.temp
fi
clear
cd /usr/local/gen/icon_voix_core_p/ || exit
echo -e "\\e[1;34mList all .pq files\\e[0m"
ls -lh ./*.pq
echo -e "\\e[1;34mLooking for .pq file older then 10min\\e[0m"
find . -maxdepth 1 -type f -mmin +5 -name '*.pq' | while IFS= read -r file; do
    [ -e "${file}" ] && echo "${file} is older than 10 mins" 
if [[ -f ${file} ]]; then
mailx -s "DJ-GTD - Pq File not updating for more than 10min on $HOSTNAME" somemail@mail.com <<EOF
The PQ file: $file need to be checked, possible issues ongoing. Restart of the ICON may be necessary.
EOF
fi
done
```

The following code has been scraped from other project and I'm trying to see if it would work.
```
NOW="$(date) | cut -b 1-10"LAST="cat /usr/local/gen/icon_voix_core_p/pq_file_date.temp"
if [ "$NOW" != "$LAST" ]; then
        echo "$NOW" > /usr/local/gen/icon_voix_core_p/pq_file_date.temp
fi
```

If anyone got some idea on how to make it work, i'm all ears.

Regards

---

### Post by aromo2 on 2017-11-22
```

FILE=/usr/local/gen/icon_voix_core_p/pq_file_date.temp
if [ file is older ]; then
   NOW=$(date +%Y%m%d)
   LAST=$(cat $FILE)
   if [ "$NOW" -ne "$LAST ]; then
      send e-mail
      echo $NOW > $FILE
   fi
fi

```

---

