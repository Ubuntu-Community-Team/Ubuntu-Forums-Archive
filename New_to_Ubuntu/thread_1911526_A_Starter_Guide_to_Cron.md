---
title: "A Starter Guide to Cron"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by trikster_x on 2012-01-19
Let me start this by saying I know there are a lot of other sites with guides about cron usage. However, I find that it is always nice when I can search for a guide on a specific topic here and find one. 

[HERE is the official Ubuntu documentation for cron.]("https://help.ubuntu.com/community/CronHowto")

[SIZE="4"]_[COLOR="Red"]A Little About Cron[/COLOR]_[/SIZE]

Cron is a CLI program that runs in the background and executes commands that are stored in a crontab file. Each user has the ability to create a crontab file, whose jobs will be run regardless of the user being logged in. In addition their is a single "sudo" crontab file that has the ability to run ROOT level jobs without the need for password verification. Once every minute cron wakes up, checks all crontab files and runs any commands that are associated with that time. It can be very useful for running backup scripts or automating your updates.

[SIZE="4"]_[COLOR="Red"]How to Use Cron- Beginners[/COLOR]_[/SIZE]

If you have a task or command you want to run for just your user profile, open a terminal and input the command:

```
crontab -e
```

For tasks or commands that need to be run system wide, use:

```
sudo crontab -e
```

Use the sudo crontab carefully, since it will not need password permission to run admin level commands once the job is created.

If it is your first time using the crontab command, you will be asked which text editor you would like to use. This is purely user discretion, but I prefer nano(option 2).

Once the crontab file is open, you will see some basic introduction text. Some people like to delete it to keep their file nice and neat, but it is not necessary. Any lines in the file that begin with a #(hash mark) are commented out and will be ignored by cron. This can be useful if you have a complicated command that you want to temporarily disable. Simply place a # at the beginning and it will be skipped over until the # is removed.

To input a command(called a [COLOR="Blue"]job[/COLOR] or [COLOR="Blue"]cronjob[/COLOR]) you first have to input a time descriptor, so cron knows when to run the job. The format is fairly simple. The first number represents the minute the job will be run on(0-59). The second number represents the hour in which the job is to be run(0-23, 0=midnight). The third number represents the day of the month the job is to be run on(1-31). The fourth number represents the month the job is to be run in(1-12). The fifth represents the day of the week the job is to be run in(0-6, 0=Sunday). Once you have the time input, then you can input a command to run. This can be virtually anything you can run through a terminal.

Example:

```
12 4 10 9 * /usr/bin/somedir/somecommand
```

This would run somecommand at 4:12 am, every September 10, regardless of the day of the week. The *(asterisk) can be substituted for any number to indicate the job should run on every instance of that time period.

```
12 4 10 * * /usr/bin/somedir/somecommand
```

Replacing the month number with an asterisk indicates that the job will now be run on at 4:12 am, on the 10th day of every month.

[SIZE="4"]_[COLOR="Red"]How to Use Cron- Intermediate[/COLOR]_[/SIZE]

Now what if you want to run a command several times a day or month, but you don't want to have to use multiple jobs? You can separate times with commas(,) or use hyphens(-) to span a period of time:

```
12,42 4 10-20 * * /usr/bin/somedir/somecommand
```

The above example will now run at 4:12 am and 4:42 am, on the 10th through the 20th day of every month.

If you want to run the job a specific specific number of times per time unit, you use a slash(/) on the appropriate time period:

```
*/10 * * * * /usr/bin/somedir/somecommand
```

This entry causes the job to run on all minutes evenly divisible by ten. Cron also offers some special strings:


[LIST=1]
[*]@reboot = Run once, at startup.
[*]@yearly = Run once a year, "0 0 1 1 *".
[*]@annually = (same as @yearly)
[*]@monthly = Run once a month, "0 0 1 * *".
[*]@weekly = Run once a week, "0 0 * * 0".
[*]@daily = Run once a day, "0 0 * * *".
[*]@midnight = (same as @daily)
[*]@hourly =Run once an hour, "0 * * * *".
[/LIST]

[COLOR="Red"][SIZE="4"]_How to Use Cron- Advanced_[/SIZE][/COLOR]

Cron also has the ability to generate a log file and report the stdout and stderr in the log file. Following are examples of how to use this ability and an explanation of what it does.

```
12 4 10 9 * /usr/bin/somedir/somecommand >> /path/to/logfile.log
```

Above will run the command and send the standard output to a logfile. Using two ">" causes the latest job to append the end of the file, without overwriting any previous output that may already be present. If you don't want to save the output from the last time the job ran, simply use one ">".

```
12 4 10 9 * /usr/bin/somedir/somecommand >> /path/to/logfile.log 2>&1
```

This will give you the standard output AND any errors that may have happened when the command ran in the log file. Again, if you wish to have the new information overwrite the old, simply remove one of the ">".

If you wish to run a GUI application through cron, you have a couple options for how to deal with it:

```
XAUTHORITY=~/.Xauthority
DISPLAY=:0.0
```

This is the easiest way to do it if you only plan on running your GUI based jobs on a single screen. Simply copy/paste the two lines above at the beginning of your crontab, before any of the jobs.

```
export DISPLAY=:0.0 && /some/command/here
```

This will run the GUI command on the first screen of the current desktop. To run it on the second screen, you would change it to "DISPLAY=:0.1".

If you have a script you run on multiple systems, but want it to run differently on each system, then use the above method. just plug it into an individual job after the time descriptor. For instance, if you have a script that opens a media player at a specific time, and you have two systems, one with a single monitor and one with dual monitors. You can use this command to have the single monitor setup just run it on the default(:0.0) and modify it to run on the second monitor on you dual setup(:0.1)

Other syntax that is usable in the crontab to specify display, and works the same as above:

```
env DISPLAY=:0.0
```





This wraps up this little guide to cron. If I missed anything, let me know. If you need help getting your cronjobs to work, leave a reply and I will help the best I can. Most importantly have fun utilizing this awesome tool.

---

