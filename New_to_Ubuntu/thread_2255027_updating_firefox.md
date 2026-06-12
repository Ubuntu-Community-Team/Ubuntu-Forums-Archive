---
title: "updating firefox"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by dave6 on 2014-12-01
Hi all

Firefox updates, I know that here on ubuntu it does not do it atuo, but needs done by hand or code into terminal, or some thing like tht.
The version of firefox that I am running here is version 22.0

First, is it worth updating to version  ??

Second, HOW ?

Thanks
Dave

---

### Post by sandyd on 2014-12-01
> **dave6 said:**
> Hi all

Firefox updates, I know that here on ubuntu it does not do it atuo, but needs done by hand or code into terminal, or some thing like tht.
The version of firefox that I am running here is version 22.0

First, is it worth updating to version  ??

Second, HOW ?

Thanks
Dave

Hi, what version of Ubuntu are you using?

---

### Post by folky2 on 2014-12-01
hello,

look here for install:
[https://support.mozilla.org/en-US/kb/install-firefox-linux](https://support.mozilla.org/en-US/kb/install-firefox-linux)

---

### Post by dave6 on 2014-12-01
ubuntu 12.04 64bit

Having looked at the above link, read the following: 1.Download Firefox from [the Firefox download page]("http://www.getfirefox.com") to your home directory.
Don't know where the home directory is at, so I will stop before I make a mess, did not even get to pt2
All I know "and care about" is when I down-load, they go to the down load folder

Dave

---

### Post by mikewhatever on 2014-12-01
That's very odd, I use 12.04 as well, and have Firefox 33 installed, which is regularly updated from the repositories.
Are you sure you have Ubuntu installed?

---

### Post by sandyd on 2014-12-01
Provided that you install updates, Ubuntu should automatically update Firefox. In this case, it is supposed to be at version 33 ([http://packages.ubuntu.com/precise/firefox](http://packages.ubuntu.com/precise/firefox))

What is the output of
```

apt-cache show firefox
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by ajgreeny on 2014-12-01
It sounds as if you must have downloaded the archive of FF at version 22 and are now using that instead of the repository version.

If I'm right, why did you do that?  You need to forget your old Windows ways of searching for applications on the web, and start using the Ubuntu repositories.

---

### Post by dave6 on 2014-12-01
> **ajgreeny said:**
> It sounds as if you must have downloaded the archive of FF at version 22 and are now using that instead of the repository version.

If I'm right, why did you do that?  You need to forget your old Windows ways of searching for applications on the web, and start using the Ubuntu repositories.

This computer has not been up-dated since the day I installed ubuntu 12, before that I think it was ubuntu 10, and I have no idea what "Ubuntu repositories" are, don'teven know where to find them
But, the day I did install this version of ubuntu, I also did this: [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks) to get rid of that supid windows looking thing down the side of the screen.......... the supid windows looking thing was a hidden file that came with the full version of office 96 / 97, they called it the task bar.

I don't do: searching for applications on the web.  I do email, evil bay and now I have to do that other waste of life ****-book, just to try and keep what little work I have coming in. PS when I get fed-up I take the odd read at mail online, the daily lies

I would give you a screen shot of what little stuff I have on this computer, only gimp will not load any screen shots into ??? nothing on clip brd it tells me.

Thats it, I'm otta here for the night
 TBC
Dave

---

### Post by deadflowr on 2014-12-01
Find the program called update manager (I think it's in Administration) and run it.
Then click Install when it lets you.
Then be patient.

If you've never updated , you'll have a lot of updates to install.

---

### Post by dave6 on 2014-12-02
> **deadflowr said:**
> Find the program called update manager (I think it's in Administration) and run it.
Then click Install when it lets you.
Then be patient.

If you've never updated , you'll have a lot of updates to install.

Thank you for the info, have just run the update manager as stated, and I was very patient.  

It took the update manager about 15 seconds to do it's bit and I quote

The software on this computer is up todate
The package information was just updated
There are no updates to install.

Ain't that a good-un, still only running firefox version 22 
Ubuntu
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-49-generic

Dave
SEE, (mikewhatever) am running ubuntu

> **sandyd said:**
> Provided that you install updates, Ubuntu should automatically update Firefox. In this case, it is supposed to be at version 33 ([http://packages.ubuntu.com/precise/firefox](http://packages.ubuntu.com/precise/firefox))

What is the output of
```

apt-cache show firefox
sudo apt-get update
sudo apt-get install firefox
```

done the above and got the below. short version ie the last bit...

```
daboss@daboss-desktop:~$ sudo apt-get update
[sudo] password for daboss: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB [5,492 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Fetched 5,492 B in 0s (13.0 kB/s)
Reading package lists... Done
daboss@daboss-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libbabl-0.0-0 libgegl-0.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daboss@daboss-desktop:~$
```

---

### Post by buzzingrobot on 2014-12-02
I don't know why, but what your system is telling you is wrong.  Hundreds of updates have been released since the intial release of 12.04, including kernel updates and important security patches.

The Ubuntu repositories are the servers that host all the packages installed on an Ubuntu system, and their updates. A correctly configured installation will alert the user that updates are available for installation.

Updates to Firefox are provided via a distribution's update system, not via Mozilla. 

It might be useful to post the contents of your "/etc/apt/sources.list" file here.

---

### Post by deadflowr on 2014-12-02
Post the output for
```
cat /etc/apt/sources.list
```
your apt-get update seems rather neutered.
(No precise-updates, or security repos listed)

---

### Post by jdeca57 on 2014-12-02
> **sandyd said:**
> Provided that you install updates, Ubuntu should automatically update Firefox. In this case, it is supposed to be at version 33 ([http://packages.ubuntu.com/precise/firefox](http://packages.ubuntu.com/precise/firefox))

Yes, but actually the latest version is 33.1.
Nothing bad, packagers take some time and test it. 
There exists a nice video on youtube:
[https://www.youtube.com/watch?v=3oLon1m3vl0](https://www.youtube.com/watch?v=3oLon1m3vl0)
That video comes from a Manjaro wiki (Manjaro is an Arch-like rolling & reasonably cutting edge distribution):
[https://wiki.manjaro.org/index.php?title=Install_Firefox_in_your_home_directory](https://wiki.manjaro.org/index.php?title=Install_Firefox_in_your_home_directory)
Their point is that a browser is the weakest point since you use it by definition to search lesser known sites and that it should be updated immediately after an update is released.
And that is a weak point for every distribution, so go to the source.

---

### Post by sandyd on 2014-12-02
> **dave6 said:**
> done the above and got the below. short version ie the last bit...

daboss@daboss-desktop:~$ sudo apt-get update
[sudo] password for daboss: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB [5,492 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Fetched 5,492 B in 0s (13.0 kB/s)
Reading package lists... Done
daboss@daboss-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libbabl-0.0-0 libgegl-0.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daboss@daboss-desktop:~$
You are missing a whole set of repositories. The only repos you have are the Universe repositories - the main repositories are missing

Run the following
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list

```

Paste the following
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```
Save the file by pressing CTRL+X and press 'Y' when asked to save.

Run
```

sudo apt-get update
sudo apt-get upgrade
```

Go for a walk while that completes, it will take a while.

Come back when its done, and try firefox again.

---

### Post by monkeybrain20122 on 2014-12-02
> **jdeca57 said:**
> Yes, but actually the latest version is 33.1.
.
I got 34.0 in today's update. Ubuntu doesn't always provide the minor version updates. Sometimes a minor version update may not be relevant to our platform, e.g Mozilla may push out a minor version update to fix a OSX bug, other times  a new major version  update is already around the corner.

---

### Post by dave6 on 2014-12-03
The thing is,, I have a very stable computer here, 2 bugs, 3 if you count me as one bug, "the end user bug, that don't know what he's doing" 
1. Screen shots don't paste to gimp
2. pdf files cut off the header when being printed, so I boot into (xp sic) when I have to print pdf file. 1 a week.

Apart from that, the computer does all that I need it to do, so going back to my first qustion
is it worth updating firefox to version 33 or 34 ?


Dave

---

### Post by buzzingrobot on 2014-12-03
> **dave6 said:**
> The thing is,, I have a very stable computer here, 2 bugs, 3 if you count me as one bug, "the end user bug, that don't know what he's doing" 
1. Screen shots don't paste to gimp
2. pdf files cut off the header when being printed, so I boot into (xp sic) when I have to print pdf file. 1 a week.

Apart from that, the computer does all that I need it to do, so going back to my first qustion
is it worth updating firefox to version 33 or 34 ?


Dave

Difficult to see how upgrading Firefox would affect those two unrelated issues.


Have you repaired your sources.list file and done a general update?

---

### Post by dave6 on 2014-12-03
> **buzzingrobot said:**
> Difficult to see how upgrading Firefox would affect those two unrelated issues.


Have you repaired your sources.list file and done a general update? No....................................it ain't broke so I ain't going to fix

To one and all a big thankyou
Can we call this dead

Cheers

Dave

---

### Post by deadflowr on 2014-12-03
> **dave6 said:**
> No....................................it ain't broke so I ain't going to fix


How would we know?
Your only post with any output was severely abbreviated , leaving us to not know what repos are enabled and what or not.
It helps to know the full output, so we can at least knock out the lack of enable repos as a cause of problems.

But anyway, if the problem is solved, or at least you think it is, mark it as such
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by wamses2 on 2014-12-05
Dave
For what it's worth, to answer your original question. No, it isn't worth changing, if 22 works for you I don't see any point in upgrading, quite a few of the releases have introduced new features, where new=annoying.

---

### Post by michael-piziak on 2014-12-05
> **dave6 said:**
> Thank you for the info, have just run the update manager as stated, and I was very patient.  

It took the update manager about 15 seconds to do it's bit and I quote

The software on this computer is up todate
The package information was just updated
There are no updates to install.

Ain't that a good-un, still only running firefox version 22 
Ubuntu
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-49-generic

Dave
SEE, (mikewhatever) am running ubuntu

Perhaps you could un-install the version of Firefox you have, then use the Software Center to install Firefox - then Firefox will be updated by your software updater (when there is an update for it).

---

### Post by buzzingrobot on 2014-12-05
The information you have included indicates that your /ets/apt/sources.list files is incomplete.  Hence, your system will be unaware of any available updates, not just the Firefox updates.   Help for correcting that was offered previously by Sandyd. If that does not resolve the issue, you should post the message generated by an update attempt as well as the contents of your /etc/apt/sources.list file.

---

### Post by dave6 on 2014-12-16
> **sandyd said:**
> You are missing a whole set of repositories. The only repos you have are the Universe repositories - the main repositories are missing

Run the following
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list

```

Paste the following
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```
Save the file by pressing CTRL+X and press 'Y' when asked to save.

Run
```

sudo apt-get update
sudo apt-get upgrade
```

Go for a walk while that completes, it will take a while.

Come back when its done, and try firefox again.

Back to this again, firefox has chucked the rattle out of the pram, done the above and got the following, including me mistyping my passwords
```
daboss@daboss-desktop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak[sudo] password for daboss: 
Sorry, try again.
[sudo] password for daboss: 
mv: cannot stat `/etc/apt/sources.list': No such file or directory
daboss@daboss-desktop:~$ #############################################################
daboss@daboss-desktop:~$ ################### OFFICIAL UBUNTU REPOS ###################
daboss@daboss-desktop:~$ #############################################################
daboss@daboss-desktop:~$ 
daboss@daboss-desktop:~$ ###### Ubuntu Main Repos
daboss@daboss-desktop:~$ deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
daboss@daboss-desktop:~$ deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

deb-src: command not found
daboss@daboss-desktop:~$ 
daboss@daboss-desktop:~$ ###### Ubuntu Update Repos
daboss@daboss-desktop:~$ deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
daboss@daboss-desktop:~$ deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
daboss@daboss-desktop:~$ deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
daboss@daboss-desktop:~$ deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
daboss@daboss-desktop:~$ deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

deb-src: command not found
daboss@daboss-desktop:~$ deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

deb-src: command not found
daboss@daboss-desktop:~$ deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

deb-src: command not found
daboss@daboss-desktop:~$ deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
WARNING:root:could not open file '/etc/apt/sources.list'

deb-src: command not found
daboss@daboss-desktop:~$ 
daboss@daboss-desktop:~$ ###### Ubuntu Partner Repo
daboss@daboss-desktop:~$ deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partnerWARNING:root:could not open file '/etc/apt/sources.list'

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
daboss@daboss-desktop:~$ deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
WARNING:root:could not open file '/etc/apt/sources.list'

deb-src: command not found
daboss@daboss-desktop:~$ 
daboss@daboss-desktop:~$ ###### Ubuntu Extras Repo
daboss@daboss-desktop:~$ deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
WARNING:root:could not open file '/etc/apt/sources.list'

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
daboss@daboss-desktop:~$ deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```

I am now lost what to do ???

HELP

Dave

---

### Post by deadflowr on 2014-12-16
You didn't sudo nano /etc/apt/sources.list like Sandyd posted.

nano is a command line text editor.
Simply run the command Sandyd posted, and then copy and paste the repository file that is posted.
The one that starts with
> #############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################



Copy that whole file.
You can right-click to paste
Then when it's pasted, click on ctrl +x, then type Y for yes, and then double check that the filename is correct and hoit enter.
Then run 
```
sudo apt-get update
```

---

### Post by dave6 on 2014-12-16
> **deadflowr said:**
> You didn't sudo nano /etc/apt/sources.list like Sandyd posted.

nano is a command line text editor.
Simply run the command Sandyd posted, and then copy and paste the repository file that is posted.
The one that starts with

Copy that whole file.
You can right-click to paste
Then when it's pasted, click on ctrl +x, then type Y for yes, and then double check that the filename is correct and hoit enter.
Then run 
```
sudo apt-get update
```

This bit
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list

When I do that I get

daboss@daboss-desktop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak[sudo] password for daboss: 
Sorry, try again.
[sudo] password for daboss: 
mv: cannot stat `/etc/apt/sources.list': No such file or directory
daboss@daboss-desktop:~$ 

NOTE: Sorry, try again.
That is not me putting in the wrong password, I have done this 5 times in a row and got the same "Sorry, try again."

Dave

I am going to restart this under a new thread......... But not now, tomorrow or maybe the day after

Thanks all

Dave

---

### Post by deadflowr on 2014-12-16
> **dave6 said:**
> I am going to restart this under a new thread......... But not now, tomorrow or maybe the day after

Thanks all

Dave

Do not start a new thread for this.
(We will either close it, or merge it into this one.)

post the output for
```
ls /etc/apt
```
Let's see if you have a sources.list file.

Or you can ignore the first entry from the command Sandyd posted and instead simply run the sudo nano command.
```
sudo nano /etc/apt/sources.list
```
And copy/paste the repo info from Sandyd's post.

A far as passwords go, it's very easy to either forget a character or have a Caps Lock on by mistake.
I do this routinely.
If it eventually let you run the command then that's that.
And Ubuntu has a default of 3 password attempts and then resets without executing the command.
It's been set like this, for as long as I've used Ubuntu. Do you remember playing around with any files, like sudoers?

---

### Post by spiffymoo on 2014-12-17
have u tried updating within firefox?

---

### Post by deadflowr on 2014-12-17
> **spiffymoo said:**
> have u tried updating within firefox?

Ubuntu's Firefox package disables that feature.

---

