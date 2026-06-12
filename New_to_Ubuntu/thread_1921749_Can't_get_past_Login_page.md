---
title: "Can't get past Login page"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by gyozu on 2012-02-07
Computer is Dual boot with Win7 and 10.04 LTS. Installed a / partion and a /home partition. 

 I had added the mediabuntu items and 2 days ago had been trying to install BitPim and Kindle for PC with Wine. Both of those failed to work properly so I removed them and the next day my working install of Virtualbox disappeared. 

Tried to login this morning and it just looped back to login page.
thought that maybe it had lost the pass work and used one of the instruction sheets to reset that.

It was not that . It seems to take the password, flashes through about 4 command lines and drop me back to the login page.


So, I'm stuck.

---

### Post by donkyhotay on 2012-02-07
at the login screen press ctrl-alt-F2 which will get you out of the GUI and into a CLI, try logging in from here and see what happens. It sounds to me like something happened to your desktop environment itself so I suspect it'll just log you in to CLI without problems but this will help elminate/confirm a possible problem the user account itself. BTW, what desktop environment are you using? gnome? KDE?

---

### Post by gyozu on 2012-02-07
Same thing happened. Just returns me to start of login process.


Using Gnome.

---

### Post by gyozu on 2012-02-08
Needed to move on, so here is what I did. It was less than elegant, but it worked.

Reading back through a variety of threads, I was led to a DiskInternals program that would allow me to copy my personal files to Windows without hasseling about permissions. Very straight forward.  Had to move about 110 Gb (video, photos, documents, PDF's) which became about 150GB in windows. Then back-checked files (as many as I could stand ) to see that they were there and I could read them on the Windows 7 side.  Then went and tried files with both Ubuntu 10.04 LTS and Mint 12 Live CDs. Could read and play files from Windows side with them.

Next, did a fresh install of 10.04 and checked the box that brought over docs from Windows side. Reformatted the partitions /,/home and /swap . Took about 2 hours to do install and shuttling of files. Install ended up generating a Documents file that had all the files I transfered to Windows in it. Everything up and running now. Just have to do some final moving around, tweaking and setting up backups.

Not fun, but doable for a rank beginner.

---

