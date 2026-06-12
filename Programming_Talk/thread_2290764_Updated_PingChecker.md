---
title: "Updated PingChecker"
date: 2015-08-15
forum: Programming Talk
---

### Post by gerowen on 2015-08-15
Just uploaded an updated copy of one of my old python scripts called "pingchecker" and thought I would share it. I wrote it several years ago to make it easier for me to clean up my Active Directory container. We had a lot of old machine names in our container that no longer pointed to active machines, but with several hundred machines actively under our control in that same container, I didn't want to just start arbitrarily deleting hostnames. On top of that, I wasn't there when the whole shebang was initially set up, so I didn't have a copy of all the active hostnames we were supposed to have, and I did a poor job of maintaining records of computer names when I would reimage computers. To find out which computers were active and which were not without manually walking around and looking at them all, I wrote this script. I then went into our Active Directory container and unchecked all of the columns except "hostname", and exported that to a text file with one hostname per line, then just copied and pasted those hostnames into the terminal when it asked for targets.  Actually the copy I used at work never asked for hostnames, it would just look for a text file by a particular name that I would create by exporting hostnames from Active Directory, but I modified this one to ask for them so it's more useful for everyday users. This made it very easy to copy and paste several hundred hostnames, then just hit enter and walk away, and have the results exported to a nice text file for me to look at when I got back. I ran the script 2 or 3 times over the course of a couple of weeks to allow for people who might have taken a machine on a trip or other anomalies, and that allowed me to find a pattern of machine names that were consistently offline so I could delete them and remove the clutter from our Active Directory OU.

This updated version has been converted from Python 2 to Python 3, and with this particular one you must have Python 3 installed to use it, Python 2 doesn't seem to like some of the error handling. I've also added colored text output while the script runs, so if you want to review the results while it's still running, or just watch it run, you'll get a colored highlight around the ping results of each target to help you pick out the important information while it's running.  I'm thinking about building in an option to export the results to a .csv file since they're just plain text files, that way you can open it with your favorite spreadsheet editor and sort long lists of hosts by their "Up" or "Down" status, but I haven't been to bed in almost 24 hours, so that'll be a project for another day, :p

Download link: [http://sourceforge.net/projects/pingchecker/files/PingChecker_15.8.15.tar.gz/download](http://sourceforge.net/projects/pingchecker/files/PingChecker_15.8.15.tar.gz/download)
Project page: [https://sourceforge.net/projects/pingchecker/](https://sourceforge.net/projects/pingchecker/)

*I linked directly to the file because as of this post, SourceForge hasn't updated the download button on the project page to point to the newest version that I just now uploaded.*

**Screenshot**: The results as they look exported to a text file.
[ATTACH=CONFIG]263850[/ATTACH]

**Screenshot**: The program running, with results highlighted for easy review while it's still running.
[ATTACH=CONFIG]263849[/ATTACH]

---

### Post by gerowen on 2015-08-15
Gonna see about updating it again to include some simple cross platform GUI options, and to ask the user if they want to read hosts from an existing file or if they want to enter them manually.  Started working on that this evening.

---

### Post by gerowen on 2015-08-16
Almost finished with another update.

I've added graphical dialogs to replace the terminal, although the terminal will still be shown in the background for you to monitor longer operations in real time, and so you can see any error messages spit out by your Python interpreter.

I've added the option to either enter some targets manually (graphical window of course), or select a file to read targets from (graphical as well).

I've added a function that exports the results to a CSV file as well as the plain text file so if you have Office software installed, you can open the CSV file as a spreadsheet and sort the results by IP address, Up/Down status, etc.

I've added a built-in graphical text viewer for displaying the results to the user in a more user friendly fashion for Linux users.  I was using the "sensible-editor" command, which usually defaults to the terminal based "nano" editor, to keep from having to type a kajillion "try, except" arguments since it's no telling whether a user will have GEdit, KWrite, Kate, etc. installed on Linux.

I've accomplished the goals I set out for today which were to make it graphical, add .csv file support, let the user choose whether to enter files manually or read them from a file, and to display the results file graphically on all systems.  Right now I'm just reviewing everything to make sure I've accounted for possible errors and trying to make the code a little more efficient.

This is mostly just a little pet project for myself to get better at Python while improving on a tool I made for myself years ago.

Here's a screenshot of one of the graphical windows which embeds an image showing you how a file containing targets should look.  This immediately precedes the file selection dialog where you pick the file.
[ATTACH=CONFIG]263870[/ATTACH]

---

### Post by gerowen on 2015-08-16
New version (15.8.16) has been uploaded.

Project page: [https://sourceforge.net/projects/pingchecker/](https://sourceforge.net/projects/pingchecker/)

---

