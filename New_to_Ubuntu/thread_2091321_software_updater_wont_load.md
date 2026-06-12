---
title: "software updater wont load?"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by jrjc on 2012-12-04
Hi,

quite new to ubuntu but have been using it for about a year without a hitch. I have 12.04 installed on an old sony viao and its never been so fast!! I originally started using it because I was stuck with the old computer and was so bored of looking at Windows. Since now I have fallen in love with it and it feels like the future, its just a lovely place to be! 

But I have encountered a problem hence posting on here. I tried to open Software Updater but it stalls and comes up with an error message and only the option to 'close':

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, EProblem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

I have absolutely no idea what to do so if anyone could help I would be really appreciative. I am a beginner but I can follow instructions so please go easy on me!!

PS. whenever I turn the machine on, an error message also comes up saying system problem detetced, report problem? When I click on report it then usually then says it can't report it? I will get the exact messages if anyone thinks it will help, but they were pretty ambiguous if I remember correctly. Thanks

thanks j

---

### Post by Frogs Hair on 2012-12-04
Run the following terminal command and post any errors in code tags using the # symbol on the reply box tool bar.  ```
sudo apt-get update 
```

---

### Post by ibjsb4 on 2012-12-04
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update

And welcome to the forum  :)

---

