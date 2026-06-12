---
title: "Access right to copy files to web server"
date: 2016-07-23
forum: New to Ubuntu
---

### Post by doranlum on 2016-07-23
Hi all, I have the folder which i have change the owner of /home/doran2/Sites to student with rw rights.

I launch ssh from WINSCP using the student account and when I attempt to copy files over it still gives access permission denied. I don't understand why.


[IMG]http://i138.photobucket.com/albums/q269/doran_lum/access%20right%201_zpso6vjl9h9.jpg[/IMG]

[IMG]http://i138.photobucket.com/albums/q269/doran_lum/access%20right%202_zpsesb3ahqn.jpg[/IMG]

---

### Post by TheFu on 2016-07-23
Directories must have execute permissions for the user/group/other for anyone to CD into them.  

chmod +x ~/Sites

Find a file/directory permissions tutorial online and spend 30 minutes trying all sorts of different things inside a temporary directory with a few different userids and groups.  Try weird permissions and see what can and cannot be accomplished.  For example, it is possible to allow a group access to a directory, but not the owner.  Read access doesn't have to be provided either for certain situations that can be handy.  Ubuntu.com has a beginning level tutorial.

---

