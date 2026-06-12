---
title: "Software Center has stall during an install of Crossover"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by Peterfc on 2012-08-19
HI

I download a trial version of Crossover and started to install it using Ubuntu Software Center. As the install was about to finish it stopped and would not complete. I switched of and restated the Software Center but it is still trying to carry on installing. Each time i close the Software Center it goes back to the point it was previously stalled at.

Is there a way to cancel an install and try again.

I am using 12.04 Advent Laptop, 250gb hard drive, 3gb ram. Celeron 743@1.30 GHz

Thanks for reading my post

---

### Post by 25tom on 2012-08-19
There should be an option in the left-hand panel of the software centre window called "progress" with a rotating circular double arrow. Click on this and you should see a list with the install process in it. Click the stop button next to the install process.
Hope this helps :)

    Edit:
I see you're using Precise, so the interface may have changed from my version of software centre...

---

### Post by Gone fishing on 2012-08-19
I'd restart then install from the commandline - open a terminal and run the command

sudo dpkg -i somethingcrossover.deb

changing somethingcrossover.deb to your deb file

See if it installs if it doesn't post back the error message or where it stalls.

---

### Post by Peterfc on 2012-08-19
Hi Guys

Thanks for your speedy help.

The progress says 1 and when i click on it nothing happens but i will try again and also right click.

I will try the command line approach when i get home i am out and have to use a windoooooows machine where i am to access the Forum.

Thanks

Peter

---

### Post by Peterfc on 2012-08-19
Hi Guys

I tried to right click the Progress but nothing happens, i also clicked the red button with the X on and the searching is cancelling but that also just keeps going but never finishes cancelling.

I also tried Sudo dpkg and it seems that that won't work either.

Thanks for your help.

Peter

peter@peter:~$ sudo dpkg -i crossover_11.2.0-1_i386.deb
dpkg: error: dpkg status database is locked by another process
peter@peter:~$

---

### Post by Gone fishing on 2012-08-19
This why I suggested restarting otherwise the software centre will prevent dpkg from running. Otherwise you will need to manually kill the stalled process.

---

### Post by 25tom on 2012-08-19
I presume you've tried rebooting your computer? That should kill the process. I had a similar problem with another program recently, and rebooting fixed it.
Good luck making things work :)

---

### Post by Peterfc on 2012-08-19
Hi Guys

I have tried by rebooting my machine a number of times but each time i start the Software Center the progress starts up again saying progress with a number 1 at the side of it. I have again tried sudo dpkg only to get the same answer as before.

I now don't want to download Crossover i just want to kill the download process in the Software center. I have tried to install an uninstall using Gdebi package installer but i get the message i have highlighted below.

[B]Only one software management tool is allowed to run at a time
Please close the other application e.g. 'Update Manager','aptitude' or 'Synaptic' first.[/B]

Again thanks for the time you have spent trying to help me.

Peter

peter@peter:~$ sudo dpkg -i crossover_11.2.0-1_i386.deb
dpkg: error: dpkg status database is locked by another process
peter@peter:~$

---

### Post by Gone fishing on 2012-08-20
To manually kill a process 

sudo gnome-system-monitor

Will open system monitor which can kill processes the process you want to kill I think will be dpkg.

---

### Post by Peterfc on 2012-08-20
HI Gone Fishing 

Thanks i can now mark this is solved. I was lost without your help but the best i can do is say thanks. 

So this Scouser from Liverpool now in Portugal says a big thanks.

Peter

---

