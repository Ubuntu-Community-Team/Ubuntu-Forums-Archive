---
title: "HowTo Change the GNOME Themes Based on Time Of Day"
date: 2006-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by coder_ on 2006-10-13
Changing the GNOME Themes Based on Time Of Day

Do you hate how at night your white Mac theme blinds your eyes? Or how you can't see a thing during the day with your black theme? I recently had a similar problem, and came up with a quick way to fix it. It involves automating the gconf editor and using cron jobs. I came up with this fix to a problem due to the thread with a similar problem located at: [http://ubuntuforums.org/showthread.php?p=1612693](http://ubuntuforums.org/showthread.php?p=1612693).  Unfortunately, I noticed he uses XFCE after I worked out and posted the GNOME solution, so if anyone knows how to automate theme changing for XFCE, give him a little help over there. :)

First we need to see if you have a cron file set up for your user. Type in
```
crontab -l
```
If it says 'no crontab for <user>' (with '<user>' replaced by your username), we need to create a crontab for your user, otherwise continue on to where we edit the file. Change directories to the home directory:
```
cd ~
```
and at the prompt, type:
```

touch .cronjobs
crontab .cronjobs

```
This will make our crontab file be /home/<user>/.cronjobs. This is where we store our cron commands to do commands at certain times. Now, we need to edit it:
```
crontab -e
```
Running that will open up a text editor (Default on Ubuntu is nano, and on SuSE 9.2 is vim, so make sure you know how to use the default text editor it opens.) Now, we need to add cron jobs to our file. Add in:
```
0 6 * * * gconftool-2 --type=string --set /apps/metacity/general/theme 'DayTheme'

0 22 * * * gconftool-2 --type=string --set /apps/metacity/general/theme 'NightTheme'
```
This will make the theme change to "DayTheme" at 6:00 A.M. everyday and change to "NightTheme" at 10:00 P.M. everyday. That's about it for my first published short how-to.  Just make sure to adjust the minutes or whatnot for what you want.  You could also automate wallpaper changing with the seasons (which I originally planned to do) and such like that with this method.

---

