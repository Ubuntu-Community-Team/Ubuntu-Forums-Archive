---
title: "Getting a script to load at startup doesn't seem to work"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by Bolli1983 on 2012-01-31
Hello,

i'm trying to set up ubuntu (11.10) on a htpc (yes, first time using linux) and so far i've got almost everything working, including a working ir-receiver without using lirc. To load the correct keymappings i have to execute 'ir-keytable -c -w /etc/rc_keymaps/imon_mce'. I'd like to have linux execute that line automatically on boot, so (found that in a [tutorial]("http://ardanedh.blogspot.com/2011/06/harmony-one-with-imon-and-xbmc-without.html")) i created a script in /etc/init.d/ and as far as i've understood, added it to the startup scripts by this 'sudo update-rc.d mce-remote defaults 55 45'. 

Now my problem is, that that script doesn't seem to get executed. As i'm totally new to linux i'm not even sure how to check, i tried typing 'dmesg' after reboot and checked everything that it spit out, i even removed the script, added an 'echo +++++' to it and added it again, then checking dmesg to see if it got executed, but i couldn't find it.

I'd be happy about any help or links to help myself (worked quite well this far). Thanks in advance =)

---

### Post by lechien73 on 2012-01-31
Hello and welcome to the forums,

Has the script been marked as executable? If you open a terminal window and type:

```
ls -l /etc/init.d
```

You will notice output like the following

```
-rwxr-xr-x 1 root root  2800 2011-07-14 06:10 umountfs
-rwxr-xr-x 1 root root  2211 2011-07-14 06:10 umountnfs.sh
-rwxr-xr-x 1 root root  2926 2011-12-15 06:40 umountroot
-rwxr-xr-x 1 root root   807 2011-07-12 10:17 unattended-upgrades
-rwxr-xr-x 1 root root  1985 2011-07-14 06:10 urandom
```

If your script doesn't have the "x" in the "-rwxr-xr-x" block at the beginning, then it won't be executed.

To change this, type:

```
sudo chmod +x /etc/init.d/mce-remote
```

---

### Post by Cheesemill on 2012-01-31
Instead of messing about with init scripts, simply place the command that you want to run at the bottom of the /etc/rc.local file.

The rc.local file is run with root privileges after all the other init.d scripts have completed.

---

### Post by Bodsda on 2012-01-31
> **Cheesemill said:**
> 
The rc.local file is run with root privileges after all the other init.d scripts have completed.

And that is exactly why you shouldnt run user scripts from rc.local

---

### Post by Bolli1983 on 2012-01-31
Thanks for the quick replies, i'm pretty sure i have NOT marked the script executable, so that's the first thing i'm gonna check, when i get home tonight.

I think i tried putting it in the rc.local file after nothing else worked and the lines didn't get executed either.(in the tutorial, that i went through, it was stated that rc.local would be be too late and could mess up lcdproc)

I'll let you know about the result tonight. Thanks again =)

One question afterwards though, if i insert 'echo blablabla' in my script (or in rc.local) and type 'dmesg' after reboot, i should be able to find "blablabla" somewhere in the output, right?

---

### Post by Cheesemill on 2012-01-31
> **Bodsda said:**
> And that is exactly why you shouldnt run user scripts from rc.local

Sorry, I thought that the OP stated the he needed to run the command as root, but looking back I can see that I must have imagined that part :)

---

### Post by Bolli1983 on 2012-01-31
Setting +x on the file did it. It's working now, thank you!

---

