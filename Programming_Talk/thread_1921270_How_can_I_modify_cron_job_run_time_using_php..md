---
title: "How can I modify cron job run time using php."
date: 2012-02-06
forum: Programming Talk
---

### Post by colinmccubbin on 2012-02-06
I have a web cam facing a view which has spectacular sunsets and sunrises. I want to grab a picture, at, say 20 minutes before sunset and 15 mins after after sunrise each day. I can use php/cURL to grab a picture from the camera, give it a name/date/timestamp and save it.

I can use php to get the sunset/rise times for my lat/long into variables, and can write a .txt file in the 'right' format that will overwrite the previous day's file/times with the new ones, but can't work out how (and where) to save the file so that it runs. 

Every 'help' page I read says something like 'compose your cron file using crontab and your favourite editor'. I know that using crontab checks the syntax before saving, but assuming I have the right syntax can I just write my revised file to a specific location and avoid using the crontab/editor route?

My hosting company lets me write files using suphp  if that makes any difference.

Thanks for your help.

---

### Post by r-senior on 2012-02-06
Editing the crontab feels like a bit of a hack, even if it works. Could you use 'at' to schedule these jobs? Maybe have a cron job that runs at midnight and schedules the sunrise/sunset jobs for that day? That's what 'at' is for really - irregular scheduled jobs.

I note you have limited access to the machine and this might not be possible. Just a suggestion.

---

### Post by Lars Noodén on 2012-02-06
+1 for [at](http://manpages.ubuntu.com/manpages/oneiric/en/man1/at.1.html)

---

### Post by colinmccubbin on 2012-02-07
Thanks folks..

I've read the at man page: [http://manpages.ubuntu.com/manpages/oneiric/en/man1/at.1.html]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/at.1.html")

And am not sure how I would use it. I can see that it appears to run a single task at some point in the future, but can't see how to get the data into it from my PHP.

The flow I think is something like this:

1.Schedule daily cronjob which:

2. Runs my php script, which gets the sun up/down times and  adds/deletes  my time offsets to these.

3. Using at, for those times run my php grab a picture script.

I'm lost between 2 and 3, :icon_frown:

Any help on using php to set up an at event would be welcome.

I'm reading the php man page on exec(), which could, I think, be used in a daily crontab job to run the command 'at' with the required times and actions. Thinking and reading about the shared server problems, I have apache set up on my home network, so will try to get it running locally first, and if it works try the external hosted server.

I would still appreciate any advice!

 Thanks,



Thank you

---

### Post by SeijiSensei on 2012-02-07
I run PHP scripts from crontab.  You need to make sure you have installed the **php-cli** package, then create a crontab entry like this:

```
*/10 * * * * /usr/bin/php /path/to/camera_script.php
```

This invokes your script every ten minutes.  The script can then check if the current time is within the window for a sunrise/sunset picture and act accordingly.

---

### Post by r-senior on 2012-02-07
Good, simple solution. =D>

---

### Post by colinmccubbin on 2012-02-07
A quick check shows that I have php5-cli installed, so I will give it a try! Many thanks indeed. :D

Colin

> **SeijiSensei said:**
> I run PHP scripts from crontab.  You need to make sure you have installed the **php-cli** package, then create a crontab entry like this:

```
*/10 * * * * /usr/bin/php /path/to/camera_script.php
```

This invokes your script every ten minutes.  The script can then check if the current time is within the window for a sunrise/sunset picture and act accordingly.

---

