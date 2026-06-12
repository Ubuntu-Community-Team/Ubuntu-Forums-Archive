---
title: "package manager failure"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by bamh1d on 2013-07-15
I have a problem running package manager in the Unity desktop on top of Ubuntu 12.04.
From Terminal I typed Sudo apt-get install -f
and got the following response

Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: Problem opening /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

What does this mean? Is this a problem of permissions? What should I do about it?
Thanks in advance for any help you can provide.

---

### Post by ibjsb4 on 2013-07-15
This should fix it

[http://ubuntuforums.org/showthread.php?t=2135737&p=12606126&viewfull=1#post12606126](http://ubuntuforums.org/showthread.php?t=2135737&p=12606126&viewfull=1#post12606126)

---

### Post by bamh1d on 2013-07-15
You're right, that seems to have done the job, although I don't understand what I did or why it solved the problem

---

### Post by ibjsb4 on 2013-07-15
Your /var/lib/apt/lists had been corrupted.  You removed it (the 'rm' command) and rebuilt it (the 'update' command).

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

edit:

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&sa=Search&cof=FORID:9)

---

