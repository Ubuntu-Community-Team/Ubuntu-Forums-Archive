---
title: "Getting rsync to work with cron"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by rgfrancis on 2013-08-22
Trying to build a very simple file server. As I learn the basics I will fancy it up a little more. So this is what I have done.

I created a folder: /ppp [COLOR="#008000"]<-- Works[/COLOR]
I changed the permissions on the folder to 0777 [COLOR="#008000"]<---Works[/COLOR]
I run the following line in terminal: rsync -r -v -z -t /ppp *<my username>*@*<my ip>*::ibackup [COLOR="#008000"]<--- Works. THIS CREATES A BACKUP[/COLOR]
I created a shell script called daily.sh in the /ibackup folder with a single line: rsync -r -v -z -t /ppp *<my username>*@*<my ip>*::ibackup [COLOR="#008000"]<--- Works[/COLOR]
While in the /ibackup folder I run: sudo ./daily.sh [COLOR="#008000"]<--- Works. THIS CREATES A BACKUP[/COLOR]

This is where things start to not work.

I edit /etc/crontab and add the following line:
15 10   * * * /ibackup/daily.sh

I check /var/log/syslog and I see this line:
Aug 22 10:15:01 unbuntu cron[839]: (*system*) RELOAD (/etc/crontab) [COLOR="#FF0000"]<-- NOTHING BACKUP UP[/COLOR]

So then I edit /etc/crontab and add the following line (adding . before /ibackup):
29 10   * * * ./ibackup/daily.sh 

I check /var/log/syslog and I see this line:
Aug 22 10:29:01 unbuntu CRON[24599]: (root) CMD (    ./ibackup/daily.sh)
Aug 22 10:29:01 unbuntu CRON[24599]: (CRON) info (No MTA installed, discarding output) [COLOR="#FF0000"]<-- NOTHING BACKUP UP[/COLOR]

So then I edit /etc/crontab and add the following line:
43 10   * * * ./ibackup/daily.sh >/dev/null 2>&1

I check /var/log/syslog and I see this line:
Aug 22 10:29:01 unbuntu CRON[24610]: (root) CMD (    ./ibackup/daily.sh >/dev/null 2>&1) [COLOR="#FF0000"]<-- NOTHING BACKUP UP[/COLOR]

So then I edit /etc/crontab and add the following line (removing space between sh and >/dev):
43 10 * * * ./ibackup/daily.sh>/dev/null 2>&1

I check /var/log/syslog and I see this line:
Aug 22 10:29:01 unbuntu CRON[24610]: (root) CMD ( ./ibackup/daily.sh>/dev/null 2>&1) [COLOR="#FF0000"]<-- NOTHING BACKUP UP[/COLOR]

Not sure what to do at this point.

Thanks in advance for any help.

---

### Post by Cheesemill on 2013-08-22
Edit your /ibackup/daily.sh script so it looks like this...
```
#!/bin/sh
/usr/bin/rsync -r -v -z -t /ppp <my username>@<my ip>::ibackup
```

Then change your crontab back to your first attempt...
```
15 10 * * * /ibackup/daily.sh
```

You need the shebang  (#!) line at the start of your script to specify what sort of script it is (in this case it's a shell script).

Also crontab doesn't have the same environment set up as a normal user so it might not know where rsync is, so use the full path.

---

### Post by rgfrancis on 2013-08-22
I made the changes and checked /var/log/syslog and I see this:
Aug 22 12:35:01 unbuntu cron[839]: (*system*) RELOAD (/etc/crontab)
Aug 22 12:35:01 unbuntu CRON[24670]: (root) CMD (    /ibackup/daily.sh)
Aug 22 12:35:12 unbuntu CRON[24669]: (CRON) info (No MTA installed, discarding output) <-- NOTHING BACKUP UP

---

### Post by ian-weisser on 2013-08-22
Cron is working. There is a problem in your script.

The "No MTA installed" line means that your job has output -like the error message-, and cron tried to e-mail you that output. Since you don't have an MTA installed to handle the e-mail from cron, the system discards the undeliverable mail.

You don't need -v (verbose flag) in a cron job unless you are saving the output to a file, or getting it mailed to you.

If you are backing up to another machine, make sure the cron environment (which is different from your login environment) has access to the appropriate ssh key.

You can install an MTA to read the error messages. That's handy for servers. It stinks when you go through the trouble of installing an MTA, configuring cron to send to the right e-mail address...and then the message isn't helpful.

For troubleshooting, I recommend redirecting your script output to a file instead of STDOUT or STDERR. You can do this through cron, or simply put in debugging lines within your script.

---

### Post by rgfrancis on 2013-08-22
If I type this line into terminal it works:

/usr/bin/rsync -r -v -z -t /ppp <my username>@<my ip>::ibackup

The files get backed up to ibackup everytime. **It works perfect.**

My script is called daily.sh and looks like this:
#!/bin/sh
/usr/bin/rsync -r -v -z -t /ppp <my username>@<my ip>::ibackup

If I manually run this script the files get backed up to ibackup everytime. **It works perfect.** All I want to do to automate the process. 

I have added the script to /etc/cron.hourly. It does not backup.

I have added the following line to /etc/crontab:

15 10 * * * /ibackup/daily.sh

It does not backup. 

Summerize:
Type line in terminal = works
Manually run script = works
Add to cron = no worky

---

### Post by SeijiSensei on 2013-08-22
Take a look in /var/log/syslog and see what errors cron reports.

---

### Post by papibe on 2013-08-22
Hi rgfrancis.

A few thoughts:[LIST]
[*]Call your script from cron using an absolute path, for instance, /home/youruser/ibackup/daily.sh (if it's in your home).
[*]Also use absolute paths for your source and destination on your script.
[*]Instead of using the verbose option and redirecting rsync output, use the --log-file option instead, e.g.:```
rsync -a --log-file=/path/to/rsync.log /path/to/source/  /path/to/destination/
```
[*]Note that if nothing changes, subsequents runs of rsync would do, well, nothing (because there's nothing to sync).
[*]If you need to run 'sudo rsync...' in order for the script to run properly, then you need to create a crontab entry for **root** by running:```
sudo crontab -e
```
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by rgfrancis on 2013-08-22
I restarted the cron daemon

I added the following to the end of my line in crontab:

/ibackup/cron.log 2>&1

I then reviewed the log and got this:

Password: rsync: connection unexpectedly closed (o bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) as io.c(605) [sender=3.0.9]

---

### Post by rgfrancis on 2013-08-22
Confused about the crontab -e. If I type that in terminal it brings up a /tmp/crontab.03oj7y/crontab and doesn't have any of the modifications I have made to the /etc/crontab. How does that work?

I am running the script using the absolute path. It is located in a folder called ibackup in the root. Am I missing something there?

Thanks

---

### Post by papibe on 2013-08-22
> **rgfrancis said:**
> I run the following line in terminal: rsync -r -v -z -t /ppp *<my username>*@*<my ip>*::ibackup
In this example, the directory ibackup is not referenced using an absolute path. Is that the current command on your script?
> **rgfrancis said:**
> Confused about the crontab -e
If all this time you were editing /etc/crontab then you are missing the user field. Having said that, I would leave /etc/crontab 'as is' and creating a separate user crontabs. That could be personal user crontab by running:
```
crontab -e
```
or for root by running:
```
sudo crontab -e
```
Regards.

---

### Post by rgfrancis on 2013-08-22
if I use sudo crontab -e and add my line do I save it as /tmp/crontab.03oj7y or do I rename it? If so where do I put it?

---

### Post by papibe on 2013-08-22
Leave it as it is.

Check if was save OK by running:
```
sudo crontab -l
```
Regards.

---

### Post by rgfrancis on 2013-08-22
The save is ok. 

The current line I have entered in sudo crontab -e is:

15 53 * * * /ibackup/daily.sh >/ibackup/cron.log 2>&1

Once again no backup. The cron.log file says this:

Password: rsync: connection unexpectedly closed (o bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) as io.c(605) [sender=3.0.9]

---

### Post by rgfrancis on 2013-08-22
This was asked of me on another rforum:

Another possibility: Could it be that the "ibackup" module on the remote machine requires entering a password and that you have set the variable  RSYNC_PASSWORD in your login shell?

If so, please be aware that cron does not set up your standard environment, so this variable will certainly be unset when the script runs from cron.

Does anyone have any idea what they are saying? Does this help anyone?

---

### Post by Cheesemill on 2013-08-22
How have you set up the password for your rsync command?

When you run the command from a terminal do you have to type in a password or have you set up key-based authentication?

---

### Post by papibe on 2013-08-22
Could you post the content of your /etc/rsyncd.conf file?

Also, have you tried anonymous sync? That is omitting the username, something like:
```
rsync -r -v -z -t /ppp  <my ip>::/ibackup
```
Regards.

---

### Post by rgfrancis on 2013-08-22
I now have a solution from another forum. It is posted below for everyone to see. Thanks

________________________________________________________________________________________________

OK,

it's neither possible for commands/scripts started by cron to ask you anything, nor is it possible for those commands/scripts to get an answer.

Reason: the command shell started by cron to run the command/script inside does not have an associated terminal to display the password prompt or to accept an answer.

So you must provide the password by other means.

1.) You could add

export RSYNC_PASSWORD=password

to the script daily.sh, in a line of its own just below "'!/bin/sh", like

#!/bin/sh
export RSYNC_PASSWORD=password
/usr/bin/rsync -r -v -z -t /ppp <my username>@<my ip>::ibackup

This is obviously insecure, because the password appears in clear text in the script, and everybody who can read the script can read the password.

2) Add "--password-file=/path/to/password_file" to the rsync options, like

/usr/bin/rsync -r -v -z -t --password-file=/path/to/password_file /ppp <my username>@<my ip>::ibackup

and create the file /path/to/password_file. It should contain just the password as a single line. Make the file owned by the user who starts the script, and make it read/writeable only by that user, e.g.

chown myuser /path/to/password_file
chmod 600 /path/to/password_file

---

### Post by SeijiSensei on 2013-08-23
Papibe's suggestion would also work, but you must be running rsync in "[daemon mode]("http://linux.die.net/man/5/rsyncd.conf")" on the remote machine.

---

### Post by LHammonds on 2013-08-29
I include a path in my crontab schedule which tends to fix any forgotten FQ paths.  [Example here]("http://ubuntuforums.org/showthread.php?t=2167224&p=12764339#post12764339").  If interested in how I setup servers, check my sig for more examples.

[B]EDIT: Sorry, didn't see the 2nd page.
[/B]
I handle my crontab schedule a bit differently.  I have my crontab schedule saved in a file, which then gets backed up and archived.  Whenever I make a change to my schedule, I make it to the file and then run crontab to load that file for the specific user (root in my case).  I've had issues in the past and have lost my schedule due to fat-fingering the crontab command so I like modifying it in the safest way possible.

Example, schedule file located @ **/var/data/crontab.root**

Here are the steps I typically do to change a schedule:

```

cp /var/data/crontab.root /var/data/2013-08-17-crontab.root.bak
vi /var/data/crontab.root   (* make my changes, save and exit *)
crontab -u root /var/data/crontab.root

```

---

