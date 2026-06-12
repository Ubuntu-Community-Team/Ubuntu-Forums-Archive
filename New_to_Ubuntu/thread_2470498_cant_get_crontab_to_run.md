---
title: "cant get crontab to run"
date: 2022-01-01
forum: New to Ubuntu
---

### Post by rburkartjo on 2022-01-01
using 20.04
first/home/ray/suspend
20 7 * * * /home/ray/suspend
56 7 * * * /home/ray/rem

of course i just run /home/ray/suspend or ./suspend as example in terminal and they run fine

however cant get them to run as crontab jobs
i tried this

/sbin/service cron start
no help
sure i am over looking something
tks

---

### Post by rburkartjo on 2022-01-01
also tried this

ray@ray-HP-ProBook-640-G1:~$ sudo chkconfig crond on
[sudo] password for ray: 
sudo: chkconfig: command not found
ray@ray-HP-ProBook-640-G1:~$ sudo systemctl enable crond
Failed to enable unit: Unit file crond.service does not exist.
ray@ray-HP-ProBook-640-G1:~$ 


tks

---

### Post by schragge on 2022-01-01
> **rburkartjo said:**
> 
ray@ray-HP-ProBook-640-G1:~$ sudo systemctl enable crond
Failed to enable unit: Unit file crond.service does not exist.

It's **cron**, not **crond**.
```
sudo systemctl enable cron.service
```

Bear in mind that a cronjob is executed by **/bin/sh** which in Ubuntu is **dash**. OTOH, when you're running it manually, you're doing so in your login shell (most probably **bash**).

> **rburkartjo said:**
> first/home/ray/suspend
What does this line mean? If this is a part of the cronjob, it is wrong.

---

### Post by rburkartjo on 2022-01-01
sch tks
but ran and still not working

---

### Post by rburkartjo on 2022-01-01
script i am using that works in terminal
#!/bin/bash
systemctl suspend

./suspend
just cant run anything in cron

---

### Post by TheFu on 2022-01-01
cron scripts don't inherit the same environment that interactive sessions get. They don't have the same PATH and most other environment variables are different.  

Whenever scripting, always, always, use the full-path-to-every command and never assume any environment variable is setup. There is no PWD either. For example, HOME might not be set in some implementations of cron.  USER may not be set. The pwd/cwd will NOT be $HOME, since $HOME might not be set.

Look through the script carefully. Which commands assume a PATH or a directory or location of files relative to something not setup?

Oh ... and don't attempt to use any programs with a GUI. They won't work.

Lastly, there are multiple different locations for crontab files.  They have different formats.  /etc/crontab isn't the same format as used with **crontab -e** created files.  For most end users, system-wide cron files really should just be scripts placed into one of the periodic run directories like cron.daily/   cron.hourly/  cron.monthly/       cron.weekly/ in the /etc/ directory.  Those locations run normal scripts, as root, at least once per period. The running of those scripts is controlled by anacron, which isn't a exact as regular cron, but for many needs, more than sufficient time resolution.  Daily backups should happen er ... once daily, no more. Anacron does that.

The example script of 
```
#!/bin/bash
systemctl suspend
```
assumes a few things that aren't valid.
1) the path is set
2) the userid running has root permissions

The correct setup would be
```
#!/bin/bash
/usr/sbin/pm-suspend
```
Further, I'd both the script into /root/bin/ ... this will prevent any non-root (or non-sudo using) users from even accessing it. No need to check the current userid ... though you could with **id -u** .... more correctly in a script it would be **/usr/bin/id -u**, then compare the result to "0", which is the userid of root. If non-zero, print an error and exit.

Hope this has helped.  More crontab tips: [https://blog.jdpfu.com/2010/06/05/5-cron-tips](https://blog.jdpfu.com/2010/06/05/5-cron-tips)
More scripting tips: [https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

---

### Post by KBar on 2022-01-01
On the topic of cron. How exactly does anacron run delayed jobs on next power up? Could you explain that in a few words or point a link, TheFu? Much appreciated!

---

### Post by TheFu on 2022-01-01
> **kbar said:**
> On the topic of cron. How exactly does anacron run delayed jobs on next power up? Could you explain that in a few words or point a link, TheFu? Much appreciated!

I don't use anacron.  I'm a control freak and want tasks to start at the specific minute I've setup, not "sometime today" which is actually all that anacron time resolution supports.  I think the @reboot time spec alias for crontabs is not anacron, but cron.  There isn't any @shutdown option, to my knowledge for either.  If someone wanted to know, they can check the manpage for crontab/anacron and follow some of the "see also" parts near the end of each manpage.  As a programmer, I know how I would implement anacron and that is probably how they did it, but without looking at the code itself, I wouldn't really know.

There are a number of different implementations of cron, each with some slight differences.  For example, the Ubuntu installed version doesn't support disabling sending emails as a global option, while I've seen that the RHEL selected version does. I haven't looked at the new Ubuntu packages, so perhaps that control is possible now? IDK.

---

### Post by rburkartjo on 2022-01-01
fu tks for your help
you have given me good advise over the years
really lost on this. i have run up to 15 scripts on ubuntu without any problems.
now cant run any cron job.

fyi this doest work get message does not exist
#!/bin/bash
/usr/sbin/pm-suspend

replaced by
#!/bin/bash
/usr/bin/systemctl-suspend

which i also cant get to run in cron
tks

---

### Post by KBar on 2022-01-01
The binary is */usr/bin/systemctl* and the argument for it would be _suspend_, so it's like this:
```
/usr/bin/systemctl suspend
```

**pm-suspend** is provided by the *pm-utils* package and is not available on a default Ubuntu system, which is based on systemd.

Have a look at the scripts in *cron.{hourly,daily,weekly,monthly}* directories. They will give you a clue how **cron** works. How often do you want your computer be suspended? Every hour? Once a week? Or upon conclusion/commencement of another process?

---

### Post by TheFu on 2022-01-01
> **kbar said:**
> The binary is */usr/bin/systemctl* and the argument for it would be _suspend_, so it's like this:
```
/usr/bin/systemctl suspend
```

**pm-suspend** is provided by the *pm-utils* package and is not available on a default Ubuntu system, which is based on systemd.

Have a look at the scripts in *cron.{hourly,daily,weekly,monthly}* directories. They will give you a clue how **cron** works. How often do you want your computer be suspended? Every hour? Once a week? Or upon conclusion/commencement of another process?

My laptop is the only system here with a known working "suspend", so I checked exactly how I do it.  After my nightly backups, I delay a few seconds and use exactly the command shown.  That laptop install was upgraded from 10.04, so there will be cruft left over.  My fresh install 20.04 desktop is a VM and both doesn't have the pm-suspend command AND I've never suspended it. Sorry for the confusion. I like to post things that I actually use and know to be working, but my systems are sometimes a little different from normal.  That's my story and I sticking to it. ;)

Whenever the error is "command not found", that means one of the following:
* the command isn't on the system - i.e. a package isn't installed.
* a typo for the command name happened.  Computers are dumb. They can only do exactly what we ask, not what we mean.
* there is some difference in where commands are being placed.  Ubuntu has been moving long-time commands to /usr/bin/ to other directories in recent releases. If you aren't running 20.04 (the current LTS), it is very helpful to mention the exact release being used. We might not notice it, but it can be very important, since things are always changing from release to release to release.

An example of a command moving locations is systemctl. 
18.04:  /bin/systemctl
20.04: /usr/bin/systemctl
I have to wonder where it is on 21.10?  Ok, not really. Just use 'which' to find commands in the PATH.

---

### Post by KBar on 2022-01-02
> **TheFu said:**
> I have to wonder where it is on 21.10?  Ok, not really. Just use 'which' to find commands in the PATH.
 
I don't think the merged-usr layout is changing any time soon. For more, read here: [https://wiki.debian.org/UsrMerge](https://wiki.debian.org/UsrMerge)

---

### Post by TheFu on 2022-01-02
> **KBar said:**
> I don't think the merged-usr layout is changing any time soon. For more, read here: [https://wiki.debian.org/UsrMerge](https://wiki.debian.org/UsrMerge)

Seems they are trying to kill NFS, just a little more every day.  Sigh.

---

### Post by schragge on 2022-01-02
> **TheFu said:**
> Seems they are trying to kill NFS, just a little more every day.  Sigh.
[quote=Debian wiki]But /etc and /var can still do [get out of sync -- schragge], and this optimizes for admins that might  know what they are doing instead of end users that might not, due to  the unreliability introduced.[/quote][;)]("https://wiki.debian.org/Teams/Dpkg/MergedUsr#Properties")

Anyway, that quote is only of academic interest now as Debian decided to go with the first approach (merged-/usr-via-aliased-dirs).

---

### Post by rburkartjo on 2022-01-02
i even downloaded zeit
[https://www.tecmint.com/zeit-gui-tool-to-cron-jobs-in-linux/](https://www.tecmint.com/zeit-gui-tool-to-cron-jobs-in-linux/)
  
and used it to schedule a job
it accepts my job but cron wont run it
wonder if i have to reset someyhing in my system

---

### Post by rburkartjo on 2022-01-02
if the problem is somewhere in the system would upgrading to 21.10 help? then in april i would up grade t0 22.04

---

### Post by KBar on 2022-01-02
Could you elaborate a bit on what exactly you want to achieve? How often do you want it to suspend? See post #10.

---

### Post by rburkartjo on 2022-01-02
kb at this point really dont care about running a suspend job per say. i just cant get any cron job to run period and had no problem when running 20.04. however my puter died and when replaced downloaded 20.04.3 and thats when started having problems. not a master but been running scripts for years. tks

---

### Post by TheFu on 2022-01-02
Does this not work?
```
#!/bin/bash
/usr/bin/systemctl     suspend
```

It will need to be run from root's crontab or a system crontab.

Did you follow the links that I posted to crontab issues and scripting 101 stuff?  That's my personal blog.

If your userid cannot run scripts from cron anymore, I'd check to see if the default cron "allowed" users has changed in the distro you are running.  I haven't noticed anything in 20.04 and use cron jobs all the time.  You could create a new userid to see if a cron job runs under that userid. This could show some issue with your normal userid.

---

### Post by rburkartjo on 2022-01-02
output

ray@ray-HP-ProBook-640-G1:~$ cat /etc/cron.d/cron.allow
cat: /etc/cron.d/cron.allow: No such file or directory
ray@ray-HP-ProBook-640-G1:~$

---

### Post by rburkartjo on 2022-01-02
and i am an admin user

ray@ray-HP-ProBook-640-G1:~$ !1042
groups ray
ray : ray adm cdrom sudo dip plugdev crontab lpadmin lxd sambashare
ray@ray-HP-ProBook-640-G1:~$

---

### Post by TheFu on 2022-01-02
> **rburkartjo said:**
> output

ray@ray-HP-ProBook-640-G1:~$ cat /etc/cron.d/cron.allow
cat: /etc/cron.d/cron.allow: No such file or directory
ray@ray-HP-ProBook-640-G1:~$

a) please use 'code tags'. Makes the terminal stuff jump out.  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)
b) what about the cron.deny?

[https://help.ubuntu.com/community/CronHowto#Allowing.2FDenying_User-Level_Cron](https://help.ubuntu.com/community/CronHowto#Allowing.2FDenying_User-Level_Cron)  <-- that is from 2016, so I'm guessing nothing has really changed.  The issue will be something local that you forgot or didn't know or overlooked. We all have blinders from time to time.

If you can show all the files, permissions, and crontab entry, someone else should see it.   Please use 'code tags' when posting anything in the terminal - show the full command, all the options, and the results, which you did above. [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) Thanks.

---

### Post by rburkartjo on 2022-01-02
and that doesnt exist either

---

### Post by TheFu on 2022-01-03
> **rburkartjo said:**
> and i am an admin user

That doesn't matter (good or bad) for cron.  The system doesn't know or care. Normal, Unix, file permissions control access 100% to files.  There is nothing special about the first userid installed onto a system if the uid does not equal 0.  Only the sudo program cares (assuming default settings for the wheel group [or sudo group on Ubuntu]), but everything else is just normal users, groups and file permissions. Nothing magical.

---

### Post by rburkartjo on 2022-01-03
fu if your up to this 
lets give this a try

here is a script that i have in my home folder

#!/bin/bash
/usr/bin/vlc


path in crontab
/home/ray/vlc

and i cant get it to run in crontab

can you try entering the same in your home folder and see if you can get to run

i am doing something wrong but cant figure it out
tks again

---

### Post by schragge on 2022-01-03
Just a quick question. Why are you doing this via a shell script? Why not just call the command directly from the crontab?
```
20 7 * * * /usr/bin/systemctl suspend
```

---

### Post by TheFu on 2022-01-03
> **rburkartjo said:**
> fu if your up to this 
lets give this a try

here is a script that i have in my home folder

#!/bin/bash
/usr/bin/vlc


Please use code tags.

We cannot run GUI programs from cron.  Pretty certain I said that already and I know my links say that.  Yes - it is in MY FIRST REPLY.   crontab programs have to work even when nobody is logged in and there aren't any GUI sessions.  Technically, there are ways to make it work, but I won't help with that.  It won't get you the end result you desire and is used by poorly created server programs where a developer was lazy and didn't remove all GUI dependencies - I'm looking at YOU ORACLE.  We all know you (Oracle) did this and that is screws all our servers.

Try a different script that uses only CLI programs.

And use 'code tags' as requested multiple times.

If you want to run something on a schedule that has a GUI, use something like **alarm-clock-applet**.

---

### Post by rburkartjo on 2022-01-04
tks fu will mess with

---

### Post by rburkartjo on 2022-01-19
this is crazy i have upgraded to ubuntu 21.10 and switch to the slim display manager the scripts are working.

---

