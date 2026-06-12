---
title: "edit remote files with eclipse"
date: 2007-09-15
forum: Programming Talk
---

### Post by nephish on 2007-09-15
hey there all, 
i was wondering how would be the easiest way to modify remote files with eclipse. All the software i work on is on my server at work. 
I would use the subversion method, because that is what i use for version control. but I don't want to commit a new revision every time i change from <div id=  to <div class=

Eclipse has projects, that when i import all the project files into my workspace, i have a copy of those files. Then, after i edit them, i have to export them. Thats kind of a pain in the neck. Going through all the file browsing, etc... 

I use vim for most of my quick edits, but would like to use some of the eclipse coolness. 

i have a lot of remote abilities, ssh, sshfs, etc.. 

would rather not use ftp.

any tips would be greatly appreciated.

thanks

---

### Post by dwhitney67 on 2007-09-16
SSH to your remote server.  Specify the -X option.  When you launch Eclipse on the remote server, it will appear on your local desktop.  Be prepared to experience bit-lag.

---

### Post by nephish on 2007-09-16
i found another way. 
in a rails project, i can use the file browser in the projects section, navigate to the folder where my project is, right click, and select 'open folder as project' 
the folder is an sshfs mounted folder where my code resides. Only bit-lag is saving the files. Not to shabby.

thanks, though, i want to use your idea on another app.

---

### Post by firebush on 2008-06-23
> **nephish said:**
> i found another way. 
in a rails project, i can use the file browser in the projects section, navigate to the folder where my project is, right click, and select 'open folder as project' 
the folder is an sshfs mounted folder where my code resides. Only bit-lag is saving the files. Not to shabby.

thanks, though, i want to use your idea on another app.

Thanks, this worked for me.

1. apt-get install sshfs
2. add the fuse group to your user (system > administration > users and groups, unlock, select groups, scroll to fuse, select properties, make sure you're checked as a member of the fuse group).
3. Restart your computer
4. Create a directory you want to use to access the remote server through.
5. Run:  sshfs <user>@<server>:<remote folder to mount> <local folder created in step 4>

You should now be able to access that folder via eclipse.

---

### Post by crossfire on 2009-10-05
you may want to check out this:

[http://www.eclipse.org/dsdp/tm/]("http://www.eclipse.org/dsdp/tm/")

---

### Post by mabelode on 2011-07-08
I have to dig this thread up since I am trying to get a fast setup going. I want to work on my desktop machine at home, but have everything work related on my laptop. Both are connected via lan.

I have tried the 'ssh -X', vnc, sshfs approach but all of them are not satisfying. I experience massive lags with the ssh based solutions and the vnc solution also lags (although not as much as ssh) but auto-completion is not working, which is unacceptable for me.

So is there a really fast solution for this? Ignore security and everything, I am only going to use this on lan.

---

