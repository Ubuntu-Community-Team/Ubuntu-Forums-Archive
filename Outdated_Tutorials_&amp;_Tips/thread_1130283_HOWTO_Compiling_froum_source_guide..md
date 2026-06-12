---
title: "HOWTO: Compiling froum source guide."
date: 2009-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dragos240 on 2009-04-19
[CENTER][IMG]http://img179.imageshack.us/img179/1928/cfs.gif[/IMG]
[/CENTER]
 
**Note: **This tutorial on howto compile assumes you use the default version of ubuntu 8.10 intrepid ibex and firefox 3 and up.
[B]
Introduction[/B]:
If your an ubuntu user here, you may know the basics of downloading a program from the Add/Remove section of your Applications bar at the top of the screen, the synaptic package manager, or even the simple apt-get program run from the terminal. But say you need a program that is not in the repositories, what do you do now? You find the tarball and compile from source! Unfortunately this is a tad hard for the average user. This is why I am creating this tutorial, to show the basics of compiling from source.
[B]
Step 1[/B]: Tarballs; Finding, downloading, extracting:
Find the program you wish to compile. In my case, I want to compile xautoclick for a flash game I play. Go to it's homepage, In this case it's [sourceforge.net]("http://sourceforge.net"), I will simply download the latest tarball from the website as shown:
[IMG]http://img512.imageshack.us/img512/2409/xautoclick.png[/IMG]
I will click either the first link or the second, I will download the first one. When firefox asks you how you want to open your file, select "Archive manager" (This will be the default anyway), this example is shown below:
[IMG]http://img131.imageshack.us/img131/4565/downloadbox.png[/IMG]
Then press the "OK" button.

File-roller will appear (Archive Manager for GNOME), and will list one directory. Click on this once, and press extract, and select the folder you wish to extract the archive contents to. If the archive is not just a single folder and has many files, select all of the files by simultaneously pressing Ctrl and a, press extract, and create a new folder, after this, click the new folder and extract the contents of it to that folder.
[B]
Step 2[/B]: Configuring the program:

Configuring is a small step in compiling that detects the dependencies on your computer, making sure that everything is there in preparation for compiling. To know what dependencies you'll need to install, check the "INSTALL" file located inside the folder, this will ***usually*** tell you what you need to configure the program. In this case, the author and programer of xautoclick has not specified what dependendies needed to be installed, I will go through this.

First, open up a terminal by either typing:
Ctrl + F2 and then typing *gnome-terminal*, or
going into "Applications" then selecting accessories, and selecting terminal.

After the terminal is opened, go into the directory you created or extracted, by doing the following command:
cd [directoryname]

If you made spaces in the folder's name do this:
*folder\ with\ spaces*. If you had uppercase letters in your folder, then specify them when typing the command.

After your inside the folder, type:
*./configure*.
If the output says:
*Access Denied*, then you haven't enabled it to be run as an executable, you can do this by doing the following command:
*chmod +x example*

Now, if the output returns errors check the install file or play around with synaptic to find the correct dependencies. When the configure returns a clean output, you then have all the correct dependencies installed.
[B]
Step 3[/B]: "Making" the program.

Now that we've run configure, we now need to "make" the file, this is the compiling part, all you have to do now, is in the terminal while in the program's directory type:
*make*

this command will compile the program, the output will be a complete mess, I assure you this. If the compile result is successful there will be no errors at the bottom, if there are, then check your dependencies again, and then repeat. If all does as planned you will have your desired program sucessfully compiled.

**Step 4**: Installing the program for internal use (optional but reccomended):
Now this step is the easiest one, simply run:
*make install*

This will copy the program files to your bin directory in /usr, making it possible to run the programs without being inside the folder.
------------------------------------------------

I hope this helped all of you wishing to compile! Good luck! :popcorn:

Please provide feedback and seggestions.

---

