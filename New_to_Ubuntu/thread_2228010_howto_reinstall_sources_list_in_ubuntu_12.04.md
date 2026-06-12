---
title: "howto reinstall sources list in ubuntu 12.04"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by okkie on 2014-06-05
my sources list got damaged somehow. How can I reinstall it or how can I reinstall 12.04 again.I have the original disk but it does not offer any reinstall option

---

### Post by slickymaster on 2014-06-05
You can use [The Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/") to generate a source list for your Ubuntu.


[LIST=1]
[*]Go to the Ubuntu Sources List Generator site.
[*]Select the Country where you want to download the repository from.
[*]Select your Ubuntu release.
[*]Scroll down the list and select the components that you want in your repository. The standard ones are &#8220;Main&#8221;, &#8220;Restricted&#8221;, &#8220;Universe&#8221;, &#8220;Multiverse&#8221;, &#8220;Security&#8221; and &#8220;Updates&#8221;. You can also include &#8220;Partner&#8221; and &#8220;Extra&#8221; to include additional software that are not provided by Ubuntu.
[*]In addition to the main sources, the Generator also include popular PPAs that you can include in your sources list. Simply check the box beside the PPA.
[*]Lastly, scroll all the way down to the bottom and press the &#8220;Generate List&#8221; button.
[*]On the next page, you should see three big boxes. The first box at the top contains the sources list that you have selected and you will need to copy/paste them into your sources.list file by opening a terminal window and running the following```
gksudo gedit /etc/apt/sources.list
```paste the sources lists into the file, save and exit.
[*]If you have added third party software&#8217;s PPA, it will show you the PPA key that you need to add to your system. Run the commands in your terminal, line by line.
[*]The third box is the alternate layout for Synaptic, which you can ignore most of the time.
[/LIST]

To complete the process, you need to update and upgrade your system:```
sudo apt-get update && sudo apt-get upgrade
```
That&#8217;s it.

---

### Post by okkie on 2014-06-05
This is what I get
madeleine@madeleine-Inspiron-1501:~$ deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy main restricted universe multiverse 
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Update Repos
madeleine@madeleine-Inspiron-1501:~$ deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-security main restricted universe multiverse 
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
madeleine@madeleine-Inspiron-1501:~$ sudo apt-get update
E: Type 'd' is not known on line 5 in source list /etc/apt/sources.list
E: The list of sources could not be read.
madeleine@madeleine-Inspiron-1501:~$ 
something else seems to be wrong

---

### Post by slickymaster on 2014-06-05
Did you follow exactly the steps I posted previously?

Can you please post back here the output you get when you run in a terminal the following:```
cat /etc/apt/sources.list
```

---

### Post by okkie on 2014-06-09
sorry for the long delays, new internet cables being installed.
here is the info:
deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
d## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receiveeb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise main restricted
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates main restricted
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates main restricted

 any
## review or updates from the Ubuntu security team.
deb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise universe
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise universe
deb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates universe
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates universe


madeleine@madeleine-Inspiron-1501:~$

---

### Post by slickymaster on 2014-06-09
Your sources list file is messed up. Please redo the steps I described in my first post, one by one, and replace the file. After doing it, please post back here the output you get from:```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by okkie on 2014-06-11
Your help is much appreciated. I have followed the steps to the best of my ability, Maybe my selection is wrong but here is the outcome of this round:
```
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Main Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Update Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Partner Repo
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Extras Repo
madeleine@madeleine-Inspiron-1501:~$ deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Main Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Update Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Partner Repo
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Extras Repo
madeleine@madeleine-Inspiron-1501:~$ deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise maingksudo gedit /etc/apt/sources.list
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$
```

---

### Post by okkie on 2014-06-11
You must have noticed okkie is doing the work and madeleine appearing all over, I am helping my daughter who I persuaded to use Ubuntu on her laptop.
Enjoy your day!

---

### Post by slickymaster on 2014-06-11
> **okkie said:**
> Your help is much appreciated. I have followed the steps to the best of my ability, Maybe my selection is wrong but here is the outcome of this round:madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Main Reposmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse deb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Update Reposmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse deb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse deb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Partner Repomadeleine@madeleine-Inspiron-1501:~$ deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partnerdeb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Extras Repomadeleine@madeleine-Inspiron-1501:~$ deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise mainNo command 'deb' found, did you mean: Command 'debc' from package 'devscripts' (main) Command 'derb' from package 'libicu-dev' (main) Command 'dab' from package 'bsdgames' (universe) Command 'debi' from package 'devscripts' (main) Command 'xdeb' from package 'xdeb' (universe)deb: command not foundmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise maindeb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Main Reposmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse deb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Update Reposmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse deb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse deb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Partner Repomadeleine@madeleine-Inspiron-1501:~$ deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partnerdeb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$ madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Extras Repomadeleine@madeleine-Inspiron-1501:~$ deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise mainNo command 'deb' found, did you mean: Command 'debc' from package 'devscripts' (main) Command 'derb' from package 'libicu-dev' (main) Command 'dab' from package 'bsdgames' (universe) Command 'debi' from package 'devscripts' (main) Command 'xdeb' from package 'xdeb' (universe)deb: command not foundmadeleine@madeleine-Inspiron-1501:~$ deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise maingksudo gedit /etc/apt/sources.listdeb-src: command not foundmadeleine@madeleine-Inspiron-1501:~$You're doing something wrong in the process, but as I'm not able to see what, here's what you're going to do:I've generate a sources list based on the following parameters: country -> South Africa; Ubuntu Release -> Precise Pangolin 12.04 with All of the Ubuntu branches repositories, Security - Important Security Updates, Security Sources Repository, Updates - Recommended Updates, Updates Sources Repository and Ubuntu Partner Repositories enabled. If you **_confirm that this are correct and aplly for your daughter computer_** what you have to do is:Open a terminal window (by pressing Ctrl+Alt+T) and run the following commands:```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.oldgksudo gedit /etc/apt/sources.list
```this will leave with an **/etc/apt/sources.list** file (completely blank) open with write permissions.Copy/paste all the text bellow to this file.```
################################################################################ OFFICIAL UBUNTU REPOS ###################################################################################### Ubuntu Main Reposdeb http://za.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse deb-src http://za.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse ###### Ubuntu Update Reposdeb http://za.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse deb http://za.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse deb-src http://za.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse deb-src http://za.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse ###### Ubuntu Partner Repodeb http://archive.canonical.com/ubuntu precise partnerdeb-src http://archive.canonical.com/ubuntu precise partner
```Save it and close Gedit.Now, again at a terminal window, run the following:```
sudo apt-get update && sudo apt-get upgrade
```and post here the output you get from it.

---

### Post by slickymaster on 2014-06-11
> **okkie said:**
> Your help is much appreciated. I have followed the steps to the best of my ability, Maybe my selection is wrong but here is the outcome of this round:
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Main Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Update Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Partner Repo
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Extras Repo
madeleine@madeleine-Inspiron-1501:~$ deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Main Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Update Repos
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Partner Repo
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$ 
madeleine@madeleine-Inspiron-1501:~$ ###### Ubuntu Extras Repo
madeleine@madeleine-Inspiron-1501:~$ deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
madeleine@madeleine-Inspiron-1501:~$ deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise maingksudo gedit /etc/apt/sources.list
deb-src: command not found
madeleine@madeleine-Inspiron-1501:~$

You're doing something wrong in the process, but as I'm not able to see what, here's what you're going to do:
I've generate a sources list based on the following parameters: country -> South Africa; Ubuntu Release -> Precise Pangolin 12.04 with All of the Ubuntu branches repositories, Security - Important Security Updates, Security Sources Repository, Updates - Recommended Updates, Updates Sources Repository and Ubuntu Partner Repositories enabled. If you **_confirm that this are correct and aplly for your daughter computer_** what you have to do is:
Open a terminal window (by pressing Ctrl+Alt+T) and run the following commands:```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
gksudo gedit /etc/apt/sources.list
```this will leave with an **/etc/apt/sources.list** file (completely blank) open with write permissions.
Copy/paste all the text bellow to this file.
```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://za.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://za.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://za.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://za.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://za.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://za.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
```
Save it and close Gedit.
Now, again at a terminal window, run the following:```
sudo apt-get update && sudo apt-get upgrade
```and post here the output you get from it.

---

### Post by robin7 on 2014-06-11
From 
```
madeleine@madeleine-Inspiron-1501:~$ deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy main restricted universe multiverse
```
and from
```
madeleine@madeleine-Inspiron-1501:~$ deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-security main restricted universe multiverse
```

I get the impression that an attempt was made to upgrade, then halted or failed. Up*grade* is not the same as up*date*. I got the two mixed up as well. Slickymaster's advice is exactly what you need todo, and I would only add one suggestion - that your new sources file should not include any of the old stuff. Delelte the whole thing and *replace* it with the one above, so that "Saucy Salamander" doesn't mess up your "Precise Pangolin."

---

