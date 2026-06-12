---
title: "sudo password doesn't work"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by peterson43 on 2011-12-12
I'm running Ubuntu 10.04 on my laptop, and today when I tried to run update-manager it wouldn't install the updates since it wouldn't accept my password for the root. I tried running other commands (both with gui programs and with the terminal) that required me to enter my root password. None of them worked. I don't see how I could have accidentally changed my root password. Is there any way to fix this?

---

### Post by lechien73 on 2011-12-12
Is your system set to automatically log you in? If not, then the sudo password is the same as your log-in password.

If this is the password you've forgotten, then here's how to reset it:

[LIST]
[*]Reboot the machine
[*]After the power on self-test screen, press and hold the Shift key
[*]When the Grub boot menu comes up, select to boot Ubuntu in Recovery Mode.
[*]At the Recovery Mode menu, choose to drop to a root shell.
[*]At the prompt, type:
[/LIST]

```
passwd your-user-name
```

[INDENT]Obviously replace *your-user-name* with your Ubuntu username.[/INDENT]
[LIST]
[*]Choose a new password
[*]Reboot the PC.
[/LIST]

---

### Post by BC59 on 2011-12-12
Boot into recovery mode-->Drop to root shell prompt and then run:

```
ls /home
```

```
passwd put_here_your_username
```

You'll then be prompted for a new password

```
exit
```

then choose normal boot

---

### Post by Rex Bouwense on 2011-12-12
Before you change your password, make sure that your Caps Lock is not on.  Linux is case sensitive.

---

### Post by peterson43 on 2011-12-12
> **lechien73 said:**
> Is your system set to automatically log you in? If not, then the sudo password is the same as your log-in password.


I do not log in automatically, so my sudo password should be the same still. Any ideas why it might not be working?

---

### Post by lechien73 on 2011-12-12
Strange...then that might indicate a problem with either the /etc/sudoers file, or your group membership.

If you type:

```
groups
```

from within a terminal window, then are you listed as a member of the admin group?

If you type:

```
ls -l /etc/sudoers
```

Then are the permissions set to:

```
-r--r-----
```

---

### Post by peterson43 on 2011-12-13
> **lechien73 said:**
> Strange...then that might indicate a problem with either the /etc/sudoers file, or your group membership.

If you type:

```
groups
```

from within a terminal window, then are you listed as a member of the admin group?

If you type:

```
ls -l /etc/sudoers
```

Then are the permissions set to:

```
-r--r-----
```
Yes it would appear that I am listed as a member of the 'admin' group. 

I also checked that the permissions of /etc/sudoers were set correctly and they were. However, if I try to open up that file in a text editor it asks for my password and then doesn't accept the password. 

The really strange thing is that my password works for logging in but not for getting super-user privileges.

---

### Post by lisati on 2011-12-13
The password is usually hidden. When you're typing it in using the terminal, it might look like it's not being accepted: don't panic, just type it in as usual and press "Enter".

---

### Post by peterson43 on 2011-12-13
> **lisati said:**
> The password is usually hidden. When you're typing it in using the terminal, it might look like it's not being accepted: don't panic, just type it in as usual and press "Enter".
This is not the problem. I've been a Linux user for a while now, so I know how entering passwords works. After I enter the password it says "Sorry, try again."

---

### Post by fdrake on 2011-12-13
2 cases possible:
1- you are in the admin group but sudoers has restrictions for your username, login as root and check the content
```
less /etc/sudoers
```
you should see sometjing like this:
> root    ALL=(ALL) ALL
.......
%sudo ALL=(ALL) ALL
.......
%admin ALL=(ALL) ALL

2-sudo program may be corrupted, suggest you to login as root and reinstall it!

---

### Post by CoffeeRain on 2011-12-13
Could it be that you are trying to use sudo logged in as a non sudoer? I've done that before. Even if you know the sudo password, you can't sudo if you aren't logged in as the sudoer.

---

### Post by lechien73 on 2011-12-13
Since you can't sudo, you're a bit stuck for checking the contents of the /etc/sudoers file.

So, boot into Recovery Mode, as I mentioned in an earlier message, and see what /etc/sudoers says from there. You could also check the contents of the /etc/sudoers.d directory, which is usually empty apart from the README file.

Mine (which hasn't been changed from the default) looks like this:

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
```

---

### Post by peterson43 on 2011-12-13
> **fdrake said:**
> 2 cases possible:
1- you are in the admin group but sudoers has restrictions for your username, login as root and check the content
```
less /etc/sudoers
```
you should see sometjing like this:

2-sudo program may be corrupted, suggest you to login as root and reinstall it!

I am not able to check your first suggestion since viewing that file requires me to enter the admin password that the system isn't accepting. 

Regarding your second suggestion, how do I 
a) log in as root (especially since my sudo password isn't working)
b) reinstall sudo

---

### Post by peterson43 on 2011-12-13
> **CoffeeRain said:**
> Could it be that you are trying to use sudo logged in as a non sudoer? I've done that before. Even if you know the sudo password, you can't sudo if you aren't logged in as the sudoer.
No that's not it. I'm logged in as the sudoer. I even tried logging in with my wifes account thinking that somehow she got switched to the sudoer. It still didn't work.

---

### Post by CoffeeRain on 2011-12-13
You would have to log in to [recovery mode]("https://wiki.ubuntu.com/RecoveryMode").

---

### Post by peterson43 on 2011-12-13
Okay, I logged in with recovery mode and was able to view my /etc/sudoers file. 

What I think must be the relevant parts of that file are

```

%sudo ALL=NOPASSWD: ALL
.....
root   ALL=(ALL) ALL
.....
%admin ALL=(ALL) ALL
%admin ALL=NOPASSWD: /usr/bin/setkeycodes


```

This looks somewhat different than what others have posted, but are the differences causing problems or is it something else?

---

### Post by MartijnNL on 2011-12-14
Is your password accepted when you do something else which requires root privileges, like running Synaptic or editing users. If so, try re-installing sudo from synaptic.

Did you at some point in the past edit the /etc/sudoers file? And if so, did you do it using visudo or did you edit it directly? You should always edit this file using visudo only.

I do not have a desktop version of 10.04 available at this moment (I have one at home), but my 10.04 server and Xubuntu 11.10 desktop both have the /etc/sudoers file as posted by lechien73 above. So it seems like you have a non-default file. But I'm not sure the lines you posted cause the problem.

The last line seems to be intended for some screen rotation script (when I google it). But it seems to be valid. The %sudo line is overruled for by the first %admin line for all users in the admin group.

Also just for testing: could you type you password into a text file and then paste it using Ctrl-Shift-V at the password prompt, and then hit enter. Just to make sure it's not something to do with a wrong character set or something like that.

---

### Post by lechien73 on 2011-12-14
I've just checked a stock 10.04 installation, and the /etc/sudoers file is pretty much the same as the one I've posted above.

If you're not using a tablet PC, or needing screen rotation, then I'd suggest resetting everything to defaults by using:

```
visudo
```

This would mean changing: 

```
%sudo ALL=NOPASSWD: ALL
```
back to:

```
%sudo ALL=(ALL) ALL
```

And removing:

```
%admin ALL=NOPASSWD: /usr/bin/setkeycodes
```

Also, it might be a good idea to change the Defaults line to read:

```
Defaults        env_reset,pwfeedback
```

This will enable you to see your password as you're typing it - just to make sure that sudo isn't interpreting the characters strangely.

Finally confirm that the permissions on /etc/sudoers haven't changed, and then try rebooting. :)

---

### Post by peterson43 on 2012-01-13
It's been a while since I messed with my computer trying to get the sudo privileges to work again since that's not my primary computer. I do use it somewhat often though and so I want to get it working again. 

I am using a tablet PC with screen rotation, so that is probably why my /etc/sudoers file looks different than others. I haven't changed anything regarding the screen rotation stuff for a long time. 

I tried something else today. I switched to recovery mode so that I could add another user to the admin group. That seemed to work successfully, but when I log in as that other user I still can't get sudo to work. It seems there's something broken with the sudo files/program itself. 

Any new ideas from people?

---

### Post by MartijnNL on 2012-01-19
Did you try my earlier suggestion?

> Is your password accepted when you do something else which requires root privileges, like running Synaptic or editing users. If so, try re-installing sudo from synaptic.

---

### Post by peterson43 on 2012-01-21
Okay, I finally gave up and just did a fresh installation of Ubuntu (11.10) on my computer. Seems to work much better now. I'll mark the thread as "solved" even though I never really fixed things, just scrapped the whole installation and put in a new one.

---

### Post by cobaltinfinity on 2013-04-15
I just had a problem with this and it was all because I used the '2' key with Shift in my password on an Apple keyboard - this is an @ sign on the physical keyboard but on the keyboard layout I had selected it was considered to be a " (i.e. speech mark) key. This wasn't a problem for my user login, but the sudo password (which is obviously set during install) made me find the " key on the Apple keyboard (i.e. next to backslash).



**EDIT: Sorry I just mega-bumped this post, didn't I? :eek: :eek: :eek:**

---

### Post by wildmanne39 on 2013-04-15
Thread closed. Please do not post in old threads.

---

