---
title: "Unable to delete Ubuntu install ISO, any advice?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Olegious on 2008-04-28
I downloaded the new Ubuntu release ISO via a torrent. The ISO was downloaded to a folder on the C drive- I have a dual boot set up going (C drive is Vista, D is Ubuntu), everything installed and runs normally. However it wont let me delete the ISO I used to install the OS- "the file is open in another program." Any idea where it could be open? I have unmounted all virtual drives, restarted the computer. I'm out of ideas....Thanks!

---

### Post by dearingj on 2008-04-28
Is it Windows that won't let you delete the file, or Ubuntu, or both?

---

### Post by Olegious on 2008-04-28
The file is saved onto Windows, so I'm assuming that Windows is the culprit- is there any way to trace where the program is running?

---

### Post by andy128 on 2008-04-28
Have you tried removing it in safe mode?

Andy

---

### Post by blazercist on 2008-04-28
OMG its a conspiracy by M$ to mess with you for downloading Ubuntu! Lol.

just boot into ubuntu and delete it with sudo from the command line.

edit: i just saw that ur really new so I'll break it down for you.

If you can currently access your windows files from ubuntu then you can do this:

sudo apt-get install nautilus-open-terminal (this will let you open terminals from teh gui in a particular directory and saves me from having to determine what the path to ur windows directory is and also from cding and blah blah blah)

now restart

now open the folder where the file is and right-click in the folder and click open terminal here

now type:

sudo rm Ubuntu.iso (or whatever the filename is)

your done.

---

### Post by Glaxed on 2008-04-28
Did you shut off your torrent client? Are you defragmenting?

---

### Post by Olegious on 2008-04-28
thanks, I'll try all of the above and let you know which works...

---

### Post by Olegious on 2008-05-01
Safe mode didnt let me delete, so I booted into Ubuntu, went into C from there and deleted it, everything seems to work fine.  thanks!

---

