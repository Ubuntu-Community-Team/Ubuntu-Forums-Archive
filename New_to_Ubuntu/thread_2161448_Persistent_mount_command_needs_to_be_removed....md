---
title: "Persistent mount command needs to be removed..."
date: 2013-07-10
forum: New to Ubuntu
---

### Post by NuxNik on 2013-07-10
I am experimenting, and learning a great deal in the process, by installing various packages and trying to make them work

I have 4 partitions, one of which ONLY gets upgraded when I'm satisfied that I can successfully install and run the software.
The 3 other partitions are WiP (Work in Progress) which have been uninstalled a few times and get re-installed as with a dd from my baseline..

I am also trying to get data that I want to available ALL the time on the baseline to be installed on a 5th partition, so that when   the baseline is run on partitions 2,3, or 4, they  still be able to run without having to set them up.
For example I have a small LAMP server running that is slowly being built up as a web server with some content for family members. So such things as the www directory, and files such as hosts, hostnames, certificates,  are actually on the data partition and symlinked to their appropriate OS directories.
So it doesn't mater which partition is actually up and running, for the web server to be "serving".

Unfortunately, I made an error when setting up one of the symlinks with a bad mount command.

Every time I reboot, the OS flags the bad mount
and gives me the option of (S)kipping the problem, or fixing it.

But I don't know how to get rid of this persistent mount command
/etc/fstab contains nothing applicable

where can I find this persistent but incorrect mount command ?

Thanks.

---

### Post by oldfred on 2013-07-11
Is it the link that is causing the issue? 
Where is link?

find /home -type l
                 ls -lah | grep ^l

---

### Post by NuxNik on 2013-07-12
Thanks for the response.
But it didn't work

I get an error message for it while the LUbuntu splash screen is still showing
I get a choice of "S" to skip the command or "M" to modify it.
"S" gets me to the desktop
"M" gets me to command line screen, where I have no clue what to modify and where.

---

### Post by oldfred on 2013-07-12
From command line run the commands posted above.
Were you looking at fstab of your install or the liveCD?
Post this also:
mount
       cat /etc/fstab

If you cannot get to gui and run Firefox, copy output to a flash drive and then post it from that.

---

