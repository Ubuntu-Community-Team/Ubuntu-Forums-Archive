---
title: "Problem with cgi-bin"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by mvsspradeep on 2012-05-10
[SIZE=3][B]Hi All,

I am new with Ubuntu. I am having some problem. What I need is there is a folder named cgi-bin is with me containing some perl script (upload.cgi). when I place that folder to access from my localhost (when used with apache 2) its throwing an error like you don't have permissions to access this directory. I couldn't access that folder. Please help me out if you have any solutions to this. 

I appreciate for the useful and quick answer. 

Thank you. [/B][/SIZE]

---

### Post by imran042 on 2012-05-14
you havent executed that script.

first of all remove the script by the command, 

sudo rm /fullpath

then write the same type of file in the terminal window and save by any extensions like .pl or .cgi(anyone would work)
after that 
execute the file by, chmod a+x filename.pl or .cgi 

then copy it in cgi-bin by using,
 
sudo cp filename.pl /usr/lib/cgi-bin/filename.pl.

now from ur browser type 
localhost/cgi-bin/filename.pl
or
127.0.0.1/cgi-bin/filename.pl

hope this works..

---

