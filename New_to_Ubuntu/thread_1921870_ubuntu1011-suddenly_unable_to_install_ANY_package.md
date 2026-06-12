---
title: "ubuntu10:11-suddenly unable to install ANY package"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by lawrencrj on 2012-02-07
Another person had this exact same problem and a fix was given that worked for him (or her) and the thread was closed.  But that fix given did NOT work for me.  Below I will give the details of the problem and the fix that was given that did not work for me.  First, understand that I am new to Linux starting last week.  After installing Ubuntu 10:11 (Unity desktop) I succeeded in downloading and installing several applications (including skype) using "terminal" with commands of the form "sudo apt-get install skype".  However, after installing WINE and trying to install from that (with no success) I totally lost the ability to install anything whatever using "sudo apt-get ..." or by any other means.  

After entering my password for authentication I consistently get a box "An unhandlable error has occurred" followed by:
"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks."  If I click on "details" I get 
"System Error: E:Not able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package." 

The following is the solution that worked when given to the other person who had a similar problem back in 2009.

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
(followed by)
sudo apt-get update && sudo apt-get upgrade
(followed by)
sudo apt-get install -f
(followed by)
sudo dpkg --configure -a

When I repeated this sequence here is what I got after
entering 
"sudo apt-get install -f":
E: unable to unlock the administration directory (/var/lib/dpkg), is
another process using it?
The only processes running was the terminal itself but I shut down and restarted and tried again with the same result.  [First I answered "no" and that was not a legal command - duhh - should have known!!]
Then even though that had not gone well I entered 
"sudo dpkg --configure -a" and got 
"dpkg: error: dpkg status database is locked by another process.

Even though the replies were not encouraging I tried again to install something and got the same message "an unhandlable error has occurred".

I welcome any suggestion that someone might have to fix this problem.
Otherwise I plan on just reinstalling Linux from scratch and reinstalling everthing I need before trying to use WINE again.

---

### Post by SuaSwe on 2012-02-07
Is there a dpkg process running?

```

ps -ef | grep dpkg
ps -ef | grep software-centre

```

... etc. In any case, if you haven't done so already, try restarting the machine then running:

```

sudo dpkg --configure -a

```

Then try again. If all else fails you can try removing the lock file itself, though be warned this could corrupt the package database, as per [this site]("http://superuser.com/questions/49483/ubuntu-synaptic-package-manager"). Removing the lock file would be done by:

```

sudo rm /var/cache/apt/lock

```

---

