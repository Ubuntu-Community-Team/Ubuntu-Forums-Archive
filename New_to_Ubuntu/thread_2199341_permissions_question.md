---
title: "permissions question"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by francis.boterblom on 2014-01-13
**Operating system name and version**: Ubuntu server 12.04
**Version of smsd**:  3.1.15
**Smsd installed from**: sources 
**Name and model of a modem / phone**: Nokia E72-1
**Interface**:  USB 

Hello,

I have setup Open Monitoring Distribution (OMD) with installes Nagios and Check_mk amongst others.

With OMD you create a site that is running under a user.

Now when Check_MK is trying to sms i will get a error, becauseits running under the user of that site.
Running it using root permission is working fine.

the error i recieve when running as the user is the following:

chown: changing ownership of `/tmp/smsd_J9qzGi': Operation not permitted
Output: mktemp: failed to create file via template `/var/spool/sms/outgoing/send_XXXXXX': Permission denied
Output: mv: missing destination file operand after `/tmp/smsd_J9qzGi'

Now permissions under the linux is not my strongest point.


So i need your help [IMG]http://smstools3.kekekasvi.com/templates/default/smilies/razz.gif[/IMG] 

Now  i believe the changing owership error is the main error i need to  solve. But because i come from a Windows environment i do not know how  to procede solving this. And what the best practice is.

Any help is welcome.

---

### Post by TheFu on 2014-01-13
First, we need to know the userids involved. What does apache runas, what are the file owners and groups and what are the permissions for each?  In UNIX/Linux, most security comes back to file permissions, so I highly recommend spending the 30 minutes on a tutorial to learn them.  Google and youtuve have a bunch.  "linux file directory permission tutor" is the search I would use.

Be certain you test everything they show in the tutors. Nothing teaches like hands-on experience.

---

### Post by bab1 on 2014-01-13
> **francis.boterblom said:**
> Now  i believe the changing owership error is the main error i need to  solve. But because i come from a Windows environment i do not know how  to procede solving this. And what the best practice is.

Any help is welcome.

All of this is under /opt/omd.  The /opt/omd/sites directory holds all of the information. What is the name of the site that you created?  This name is also the user name and group name that the site should run under.  OMD should do this for you if the scrip you used to create the site was run correctly.

Post the terminal output of this command```
ls -l /opt/omd
```...this will provide us with the correct OMD structure and directory ownership.

---

### Post by francis.boterblom on 2014-01-14
Hello,

To answer the question of bab1 first:

```
cmk@UCMK-HHW:~$ ls -l /opt/omd/
total 12
drwxr-xr-x 2 root root 4096 Dec  9 20:09 apache
drwxr-xr-x 3 root root 4096 Dec  9 20:09 sites
drwxr-xr-x 3 root root 4096 Nov 14 03:24 versions
```

But i think this is more interesting:

```
cmk@UCMK-HHW:~$ ls -l /opt/omd/sites/
total 4
drwxr-xr-x 7 heerhugowaard heerhugowaard 4096 Dec 12 19:54 heerhugowaard
```

I have seen the tutorials, but some things are not explained in those tuts. I know how to change ownership for example, but changing the ownership of /tmp/ to user heerhugowaard for this example will limit me only to that user, if another needs acces to /tmp/ i am in trouble. So i am not grasping how i can solve that sort of permission issues. Probally because i thing to much the Microsoft way and overlook the simple answer.

Regards,

Francis

---

### Post by bab1 on 2014-01-14
> **francis.boterblom said:**
> Hello,

To answer the question of bab1 first:

```
cmk@UCMK-HHW:~$ ls -l /opt/omd/
total 12
drwxr-xr-x 2 root root 4096 Dec  9 20:09 apache
drwxr-xr-x 3 root root 4096 Dec  9 20:09 sites
drwxr-xr-x 3 root root 4096 Nov 14 03:24 versions
```

> 
This looks fine.  All users (others) have the rights to read and directory and interact (descend into) any directory.  The last right most r-x says so.


But i think this is more interesting:

```
cmk@UCMK-HHW:~$ ls -l /opt/omd/sites/
total 4
drwxr-xr-x 7 heerhugowaard heerhugowaard 4096 Dec 12 19:54 heerhugowaard
```

I have seen the tutorials, but some things are not explained in those tuts. I know how to change ownership for example, but changing the ownership of /tmp/ to user heerhugowaard for this example will limit me only to that user, if another needs acces to /tmp/ i am in trouble. 

Correct.  What is inside /opt/omd/sites/heerhugowaard?  Post the output of ```
ls -l /opt/omd/sites/heerhugowaard 
```...nextime use a shorter user/site name.  You will get real tired of heerhugowaard.  :-)
> 
So i am not grasping how i can solve that sort of permission issues. Probally because i thing to much the Microsoft way and overlook the simple answer.

Regards,

Francis
Let's see what you have for permissions on the tmp directory for the site of /opt/omd/sites/heerhugowaard and go from there.

---

### Post by francis.boterblom on 2014-01-14
Here you go..

```
cmk@UCMK-HHW:~$ ls -l /opt/omd/sites/heerhugowaard
total 16
lrwxrwxrwx  1 heerhugowaard heerhugowaard   11 Dec  9 20:09 bin -> version/bin
-rw-------  1 heerhugowaard heerhugowaard  639 Dec 12 12:47 dead.letter
drwxr-xr-x 25 heerhugowaard heerhugowaard 4096 Dec  9 21:39 etc
lrwxrwxrwx  1 heerhugowaard heerhugowaard   15 Dec  9 20:09 include -> version/include
lrwxrwxrwx  1 heerhugowaard heerhugowaard   11 Dec  9 20:09 lib -> version/lib
drwxr-xr-x  5 heerhugowaard heerhugowaard 4096 Dec  9 20:09 local
lrwxrwxrwx  1 heerhugowaard heerhugowaard   13 Dec  9 20:09 share -> version/share
drwxr-xr-x 14 heerhugowaard heerhugowaard  320 Jan 13 08:11 tmp
drwxr-xr-x 13 heerhugowaard heerhugowaard 4096 Dec  9 20:09 var
lrwxrwxrwx  1 heerhugowaard heerhugowaard   19 Dec  9 20:09 version -> ../../versions/1.00


```

The long name was maybe not a good choise ;)

What i thought that the error was about the /tmp not the /opt/omd/sites/heerhugowaard/tmp, so that makes things easier.

---

### Post by bab1 on 2014-01-14
> **francis.boterblom said:**
> Here you go..

```
cmk@UCMK-HHW:~$ ls -l /opt/omd/sites/heerhugowaard
total 16
lrwxrwxrwx  1 heerhugowaard heerhugowaard   11 Dec  9 20:09 bin -> version/bin
-rw-------  1 heerhugowaard heerhugowaard  639 Dec 12 12:47 dead.letter
drwxr-xr-x 25 heerhugowaard heerhugowaard 4096 Dec  9 21:39 etc
lrwxrwxrwx  1 heerhugowaard heerhugowaard   15 Dec  9 20:09 include -> version/include
lrwxrwxrwx  1 heerhugowaard heerhugowaard   11 Dec  9 20:09 lib -> version/lib
drwxr-xr-x  5 heerhugowaard heerhugowaard 4096 Dec  9 20:09 local
lrwxrwxrwx  1 heerhugowaard heerhugowaard   13 Dec  9 20:09 share -> version/share
drwxr-xr-x 14 heerhugowaard heerhugowaard  320 Jan 13 08:11 tmp
drwxr-xr-x 13 heerhugowaard heerhugowaard 4096 Dec  9 20:09 var
lrwxrwxrwx  1 heerhugowaard heerhugowaard   19 Dec  9 20:09 version -> ../../versions/1.00


```

The long name was maybe not a good choise ;)

What i thought that the error was about the /tmp not the /opt/omd/sites/heerhugowaard/tmp, so that makes things easier.

As you can see the user heerhugowaard already is the owner and group owner of the *tmp* directory ```
drwxr-xr-x 14 [COLOR="#FF0000"]heerhugowaard heerhugowaard[/COLOR]  320 Jan 13 08:11 tmp
``` 
What is in the *tmp* directory?   Post the output of ```
ls -l /opt/omd/sites/heerhugowaard/tmp
```.

Have you visited these sites?

[http://omdistro.org/doc/configuration_basics]("http://omdistro.org/doc/configuration_basics")

[http://mathias-kettner.com/checkmk_install_with_omd.html]("http://mathias-kettner.com/checkmk_install_with_omd.html")

---

### Post by francis.boterblom on 2014-01-14
Here the output:

```
cmk@UCMK-HHW:~$ sudo ls -l /opt/omd/sites/heerhugowaard/tmp
[sudo] password for cmk:
total 4
drwxr-xr-x 4 heerhugowaard heerhugowaard 100 Jan 13 08:11 apache
drwxr-xr-x 4 heerhugowaard heerhugowaard  80 Jan 13 08:11 check_mk
drwxr-xr-x 2 heerhugowaard heerhugowaard  40 Jan 13 08:11 dokuwiki
lrwxrwxrwx 1 heerhugowaard heerhugowaard   6 Jan 13 08:11 icinga -> nagios
drwxr-xr-x 2 heerhugowaard heerhugowaard  60 Jan 14 15:27 lock
drwxr-xr-x 4 heerhugowaard heerhugowaard 120 Jan 14 22:04 nagios
drwxrwxr-x 4 heerhugowaard heerhugowaard  80 Jan 13 08:11 nagvis
drwxr-xr-x 5 heerhugowaard heerhugowaard 100 Jan 13 08:11 php
drwxr-xr-x 5 heerhugowaard heerhugowaard 100 Jan 13 08:11 pnp4nagios
drwxr-xr-x 2 heerhugowaard heerhugowaard  40 Jan 13 08:11 rrdcached
-rw-r--r-- 1 heerhugowaard heerhugowaard   5 Jan 13 08:11 rrdcached.pid
drwxr-xr-x 3 heerhugowaard heerhugowaard 140 Jan 14 15:27 run
drwxr-xr-x 4 heerhugowaard heerhugowaard  80 Jan 13 08:11 shinken
drwxrwx--- 3 heerhugowaard heerhugowaard  60 Jan 13 08:11 thruk


```

I am going to read the links you posted although i have been on the websites several times espescially the check_mk site.

---

### Post by bab1 on 2014-01-14
Why are you using sudo?  ```
sudo ls -l /opt/omd/sites/heerhugowaard/tmp
```

Did you use sudo to create this site?


Additional thoughts: 

Permissions are provided for:  the owner(creator), the group and all others.  And example of read, write and execute would look like this: rwx.  To apply that to the user, group, others looks like this: [COLOR="#FF0000"]rwx[/COLOR][COLOR="#0000FF"]rwx[/COLOR][COLOR="#008000"]rwx[/COLOR]

The files in tmp show that the owner has rwx and the group has r-x (read and execute).  Even the others (everyone) has r-x.

If I see anything that looks unusual it would be that the default permissions for an Ubuntu 12.04 system should be: rw-rw-r-- this would be a umask of 0002.  post the output of```
umask
```...this will show the default umask.

Are you running this site as the user heerhugowaard?

---

### Post by francis.boterblom on 2014-01-15
I am logged in as user cmk, the use of sudo is sometimes nessecary for doing some root user stuff.
For the ls command i do not need sudo , it is just a habbit i typed sudo in this case.

```
cmk@UCMK-HHW:~$ umask
0002

```

Yes this site is running as user heerhugowaard, check_mk is running a notification script sms that calls sendsms, if i run this as user heerhugowaard i get the same errors.

```
cmk@UCMK-HHW:~$ sudo su heerhugowaard
[sudo] password for cmk:
OMD[heerhugowaard]:~$ sendsms
Destination(s): xxxxxxxxxx
Text: test 900
--
Text: test 900
To: xxxxxxxxx
chown: changing ownership of `/tmp/smsd_kLXSe2': Operation not permitted
mktemp: failed to create file via template `/var/spool/sms/outgoing/send_XXXXXX': Permission denied
mv: missing destination file operand after `/tmp/smsd_kLXSe2'
Try `mv --help' for more information.
```

---

### Post by francis.boterblom on 2014-01-15
ok, changing the tmp of site heerhugowaard from 755 to 775 makes it work, sms is send out correctly.
Is this ok todo, security wise?

---

### Post by francis.boterblom on 2014-01-15
hmm after reboot the permission of tmp are put back to 755.
but even worse, changing agian to 775, is giving the same errors again....

frustrating

---

### Post by bab1 on 2014-01-15
> **francis.boterblom said:**
> I am logged in as user cmk, the use of sudo is sometimes nessecary for doing some root user stuff.
For the ls command i do not need sudo , it is just a habbit i typed sudo in this case.

I understand.
> 

```
cmk@UCMK-HHW:~$ umask
0002

```

This is correct.
> 

Yes this site is running as user heerhugowaard, check_mk is running a notification script sms that calls sendsms, if i run this as user heerhugowaard i get the same errors.

```
cmk@UCMK-HHW:~$ sudo su heerhugowaard
[sudo] password for cmk:
OMD[heerhugowaard]:~$ sendsms
Destination(s): xxxxxxxxxx
Text: test 900
--
Text: test 900
To: xxxxxxxxx
chown: changing ownership of `/tmp/smsd_kLXSe2': Operation not permitted
mktemp: failed to create file via template `/var/spool/sms/outgoing/send_XXXXXX': Permission denied
mv: missing destination file operand after `/tmp/smsd_kLXSe2'
Try `mv --help' for more information.
```
I think the problem is with OMD.  Since the user heerhugowaard already owns everything in /opt/omd/sites/heerhugowaard and the permissions are already read, write and execute you should not have this error.  The error messages are standard error messages for chown and mktemp and are correct.  I would talk to the folks at OMD for a solution.  It looks like there is a bug in their code.

---

