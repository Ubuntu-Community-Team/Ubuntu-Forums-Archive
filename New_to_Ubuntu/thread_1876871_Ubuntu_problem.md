---
title: "Ubuntu problem"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by ank123 on 2011-11-07
Hi, I was exploring linux (ubuntu) as usual..... I deleted  dpkg/status file by mistake.... I knew that I had done a major  mistake.... So i tried to recover it by using the following commands....
 sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
 sudo dpkg --clear-avail 
 sudo apt-get update
 sudo apt-get upgrade
 But after execution of 4th command, i got another error as 
 E: Encountered a section with no Package: header
 E: Problem with MergeList /var/lib/dpkg/status
 E: The package lists or status file could not be parsed or opened.
 So i tried another set of instructions which is as given...
 # sudo dpkg --configure -a
 # sudo aptitude update
 # sudo aptitude upgrade
 But still though it didn't work. 
 Without that status file, I can't install or modify any softwares, so  urgent help is highly appreciated :) Can I try to write my own status  file?? If yes, how? Let me know about it...... :D

---

### Post by wildmanne39 on 2011-11-07
Hi, please use normal fonts and try this it may work.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thank you

---

### Post by Rubi1200 on 2011-11-07
Hi and welcome to the forums ank123 :)

Unless you need to specifically highlight something, please use the default formatting.

And, let us know if the great advice offered by wildmanne39 helps resolve the problem.

---

### Post by ank123 on 2011-11-08
No it didn't solve the problem..... I'm getting the error as 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by wildmanne39 on 2011-11-08
Hi, that usually fixes the issue, you can try this run the commands on line at a time.
```
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
```
If that does not work you can have a look at this link it will allow you to recreate the source list that you had when you first installed ubuntu.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Thank you

---

### Post by ank123 on 2011-11-09
Yeah, it worked.... thanks :D :popcorn:

---

### Post by wildmanne39 on 2011-11-09
Hi, your welcome! I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by Rubi1200 on 2011-11-11
> **ank123 said:**
> Yeah, it worked.... thanks :D :popcorn:
Good news :)

Nice work by wildmanne39.

As requested, please mark this thread Solved.

Thanks.

---

### Post by ank123 on 2011-11-11
when i click on thread tools i get 'printable version'. There is no option such as 'mark this thread as solved' :confused:

---

### Post by ank123 on 2011-11-11
> **ank123 said:**
> when i click on thread tools i get 'printable version'. There is no option such as 'mark this thread as solved' :confused:
I marked this thread as solved  :)

---

### Post by wildmanne39 on 2011-11-11
Hi, yep I see you figured it out. Good Job!!!

---

