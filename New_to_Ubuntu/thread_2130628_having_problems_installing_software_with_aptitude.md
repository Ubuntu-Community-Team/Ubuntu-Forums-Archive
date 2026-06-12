---
title: "having problems installing software with aptitude"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by xyyz on 2013-03-30
i'm completely new to Linux, let alone Ubuntu.

i'm following the following tutorial: [http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194)

i'm having issue with this part:


[LIST=1]
[*]At the $ prompt, type **aptitude -y install vim-nox** for use instead of the built-in VI editor. [more info]("http://en.wikipedia.org/wiki/Vim_%28text_editor%29") 
[*]At the $ prompt, type **aptitude -y install p7zip-full** to install 7-zip archive utility. 
[*]At the $ prompt, type **aptitude -y install sendemail** to install a command-line email utility. 
[/LIST]

whenever i try entering these commands, the packages do not install.

here's an example of an error i get when trying to install sendmail:

```
Couldn't find any package whose name or description matched "sendmail"
Couldn't find any package whose name or description matched "sendmail"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

can someone help me out please?

---

### Post by Plueonic on 2013-03-30
Do you have the universe repository enabled? Open the software center > edit menu > software sources > check "community maintained...." 
Then, if the local cache doesn't start to update, run ```
sudo apt-get update
```

---

### Post by fantab on 2013-03-30
Open "Ubuntu Software Center" and install the packages you need. To be able to download and install certain software you need to enable "INDEPENDENT" and/or "PARTNER" Repositories. This can be done with "Software Sources".

By the way Ubuntu uses apt-get and not aptitude by default.

$ sudo apt-get install packagename

---

### Post by d0006 on 2013-03-30
Some suggestions:
(Obligatory DAGS comment).

I think your main problem is not running aptitude as root (sudo, sudo -i, etc).

Go here (very cool!) [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Generate a sources list.
ctrl-alt-t to open a terminal, ctrl-shift-t to open a second tab in the terminal window (the first tab will be "frozen" (whatever the correct term is) when you open Nautilus).
```
gksudo nohup nautilus
``` (gksudo is (one of) the correct method(s) to run a GUI program as root. nohup just lets you close the terminal without killing Nautilus.).
Navigate to /etc/apt/sources.list, double click on sources.list (it should open in gedit as root), immediately save as sources.list.old. 
Copy sources list (synaptic version), paste in gedit, save as sources.list.
Now use apt-get:
```
sudo apt-get update
sudo apt-get install vim-nox
```
Repeat sudo apt-get install for other packages.

This should be bullet proof.

I would install synaptic.  It works great for me.

---

### Post by oldos2er on 2013-03-30
Have you run ```
sudo apt-get update
```

---

### Post by DuckHook on 2013-03-30
Hello and welcome to both the forums and Ubuntu/Linux in general.

Could you tell us why you are trying to install sendmail? Unless your circumstances are non-standard, you don't need this app. Mail clients like Thunderbird, Evolution and Sylpheed can be configured to sync with your email provider and send through their smtp or imap server.

---

### Post by schragge on 2013-03-30
I guess the OP is trying to install [sendemail](http://manpages.ubuntu.com/manpages/precise/en/man1/sendEmail.1.html), not sendmail.

---

### Post by DuckHook on 2013-03-30
> **schragge said:**
> I guess the OP is trying to install [sendemail]("http://manpages.ubuntu.com/manpages/precise/en/man1/sendEmail.1.html"), not sendmail.

Ahh. My bad. Thanks for clarification. Going cross-eyed in my decrepitude.

---

