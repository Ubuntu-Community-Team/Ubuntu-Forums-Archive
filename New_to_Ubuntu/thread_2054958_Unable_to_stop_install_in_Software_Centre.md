---
title: "Unable to stop install in Software Centre"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Peterfc on 2012-09-08
Hi

I recently posted when i found that trying to install Crossover the install never stopped. The install had a little before it finished and just carried on at that point. Each time i switch on the software centre i see that a package is still installing and it causes my machine to run very slow. 

Each time i try to install the updates i get a message that says

" Unable to get exclusive lock "

This usually means that another package management application (like apt-get or aptitude) is already running Please close that application first.

One reply from GONE FISHING advised that i put into the terminal " sudo gnome-system-monitor " doing this worked as was able to stop the process but i have since found that when i want to use the software centre the process starts installing again. 

Todays i had had enough i can't do any updates or get rid of the install in the software centre so i decided to install the 12.10 beta. using ALT and F2 then update-manager -d seemed a good idea until i get the same message. 

In the software centre it shows that Crossover is installed and if i click it i can then install software that runs with Crossover.

Thanks for reading my post.

---

### Post by Epodx64 on 2012-09-08
try this from a terminal
sudo apt-get clean
sudo apt-get check

---

### Post by Peterfc on 2012-09-08
Hi

Thanks for a quick reply.

Sorry to say it didn't work i have posted the terminal reply.

Peter

---

### Post by Epodx64 on 2012-09-08
Is there a job process that's running the Software center? from a terminal type
ps -A
and see if you can identify the process that's running apt might even be ubuntu-software-center my package manager comes up as muon & qaptworker but i'm using Kubuntu (KDE) so it will be different then yours if you can figure out whats causing it kill it with
sudo kill -9 pid

pid is whatever the pid number is next to it in ps -A

---

### Post by tienlbhoc on 2012-09-08
go to system monitor to find and kill

---

