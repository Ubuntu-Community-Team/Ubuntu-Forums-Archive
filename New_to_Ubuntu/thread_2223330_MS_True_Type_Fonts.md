---
title: "MS True Type Fonts"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by rickm1945 on 2014-05-10
I tried installing MS True Type fonts from software manager and via Terminal. I have not been successful at either. Help Please!

---

### Post by howefield on 2014-05-10
Which version of Ubuntu ?

```
sudo apt-get update
```
then
```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by Vladlenin5000 on 2014-05-10
Obs.: There's an EULA (End User License Agreement) from Microsoft you must agree with otherwise the installation will be aborted. When such dialog window appears in the terminal you need to use the TAB and arrow keys to navigate the options and ENTER to ultimately select the desired option.

---

### Post by mikewhatever on 2014-05-10
> **Vladlenin5000 said:**
> Obs.: There's an EULA (End User License Agreement) from Microsoft you must agree with otherwise the installation will be aborted. When such dialog window appears in the terminal you need to use the TAB and arrow keys to navigate the options and ENTER to ultimately select the desired option.

While accepting the EULA is the usual trouble with msfonts, we don't actually know what happened.
rickm, can you tell us.

---

### Post by monkeybrain20122 on 2014-05-10
It comes with restricted-extras, I used to just bypassed it by refusing to accept the EULA, but pipelight appears to need it so I accept it so I guess the fonts are just available somewhere in the system. I never change the default fonts in Ubuntu.

---

### Post by Vladlenin5000 on 2014-05-10
You might need to reinstall (if not, it doesn't hurt to do it anyway and we can troubleshoot from there): ```
sudo apt-get purge ttf-mscorefonts-installer
``` followed by ```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by rickm1945 on 2014-05-11
@howefield Ubuntu 14.04

---

### Post by rickm1945 on 2014-05-11
```
richard@richard-Studio-XPS-8100:~$ sudo apt-get purge ttf-mscorefonts-installer
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 134 kB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: error processing package ttf-mscorefonts-installer (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@richard-Studio-XPS-8100:~$ 

```
this was returned on purge.

---

### Post by rickm1945 on 2014-05-11
This was returned on trying to reinstall like it said to do.
```
richard@richard-Studio-XPS-8100:~$ sudo apt-get purge ttf-mscorefonts-installer
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 134 kB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: error processing package ttf-mscorefonts-installer (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@richard-Studio-XPS-8100:~$ 


```

---

### Post by fatriff on 2014-05-11
This thread appears to hold the solution..

[http://ubuntuforums.org/showthread.php?t=2179342]("http://ubuntuforums.org/showthread.php?t=2179342")

---

### Post by rickm1945 on 2014-05-11
That will probably work but when the EULA comes up at bottom says <OK> and no way to accept it. I hit enter but nthing happened. any ideas?

---

### Post by Vladlenin5000 on 2014-05-11
> **rickm1945 said:**
> That will probably work but when the EULA comes up at bottom says <OK> and no way to accept it. I hit enter but nthing happened. any ideas?

Yes, post #3. Please read it again.

---

### Post by rickm1945 on 2014-05-11
@mikewhatever When EULA pops up there is <ok> bottom but it does noting. I hit enter and nothing so I can't accept the EULA. That's probably the big problem.

---

### Post by rickm1945 on 2014-05-11
What I'm trying to tell you is nothing happens. No arrow keys work nor does tab nor does enter.

---

### Post by matt_symes on 2014-05-11
Hi

> **rickm1945 said:**
> @mikewhatever When EULA pops up there is <ok> bottom but it does noting. I hit enter and nothing so I can't accept the EULA. That's probably the big problem.

As has been suggested, hit the <TAB> key on the EULA page. 

This should highlight the <ok> option in red. 

Then hit the <enter> key.

Does this not work for you ?

EDIT:

> What I'm trying to tell you is nothing happens. No arrow keys work nor does tab nor does enter.

That is very odd !!

Kind regards

---

### Post by Vladlenin5000 on 2014-05-11
Always hit TAB before anything else... In the first screen it should immediately highlight th "OK"... In the next screen there's a YES/NO selection to be made (and you want YES, obviously) so, again, in order to navigate between the options you need here the arrow keys (the default option is NO and you need to highlight YES with the arrow keys. TAB always advances to the dialog box/window options.

---

### Post by craig10x on 2014-05-11
Or another way you can do it it, is to install synaptic package manager and do it with that...on that, the license agreement WILL pop up...problem with the software center is that there has been a bug in it for a long time where when you install ubuntu restricted extras, the agreement comes up but you don't see it because it's under the software center window, so since you don't check the yes box it doesn't get installed...i always minimize the software center when installing restricted extras so i can see that window when it pops up...

However, if you re-install MS-Core fonts in package manager, you WILL see that agreement window popping up...and that should get it installed properly...

---

### Post by Vladlenin5000 on 2014-05-11
@[**[COLOR=#000000]craig10x[/COLOR]**]("http://ubuntuforums.org/member.php?u=869825")

The thing is: The license agreement does popup... The problem seems to be selecting the options. Your solution - which isn't a "solution" at all - doesn't solve the user inability to use the TAB-Arrow Keys-ENTER, it just adds an additional difficulty layer for a newbie and it's totally unnecessary.

---

### Post by rickm1945 on 2014-05-11
@ fatriffI have issued the command [code'richard@richard-Studio-XPS-8100:~$ sudo apt-get clean
[sudo] password for richard: 
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
richard@richard-Studio-XPS-8100:~$ 

[/code]

---

### Post by fatriff on 2014-05-11
> **rickm1945 said:**
> @ fatriffI have issued the command [code'richard@richard-Studio-XPS-8100:~$ sudo apt-get clean
[sudo] password for richard: 
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
richard@richard-Studio-XPS-8100:~$ 

[/code]

Try this in terminal..

```
sudo rm /var/cache/apt/archives/lock
```

then 

```
sudo apt-get update

```
then try again...

---

### Post by rickm1945 on 2014-05-11
Return is:
```
richard@richard-Studio-XPS-8100:~$ rm /var/cache/apt/archives/lock
rm: remove write-protected regular empty file &#8216;/var/cache/apt/archives/lock&#8217;? y
rm: cannot remove &#8216;/var/cache/apt/archives/lock&#8217;: Permission denied
richard@richard-Studio-XPS-8100:~$ 


```

---

### Post by matt_symes on 2014-05-11
Hi

```
sudo rm /var/cache/apt/archives/lock
```

then try again.

Kind regards

---

### Post by rickm1945 on 2014-05-12
Synaptic package managr won't install: Here is the error return: 
```

nstallArchives() failed: Selecting previously unselected package synaptic. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170175 files and directories currently installed.) 
Preparing to unpack .../synaptic_0.81.1_amd64.deb ... 
Unpacking synaptic (0.81.1) ... 
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for mime-support (3.54ubuntu1) ... 
Processing triggers for hicolor-icon-theme (0.13-1) ... 
Processing triggers for man-db (2.6.7.1-1) ... 
dpkg: error processing package ttf-mscorefonts-installer (--configure): 
 package ttf-mscorefonts-installer is not ready for configuration 
 cannot configure (current status `half-installed') 
Setting up synaptic (0.81.1) ... 
Error in function:  


```

---

### Post by rickm1945 on 2014-05-12
I started all over frrom the first post and I finally got the fonts installed. I thank all of you who assisted me in getting these fonts installed.

---

