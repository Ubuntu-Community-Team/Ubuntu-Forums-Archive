---
title: "Installing winedoors"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by apdc on 2008-08-06
Gentlemen:
I am new to linux and i keep on having the same difficulty when trying to install a program.  Once I download it the file or folder appears in a box named downloads.  From there I can't manage to unzip and unload.  when I double click a new box opens and is entitled Launch application.  From there I am supposed to choose an application...

Sometimes I stumble upon archive manager and that unzips and installs it, but I can't figure it out all the time.  I know this soundsverystrange to an expert but i guess I have been too close to windows environments.
can you help?

---

### Post by macaholic on 2008-08-06
Ubuntu uses a package system called dpkg, and generally you can install files ending in .deb, however the easiest way to install applications is through Synaptic System > Administration > Synaptic Package Manager. If it is not in there, try looking for it on sites such as [getdeb.net]("http://getdeb.net"), I know for a fact they have wine-doors available for download.

---

### Post by cardinals_fan on 2008-08-07
Download [this file]("http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb") and double click it.

---

### Post by apdc on 2008-08-10
Thanks for your reply. Your instruction were very clear and simple but I am still having challenges.  When I doubleclick,the launch application window opens and it states that the link needs to be opened with an application.  It then allows me to clkick a button named choose and when I click this another window opens with what appears to be a list of my program files..

I checked into my synoptic file manager and wine-doors is not listed.

please help!

---

### Post by k3lt01 on 2008-08-10
This is the link for Wine-Doors for Ubuntu and variants
[http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb](http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb)
I have used it and even though it lists programs it is very hit and miss, for example it lists Internet Explorer but it would not install it on my system.

---

### Post by apdc on 2008-08-10
Thanks very much for your reply.  I have been to that site and have downloaded the file.  The problem that I am having is not so much a winedoors issue than a basic installing stuff on Linux or xubuntu.  

The problem I am having is that once I download the file and try to install it, it is asking me to choose an application to open or execute it and i do not know what to choose.

thanks

---

### Post by k3lt01 on 2008-08-10
When you double click on the file you downloaded a Package Manager should open, not a window asking you to select a file. I believe you would be better off trying Ubuntu not Xubuntu to learn with, the extensive graphical nature of Gnome (the X windows environment) compared to the very basic graphical nature of Xcfe makes Gnome much easier to learn on for someone who has just come from a lifetime of Microsoft Windows.

---

### Post by Harpoon on 2008-08-10
apdc:  It could be that you need to install a small program named "dpkg"  You can get this in the repositories using synaptic (hit search, enter dpkg in the search box, then choose search the name only (not name and description).  From the files listed, choose the one that says dpkg (forget the other items for now) and install it.

Alternatively, you can do this from a terminal (cli) by opening a terminal from applications and typing 

sudo apt-get install dpkg

I've just come off two **very** long days of work and haven't yet had enough coffee, so if the post makes no sense, I apologize.
If all goes well, which it should, when you "double-click" on a file the ends in .deb, this program should automatically launch and you can just answer the simple yes/no questions to get the job done.

I assumed that this package was installed by default, and others have apparently made this assumption, too.  

I hope this solves your problem.

---

### Post by apdc on 2008-08-12
Thanks very much for your reply.  I was encouraged with the clarity of your understanding of the problem and solution.  Unfortunately, there is no real change.  dpkg was already installed and after installing all of the other items with dfkg in their names, there is still no change.

---

### Post by rixtr66 on 2008-08-12
do you have the gdebi package installed?you need it to install .deb packages
rick

---

### Post by cardinals_fan on 2008-08-12
Download [this file]("http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb") and place it on your desktop.  Open a terminal and type the following:
```
cd /home/yourusername/Desktop/
sudo dpkg -i wine-doors_0.1.2_all.deb
```
Does that work?

---

### Post by k3lt01 on 2008-08-13
Would it be possible for you to take a scree shot of each step you are doing and posting them here as you go? I m asking cause it should be working for you by what you are saying is installed yet it isn't so some screen shots if they are possible may be able to help a little.

---

### Post by Nymrat on 2008-12-04
Hello all,

In my experience, command-line tools such as apt-get and dpkg work a lot faster than their gui counterparts/front-ends.

I recommend learning to use them, but if you're happy just clicking away, **gdebi** would be the program to select. It should already be default, but I've been confused in the past trying to install .debs only to have the computer try to open them with ark or file-roller!

Also, if you're ever asked to select a program in a window with your home folder displayed (this happens to me with opengeu), navigate to /usr/bin/. If the one your looking for isn't there, it's probably in /bin/.

Hope someone finds this helpful!

---

