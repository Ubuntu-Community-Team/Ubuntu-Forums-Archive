---
title: "Netflix desktop"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by talkingstove on 2013-04-23
I had netflix working for a while and all was good in the land.
Then that dang "silverlight update" rolled around, didnt see a way past it and ended up netflix because it didnt work anymore.
 
After trying all that I could I uninstalled netflix-desktop and wine altogether 
now for some reason I cant even install because I keep getting this error

$ sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package netflix-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  wine-browser-installer


E: Package 'netflix-desktop' has no installation candidate


Can someone please help me out? I have no idea what

---

### Post by VeeDubb on 2013-04-23
I've not had any issues with netflix desktop since I only use it rarely.  (I have a separate set-top box and my TV is a whopping 15 feet from the desktop, so I don't need it much)

Anyway, I believe the solution to your problem lies right there in the feedback you got from the terminal.  

The following packages replace it......


That generally means that the package you're trying to install has been superceded by something else, and it's trying to tell you what the replacement is.  Try installing the package it's telling you to install.

---

### Post by talkingstove on 2013-04-23
I have attempted to do so and get a very similar error
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine-browser-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'wine-browser-installer' has no installation candidate

I am now even more lost than before @_@

---

### Post by khelben1979 on 2013-04-23
Open up Ubuntu Software Center. Choose to search for package: netflix. What packages does it list for you?

---

### Post by talkingstove on 2013-04-27
"No items match "netflix""

---

### Post by khelben1979 on 2013-04-27
You definitely should check out [the Netflix homepage]("http://www.compholio.com/netflix-desktop/").
Read what it says and just follow the instructions. One important thing to note from what they have written: > Currently, Wine does not include all of the necessary patches to use Netflix "out of the box", so the PPA below also contains a custom build of Wine with the patches included.

You probably have a version of Wine in your Ubuntu system which is not capable of using Netflix. I don't know why your Software Center cannot find the package though, but continue to read from their webpage and you might note more things as well which should be of importance in this. Standard version of Wine shipped with Ubuntu, not compatible with Netflix.

---

### Post by dailyplummet on 2013-06-15
The simple way to set this up is to import the developer's package repository into your apt installer program.

Go to a terminal and type the following:

     sudo apt-add-repository ppa:ehoover/compholio

     sudo apt-get update

     sudo apt-get install netflix-desktop

When the netflix-desktop is installed, just type the command "netflix-desktop" and a modified version of wine will format your desktop for Netflix and start the program.

I would advise you have a later version of Ubuntu installed. I got this to work on versions 12.04 and later.

Good luck.

---

### Post by b|ackhole on 2013-10-28
I think I know what went wrong here, because the same thing has happened to me. But this happened after I went to completely clean Netflix-Desktop from my computer to reinstall it after it was behaving somewhat glitchy.

I went into the SPM and completely removed wine-browser-installer and related packages, including netflix-desktop and the silverlight plug-in. Since then even if I follow the suggestions here to apt-add-repository, update and install the netflix-desktop again it seems to have no clue what I'm looking for. I tried to launch it right from the dev file but in the Software Centre received a message saying there was an error.

- - -

I **[Solved]** this for myself by going into the Synaptic Package Manager. 
Edit > Reload Package Information
then
Settings > Repositories > Other Sources, and finding what was unselected and adding them back.

Then I went through the usual install process for Netflix and it was able to find the missing information. And ta-da, at least my netflix is working again. :D

---

