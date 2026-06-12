---
title: "How do I grant permission for lp0?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by csdiwhitt on 2008-08-16
This problem has been around a while, but I can not find a solution that I can do or works.  I have defined my printer, recognized by the cups,  When I print the print test page a print job is completed, but there is a message in /var/log/messages as follows:

Aug 16 15:29:01 whitt-desktop kernel: [30445.975135] audit(1218914941.304:5): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=14127 profile="/usr/sbin/cupsd" namespace="default"

I found this:

5. 3. Check device file permissions

Device files for printers (like /dev/lp0, /dev/usb/lp0, ...) must be readable and writable for the user "root" and the group "sys".
in:
[http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_1_1](http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_1_1)

Nice to know, but there was no suggestion of a method to use to do this or even a suggestion of how to fix it.

I have Googled and Search documentation until I am half blind.

I do not understand Commands and don't turst things that I don't understand.

I have had this on my back for over a month.  If you know how to grant permission for /dev/lp0 I would be ever grateful.

---

### Post by sisco311 on 2008-08-16
Add your user to the lp group.
Open a terminal and run the following command:
```
sudo adduser *your-user-name*-*here* lp
```then log out and log in(or reboot).

---

### Post by csdiwhitt on 2008-08-16
OK, I did that, but I get the same message.

whitt@whitt-desktop:~$ sudo adduser lp whitt
[sudo] password for whitt: 
Adding user `lp' to group `whitt' ...
Adding user lp to group whitt
Done.
whitt@whitt-desktop:~$ 

Result message:

Aug 16 16:32:34 whitt-desktop kernel: [34252.059447] audit(1218918754.393:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=14996 profile="/usr/sbin/cupsd" namespace="default"

Thanks.  It didn't solve the problem, but your suggestion was very clear.

---

### Post by Too Late on 2008-08-16
You have to reboot (or re-login) before that change takes effect.

edit: Sorry, it was already said before, didn't notice that.

---

### Post by csdiwhitt on 2008-08-16
Rebooted, but still no change:

Aug 16 16:45:24 whitt-desktop kernel: [  134.506533] audit(1218919524.150:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6241 profile="/usr/sbin/cupsd" namespace="default"

---

### Post by sisco311 on 2008-08-16
never mind!
It's a bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217787](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217787)

update your system:
```
sudo aptitude update
sudo aptitude full-upgrade
```

---

### Post by csdiwhitt on 2008-08-16
OK:

whitt@whitt-desktop:~$ ls -1 /dev/lp0
/dev/lp0
whitt@whitt-desktop:~$ 

I don't know what it means, but no nasty message.

---

### Post by Too Late on 2008-08-16
It's "ls -l" (letter L with small case), NOT "ls -1" (number one).

---

### Post by cariboo on 2008-08-16
When I run ls -l /dev/lp0, I get the following:

```
crw-rw---- 1 root lp 6, 0 2008-08-15 15:17 /dev/lp0
```

Are you not pasting the output?

Jim

---

### Post by csdiwhitt on 2008-08-16
Sorry, not careful enough.

whitt@whitt-desktop:~$ ls -1 /dev/lp0
/dev/lp0
whitt@whitt-desktop:~$ ls -l /dev/lp0
crw-rw---- 1 root lp 6, 0 2008-08-16 16:53 /dev/lp0
whitt@whitt-desktop:~$ 

It does make a difference.

---

### Post by csdiwhitt on 2008-08-16
Yes, I did paste the input and output from my terminal.  Problem is that the  l and 1 look the same on my email.  I will have to fix that.

whitt@whitt-desktop:~$ ls -1 /dev/lp0
/dev/lp0
whitt@whitt-desktop:~$ ls -l /dev/lp0
crw-rw---- 1 root lp 6, 0 2008-08-16 16:53 /dev/lp0
whitt@whitt-desktop:~$

---

### Post by ds[de] on 2008-08-16
> **csdiwhitt said:**
> 
whitt@whitt-desktop:~$ sudo adduser lp whitt
[sudo] password for whitt: 
Adding user `lp' to group `whitt' ...
Adding user lp to group whitt
Done.
whitt@whitt-desktop:~$

I'm not at an ubuntu computer at the moment, but from your output it seems like the command should be:

```
sudo adduser whitt lp
```

because you want to add user 'whitt' (you) to group 'lp', not the other way round (i.e. in the way sisco311 proposed, but with the command slightly altered).

Regards,
ds[de]

---

### Post by sisco311 on 2008-08-17
> **'ds[de] said:**
> I'm not at an ubuntu computer at the moment, but from your output it seems like the command should be:

```
sudo adduser whitt lp
```because you want to add user 'whitt' (you) to group 'lp', not the other way round (i.e. in the way sisco311 proposed, but with the command slightly altered).

Regards,
ds[de]
Thanks.
You're right.

The command is:
```
sudo adduser *username groupname*
```or
```
sudo usermod -aG *groupname username*
```

---

### Post by csdiwhitt on 2008-08-17
OK.  I guess I was already there.

whitt@whitt-desktop:~$ sudo add whitt lp
[sudo] password for whitt: 
sudo: add: command not found
whitt@whitt-desktop:~$ sudo adduser whitt lp
The user `whitt' is already a member of `lp'.
whitt@whitt-desktop:~$

---

### Post by lswest on 2008-08-17
actually, I'm not sure adduser would be the right command (I believe it erases all other groups you're a member of in the process of adding you to one group).  The command I use is ```
sudo gpasswd -a *user* group
```

about the permissions, can you please post the output of ```
ls -la /dev/lp*
``` please, so we know what has to be changed (if anything).

---

### Post by csdiwhitt on 2008-08-17
Thanks, but I have check and I am still a member of at least two other groups.  These line commands do seem a little dangerous.

---

### Post by lswest on 2008-08-17
> **csdiwhitt said:**
> Thanks, but I have check and I am still a member of at least two other groups.  These line commands do seem a little dangerous.

Good to know, I've had some bad experiences with it, but it may have been my error.  Now we just need to sort out the permissions of your /dev/lp files.

Command line does offer a fast and efficient way to do things, but also expects you to know what you're doing.  I always suggest reading the manpage of a program before using it (by doing "man *command*" without the quotes).  It also helps the learning process.

---

### Post by csdiwhitt on 2008-08-17
I suppose that this shows my ignorance, but the message would indicate that CUPS is looking at /dev/tty:

Aug 17 13:28:58 whitt-desktop kernel: [17731.147685] audit(1218994138.517:5): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" [COLOR="Blue"]name="/dev/tty"[/COLOR] pid=6955 profile="/usr/sbin/cupsd" namespace="default"

If memory serves me correctly that is a reference to the old teletype device that we used many years ago.

---

### Post by lswest on 2008-08-17
sorry, didn't realize.

tty is actually the reference to a loopback file (tty0-6 are black and white full-screen terminals, and tty7 is the GUI).  And as such, I don't see how it would be denied.

Are you a user in the cups group?  Or is there a group called "printing"?

---

### Post by Gamma746 on 2008-08-17
This```
Aug 17 13:28:58 whitt-desktop kernel: [17731.147685] audit(1218994138.517:5): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6955 profile="/usr/sbin/cupsd" namespace="default"
``` looks like an apparmor error message.

Read ```
man apparmor
``` for more information.

---

### Post by csdiwhitt on 2008-08-17
I didn't have either, but I do now.  Same result though.

Aug 17 16:04:48 whitt-desktop kernel: [27064.021857] audit(1219003488.577:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=9982 profile="/usr/sbin/cupsd" namespace="default"

---

### Post by csdiwhitt on 2008-08-18
Sorry, I am new to Linux and to replying, but I got this suggestion from sisco311 and I don't know if everyone gets each reply.

OK, that seemed to work, but I may have had the latest version.

Reading package lists... Done
whitt@whitt-desktop:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done            
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done            
Building dependency tree      
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Building tag database... Done      

This is the end of the second command.  I could give you the all the read list stuff, but it is long.

---

### Post by csdiwhitt on 2008-08-18
To Gamma746;

I did the "man apparmor" and got a lot of information that I don't know how to use or control.  I have found reference to a fix:


 Chris Vigelius wrote on 2008-05-05: (permalink)

I can confirm that 2.1+1075-0ubuntu9.1 fixes this bug, and #221087 too (on Hardy final/I386)
 Martin Pitt wrote on 2008-05-07: (permalink)

Copied to hardy-updates.
 Launchpad Janitor wrote on 2008-06-09: (permalink)

This bug was fixed in the package apparmor - 2.1+1075-0ubuntu10

I found this:

apparmor (2.1+1075-0ubuntu9.1) hardy-proposed; urgency=low

  * added abstractions/smbpass and #include it in abstractions/authentication
    to allow access to /var/lib/samba/*.tdb. LP: #217787

 -- Jamie Strandboge <jamie@ubuntu.com>  Fri, 02 May 2008 13:13:52 -0400

So the fix is in ubuntu9.1.

---------------
apparmor (2.1+1075-0ubuntu10) intrepid; urgency=low

  [ Jamie Strandboge ]
   * added abstractions/smbpass and #include it in abstractions/authentication
     to allow access to /var/lib/samba/*.tdb. LP: #217787

  [ Mathias Gug ]
   * update likewise-open authentication abstraction: allow access to
     privileged pipe (LP: #235646).
   * Update smbd profile to include access to /var/spool/samba/ (printer
     sharing) and utmp update (LP: #237066).
   * Update esound location in audio profile (LP: #229127).
     Thanks to Adam Mondl.
   * Add dnsmasq profile (LP: #148590). Thanks to John Dong.

 -- Mathias Gug <email address hidden> Mon, 09 Jun 2008 18:24:09 -0400

but I don't have: apparmor (2.1+1075-0ubuntu10) intrepid; urgency=low
I am still at ubuntu9.1

---

### Post by csdiwhitt on 2008-08-20
I have been searching documentation and found something that looked like it might work, because it seemed to have the permission that my message said it wasn't getting. This came from:

file:///usr/share/cups/doc-root/help/ref-cupsd-conf.html


The following commands will create an appropriate temporary directory called /foo/bar/tmp:

mkdir /foo/bar/tmp
chmod a+rwxt /foo/bar/tmp

I tried them, but this doesn't work.

whitt@whitt-desktop:~$ mkdir /foo/bar/tmp
mkdir: cannot create directory `/foo/bar/tmp': No such file or directory
whitt@whitt-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
whitt@whitt-desktop:~$ sudo mkdir /foo/bar/tmp
[sudo] password for whitt: 
mkdir: cannot create directory `/foo/bar/tmp': No such file or directory
whitt@whitt-desktop:~$ 

I obviously do not understand makdir.

There is also no mention of granting any permission in the: 
Ubuntu Help Center -> New to Ubuntu? -> An overview of your desktop and how to use it.

I put my first PC together in September 1981.  All I had to do was plug the end of the parallel cable into the printer and the other into the PC, install DOS ane press the Print Screen key the verify the the printer worked.  We are digressing in the area of Desktop computing.

---

### Post by csdiwhitt on 2008-08-26
The problem is not lp0, its tty.  Read Write permission is being denied.  Here is a recap of what I have done and found.

I defined my printer using:

[http://localhost:631/printers/](http://localhost:631/printers/)

The printer was recognizes and the follow was presented by cups:

Description: Lexmark
Location: Beside My Desk
Printer Driver: Lexmark 4039 10plus Foomatic/Postscript (recommended)
Printer State: idle, accepting jobs, published.
Device URI: parallel:/dev/lp0

When I tried to Print Test Page I got the completed message:

Lexmark4039ECP+EPP-31  	Test Page  	whitt  	17k  	Unknown  	completed at
Sun 24 Aug 2008 04:24:15 PM EDT 

but no print out.  I looked for other messages and found:


Aug 24 16:16:28 whitt-desktop kernel: [ 1457.086993] audit(1219608988.947:4): type=1502 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=7403 profile="/usr/sbin/cupsd" namespace="default"

I mistook /dev/tty to be an alias for lp0 and checked to see how it was authorized:

whitt@whitt-desktop:~$ sudo add whitt lp
[sudo] password for whitt:
sudo: add: command not found
whitt@whitt-desktop:~$ sudo adduser whitt lp
The user `whitt' is already a member of `lp'.
whitt@whitt-desktop:~$ ls -l /dev/lp0
crw-rw---- 1 root lp 6, 0 2008-08-17 08:33 /dev/lp0
whitt@whitt-desktop:~$

I found out that the is for a terminal designation so I checked /dev/tty for its authorization:

whitt@whitt-desktop:~$ ls -l /dev/tty
crw-rw-rw- 1 root dialout 5, 0 2008-08-18 06:41 /dev/tty
whitt@whitt-desktop:~$

Hoping to get passed this denial of permission and or get better messages identifying the problem I set apparmor to complain mode for cups:
 
[sudo] password for whitt:
root@whitt-desktop:~# aa-complain(8)
-su: syntax error near unexpected token `8'
root@whitt-desktop:~# aa-complain
Please enter the program to switch to complain mode: cups
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
root@whitt-desktop:~#

I got another message:


Aug 25 16:07:34 whitt-desktop cupsd: Unable to open log file "/var/log/cups/error_log" - Permission denied

from:  user.log  25AUG2008

Now I have an additional problem.  This file has the following permission:

Properties

The problem is obvious.  The file that apparmor tried to put a message has root read/write, lpadmin has read only and others have no access at all, including apparmor.


Aug 25 16:07:34 whitt-desktop kernel: [36076.231729] audit(1219694854.763:3): type=1502 operation="inode_permission" requested_mask="::a" denied_mask="::a" name="/dev/tty" pid=14943 profile="/usr/sbin/cupsd" namespace="default"

Aug 25 16:50:53 whitt-desktop kernel: [38670.016816] audit(1219697453.323:4): type=1502 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=15615 profile="/usr/sbin/cupsd" namespace="default"

Both of these were from /var/log/messages

I have not set any device permissions and without a root logon I don't think I have set any permissions on the error_log data set.

My only conclusion is that Ubuntu does not want Desktop users and owners to be able to print anything.

I have attached Screen Shots of the properties of error_log and of System Information output.

I would like to thank all of you that responded to my questions.  I am sorry that I am so new at this that I didn't know what to ask.

I am sorry if I have wasted your time.  It looks like Ubuntu sent me a CD with a very confused CUPS implementation.  The one I have is Ubuntu 9.04 LTS Desktop Edition (64-bit).

---

