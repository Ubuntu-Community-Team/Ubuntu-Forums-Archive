---
title: "Gambas - general questions and discussion"
date: 2013-11-10
forum: Programming Talk
---

### Post by Tom_Carr on 2013-11-10
This is a thread for general Gambas questions and discussion.  

First thing, I am reposting this by kalaharix in another thread.   I think it is a good idea to install gambas3, even though the older gambas2 is the only one in the ubuntu software center

------------ kalaharix said:

[COLOR=#000000]The Gambas wiki refers to Gambas3. Gambas2 has not been updated for some time.[/COLOR]

[COLOR=#000000]I will give you my take on why Gambas3 is not in the Ubuntu Software Centre: It will not get into The Ubuntu Software centre if it is not in parent Debians repository. Debian is a very conservative distribution. Gambas is very active and constantly updated. Many of the dependencies that Gambas3 requires are newer than those used by Debian. Attempts have been made over the years to incorporate Gambas3 in to the Debian repository (an attempt is being made at the moment) but it is apparently a lot of work.[/COLOR]

[COLOR=#000000]Paradoxically, it is relatively easy to install Gambas3 on Ubuntu and derivatives by specifying a software source from within the Gambas community. There are currently two software sources for Gambas3: one for the stable release and another for the daily build. There are many instructions on the web using these sources. One set that I have written is at [/COLOR]

[http://kalaharix.wordpress.com/](http://kalaharix.wordpress.com/)

[COLOR=#000000]I have just used these instruction s to install Gambas3 on a fresh install of Lubuntu 13.10 and know it works on Ubuntu 13.10. Somebody has commented on the blog that it works on Mint 15. Many non-Debian derived distributions already have Gambas3 in their repositories.[/COLOR]

[COLOR=#000000]Gambas3 is well worth the effort and remains, to my mind, the finest application for data manipulation in Linux.[/COLOR]

---

### Post by Tom_Carr on 2013-11-10
Question - 
When you open gambas3, a screen comes up that lets you open a bunch of examples.  After you have been working with an a project or looking at an example, how can you get back to the list of examples and open a new one?  The only way I have found so far is to close gambas and reopen it.

---

### Post by Tom_Carr on 2013-11-10
Question -
Is there a gambus forum somewhere, or any other place that would be better to ask questions about gambas?

---

### Post by qamelian on 2013-11-10
Just as a matter of interest, if you are using Ubuntu 13.10, Gambas3 is in the Ubuntu repositories, so it can be installed with no hassle at all. :)

---

### Post by Tom_Carr on 2013-11-10
Thanks for the info.  I am still using 12.04.  I generally only update on the LTS versions.

---

### Post by kalaharix on 2013-11-11
'Gambas3 is in the Ubuntu repositories, so it can be installed with no hassle at all'

Yes but because of dependency problems it doesn't work (completely).  Gambas creator Benoit Minisini and the Debian maintainer are thrashing this out on the Gambas forum at the moment.

Do not use the repository version.

The Gambas 'forum', by the way is at [http://gambas.8142.n7.nabble.com/]("http://gambas.8142.n7.nabble.com/"). This is the primary information point.

There is also a more traditional forum at [http://whiteislandsoftware.com/forum/index.php?page=forumview&keep_session=749860054]("http://whiteislandsoftware.com/forum/index.php?page=forumview&keep_session=749860054")

---

### Post by jamesfbays on 2014-01-17
I'm now looking at gambas3 (after playing around with gambas2). I can see the improvements, and the documentation looks good. I'm sorry to see that there are (were?) some dependency problems. Gambas3 looks very promising for me. I hope every thing is good by 14.04 LTS.

---

### Post by kalaharix on 2014-01-19
Gambas3 may not be in the Debian repository but that does not stop you using it with Ubuntu. It really is easy to add an external data source from which Gambas3 (with all the necessary dependencies) can be installed. Just follow these really simple instructions (using Ubuntu 13.10):

1. Open the Dash Home (the top icon on the menu bar) and type <terminal> and then press the <enter> key (don't type the '<' and '>'). Click on the first 'Terminal' Icon to open the terminal.

2. Type the following line-by-line into the terminal. Press <enter> at the end of each line. If you are unused to the command line, it is best to copy-and-paste each line from here into terminal.  (<ctrl><v> from the keyboard does not paste in terminal. <right-click> instead and choose paste). At various points you will have to respond with your administrator password or with <y> for yes.

sudo add-apt-repository ppa:nemh/gambas3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gambas3

(dist-upgrade may find nothing to do: it depends how up-to-date your installation is).

Open Dash home again as above and type <gambas3>. The search should show the Gambas icon which you can load or drag onto the menu bar.

---

### Post by Tom_Carr on 2014-02-14
How do you set up a message as a function and move the response button info to a variable?  All I can find are examples like this:

[COLOR=#000000][FONT=monospace]PRINT Message("Program v0.3\\nVersion of 2006-03-28")[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]PRINT Message.Info("Program v0.3\\nVersion of 2006-03-28", "Fine")[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]PRINT Message.Warning("Your changes will be lost", "Save", "Ignore", "Cancel")[/FONT][/COLOR]

[http://gambasdoc.org/help/comp/gb.qt/message](http://gambasdoc.org/help/comp/gb.qt/message)

---

