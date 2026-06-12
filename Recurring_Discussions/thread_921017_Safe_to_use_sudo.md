---
title: "Safe to use sudo?"
date: 2008-09-15
forum: Recurring Discussions
---

### Post by SSVegito888 on 2008-09-15
1. Is using sudo considered the same thing as logging in as root?


2. Is it safe to use sudo?

3. Also, if you have to is it safer to use su or sudo?




Thanks,

SSvegito888

---

### Post by aysiu on 2008-09-15
*sudo* allows you to temporarily escalate to root-like privileges (after a password authentication) for a particular task.

Logging in as root makes you semi-permanently (until you log out) root on every application you run and with no password authentication (except when you log in) for any task.

So the answer is **No** it isn't the same as logging in as root, and **yes** it is safe.

**su** without a particular user specified prompts you to log in as root

**sudo** allows you to escalate privileges for a particular command but keeps you logged in as the current user

---

### Post by Jive Turkey on 2008-09-15
In ubuntu and I think in debian too it is the preferred way to do tasks that require more privileges/access that the user normally has.  In some other distros su or logging in as root may be the preferred way.

As far as "safe" you can hose your system with a single command using sudo or su or any other "as root" type of action, be careful and know what you are doing.  I believe you can wipe your whole filesystem with a single typo in some circumstances.  I havent tried it.

---

### Post by cardinals_fan on 2008-09-15
I personally consider "sudo" less safe than "su", especially with the default 15?-minute timeout in Ubuntu.  Since almost all malware relies on social engineering (in which the user makes the error) to run, the safest system provides said malware no way to run as administrator.  Allowing a program to request root privileges hands the user an opportunity to screw up.  The default timeout is incredibly dangerous - if malware runs "gksudo" less than 15? minutes after the last authorization, it can do whatever it likes with no password prompt.

On my nice, secure box with "su", the only way for an app to run as root is if I execute it from within the root shell, which I exit as soon as I'm done administering the system.

Just my 2¢

---

### Post by deijsman on 2008-09-15
sudo is the best method, unless you have a lot of work to do as root.

Some tips - you should be using sudo only when you *must*

If you are trying to do some task that shouldn't require root privileges and it works with sudo, you are better off making it work with your admin user.  

sudo or su can easily wreck a system...

---

### Post by amac777 on 2008-09-15
To get a complete answer, please read this page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Short answers:
1. The safety of sudo depends on the command you are trying to exectue. sudo gives the command the full administrator power so if you use sudo with a command to delete all files on the system, I would consider that to be not safe. Be careful when you use sudo.

2. By default, su cannot be used on Ubuntu because the root account is disabled.

---

### Post by cardinals_fan on 2008-09-15
To expound a bit on my earlier post:

Sudo is, in and of itself, **not** a security risk.  Yes, it allows a program to request root privileges, but the user still has to sign off on the action.  The major security issue is the default sudo timeout employed in Ubuntu.  That allows a program to obtain root privileges **without the user's knowledge/permission**.  I consider that a major security flaw in the default Ubuntu installation.

---

### Post by niccholaspage on 2008-09-15
sudo is safe now knowing that the code to delete the file system does not work anymore.
Or At least it won't work on my system.

---

### Post by SSVegito888 on 2008-09-15
I am probably going to modify the sudoers file to ask for my password every time by adding the following line to the end of /etc/sudoers :


Defaults:ALL timestamp_timeout=0




Any sugestions on how do to do this safely will be greatly appreciated.




PS: I have login as root disabled.

---

### Post by cardinals_fan on 2008-09-15
> **SSVegito888 said:**
> I am probably going to modify the sudoers file to ask for my password every time by adding the following line to the end of /etc/sudoers :


Defaults:ALL timestamp_timeout=0




Any sugestions on how do to do this safely will be greatly appreciated.




PS: I have login as root disabled.
A great idea!  Just enter "sudo visudo", use the down arrow to find that line, the right arrow to highlight the number, "x" to delete one of the digits, "r" to enable replace, "0" to replace the number, "Esc" to go back to command mode, and, if you're SURE everything looks good, ":wq" to write and quit.  If you screw up, ":q!" will quit without saving changes.

EDIT: This thread says it well: [http://ubuntuforums.org/showthread.php?p=116697#post116697](http://ubuntuforums.org/showthread.php?p=116697#post116697)

---

### Post by SSVegito888 on 2008-09-15
One more thing, When I installed Ubuntu 8.04 Hardy on my Desktop PC, I was instructed to create a Username and password.



This is the only user on the system besides root (DISABLED)


This user is set to administer the system **but is not root.**

When I want to do something that requires root privlidges, I still have to enter my password.


Oh, and my password is about 20 characters.


Is all of this safe to do?

---

### Post by cardinals_fan on 2008-09-15
> **SSVegito888 said:**
> One more thing, When I installed Ubuntu 8.04 Hardy on my Desktop PC, I was instructed to create a Username and password.



This is the only user on the system besides root (DISABLED)


This user is set to administer the system **but is not root.**

When I want to do something that requires root privlidges, I still have to enter my password.


Oh, and my password is about 20 characters.


Is all of this safe to do?
Yes.  Just make sure that the timeout is set to zero.

EDIT: Remember, security is up to the user, not the OS.  If you blindly grant any program root permissions, you might as well run as root.  Be cautious and you'll do fine :)

---

### Post by SSVegito888 on 2008-09-15
Thanks!!!

---

