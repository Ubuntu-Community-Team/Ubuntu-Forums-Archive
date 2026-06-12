---
title: "How to delete every folder named &quot;derek&quot; except &quot;/home/derek&quot; more than one week old."
date: 2021-12-09
forum: New to Ubuntu
---

### Post by kaolincash on 2021-12-09
Howdy folks,

I have a nasty habit of leaving "to be deleted" files strewn about my server in folders named derek.

I use WinSCP's explorer interface a lot and to minimise having instances and tabs open while actually using it like a file explorer (deleting large bodies of small documents, etc.), I don't like to have it clog up the pipes with multiple connections to manage several deletion processes occurring simultaneously. So I prefer to just select a bunch of files over SFTP and drag them into a new folder called "derek" that I then resolve to return to delete later. I'm sure you see the obvious flaw in my extremely lazy plan.

So, once you're all finished cringing at my attempt to manage a remote ubuntu server by using WinSCP like it's Windows Explorer and KiTTY like it's PowerShell, (I'm *very* much in a transitional period and would like more freedom to tinker around and make mistakes without filling up my drive with loose files when something I experiment with fails and I put off cleaning up the residual files due to the multiconnection issue in WinSCP), I'd like help in creating a spider that really likes to eat people named derek. 

I would like to be talked through the steps needed to create a service that starts upon booting the server that monitors for any directory named "derek", then deletes every instance of every directory named "derek" currently over a week old, with the sole exception of the directory at "/home/derek", which, of course, should be immune to the sweeping process. I'd like this to recur weekly, indefinitely, silently, and automatically upon starting the server. If, upon boot, it has run within the last week, I would like it to skip the search and terminate or something along those lines.

I have SSH access, SFTP, and also I have Cockpit set up with the terminal there, so I'm covered for access. I hope this is enough information for us to get started figuring out what steps I need to take, really this is more an orienteering challenge than anything, I think, so with a bit of friendly guidance and prescience that I'm *very* new to linux, having spent my whole life using Windows exclusively, and so my foundational knowledge is extremely limited.


**TL;DR**:
I would like a silent, auto-starting, weekly janitor spider that crawls through my entire server for folders named "derek" older than one week, unless the path is equal to "/home/derek" relative to root (so it would delete /home/derek/derek but not /home/derek). It also needs to not trigger a search every time I restart the server--only if it's been at least a week since its last hunt.

TIA for your assistance,
Maia

nb. I call the folder "derek" because it takes less time than it does to type "delete".

---

### Post by TheFu on 2021-12-10
I'd use '**find**' to create a list, then remove all that have /home/derek in the name with **egrep -v**.  Put the command into a file (called a script). If you are working on homework, look for a "top 50 find examples" webpage on the internet for examples of *find*. It is one of the few commands where examples really help towards understanding.

**Find** has options for directories, files, modified over X days ago and to delete. Creating a file in a directory isn't the best answer. If you renamed the directory, perhaps appending -DELETE to the name, that would be easier than looking for a file inside a directory you want to delete.

Find is very unforgiving, so be 100% certain when the -delete option is used that it didn't "find" more than you really wanted.  Lots of admins have stories - including me.  I once was looking for Netscape cache files and it found /, then started deleting the entire OS. Two things were in my favor.  There was a CDROM in the machine mounted on /cdrom, so there were lots and lots of permission denied errors.  I never banged on <cntl>-c faster or more often than that day.  The other thing was I'd created a tape backup the day prior - purely by chance.

To run it weekly, put the script into crontab ... but why not just use 'at' when you decide to delete something.  You can have **at** delete stuff in the future.
```
echo "rm  /path/to/directory" | at now + 7 days
```
Pro Tip.  Don't use relative paths. Always use full paths in scrips.  Cron doesn't set the PWD or most other environment variables, so the script shouldn't expect those to be set. **Always use full paths to command and data locations in scripts.** Always.

---

### Post by KBar on 2021-12-10
Recently, I was looking through cron jobs on my computer and stumbled upon this script that runs every day: [https://git.launchpad.net/ubuntu/+source/apport/tree/etc/cron.daily/apport](https://git.launchpad.net/ubuntu/+source/apport/tree/etc/cron.daily/apport)

If you place it in */etc/cron.weekly*, it will run weekly, as it says. The day and the time when it runs is written in */etc/crontab*. Its sibling, anacron, allows running postponed cron jobs, i.e. if the system was down during the time cron jobs were supposed to run.

Obviously, you'd need to modify the script for your needs.

I think *cron* should be installed on Ubuntu Server by default. At least its manifest file suggests that.

---

