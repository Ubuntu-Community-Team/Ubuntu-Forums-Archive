---
title: "Something so simple, yet so frustrating, please help."
date: 2008-05-09
forum: New to Ubuntu
---

### Post by pwharity on 2008-05-09
Hello.  Downloaded new Audacious Skins to my desktop. Extracted them to a NEW FOLDER I created.  Unable to drag that folder to usr/share/audacious/skins as I get, Error moving file: Permission denied.  When I try to grant permission to the folder "Skins" I get,"net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share."

First Question: What changed since 7.10 and why do I need this SAMBA thingie if I am moving from one folder to another on my own computer, not sharing to another user or computer over network?  Someone please explain this to me. I have perused the forum and there is mention of a BUG?

---

### Post by tamoneya on 2008-05-09
you need to have root permissions to do this.  Hit Alt-F@ and type ```
gksudo nautilus
```This will launch the file browser and you should do all the file copying within that.

---

### Post by lgastmans on 2008-05-09
[QUOTE=pwharity;4916525]Hello.  Downloaded new Audacious Skins to my desktop. Extracted them to a NEW FOLDER I created.  Unable to drag that folder to usr/share/audacious/skins as I get, Error moving file: Permission denied.  When I try to grant permission to the folder "Skins" I get,"net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share."

Try the following, something I do once in a while when I get the same permission denied:
Open up a terminal
type cd /usr/share/audacious/
type sudo chmod -R 777 skins (this will set all permissions for the folder skins)
then try to drag the folder and see.

---

### Post by hyper_ch on 2008-05-09
> **lgastmans said:**
> Try the following, something I do once in a while when I get the same permission denied:
Open up a terminal
type cd /usr/share/audacious/
type sudo chmod -R 777 skins (this will set all permissions for the folder skins)
then try to drag the folder and see.

DO NOT DO THAT! It is very bad advice circumventing the security precautions on the system by just randomly chmod anything to 0777!

---

### Post by malathion on 2008-05-09
> **hyper_ch said:**
> DO NOT DO THAT! It is very bad advice circumventing the security precautions on the system by just randomly chmod anything to 0777!

I agree. Please follow tamoneya's advice.

---

### Post by lgastmans on 2008-05-09
ok guys, i agree, but on your own machine?
he could always learn up the different options for chmod and give himself the rights
right? or wrong?

---

### Post by Wim Sturkenboom on 2008-05-09
> 
ok guys, i agree, but on your own machine?

You teach yourself bad habits. One day you are appointed as e.g. a sysadmin in a *nix environment and you do the same.

---

### Post by hyper_ch on 2008-05-09
even on your own machine it's bad.

---

### Post by lgastmans on 2008-05-09
Ok, will try to kick the bad habit :)

But we are talking only about the fact that I said 777 right? A more discreet approach as in using chmod u+x would be permissible right?

---

### Post by hyper_ch on 2008-05-09
giving rwx permission to the world on any system folder is not a good habit...

---

### Post by malathion on 2008-05-10
> **lgastmans said:**
> Ok, will try to kick the bad habit :)

But we are talking only about the fact that I said 777 right? A more discreet approach as in using chmod u+x would be permissible right?

Really, there is never a reason to change permissions on a system folder. If you want to interact with it, use sudo. :)

---

### Post by lgastmans on 2008-05-11
Thanks guys, lesson learnt.

But one last question, though: the person who originally posted this thread, in case it is someone who has no knowledge of using a terminal, how does he copy his files to that "skins" system folder? I mean, apart from using "sudo nautilus" or "sudo krusader" or "sudo cp...".

Just wondering

---

### Post by malathion on 2008-05-11
> **lgastmans said:**
> Thanks guys, lesson learnt.

But one last question, though: the person who originally posted this thread, in case it is someone who has no knowledge of using a terminal, how does he copy his files to that "skins" system folder? I mean, apart from using "sudo nautilus" or "sudo krusader" or "sudo cp...".

Just wondering

Well, if you eliminate all the ways of doing it, then he doesn't. Keep in mind that your proposed solution requires familiarity with the terminal as well.

---

### Post by ikt on 2008-05-11
> **tamoneya said:**
> you need to have root permissions to do this.  Hit Alt-F@ and type ```
gksudo nautilus
```This will launch the file browser and you should do all the file copying within that.

and why again does a person need to launch a file manager from terminal to install a media player skin?

as opposed to winamp where you double click on a skin and it installs automatically..

somethings not right..

---

### Post by Drakkor on 2008-05-11
```
gksudo nautilus
``` is for Kubuntu
```
sudo nautilus
``` is for Ubuntu

---

### Post by inportb on 2008-05-11
> **Drakkor said:**
> ```
gksudo nautilus
``` is for Kubuntu
```
sudo nautilus
``` is for Ubuntu

To the contrary. gksudo is for Ubuntu/GNOME. kdesu is for Kubuntu/KDE. and sudo is for terminal.

---

### Post by Drakkor on 2008-05-11
Hmmmmmm. I just always use sudo nautilus :)

---

### Post by inportb on 2008-05-11
> **Drakkor said:**
> Hmmmmmm. I just always use sudo nautilus :)

And I always use *sudo kate*. :)

I haven't run into this problem before, but some people have pwned their .ICEauthority files by using sudo on some graphical apps (the file became root-owned, and had to be fixed).

---

### Post by lgastmans on 2008-05-12
> **malathion said:**
> Well, if you eliminate all the ways of doing it, then he doesn't. Keep in mind that your proposed solution requires familiarity with the terminal as well.
right you are, malathion

---

### Post by malathion on 2008-05-12
> **ikt said:**
> and why again does a person need to launch a file manager from terminal to install a media player skin?

as opposed to winamp where you double click on a skin and it installs automatically..

somethings not right..

In a word, security. Running everything as Administrator on a windows system gets you around lots of these security "hassles." And it also makes it very easy for adware to destroy your system.

Ideally, the application would have a script that would try to install the script as root, thus prompting the user for their password. But that is not something that can be enforced by the system; the author of the software must implement it.

---

