---
title: "Sinq pc to android tablet"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Primus1 on 2012-10-12
Hi I have Dropbox on my Nexus 7 Tablet and Ubuntu 10.04 desktop computer. I installed it using the Terminal with the code Dropbox gave. Everything works fine but I have to run Dropbox from the command line using this command:

~/.dropbox-dist/dropboxd

Is there a way to add a shortcut to my apps or an icon on my desktop area?

Thanks.

---

### Post by androssofer on 2012-10-12
> **Primus1 said:**
> Hi I have Dropbox on my Nexus 7 Tablet and Ubuntu 10.04 desktop computer. I installed it using the Terminal with the code Dropbox gave. Everything works fine but I have to run Dropbox from the command line using this command:

~/.dropbox-dist/dropboxd

Is there a way to add a shortcut to my apps or an icon on my desktop area?

Thanks.

this should help:

[http://www.howtogeek.com/106470/create-desktop-shortcuts-in-ubuntu-11.04-and-11.10/](http://www.howtogeek.com/106470/create-desktop-shortcuts-in-ubuntu-11.04-and-11.10/)

---

### Post by audiomick on 2012-10-12
Hallo. 
When you say that you have to start the application from a terminal, this indicates, based on the command you quoted,  an executable file in the folder /home/<user-name>/.dropbox-dist, where <user-name> is of course your user name. If you don't know this to be a fact, you can look by enabling "view hidden files" in the view menu of the file manager, Nautilus, and having a look. When you have found the file that is being executed by that command, you can add an entry pointing to it to your applications menu, or add a starter to your task bar.

The starter is easy: Right click on the task bar (panel?) at the top of that screen and select "add to panel", select "user defined" and use the search button in the window to navigate to the executable file and associate it with the new starter.

For the menu: go to system> settings> menu (might be called "main menu". I'm guessing, mine is in German...). Select the menu you want to add the entry to out of the tree on the left pane. Click "add" on the right, and associate with the executable as above by using the "search" button.

Hope this gets you where you want to go.

---

### Post by Primus1 on 2012-10-12
Thanks guys, I will be back to this tomorrow to try your advice.

---

### Post by Primus1 on 2012-10-13
Thanks audiomick, your instructions worked. I had to wrestle it a bit because some of the things you mention had different names to your German systems but very pleased I managed it, thanks.
Thanks too androssofer for taking the time to answer, the link you gave is useful.

Marking this thread as 'solved'.

---

### Post by audiomick on 2012-10-13
Glad you got it sorted

---

### Post by Primus1 on 2012-10-14
:)

---

