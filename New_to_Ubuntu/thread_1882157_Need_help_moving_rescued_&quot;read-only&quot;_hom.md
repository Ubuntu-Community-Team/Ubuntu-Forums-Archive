---
title: "Need help moving rescued &quot;read-only&quot; home folder to new venue."
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Mesquiter on 2011-11-16
Several weeks ago my Ubuntu Meerkat 10.10 OS crashed during an update and I was unable to boot it again. I spent two weeks learning how to rescue my encrypted files until I ran across a program included in Ubuntu 11.04 and 11.10  "ecryptfs-recover-private." (private being an encrypted home folder)

I downloaded 11.10 and burned a live USB stick with persistent memory to save changes.  Inserting your system pass-word into the "ecryptfs-recover-private" program decrypts your "eCrypted" home folder and places a copy of it in your live USB system files in a temporary folder labeled /tmp/ecryptfs.XXXXX in a read only format.

I can read all my files and see the pics of my grandkids, but I can't move the folder or copy the files using the graphic interface. I've tried everything I know, but each time it denies me because of not having permission. I tried copying to the live USB and even an extra blank USB to no avail.

What do I have to do to be able to reclaim my files and move them where I need them? I'd like to copy the entire folder to another venue. I've only been using Ubuntu for about six months and know very little about using a terminal, but I'm trying to learn. Please help a cyber-challenged old man become a hero to his great-grand son. Your time and help will be greatly appreciated. Thanks.

---

### Post by David006 on 2011-11-16
Simple steps:

You have a computer, running Ubuntu Linux ..


What version?  Ubuntu 11.04 or Ubuntu 11.10


Where do you think your files now are?  On the USB, or in a folder that is R/O, etc.

-- Can you only see thme from the GUI app. that you used?


Where do you want the files to be?

---

### Post by hansdown on 2011-11-16
Hi, Mesquiter.

Running the live media,open a terminal, and copy and paste this...,also have a usb plugged in...


```
gksudo nautilus
```

You should be able to, drag and drop the files to the usb.

---

### Post by Mesquiter on 2011-11-16
I'm using Ubuntu 11.10 on a USB stick with persistent memory.  I had to "gksu nautilus" to open the temporary (tmp) folder and have tried several times to drag and drop to my other USB stick or to the Desktop of 11.10 and each time I get the same message.  I don't have permission to move or copy the folder.

---

### Post by hansdown on 2011-11-16
> **Mesquiter said:**
> I'm using Ubuntu 11.10 on a USB stick with persistent memory.  I had to "gksu nautilus" to open the temporary (tmp) folder and have tried several times to drag and drop to my other USB stick or to the Desktop of 11.10 and each time I get the same message.  I don't have permission to move or copy the folder.

Mesquiter,

Navigate to the right folder.

If,  it is pictures, go there.

Tmp folder, is.... not there, when you, come back.

---

### Post by Mesquiter on 2011-11-16
If I shut down Ubuntu using my USB stick, when I start it up again the /tmp/ecryptfs.xxxx file is no longer in the system files.  I have to open a terminal each time to run the "ecryptfs-recover-private" program again and it will bring up my old home folder from my hard drive, place it in the sys. files under the name /tmp/ecryptfs.xxxx.  I can then open the tmp. folder with "gksu nautilus" and view all the files and pics.  I just can't do anything with them.  I can't copy and paste, move the folder, nor any of the individual files.

If you're asking if I move away from the /tmp file and come back to it is it still there?  Yes, it's stays until I shut down the USB stick.  If I close the terminal it won't open again until I start another terminal and "gksu nautilus."

---

### Post by hansdown on 2011-11-17
> **Mesquiter said:**
> If I shut down Ubuntu using my USB stick, when I start it up again the /tmp/ecryptfs.xxxx file is no longer in the system files.  I have to open a terminal each time to run the "ecryptfs-recover-private" program again and it will bring up my old home folder from my hard drive, place it in the sys. files under the name /tmp/ecryptfs.xxxx.  I can then open the tmp. folder with "gksu nautilus" and view all the files and pics.  I just can't do anything with them.  I can't copy and paste, move the folder, nor any of the individual files.

If you're asking if I move away from the /tmp file and come back to it is it still there?  Yes, it's stays until I shut down the USB stick.  If I close the terminal it won't open again until I start another terminal and "gksu nautilus."

O.K.

Are you able to see the files, that you need, to save?

Edit:

Can you plug another usb in, to copy the files?

---

### Post by Mesquiter on 2011-11-17
Yes, I can see the files.  I can open each one and read the contents.  I can look at my pictures.  I have tried to move them and the folder to two different USB memory sticks but get the same message every time.  I don't have permission.

---

### Post by hansdown on 2011-11-17
> **Mesquiter said:**
> Yes, I can see the files.  I can open each one and read the contents.  I can look at my pictures.  I have tried to move them and the folder to two different USB memory sticks but get the same message every time.  I don't have permission.

I pride myself, on being helpful, but I may have erred.

If you rightclick on a file, Then, check permissions, can you change the permissions?

---

### Post by Mesquiter on 2011-11-17
Don't be too hard on yourself, friend.  At least you and David006 answered my plea and I think you're on the right track.  The more I read about the eCrypts program the more I think it's not your garden variety problem.  From my surfing the Net I think it has something to do with ownership or permissions, but when I right-click on a file the permission section is not active.

---

### Post by hansdown on 2011-11-17
I'm starting to wake up, now.

These are encrypted files, yes?

---

### Post by mc4man on 2011-11-17
The recovered dir is still owned by the orig. username. So from the method you used you'll need to 1st. copy the files from 1 root browser to another root browser, then you'll be able to copy out to removal media, ect.

Ex.
In one terminal
```
sudo mkdir /tmp/backup; gksudo nautilus /tmp/backup
```

Then open another root browser (gksudo nautilus) either from a 2nd terminal or Alt+F2, browse in it to /tmp/the_recovered_directory

Copy whatever you wish to /tmp/backup, then you will be able to copy from /tmp/backup as 'ubuntu user' to your external media


A much easier way using same recovery method

Boot to live cd, create a new user using the exact same username as was used on the install you wish to recover from. Make this new user's account type 'Administrator' 
(password doesn't matter, 123456 is fine

Log out & into the new user, do the recovery, you'll then own the /tmp/recovered_directory & can copy at will.

Edit:
Note if using a 11.04 live session to recover

If there there no log out shown in the indicator  then try opening a terminal & running

```
gconftool-2 -s -t bool  /apps/indicator-session/suppress_logout_menuitem false
```

---

### Post by Mesquiter on 2011-11-17
mc4man

I tried your first suggestion and created a folder named "backup" but could transfer neither the folder nor the files to it.  I'm not using a live CD.  I'm using a live Ubuntu 10.10 USB stick with persistent memory: a "casper" file.  I don't think you can record yourself as Administrator on a live CD because once you burn the disk you can't add more to it.  (Unless you're talking about a rewritable CD and I don't have one of those.)   The USB live version should work as I added the same name as administrator but it didn't seem to do any good.  I still get the "you don't have permission" message.

Eight hours later:

I thought about your first suggestion and check my tmp files when I returned this morning and the "backup" file I created was gone as well as the /tmp/ecryptfs.XXXX file.  I got to thinking I might be able to create a super-doer file using "gksu nautilus" on my extra USB stick.  I ran the ecryptfs-recover-private program again, got another /tmp/ecryptfs.XXXXX file and opened it under under the first terminal.  I created a second terminal and using "gksu nautilus" created a folder on my extra USB stick called "Meercat" and voila' . . . it worked!   I now have complete control of all my lost files.  Six months of work on a western novel I couldn't imagine writing again from my failing memory and all my great-grand son's rodeo pics.  You helped make this old man a hero to his great-grand son.  Now I can reinstall Ubuntu on my hard drive but this time I won't make the mistake of encrypting my files.  Thanks to all who responded and especially you, mc4man for your suggestions.

Mesquiter

---

