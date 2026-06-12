---
title: "How to make a copy"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by manners2345 on 2008-08-13
How do I make a copy of my currently installed Ubuntu, to an external HDD. That way when I shaft the installation, which I have done to many times to count!!! I do not have to start from scratch installing Desktop, then all of the updates and all the extras I have added. It generally takes me 3 days to get back to where I was before I blew it!! And generally I have forgotten some stuff!!

If I copy it, how do I reinstall to internal HDD and use it???

A whole to of thanks

manners2345

---

### Post by cosine352 on 2008-08-13
open the source list for apt

> sudo gedit /etc/apt/sources.list

Then add the lines below at the bottom
> # Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

Then install remastersys

> sudo apt-get install remastersys

Now you can do a backup of your system using this application

you can find the application (after installation) in 

> system --> administration --> remastersys backup

This will give you a nice graphics interface
OR you can just paste this command in the terminal

> sudo remastersys backup

to clean the backup
> sudo remastersys clean

you can find the backup in /home/remastersys

---

### Post by DGortze380 on 2008-08-13
> **cosine352 said:**
> open the source list for apt



Then add the lines below at the bottom


Then install remastersys



Now you can do a backup of your system using this application

you can find the application (after installation) in 


OR you can just paste this command in the terminal



to clean the backup


you can find the backup in /home/remastersys

or just use the rsync, or dd command.

---

### Post by sydbat on 2008-08-13
I keep hearing about this remastersys. Is it really that good? After adding the link in Synaptic, it says "Not Authenticated" (or something similar) and then wants to install 10 - 15 dependencies. Is this normal?

---

### Post by robert shearer on 2008-08-13
Yes it's that good. Yes thats normal.

Look here for more info  [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by sydbat on 2008-08-14
Cool. I'll give it a go.

---

### Post by manners2345 on 2008-08-14
Thank you for the informaqtion on how to do the type of backup I asked about.

manners2345

---

### Post by manners2345 on 2008-08-14
And thank you also for the very detailed info

manners2345

---

