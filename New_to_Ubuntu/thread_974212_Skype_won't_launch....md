---
title: "Skype won't launch..."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by DGZDGZ on 2008-11-07
Hello. I downloaded skype earlier on today and it was working fine. I've just tried to load it up and won't open. The skype menu & taskbar box flash up for a milli-second then disappear.

Can anyone help?

thanks.

---

### Post by brian_p on 2008-11-07
> **DGZDGZ said:**
> Hello. I downloaded skype earlier on today and it was working fine. I've just tried to load it up and won't open. The skype menu & taskbar box flash up for a milli-second then disappear.

Diagnosing the root cause may not be straightforward here so perhaps the best approach is to remove and purge skype and any dependencies which it pulled in. Then reinstall. Also backup the skype files in your $HOME.

```
mv skype_directory skype-backup
```

---

### Post by DGZDGZ on 2008-11-07
hi there, and thanks for the response. this will sound daft, but I can't see the skype program in the add/remove applications menu menu. is there a command i can use to remove it?

much appreciated?

---

### Post by brian_p on 2008-11-07
> **DGZDGZ said:**
> hi there, and thanks for the response. this will sound daft, but I can't see the skype program in the add/remove applications menu menu. is there a command i can use to remove it?

much appreciated?

On my system I'd do

```
sudo apt-get -s remove --purge skype
```

EDIT: Remove -s to really do it.

---

### Post by White Barry on 2008-11-07
> hi there, and thanks for the response. this will sound daft, but I can't see the skype program in the add/remove applications menu menu. is there a command i can use to remove it?

I'm sort of a noobie to this but I believe this should help:

```
sudo apt-get remove skype
```

not sure about the details on how to "purge" so maybe someone with a little more experience could assist

Edit: K listen to brian... like I said I'm still a noob

---

### Post by JeppeM on 2008-11-07
Try opening a terminal and then type "skype" and see if it gives you any errors when it starts up... Many programs will add errors to the terminal output when run from there if there's a critical error...

---

### Post by DGZDGZ on 2008-11-07
when i inputed 'skype' it returned 'aborted'

managed to remove app with the 'sudo apt-get remove -s' command. 

Reinstalling now, fingers crossed..........

---

### Post by DGZDGZ on 2008-11-07
can't believe it! 

reinstalled it and it's still doing the same thing](*,)

Anyone got an idea:?:

---

### Post by brian_p on 2008-11-07
> **DGZDGZ said:**
> can't believe it! 

reinstalled it and it's still doing the same thing](*,)

Anyone got an idea:?:

Where did you obtain your version of skype from?

---

### Post by JeppeM on 2008-11-07
Looks like you have something similar to this reported but: [#SCL-305]("https://developer.skype.com/jira/browse/SCL-305;jsessionid=4FDAC91FD631607A5CCB7B1D5603A4A3?page=all"). Try doing this from the commandline:
```
rm ~/.Skype/shared.xml
```
the command will delete the file shared.xml from your personal skype settings directory, it could be that file which is causing the problems. When done, try to start it again...

---

### Post by Sami_Sdata on 2008-11-07
You said you ran it earlier with no problems.  When you closed it did you close the program or just the window on the desktop?  It might still be running minimized in your system tray and just won't start a second copy.

---

### Post by B34ST1Y on 2008-11-07
try ```
sudo apt-get remove skype
```

then reinstall it straight from the website [www.skype.com](www.skype.com) - use gdeb to install it....it should be a straight .deb file...

---

### Post by Crafty Kisses on 2008-11-07
This has already been stated, you should try Skype from the Terminal and see if you get any error messages.

---

### Post by JeppeM on 2008-11-07
> **Codename said:**
> This has already been stated, you should try Skype from the Terminal and see if you get any error messages.
Yes it has lol :D He just got "aborted"

---

### Post by Crafty Kisses on 2008-11-07
If you create the following directory:
```
mkdir ~/.Skype/Logs
```
Does anything get written to it?

---

### Post by DGZDGZ on 2008-11-08
thanks for the help people!

I cannot understand this at all. I've tried using the sudo apt-get remove command to remove the program and reinstalled it again from the skype web site (which was where the working version was from originally). 

 I'm new to linux so please stick with me ](*,). ! A couple of questions on what i'm doing (or may be doing wrong)?

1. when i use the command line to remove the package, should the icon in the 'applications' drop down task bar menu automatically be removed- cos it always remains.

2. when i close the program after using it the last time, i closed it from the small minimized icon on the task bar. Is there a way to check that the program isn't running in the back ground?- something equivalent to task manager in windows?

3.  possibly the most stupid question of the 3:redface:, when i use the 'mkdir ~/.Skype/Logs' i can't locate the folder anywhere in the system folder- where would this folder be located?

many thanks in advance

DGZ

---

### Post by dracayr on 2008-11-08
2) System&#8594;administration&#8594;System monitor 
or ```
ps -e
```
3) with the command 'mkdir ~/.Skype/Logs', you created the directory Logs, which is in the .Skype directory, which is in your home directory

dracayr

---

### Post by DGZDGZ on 2008-11-08
It would appear that i'm destined not to use skype on my laptop. it runs fine on my linux partition on my desktop so i may as well admit defeat](*,) I'm also having trouble updating from the task manager now (i've got the stop sign logo on my taskbar). 

This may be a hardware fault, cos XP was glitchy on my laptop too!!

Many thanks for the help people!

---

### Post by JeppeM on 2008-11-08
> **DGZDGZ said:**
> It would appear that i'm destined not to use skype on my laptop. it runs fine on my linux partition on my desktop so i may as well admit defeat](*,) I'm also having trouble updating from the task manager now (i've got the stop sign logo on my taskbar). 

This may be a hardware fault, cos XP was glitchy on my laptop too!!

Many thanks for the help people!
One last thing before i give up :) Uninstall again using apt-get, and then do this commad in the Terminal:

```
rm -rf ~/.Skype
``` 

This will delete the entire .Skype directory, which i think is what's causing the problems for you (there's most likely a corrupt file in there somewhere). After that, install again... 

The reason you couldn't locate the .Skype/logs dir before is because anything starting with . on linux is hidden... If you go the your home folder in the file browser, and then press CRTL+h, then all the hidden directories will be shown - You'll notice that there's a lot in there, basicly this is where all your "personal" application data is being saved (firefox bookmarks, emails if you use an email program, settings of all kinds etc)... Be very careful, if you delete anything, you might end up having to set up one of your programs from scratch... To hide the folders again, press CRTL+h one more time.

I hope this helps you, Skype should without a doubt work, and we need to get it fixed! :D

---

### Post by DGZDGZ on 2008-11-08
Right.............

the remove code successfully removed the program.:D

 I re-installed from the skype website and the same thing happens(screen flashes up then disappears!)- except it's a different screen. Last time it was the main skype login screen, now it's the set up wizard- it only pops up for a fraction of a second then disappears, weird & confusing!:confused: 

](*,)loosing the will to skype](*,)

---

### Post by brian_p on 2008-11-08
> **DGZDGZ said:**
> 

](*,)loosing the will to skype](*,)

Run out of steam yet? Fancy installing from the Medibuntu repository? It goes like this:

[http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)

---

### Post by JeppeM on 2008-11-09
> **DGZDGZ said:**
> Right.............

the remove code successfully removed the program.:D

 I re-installed from the skype website and the same thing happens(screen flashes up then disappears!)- except it's a different screen. Last time it was the main skype login screen, now it's the set up wizard- it only pops up for a fraction of a second then disappears, weird & confusing!:confused: 

](*,)loosing the will to skype](*,)
Sorry man, i'm all out of ideas then :( Looks like you have tried everything, i honestly can't think of anything else which might help...

---

### Post by zippy_uk_2001 on 2009-02-08
Just to add to this in case it helps anyone else who's getting the same issue...

It doesn't seem to make any difference if you install from the package, or by adding the repository and installing that way.

If you add the ~/.Skype/Logs directory you do get a couple of logs created, but they're binary files, so I'll need to run them through something that can read them...
-rw-r--r-- 1 zippy zippy  3137 2009-02-08 16:51 skype_2009_02_08_165136.trace.txt
-rw-r--r-- 1 zippy zippy 13749 2009-02-08 16:51 skype_2009_02_08_165136.log

skype_2009_02_08_165136.trace.txt: data
skype_2009_02_08_165136.log: data

running from the command line doesn't give anything - just the 'aborted' message after the window pops up - I've tried getting a screenshot, but it disappears too quickly. 

Did try 
killall pulseaudio
in case it was that affecting things, but no difference

tried removing both the 
shared.xml
shared.lck 
files, no difference, 


/usr/bin/skype
/usr/bin/skype.real
doesn't make any difference if you do or don't run the skype script before the skype.real. So where the skype script loads v4l1compat.so it doesn't seem to that which is at fault

running skype with sudo, or actually su'ing to root also makes no difference

I'm going to try and do some more with the two log files - I'll post if I find anything.

for info...
$ skype --version
Skype 2.0.0.72

$ uname -a
Linux compaq-ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Skype-debian_2.0.0.72-1_i386.deb 

Cheers,
Zippy

---

### Post by zippy_uk_2001 on 2009-02-08
Found out that the window that's trying to launch in the "End User License Agreement" window, but it's blank, I tried clicking around the window to see if there was an active button, but it does appear to be an un-populated window, which (according to KDbg) is why it's aborting - there's no way for it to continue so it goes home.

I think that means we have no DIY way of fixing this - although very happy to be proved wrong!

For interest, I also tried running my two log files through a few tools and can't get any sense out of them - well, not with what I have anyway :-)

From here I think there are two options, firstly I'm going to try and find out if I can kid Skype into thinking I've agreed to the license agreement - maybe it just populates a file somewhere with a flag (if anyone has any ideas there feel free to chip in ;-) )?

If I can't get that to work then I'll uninstall this version and see if I can track down a previous, older version of Skype from somewhere.

I'll let you know how I get on.
Zippy

---

### Post by zippy_uk_2001 on 2009-02-24
bit more info that may be relevant - installed Skype on an Ubuntu server at work today and went in fine.

Noticed a slight difference on versions which may be part of the problem

Working ok on 2.6.27-12-generic
Not working on 2.6.27-11-generic

I'll see if I can get the update and try again - will post results

---

### Post by zippy_uk_2001 on 2009-02-24
Installed 2.6.27-12-generic - Skype now works fine

Didn't actually need to re-install it, just worked.

Zippy

---

### Post by zippy_uk_2001 on 2009-03-02
Note: Found it wasn't the kernel patch that actually fixed it - but 'something' in the process of applying patches to the machine. Not every patch will fix it though, which means there must be some common file(s) that get updated in certain pacthes that affect Skype working.

-Zippy

---

### Post by ucob012z on 2011-05-26
salam...

try re install the skype following the url below,

[http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)

maybe can help.....

---

### Post by tim73 on 2011-05-26
The current problem (May 26th, 2011) is solved simply removing ~/.Skype/shared.xml file and starting Skype. It asks for license agreement, click ok and then it should work normally.

---

### Post by s.fox on 2011-05-26
Necromancy.  Please start a new thread.

Thread Closed.

---

