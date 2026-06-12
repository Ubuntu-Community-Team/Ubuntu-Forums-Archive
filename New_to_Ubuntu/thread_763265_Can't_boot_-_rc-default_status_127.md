---
title: "Can't boot - rc-default status 127"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Xiong Chiamiov on 2008-04-22
EDIT: summary's [at the bottom]("http://ubuntuforums.org/showthread.php?p=4769702#post4769702")

So, I upgraded to Hardy today (isn't that how all bad threads go?), and had to sort through a whole mess of problems, most of them related to all the crap I had done to KDE.  I finally got everything working, then updated everything in adept, rebooted, updated again, and it told me I had to reboot.  First sign of trouble was when it said that it couldn't find /sbin/shutdown, so I hard-rebooted.  Now, right after it starts the NFS service, I get:
```

rc-default main process (4885) terminated with status 127

```
[This]("http://ubuntuforums.org/showthread.php?t=330463") is fairly close to the error I'm getting, but the only solution posted in there is... not very helpful.  I seem to remember telling adept to use the package manager's version of some file that seemed like rc-default (though I know for sure it was in the KDE3 folder somewhere).  I've lost track of which times I've done what, but I thought that that was before a successful boot.  Anyways, I'll play around with seeing if I can figure out how to reset rc-default to, well, default, and I'd appreciate any insights in the meantime.

---

### Post by Xiong Chiamiov on 2008-04-22
.

---

### Post by warp99 on 2008-04-23
> **Xiong Chiamiov said:**
> So, I upgraded to Hardy today (isn't that how all bad threads go?), and had to sort through a whole mess of problems, most of them related to all the crap I had done to KDE.  I finally got everything working, then updated everything in adept, rebooted, updated again, and it told me I had to reboot.  First sign of trouble was when it said that it couldn't find /sbin/shutdown, so I hard-rebooted.  Now, right after it starts the NFS service, I get:
```

rc-default main process (4885) terminated with status 127

```
[This]("http://ubuntuforums.org/showthread.php?t=330463") is fairly close to the error I'm getting, but the only solution posted in there is... not very helpful.  I seem to remember telling adept to use the package manager's version of some file that seemed like rc-default (though I know for sure it was in the KDE3 folder somewhere).  I've lost track of which times I've done what, but I thought that that was before a successful boot.  Anyways, I'll play around with seeing if I can figure out how to reset rc-default to, well, default, and I'd appreciate any insights in the meantime.
 
The file /etc/event.d/rc-default is a script:

```
#rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

```
When no default runlevel information is available this particular script attempts to determine what is should be.

Which service is the problem? You can stop the service from being loaded by issuing:
```
sudo update-rc.d -f ($name_of_service) remove
``` 
since there seems to be a problem with the runlevels not being correct. Once you do that you can issue:
```
sudo update-rc.d ($name_of_service) defaults
```
to resume loading the service normally at boot time.

If that does not solve the problem you may need to purge the package that supplies the service, then reinstall to get the correct script in your /etc/init.d/ folder. So you would run:
```
sudo apt-get remove --purge ($name_of_package_for_service)
```
then:
```
sudo apt-get install ($name_of_package_for_service)
```
to have the default configuration restored.

---

### Post by Xiong Chiamiov on 2008-04-23
My problem is that all of this happens before I can get to any prompt, either through normal boot or recovery.  If there's a way to somehow skip that, then I could do some stuff, like what you suggested.

---

### Post by Xiong Chiamiov on 2008-04-23
I guessed that the error I was getting was that telinit didn't exist, so I copied it over from the Live CD I'm on (which is a Hardy beta), and now I get this:
```

*Starting portmap daemon
*Starting NFS common utilities
/bin/sh: 1: runlevel: not found
IFS='
'
OPTIND='1'
PATH='/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin'
PPID='1'
PS1='# '
PS2='> '
PS4='+ '
PWD='/'
TERM='linux'
UPSTART_EVENT='runlevel'
UPSTART_JOB='rc2'
UPSTART_JOB_ID='5'

```
and here's my /etc/event.d/rc-default :
```

# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
	runlevel --reboot || true

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script

```

Should I get this moved out of the Beginner Forum?

---

### Post by warp99 on 2008-04-23
> **Xiong Chiamiov said:**
> I guessed that the error I was getting was that telinit didn't exist, so I copied it over from the Live CD I'm on (which is a Hardy beta), and now I get this:
```

*Starting portmap daemon
*Starting NFS common utilities
/bin/sh: 1: runlevel: not found
IFS='
'
OPTIND='1'
PATH='/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin'
PPID='1'
PS1='# '
PS2='> '
PS4='+ '
PWD='/'
TERM='linux'
UPSTART_EVENT='runlevel'
UPSTART_JOB='rc2'
UPSTART_JOB_ID='5'

```
and here's my /etc/event.d/rc-default :
```

# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
	runlevel --reboot || true

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script

```

Should I get this moved out of the Beginner Forum?

You can easily solve this problem by running:
```
sudo apt-get remove --purge nfs-common
```
and then reinstall the package:
```
sudo apt-get install nfs-common
```
the /etc/init.d/nfs-common script is missing it's runlevel defaults so you need to remove the corrupt script and replace it with the correct one through the apt-get package management system. 

If that does not clear up the problem the error may be with some supporting packages, so you can run:
```
sudo update-rc.d -f nfs-common remove
```
to stop the nfs service from starting at boot since nfs is only needed for networking. This way you can boot normally until you determine the problem.

Edit:
The file telnit is supplied by the package 'upstart-compat-sysv' so I would suggest reinstalling that package:
```
sudo apt-get install --reinstall upstart-compat-sysv
```

---

### Post by warp99 on 2008-04-23
> **Xiong Chiamiov said:**
> My problem is that all of this happens before I can get to any prompt, either through normal boot or recovery.  If there's a way to somehow skip that, then I could do some stuff, like what you suggested.

You can get to a prompt by pressing crtl+alt+f2 to reach a login console. If that does not work you can boot to the install disc, then mount the drive and chroot into the drive and repair the damage that way, but first see if you can use the crtl+alt+f2 console login.

---

### Post by Xiong Chiamiov on 2008-04-23
> **warp99 said:**
> You can easily solve this problem by running:
```
sudo apt-get remove --purge nfs-common
```
and then reinstall the package:
```
sudo apt-get install nfs-common
```

> **Xiong Chiamiov said:**
> My problem is that all of this happens before I can get to any prompt, either through normal boot or recovery.  If there's a way to somehow skip that, then I could do some stuff, like what you suggested.
Right now I'm disabling all of the nfs-common's in rc0-6 and rcS, similarly to [this]("http://ubuntuforums.org/showthread.php?t=313241&highlight=startx+gdm#5"), and we'll see how that goes.

---

### Post by Xiong Chiamiov on 2008-04-23
Ok, so now nfs-common doesn't start, but I still get a hang.  I looked up a little farther on the screen, and saw an error about AppArmor, so I copied over /usr/sbin/apparmor_status and /sbin/apparmor_parser.  That got rid of that message, but now I've got a longer one (or series of them) that, unfortunately, are mostly scrolled above my view.  They all pertain to apparmor and don't look like easy copy-n-paste-file fixes, but rather that something went wrong in my apparmor installation.  If I could get to where I could run adept, I think I would be fine, but I'm not altogether sure how to get there.

---

### Post by Xiong Chiamiov on 2008-04-23
> **warp99 said:**
> You can get to a prompt by pressing crtl+alt+f2 to reach a login console. If that does not work you can boot to the install disc, then mount the drive and chroot into the drive and repair the damage that way, but first see if you can use the crtl+alt+f2 console login.

I'm sorry, I missed that post.  Thank you very much, that's a nice useful thing to know.

Conclusion:
If you get something like this:
```

rc-default main process (4885) terminated with status 127

```
then you need to copy the file 'telinit' from /sbin on a live CD to that same folder on your installation.

For the apparmor problems I was having, I had to skip to a login console by pressing ctrl+alt+f2 during boot, then installing first the apparmor-profiles package, followed by apparmor.

This was *way* too tiring a day, and I needed to be writing a paper...
warp99, if the thanks system was working, I'd give you one, but as it is, you'll have to wait.

---

### Post by scott29 on 2008-08-22
I have this problem...exactly how to I copy the 'telinit' file from the CD?  Where is it?  Can somebody please help?

Thanks.

---

