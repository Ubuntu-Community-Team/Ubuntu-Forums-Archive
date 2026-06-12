---
title: "how to accomplished to run zenity in cronjob"
date: 2012-04-02
forum: Programming Talk
---

### Post by jao_madn on 2012-04-02
Hi,

I would like to ask some few questions about zenity. I write a script that would generate a report if any changes on the files. i want to used zenity to had a visual alarm report if theres some changes on the comparisons of the file.I used this line of zenity but it doesn't work in cronjob. I terminal windows it works fine(the scripts and the zenity line)

```
cat /home/user/tmp/change_report_file | /usr/bin/zenity --text-info --title="Package Change Report" --width=800 --height=300 > /dev/null 2>&1 &
```

---

### Post by Habitual on 2012-04-02
Make a shell script with these 2 lines:
```

#!/bin/bash
cat /home/user/tmp/change_report_file | /usr/bin/zenity --text-info --title="Package Change Report" --width=800 --height=300

```

save it as say ~/zrpt.sh

Terminal>
```
chmod 700 ~/zrpt.sh
```

Open the crontab editor:
```
crontab -e 
```
and add
```
30 23 * * *  ~/zrpt.sh > /dev/null 2>&1

```
save and exit.
Done.

the 30 23 is 23:30 hours, adjust as necessary.

---

### Post by jao_madn on 2012-04-02
@Habitual: Thanks for a speedy response, but i believe you mis understand me. What im trying to say is not how to schedule the script in the cronjob but how to make it work the zenity program to display or pop-up a dialog window in the display :0.0 which is a problem in zenity when using in crontab but in terminal window its working fine.

I solve or found my solution of my problem in this link "[Running X app in crontab]("http://promberger.info/linux/2009/01/02/running-x-apps-like-zenity-from-crontab-solving-cannot-open-display-problem/")" i add the --display=:0.0 in the zenity which is 
```
cat /home/jao/tmp/zenity | /usr/bin/zenity --text-info --title="Package Change Report" --width=800 --height=300 --display=:0.0
```

or maybe theirs much better solution.

others recommend to add something in the .bashrc since my solution doesn't work to them is enable the scripts to had access to the x session which i didn't try like this one.

add this on ~/.bashrc
```
[[ $DISPLAY ]] && /usr/bin/xhost +localhost
```
in the crontab 
```
* * * * * export DISPLAY='localhost:0.0' bash /script_with_zenity
```

or this "**[zenity and crontab - can't get them work together]("http://ubuntuforums.org/showthread.php?t=1344051")"**

---

