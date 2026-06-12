---
title: "Update overwrites /etc/default/grub? How could that happen?"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by Chiel92 on 2012-05-22
Hi,

Today I ran an apt-get upgrade, and the grub configuration file appeared to be reset...
How could that happen? Does it possibly have anything to do with the update?

Regards

---

### Post by mango.muncher on 2012-05-22
Hi Chiel92,
Yes from my experience this is normal for an update. I have had to re-tweak Grub files before due to over writing during upgrades. It can get tricky when its been a few years since the last tweak.

---

### Post by Nicholas Lee on 2012-05-22
For what it is worth, I had the same problem with today's updates.
It reset the grub file back to its 'factory settings'.
 
I have no idea why todays update does this, but it is a pretty major thing to do without adequte warning or making a backup for you.
I am less than happy about this and I invite whoever was responsible to explain themselves!
 
In my case, a grub reset meant that I couldn't VNC onto my headless Ubuntu PC becuase it deleted the following line from my grub file:
GRUB_CMDLINE_LINUX="nomodeset"
 
In case anyone has the same problem, the solution was to run Xming on the local Windows PC and then use Putty SSH to remotely get a terminal window on the remote Ubuntu PC, and log in.
Then I did:
cd ..
cd .. 
sudo gedit /etc/default/grub
 
This poped up a graphical text editor on my Windows PC allowing me to put back the missing line in the grub file.
 
Then I did 
sudo shutdown -r now
to re-boot the Ubuntu box, and then everything was fine again.

---

### Post by Chiel92 on 2012-05-22
> **mango.muncher said:**
> Hi Chiel92,
Yes from my experience this is normal for an update. I have had to re-tweak Grub files before due to over writing during upgrades. It can get tricky when its been a few years since the last tweak.

Okay. I thought only grub.cfg would be overwritten in these cases, and not /etc/default/grub.
Luckily I know how to retweak it.

---

### Post by buzzingrobot on 2012-05-22
Today's update included a new kernel. That requires a grub edit, which would have been done by the updater.  But, yes, I would expect it to maintain a user's kernel options.

---

### Post by philinux on 2012-05-22
> **buzzingrobot said:**
> Today's update included a new kernel. That requires a grub edit, which would have been done by the updater.  But, yes, I would expect it to maintain a user's kernel options.

It would also normally ask if you want to keep your version or install the new "package maintainers version". You can then inspect the difference and then either keep yours or install the new one.

If this did not happen then this is a bug which needs reporting.

I have a modified /etc/default/grub and it has not been changed. My system is fully up to date.

(grub.cfg is generated but the other scripts.)

---

### Post by Chiel92 on 2012-05-22
> **philinux said:**
> It would also normally ask if you want to keep your version or install the new "package maintainers version". You can then inspect the difference and then either keep yours or install the new one.

I'm pretty sure I didn't get this. (I just updated using the update manager, not in the terminal.)

> 
If this did not happen then this is a bug which needs reporting.
I will send a bug report, if I can findout where to do that (I never have done it, so this is a good opportunity :) )

> 
I have a modified /etc/default/grub and it has not been changed. My system is fully up to date.
Weird, do we have the same ubuntu version? (Ubuntu precise pangolin 12.04)

---

### Post by philinux on 2012-05-22
Yep running 12.04 on main hard drive.

---

### Post by philinux on 2012-05-22
Still the same file. Untouched.

```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_DISABLE_OS_PROBER=true

```

---

### Post by Chiel92 on 2012-05-22
I did a bugreport bug here:
[https://savannah.gnu.org/bugs/index.php?36525](https://savannah.gnu.org/bugs/index.php?36525)

I guess it explains the problem clear enough.

---

### Post by Chiel92 on 2012-05-22
> **Chiel92 said:**
> I did a bugreport bug here:
[https://savannah.gnu.org/bugs/index.php?36525](https://savannah.gnu.org/bugs/index.php?36525)

I guess it explains the problem clear enough.

They closed the bug report saying: "We don't handle apt actions here."

What should I do?

---

### Post by wilee-nilee on 2012-05-22
> **Chiel92 said:**
> They closed the bug report saying: "We don't handle apt actions here."

What should I do?

Do you have a customized grub setup say for a default boot, what is it if you can tell us.

---

### Post by Chiel92 on 2012-05-22
> **wilee-nilee said:**
> Do you have a customized grub setup say for a default boot, what is it if you can tell us.

I didn't do very difficult things in /etc/default/grub, I have already restored it. 
I only changed the lines about the timeout and stuff.
But I have been told this bug needs reporting, so...

---

### Post by philinux on 2012-05-22
> **Chiel92 said:**
> They closed the bug report saying: "We don't handle apt actions here."

What should I do?

Raise one at launchpad. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by wilee-nilee on 2012-05-22
> **Chiel92 said:**
> I didn't do very difficult things in /etc/default/grub, I have already restored it. 
I only changed the lines about the timeout and stuff.
But I have been told this bug needs reporting, so...

Strange I never get my grub.cfg rewritten changing the default wait time back to 10, from my preferred 5.

I may have missed it though I have 3 linux OS on my HD and change the grub control at a whim to the one I want to default boot.

---

### Post by Chiel92 on 2012-05-22
> **philinux said:**
> Raise one at launchpad. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Thanks for the advice!
I read the page you pointed me at. They seem to ask for a report regarding a specific package.  Is there a specific package responsible for this bug? How do I know which one?

(Sorry if my questions are a bit stupid. I have no experience with this stuff.)

---

### Post by philinux on 2012-05-22
> **Chiel92 said:**
> Thanks for the advice!
I read the page you pointed me at. They seem to ask for a report regarding a specific package.  Is there a specific package responsible for this bug? How do I know which one?

(Sorry if my questions are a bit stupid. I have no experience with this stuff.)

Use this its pretty neat from a terminal.

ubuntu-bug update-manager

If its the wrong package it will be changed for you.

---

### Post by Chiel92 on 2012-05-22
> **philinux said:**
> Use this its pretty neat from a terminal.

ubuntu-bug update-manager

If its the wrong package it will be changed for you.

Allright, thanks for your help! 
It looks like I successfully submitted the bugreport. :)

---

### Post by buzzingrobot on 2012-05-22
> **philinux said:**
> It would also normally ask if you want to keep your version or install the new "package maintainers version". You can then inspect the difference and then either keep yours or install the new one.

(grub.cfg is generated but the other scripts.)

The new kernel was installed correctly here, but silently.  I used apt; Update Manager reported no updates.

---

