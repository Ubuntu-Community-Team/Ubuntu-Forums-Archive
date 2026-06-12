---
title: "Intrepid Adept help"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by AirWreck on 2008-11-01
Only two months into Kubuntu learning curve and stumped on this one...

I installed Intrepid beta a few weeks ago and couldn't get Adept to see uninstalled packages.  I ended up just going to an aptoncd disk I made and installed synaptic so I could install the rest of my desired packages.  The beta appeared to no longer be updating and was getting errors when I tried to run updates for the last few days so I did a fresh install of the official release this morning.  Same problem in Adept again, I can only see about five installable packages.  It seems like I have the usual repositories enabled and I tried toggling some of the buttons "installed," "not installed," etc., but no love.  sudo apt-get install synaptic is giving me no love from the command line.  I could do the aptoncd thing again but would have to install the various dependencies before getting to aptoncd.  I would like to get this right from the get go with this fresh install soooooo....

Am I missing something basic in this new Adept?  If nothing else, any tips on just getting plain old synaptic?  Thanks (FYI - running Dell Studio 15 laptop).

airwreck@airwreck-laptop:~$ sudo apt-get install synaptic
[sudo] password for airwreck:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
airwreck@airwreck-laptop:~$

---

### Post by gjoellee on 2008-11-01
Before I start helping you have you updated your system so you are at Kubuntu 8.10 Final version?

---

### Post by AirWreck on 2008-11-01
I believe so but not absolutely certain = I ran a "fetch list" in Adept after the install and then clicked on the new green update squiggle down in the menu panel.  I did the reboot and have run the fetch list a few times since with nothing new popping up.  Thanks in advance for your help.  BTW - when I run the "fetch" all of the Translation-en_US packages show as "failed."

---

### Post by gotaug on 2008-11-01
I've got a fresh/vanilla install of intrepid AMD64 final release.  Adept crashes after I put in my password, and won't even open to the password dialogue again, unless I reboot.

---

### Post by gotaug on 2008-11-09
My problem was having a wrong address in the sources.list file.  once I edited it out using Kate (launched as sudo kate in Konsole to make it possible to save the changes), then Adept started working again.  
  
Something as small as a bad repository address shouldn't crash the whole Adept application.  This is a real flaw in the program.

---

