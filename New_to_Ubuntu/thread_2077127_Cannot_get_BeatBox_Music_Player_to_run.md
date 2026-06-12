---
title: "Cannot get BeatBox Music Player to run"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by travelfool on 2012-10-27
hello all,

I have tried to install BeatBox music player but it will not open at all (no reaction when I open it from 'Dash Home') 

I am VERY new to Ubuntu (3 days old and proud) . I have 12.4 and all updates installed.
 I installed using Terminal command:
 

    sudo add-apt-repository ppa:sgringwe/beatbox
    sudo apt-get update && sudo apt-get install beatbox


 but like I said nothing happens when I click on the Beatbox Icon in Dash.


Firstly, what can I do to make it work?



Secondly, what is better - BeatBox or Clementine?


Thirdly, how do I uninstall BeaBox (or any other program for that matter?)


Lastly (bit of a tangent here), how do I view all the programs I have on my computer in one go?


Thank you in advance

---

### Post by mardybear on 2012-10-27
Hi travelfool...

I don't use Ubuntu 12 but do you have synaptic installed? Enter 'sudo synaptic' into terminal to find out. If so synaptic will show which software is installed...numerous filters are available. If not installed, you should be able to install it via terminal by entering 'sudo apt-get install synaptic'.

I believe Ubuntu 12 also uses another software manager i can't recall offhand - software center or something.

It could be that Beatbox is missing dependencies. If so uninstall via synaptic and reinstall. If additional dependencies are required, synaptic will let you know. If Beatbox isn't available, you may need to activate additonal repositories in synaptic.

I don't use either so can't comment with is better, Beatbox or Clementime.

Welcome to Ubuntu.

mardybear

---

### Post by NikTh on 2012-10-27
Hi and Welcome. 

OK, several questions here , I will try to do my best to answer most of them.
> **travelfool said:**
> 
I have tried to install BeatBox music player but it will not open at all (no reaction when I open it from 'Dash Home')
Firstly, what can I do to make it work?  

Try to run beatbox from the terminal , I assume is this command ```
beatbox
``` and post back here any messages in the terminal.
> **travelfool said:**
> 
Thirdly, how do I uninstall BeaBox (or any other program for that matter?) 
As you began with terminal I suggest to continue with terminal an be more familiar with it. Terminal is your best friend and your worst enemy (if don't know what you are doing). 

To uninstall a program run ```
sudo apt-get remove <package name>
```eg: ```
sudo apt-get remove beatbox
```If you want to remove the external repository (PPA) run 
```
sudo add-apt-repository --remove <repository name>
```eg:```
sudo add-apt-repository --remove ppa:sgringwe/beatbox
```There is a switch with remove command when you remove a package, named **purge**. Purge is useful when you want to remove completely a program (including configuration files) . In that case run ```
sudo apt-get remove --purge <package name>
```If you want to read about a command use the terminal with **man** command. 
eg: ```
man apt-get
```


> **travelfool said:**
> Lastly (bit of a tangent here), how do I view all the programs I have on my computer in one go?

You can view them from Ubuntu Software Center or Synaptic package manager. 

You have to install synaptic because is not installed by default (as USC is). 

```
sudo apt-get install synaptic
```From USC goto **Installed** and you will see. 
From Synaptic package manager click on **status** and then **installed**
From terminal give this commands 
```
dpkg --get-selections > installed.txt
gedit installed.txt
```> **travelfool said:**
> Secondly, what is better - BeatBox or Clementine? I cannot answer that because never used BeatBox or/and Clementine . 

Thanks

---

### Post by madinc on 2012-10-27
I also don't use those apps i use Rhythmbox only but to see, install or remove software i agree with mardybear synaptic is a great app but if  you prefer the terminal you can do it like this:

```
sudo apt-get remove "your-app-name-here"
```or

```
sudo apt-get purge "your-app-name-here"
```remove:
remove is identical to install except that packages are removed instead of installed. Note the removing a package leaves its configuration files in system. If a plus
sign is appended to the package name (with no intervening space), the identified package will be installed instead of removed.

purge:
purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).

---

### Post by travelfool on 2012-10-27
thank you all, loads of great help.

am guessing that as Ubuntu originally  came from the programmers world (i.e. teckies) and that UI (like I am used to) are not as central to the latter versions on this lovely open source land!!! thanks for expling more codes for Terminal (what other key ones are there and I is there a list anywhere?)

 found out from...
 [http://www.freesoftwaremagazine.com/articles/see_all_your_installed_applications_ubuntu_unity](http://www.freesoftwaremagazine.com/articles/see_all_your_installed_applications_ubuntu_unity)
...how to find all my programs (would like to think I would have eventually found it buy my self :oops:)

am going to use RB for my music for now (is this what you guys use?)

I noticed this message in Terminal when I was trying to install BB:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

and from nosing around on the Internet I think that the 'software updater' is blocking my progress for installing BB and other software I think. how can I get around this (I still want to keep it running all the time, jsut not when I want to install something)

thanks again all...

---

### Post by travelfool on 2012-10-27
meant to add this... [http://askubuntu.com/questions/99537/installation-error-unable-to-lock-the-administration-directory](http://askubuntu.com/questions/99537/installation-error-unable-to-lock-the-administration-directory) ...as a way to get around the problem but do not want to stop 'Software Updater'

Thank agian :)

---

### Post by BertN45 on 2012-10-27
Just wait software updater will finish after some time.

---

### Post by BertN45 on 2012-10-27
Clementine is good, I have tried it and liked it as a player, but not so much for maintaining the music db. You could also use e.g. quod libet or the standard rhytmbox. It is all a matter of taste. Quod libet is perfect to update the tags with the info about the songs and it has a nice album view and great search facilities.

---

### Post by travelfool on 2012-10-28
Hello BertN45,

thanks for the advice. It has been 48 hours and I still can not install BB. I think Software Updater is continually running in the background?

cheers

---

