---
title: "Remove Aqsisteam/PPA"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by tmcq on 2012-11-12
Trying to use some 3D Modeling software, I installed Aqsisteam.  It never worked, and I've abandoned my attempt - but now I have a red triangle almost constantly telling me that my update is failing.  The errant files are associated with this Aqsisteam installation.  How do I get rid of it?

---

### Post by Cheesemill on 2012-11-12
Can you post the outputs of:
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

---

### Post by tmcq on 2012-11-14
Output as requested:

tmcq@Qtop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
tmcq@Qtop:~$ ls -l /etc/apt/sources.list.d

---

### Post by sandyd on 2012-11-14
> **tmcq said:**
> Output as requested:

tmcq@Qtop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
tmcq@Qtop:~$ ls -l /etc/apt/sources.list.d

Hi, can you post the output of
```

tmcq@Qtop:~$ ls -l /etc/apt/sources.list.d
```
you seem to have missed it in the above output ;)

---

### Post by monkeybrain2012 on 2012-11-14
Simply deleting the ppa from your source list cannot reverse what has been installed.You need to also downgrade the packages which have been installed from the ppa. 

To do this, install ppa-purge

```
sudo apt-get install ppa-purge
```

then run it

```
sudo ppa-purge ppa:aqsisteam/ppa
```

---

### Post by tmcq on 2012-11-16
> **sandyd said:**
> Hi, can you post the output of
```

tmcq@Qtop:~$ ls -l /etc/apt/sources.list.d
```
you seem to have missed it in the above output ;)

I got a "command not found" error from that attempt.

---

### Post by tmcq on 2012-11-16
> **monkeybrain2012 said:**
> Simply deleting the ppa from your source list cannot reverse what has been installed.You need to also downgrade the packages which have been installed from the ppa. 

To do this, install ppa-purge

```
sudo apt-get install ppa-purge
```

then run it

```
sudo ppa-purge ppa:aqsisteam/ppa
```

The first code did something...the second gave me:
Updating packages lists
W: Failed to fetch [http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: aqsisteam ppa
Warning:  Could not find package list for PPA: aqsisteam ppa

---

### Post by tmcq on 2012-11-21
Any more suggestions here?  Still dealing with the infernal red triangle, and the unsettling feeling that there is something on my computer that I can't control...that is why I dumped Windows!

---

### Post by Bashing-om on 2012-11-21
tmcq; Hi !

This is ubuntu - all things are under your control --no secrets!
However, it does take a lot of understanding to master your machine.
Addressing the situation at hand: There are -to my knowledge - two files where that error may originate; /etc/apt/sources.list and /etc/apt/sources.list.d (added ppas).
Your sources.list looks good.
The command to look at /etc/apt/sources.list.d I would have expected to return some value, if the file is empty ->total 0 ;
else ->a list of added ppas ;
The error "W: Failed to fetch [http://ppa.launchpad.net/aqsisteam/p...-i386/Packages]("http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/binary-i386/Packages")  404  Not Found" indicates a source still exist -> most likely in /etc/apt/sources.list.d  ....
Rerun sandyd's directive once more ..copy and paste to preclude errors on your part[terminal commands must be - letter/CASE/space/options - perfect to result in an expected output]
[INDENT]I am try'n to help <== BDQ

[/INDENT]

---

### Post by tmcq on 2012-11-21
tmcq@Qtop:~$ ls -l /etc/apt/sources.list.d
total 48
-rw-r--r-- 1 root root 130 Nov 17 12:48 aqsisteam-ppa-precise.list
-rw-r--r-- 1 root root 130 Nov 17 12:48 aqsisteam-ppa-precise.list.save
-rw-r--r-- 1 root root 134 Nov 17 12:48 chrysn-openscad-precise.list
-rw-r--r-- 1 root root 134 Nov 17 12:48 chrysn-openscad-precise.list.save
-rw-r--r-- 1 root root 176 Nov 17 12:48 google-chrome.list
-rw-r--r-- 1 root root 176 Nov 17 12:48 google-chrome.list.save
-rw-r--r-- 1 root root  59 Nov 17 12:48 google_list.list
-rw-r--r-- 1 root root  59 Nov 17 12:48 google_list.list.save
-rw-r--r-- 1 root root  82 Nov 17 12:48 precise-partner.list
-rw-r--r-- 1 root root  82 Nov 17 12:48 precise-partner.list.save
-rw-r--r-- 1 root root 165 Nov 17 12:48 private-ppa.launchpad.net_commercial-ppa-uploaders_puzzle-moppet_ubuntu.list
-rw-r--r-- 1 root root 165 Nov 17 12:48 private-ppa.launchpad.net_commercial-ppa-uploaders_puzzle-moppet_ubuntu.list.save

---

### Post by tmcq on 2012-11-21
Oh...and thanks BDQ!!!

---

### Post by Bashing-om on 2012-11-21
Now we can answer your question from first post !

You are going to delete the -no longer needed - and any other not wanted entries in
/etc/apt/sources.list.d ...
```
cp /etc/apt/sources.list.d  /etc/apt/sources.list.d-old
gksudo gedit /etc/apt/sources.list.d

```will require your password in order to make changes to your system.
Delete in the editor window the complete lines with the  2 references to "aqsisteam";
Documentation in any config file is always desirable -> suggest ya make a comment line and reference the original file, document that these lines removed(comment denoted by "#" as first character in each line of comments [#this is a comment])
Save your changes and exit the gedit utility.
Still in terminal execute the following terminal commands.
```
sudo apt-get update
sudo apt-get upgrade

```for info/confirmation of commands:
```
man man
man cp
man gedit
man apt-get

```remember ----->reading is good !

ya shud be good to go !
any errors -> post back ![INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by tmcq on 2012-11-22
I have no idea how to do the corrections you specified.  Do I simply run those codes in terminal - or is there more.  You mention an "editor window" and creating comment lines...WHERE and HOW?  I am fairly computer savvy - I've programmed in multiple languages, and use all different types of applications - but I always feel like I missed Calculus I and II and I'm trying to figure out Calculus III when reading solutions here.

(By the way - I find Calculus III to be much easier to understand...it was just an analogy).

---

### Post by monkeybrain2012 on 2012-11-22
> **tmcq said:**
> The first code did something...the second gave me:
Updating packages lists
W: Failed to fetch [http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/aqsisteam/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: aqsisteam ppa
Warning:  Could not find package list for PPA: aqsisteam ppa

Several possibilities

1) Server temporarily down, so just need to re-run ppa-purge again after a few hours.

2)Unlikely,  the repository is removed. You can check the ppa's webpage to make sure it is not the case.

3) Very likely. You have disabled the ppa from sources.list or sources.list.d because of other people's advice on this thread before you ran ppa-purge and as a result ppa-purge couldn't find it. To make sure that this is the case check sources.list to see if there is an entry for the ppa and check the directory sources.list.d to see if there is a file for the ppa. If no then you need to re-enable the ppa for ppa-purge to work (add it through synaptic, or "sudo add-apt-repository ppaname" in the terminal ..do whatever you did to add the ppa in the first place)

---

### Post by monkeybrain2012 on 2012-11-22
> **Bashing-om said:**
> Now we can answer your question from first post !

You are going to delete the -no longer needed - and any other not wanted entries in
/etc/apt/sources.list.d ...
```
cp /etc/apt/sources.list.d  /etc/apt/sources.list.d-old
gksudo gedit /etc/apt/sources.list.d

```will require your password in order to make changes to your system.
Delete in the editor window the complete lines with the  2 references to "aqsisteam";
Documentation in any config file is always desirable -> suggest ya make a comment line and reference the original file, document that these lines removed(comment denoted by "#" as first character in each line of comments [#this is a comment])
Save your changes and exit the gedit utility.
Still in terminal execute the following terminal commands.
```
sudo apt-get update
sudo apt-get upgrade

```for info/confirmation of commands:
```
man man
man cp
man gedit
man apt-get

```remember ----->reading is good !

ya shud be good to go !
any errors -> post back ![INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

Well problem is if he installed some packages from the ppa and they are causing problems disabling/removing the ppa is not going to solve the problem. If he knows exactly what he has installed from the ppa then yes, he can just remove the ppa, and then uninstall the offending package. But what if he upgraded something from the ppa because of dependencies? First he may not know what they are, secondly he won't be able to just remove them because they may be needed for other software. Now he could manually find them (in synaptic looking for local/obsolete packages) and downgrade them one by one to an earlier version. But ppa-purge does it quickly and easily PROVIDED OP HAS NOT REMOVED THE PPA.

---

### Post by Bashing-om on 2012-11-22
I can relate to how you feel. (we were all there at one time)..
OK, back to baby steps. As you were able to provide the requsted information back to this post, you have jumped over the biggest hurdle.
With the following commands in the terminal, you will copy the sources.list.d file located in the subdirectory "apt" located in the directory "etc" under the root "/" -> copy and paste back into your terminal to preclude errors .
I am going to use the "absolute" path to the files so that the commands are operable from anywhere you are located in the file's system hierarchy.
```
cp /etc/apt/sources.list.d /etc/apt/sources.list.d-old
```makes a backup copy of the current file (never can tell what might happen- always make a back door)
Now with the folowing you will open up the text editor "gedit" to make the corrections to the data-base file:
```
gksudo gedit /etc/apt/sources.list.d
```We use "gksudo" on graphical applications to gain administrative authority to effect the changes, rather than "sudo"
Documentation in any config file is always desirable -> suggest ya  make a comment line and reference the original file, document that these  lines removed(comment denoted by "#" as first character in each line of  comments [#this is a comment])
Save your changes and exit the gedit utility. --- The utility "gedit" can be used as a simple "WYSIWUG" (what you see is what you get) editor, and will be so in this case. You may make any number of comment lines to explain to yourself a-a year or so from now- what you did and why precceding each line with the "#" character.

Keep your mouse pointer on the gedit window to maintain focus on the gedit window.
arrow keys on the keyboard to move around in the file, delete key to  s l o w l y delete one character at a time until the two offending lines are removed.
type any key to input text.
save your changes -> press the disk drive icon -to the left of the word "save" in the gedit window's task bar.
exit gedit -> Press the red encircled "x" top left of the gedit window.
back in terminal you are going to update your sources' data base:
```
sudo apt-get update
```The next command from terminal, compares your system's database to the mirror site's database and make the adjustments on your system so all packages are up-to-date.,
```
sudo apt-get upgrade
```that should do it ..post back with any errors generated.
Reboot and all is good !

I find computers easy as logical --calculas III done me in ![INDENT][INDENT][INDENT]try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by monkeybrain2012 on 2012-11-22
> **Bashing-om said:**
> I can relate to how you feel. (we were all there at one time)..
OK, back to baby steps. As you were able to provide the requsted information back to this post, you have jumped over the biggest hurdle.
With the following commands in the terminal, you will copy the sources.list.d file located in the subdirectory "apt" located in the directory "etc" under the root "/" -> copy and paste back into your terminal to preclude errors .
.....
I find computers easy as logical --calculas III done me in ![INDENT][INDENT][INDENT]try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

???

Dude, OP is a new user. There is a much simpler way to do this with a gui. Open the software Centre, go to Edit > Software Sources > Other Software and uncheck the box for the PPA or right click it and choose "remove" then reload SC and that's it. Why make things unnecessarily complicated??!!

But like I said he shouldn't remove or disable the ppa if he needs to downgrade already installed packages.


EDITED: BTW this is even wrong

> gksudo gedit /etc/apt/sources.list.d

/etc/apt/sources.list.d/ is a directory and you can't edit it. What you want to say is to cd into it and delete the files associated with the ppa. The backup line for cp is also wrong because it is a directory and you have to copy it recursively, and it is completely unnecessary to back up the directory (not even need to back up sorces list as you can simply comment out entries, but I digress.)

---

### Post by Bashing-om on 2012-11-22
I respectfully disagree, as a New user It behooves greatly to learn the operating system -> what is so hard about a simple edit to a file ?
The referenced ppa seems to no longer be in operation and may indeed require removal of the packages, practice in terminal is a good thing.

[INDENT]just my 1 ponds worth ==> BDQ

[/INDENT]

---

### Post by monkeybrain2012 on 2012-11-22
> **Bashing-om said:**
> I respectfully disagree, as a New user It behooves greatly to learn the operating system -> what is so hard about a simple edit to a file ?
The referenced ppa seems to no longer be in operation and may indeed require removal of the packages, practice in terminal is a good thing.

[INDENT]just my 1 ponds worth ==> BDQ

[/INDENT]

Except that your instructions are also wrong. see my edit.

---

### Post by tmcq on 2012-11-22
> **monkeybrain2012 said:**
> 

3) Very likely. You have disabled the ppa from sources.list or sources.list.d because of other people's advice on this thread before you ran ppa-purge and as a result ppa-purge couldn't find it. To make sure that this is the case check sources.list to see if there is an entry for the ppa and check the directory sources.list.d to see if there is a file for the ppa. If no then you need to re-enable the ppa for ppa-purge to work (add it through synaptic, or "sudo add-apt-repository ppaname" in the terminal ..do whatever you did to add the ppa in the first place)

There are two Aqsisteam files in the "sources.list.d" directory:  Aqsisteam-ppa-precise.list, and Aqsisteam-ppa-precise.list.save.  I found several files titled sources.list - but none that have any reference to "Aqsisteam".

Can I just delete the two files?  Would that not solve my problem?

---

### Post by monkeybrain2012 on 2012-11-22
> **tmcq said:**
> There are two Aqsisteam files in the "sources.list.d" directory:  Aqsisteam-ppa-precise.list, and Aqsisteam-ppa-precise.list.save.  I found several files titled sources.list - but none that have any reference to "Aqsisteam".

Can I just delete the two files?  Would that not solve my problem?

To delete these two files, run

```
sudo rm /etc/apt/sources.list.d/Aqsisteam*
```then run

```
sudo apt-get update
```This would remove the ppa from your system.

(Note: these steps are the same as opening the Software Centre, go to Edit >  Software Sources > Other Software and choose the entry for Aqsisteam, right click and choose remove and then reload the SC)

 If Bashing-Om is correct that the repository for the ppa no longer exists (which explains the 404 error you get for running ppa-purge) this will fix error message in updating. But if you have installed programs from it which gives you troubles, you will still need to uninstall them. Removing the ppa doesn't uninstall the programs.

---

### Post by tmcq on 2012-11-22
sudo rm /etc/apt/sources.list.d/Aqsisteam*

This code did not work - I got 
rm: cannot remove `/etc/apt/sources.list.d/Aqsisteam*': No such file or directory

I then tried through software center.  Found the two entries and removed them as recommended.  I ran the update, but my error still remains.  I assume - as you have said - that I installed "programs from it..." but I do not know what that means or how to uninstall programs I'm not aware of.  Is there a way to search for the programs that may be involved in this error?

---

### Post by monkeybrain2012 on 2012-11-23
> **tmcq said:**
> sudo rm /etc/apt/sources.list.d/Aqsisteam*

This code did not work - I got 
rm: cannot remove `/etc/apt/sources.list.d/Aqsisteam*': No such file or directory

I then tried through software center.  Found the two entries and removed them as recommended.  I ran the update, but my error still remains.  I assume - as you have said - that I installed "programs from it..." but I do not know what that means or how to uninstall programs I'm not aware of.  Is there a way to search for the programs that may be involved in this error?

Maybe the wild card character * doesn't work and you have to run the rm commmand twice, one for each file.

Did you reload the software centre? What are the errors?

---

### Post by tmcq on 2012-11-27
Hey all - I haven't seen the update error symbol now for a few days...the above suggestions may have solved the problem.  Thanks for all the help.

---

### Post by Bashing-om on 2012-11-28
Hey ; Outstanding !

Pleased all is back in order.

Please mark this thread as solved from the thread tool menu at top of post. The solved mark helps others in many ways.

[INDENT]Happy ubuntu'n <== BDQ

[/INDENT]

---

