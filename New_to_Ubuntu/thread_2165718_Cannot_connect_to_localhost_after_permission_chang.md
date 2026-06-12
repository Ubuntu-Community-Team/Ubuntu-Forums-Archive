---
title: "Cannot connect to localhost after permission change"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by 1888software on 2013-08-06
Localhost apache2 webserver WAS running ok on Ubuntu 13.04.
I changed permission on[COLOR=#008000] /var/www/[/COLOR] so that I could access it with my non root account. It's a standalone server used only by myself for testing.
Now localhost does not run at all :(
[COLOR=#008000]Ping localhost shows server IS running.[/COLOR]

The browser error is: 

[B][COLOR=#ff0000]Unable to connect
Firefox can't establish a connection to the server at localhost.[/COLOR][/B]

What should I be checking to resolve this?

With thanks.

---

### Post by linuxonbute on 2013-08-06
What user did you change it to?
post the results of 
```

ls -l /var

```
and 
```

ls -l /var/www

```

---

### Post by 1888software on 2013-08-06
laptop@ubuntu-VPCEE43FX:~$ ls -l /var 
 total 52 
 drwxr-xr-x  2 root   root     4096 Aug  5 07:52 backups 
 drwxr-xr-x 18 root   root     4096 May  8 21:16 cache 
 drwxrwsrwt  2 root   whoopsie 4096 Aug  4 05:26 crash 
 drwxr-xr-x  2 root   root     4096 Jan 22  2013 games 
 drwxr-xr-x 66 root   root     4096 Jul 26 11:42 lib 
 drwxrwsr-x  2 root   staff    4096 Oct  9  2012 local 
 lrwxrwxrwx  1 root   root        9 Aug  2 06:32 lock -> /run/lock 
 drwxr-xr-x 17 root   root     4096 Aug  5 07:52 log 
 drwxrwsr-x  2 root   mail     4096 Oct 17  2012 mail 
 drwxrwsrwt  2 root   whoopsie 4096 Oct 17  2012 metrics 
 drwxr-xr-x  2 root   root     4096 Oct 17  2012 opt 
 lrwxrwxrwx  1 root   root        4 Aug  2 06:32 run -> /run 
 drwxr-xr-x  9 root   root     4096 May 25 01:12 spool 
 drwxrwxrwt  2 root   root     4096 Aug  5 23:44 tmp 
 drwxr-xr-x  4 laptop root     4096 Aug  4 18:41 www 
 

 

 laptop@ubuntu-VPCEE43FX:~$ ls -l /var/www 
 total 12 
 drwxrwxr-x 4 laptop laptop 4096 Aug  4 05:09 1888software.com 
 drwxrwxr-x 2 laptop ubuntu 4096 Aug  4 01:35 folder1 
 -rw-r--r-- 1 laptop root    194 Aug  4 04:58 index.html

---

### Post by linuxonbute on 2013-08-06
Not sure exactly how much you will need to do.

So first just try
```

sudo chown www-data.www-data /var/www

```
and see if that is enough.

---

### Post by 1888software on 2013-08-06
When I logged in as superuser to make the change [COLOR=#ff0000]Ubuntu threw two errors[/COLOR]. I authorized sending the reports, launched Firefox, typed in localhost and nada:

[B][COLOR=#ff0000]Unable to connect
Firefox can't establish a connection to the server at localhost.[/COLOR][/B]

Over to you. With thanks for your help!

---

### Post by linuxonbute on 2013-08-06
What were the errors?
Did the change of user take place anyway?
Try
```

ls -l /var

```

---

### Post by 1888software on 2013-08-06
I didn't write the errors down, I get so many... almost everytime I logon as superuser there are Ubuntu errors...

I no longer see laptop as a user. This is the non root user I need to run the files under, so I can work without working as root.

ubuntu@ubuntu-VPCEE43FX:~$ sudo chown www-data.www-data /var/www
[sudo] password for ubuntu: 
ubuntu@ubuntu-VPCEE43FX:~$ ls -l /var
total 52
drwxr-xr-x  2 root     root     4096 Aug  5 07:52 backups
drwxr-xr-x 18 root     root     4096 May  8 21:16 cache
drwxrwsrwt  2 root     whoopsie 4096 Aug  6 00:06 crash
drwxr-xr-x  2 root     root     4096 Jan 22  2013 games
drwxr-xr-x 66 root     root     4096 Jul 26 11:42 lib
drwxrwsr-x  2 root     staff    4096 Oct  9  2012 local
lrwxrwxrwx  1 root     root        9 Aug  2 06:32 lock -> /run/lock
drwxr-xr-x 17 root     root     4096 Aug  6 00:03 log
drwxrwsr-x  2 root     mail     4096 Oct 17  2012 mail
drwxrwsrwt  2 root     whoopsie 4096 Oct 17  2012 metrics
drwxr-xr-x  2 root     root     4096 Oct 17  2012 opt
lrwxrwxrwx  1 root     root        4 Aug  2 06:32 run -> /run
drwxr-xr-x  9 root     root     4096 May 25 01:12 spool
drwxrwxrwt  2 root     root     4096 Aug  6 00:17 tmp
drwxr-xr-x  4 www-data www-data 4096 Aug  4 18:41 www


Over to you [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar10274_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=10274") 				 				 					 						 	[**[COLOR=#000000]linuxonbute[/COLOR]**]("http://ubuntuforums.org/member.php?u=10274")

---

### Post by 1888software on 2013-08-06
linuxonbute,
It is past midnite here on the West Coast of Canada.
I am logging off to get some sleep.
I will check in when I wake up.
Thank you very much for your assistance so far, i appreciate it.
ps also see my private message
1888software

---

### Post by linuxonbute on 2013-08-06
The change you made which caused the problem was
chown laptop.root /var/www
this changed the user ( Read as OWNER ) to laptop
and the group to root.
So you have given group called root access to it.
This is not how to set it up.
Did you understand this?

On my system it is www-data.www-data
so the owner is www-data
and the group is www-data

Now on my system www-data is the default user
and www-data is the default group
I expect this was true of yours.

>>> They are not the same entity <<<

To access the localhost web page I need to be a member of the www-data group.

Okay, let's do a few more checks.
run the following commands as your normal user
and post the results
>>>> WARNING <<<<
posting these results gives hackers some knowledge of your system.
If you are not happy for this to happen then send me a private message instead.
```

whoami

groups

cat /etc/groups|grep www-data

```

---

### Post by 1888software on 2013-08-07
Thank you for your reply.

I marked the other helper's reply as solved because I respect and appreciate the gratuitous help supplied by any user. The advice DID run in my terminal without error. However, it may have given me a new problem - I don't know, I'm just a newbie. I do not even know how to create a group, or what I would use one for if I did.

Since I have been recently hacked (on windows) on multiple days I will post whoami info to private message.

Thanks again for your help. Over to you linuxonbute.

---

### Post by 1888software on 2013-08-07
To answer the outstanding questions:

a. no I did not understand what I was doing
b. to the best of my knowledge yes www-data was the default setup

root is the superuser
laptop is the non-root user

I need to be able to work as the user called "laptop".
"laptop" needs read write - all - access to files in the /var/www/ folder or 
alternatively somehow it needs to be setup so that I can easily copy edit and move files logged in as "laptop"

My undertstanding is that it is NOT a good idea to login and work as root. That's why I think I should use "laptop".

WhoamI to be posted to private...

Thank you.

---

### Post by 3rdalbum on 2013-08-07
The default permissions are correct - only root should be able to write to /var/www and you should copy your files to that folder as root instead of loosening it's permissions.

By default, /var/www is readable by all, but your changes stopped that. Now that you have partly rectified that by making www-data the owner, you could try restarting Apache (rebooting will do this, or use 'sudo service apache2 restart').

You could also try adding read permission to /var/www for all, which is a default permission anyway:

sudo chmod a+r /var/www

---

### Post by linuxonbute on 2013-08-07
True. only root should have write access if it is internet facing. The OP said this is just for testing himself and will not be accessible from the internet.
So I don't think giving write permissions to his non root user should be a problem although he should be able to write using sudo.
Then again i might be wrong - I often am.

---

### Post by 1888software on 2013-08-15
WOW!
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar10274_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=10274") 				 				 					 						 	[**[COLOR=#000000]linuxonbute[/COLOR]**]("http://ubuntuforums.org/member.php?u=10274") did an outstanding job on the fix. Case closed, with THANKS!

---

