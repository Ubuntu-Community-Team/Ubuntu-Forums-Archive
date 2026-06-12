---
title: "Files with a ~ in the name."
date: 2014-01-05
forum: New to Ubuntu
---

### Post by flyfisherbryan on 2014-01-05
I am doing a lot of reading and doing excecises in terminal in an effort to learn more about my system (Ubuntu 13.10).  When I first opened terminal I noticed there were 2 copies of a file in my home directory, one of which had ~ after the name.  In the GUI there was only the one copy without that symbol.  I have deleted that file, but the file with ~ can still be seen in terminal.  (Opening my documents directory reveals double copies of many text files.)  When I open tools in my home folder in the GUI I see an offer to restore missing files, and when I open it that file is listed.  So I must assume that that ~ file was made to facilitate recovery.  So I want to know:

How was it made? 
Why was it made?
Do I have to go into Terminal to make these "shadow copies" go away? 
Or can I somehow find them and delete in the GUI?
Is this something I can turn off? 

Answers to these questions will help me establish security protocols for documents on my system.  Thanks.

---

### Post by hoopia on 2014-01-05
It was probably made by Gedit, which automatically backs up files with a tilde by default. You can turn that off by going to Gedit Edit->Preferences->Editor tab, and then uncheck Autosave.

---

### Post by deadflowr on 2014-01-05
The ~ symbol at the end of the file means it's a backup.
Text editors, like gedit, automatically create a backup of any file when you save.
You'll notice this anytime you save.
The file is hidden, normally, so you would need to view hidden files/folders to see it.
ctrl +h normally allows you to see the hidden files in the file manager(Files).
They are normally A-Okay to delete.

It's done this way to give the user a save in case the user accidentally made a save of the file which would cause the user undue harm. the user can simply replace the broken file with the backup. 
The one problem is that the file is overwritten everytime a new save happens.

---

### Post by flyfisherbryan on 2014-01-05
That was easy, but I could not find that answer in the manual.  Thanks!

---

