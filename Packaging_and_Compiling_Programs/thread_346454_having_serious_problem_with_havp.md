---
title: "having serious problem with havp"
date: 2007-01-25
forum: Packaging and Compiling Programs
---

### Post by AlexenderReez on 2007-01-25
somehow when i want to install something else , havp (with is already in my system) prevent me do to so . . . so when i open base and check . . . this this error 

Could not open lock testfile /var/run/havp/havp-OtCnka: No such file or directory


when i want to uninstall havp , it gives me same error

reez@reez-desktop:~$ sudo apt-get remove havp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  unzoo clamav-base libclamav1 libgmp3c2 havp
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  havp
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 811kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161502 files and directories currently installed.)
Removing havp ...
Stopping havp: invoke-rc.d: initscript havp, action "stop" failed.
dpkg: error processing havp (--remove):
 subprocess pre-removal script returned error exit status 1
Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-OtCnka: No such file or directory
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)


what should i do???:(

---

### Post by orcalover on 2007-02-09
I had the same problem. Try doing this:

First, create the directory /var/run/havp

```
sudo mkdir /var/run/havp
```

Then, do this:

```
sudo echo "exit 0" > /etc/init.d/havp
```

Now, run autoremove (just to clean some things up).

```
sudo apt-get autoremove
```

Now, run the uninstall

```
sudo apt-get remove havp
```

And, I always like to do an autoremove after removing applications. 

```
sudo apt-get autoremove
```

This should take care of the problem. To check that HAVP has in fact been removed, you can search for it using the Synaptic Package Manager ( System -> Administration -> Synaptic Package Manager ). 

Click on search, then search for havp. If the checkbox is clear, then havp has been removed. 

Hope this helps. 

Sean

---

### Post by helliewm on 2007-02-17
Having the same problems, unfortunately this did not work for me. Here is the output.

Any ideas??

helen@helen-desktop:~$ E: havp: subprocess post-installation script returned error exit status 1
bash: E:: command not found
helen@helen-desktop:~$ sudo mkdir /var/run/havp
Password:
helen@helen-desktop:~$ sudo echo "exit 0" > /etc/init.d/havp
bash: /etc/init.d/havp: Permission denied
helen@helen-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgdchart-gd2-noxpm libnessus2
The following packages will be REMOVED:
  libgdchart-gd2-noxpm libnessus2
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 426kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 217876 files and directories currently installed.)
Removing libgdchart-gd2-noxpm ...
Removing libnessus2 ...
Setting up havp (0.79-1) ...
Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-Ypx6kX: Permission denied
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)
helen@helen-desktop:~$ sudo apt-get remove havp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  havp
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  havp
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 811kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 217860 files and directories currently installed.)
Removing havp ...
Stopping havp: invoke-rc.d: initscript havp, action "stop" failed.
dpkg: error processing havp (--remove):
 subprocess pre-removal script returned error exit status 1
Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-iBAsD0: Permission denied
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)
helen@helen-desktop:~$ 

Helen

---

### Post by orionsbelt on 2007-02-22
i was having the same problem removing havp.  i followed the instructions listed above, but i did not run "sudo apt-get autoremove" (because i'm a newbie and i don't know what that means).  i don't think that's what's relevant, though.

when you got to the step:
*sudo echo "exit 0" > /etc/init.d/havp*

you had the error message:
[I]helen@helen-desktop:~$ sudo echo "exit 0" > /etc/init.d/havp
bash: /etc/init.d/havp: Permission denied[/I]

that's because you need to be in root to fix it.  i was a bit worried about messing around in root, because sudo exists for a reason.  basically, you can mess with things that you might not want to mess with.  so after you're done, definitely close the terminal window and go back to sudo.  (if i'm not describing this right, someone please correct me.)

to get to root, run:
*~$ sudo su*

then run:
[I]sudo echo "exit 0" > /etc/init.d/havp
sudo apt-get remove havp[/I]

hopefully, that will fix your problem.  as was mentioned above, i would check in your synaptic package manager to make sure it has been removed (just make sure it's unchecked).

btw, i'm assuming you're having this problem because of clamav, the antivirus program.  i was also having issues with it, which i'm cross-referencing [here]("http://www.ubuntuforums.org/showthread.php?t=290935&highlight=havp+install") and [here]("http://www.ubuntuforums.org/showthread.php?t=366426&highlight=clamav").  also, the initial bug has been documented [here]("https://launchpad.net/ubuntu/+source/clamav/+bug/66636/comments/1").  

if you want to remove ClamAV, then there are instructions [here.]("http://www.getautomatix.com/forum/lofiversion/index.php?t695.html")

---

### Post by xdarkxanarchyx on 2007-03-18
This worked for me after doing "sudo su." Everything is working well now. Thank you!
(This was on a i386 running 6.10)

---

### Post by jtx472 on 2007-03-22
Kudos to ORIONSBELT!  I had the same problem with the havp error and I was  online yesterday most of the  day trying  to find a fix.  I was back  and forth  with a tech on Launchpad who gave me a  couple of  "fixes"  that didn't work.  He finally sent  it in to the bug department and someone from there sent me a fix that I could not figure out (I'm a  newbie too).  And I searched the forums  and  tried several suggested  fixes,  including  the  first  one suggested in this thread, but it  didn't work either  until I used  yours.  And  that did  the  trick.  So from one newbie to another...thanks much!

---

### Post by Cazzj on 2007-04-22
All hail Orionsbelt!  :-)  Thank you Orinonsbelt.  Your instructions fixed my pesky havp problem too.

Cheers....Cazzj

---

### Post by kondax on 2007-05-31
Thank you orcalover and orionsbelt very good job!!!

I just fixed this error with your help.....cheers!!!!:D

---

### Post by quixotic-cynic on 2007-08-15
Thank you so much for explaining that! (I was really screwed...) 

I'm definitely going to be more careful what I install in future...

---

### Post by RedSquirrel on 2007-08-15
> **orionsbelt said:**
> i was having the same problem removing havp.  i followed the instructions listed above, but i did not run "sudo apt-get autoremove" (because i'm a newbie and i don't know what that means).  i don't think that's what's relevant, though.

when you got to the step:
*sudo echo "exit 0" > /etc/init.d/havp*

you had the error message:
[I]helen@helen-desktop:~$ sudo echo "exit 0" > /etc/init.d/havp
bash: /etc/init.d/havp: Permission denied[/I]

that's because you need to be in root to fix it.  i was a bit worried about messing around in root, because sudo exists for a reason.  basically, you can mess with things that you might not want to mess with.  so after you're done, definitely close the terminal window and go back to sudo.  (if i'm not describing this right, someone please correct me.)

You can avoid using 'sudo su' and just use sudo, but you have to use **tee**, like this:

```
echo "exit 0" | sudo tee -a /etc/init.d/havp
```The following command does not work when you run as a regular user
```
sudo echo "exit 0" > /etc/init.d/havp
```because the sudo applies to the 'echo' and then the redirect runs with your regular user's privilieges. Hence, you will not be able to write to '/etc/init.d/havp'.

See this document: 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It's very helpful. :)

Also look at the man page for tee:

```
man tee
```

---

### Post by wyoh on 2008-02-06
You guys rock!

I've been fighting with this stupid thing for a couple of hours now.  Guess I should have checked here with the experts first!

Wyoh

---

### Post by Godzeye on 2009-02-06
perhaps I should be in absolute beginners but after fighting with havp for like months!! yes months, i think what fixed it for me was using killall on clamav then doing the update and remember its proposed...however i really don't think i know how to configure it correctly or really at all what it (havp) is supposed to do for me although it seems to be all in there!


wishing i found this thread months ago! thanks!

---

