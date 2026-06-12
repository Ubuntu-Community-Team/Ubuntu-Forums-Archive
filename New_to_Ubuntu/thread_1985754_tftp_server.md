---
title: "tftp server"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by fathercisco on 2012-05-23
Hi All

Am very new to ubuntu and am looking to set up a tftp server to aid me with my CCNA studies, i have followed several guides on how to do this and have had results from not working at all to error code 2.
I am sure this is due to user error but would appreciate any help anybody can give.

Regards
Fathercisco

---

### Post by ikt on 2012-05-24
Do you get stuck through this?

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

Is there anything specific which is not happening?

---

### Post by fathercisco on 2012-05-24
Hi

Thank you for your reply, that is the guide i was using and to be honest the first few times nothing happened at all !!.
Now all i have is error code 2 access violation permission denied.
I have tried creating the file initially in /etc/var/tftpboot and changing the permissions as suggested in another guide (not sure which one i have tried a few) but to no avail.
Any help you can give would be greatly received thank you in advance.

---

### Post by andrebreiler on 2012-05-24
> **fathercisco said:**
> 
Now all i have is error code 2 access violation permission denied.
I have tried creating the file initially in /etc/var/tftpboot and changing the permissions as 

Could you please quote the command you are running including the output ?
(are you running it from a cisco device or from a host ?)

In addition can you please verify a few things:

[LIST=1]
[*]Which tftpd is installed ? ```
dpkg -l '*tftpd*' | grep '^i'
``` (it will list all packages with "tftpd" in the name and then filter only installed ones ["i" as first character on a line in the output of dpkg means "installed"]).
 There is more than one tftpd available in ubuntu and all have a slight different behavior so it is best to make sure that all posts refer to the same implementation.
[*]Can you provide the xinetd configuration file please ?
 If you followed the guide mentioned then it should be /etc/xinetd.d/tftp .
 Specifically I'm interested in the server_args and disable/enable lines. I suspect that you have a ```
server_args     = /tftpboot
``` line in as given in the guide.This will mean that you need to put all the files to be handled into /tftpboot (not /etc/var/tftpboot nor /var/lib/tftpboot).
[*]can you please provide a long listing of the tftpboot directory ```
ls -la /tftpboot
``` Some implementations of tftpd do check that the files are owned by the nobody user, are readable by everyone, and are not symbolic links (these are common reasons for permission denied).
[/LIST]
Enjoy you CCNA :)

---

### Post by fathercisco on 2012-05-31
Hi 

Sorry for taking so long to get back to you after your very quick offer of help, i have been snowed under at work and barely had time to think!
It will be a couple of days before i am back in front of the machine in question.
However i can confirm that i have altered the server_args to /var/lib/tftpboot
I would like to ask the following.
I am using Mediatomb and have two internal hdd's so far all is well except when i try to use the second hdd i keep getting a unable to list directory /media/a : permission denied.
Again i apologise for the change in question but i am unable to confirm from memory the configuration.

Any help you could give with the other problem would be greatly appreciated and thank you in advance;

---

### Post by andrebreiler on 2012-06-05
> **fathercisco said:**
> 

Sorry for taking so long to get back to you after your very quick offer of help, i have been snowed under at work and barely had time to think!;

Sounds somehow familiar ...
Anyway, no worries. Take your time.

> **fathercisco said:**
> 
However i can confirm that i have altered the server_args to /var/lib/tftpboot;

In this case can you plese get a listing of /var/lib/tftpboot please.

> **fathercisco said:**
> 
I am using Mediatomb and have two internal hdd's so far all is well except when i try to use the second hdd i keep getting a unable to list directory /media/a : permission denied.;

That sounds to me like the disks (permissions/ownerships) are not set so that the mediatomb user can access the content of the disks.
(is it some external disk which gets plugged in and therefore assigned the permissions of the currently logged in user ?)

However I'd suggest asking the question either in a thread discussing this already or in a new thread so it can be easily found.
One thread which looks like it could be applicable to you is [http://ubuntuforums.org/showthread.php?t=1373939&highlight=mediatomb+permissions](http://ubuntuforums.org/showthread.php?t=1373939&highlight=mediatomb+permissions) .

---

### Post by fathercisco on 2012-06-05
Hi

Thank you for your patience i will be able to get the listings off the box in question tonight.
I do appreciate your help because this has me completly stumped!!!!

---

