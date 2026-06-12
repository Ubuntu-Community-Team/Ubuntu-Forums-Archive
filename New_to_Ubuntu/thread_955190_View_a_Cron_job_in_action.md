---
title: "View a Cron job in action"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by jesrani on 2008-10-22
I have put some backup jobs in the crontab, to run at scheduled times. However when these run, there is no popup window or any intimation to know that these are running. If I open webmin and then run manually I can see what is going on. Is there any way that I can get a popup window or something when the job is running.

---

### Post by kilroy423 on 2008-10-22
How would you like to be notified of these running(webpage, text file)?

---

### Post by jesrani on 2008-10-22
Webpage would be ok, even a text file is no problem. I just want something to come up showing the progress.

---

### Post by kilroy423 on 2008-10-22
just have your cron do something at the end of the cron to let you know it completed. If you want it to give you status reports then add acouple of these throughout with a number.

echo "I ran" > Desktop/status.txt ; date >> Desktop/status.txt

You can go alot further with this, depending on how much time you want to put into coding it.

---

### Post by jesrani on 2008-10-22
Can you explain a bit more. I am not very good at linux and whatever I have setup is with help from the forums.
I have a .sh file which has the commands to run a backup. This file is run at specific intervals. Should I add some command to the end of this file? Exactly what do I type?

---

### Post by kilroy423 on 2008-10-22
if you were to use the simple one I posted above, just paste it to the bottom of the .sh script.  You will have to edit where you want that file to go.

```
echo "I ran" > Desktop/status.txt ; date >> Desktop/status.txt
```

This will created a text file on the Desktop with the date and I ran.  You will have to change the path to something like /home/USER/Desktop/status.txt . (replace USER with your username)

---

### Post by jesrani on 2008-10-22
Hello. I did as instructed but this was not exactly what I had in mind. My .sh file has commands to copy some files from a particular folder to another HDD. When I open Webmin and run the scheduled task I see the actual job being done, some files being copied and some being deleted. But this is when I do it manually. The job is scheduled to run automatically at a certain time of the day and it does too (I can see the updated files) but I cannot see it as it is happening. This is what I want. Sorry if I was not clear initially. Hope I am now.

---

### Post by MrWES on 2008-10-22
> **jesrani said:**
> I have put some backup jobs in the crontab, to run at scheduled times. However when these run, there is no popup window or any intimation to know that these are running. If I open webmin and then run manually I can see what is going on. Is there any way that I can get a popup window or something when the job is running.

I use this little popup tool to notify me of scheduled shutdowns. You could put this to run say five minutes before your backup:

```
/usr/bin/zenity --display :0 --warning --text="Backup Running in 5 minutes. Please close all files"
```

Pretty neat stuff.

Bill

---

### Post by jesrani on 2008-10-22
> **MrWES said:**
> I use this little popup tool to notify me of scheduled shutdowns. You could put this to run say five minutes before your backup:
Bill

Thanks but this is a separate message window I assume. I want to see what is going on in my scheduled job. I want to see the tasks being done.

---

### Post by wizard10000 on 2008-10-22
> **jesrani said:**
> Thanks but this is a separate message window I assume. I want to see what is going on in my scheduled job. I want to see the tasks being done.

Then put this in your crontab -

gnome-terminal -x /path/to/script.sh

---

### Post by kilroy423 on 2008-10-23
> Thanks but this is a separate message window I assume. I want to see what is going on in my scheduled job. I want to see the tasks being done.

Ok..easy enough.  Add zenity to your cron, I would pipe your script into zenity

```
YOUR SCRIPT | zenity --progress
```

Now edit your script as follows:

```
echo "10"
echo "#" "10"
sleep 2
echo "25"
echo "#" "25"
sleep 5
echo "75"
echo "#" "75"
sleep 2

```

any lines beginning with a # will echo out a statement to the progress bar(you can make it say what you want!).  Any lines beginning with a number will fill the progress bar.  Before you put this into your script I would play around with what I pasted above, just dump it into a test script and have fun!

---

### Post by jesrani on 2008-11-12
> **wizard10000 said:**
> Then put this in your crontab -

gnome-terminal -x /path/to/script.sh

Hello. I am responding after long time to this question. When I enter this command in cron I get an error. Gnome terminal dies not open.
I searched on net and found this command works for me:
export DISPLAY=:0 && gnome-terminal -x /path/to/script.sh.

It did exactly what I wanted, opened a terminal window and ran the scrip. Now the problem is that the terminal window closes after the script is finished. Any way of keeping it on so that I can check out the actions and then close the terminal?

---

