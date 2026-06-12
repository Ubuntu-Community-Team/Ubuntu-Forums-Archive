---
title: "chown command"
date: 2020-03-25
forum: New to Ubuntu
---

### Post by skybird182 on 2020-03-25
In my Linux exam book the statement is made that **chown** can do the following but no syntax given:

[LIST=1]
[*]make new group 
[*]change owner and group at the same time 
[/LIST]

As an example:
[LIST=1]
[*]new group (lab) is created 
[*]give the new group (lab) and an owner (xyz) access to the file (new-file). 
[/LIST]

new group - lab
add owner  - xyz
new-file (file name to receive new permissions)

What is the chown command to do this ?

Thanks

---

### Post by yancek on 2020-03-25
There are countless web sites with detailed explanations of using the chown command such as the one below.  An online search should provide you with all the information you need.

[https://linuxize.com/post/linux-chown-command/](https://linuxize.com/post/linux-chown-command/)

---

### Post by GhX6GZMB on 2020-03-25
> **skybird182 said:**
> In my Linux exam book the statement is made that **chown** can do the following but no syntax given:

[LIST=1]
[*]make new group
[*]change owner and group at the same time
[/LIST]


2. is correct, 1. is to my knowledge _not_ correct.

[https://linux.die.net/man/1/chown](https://linux.die.net/man/1/chown)

---

### Post by skybird182 on 2020-03-25
I looked at websites to find an example before posting.

---

### Post by TheFu on 2020-03-25
If you want to learn this stuff, here's a reference: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
It is a no-hassle download. Nothing to sign up to get. No email to provide. Grab the boot in your preferred language.

Plus, every Unix system has local manpages.  If you are going to work at the shell or CLI, you'll **NEED** to learn to use the manpages.

```
$ man chmod
```

To search the tiny, 1-line summary for every command, use **apropos**
```
$ apropos chown
```
This will return all the manpages with that term. Not all manpages are for commands. Some are for configuration files, so we often need to specify exactly which manpage section to be shown.
On one of my systems, 
```
$ apropos passwd
chgpasswd (8)        - update group passwords in batch mode
chpasswd (8)         - update passwords in batch mode
fgetpwent_r (3)      - get passwd file entry reentrantly
getpwent_r (3)       - get passwd file entry reentrantly
gpasswd (1)          - administer /etc/group and /etc/gshadow
grub-mkpasswd-pbkdf2 (1) - generate hashed password for GRUB
mkpasswd (1)         - Overfeatured front end to crypt(3)
mksmbpasswd (8)      - formats a /etc/passwd entry for a smbpasswd file
pam_localuser (8)    - require users to be listed in /etc/passwd
passwd (1)           - change user password
passwd (1ssl)        - compute password hashes
passwd (5)           - the password file
passwd2des (3)       - RFS password encryption
smbpasswd (5)        - The Samba encrypted password file
smbpasswd (8)        - change a user's SMB password
SSL_CTX_set_default_passwd_cb (3ssl) - set passwd callback for encrypted PEM file handling
SSL_CTX_set_default_passwd_cb_userdata (3ssl) - set passwd callback for encrypted PEM file handling
update-passwd (8)    - safely update /etc/passwd, /etc/shadow and /etc/group
vnc4passwd (1)       - change a VNC password
vncpasswd (1)        - change a VNC password

```
There are 3 lines returned with just "passwd".  It is handy to understand the passwd DB/config file organization. That is documented in section ... 5.
If we use **man passwd**, then the first found section will be shown - section 1, for the command.  To see section 5, 
```
$ man -s 5 passwd
```

Anyway, you'll need to learn to use manpages so there isn't any need to wait for someone on a forum to sorta answer the question, but not really answer it at all.  

*It is against the rules to do someone's homework in these forums.*  We certainly won't answer test questions.

---

### Post by GhX6GZMB on 2020-03-25
Normal syntax would be

sudo chown [options] xyz:lab [file]. A typical option would be -R if [file] is a directory.

---

### Post by coffeecat on 2020-03-25
> **skybird182 said:**
> 
What is the chown command to do this ?


From the [posting guidelines,]("https://ubuntuforums.org/showthread.php?t=2158945") which are part of the [forum rules]("https://ubuntuforums.org/misc.php?do=showrules"):

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service.

---

### Post by skybird182 on 2020-03-25
This is what I got when I tried the above command: new-file is a file

Is an option missing ?

sudo chown xyz:lab new-file
chown: invalid user: ‘xyz:lab’

---

### Post by skybird182 on 2020-03-25
This is very helpful. Thanks

---

### Post by TheFu on 2020-03-25
> **skybird182 said:**
> This is what I got when I tried the above command: new-file is a file

Is an option missing ?

sudo chown xyz:lab new-file
chown: invalid user: ‘xyz:lab’

xyz:lab is **username:groupname**
Both must exist as shown in the command.

BTW, xyz.lab is also an acceptable way to say username.groupname. Old Unix terminals didn't have a ':' character, so the '.' can be used.

So, *thefu:users* or *thefu:audio* might be clearer examples.

"new-file" must exist too. To create an empty file, use the '**touch**' command.
The book link provided above has a chapter on Unix permissions.

---

### Post by skybird182 on 2020-03-25
This is very helpful. Thanks

---

### Post by skybird182 on 2020-03-25
Thanks for the info. Not sure why my book says it can be done. Maybe other distros allow this. I am thinking this capability would bypass the useradd command.

---

### Post by TheFu on 2020-03-26
> **skybird182 said:**
> Thanks for the info. Not sure why my book says it can be done. Maybe other distros allow this. I am thinking this capability would bypass the useradd command.

There was a history of slightly different commands between the different Unixen, because each company wrote their own.  There's a reason the GNU guys think we shouldn't call Linux anything except "GNU/Linux", that's because they are all using the GNU versions of user-land tools.  So, pretty much regardless of the Linux distro, the ls command is from GNU and behaves the same way, unless some other specific default feature is enabled which doesn't allow that.

99.99% of the time, Linux is Linux, except when we use specific system admin commands that are distro specific.  For example, Ubuntu has AppArmor, but RHEL uses SELinux instead.  So the commands for apparmor are specific to Ubuntu (and child distros) and the commands for SELinux are specific to RHEL (and child distros for it).  There is a graphic on Wikipedia that shows the relationships between many (200+?) Linux distros.  Most normal people have no idea about that.

So ... what does all this mean?  Basically, chmod is chmod on any Linux distro if the same version of the command is being used on both distros.  Check the version for most commands, but using a --version option.  Commands do change over time.
```
$ chmod --version
```
Sometimes the option is -v or -V. Always remember that Unix is case sensitive.  -v also gets used to add "verbosity" to the output of some commands.  More "v"s gets more verbose output which can help troubleshoot problems.  That is mostly used by client/server commands, like ssh.   *ssh -vvvv userid@remote* would produce 4 levels of verbosity. Sometimes very handy.

I remember when the -h option became available for **du**, **df**, and **sort** commands.  Completely changed my world.  I'll leave that for you to look up and understand.  Some commands seem to never change, er ... until they do.

Other commands seem to change for the worse.
**ifconfig** and **route** make nice output, but have been replaced with **ip {option}** which makes ugly output. Nice output that is easy to read should be the default. Ugly output, good for scripting, should require an option.  IMHO.

Get a better book.  I'd be suspect of other things in that book, since the publisher didn't round up a sufficient review and editorial staff to catch a mistake.

Or you misread/misunderstood the book.  Realistically, that's probably more likely. ;)

---

### Post by kevdog on 2020-03-26
To my knowledge chown can not create a new group.

---

