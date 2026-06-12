---
title: "attempting win file recovery with lubuntu live usb"
date: 2017-06-11
forum: New to Ubuntu
---

### Post by rabbitrabbit on 2017-06-11
I have a Lenovo U460 win 7 laptop that has acquired a virus that is completely bogging down the cpu and physical memory (but not in safe mode). I've been wanting to getaway from Windows and this is the last straw. There are some files I'd like to recover before making the switch, but I'm too wary to just copy them onto a usb. Thankfully most are already backed up, but there are some I'm not sure about. I read a suggestion that I could boot linux from a live usb and upload my files to something like dropbox. I chose lubuntu v17.04 since I only had a small usb handy and have zero linux experience. Got it onto the usb no problem with Win32diskimager thanks to ubuntu instructions. Actually ended up using 16GB usb.  Booted up the laptop and got an error that goes by too quickly to catch, but lubuntu starts fine. I'm able to get onto my network and see my files on the c drive. When I try to get online, however, it wants me to create a user for firefox, but says I don't have permission to save the info. When I try to choose the save location there is no response or selection screen. Lubuntu refused to shutdown and instead of seeing the time in the lower right corner I'm seeing a timer counting up and some kind of progress bar on the upper right corner that has no label. At one point the screen went black and only came back up randomly, seemingly not in response to anything I did. Rebooted and retried with all the same results.   Now I don't actually care about getting online at this point, I just want to save my files somehow. I put the maybe-not-backed-up ones on the usb with the lubuntu live install, in their own folder. Of course, since I don't have another machine that has a linux install I can't go check to see if my files are really there.  My question for you guys is, should the files really be there? Once I install lubuntu on the laptop (I was going to keep the win7 recovery partition but at this point I'm thinking dban and start from scratch) what is the best way to get it to recognize my old win backup drive and various win formatted usb sticks?   Thanks in advance!

---

### Post by Autodave on 2017-06-11
Are you wanting to keep the Windows recovery area of the HD for possible future use? Or, just forget Win and use Lubuntu?

From the live installer that you save the files to: did you look to see if they are actually in the created folder?

As for Firefox, I have never created a user name: I just hit ENTER to get past it (or whatever, like NOT NOW, REMIND ME LATER, etc).

---

### Post by rabbitrabbit on 2017-06-11
Wouldn't mind keeping the win7 partition.  For the live usb - I created a folder outside the lubuntu folder and copied the files there. So the usb contains my copied files folder, boot folder, system volume info folder and the bootmgr file.  I tried skipping the user bit, but never got a browser window. I just tried it again right now and it worked perfectly. Even though I'm happily uploading the desired files right now I'd still love to know what you thing about the files I put on the usb.

---

### Post by Autodave on 2017-06-11
I personally would be OK with it. But, why don't you look at them on another computer and be sure?

---

### Post by rabbitrabbit on 2017-06-11
Files are available in dropbpx, but I can't check the usb on another computer right now. I have no access to a linux machine until I flip mine. I do still see the files on the usb even after shutting down, removing the usb and restarting via the usb again, so it looks like things have worked as they are supposed to.

---

### Post by Autodave on 2017-06-11
Then look at them in Dropbox or have someone else check them. If it were me, and I checked them on the USB stick and found them intact, I would feel safe to continue.

---

### Post by grigspace on 2017-06-12
You can use second USB Flash drive to copy necessary files on it.
You can use external HDD to do the same.
You can compress desired files to archive and send them to E-mail as attachment using web mail service.
You can compress desired files to archive and send them to google drive using web browser ([http://drive.google.com](http://drive.google.com))

So You have many options :)

---

### Post by rabbitrabbit on 2017-06-12
I meant I did check in dropbox and I do see the files. I also see them on the USB, but only via the only while running lubuntu off  the same USB. Either way, I'm good now. And I've learned that you can put files onto a Live install USB. Thanks!

---

