---
title: "bash script help"
date: 2008-07-11
forum: Programming Talk
---

### Post by maerlma on 2008-07-11
I can't get this script to work, does anyone see what I'm doing wrong?

# Find which week of the month 1-4 it is.
day_num=$(date +%d)
if [ $day_num < 08 ]; then
        week_file="$hostname-week1.tgz"
elif [ $day_num > 07 && $day_num < 15 ]; then
        week_file="$hostname-week2.tgz"
elif [ $day_num > 14 && $day_num < 22 ]; then
        week_file="$hostname-week3.tgz"
elif [ $day_num > 21 && $day_num < 32 ]; then
        week_file="$hostname-week4.tgz"
fi

echo "Backing up $backup_files to $dest/$archive_file"
date
echo
echo "$week_file"
echo
echo "$month_file"
echo
echo "$day_num"


$week_file never gets populated. help!

---

### Post by ghostdog74 on 2008-07-11
```

cal|tail +3|egrep -n -o $(date +%d)|cut -d":" -f1

```

---

