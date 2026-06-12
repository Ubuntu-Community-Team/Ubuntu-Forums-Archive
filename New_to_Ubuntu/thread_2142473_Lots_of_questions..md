---
title: "Lots of questions."
date: 2013-05-05
forum: New to Ubuntu
---

### Post by Allicaz on 2013-05-05
Hello every one,
I am new to forums, this is my very first ever post/ thread in a forum. So I apologize in advance if i have started in the wrong discusion board.

I have spent the last 4 days searching and reading posts and threads on this forum, trying to find the answer to my main question, and I really don't know where to start, so I have started here.

A few things all readers of this post should know: I am very new to forums as I have already said, I've used ubuntu 12.04 for a year roughly. and my Knowledge, understanding and use of commands is very very limited. 

Here goes.

I am not able to loggin any more, but can login using guest, I can also login using pressing crtl alt F1 and getting a tty, I think? which I tryed doing after reading several posts realed in some way to my problem.

I can give a description ogf what I did to not be able to loggin, in another post as it is very detailed and long, if needed.
I want to back up my files (mostly my photos) and sync them to my ubuntu one account, but I am not able to login on my computer, I've read  posts about  about how to change my password using recovery mode, and not logging on as root. and only having one user account, I have now learned that lesson the hard way:)

Most of the posts I have read relate to upgrading from one version of ubuntu to another. my problem does Not relate to most of the posts I have read.

I have not upgraded from one version to another. Only tried to change my password, in correctly by the looks of it.
 Thank you, very much in advance.:confused:

---

### Post by Bashing-om on 2013-05-05
Hi Allicaz; Welcome to the forum.

We are here to help you over any hurdle !

Posting etiquette : One problem per post -> keeps the forum un cluttered and easier to search.

Your first priority is of course the pass word issue. As I read your enquiry you have attempted to change your password, and now have no access?
See this tutorial to regain/reset a password:
Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Impavidus on 2013-05-05
If you manage to change your password using Allicaz's link and still cannot login with the new password, there may be something wrong with your settings. Most commonly people have used sudo the wrong way and have root-owned files in their home directory. To solve this, follow the same instructions as given in that link, up to and including the **mount -o rw,remount /** and then give the command```

chown -R yourusername:yourusername /home/yourusername
```substituting your user name. Then type **exit**.

---

### Post by CatKiller on 2013-05-06
If you can log in on a TTY, then it's not a password issue. If the symptom is that you log in and get returned to the login screen then it seems more like a graphics problem causing X or your display manager to restart; the first thing you see when the display manager starts is the login screen.

---

### Post by Allicaz on 2013-05-06
Thank you all,

I did use the link [http://www.psychcays.net/ubuntu/resetpassword](http://www.psychcays.net/ubuntu/resetpassword) you posted to reset the password, 3 times before posting on here. the third time I changed back  to the original one, my home folder is encrypted.

---

### Post by slickymaster on 2013-05-06
> **CatKiller said:**
> If you can log in on a TTY, then it's not a password issue. If the symptom is that you log in and get returned to the login screen then it seems more like a graphics problem causing X or your display manager to restart; the first thing you see when the display manager starts is the login screen.

+1
I think [COLOR=#000000]CatKiller might be right. Chech these out:
[/COLOR][Ubuntu 12.04 cannot login, bounces back to login splash]("https://answers.launchpad.net/ubuntu/+source/lightdm/+question/197479")
[Stuck at login screen]("http://askubuntu.com/questions/130387/stuck-at-login-screen")
[Can't log in to my ubuntu 12.04]("http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04")

---

### Post by Allicaz on 2013-05-06
This is what is diplayed when i login with tty2

I am writing it word for word.

ubuntu 12.04.2 LTS caz-AOA110 tty2
caz AOA110 login caz
password
last login: sun may 5 16:42:38 BST 2013 on tty2
welcome to ubuntu 12.04.2 Lts (GNU/LINUX 3.2.0-40 generic-pae i686)
   *Documentation https: //help.ubuntu.com

15 packages can be updated
11 updates are security updates

signature not found in user keyring
perhaps try the interactive 'ecrypts-mount-private'
caz@caz-AOA110:~$

What shall I do now? and can I do it from that screen?:confused:

---

### Post by grahammechanical on 2013-05-06
> my home folder is encrypted.

That was key information that was needed in the first post. Did you try to change the encryption password?

---

### Post by Allicaz on 2013-05-06
Sorry, I did'nt know what information to put first, was in panic mode and have been since Monday night.
I only tried to chage my login password using the drop down icons on the black bar at the top of the screen, not knowing commands and termials.
 At the time I totally forgot that my home folder is encrypted.

I think I have the passphrase I wrote down at the end of installing, I wrote down a sequence of numbers and letters at the time and i've still got it. Would that be the passphrase?

---

### Post by Allicaz on 2013-05-07
I have managed to pluck up the courage to try some command when logged using tty but am getting errors.
I am going to look on another board to find the solution.

These are the commands i tried:

ecryptfs-mount-private

and 

ecrptfs-recover-private

I can post the results from these commands if any one wants to know them, please ask.
thank you all for your help so far

---

### Post by Bashing-om on 2013-05-07
Allicaz; Hi again .

I say again we are here to help. I have no knowledge of encrypted file systems and thus not able to help you.

Bear with us and others- who have the experience-  will see your thread and pick up.
[INDENT=2]
Patience is a virtue 
[/INDENT]

---

### Post by mastablasta on 2013-05-07
> **Allicaz said:**
> I think I have the passphrase I wrote down at the end of installing, I wrote down a sequence of numbers and letters at the time and i've still got it. Would that be the passphrase?


sounds like a passphrase to me. or perhaps a key.

encrypted home or the whole disk prevents other access to your data. but it also prevents you from easy data recovery in case of disk corruption. 

i am curious - if you can login to tty, can you get to your home folder in there?

---

### Post by Allicaz on 2013-05-07
> **mastablasta said:**
> sounds like a passphrase to me. or perhaps a key.

encrypted home or the whole disk prevents other access to your data. but it also prevents you from easy data recovery in case of disk corruption. 

i am curious - if you can login to tty, can you get to your home folder in there?

I think it could be the whole disk, there is only 1 account, and a guest account that I am using to post.

I logged on using tty2 and tried to run this command

'ecryptfs-mount-private'

I followed the prompts and got errors after trying login password and the passphrase I thought I had.

I can post you the results of what came up on the sceen, as I wrote them down bofore I pressed crtl alt f7 to exit.

---

### Post by Allicaz on 2013-05-08
> **Allicaz said:**
> I think it could be the whole disk, there is only 1 account, and a guest account that I am using to post.

I logged on using tty2 and tried to run this command

'ecryptfs-mount-private'

I followed the prompts and got errors after trying login password and the passphrase I thought I had.

I can post you the results of what came up on the sceen, as I wrote them down bofore I pressed crtl alt f7 to exit.

Here is the output from the screen with the commands I have tried.

Signature not found on user keyring
perhaps try the interactive 'ecryptfs-mount-private'
caz@caz-AOA110#$ ecryptfs-mount-private
Enter login: login password
Error:unwrapping passphrase and inserting into user 
session keyring failed[-5]
info check the system log for more information from librecryptfs
Error your passphrase is incorrect
Enter login passphrase:

tried again but this time I put the passphrase in I thought I had,
same result

Tried for a third time and this time I got

Error:your passphrase is incorrect
Error: too many incorrect password attempts, exiting

So I tried this instead,
ecryptfs-recover-private

I got this,

Error: this programme must be run as root

Any ideas?

---

### Post by Allicaz on 2013-05-09
I have 37 packages that can be updated, 16 are security updates.
I  have looked at these updates in the package manager through the guest session, 
I would normally click on install but and let the package manager do the rest. 
Can I install these updates throuh tty1? as that is the only way I can login, not sure if I can do it through the guest account.

I think if these updates are installed then I might be able to login normally, as one of them, has something to do with gnome session keyrings

---

### Post by squakie on 2013-05-09
Personally, I would wait on updates until this is solved.  If you could, please post back the result that was asked for earlier:  If you log in via tty/terminal, can you see your own folder?  I'm not sure what you would be trying to mount if it's your home folder or the entire system disk that is encrypted.

So, log in via tty, then:

pwd <enter>

ls <enter>

Please post back the results of those 2 commands.

If it a separate disk entirely that is encrypted and you are trying to mount it, please let us know.

I also don't have experience with encrypted drives, so I can't help there.  For the ecryptfs-recover-private, try sudo ecryptfs-recover-private

it also mentions checking sys log - what shows there?

---

### Post by Allicaz on 2013-05-10
> **squakie said:**
> Personally, I would wait on updates until this is solved.  If you could, please post back the result that was asked for earlier:  If you log in via tty/terminal, can you see your own folder?  I'm not sure what you would be trying to mount if it's your home folder or the entire system disk that is encrypted.

So, log in via tty, then:

pwd <enter>

ls <enter>

Please post back the results of those 2 commands.

If it a separate disk entirely that is encrypted and you are trying to mount it, please let us know.

I also don't have experience with encrypted drives, so I can't help there.  For the ecryptfs-recover-private, try sudo ecryptfs-recover-private

it also mentions checking sys log - what shows there?

I logged in throught  tty1
entered password and then 
ls <enter>

this is the result:

[B]Access-Your-Private-Data. desktop README txt
[/B]
I don't know how to check the system logs, could you give me a command to do this please.

This is what I get when I loggin throuh tty:

After enetering login and password.

**Last login sun may 5 and the time on tty**<example>
[B]Welcome to ubuntu 12.04.2 LTS (GNU/LINUX 3.2.0-40 generic-pae i686)

37 packages can be updated
16 are security updates.

Signature not found in user kering
 Perhaps try the interactive 'ecryptfs-mount-private'
caz@cazAOA110 #$




[/B]
This is what I see on the screen when I loggin through tty.

---

### Post by squakie on 2013-05-11
Try one of the ecryptfs-mount-private's again, then cat /var/log/syslog.0 | tail --lines 20 

Copy and paste that output here between code tags.

---

### Post by Allicaz on 2013-05-11
> **squakie said:**
> Try one of the ecryptfs-mount-private's again, then cat /var/log/syslog.0 | tail --lines 20 

Copy and paste that output here between code tags.

I tried ```
ecryptfs-mount-private
```

then ```
cat/var/log/syslog.0 tail --lines 20
```

this was the out put

[CODE] -bash cat/var/log/sys/.0 No such file or directory[/CODE

---

### Post by Impavidus on 2013-05-11
You missed a space and the pipe ("|", vertical bar, on my keyboard shift+\ and above the enter key, but rather variable among keyboards). The command was (exaggerating the number of spaces to make it clear, you'll only need one at each position):```

cat    /var/log/syslog.0    |    tail    --lines    20

```

---

### Post by Allicaz on 2013-05-11
> **Impavidus said:**
> You missed a space and the pipe ("|", vertical bar, on my keyboard shift+\ and above the enter key, but rather variable among keyboards). The command was (exaggerating the number of spaces to make it clear, you'll only need one at each position):```

cat    /var/log/syslog.0    |    tail    --lines    20

```

After findiing the right key to get the vertical bar  and adding the space, I tried again and this was the output
```
cat: /var/log/syslog.0 : no such file or directory
```

I tried several time but got the same output.

---

### Post by Bashing-om on 2013-05-11
Allicaz; Hi ! I continue to monitor your thread.

My 12.04 install also does not contain the file "/var/log/syslog.0" Maybe look at files:
syslog and syslog.1
my output:
> sysop1@1204-a:~$ ls -la /var/log/sysl*
-rw-r----- 1 syslog adm 540730 May 11 14:17 /var/log/syslog
-rw-r----- 1 syslog adm 320410 May 10 10:14 /var/log/syslog.1
-rw-r----- 1 syslog adm  59114 May  9 00:41 /var/log/syslog.2.gz
-rw-r----- 1 syslog adm  58981 May  8 10:17 /var/log/syslog.3.gz
-rw-r----- 1 syslog adm  59185 May  7 05:59 /var/log/syslog.4.gz
-rw-r----- 1 syslog adm  59066 May  6 10:25 /var/log/syslog.5.gz
-rw-r----- 1 syslog adm  38730 May  5 10:02 /var/log/syslog.6.gz
-rw-r----- 1 syslog adm  21505 May  4 11:30 /var/log/syslog.7.gz
sysop1@1204-a:~$  Note that I globbed (*) for all files starting with the characters "sysl" and this results in printing out all files starting thus no matter what characters are after.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by squakie on 2013-05-11
As I said in my first post - I don't know anything about encrypted disks - I'm just hoping the log file might show something we can track down, or at least maybe some more information for someone who does know this.  Thanks Impavidus - I didn't make that cat statement very clear, especially if someone is new to it.  I'm going to remember your post so if I want to tell someone else to do the same thing it would be readable and understandable.  Thanks!

---

### Post by squakie on 2013-05-11
Thanks Bashing-om -  I was trying without being on my Ubuntu box, and indeed I think I messed up.  I *think* it is as you have  have shown:  I think it would be syslog for the current log file, and suffixed by a number for each older log it keeps.  Sorry about that.  I'm glad others are here trying to help the OP as well.  I think I'll just move to the background so that others can help without messing up like I did.

---

### Post by Bashing-om on 2013-05-11
@  		squakie; Only justice, How many times have you caught my back side.

As many post that we respond to, and as scatter brained as we may become, there is bound to be a slip on occasion.

We continue, awaiting enlightenment from those experienced with encrypted file systems.
[INDENT=2]
It is all good 

[/INDENT]

---

### Post by squakie on 2013-05-11
I guess maybe we should tell the OP:  do the same "cat" statement over except using only syslog as the file name.  Sorry about that!

---

### Post by Allicaz on 2013-05-12
Thanks Bashing-om, I just changed the 0 to a 1.

Squakie, Here is the out put of ```
cat var/log/syslog.1 | tail -- lines 20
```

```
may 11 14:17:35 caz-AOA110 kernel:  [508.593759] type=1400 audit(1368278255.736:32):apparmor ="DENIED" operation="mount" parent=1 Profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/tmp/guest-3mayxu/.gvfs/" pid=1965 comm="gvfs-fuse deam
o" fstype="fuse.gvfs-fuse-daemon" srcname="gufs-fuse daemon" flags="rw,nosuid,nodev"

caz-AOA110 dbus[497]: [system] Activating service name= 'org.freedesktop.UDisks' (using service help)
caz-AoA110 dbus[497]: [system] Successfully activated service 'org. freedesktop.UDisks'
caz-AOA110 rtkit-daemon [1721]: Successfullymade thread 2009 of proccess 2009 (n/a) owned by '123' high priority at nice level-11
caz-AOA110 rtkit-daemon[1721]: supervising 4 threads of 2 proccesses of 2 users.
caz-AOA110 rtkit-daemon[1721]: Successfully made thread 2012 of process 2009 (n/a) owned by '123' RT at priority 5.
caz-AOA110 rtkit-daemon[1721]: Supevising 5 threads of 2 proccesses of 2 users.
caz-AOA110 rtkit-daemon[1721]: Successfully made thread 2013 of process 2009 (n/a) owned by '123' RT at priority 5.
caz-AOA110 rtkit-daemon[1721]: Supervising 6 threads of 2 processes of 2 users.
caz-AOA110 goa[2213]: goa-daemon version 3.4.0 starting [main.c:112,main ()]
caz-AOA110 dbus[497]: [system] Activating service name= 'org.freedesktop.packagekit (using service helper).
caz-AOA110 AptDaemon: INFO: Initializing daemon.
caz-AOA110 AptDaemon.packagekit: INFO: Initializing packagekit compat layer.
caz-AOA110 dbus[497]: [system] Successfully activated service 'org.freedesktop.packagekit'.
caz-AOA110 AptDaemon.packagekit: INFO: Initializing packagekit transaction.
caz-AOA110 AptDaemon.worker: INFO: Simulating trans: /org/debian/apt/transaction/286efae5b3f54537bcf34d3c2c5b556a
cazAOA110 AptDaemon.worker: INFO: Proccessing transaction /org/debian/apt/transaction/286efae5b3f54537bcf34d3c2c5b556a
cazAOA110 AptDaemon.packagekit: INFO: Get updates()
cazAOA110 AptDaemon.worker: INFO: Finished transaction/ org/debian/apt/transaction/286efae5b3f54537bcf34d3c2c5b556a
caz-AOA110 kernel: [ 607.592895] init: tty1 main proccess ended. respawning

```

Sorry for the delay. Hope this is good information.

---

### Post by squakie on 2013-05-13
Try the "mount" again and then immediately follow it with the cat - that way we can see if it generated any errors in the log.  You may also want to change the lines from 20 to 40 so more of the log is available and also just use syslog as that will be the most current - the .<some number> log files are archived older log files.  Unless something obvious stands out, that will be the best I can do for you.  Hopefully that information will help someone who knows this to help you fix your problem.  Sorry, but I just don't have the experience in it to be able to help beyond looking for something obvious in the log.

---

### Post by Allicaz on 2013-05-14
Here is some of the output after doing the "mount" again

```
ecryptfs-insert-wrapped-passphrase-into -keyring: Incorrect wrapping key for file [/home/caz/.ecryptfs/wrapped-passphrase]
ecryptfs-insert-wrapped-passphrase-into keyring: Error attempting to unwrap passphrase from file [/home/caz/.ecryptfs/wrapped-passphrase; rc=[-5]

```

The same thing is displyed several times, as when you first try, and come up with the error login passphrase is incorret, it tells you to try again. You get three attempts and then it exits.

Here is the list of updates waiting to be installed, there is now 41, not 37.

Important updates:
```
4 updates for antivirus (clamav)
3 for free implementation of the Open GL API DRI
1 for mesa open GL utility
1 for x acceleration library
6 realting to linux kernel
1 for IRC connection managerfor telepathy

Recommended updates:
1 for utilities for configuring and using ALSA
1 for GNOME keyring services
1 for shared library for ALSA applications
4 for userspace interface 
Glib wrapper library for PKcs#11 -runetime
2 for library for crypto UI
GNU TLS library
2 for network management framework
PAM module to unlock the GNOME keyring upon login
SSL shared libraries
unnity 2d shared library
network management framework 
secure socket layer  binary & related cryptographic tools
unity interface for non-accelerated graphics cards
common files for Unity 2d enviroment
UNITY 2d spread
tools for manipulating MSDOS files (new update)
```

I'm hoping these updates might solve my problem any ideas any one?

---

### Post by Allicaz on 2013-05-14
Update, I have created a new user and was able to install the updates.

---

### Post by Bashing-om on 2013-05-14
Allicaz; Hi !

You do good in that respect. At least you now have an acess to your system. Mean while we continue to await the notice of someone experienced with encrypted file systems. (sorry It ain't me, have not been there and no intent to do so ).
[INDENT]
no help, but I'll feel for you.
[/INDENT]

---

### Post by johnluck on 2013-05-16
I see that other members helped you very well, if you need anything else u'r always welcome.





[download games]("http://idownloadgames.net")

---

### Post by Allicaz on 2013-05-16
> **Bashing-om said:**
> Allicaz; Hi !

You do good in that respect. At least you now have an acess to your system. Mean while we continue to await the notice of someone experienced with encrypted file systems. (sorry It ain't me, have not been there and no intent to do so ).[INDENT]
no help, but I'll feel for you.
[/INDENT]


Thank you all for your help.
After spending most of the day trying to figure out how to recover my files with a live usb, it did not work!, I made a mess if it and got to the point of not being able to login on any of the accounts,  not even the new one I created.

In the end I had to do a complete reinstall, this time_ with out the encryption option_. 
I was going to reinstall any way, but wanted my photo's and video's first, I learnt a very hard lesson and will not be maing the same mistake again.

Once again, thank you to all that tried to help x

---

