---
title: "Script running in Startup or Cron with admin privileges ?"
date: 2006-08-20
forum: Programming Talk
---

### Post by Browser_ice on 2006-08-20
I have 2 scripts that I have put into my session startup but noticed that they are not being run. They are for doing an AVG update and AVG full scan using SUDO. When I run them manualy, it asks me for the password and then runs ok. But never run from the startup. I figure it is because it cannot access admin privileges to successfuly run.

How do I do that ?

If I fix this then the same technics could be use for any scripts running in the cron tab ?

---

### Post by tagra123 on 2006-08-21
If running in /etc/init.d they will not need the sudo command.

Try using the full path to the file you are trying to execute.


If a script is in your home directory you will want the command to look something like this.

/home/myusername/SomeShellScript.sh


About cron jobs:

I prefer crontab over ubuntu's default setup of just dropping files in to the /etc/cron.hourly /etc/cron.weekly, or /etccron.daily directories 

I create my cronjobs in a text file -- one for root (backup scripts), and one for just my use.

sudo crontab (options) gives access to the root crontab
crontab (options) gives access to the current user

There is an example in this post (It's near the bottom):

[http://www.ubuntuforums.org/showpost.php?p=1402126&postcount=17](http://www.ubuntuforums.org/showpost.php?p=1402126&postcount=17)

---

### Post by LordHunter317 on 2006-08-21
It could use admin privileges, but you need a password. It won't even try to prompt if it doesn't have a terminal, just fail.

Your options are:[list][*]Put these in root's crontab, like they belong.  Despite what tagra123 said, never add anything to root's crontab.  Edit /etc/crontab, or add to /etc/cron.*/.  It's more difficult to adminster your system if your cron entries are everywhere, which is why I don't use root's crontab.  All of root's entries are defined in the master file.[*]Add NOPASSWD to an sudoers entry for them so they don't prompt.  But this is wrong, you want to do number 1.[/list]But why are you doing a full scan on login anyway?  If you have bad stuff, it's already too late.

---

### Post by tagra123 on 2006-08-22
> **LordHunter317 said:**
> It could use admin privileges, but you need a password. It won't even try to prompt if it doesn't have a terminal, just fail.

Your options are:[list][*]Put these in root's crontab, like they belong.  Despite what tagra123 said, never add anything to root's crontab.  Edit /etc/crontab, or add to /etc/cron.*/.  It's more difficult to adminster your system if your cron entries are everywhere, which is why I don't use root's crontab.  All of root's entries are defined in the master file.[*]Add NOPASSWD to an sudoers entry for them so they don't prompt.  But this is wrong, you want to do number 1.[/list]But why are you doing a full scan on login anyway?  If you have bad stuff, it's already too late.



This is tagra123

You say to add it to the root's crontab and then turn around and say not to???

The cron entries are not everywhere. I based my method on the crontab's own documentation  "man crontab". Your way works too.

The only dirrerence I see is that Ubuntu lets everything to be manually entered in the /etc/crontab instead of the /var/spool/cron/crontabs (which is where crontab -e  normally stores its' cronjobs. There is a crontab file for each user useing the crontab command. 

I keep the cronjobs  as text file in the home directory for easy editing and giving easy examples. Of course, I'm the only one using this machine so I know where everything is anyway. 

If this was a multiple user machine I can see that there might be some advantage to using Ubuntu's  /etc/crontab way of doing things.

Either way is OK,  but I just prefer editing a text file and then inserting it.


I think we are doing almost exactly the same thing , that is both will accomplish the same thing.

I do agree with the part about scanning at startup. Why not just scan once weekly or once daily by using the cron job?

---

### Post by LordHunter317 on 2006-08-22
> **tagra123 said:**
> You say to add it to the root's crontab and then turn around and say not to???I messed up.  Don't put them in root's crontab.  Debian/Ubuntu policy isn't to put anything there, so you shouldn't either.

> If this was a multiple user machine I can see that there might be some advantage to using Ubuntu's  /etc/crontab way of doing things.There's an advantage if you're single user: all system cronjobs are defined in a single place.  Where the scripts are is rather irrelevant, since I define tons of jobs that don't need external files.

---

### Post by tagra123 on 2006-08-22
> **LordHunter317 said:**
> I messed up.  Don't put them in root's crontab.  Debian/Ubuntu policy isn't to put anything there, so you shouldn't either.

There's an advantage if you're single user: all system cronjobs are defined in a single place.  Where the scripts are is rather irrelevant, since I define tons of jobs that don't need external files.


I think what you mean is to place everything in the /etc/crontab file and for root jobs use root as the user and for user jobs use someusername for those jobs.

In Ubuntu's modified /etc/crontab the user has to be defined so rather than using sudo crontab somecronjobs.txt it could just be marked as root user and edited directly into the /etc/crontab file. That in effect would be the same as the "sudo crontab" and the regular user specific jobs would just list that user.  


If more than one user -- everyones jobs are in one place. I still like the idea of each users jobs being in their own file.  I take back what I said before -- on a multiple user computer that isn't a good idea. That is any sudoer can mess with anyones cronjobs. Is this correct?




Now I only have 7 jobs running with cron so I still don't see the real advantage but I may try it. Who knows maybe I'll like doing it that way better.

---

### Post by LordHunter317 on 2006-08-22
> **tagra123 said:**
> I think what you mean is to place everything in the /etc/crontab file and for root jobs use root as the user and for user jobs use someusername for those jobs.No, I mean place system jobs in /etc/crontab or /etc/cron.d.  

That may mean only jobs for root.  It may mean jobs for root and daemon accounts (e.g., www-data, named).  It certainly doesn't mean jobs for everyone.


> If more than one user -- everyones jobs are in one place.That's not what I was suggesting be done, however.  Apologies if it wasn't clear.  There's a major difference between system jobs and jobs for other interactive users.  And system jobs ought to be defined in a central place.

Other interactive users obviously need independent control over their jobs.  But using two places for root's jobs is senseless and bad.  And seeing as the system already uses one place, you're somewhat stuck.

---

### Post by tagra123 on 2006-08-22
> **LordHunter317 said:**
> No, I mean place system jobs in /etc/crontab or /etc/cron.d.  

That may mean only jobs for root.  It may mean jobs for root and daemon accounts (e.g., www-data, named).  It certainly doesn't mean jobs for everyone.


That's not what I was suggesting be done, however.  Apologies if it wasn't clear.  There's a major difference between system jobs and jobs for other interactive users.  And system jobs ought to be defined in a central place.

Other interactive users obviously need independent control over their jobs.  But using two places for root's jobs is senseless and bad.  And seeing as the system already uses one place, you're somewhat stuck.



Gotcha.

That does make more sense.  I went ahead and gave it a try your way. Its executing jobs just fine now.  

I had really never took the time to look over Ubuntu's way originally. I just fired up crontab to start the jobs. 

If you look at the previous post in the scheduled backup server thread I posted both ways now.

---

