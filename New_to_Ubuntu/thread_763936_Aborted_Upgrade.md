---
title: "Aborted Upgrade"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by huzzak on 2008-04-23
Hey guys,

So, I thought that I would upgrade to Hardy Heron last night and avoid the rush or something.  It was taking too long so I put my laptop on the coffee table and went to bed.  One of my roommates unplugged it midway through the upgrade, it ran out of power and now Ubuntu can't get past the login screen.  It says that it can't find /home/jlutes/ - my home directory.  This is actually on a different partition from the rest of my operating system because I figured that it'd be easier to have it that way in case of any problems.  Is there a way to reassociate the partition?  I looked to just installing everything over again but couldn't figure out how to tell the installer that I wanted it to use my home partition as my home partition and to not do anything to the data therein.  I'm trying to backup my data now, but any advice or insights from the older and wiser crowd would be appreciated.  Thanks.

---

### Post by Confuzius on 2008-04-23
I'm pretty sure that it has to do with specifying up a matching userid.  Unfortunately my knowledge dosn't go that much farther, but you might be able to figure something out here
[http://ubuntuforums.org/showthread.php?t=109752](http://ubuntuforums.org/showthread.php?t=109752)

It might help, I know that if you're dual booting 2 different distros each with user "john" unless you specify the UID on each distro to be the same number, it sounds like you might have that sort of problem, but instead of 2 distros it's a broken install.

---

### Post by mister_pink on 2008-04-23
If you plan on reinstalling from the live CD then you need to select manual partitioning. On the next screen select your home partition and tell it to mount as /home and make sure that the format box is not ticked! Tell it which to mount as / tick format on that row. That should sort you out. Your current install might be fixable though, you could try booting into recovery mode and running something like
apt-get install -f
and maybe various other apt-get commands to finish the upgrade.

---

### Post by huzzak on 2008-04-23
I guess I am ashamed to admit that I didn't think about trying to continue the upgrade from the command line.  I did what mister_pink described though and am still having troubles.

For some reason my /home partition is reading as being completely full.  I did "df -h" and it says that /dev/sda7 has 30G completely filled.  This can't be true, but how can I convince the operating system of this ... maybe without reformatting it?  Thanks guys.  Seriously.

UPDATE: It turns out that I am a LIAR and my informations are not to be trusted.  I HAD managed to fill up my home partition through trying to backup my data.  A quick rm -rf of the extra folders I made for myself took care of the problem.

Thanks for your help.  You guys rock.

---

