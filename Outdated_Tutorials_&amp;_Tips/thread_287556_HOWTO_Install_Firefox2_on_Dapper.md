---
title: "HOWTO: Install Firefox2 on Dapper"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by dickohead on 2006-10-28
Download the tar.gz file from getfirefox.com, then extract it to your home folder by doing either of the following:

Right Click - Extract Here
or
```
tar -zxvf firefox-2.0.tar.gz
```

Then open up a terminal and type:
```
sudo mkdir /usr/share/firefox2
```
```
sudo cp -R /home/YOURNAME/firefox/* /usr/share/firefox2/
```
```
sudo ln -sf /usr/share/firefox/firefox /usr/bin/firefox
```

then close all current firefox windows and run firefox again.

Enjoy.

If anyone can let me know how to EASILY make a deb package from the firefox folder that would be sweet!

---

### Post by aysiu on 2006-10-29
I don't know about easily making a .deb, but this script--created by Nanotube and modified by me--will automatically download and install (fully integrated) the latest Firefox.
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by melissawm on 2006-11-04
So, WHY isn't there a firefox2 package in the Dapper repositories, if Dapper will continue to be supported? Why only Edgy? I don't get it! It's just not very logical that there's a package we can install via synaptic for Edgy but not for Dapper. Can someone explain why??

---

### Post by aysiu on 2006-11-05
> **melissawm said:**
> So, WHY isn't there a firefox2 package in the Dapper repositories, if Dapper will continue to be supported? Why only Edgy? I don't get it! It's just not very logical that there's a package we can install via synaptic for Edgy but not for Dapper. Can someone explain why??
Stability.

Adding newer versions of some packages and keeping older versions of other packages sometimes causes conflicts with dependencies and libraries.

Installing Firefox from Mozilla (as opposed to the one in the repositories) sets up a static binary that doesn't depend on much else.

---

### Post by tep200377 on 2006-11-05
Hey, thanks! .. Finally a straight forward and good HowTo on FF2 for us who try to convert to linux.
But i have one question since im a n00b. I can only start FF2 by  typing ./firefox in the /usr/share/firefox2/ folder .. How do i link it to the icon on the desktop ?

---

### Post by CurtisGall on 2006-11-05
Goto Accessories -> Alacarte Menu Editor
Click on Internet
Right click on the Firefox icon -> select Properties
In the entry editor in the command box either type in:
/usr/share/firefox2/firefox
or use the browse button navigate to the firefox2 directory select the firefox file then click the open button.
Then close entry editor and menu editor and click the firefox icon in the main menu and it should launch.
It should also work the same way for a desktop icon.
Just right click on the icon select properties -> click the launcher tab
Insert /usr/share/firefox2/firefox in the command box.

---

### Post by aysiu on 2006-11-05
> **tep200377 said:**
> Hey, thanks! .. Finally a straight forward and good HowTo on FF2 for us who try to convert to linux.
But i have one question since im a n00b. I can only start FF2 by  typing ./firefox in the /usr/share/firefox2/ folder .. How do i link it to the icon on the desktop ?
This HowTo isn't that straightforward, especially since it requires you to paste four commands in the terminal and doesn't integrate Firefox with Ubuntu.

Please--use this script: you paste only two commands (instead of four), and it integrates Firefox with Ubuntu so that the command *firefox* launches the new Firefox and so that new plugins will actually be used by Firefox 2.0:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by rantak on 2006-11-05
Or you can just get Swiftfox 2.0 .deb (Firefox that is compiled for different processor types) from [http://www.getswiftfox.com/debian.htm]("http://www.getswiftfox.com/debian.htm") and for example 

sudo dpkg --install swiftfox_2.0-1_pentium4.deb

---

### Post by dickohead on 2006-11-05
While it may not be entirely straight-forward, it works great! It also gets people using the terminal, which isn't such a bad thing. 
I don't agree that it doesn't "Integrate" Firefox with Ubuntu, when I run Firefox, Firefox2 loads up, so I'm not sure what you're talking about there.

Perhaps you should have said: Integrates better, as your script does make a couple more symbolic links and links to plugins under /opt. But the above still works, and doesn't do all of the work for people - some people like to know HOW TO do things, not just how to have it done for them - hence this being a howto. :D

---

### Post by aysiu on 2006-11-05
On a very basic level, your instructions work, but if you want people to learn how to do it, they can also go here:
[http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion)

That has a lot of commands to be copied and pasted.

Also, if you want people to understand things, you may also want to explain what the commands do instead of just telling people to copy and paste the commands.

It might make sense for you to have a disclaimer in the beginning: > This will go step by step on how to unzip Firefox 2.0 and allow you to launch it with the *firefox* command. Your plugins will not be integrated.

If you want a more automated process with a tighter integration (linked plugins, for example), try [this script.](http://www.psychocats.net/ubuntu/firefox) If you want a less automated set of commands for a tighter integration, the look at [this page](http://help.ubuntu.com/community/FirefoxNewVersion).

Options are good.

---

