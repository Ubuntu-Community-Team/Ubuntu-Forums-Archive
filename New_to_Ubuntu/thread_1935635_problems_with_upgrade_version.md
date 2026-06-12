---
title: "problems with upgrade version"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by david.mann8 on 2012-03-04
hi been using 10.04 for some time. 32bit i believe.

Just bought a new epson printer and suggestions online were to upgrade to 11.10 as it wouldnt load the drivers

So i went ahead a did this. Some 4hrs later i came home with some issue that needed resolving some preference (which i cant remember at all) and so on trying to make a choice my mouse and keyboard would do nothing. I even plugged in the original wired keyboard and mouse thinking the driver for wireless had gone wrong, still nothing. me being me i forced a shut down (held power button!) clearly the wrong choice. on start up it went to the ubuntu screen with the moving red dots and stays there.  I can get into the set up screens etc but dont have any idea what to do. Any help would be greatly appreciated. I can by pressing escape get some scrolling info that stops and mentions things that are ok etc. Obviously im using another pc to do this in case your wondering. many thanks

---

### Post by NikTh on 2012-03-04
My suggestion is simple . But wait for another maybe better than mine. 
Backup your system ( your important files) and try a fresh install of 11.10 . This is not the usually way for ubuntu , but after two continuously upgrades i think everything messed up.

---

### Post by david.mann8 on 2012-03-05
thats what i thought, but how do i back up when i cant get past the ubuntu logo and on to my desktop?

---

### Post by NikTh on 2012-03-05
> **david.mann8 said:**
> thats what i thought, but how do i back up when i cant get past the ubuntu logo and on to my desktop?

With a liveCD/Usb . Boot from there , connect to your drive and move all your important files to another disk . With rsync for example
```
 rsync -av /path/to/source/directory /path/to/target/directory
``` if you want more options for rsycn then have a look to manual  . ```
man rsync
```

---

### Post by david.mann8 on 2012-03-05
thanks for your help. just waiting for a cd to reload it from, downloaded before. hopefully what youve posted will make sense when i get on with it. i'll reply in a day or so.

---

### Post by david.mann8 on 2012-03-07
Hi My disc for 11.10 has arrived. Just went to see if it would help and now before the ubuntu logo comes up it say BOOTMGR IS MISSING (restart)

I have a acer revo which has its own OS but it only offers windows as an option for a OS so dont think i can load my disc that way...any ideas wouldbe gratefully received.

---

### Post by david.mann8 on 2012-03-07
Got it to load cd, asking if new install or alongside exisiting...how do i get my files from a old os to new?

---

### Post by Mark Phelps on 2012-03-07
That error message implies that you are running Win7 on the PC.  Can you confirm this?

If that is true and you still want to be able to use Win7, you will have to restore the Win7 boot loader files -- presuming that the Win7 OS files and data are still there.

Also, if you do want to either continue to use Win7 or to save the Win7 files, do NOT use the install alongside option.

---

### Post by david.mann8 on 2012-03-07
Hi, past that now...think most of upgrade is done via a cd but stuck on "restoring previously installed packages... about 15mm from end of red progress bar and no movement for at least 30mins!! mouse pointer is still rotating and the disc starts and stops spinning every minute or so.....is this normal?

---

### Post by david.mann8 on 2012-03-07
just gone back to it and it said there was an error but will continue and i have to manually restore some items... hope thats it

---

### Post by david.mann8 on 2012-03-07
got a computer again!!! Trying to figure out email now...had 10.04 previously, now mozilla thunderbird, my contacts are there but have to re configure my accounts.....hoping my email will be there when i remeber my account details

---

