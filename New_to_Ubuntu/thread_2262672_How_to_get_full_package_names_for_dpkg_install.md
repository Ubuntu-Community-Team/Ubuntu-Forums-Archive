---
title: "How to get full package names for dpkg install"
date: 2015-01-26
forum: New to Ubuntu
---

### Post by dan-roeder80 on 2015-01-26
I am new to Ubuntu and currently running v14.04.  I would like to install a package using dpkg.   This is just to learn how to install packages using dpkg not necessarily any specific package.  So first, I listed the available packages using the dpkg -l command.  I see a package called brasero.  I tried to install it using the following: sudo dpkg -i brasero.  I receive an error: cannot access archive: No such file or directory.  Obviously I didn't enter the full name of the package.  This is what I am having issues with trying to determine what the full name of a package is so I can install it.


When I use the dpkg -l command, I see all the application names down the left column, version information in the middle column and a description of what the application does in the right column.  But nothing tells me the exact package name I have to enter in order to install the application.


I have also used dpkg --get-selections and again brasero is displayed but not the full package name.  


How do I find the exact full package name in dpkg?  The full package name usually ends in .deb or something.  


I know there are easier ways to install packages but I would like to do this with dpkg for my own edification.

---

### Post by deadflowr on 2015-01-26
You actually have to have the .deb file to use dpkg to install it.

Did you download the .deb file?

Unlike apt(advanced packaging tool) which can be used to fetch and automatically install the package.

Basic how-to install a package with dpkg would be

First download the package.

Second open a terminal and then use cd(change directory) to move you into the directory where you downloaded the package.
(example, if you downloaded the package using firefox and used firefox's default download location you would cd in the Downloads folder, with cd Downloads)

Third run the dpkg install command : sudo dpkg -i package-name.deb
(hint use tab completion to help autofill; start typing the package name and press the tab button and it'll fill in the rest, magically) 

I don't know if any of this makes sense or helps...

---

### Post by dan-roeder80 on 2015-01-27
[[COLOR=#C61919]deadflowr[/COLOR]]("http://ubuntuforums.org/member.php?u=1276577")[COLOR=#000000]  - Thank you for the reply.  It made absolute sense.  I had run the -l command and saw a list of .deb packages and thought I could simply install from there similar to apt.  In addition, that tab autofill is awesome.  I will remember that one!  Again, thank you for your help.  I am going to download a .deb file and try the install per your instructions.[/COLOR]

---

### Post by Holger_Gehrke on 2015-01-27
One more important difference between apt and dpkg: apt takes care of dependencies automatically, dpkg doesn't. If a package you're trying to install needs something you have not installed yet, dpkg will fail while apt will fetch and install the needed package.

Actually apt is built on top of dpkg and uses it for the the basic functions and adds it's own additional features.

---

### Post by bapoumba on 2015-01-27
This one I have bookmarked : [http://debian-handbook.info/browse/stable/](http://debian-handbook.info/browse/stable/)
[http://debian-handbook.info/browse/stable/sect.manipulating-packages-with-dpkg.html](http://debian-handbook.info/browse/stable/sect.manipulating-packages-with-dpkg.html)

---

### Post by dan-roeder80 on 2015-01-28
The Debian Administrator's Handbook looks like an excellent resource for dpkg questions.  I'm not sure if your blog is still there.  I keep getting a timeout error trying to reach it.  I installed ppa-purge, ppa.  Hopefully I won't need it but you never know.  Thanks for the great resources.

---

