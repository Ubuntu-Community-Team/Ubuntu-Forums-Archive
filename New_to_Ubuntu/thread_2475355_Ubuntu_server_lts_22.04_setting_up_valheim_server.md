---
title: "Ubuntu server lts 22.04 setting up valheim server"
date: 2022-05-24
forum: New to Ubuntu
---

### Post by wart101 on 2022-05-24
Hi, not sure if this is exactly the right place. 

I am very new to ubuntu so the whole architecture seems very foreign to me but i am slowly learning and adjusting.

The issue i am having currently is i can't get my Valheim server to work through systemd. the server is currently running fine i have friend playing on it but i can't do anything through the terminal and i currently have to remote SSH in to do anything.

This is my systemd file.

```
[Unit]
Description=Valheim service
Wants=network.target
After=syslog.target network-online.target


[Service]
Type=simple
Restart=on-failure
RestartSec=10
User=adam
WorkingDirectory= /home/adam/Valheim
ExecStart= /home/adam/valheim/start_valheim.sh


[Install]
WantedBy=multi-user.target

```
This is what jounal logs is outputting

```
May 21 17:13:43 homeserver systemd[1]: Started Valheim service.
May 21 17:13:43 homeserver systemd[50202]: valheim.service: Failed to locate executable /home/adam/Valheim/start_valheim.sh: No such file or directory
May 21 17:13:43 homeserver systemd[50202]: valheim.service: Failed at step EXEC spawning /home/adam/Valheim/start_valheim.sh: No such file or directory
May 21 17:13:43 homeserver systemd[1]: valheim.service: Main process exited, code=exited, status=203/EXEC
May 21 17:13:43 homeserver systemd[1]: valheim.service: Failed with result 'exit-code'.
May 21 17:13:53 homeserver systemd[1]: valheim.service: Scheduled restart job, restart counter is at 11.
May 21 17:13:53 homeserver systemd[1]: Stopped Valheim service.
May 21 17:13:53 homeserver systemd[1]: Started Valheim service.
May 21 17:13:53 homeserver systemd[50410]: valheim.service: Failed to locate executable /home/adam/Valheim/start_valheim.sh: No such file or directory
May 21 17:13:53 homeserver systemd[50410]: valheim.service: Failed at step EXEC spawning /home/adam/Valheim/start_valheim.sh: No such file or directory
May 21 17:13:53 homeserver systemd[1]: valheim.service: Main process exited, code=exited, status=203/EXEC
May 21 17:13:53 homeserver systemd[1]: valheim.service: Failed with result 'exit-code'.
May 21 17:14:03 homeserver systemd[1]: valheim.service: Scheduled restart job, restart counter is at 12.
May 21 17:14:03 homeserver systemd[1]: Stopped Valheim service.

No such file or directory.
```

Please help!

---

### Post by TheFu on 2022-05-24
Are you new to Linux/Unix?  Ubuntu is very similar to all the other Unix-based OSes. Nothing too different.

Now, if you are from those other, non-Unix, commercial OSes, then it is a huge difference.  Someone new really should spend the first 6-12 months using a Linux desktop first.  This will help you learn more what 
```
Failed to locate executable /home/adam/Valheim/start_valheim.sh: No such file or directory
```
means and how to deal with it.  It is extremely fundamental.  I'll ask the obvious questions.

Is there a file in /home/adam/Valheim/start_valheim.sh ?  If you didn't put it there, then it doesn't exist.  You cannot run a program that doesn't exist.

Is the file permissions set to allow execute and read permissions for the userid?  If it is a script (which is a guess, not necessarily correct), then the userid that is trying to run it, must have read permissions on the file.

Pro Tips:
Don't run user script from any user's HOME directory areas as root. This is an easy way to get pwn'd.  Put the program's and scripts somewhere that root has access and only root can modify, not any end-user account.

This stuff would be learned in a basic Unix class within the first few days.  You'll want to understand directories, files, location, absolute paths, relative paths, and Unix permissions if you have any hope to run a server of any sort, at least not to have a immediately cracked and pwn'd like 2M other internet servers.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle, free, download which explains Linux in the most efficient order.  I tell people to work through the 1st 250-ish pages in order, reading and completing the exercises as you go.  Learning ad hoc is very inefficient, since Unix skills build on prior skills.  Running a server is about step 100, but if only 20 of the prior steps have been learned, you'll waste more time than just working from step 1 ... step 100.

There are other Linux server teaching tools online too.  There's a 22 part series on github just to teach linux admin.  I wasn't able to find it.  They restart it every month. The guy that created it died about a year ago, but it has been forked, though some of the answers/methods are different than what I'd teach in my classes.

---

### Post by #&amp;thj^% on 2022-05-24
> **TheFu said:**
> 
There are other Linux server teaching tools online too.  There's a 22 part series on github just to teach linux admin.  I wasn't able to find it.  They restart it every month. The guy that created it died about a year ago, but it has been forked, though some of the answers/methods are different than what I'd teach in my classes.
That really is a great place to start, to add I think there are now 14 forks of the same title.
I always have this one bookmarked: [https://github.com/ajitkmr36/Fundamentals-of-Unix-and-Linux-System_Administration](https://github.com/ajitkmr36/Fundamentals-of-Unix-and-Linux-System_Administration)
Hope that's the same as TheFu mentions.

---

### Post by TheFu on 2022-05-24
That isn't it 1fallen.  I tried to find it in an old post to my LUG, but wasn't able.  Looking back isn't something the LUG meetup page does well.  The lessons and exercises are all-in-one location on github.  I think the most popular fork is by an Argentinian or Brazilian. The content is English.

There are free materials from the LPI group. [https://wiki.lpi.org/wiki/Free_Training_Materials](https://wiki.lpi.org/wiki/Free_Training_Materials)  They offer LPI certification.  

I'm not certified in anything related to Linux or Unix, but knowing the information and decades of experience get me into interviews when I'm looking for work.  For someone younger, I suppose some sort of cert is needed to get passed HR.  When I was hiring people for my teams, I'd ask the HR people not to worry about certs very much. Certs often mean that people test well, memorize stuff for 24 hrs, but don't really know much in practice.  I'd rather have someone with 2 yrs admin experience and no certs than someone with L1, L2, L3 certs and no experience at all.

I'm not against paying for stuff, but IME, the paid stuff doesn't teach any better or more. OTOH, if you pay, perhaps you'll have more incentive to actually do the work and learn the information?  When I pay for things, that gives me more incentive NOT to waste money by following through. That is really the hardest part in any learning effort. Following through 5x a week for 3+ weeks and you have a habit. Less than 3 weeks and it isn't a habit.  For every computer skill, just expect to be learning for the rest of your life and make a plan to spend at least 5 hrs a week learning _something_.  Doesn't really matter what, but gaining the habit is critical as a life skill.

---

### Post by #&amp;thj^% on 2022-05-24
Thanks for that, important to confirm or deny bad info/links. 
If you do find it, I would certainly like to reference that material for my own sake.
of course no pressure though. ;)

---

### Post by TheFu on 2022-05-24
[https://linuxupskillchallenge.com/](https://linuxupskillchallenge.com/)  Found it. The link there to the github is the correct fork.

---

### Post by #&amp;thj^% on 2022-05-24
> **TheFu said:**
> [https://linuxupskillchallenge.com/](https://linuxupskillchallenge.com/)  Found it. The link there to the github is the correct fork.
That was quick, very much appreciated as well.
Sorry to OP for off topic but that link is very very useful.

---

### Post by him610 on 2022-05-24
> that link is very very useful.

Yes, thank you. Already bookmarked.

---

### Post by wart101 on 2022-05-26
Apparently i can't post?

---

### Post by ActionParsnip on 2022-05-26
What is the output of:
```

ls -la /home/adam/valheim/start_valheim.sh

```
Thanks

---

### Post by wart101 on 2022-05-27
> **ActionParsnip said:**
> What is the output of:
```

ls -la /home/adam/valheim/start_valheim.sh

```
Thanks

```

adam@homeserver:/$ ls -la /home/adam/valheim/start_valheim.sh
-rwxrwxr-x 1 adam adam 584 May 25 17:47 /home/adam/valheim/start_valheim.sh
adam@homeserver:/$



```

---

### Post by TheFu on 2022-05-27
> **wart101 said:**
> ```

adam@homeserver:/$ ls -la /home/adam/valheim/start_valheim.sh
-rwxrwxr-x 1 adam adam 584 May 25 17:47 /home/adam/valheim/start_valheim.sh
adam@homeserver:/$



```

Now that you can find the file, does it work?
/home/adam/valheim/start_valheim.sh

BTW, ```

WorkingDirectory= /home/adam/[COLOR="#FF0000"]V[/COLOR]alheim
ExecStart= /home/adam/valheim/start_valheim.sh
```

Points to a different working directory.  All Unix file systems are case sensitive.
Also, is a space allowed after the '=' in systemd unit files?  None of my unit files have a space there.

---

### Post by MAFoElffen on 2022-05-28
A point of perspective:

You are talking about hosting a Game Server for a friend (remote), of a Game Server that works on Windows and Linux. (Right?) Windows Server uses the .exe and Linux uses the .sh...

The fundamental building blocks that you should think of is that when you install something for remote use, is Security of the physical machine. Tutorials on that Game Server recommend it being installed as a container or a Virtual Machine, so it is isolated from the physical machine. Though it can be installed on a dedicated server. No where does it say to install the files in a Machine's User's home directory, right? >>> Usually in /usr/share/<application_directory> And an Application is usually considered as a Service/User, when it installs and accesses things... that is how it usually installs.my

Next, remote permissions of, should not be set to Root, but rather to a User Group that needs access to it or to the Application or Service itself, which Users have access to through User Groups... That is the Security Rule of thumb methodology, whether you are using Windows, UNIX or Linux Servers. Correct me if you think I am wrong. That methodology has existed for years and will simplify much of what you are trying to do. (Create Security Groups with access and permissions. Create Users and add those Users to the Security Groups.) Though Game Servers usually get access through a game hub, where they connect to game host servers.

As for starting a service, that is different, but I see it not finding the startup script 'from' the service file... Which may have to be modified to point it to the path location where it actually resides.

If you look closely... you have a typo. Linux is "case sensitive".
```

[Service]
Type=simple
Restart=on-failure
RestartSec=10
User=adam
WorkingDirectory= /home/adam/[COLOR=#ff0000]V[/COLOR]alheim
ExecStart= /home/adam/[COLOR=#ff0000]v[/COLOR]alheim/start_valheim.sh

```
See the "case" difference in the characters highlighted in [COLOR=#ff0000]Red[/COLOR]? Just changing that should make it work. (...start that service and be in the correct working directory.)

My further recommends would be to install into /usr/share/valheim/. Create a User Group named valheim with directory permissions to that User Group. Fix the service file pointers to that path. Change User=adam in [Service] in the .service file to Group=valheim, and add the associated Users to that valheim Security Group. Tweak the permissions of that directory to give just the permissions and access it needs to that Security Group. As a sys admin (you, Wheel Group)), you have access to that directory.

I've seen many tutorials on this Game Server. That is what I saw, and as a Sys Admin, how I interpret those.

I never blindly give blanket "Root access" to individual external sources, outside my own sandbox. Just saying. Having given instruction to people through here, some things may be misinterpreted by some people. Just want to be clear on that, to be safe.

---

### Post by wart101 on 2022-05-28
> **MAFoElffen said:**
> A point of perspective:

You are talking about hosting a Game Server for a friend (remote), of a Game Server that works on Windows and Linux. (Right?) Windows Server uses the .exe and Linux uses the .sh...

The fundamental building blocks that you should think of is that when you install something for remote use, is Security of the physical machine. Tutorials on that Game Server recommend it being installed as a container or a Virtual Machine, so it is isolated from the physical machine. Though it can be installed on a dedicated server. No where does it say to install the files in a Machine's User's home directory, right? >>> Usually in /usr/share/<application_directory>

Next, remote permissions of, should not be set to Root, but rather to a User Group that needs access to it or to the Application or Service itself, which Users have access to through User Groups... That is the Security Rule of thumb methodology, whether you are using Windows, UNIX or Linux Servers. Correct me if you think I am wrong. That methodology has existed for years and will simplify much of what you are trying to do. (Create Security Groups with access and permissions. Create Users and add those Users to the Security Groups.)

As starting a service, that is different, but I see it not finding the startup script 'from' the service file... Which may have to be modified to point it to the path location where it actually resides.

I've seen many tutorials on this Game Server. That is what I saw, and as a Sys Admin, how I interpret those.

I never blindly give blanket "Root access" to individual external sources, outside my own sandbox. Just saying. Having given instruction to people through here, some things may be misinterpreted by some people. Just want to be clear on that, to be safe.

I'm aware that the way I have set it up has made security extremely weak but I'm not to fussed with that right now, I just want to get it working and I can sort out the security issue's later, I know that's probably backwards.

---

### Post by wart101 on 2022-05-28
ok I got it working.

in the valheim_server.sh file (at the start i had)

```

#!/bash/sh

```

I changed it to.

```

#!/bin/bash

```

working fine now, i don't fully understand why but there it is.

---

### Post by MAFoElffen on 2022-05-28
LOL. Understood. Might work with either
```

#!/bin/bash

#OR

#!/bin/sh

```
sh binary is not in /bash... That does not exist from / (root directory)


More tips in the edit to my post...

---

### Post by wart101 on 2022-05-28
:guitar::guitar::guitar::guitar:

---

### Post by wart101 on 2022-05-28
> **TheFu said:**
> Are you new to Linux/Unix?  Ubuntu is very similar to all the other Unix-based OSes. Nothing too different.

Now, if you are from those other, non-Unix, commercial OSes, then it is a huge difference.  Someone new really should spend the first 6-12 months using a Linux desktop first.  This will help you learn more what 
```
Failed to locate executable /home/adam/Valheim/start_valheim.sh: No such file or directory
```
means and how to deal with it.  It is extremely fundamental.  I'll ask the obvious questions.

Is there a file in /home/adam/Valheim/start_valheim.sh ?  If you didn't put it there, then it doesn't exist.  You cannot run a program that doesn't exist.

Is the file permissions set to allow execute and read permissions for the userid?  If it is a script (which is a guess, not necessarily correct), then the userid that is trying to run it, must have read permissions on the file.

Pro Tips:
Don't run user script from any user's HOME directory areas as root. This is an easy way to get pwn'd.  Put the program's and scripts somewhere that root has access and only root can modify, not any end-user account.

This stuff would be learned in a basic Unix class within the first few days.  You'll want to understand directories, files, location, absolute paths, relative paths, and Unix permissions if you have any hope to run a server of any sort, at least not to have a immediately cracked and pwn'd like 2M other internet servers.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle, free, download which explains Linux in the most efficient order.  I tell people to work through the 1st 250-ish pages in order, reading and completing the exercises as you go.  Learning ad hoc is very inefficient, since Unix skills build on prior skills.  Running a server is about step 100, but if only 20 of the prior steps have been learned, you'll waste more time than just working from step 1 ... step 100.

There are other Linux server teaching tools online too.  There's a 22 part series on github just to teach linux admin.  I wasn't able to find it.  They restart it every month. The guy that created it died about a year ago, but it has been forked, though some of the answers/methods are different than what I'd teach in my classes.


I probably understated my Linux knowledge mostly so someone with experience doesn't overwhelm me with information that i have to sift through to understand, that said thank you for the link to the tutorial, i started going through it and have learnt some new things/tricks so it has really helped. although my issue is solved i will definitely use it, as you mentioned most of my knowledge has been gained through ad-hock means which I'm comfortable learning this way but you are right, it is very inefficient.

---

### Post by TheFu on 2022-05-28
As to sh vs bash.  Unix systems have many different "shells".  sh and bash are 2 options, but there are many others. Bash should be 99% backwards compatible to sh (aka Bourne Shell) which was one of the earliest shell on all Unix systems.  However, sh cannot process scripts that use bash commands.

Basically, sending **bash** commands to the **sh** program is like speaking a different dialect of the same language. Often, the meaning comes through, but sometimes it doesn't.

And just to be very clear, the extension on the filename means NOTHING, ZERO, NADA to Unix/Linux. Extensions are handy for humans, but the computer looks at the file "signature" ... in this case the first line ... to see which tool should be used to interpret all the following lines.  This is commonly how all Unix scripts work.  The first line defines the interpreter.  Some other commonly seen interpreters.
```
/usr/bin/awk
/usr/bin/bash
/usr/bin/sh
/usr/bin/python3
/usr/bin/perl
```
But any program that accepts input from stdin can be used.

---

