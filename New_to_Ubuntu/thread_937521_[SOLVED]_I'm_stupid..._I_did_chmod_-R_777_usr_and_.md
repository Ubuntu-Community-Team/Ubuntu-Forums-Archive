---
title: "[SOLVED] I'm stupid... I did chmod -R 777 /usr and messed up system"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by iansane on 2008-10-03
Hi, as the subject says, I'm stupid.

I thought changing permissions to 777 is security risk but did not know it would make me loose priveleges.

I lost ability to sudo which I got back by using recovery mode to 
```

chown root:root /usr/bin/sudo
and
chmod 4755 /usr/bin/sudo

```

Got that from post where someone did a chown on the /usr folder.

Can anyone tell me a safe permission to set recursively?

I tried 755 but can't access users and groups from system>administration

It tells me I don't have permission.

How can I add myself to the root group or do I need to get the permissions straightened out instead?

I'm thinking I would be better off doing a fresh install than trying to find permissions of every file and folder and reset them.

Thanks for any help

---

### Post by Frak on 2008-10-03
On both commands, use -R as an argument. Such as:

chown root:root -R /usr/bin/sudo
chmod 4755 -R /usr/bin/sudo

---

### Post by iansane on 2008-10-04
but sudo is a app inside /usr/bin

are you saying apply those permissions to all of the /usr directory?

---

### Post by iansane on 2008-10-04
Just did a clean install. Was glad ndiswrapper was on the live cd.

So if anyone can explain the reason changing permissions to allow all with 777 caused me to loose things I'd like to know but that problems solved.

Thanks

---

### Post by oldos2er on 2008-10-04
[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions) and [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by nowshining on 2008-10-04
> **iansane said:**
> Just did a clean install. Was glad ndiswrapper was on the live cd.

So if anyone can explain the reason changing permissions to allow all with 777 caused me to loose things I'd like to know but that problems solved.

Thanks

u know if ur just going to re-install everytime someone tries to help u - there is NO reason asking on the forums for help, just re-install and be done with it.. :| 'cause I think on like every other help Q, u just re-installed after a suggestion of help has been offered, either that or I got u mixed up with someone else...

---

### Post by iansane on 2008-10-04
> **nowshining said:**
> u know if ur just going to re-install everytime someone tries to help u - there is NO reason asking on the forums for help, just re-install and be done with it.. :| 'cause I think on like every other help Q, u just re-installed after a suggestion of help has been offered, either that or I got u mixed up with someone else...

I didn't think that I did it that often. I hate having to reinstall but there are times when it takes days to get a response that works. Those times I go ahead and reinstall. 

I'll admit, sometimes a day or two  trying to fix something and waiting for a response seems more like weeks and I give up and pull out the CD. I apologize to anyone who feels they have waisted time trying to help me, and I will try to keep that in mind before I ask for help again.

This time I just didn't see trying to figure out default permissions for hundreds or thousands of files and manually reseting them. 

I know, I was impatient this time but still haven't got a response as to how to fix the problem for the whole /usr directory and I need my computer today so I'm glad I went ahead and re-installed.

I also know the best fix is not to do stupid things like this but like I said, I didn't think 777 permissions would cause the system to not act right.

oldos2er,

Thanks for the links. I'll read more about permissions.

---

### Post by The Cog on 2008-10-04
As it happens, reinstalling is probably the only way to restore the correct permissions from a nono like that. Permissions are fundamental to unix,and you should try to work with them not against them. Still, it's all a learning process. Enjoy the learning rather than beating yourself up for not knowing everything straight off.

---

### Post by JoshuaRL on 2008-10-04
> **nowshining said:**
> u know if ur just going to re-install everytime someone tries to help u - there is NO reason asking on the forums for help, just re-install and be done with it.. :| 'cause I think on like every other help Q, u just re-installed after a suggestion of help has been offered, either that or I got u mixed up with someone else...

First off, please try to be just a little bit kinder.  When I started I reinstalled over 10 times trying to figure out why my computer didn't work.  Turned out I just needed to mess with a few settings in xorg.conf, but it took me a while to get there.  Fortunately things have gotten much better now.

Second, please try not to use IM or txt talk here on the forums.  Not everyone speaks english well here, and so it can be difficult or impossible for them to understand you.  Plus, it makes it really difficult for people to search for answers to their problems if everyone is using shorthand of various sorts.

Look at the "Welcome to the Ubuntu Forums!" link in my signature for some good reminders.

---

### Post by RequinB4 on 2008-10-04
Agree with the above.  One time late at night on a friday I decided to change so recursivley half the folders on / weren't accessible by anyone (I have no idea why, don't ask)... Eventually did a reinstall, but it just goes to show you be verrry careful with permissions, and even more careful with the 'sudo' command - i think even more experienced users can forget that sometimes :P.

Glad you got it working, even if it was just a reinstall.

---

### Post by humperdink on 2009-04-14
I did the same stupid thing in a fit of rashness.  I was able to solve it with 

chmod -R 4755 /usr

This allowed me to mount the windows partitions from the desktop "places" menu and regain sudo abilities.  I don't know if I messed other things up in the process though.

---

### Post by pfoff on 2011-03-06
We have a guy who tried that on a clients server, so I had to write a script, that gathers uid/gid/perm infos from a reference host(must be same distri/version and contain mostly the same packages) and sets them (eventually by booting a live cd) on the target host.
Prooved to be very useful, so I like to share it with you!) 
You have to run it on the reference host for the important dirs(/var /etc /usr... or try / with lot of ram and time!) like that:
fix_perms.pl /DIR /tmp/fixperms_DIR.db
So you get a db file that has the infos you need. Copy it together with the script on the target host and run the script there like that:
fix_perms.pl /tmp/fixperms_DIR.db
After that the perms on DIR are reset correctly! If you are in a live environment you will have to chroot to the dir where your target partition is mounted, as it will work on the same dirs as before!
It worked well on 3 hosts and many times on our testing vm, but like always:
AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY....

---

