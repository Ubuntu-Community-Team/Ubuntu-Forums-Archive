---
title: "Why are text documents opening a Terminal window?"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2012-02-13
Whenever I click on a text document in Ubuntu, they open a blank terminal window.  I want them to open with GEdit or something similar.
How do I change that on a system-wide level?

---

### Post by uRock on 2012-02-13
Right-click, then select Properties then select Open with tab, then select Gedit, then click the Set Default button.

---

### Post by drs305 on 2012-02-13
In a file browswer, right click the same type of file, select Properties, Open With, and select Text Editor or another option. 

There may be a tick box to allow you to use it for all files of this type, depending on the file browser. If you don't see an app listed, you can select a command, such as /usr/bin/gedit.

---

### Post by oklokl on 2012-02-13
ubuntu-tweak

Admins > File Administrator > txt > gedit

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212647&stc=1&d=1329189134[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212648&stc=1&d=1329189134[/IMG]


sudo apt-get install dconf-editor
Alt+F2 

dconf-editor
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212649&stc=1&d=1329189776[/IMG]

---

### Post by uRock on 2012-02-13
> **oklokl said:**
> ubuntu-tweak

Admins > File Administrator > txt > gedit
ntuforums.org/attachment.php?

I wouldn't recommend installing ubuntu-tweak for making such a slight change.

---

### Post by Learning Linux 2011 on 2012-02-14
> **uRock said:**
> Right-click, then select Properties then select Open with tab, then select Gedit, then click the Set Default button.

Thanks, that was pretty simple :-)

---

