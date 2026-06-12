---
title: "Help. Complete Newbie: how do I install a downloaded program .tar.bz2"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by Dehdreamer on 2011-12-10
Hi everyone a Ubuntu (and linux) complete newbie here. 

I only installed Ubuntu a few days ago and I'm still getting used to it and finding alternatives for some of my fav. windows program. I downloaded the linux version of [Celtx]("http://celtx.com/") but I have no idea how to get it running. I have found a program in the file that starts it but is there anyway to set up a desktop icon or something so I don't have to keep hunting through the folder to get into it and use it?

Sorry like a said I'm a complete Newbie but I'm working to figure this out.
Thanks for your time.

---

### Post by haqking on 2011-12-10
First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)

You can also use Gdebi package installer or look at dpkg.

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set 

Have fun

Regards

haqking

---

### Post by satanselbow on 2011-12-10
Installing from source isn't really recommended unless the current Ubuntu repo version is really out of date or not included. Different source bundles (tarballs) also require different handling so there isn't really a "one cure fits all" answer... however...

The current version of Celtx is in the repos ;)

Either install from software center or drop to a terminal and:

```
sudo apt-get install celtx
```

---

### Post by N00b-un-2 on 2011-12-10
> **Dehdreamer said:**
> is there anyway to set up a desktop icon or something so I don't have to keep hunting through the folder to get into it and use it?

in order to make a launcher (desktop icon) to open a program, simply right click on the desktop and select "create a launcher".  Then Type in a name for the application, a comment which describes what the application does, and the command that launches it.  If you wish to launch it from the folder where the executable file is then type in the actual location of the file, for example 

```
/home/your user name/Downloads/celtx/celtx
```

Another thing you may want to consider is adding the ability to launch the application with a single word command instead of having to point to it's actual location.  This is done very easily by creating a symlink to the executable binary file in /usr/bin or /usr/local/bin.  For example

```
sudo ln -s /home/your user name/Downloads/celtx/celtx /usr/bin/
sudo chmod o+x /usr/bin/celtx
```

Then to test your symlink, open a terminal or hit alt+f2 and type celtx.  That's it

---

### Post by Dehdreamer on 2011-12-10
Thanks guys :)

You've both been helpful but now I've got two more questions. 
 1) What's a repo? 
 2) I know know about the Ubuntu Software Center (cause it's in the launcher) how do I find others?

Thanks for the code satanselbow I think I know how to open a terminal so I'll try that. :)

Edit: Thanks N00b-un-2 I'll have to try that.:)

---

### Post by haqking on 2011-12-10
> **Dehdreamer said:**
> Thanks guys :)

You've both been helpful but now I've got two more questions. 
 1) What's a repo? 
 2) I know know about the Ubuntu Software Center (cause it's in the launcher) how do I find others?

Thanks for the code satanselbow I think I know how to open a terminal so I'll try that. :)

Edit: Thanks N00b-un-2 I'll have to try that.:)

[What is a repo]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by N00b-un-2 on 2011-12-10
> 1) What's a repo?
2) I know know about the Ubuntu Software Center (cause it's in the launcher) how do I find others?

1) a repo is short for "repository".  Its an online server that stores applications to be installed on your computer.  They are defined in a plain text file called /etc/apt/sources.list, or in individual lists in /etc/apt/sources.list.d/

2) Welcome to the magic of Ubuntu!  Ubuntu's use of PPAs is the thing that sets Ubuntu apart from every other Linux distro out there.  A "PPA" is a "Personal Package Archive".  
The best thing to do if you're looking for a specific application, before you try to compile it yourself or download a standalone binary would be to look and see if there is a PPA for it.  
For example, if you wanted to install Firefox daily build instead of the stable Firefox that ships with Ubuntu, you would Google "Firefox Daily PPA". which would lead you to the Firefox Daily PPA on Launchpad (most of them are on Launchpad) here [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa").  Then to add the repo to your sources, you open a terminal and add it.  The command looks like 

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```
Then update your sources
```
sudo apt-get update
```
and now the software in the PPA will be available for download.
issuing the command
```
sudo apt-get upgrade
```
would then upgrade Firefox, Yasm and Thunderbird (if you had them installed).

I'm not recommending that you install unstable Firefox.  I was just using it as an example and would actually strongly advise against upgrading to an unstable browser.  However, with that being said, often times bug fixes and work arounds will be created for applications that are not available in the static versions contained in the default Ubuntu Repos.  Applications that rely on web services such as Twitter or Pandora Radio (Gwibber and Pithos respectively) have broken apps in the default Ubuntu Repos because it takes a long time for the stable repos to update because of testing and bug fixes usually.  Installing the latest versions of those applications will restore functionality (being able to connect to your twitter or pandora account).

I hope that helps some.  I know it's a lot to take in for a newbie.

---

### Post by Dehdreamer on 2011-12-10
> **satanselbow said:**
> Installing from source isn't really recommended unless the current Ubuntu repo version is really out of date or not included. Different source bundles (tarballs) also require different handling so there isn't really a "one cure fits all" answer... however...

The current version of Celtx is in the repos ;)

Either install from software center or drop to a terminal and:

```
sudo apt-get install celtx
```

Ok so i tried to find it with the software center it still says it isn't there. I tried the terminal code once it said there was a duplicate source so i thought maybe my download was the problem so I deleted it and tried again and this is what i got..
[IMG]https://lh4.googleusercontent.com/-Nok3A92cMgo/TuNjnX_DY4I/AAAAAAAAAAg/zXMbV5k1Ha8/s720/celtx%252520help2.png[/IMG]

Now what?

EDIT: Noob you keep ninjaing me lol. Xp I've updated the mozilla repo but I'm still getting told it can't locate the celtx package.... *head scratch*

---

### Post by N00b-un-2 on 2011-12-10
celtx would not be in the Mozilla repo my friend.  There is no PPA for it as near as I can tell.  In a case like this, you will need to install it from the downloaded tar.bz2.
If you did add the mozilla daily ppa, you need to remove it.

---

### Post by haqking on 2011-12-10
> **N00b-un-2 said:**
> celtx would not be in the Mozilla repo my friend.  There is no PPA for it as near as I can tell.  In a case like this, you will need to install it from the downloaded tar.bz2.
If you did add the mozilla daily ppa, you need to remove it.

[https://launchpad.net/~colindean/+archive/ppa](https://launchpad.net/~colindean/+archive/ppa)
[http://www.ubuntuupdates.org/packages/show/197987](http://www.ubuntuupdates.org/packages/show/197987)

---

### Post by Dehdreamer on 2011-12-10
... ya I'm an idiot. How do I remove it? 

I've managed to find the wiki install instructions for it [here]("http://wiki.celtx.com/index.php?title=Installation") but now I'm getting errors since there's tar in the command line twice.... 

thanks for all you help.

---

### Post by N00b-un-2 on 2011-12-10
Correction.  I found it in the GetDeb.Net repo, which you can add using the following command.

```
wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu oneiric-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'
```

Then do

```
sudo apt-get update && sudo apt-get install celtx
```

---

### Post by Dehdreamer on 2011-12-10
> **haqking said:**
> [https://launchpad.net/~colindean/+archive/ppa](https://launchpad.net/~colindean/+archive/ppa)
[http://www.ubuntuupdates.org/packages/show/197987](http://www.ubuntuupdates.org/packages/show/197987)

Thanks haqking :)

---

### Post by N00b-un-2 on 2011-12-10
> **Dehdreamer said:**
> ... ya I'm an idiot. How do I remove it?

```
sudo rm -rfv /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-oneiric.list


sudo apt-get update
```

---

### Post by N00b-un-2 on 2011-12-10
There is always more than one way to skin a cat!  Often, individual devs will create PPAs for single apps, like colindean's PPA for celtx.  In this instance I would actually recommend you go with that PPA instead of the getdebs.net PPA because it only affects the application celtx instead of the hundreds of apps on getdebs.

---

### Post by Dehdreamer on 2011-12-10
N00b you're the BEST!... thanks for your help I just have one last question. I have three err messages. 
[IMG]https://lh6.googleusercontent.com/-qAEujO35RZo/TuNunUDNLOI/AAAAAAAAAA4/Bcnmhjc9cTQ/s640/celtx%252520help3.png[/IMG]

---

### Post by haqking on 2011-12-10
> **Dehdreamer said:**
> N00b you're the BEST!... thanks for your help I just have one last question. I have three err messages. 
[IMG]https://lh6.googleusercontent.com/-qAEujO35RZo/TuNunUDNLOI/AAAAAAAAAA4/Bcnmhjc9cTQ/s640/celtx%252520help3.png[/IMG]

we cant read your error messages.

add the image as an attachment so we can enlarge it

---

### Post by Dehdreamer on 2011-12-10
Sorry here you go.

---

### Post by N00b-un-2 on 2011-12-10
That error means that the getdebs repo isn't current or was configured for the wrong version.  My advice in this case would be to remove the getdebs repo and add the colindean repo.
```

sudo rm -rfv /etc/apt/sources.list.d/getdeb.list
sudo add-apt-repository ppa:colindean/ppa
sudo apt-get update && sudo apt-get install celtx
```

---

### Post by N00b-un-2 on 2011-12-10
@dehdreamer out of curiosity what version of Ubuntu are you running?  10.04?

---

### Post by Dehdreamer on 2011-12-10
ok... so if this works how do I open the program?
@N00b the newsest one on the ubuntu site... 11.10

---

### Post by N00b-un-2 on 2011-12-10
In that case if you added ppa:colindean/ppa, you're probably going to need to edit /etc/apt/sources.list.d/colindean.list and change all instances of 'oneiric' to 'lucid' since 10.04 was the last version that celtx was packaged for.  Then sudo apt-get install celtx and then you should be able to start the application with alt+f2 and type celtx.

---

### Post by Dehdreamer on 2011-12-10
ya I'm getting errors again so to make that edit I type in sudo first or just start with the edit/etc... 

and alright hopefully we're getting close :)

---

### Post by N00b-un-2 on 2011-12-10
the command you need to enter is 
```
sudo gedit /etc/apt/sources.list.d/colindean-ppa-oneiric.list

```
then change oneiric to lucid, save the file, sudo apt-get update and then sudo apt-get install celtx

---

### Post by Dehdreamer on 2011-12-10
my newbieness is showing again all I get is a blank file where do I change the oneiric to lucid?

EDIT: NVM musta typed something wrong second try it opened right. Changes made.

EDIT: I made the changes but it's now telling me that the file can't be found again.

---

### Post by oldos2er on 2011-12-10
> **N00b-un-2 said:**
> the command you need to enter is 
```
sudo gedit /etc/apt/sources.list.d/colindean-ppa-oneiric.list

```
then change oneiric to lucid, save the file, sudo apt-get update and then sudo apt-get install celtx

Graphical programs like gedit should be called with 'gksudo' or 'gksu'. [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

