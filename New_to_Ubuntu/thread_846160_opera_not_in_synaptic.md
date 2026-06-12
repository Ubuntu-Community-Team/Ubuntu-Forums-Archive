---
title: "opera not in synaptic?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by PureRicanGringo on 2008-07-01
OK, I am trying to revert the version of Opera back to 9.27 because there are a pair of websites that seem to work better there but I keep running into a problem. I originally installed Opera by downloading it directly from the website but now when I try to install the older version I am told that a later version already exists on my system. I thought, "OK no big deal, I will lock the version in synaptic." For some reason Opera is not showing up in either the add/remove programs list or in synaptic. What am I doing wrong?

Thanks in advance. :-)

---

### Post by pedro_orange on 2008-07-01
So you installed Opera from a .deb originally?

You may need to do a command line removal if that is indeed what you are trying to do:

```
sudo dpkg -r package-name
```

---

### Post by PureRicanGringo on 2008-07-01
> **pedro_orange said:**
> So you installed Opera from a .deb originally?

You may need to do a command line removal if that is indeed what you are trying to do:

```
sudo dpkg -r package-name
```

Thank you so much for responding. It sounds like you are right about working from the command line, but I am not sure of the official name of the package I need to remove. I tried just calling it "opera" but that didn't work. Do you have any suggestions?

Also, in your opinion why would searches for "opera" in both the add/remove and synaptic not bring back any results?

---

### Post by pedro_orange on 2008-07-01
I'm not 100% sure why exactly, but when you install stuff from .debs they are not added to a list that is maintained by Synaptic and Add/Remove.

However, all the software you install will be known by dpkg.

You can list all the installed software on your machine using the following command:

```
dpkg -l
```

To make it more readable pipe it into less:

```
dpkg -l | less
```

Space bar goes down a page. You could try grepping it:

```
dpkg -l | grep opera
```

Either way, you should find the package name from that list. Then you can go ahead and do the:

```
dpkg -r package-name
```

Goodluck.

---

### Post by hyper_ch on 2008-07-01
who tells you there's a newer version? Opera?

---

### Post by PureRicanGringo on 2008-07-01
> **hyper_ch said:**
> who tells you there's a newer version? Opera?

Thanks for asking. I attached a thumbnail of what comes up.

---

### Post by hyper_ch on 2008-07-01
Hmmm, I see - did you manually install Opera 9.5?

---

### Post by Colonel Kilkenny on 2008-07-01
Try installing Opera 9.51 RC3 instead of 9.27. There really shouldn't be any reasons to downgrade.

[http://my.opera.com/desktopteam](http://my.opera.com/desktopteam)

---

### Post by PureRicanGringo on 2008-07-02
> **Colonel Kilkenny said:**
> Try installing Opera 9.51 RC3 instead of 9.27. There really shouldn't be any reasons to downgrade.

[http://my.opera.com/desktopteam](http://my.opera.com/desktopteam)

I really don't quite understand why I am having such a hard time with this. I have managed to successfully install other programs.:confused:

Anyway, I downloaded 9.51 RC3 and unpacked it to my desktop. I then opened it up and clicked on something that said "install". Anyway, now that I have done this I can't get any version of Opera to open up. 

I think ideally, I would uninstall every part of Opera and try it from scratch from synaptic.

---

### Post by pedro_orange on 2008-07-03
Hey, sucks this is still an on going problem for you.
So, I've just installed Opera 9.51.2061 - downloaded from the website, and just opened the deb and installed.

Now I'm going to uninstall it.

So I'm going to check my dpkg list, and search for the string 'opera'

```
pedro@pedro-laptop:~$ sudo dpkg -l | grep opera
[sudo] password for pedro: 
ii  eject                                      2.1.5-6                                            ejects CDs and operates CD-Changers under Li
ii  opera                                      9.51.2061.gcc4.qt3                                 The Opera Web Browser
pedro@pedro-laptop:~$ 

```

Ok so it's found it.
So now I'm going to uninstall it, cause now I know the package name is called opera.

```
pedro@pedro-laptop:~$ sudo dpkg -r opera
(Reading database ... 140215 files and directories currently installed.)
Removing opera ...
pedro@pedro-laptop:~$ 
```

Hope this helps.

---

### Post by PureRicanGringo on 2008-07-21
> **pedro_orange said:**
> Hey, sucks this is still an on going problem for you.
So, I've just installed Opera 9.51.2061 - downloaded from the website, and just opened the deb and installed.

Now I'm going to uninstall it.

So I'm going to check my dpkg list, and search for the string 'opera'

```
pedro@pedro-laptop:~$ sudo dpkg -l | grep opera
[sudo] password for pedro: 
ii  eject                                      2.1.5-6                                            ejects CDs and operates CD-Changers under Li
ii  opera                                      9.51.2061.gcc4.qt3                                 The Opera Web Browser
pedro@pedro-laptop:~$ 

```

Ok so it's found it.
So now I'm going to uninstall it, cause now I know the package name is called opera.

```
pedro@pedro-laptop:~$ sudo dpkg -r opera
(Reading database ... 140215 files and directories currently installed.)
Removing opera ...
pedro@pedro-laptop:~$ 
```

Hope this helps.

Wow, thank you for trying. The thing is that I just don't understand why this is so freaking hard, you know? I mean why can I not get any version of Opera to open? I have tried installing it directly from the opera website and everything appears to be OK, but when I click on the little Opera icon in applications nothing happens.

I then followed your advice on how to find and remove Opera (thank you, by the way) and then searched for and found Opera 9.27 in synaptic and installed it from synaptic, but the same problem, I can't find a way to get it to open up.

Jake

---

### Post by Elfy on 2008-07-21
Try to rename the hidden folder so that when opera starts it recreates it. Open anautilus, do Ctrl+H to see hidden files - look for .opera and remove period from beginning of name - then try and open opera.

If it still doesn't open - open a terminal and try to run opera from there with ```
opera
```

---

### Post by PureRicanGringo on 2008-07-21
> **forestpixie said:**
> Try to rename the hidden folder so that when opera starts it recreates it. Open anautilus, do Ctrl+H to see hidden files - look for .opera and remove period from beginning of name - then try and open opera.

If it still doesn't open - open a terminal and try to run opera from there with ```
opera
```

OK, it sounds like you are on the right track. How do I find the hidden file in order to rename it? I opened up terminal and coded in "opera" but I got the following:

> bigdog@BigDog-Ubuntu-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/bigdog/lib/opera/9.51/opera: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
bigdog@BigDog-Ubuntu-desktop:~$ 


What do you think?

---

### Post by Elfy on 2008-07-21
> Open nautilus, do Ctrl+H to see hidden files - look for .opera and remove period from beginning of name - then try and open opera.;)

---

### Post by PureRicanGringo on 2008-07-21
> **forestpixie said:**
> ;)

OK, I removed the period, no problem. I then tried to start Opera but nothing. I tried going back to terminal and just typing "opera" but I got the same error message so I went to applications and tried clicking on the "opera" icon and nothing at all. How should I be trying to open it?

---

### Post by Elfy on 2008-07-21
If it's going to open anyway will do ;) , as it's not best to do it with terminal until it is fixed, then you can see error messages.

Uninstall it - again :) then run this in a terminal to move the .opera folder again.

```
mv ~/.opera ~/.operabackup
```

Now reinstall opera - I would go fo the opera one rather than the synaptic version, but as it's caused some problems previously with some sites - you choose. Once it's installed run it from the terminal. Post any error messages here, I'll be back in a while.

Now that we have an error message a quick search found many similar errors so that's a good start

[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=ERROR%3A+ld.so%3A+object+%27libawt.so%27+from+LD_PRELOAD+cannot+be+preloaded%3A+ignored&sa.x=0&sa.y=0](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=ERROR%3A+ld.so%3A+object+%27libawt.so%27+from+LD_PRELOAD+cannot+be+preloaded%3A+ignored&sa.x=0&sa.y=0)

---

### Post by PureRicanGringo on 2008-07-21
> **forestpixie said:**
> 

Uninstall it - again :) then run this in a terminal to move the .opera folder again.

```
mv ~/.opera ~/.operabackup
```

Now reinstall opera - I would go fo the opera one rather than the synaptic version, but as it's caused some problems previously with some sites - you choose. Once it's installed run it from the terminal. Post any error messages here, I'll be back in a while.

Now that we have an error message a quick search found many similar errors so that's a good start

[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=ERROR%3A+ld.so%3A+object+%27libawt.so%27+from+LD_PRELOAD+cannot+be+preloaded%3A+ignored&sa.x=0&sa.y=0](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=ERROR%3A+ld.so%3A+object+%27libawt.so%27+from+LD_PRELOAD+cannot+be+preloaded%3A+ignored&sa.x=0&sa.y=0)

OK when I coded

```
mv ~/.opera ~/.operabackup
```

I got:

>  mv ~/.opera ~/.operabackup
mv: cannot stat `/home/bigdog/.opera': No such file or directory


Anyway, it looks like there is nothing to move because it is completely removed by the uninstall problem, right? Anyway, I am going to go to the Opera website and install the 9.51 version.

---

### Post by PureRicanGringo on 2008-07-21
OK,

I just downloaded opera-9.51-2061.gcc3-shared-qt3.i386 to my desktop. What is the best way to install it so that it will freaking open? :)

I really feel like this is all because I am doing something so stupid that it doesn't even occur to the people on these forums to ask me about because it is so basic. I am sorry for being so dense.

---

### Post by Elfy on 2008-07-21
Double click it and it should install with Gdebi.

---

### Post by PureRicanGringo on 2008-07-21
> **forestpixie said:**
> Double click it and it should install with Gdebi.

What, exactly, should I double click on? I have double clicked on just about everything I can find in the file that looks remotely likely. I have found a number of executable text files but none of them do anything when I click on them. I mean, a few of them come up and ask me if I want to run them either in terminal or just run them but it does not matter what I select as nothing happens in either case.

---

### Post by aysiu on 2008-07-21
Paste these commands into the terminal: ```
sudo apt-get remove opera
wget -c ftp://get.opera.com/pub/opera/linux/927/final/en/i386/shared/opera_9.27-20080331.6-shared-qt_en_i386.deb
sudo dpkg -i opera_9.27-20080331.6-shared-qt_en_i386.deb
``` The first command will uninstall Opera 9.5. The second command will fetch 9.27 from Opera's website. The third command will install the old version.

---

### Post by PureRicanGringo on 2008-07-22
> **aysiu said:**
> Paste these commands into the terminal: ```
sudo apt-get remove opera
wget -c ftp://get.opera.com/pub/opera/linux/927/final/en/i386/shared/opera_9.27-20080331.6-shared-qt_en_i386.deb
sudo dpkg -i opera_9.27-20080331.6-shared-qt_en_i386.deb
``` The first command will uninstall Opera 9.5. The second command will fetch 9.27 from Opera's website. The third command will install the old version.

When I pasted the first two commands into terminal everything appeared to work fine. When I pasted the third I got the following:

>  sudo dpkg -i opera_9.27-20080331.6-shared-qt_en_i386.deb
(Reading database ... 151980 files and directories currently installed.)
Preparing to replace opera 9.27-20080331.6 (using opera_9.27-20080331.6-shared-qt_en_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera


Does what I am doing wrong jump out at you?

---

### Post by SunnyRabbiera on 2008-07-22
you need the libqt3-mt package, its easy to get via synaptic.
As for installing opera's older versions make sure to remove the hidden opera folder in your home directory, by oping up home and pressing ctrl- h and deleting the .opera directory.
Also try to use the static qt packages, and not the default one listed on opera's website

---

### Post by aysiu on 2008-07-22
```
sudo apt-get -f install
``` should fetch the missing dependency for you.

---

### Post by PureRicanGringo on 2008-07-22
I appreciate everyone trying to help, but so far nothing is really working. I do not mean to whine, I know that anyone that takes the time to even try to help me deserves my thanks, I just want to take a step back and restate my problem.

Just to refresh, all I want to do is to be able to use some version of Opera. I would prefer to be able to use the most recent (9.51) version of Opera but at this point I will take anything I can get. The odd thing is that nothing that anyone has had me paste into terminal has gotten that to work.

My original question had to do with why, on my system at least, I could not do a simple add/remove application or synaptic search and find Opera in the list of available apps. Now just a little while ago, after pasting who remembers what, it appeared that the 9.27 version was there in synaptic but installing it did not work. It seems to me that something is fundamentally wrong with some setting on my system for this not to be working. In my small experience Opera should be in synaptic. I should at least be able to download it and have the gdeb package thingy work for me, right? Doesn't this mean that something is not right?

---

### Post by aysiu on 2008-07-22
If you go to System > Administration > Software Sources and enable the Partner repository (I think it's the second tab from the left), and then Reload when prompted, Opera should be available in Synaptic.

I don't know why this isn't working for you. Every time I've wanted to give Opera another go (and then gone running back to Firefox, but that's another story), I've just downloaded the .deb from the Opera website and double-clicked it, and everything worked.

I don't think your situation is typical, but we'll try to help you fix it however we can.

---

### Post by stmiller on 2008-07-22
Opera is not included in the standard Ubuntu repos. This is somewhat due to the opera distribution license. Opera does not allow it to be distributed by anyone but them, and Ubuntu is also picky about what software is included due to the license a particular package has. Just go to the opera website to get opera. :)

---

### Post by Pawcatuck on 2008-07-22
To find Opera, I opened Synaptic Package Manager, opened the Settings menu, and chose Repositories. 

A window opened. The second tab was Third-Party Software, and I X'd the first of two entries, which is:

**[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy** partner.

Then I hit the Close button, and then Reload from Synaptic's top menu.

Opera is now in my list. Think I'll install it right now; I always loved Opera and wouldn't use anything else back in my Windows days.

(A minute later) Just FYI, it's version 9.27 in the partner repo.

---

### Post by PureRicanGringo on 2008-07-24
> **Pawcatuck said:**
> To find Opera, I opened Synaptic Package Manager, opened the Settings menu, and chose Repositories. 

A window opened. The second tab was Third-Party Software, and I X'd the first of two entries, which is:

**[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy** partner.

Then I hit the Close button, and then Reload from Synaptic's top menu.

Opera is now in my list. Think I'll install it right now; I always loved Opera and wouldn't use anything else back in my Windows days.

(A minute later) Just FYI, it's version 9.27 in the partner repo.


OK, I was able to get Opera (version 9.27) to show up in synaptic. I selected it for installation and hit apply or whatever it is. Then after watching it go through the install process I then tried to open Opera from "applications" with no luck. Meaning absolutely nothing happens that I can see. Then I opened terminal and coded in "opera" and got this error message:

> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/bigdog/lib/opera/9.51/opera: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Does this mean anything to anyone?

---

### Post by Elfy on 2008-07-24
The error is soemthing to do with java - can you open a terminal and run these and post outputs

```
 sudo updatedb
locate libjvm.so
locate libawt.so
cat ~/.opera/javapath.txt
```

---

### Post by PureRicanGringo on 2008-07-24
OK, I keep trying different stuff. This time I followed the link provided by Colonel Kilkenny to the Opera Desktop team's site and downloaded the .deb for 9.52. Once it had downloaded and package installer tried to install it I got the message that appears in the screenshot.

Anyway, does that mean that I need to download something called "libqt3c102-mt", and if so how do I do that? What does it mean? Why are we here? Are we alone? Getting angsty.

---

### Post by Elfy on 2008-07-24
I have libqt3-mt installed - but not the one you refer to, try to install that and then run gdebi again with the deb file.

```
sudo apt-get install libqt3-mt
```

---

### Post by PureRicanGringo on 2008-07-24
> **forestpixie said:**
> The error is soemthing to do with java - can you open a terminal and run these and post outputs

```
 sudo updatedb
locate libjvm.so
locate libawt.so
cat ~/.opera/javapath.txt
```

OK, I did:
```
sudo updatedb
```

And I get:

>  sudo updatedb
bigdog@BigDog-Ubuntu-desktop:~$ 


(in other words, nothing happened at all)

I do:
```
locate libjvm.so
```

and get:

>  locate libjvm.so
/usr/lib/gcj-4.2-81/libjvm.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/server/libjvm.so


I do:

```
locate libawt.so
```

And I get:

> locate libawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so


Finally, I do:

```
cat ~/.opera/javapath.txt
```

And I get:

>  locate libawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so
bigdog@BigDog-Ubuntu-desktop:~$ cat ~/.opera/javapath.txt
cat: /home/bigdog/.opera/javapath.txt: No such file or directory


Does any of this make any sense to anybody? Why is this so hard? Is it something I am doing?

---

### Post by PureRicanGringo on 2008-07-24
> **forestpixie said:**
> I have libqt3-mt installed - but not the one you refer to, try to install that and then run gdebi again with the deb file.

```
sudo apt-get install libqt3-mt
```

Also, I did this:

```
sudo apt-get install libqt3-mt
```

And I get:


>  sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt3-mt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Elfy on 2008-07-24
No it doesn't make a great deal of sense to me :D - I didn't expect an output to the updatedb command, I did expect an output for the other three.

You haven't got the last file - we can make it and see if that helps, I'm not completely sure what is happening. To make the file run this command

```
nano /home/bigdog/.opera/javapath.txt
```

Paste this in

> /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/
Ctrl+O and enter, then Ctrl+X

Then see if it boots.

---

### Post by Elfy on 2008-07-24
Further I can't understand why you now get dependency problems for a package which exists and was presumambly there when you first installed the 9.5* version before you wanted to revert to 9.27.

---

### Post by PureRicanGringo on 2008-07-24
> **forestpixie said:**
> Further I can't understand why you now get dependency problems for a package which exists and was presumambly there when you first installed the 9.5* version before you wanted to revert to 9.27.

Dude, I am to the point now where I can barely remember why I started this whole mess. I think it was because there were a couple of websites that were not rendering correctly in 9.5. Anyway the point is that now I would consider it a major victory to be able get any version at all of Opera to run.

---

### Post by PureRicanGringo on 2008-07-24
> **forestpixie said:**
> No it doesn't make a great deal of sense to me  - I didn't expect an output to the updatedb command, I did expect an output for the other three.

You haven't got the last file - we can make it and see if that helps, I'm not completely sure what is happening. To make the file run this command

Code:

nano /home/bigdog/.opera/javapath.txt

Paste this in

Quote:
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/
Ctrl+O and enter, then Ctrl+X

Then see if it boots. 


Well, I was able to do what you said without getting any weird error messages. Once that was done I went ahead and tried to open opera by coding "opera" in terminal. What I got was this:

>  opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/bigdog/lib/opera/9.51/opera: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


My whole point is that I need to be able to access this website:

retailer.echostar.com

It won't work in Firefox and it was giving me problems in Opera 9.50 but in Opera 9.27 it was working pretty well.

---

### Post by Elfy on 2008-07-24
No idea then - aysiu has been here once and I expect will do so again, perhaps (s)he has some idea of what the deal is, certainly usually has; I can't see from the error and search results what can be done.

Can't see if the site works here as I have no logon details.

Sorry I can't be of more help.


The only other thing I could suggest would be to reinstall java as all the searching I've done points to it not working correctly with opera.

---

### Post by aysiu on 2008-07-24
I have no idea.

I Googled the *error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory* error message, but it just led to a lot of dead-ends.

---

### Post by Elfy on 2008-07-24
I hoped you'd pitch up :)

Everywhere I look it points at a java problem - I thought I had it with this - but I apparently have a problem too- becauase the second command of post 4 fails for me as well - but I don't think I have a problem?

[http://www.linux-archive.org/kubuntu-user/108957-how-do-i-get-opera-work.html](http://www.linux-archive.org/kubuntu-user/108957-how-do-i-get-opera-work.html)

---

