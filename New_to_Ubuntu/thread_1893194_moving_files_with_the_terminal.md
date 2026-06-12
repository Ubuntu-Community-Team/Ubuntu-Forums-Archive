---
title: "moving files with the terminal"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by Chocolate Thunder on 2011-12-09
hello everyone, 
 
I'm new to linux, new to ubuntu and new to the forums.  I'm still a total n00b when it comes to using the command line, so much so that I apparently don't even know the right terms to google search answers to my problem, so I come to you:
 
I am learning web design at my college.  To get the .html file on the internet, I need to move the file from my computer where i made it, to a specific Unix server at my school that my class uses.  Back when I was a windows user this was easy, I just used cyberduck or WinSCP.  However, I'm slowly learning that you can do pretty much anything from the terminal, and its usually a lot faster (and more fun), provided you know how to do it.  I can log in to the school server using "[EMAIL="ssh_myusername@schoolservername"]ssh_myusername@schoolservername[/EMAIL]" and use basic Unix commands to move around my personal user directory on the school's server, but I can't for the life of me figure out any commands to move a local file on my computer and transfer it to my "www" folder on my user directory on the school server using the terminal.  I would be eternally grateful if someone would clue me in on how to do this. 
 
PS, i would also be interested in knowing how to move files from the school server onto my personal computer as well.  It's probably a different way of using the same command, but someone could tack on an answer to that as well, I would be eternally grateful X2.:confused:

---

### Post by BBQdave on 2011-12-09
Basic file movement:

mv **filename dir-name** 
this moves the file into *dir-name*

cp [B]filename dir-name

[/B]this copies the file into [I]dir-name

[/I]The *current working directory* would be your University's directory
(what you would be in to make copies to your personal directory) :)

[http://mally.stanford.edu/~sr/computing/basic-unix.html](http://mally.stanford.edu/~sr/computing/basic-unix.html)

---

### Post by jwbrase on 2011-12-09
You'll want to use sftp. It's included with the OpenSSH package.

You can also use filezilla, which is a graphical client like cyberduck or WinSCP.

---

### Post by Chocolate Thunder on 2011-12-09
Thanks, BBQdave! I'm still a bit confused (mostly regarding how to incorporate the right file paths) but at least now I have a command to search for details about.  Many thanks!

---

### Post by jwbrase on 2011-12-09
> **BBQdave said:**
> Basic file movement:

mv **filename dir-name** 
this moves the file into *dir-name*

cp [B]filename dir-name

[/B]this copies the file into [I]dir-name

[/I]The *current working directory* would be your University's directory
(what you would be in to make copies to your personal directory) :)

[http://mally.stanford.edu/~sr/computing/basic-unix.html](http://mally.stanford.edu/~sr/computing/basic-unix.html)

mv and cp are all well and good for moving files around between locations on the same machine, but the OP is looking for ways to move files between machines, for which he'll need sftp or filezilla (or any of a number of similar programs).

---

### Post by BBQdave on 2011-12-09
> **jwbrase said:**
> mv and cp are all well and good for moving files around between locations on the same machine, but the OP is looking for ways to move files between machines, for which he'll need sftp or filezilla (or any of a number of similar programs).

+1    [http://filezilla-project.org/](http://filezilla-project.org/)

---

