---
title: "adduser error (No UID is available)"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by cwmur on 2008-07-22
Ubuntu 8.04 all patched up as of today.

Basically, telnetd failed to install.  I tracked the problem down the "adduser" command.  It appears that there are no UIDs between 100-999.

root@caottd04050-linux:/home/cwmur# adduser --system xyz
adduser: No UID is available in the range 100-999 (FIRST_SYS_UID - LAST_SYS_UID).
adduser: The user `xyz' was not created.
root@caottd04050-linux:/home/cwmur# 

However, checking at the usual files (/etc/passwd), there is no way that all the UIDs are used up.  The last UID in that range used was 125, leaving 126 to 999 available.

Is there any other spot to look where UIDs are used?  

This is my 2nd attempt at fixing this problem.  The first time, a clean reinstall fixed it, and I'm hoping I don't need to that again.

Note that the first time the problem occurred, it failed on installing xrdp.  (telnetd installed first).  The 2nd time, xrdp was installed first, and telnetd was failing.  Not sure if anything is related to the above.

Any help much appreciated.
/cwmur

---

### Post by RealPSL on 2008-07-22
What about in /etc/groups maybe it is running out of gids in that range although the error message does not indicate that. The other thing I would try is running the pwck and grpck commands to ensure that they are consistent.

---

### Post by cwmur on 2008-07-23
Thanks for the info.

There appears to be no problems in /etc/group.

I ran both pwck and grpck.

pwck returned that some of the home directories were invalid, but nothing drastic.
[I]
root@caottd04050-linux:/etc# pwck
user lp: directory /var/spool/lpd does not exist
user news: directory /var/spool/news does not exist
user uucp: directory /var/spool/uucp does not exist
user www-data: directory /var/www does not exist
user list: directory /var/list does not exist
user irc: directory /var/run/ircd does not exist
user gnats: directory /var/lib/gnats does not exist
user nobody: directory /nonexistent does not exist
user dhcp: directory /nonexistent does not exist
user syslog: directory /home/syslog does not exist
user klog: directory /home/klog does not exist
user hplip: directory /var/run/hplip does not exist
user pulse: directory /var/run/pulse does not exist
pwck: no changes
root@caottd04050-linux:/etc# 
[/I]

I looked into /usr/sbin/adduser script, and that problem occurs when first_avail_uid returns -1, which happens when all UIDs between 100-999 cause getpwuid($t) to return something that is defined.  No clue why yet...

Will keep investigating... I do not want to have to reinstall Ubuntu again, and since the problem cropped up twice in my 2 attempts at installation, I'm sure it will happen in my next install... unless we find a fix.

Anyways -- thanks.

---

### Post by cwmur on 2008-07-23
I found the cause of the problem.

I tweaked the adduser script to print out the users associated with the uids.  And they were users from across the network.

This got me thinking.  I also had the "nis" package installed (so that I can access my directory in the network, for backups).  So I uninstalled the nis package, and the adduser script started to work again.

So I need to now figure out if nis has any config options to avoid this problem (or I simply need to uninstall nis, install new programs, reinstall nis).

---

### Post by cwmur on 2008-07-23
Quick workaround (not permanent fix):

My nsswitch.conf has:
[I]
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:     files nis
group:      files nis
shadow:     files nis

... parts snipped ...
[/I]

Update /etc/nsswitch.conf to

[I]
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

#passwd:     files nis
#group:      files nis
#shadow:     files nis
passwd:         compat
group:          compat
shadow:         compat
[/I]

And attempt to run adduser --system.  It should now work.

Afterwards, restore to the previous nsswitch.conf.

---

