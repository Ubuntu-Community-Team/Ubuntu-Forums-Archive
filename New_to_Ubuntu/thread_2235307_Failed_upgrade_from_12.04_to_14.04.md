---
title: "Failed upgrade from 12.04 to 14.04"
date: 2014-07-20
forum: New to Ubuntu
---

### Post by quailwoods on 2014-07-20
I tried to upgrade from 12.04 to 14.04, and it seemed like everything went well, but now it opens in the sign in for 12, but hangs after the password is entered: some terminal screens with data flash by, then it's back to the sign in page. Can't seem to get into terminal either. Suggestions?

---

### Post by alias2234 on 2014-07-20
Well, I dont trust the upgradeprocedure. I do a new full install instead and that worked for me. My ubuntu system works very good now.

---

### Post by whitesmith on 2014-07-20
Reinstalls are never as clean as fresh installs. Back up your home directory and reinstall. If you want the new (14.04) installation to have the same applications as the old (12.04), do this before reinstalling:```
sudo dpkg --get-selections > ~/installed.lst
```After restoring the home directory in 14.04 do this:```
sudo dpkg --set-selections < ~/installed.lst
sudo apt-get -y update
sudo apt-get dselect-upgrade
``` and all applications will magically return.

---

### Post by quailwoods on 2014-07-20
Thanks to Whitesmith and Alias. . .but I can't get it to OPEN. If it won't open and I can't get into terminal is there a boot sequence I can use?

---

### Post by whitesmith on 2014-07-20
First try logging in as guest. You say you "can't get into terminal." Does this mean a "GUI terminal" (Ctrl+Alt+t)? If so, try opening a tty-terminal (Ctrl+Alt+F2). If you can login there you can at least run the code to save your important data. 

It sounds to me like you have an issue with the video firmware. Let me know if you can do the tty login. If you can there's hope of saving the installation.

---

### Post by quailwoods on 2014-07-20
Couldn't control alt anything to work: it just keeps reverting back to the "guest" screen. After many tries, a took a picture of the flash screen there are about two pages of text, one line looks like "funkconfigwarning etc/fonts/conf.d09-fonts-nanum.conf" line 9 having multiple values in <test> iso

some end with "having multiple <family> in alias", and it looks like they all start with " /etc/fonts/conf.d/89 or 90"

I've been extracting files using ROX in Puppy, but I wonder if there's something I could delete or replace using Puppy.

---

### Post by whitesmith on 2014-07-20
Try this. Boot off the 14.04 iso image disk (or usb). Tell it you want to **try**, not install, Ubuntu. Are you able to get a GUI now? If not, then your hardware is not compatible with 14.04. This should always be the first step in a Linux install on untested equipment. I assumed, incorrectly I suppose, that you already did this.

---

### Post by quailwoods on 2014-07-22
I hadn't, but now I have. It's INCREDIBLY SLOW!! After waiting 15 minutes for it to load, and another 5 to load the test version, I WAS able to get into the dead 12.04-14.04 mess and download the home files to a thumb drive. I presume the thing to do is to reformat the HDD and start over. Any suggestions on how to lay it out? And I guess the big question is, once I DO install it to the HDD, will it run any faster?

---

### Post by quailwoods on 2014-07-22
PS. Just curious: as I looked at the files for the12.04 mess, then at the files for the 14.04 SD, I wondered what would happen if you just deleted the bin, usr, etc, home files and all the others and stuck in the ones from the SD, could one get away with it?

---

