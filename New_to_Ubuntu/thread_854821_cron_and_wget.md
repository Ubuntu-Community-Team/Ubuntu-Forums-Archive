---
title: "cron and wget"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by anabi on 2008-07-09
Hi,

I am using wget to download files. I want to be able to use cron to schedule these downloads. I've had a look at the cron manual but am still unsure exactly how to use cron. Can someone please give me an example, or a step by step on how to use cron and wget.

Thank you

---

### Post by llamakc on 2008-07-09
If you'd like an exact answer provide an example of the manner in which you use wget. 

Mostly you will edit your crontab with the command

```

crontab -e

```

and place something akin to 

```

* * * * *  /usr/bin/wget (ANY wget OPTIONS) "http://name.of/address/" </dev/null 2>&1

```

There are many options and variables so we'd need more information.

---

### Post by anabi on 2008-07-09
Thanks for your reply. To be exact I use wget with the following comman line

```

wget --username=<username> --password=<password> -i <filename>

```

And I wanted to schedule these downloads between 3-9am as my ISP allows me additional downloads during this period. How would I go about this?

---

### Post by llamakc on 2008-07-09
Type:

```

crontab -e

```Enter:

```

30 4 * * * /usr/bin/wget --username=<username> --password=<password> -i <filename> "http://path/to/site" 
>/dev/null 2>&1
```

will run the command at 4:30 AM

To be honest I've always found it easier to create a bash script and just run that from cron. I seem to avoid errors that way.

---

### Post by anabi on 2008-07-09
Thanks once again for your reply. I was hoping you could explain that command to me further. ```
 30 4 * * * 
``` sets the start time? ```
 /usr/bin/wget --username=<username> --password=<password> -i <filename> "http://path/to/site" 
``` is the command line to execute. what is ```
 >dev/null 2>&1 
``` ? also is it possible to enter an end time? 

edit: also once i've put that all into the crontab and saved it. Will it run automatically from there?
When trying to save the above crontab i get a "bad minute" error.

---

### Post by llamakc on 2008-07-09
Yes the

30 4 * * *

sets the start time, so you can change it. The hours (the second field) use a 24 hour clock.

> 
To prevent the sending of errors and output, add any one of the following at the end of the line for each cron job to redirect output to /dev/null.
[B]
>/dev/null 2>&1[/B]
OR
**&> /dev/null**


And I do not know how to tell it to stop in this fashion. One could wrap the wget stuff in a script and run THAT from cron, and then set a second cron to kill that script. There maybe an easier way though.

If you put the entire wget line in a script like

```

#!/bin/sh
wget ...blah blah blah

```

and saved the script as wget-cron.sh (or any name) you could run that from cron with:

```

30 4 * * * /path/to/wget-cron.sh >/dev/null 2>&1

```

and have a second script named kill-wget-cron.sh with the contents of:

```

#!/bin/sh
killall wgeet-cron.sh

```

and choose which time to run THAT:

```

30 5 * * * /path/to/kill-wget-cron.sh >/dev/null 2>&1

```

Anyway, that's it roughly in theory at least. All of the details would have to be massaged and I probably forgot something. The point is that scripts can be started from cron also.

BASH if feature-rich and I'm sure if you asked a question about 'how do I run a script from time X until time Y' somebody would have a much more correct and elegant answer.

Plus I'm drunk.

---

### Post by llamakc on 2008-07-09
It very well may be easier to just `apt-get install gnome-schedule` also.

---

### Post by anabi on 2008-07-10
okay well thanks for all your help. But I keep getting a "bad minute" error when the crontab is installing.

```

30 4 * * *  wget --username=<username> --password=<password> http://website.com

```

Anyone know why?

Thanks!

---

### Post by llamakc on 2008-07-10
> **anabi said:**
> okay well thanks for all your help. But I keep getting a "bad minute" error when the crontab is installing.

```

30 4 * * *  wget --username=<username> --password=<password> http://website.com

```Anyone know why?

Thanks!

Are you certain there is not a blank space before the "30"?

---

### Post by anabi on 2008-07-10
I just checked, no blank space =(

---

### Post by llamakc on 2008-07-10
Are you using the redirect part? My > should be a >>.

```

30 4 * * * /usr/bin/wget --username=<username> --password=<password> -i <filename> "http://path/to/site" 
**>>**/dev/null 2>&1
```

I use the "30 4 * * *" for other scripts and it works perfectly. If you share your actual crontab it may be easier to troubleshoot.

You can type:

```

crontab -l

```and post that here.

---

### Post by anabi on 2008-07-10
crontab -l doesnt work because the tab doesnt get install. I've tried doing it with the script files like you explained. And it installs. But when it doesnt run anything when the time comes. Here is what my crontab ```
01 15 * * * wget-cron.sh >>/dev/null 2>&1 
```

My script file is saved in my home directory ```
#!/bin/sh
wget --username=4611 --password=5THAFm http://rapidshare.com/files/113054451/backup624.part10.rar
```

So all this installs. But when the time comes, nothing happens. Does this help?

---

### Post by llamakc on 2008-07-10
> **anabi said:**
> crontab -l doesnt work because the tab doesnt get install. I've tried doing it with the script files like you explained. And it installs. But when it doesnt run anything when the time comes. Here is what my crontab ```
01 15 * * * wget-cron.sh >>/dev/null 2>&1 
```My script file is saved in my home directory ```
#!/bin/sh
wget --username=4611 --password=5THAFm http://rapidshare.com/files/113054451/backup624.part10.rar
```So all this installs. But when the time comes, nothing happens. Does this help?

01 15 means 3:01 in the afternoon, and your syntax is wrong. You didn't adhere to what I suggested.

There are plenty of resources on the net for the syntax of cron.

If you want it to run at 1:15 AM, you'd put 

15 1 * * *

---

### Post by anabi on 2008-07-10
oh i was trying to run it at 3:01 pm. Its 3:30 pm here in sydney and at the time i wrote that it was just before 3:01pm so i wanted to see if it worked properly. What is wrong with my syntax?

---

### Post by kpkeerthi on 2008-07-10
First make sure the wget-cron.sh is executable
```
chmod u+x wget-cron.sh
```

Next, any reference to a file in crontab should be fully qualified, like so
```

01 15 * * * /home/<put-your-user-id-here>/wget-cron.sh > /dev/null 2>&1

```

* Also note that redirect to /dev/null can be as simple as >

---

