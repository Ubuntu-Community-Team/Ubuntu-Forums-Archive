---
title: "Problem re automatic updating"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by lesliek on 2013-03-20
I just had some updating problem. Here's what I was told:

leslie@ubuntu:~$ sudo apt-get check
[sudo] password for leslie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 perl : Depends: perl-modules (>= 5.14.2-6ubuntu2.3) but 5.14.2-6ubuntu2.2 is installed
E: Unmet dependencies. Try using -f.
leslie@ubuntu:

I'm simply afraid to run apt-get -f install, because I might stop my system from running.

I Googled for "perl-modules" "5.14.2-6ubuntu2.3", but didn't get any hits that seemed to me to be helpful.

Can I just find and install the newer perl-modules? If so, how?

Edit: How I show my ignorance!

I found I could do sudo apt-get install perl-modules=5.14.2-6ubuntu2.3, which seems to have solved my problem, so I came back here to delete my post, but can't figure out how to do that!

Apologies for troubling people.

---

### Post by ibjsb4 on 2013-03-20
Just mark it solved :D

---

