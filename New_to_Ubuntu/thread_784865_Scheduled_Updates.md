---
title: "Scheduled Updates?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by faithsnathan on 2008-05-06
[SIZE=4][FONT=Trebuchet MS]My satellite provider throttles me down to below dial-up speeds if I use too much bandwidth in a given time frame.  They do, it seems, give me "unlimited" bandwidth from 2 - 5am.  Hopefully this is a good idea, but I always install all of the updates in the Update Manager.  I'm using Hardy Ubuntu.  Is there a way to install the updates automatically during a scheduled time?

Thanks in advance!
[/FONT][/SIZE]

---

### Post by dark_harmonics on 2008-05-06
Check this out on using crontab [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

If you schedule it to do a ```
sudo apt-get update && sudo apt-get upgrade -y
``` that should fit your bill :) (caution i never actually did this myself yet).

Edit:
tested that code and it works

---

### Post by nowshining on 2008-05-06
why not just disable auto updates and then checck and install manually?

---

### Post by dark_harmonics on 2008-05-06
> **nowshining said:**
> why not just disable auto updates and then checck and install manually?

Read carefully. He wanted to schedule it.

---

### Post by nowshining on 2008-05-06
i know that, it was a suggestion, and of course it would be better with his lower than dial-up speeds to do it manually than schedualling esp. if he doesn't keep his computer turned on all the time..

---

### Post by nhandler on 2008-05-06
> **dark_harmonics said:**
> Check this out on using crontab [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

If you schedule it to do a ```
sudo apt-get update && sudo apt-get upgrade -y
``` that should fit your bill :) (caution i never actually did this myself yet).

Edit:
tested that code and it works

Why not just use the root crontab. You can edit it by entering "sudo crontab -e" in a terminal. This is just like a normal crontab, except all the commands will be run as root. As a result, there is no need for sudo. This is good because I doubt you want to have to enter your password at 2 am.

---

### Post by faithsnathan on 2008-05-07
> **Cheater said:**
> Why not just use the root crontab. You can edit it by entering "sudo crontab -e" in a terminal. This is just like a normal crontab, except all the commands will be run as root. As a result, there is no need for sudo. This is good because I doubt you want to have to enter your password at 2 am.

[FONT=Trebuchet MS][SIZE=4]Thanks for the suggestions, everyone!  :popcorn:  I've never heard of crontab.  I'll try to figure out what you're saying about this editing in the terminal business when I get home tonight.  I have XP at work, so I can't play around with Ubuntu right now.  
Basically, I get free bandwidth from 2-5am, while the rest of the time I have to keep from using too much.  I have decent speeds usually, I just can't use too much at a time.  So I'm wanting to try out this crontab thing tonight to see if it'll let me schedule backups at that certain time.  

By the way, I didn't know you could do automatic backups in Ubuntu.  I think I'd do that and avoid the hassle if it weren't for the bandwidth issue.  Boy, this is getting long.
[/SIZE][/FONT]

---

### Post by faithsnathan on 2008-05-07
Below, I've included screenshots of how my crontab looks in the terminal.  Hopefully, this is right.  I guess I'll find out in the morning after I get up for work.  

Also, is there a way I can tell it to shutdown after it gets through playing around with the updates, or would that just be asking too much at a time.  :)

The Ubuntu Forums community is full of great people.  Thank you to all of you who've helped me thus far!

---

### Post by faithsnathan on 2008-05-08
Well, I scheduled it to run (I think).  It didn't, that I can tell.  This morning when I got up, I opened Update Manager, and it still has the 55 updates it had last night before I went to bed.  I restarted the computer, just in case it needed that to clear them from the screen or something.  When I opened Update Manager again, still the same thing.  55 available.  :mad:

If one of you wonderful cron users could please look at the screenshots above to see if I typed all that stuff in right?  Why is such a simple thing so complicated?  Put another way, why do I make such a simple thing so complicated?  Thanks.

---

### Post by faithsnathan on 2008-05-08
[FONT=Trebuchet MS][SIZE=4]I guess I'll keep replying to my own thread.  :confused:  Anyway, I've a strike of inspiration (or guesswork), so I'm trying the code a little different.  Below is the code I'll try tonight.  I'll have to wait until tomorrow to see if it works.

```
nathan@mansell-laptop:~$ sudo crontab -l
# 0 2  * * *  sudo apt-get update && sudo apt-get upgrade -y
```
[/SIZE][/FONT]

---

### Post by faithsnathan on 2008-05-09
> [FONT=Trebuchet MS][SIZE=4]I'll have to wait until tomorrow to see if it works.[/SIZE][/FONT]


Well, it didn't work.  Again.  :(

---

### Post by glennric on 2008-05-09
When you do "sudo crontab -l" you are getting
```
# 0 2  * * *  sudo apt-get update && sudo apt-get upgrade -y
```
Note the # at the beginning of the line.  That means the line is remarked out and won't be run.  Type "sudo crontab -e" and remove that.

---

### Post by faithsnathan on 2008-05-09
> **glennric said:**
> When you do "sudo crontab -l" you are getting
```
# 0 2  * * *  sudo apt-get update && sudo apt-get upgrade -y
```Note the # at the beginning of the line.  That means the line is remarked out and won't be run.  Type "sudo crontab -e" and remove that.

[FONT=Book Antiqua][SIZE=4]Thank God someone figured it out!  Well thank you, glenric.  I'll try that this evening.  Here, have some popcorn, on the house.[/SIZE][/FONT]  :popcorn:

[FONT=Book Antiqua][SIZE=4]I guess this could turn into a how-to for anyone who wants to schedule updates (or schedule anything else for that matter).[/SIZE][/FONT]

---

### Post by glennric on 2008-05-09
By the way there is a package called cron-apt specifically designed for this sort of thing.  Install the package and edit the file /etc/cron.d/cron-apt and change the line
```
0 4 * * *	root	test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt
```
to the time you want (so change to 4 to a 2).

---

### Post by glennric on 2008-05-09
With cron-apt there are lots of other options as well.  Edit the file /etc/cron-apt/config (as well as other files in that directory and sub-directory) to change other options.  For instance if you uncomment the lines "# MAILTO=root" and "# MAILON=error" and probably change root to your username you will get mail messages about errors.  If you change "MAILON=error" to "MAILON=always" you will always get a mail message when cron-apt is run.  The file explains its options pretty well, so just look through it.

---

### Post by faithsnathan on 2008-05-09
> Install the package and edit the file

How do you edit a file?

---

### Post by glennric on 2008-05-09
It seems that the program doesn't actually install the upgrades, it just downloads them.  Then you can run "sudo apt-get upgrade" and install them when you want.  If you want cron-apt to automatically download and install, then edit the file /etc/cron-apt/action.d/3-download and remove the -d option on the dist-upgrade line.  You also might want to change dist-upgrade to just upgrade, although I recommend leaving it.   

Note that dist-upgrade does not upgrade to a later release of Ubuntu, contrary what many Ubuntu users seem to believe.  It intelligently handles changing dependencies with new versions of packages (straight from the man page).

---

### Post by glennric on 2008-05-09
Edit a file by typing "gksu gedit filename"

---

### Post by faithsnathan on 2008-05-10
> **glennric said:**
> When you do "sudo crontab -l" you are getting
```
# 0 2  * * *  sudo apt-get update && sudo apt-get upgrade -y
```Note the # at the beginning of the line.  That means the line is remarked out and won't be run.  Type "sudo crontab -e" and remove that.

After taking out the pound sign, I tried it again last night.  IT WORKED!  Thank you to everyone, once again.  Now how can I mark this as solved?

---

### Post by nhandler on 2008-05-15
Glad you got this sorted out. You mentioned earlier that you wanted your computer to shutdown after it finishes installing the updates. There is a command in linux called 'shutdown' that can do just that. The easiest way to use it is by entering 'shutdown now'. That will do just what it says, shutdown the computer now. There are other options you can use with shutdown as well. Read the man page ('man shutdown') to learn about them.

---

