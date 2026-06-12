---
title: "Install failing on 'Where are you?'"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by MartinJH on 2014-04-22
I've decided to convert a 5 year old Dell XPS 430 (see PC spec at bottom) from Windows Vista to Ubuntu 64 bit (ubuntu-14.04-desktop-amd64.iso) but the install is failing. I burned the iso file on DVD and I'm using an ASUS wireless USB (USB-N53 adaptor) for connecting the PC to my internet router.

Once the Ubuntu install process gets under way, it finds my wifi connection and after the password is entered, it gets to the "Preparing to Install Ubuntu" page. I ticked on 'Download updates while installing' and 'Install This 3rd-Party Software', where next I'm taken to the Installation Type page. I select "Erase disk and install Ubuntu" and after a few seconds the "Where are you?" page is displayed with the world map. It's at this point that a small pop-up window appears. The title is "??? ???" and the contents is a Stop sign (dark circle with white horizontal bar) with "??? ???". I click on the OK button and I'm thrown back to the previous Installation Type page. If I select "Erase disk and Install Ubuntu" again, I get the same pop-up error on the "Where are you?" page. Sometimes it takes multiple clicks on the OK button to close it and other times it's just gets stuck at that point. 

I've tried to install with the USB wifi adaptor removed (so I dont click on Download updates) but I get the same pop-up error on the "Where are you?" page. Incidentally, if I get totally stuck with the pop-up window refusing to close and I select the top-right hand option to shut down Ubuntu, the DVD drive opens up and the following information is displayed. The PC doesn't actually shut down.

wait-for-state stop/waiting
 * Stopping rsync daemon rsync
* speech-dispatcher disabled; edit /etc/default/speech-dispatcher
* Asking all remaining processes to terminate ...

Any help appreciated.
Martin


PC Details:
Dell XPS 430 (approx 5 years old)
Core 2 Quad Processor (2.83GHz, 1333Mhz FSB, 12MB Cache)
8 GB RAM. 1066MHz DDR3 Dual Channel

---

### Post by Impavidus on 2014-04-22
Have you checked the dvd for errors?
If your computer boots from usb that may be a better option.

---

### Post by MartinJH on 2014-04-22
I'm using a Verbatim DVD+R disk. When I burned the disk from Windows, I was able to view the files in Windows Explorer. Not sure how to check for actual errors. I might use my Mac to burn another CD and then check for errors (I'll google it).

---

### Post by Impavidus on 2014-04-22
When you boot from the dvd and have selected the lanuage you should get a menu, including an option to check the disk for errors.

---

### Post by MartinJH on 2014-04-22
Just burned another DVD, this time from my Mac, along with verifying the disk. But still get the "??? ???" pop up window on "Where are you?". I need to see what else could be the cause. Not a very helpful error, to say the least.

---

### Post by MartinJH on 2014-04-22
On the first page, I see a list of languages and "Try Ubuntu" "Install Ubuntu" buttons. I'll play around and see if I can get past the error.

---

### Post by MartinJH on 2014-04-22
Still no luck. There isn't an option to check for disk errors. Interestingly, when I run the Try Ubuntu option, there is an Install option within it, and although I get the same "??? ???" error on the "Where are you?" page, I'm also occasionally able to get to the next page which is the keyboard language page. But again, I get the "??? ???" pop up window. I'm starting to think this installation isn't compatible with my pc.

---

### Post by migs73 on 2014-04-22
Have you cheked the .iso file you downloaded in the first place? If you check the disc for errors it'll only check it against the file you burn on it. If that file is corrupted then so will the disc be corrupted.
Try checking the downloaded .iso file using the method mentioned here:

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

If this shows an error you'll need to download the file again.

If it is OK then we'll need to get more ideas.

Good Luck

Mike

---

### Post by SuperFreak on 2014-04-22
I know this is obvious, but you are choosing a location when it asks you "where are you?", right?

---

### Post by MartinJH on 2014-04-22
The checksum works out ok, using Mac's md5 command. It matches ubuntu-14.04-desktop-amd64.iso.

Superfreak: It doesn't give me the option to pick the location. When the wifi USB isn't plugged in, the map location defaults to the New York timezone, while with the wifi USB plugged in, it rightly defaults to London. However, the "??? ???" pop-up appears at that point and selecting OK either crashes back to the previous page, or it just gets stuck.

I'm going to try Ubuntu 13.10.

---

### Post by SuperFreak on 2014-04-22
You mentioned wifi. You need to have a hard wired connection to install
 ie via ethernet

---

### Post by MartinJH on 2014-04-22
No luck with 13.10. I get the same error on "Where are you?". The actual error is the same as this:

[http://ubuntuforums.org/showthread.php?t=1767203](http://ubuntuforums.org/showthread.php?t=1767203)

---

### Post by MartinJH on 2014-04-22
I'll try to install with a wired internet connection tomorrow. 

I was reading through this thread ([http://ubuntuforums.org/showthread.php?t=1712753](http://ubuntuforums.org/showthread.php?t=1712753)) and I'm wondering if Ubuntu is having issues finding a hard disk. I think my PC is using RAID 0 disks and perhaps Ubuntu can't see them.

---

### Post by MartinJH on 2014-04-22
Hmm. When I select "Try Ubuntu" and select "About this computer", worryingly it states that Disk is just 4.2GB. There should be 1.2 TB. All other details, such as Memory, Processor, Graphics, OS Type look right. So if Ubuntu was copying files during the install, that could explain the weird errors. Now I just need to work out how to get Ubuntu to recognise the RAID disks.

---

### Post by pfeiffep on 2014-04-22
> **SuperFreak said:**
> You mentioned wifi. You need to have a hard wired connection to install
 ie via ethernet

My experience refutes that statement as I have successfully installed using wifi - of course that means the install disk provided the option for me to log in to my wifi.

---

### Post by SuperFreak on 2014-04-22
> **pfeiffep said:**
> My experience refutes that statement as I have successfully installed using wifi - of course that means the install disk provided the option for me to log in to my wifi.

My mistake

---

### Post by MartinJH on 2014-04-24
Finally got Ubuntu 14 installed. The issue was with the already allocated RAID 0 Windows disks. It took me a while but I managed to use gparted and a bit of hackery (which I forgot to document) to remove the RAID 0 settings on the disks and format them to ext4. Once that was done then I was able to fully install Ubuntu without issue.

---

### Post by MartinJH on 2014-04-24
I'm not sure how I set this query to SOLVED.

---

### Post by Impavidus on 2014-04-24
Click "tread tools" (above the first post of the page), then click "mark as solved".

---

