---
title: "Bash script is not executed on startup"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by Hellboy256 on 2014-10-24
I have a test script /home/tom/Scripts/test.sh
```

#! /bin/bash
touch abc.txt

```

that I added to Startup Applications but not file is created on login. Note my /home is encrypted I don't know if that is the problem!?

---

### Post by TheFu on 2014-10-24
chmod +x /home/tom/Scripts/test.sh

---

### Post by Hellboy256 on 2014-10-24
No that didn't help, I also tried
chmod 777 /home/tom/Scripts/test.sh

---

### Post by TheFu on 2014-10-24
Don't use 777 .... er ... EVER. I cannot think of any good reason to set permissions open like that - well, unless you are running a hacking contest and want to be hacked.

Web search found this: [http://askubuntu.com/questions/156765/adding-a-file-to-the-list-of-startup-applications](http://askubuntu.com/questions/156765/adding-a-file-to-the-list-of-startup-applications)
Did that work?

---

### Post by Hellboy256 on 2014-10-24
Yes the command 
xdg-open /home/dan/Scripts/test.sh 
did work but not bash!?

Can u explain me why the chmod 777 can be hacked so easily??

---

### Post by 3246251196 on 2014-10-24
user, group, other - each one is octal: read,write,execute. if i - the user - want full permissions (read, write, execute) then I want to set the bits for each: 111, this in binary is 7 (decimal). If I want the group to only be able to read and execute then I want to set 101, this is 5. And, if I want all other persons to only be able to read then I want 100 - 4.

chmod 754 myfile.sh

will enable this. Now, only I can write, read and exe. The group can read and exe and all other can only read the script. By setting all bits for user, group and other then anyone at all can change your script.

-rwxr-xr--  1 me me       0 Oct 24 20:34 myFile.sh

===

I believe something in your .bash_profile file in ~ should run commands on login. Unless everytime you start a new bash session you want to run the script then place it in .bashrc. If none of these exist just create them.

---

### Post by TheFu on 2014-10-24
> **3246251196 said:**
> 
will enable this. Now, only I can write, read and exe. The group can read and exe and all other can only read the script. By setting all bits for user, group and other then anyone at all can change your script.

Further, they could let the script continue to do what it does, but add other things to it. If your account has sudo rights, then they own the machine.  If not today, eventually.  As long as the script does what you believe it should, you are unlikely to look at it again.

If there are any services running on the system (perhaps a wordpress site with a bad theme?), then access to anyone on the internet smart enough to hack in and find completely open files can happen.

So ... it is time to learn more about file and directory permissions, that is clear. There are many resources, but usually when folks need that knowledge, they are ready to learn much more - a web search for "linux command line" will find a free, no-hassle, PDF book (also published as a real book you can buy anywhere) that provides a little background, history, explains why as well as how.  Highly recommended.  Skim it, see what it has inside, Hopefully, you'll get interested in the first 100 pgs or so to read the background and have the rest as a reference for specific questions.  It is nicely organized, unlike single web search results.  

BTW, the explanation of permissions above is the bare minimum. There are many subtle things possible that are not intuitively obvious.  For example, how to allow any except 1 person to read a file, but still allow them to execute it?  Or how directory permissions are what really controls access to files, regardless of the file permissions.  Subtle things like that.  Beginning level understanding is easy.  Expert level takes a little more effort.

---

