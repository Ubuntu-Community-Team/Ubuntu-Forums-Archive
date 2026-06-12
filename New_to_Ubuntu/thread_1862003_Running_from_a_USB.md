---
title: "Running from a USB"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by davidc60 on 2011-10-16
Hi,
I have recently put Ubuntu 11.10 onto a USB stick. The 'Devices' column on the Desktop shows:
i) the 2 main partitions on my HDD, 
ii) my mobile broadband dongle connection, and 
iii) 'casper-rw' (the USB itself is not listed as such)
Although I have clicked on 'casper-rw' there doesn't seem to be any way to access the other Linux-related apps that I have copied onto the USB stick from elsewhere.
1) If it is actually possible to run the other Linux-related apps (that are presently on the USB) from the Ubuntu OS can anyone enlighten me as to how to do so? Do I really need to place them inside one of Ubuntu's folders to get *them* going? If so, which one?
2) Similarly, if and when I add more apps (from the Software Centre) where should I put them on the USB?
3) It has previously been my intention to keep running Ubuntu from the USB for six months then simply starting over again (with a new USB if necessary) when the next version appears next April. If, however, I do eventually decide to install it on the HDD (eg using Wubi), then apart from possible speed issues and also apart from the usefulness of being able to dual-boot with Windows, is there really any other advantage in actually installing it or should the full OS and the apps run just as well from the USB for a few months? Will I be missing out on anything if I keep things as they are by just using the USB?
Thanks,
DavidC
(new to Ubuntu - firmly in the 'haven't-really-got-a-clue' category of users!)

---

### Post by 73ckn797 on 2011-10-16
Did you download the 11.10 ISO? 
Did you install the 11.10 to the USB using Startup Disk Creator to make it bootable?
There is an option to designate space on the USB for storing files. If the USB has enough memory maybe you can install programs once booted from the USB.

---

### Post by davidc60 on 2011-10-16
Thanks for your reply. I downloaded a torrent program, then the 11.10 ISO, then used 'USB Installer' to put it onto the USB - I vaguely recall an option to allocate 'Persistent' file space but I skipped it as I wasn't sure at the time what it was really about. It sounds like it could be the same as what you have mentioned. I'll go back to the Installer and review the options again. Thanks.

---

### Post by Lisiano on 2011-10-16
If you have a fairly large USB, say 8GB, instead of a LiveUSB you should install it to the USB as a normal install. The problem with LiveUSB is that if you ever try to update your USB, it will download all the updates and instead of updating, reinstall the updates into the persistence space while keeping the old files intact.
To install to a USB, you should either burn a LiveCD/LiveUSB and tell it to install to another USB OR use a Virtual Machine (VMware or VirtualBox) and install to the USB from there.

EDIT: If you wish, I could walk you through the process using pictures.

---

### Post by davidc60 on 2011-10-18
Hi,
Thanks for your note. I do have a spare (brand new) 8gb USB (Fat32) and I have tried 'installing' from the LiveUSB to that 8gb USB as you have suggested but without success so far. When given the choice of 'alongside Windows', 'replace Windows' or 'something else', I have been choosing 'something else'. 
Then, the next screen is the 'Installation Type' screen and this is where I have been getting stuck. Although I have been able to choose my 8gb USB from the list of potential drives, when I click on the Install button I keep getting the message: 'No Root File System is Defined. Correct this from the Partitioning menu'.
I am not really sure what this actually means but nevertheless I have clicked on the drive to bring up an 'Edit the Partition' screen. Here I have left the partition size as the full 8004mb, and have selected FAT32 from the next drop down list. Then, the final option refers to the 'mount point' and I do not understand that at all. I have tried two combinations so far eg. leaving it blank or '/dos'. Either way, whatever I try, when I go back to the Install button I continue to get the message: 'No Root File System is Defined. Correct this from the Partitioning menu'. 
So I cannot take things any further until I can determine what that really means and what I should do about it. I did not try the '/windows' option on the mount point list as I would prefer to keep things as far away from Windows as possible until I know more about what's going on (I don't want to mess everything up!). Should I really have selected '/windows' in order to be able to continue with the install? If I do so, will the effect be the same as the specific option to install Ubuntu 'alongside Windows' with the only real difference being that I will be using an USB as my drive rather than an empty partition on my HDD?
(Incidentally, I noticed that there is also something mentioned on the file system drop-down list about a Swap area. Is this something that I should be considering even when installing to a USB? Presumably this allows files and applications to be easily made available between both Windows and Ubuntu?)
Any further advice you can offer to help me around the obstacle regarding the Root File System would be appreciated. Thanks, DavidC

---

### Post by florus on 2011-10-18
The swap area is where your computer stores data when you suspend or hibernater. Size normally equal to system ram - clearly not wanted on a USB stick.

---

### Post by florus on 2011-10-18
Your mount point will be '/' (without the inverted commas) . This defines your boot partition. Keep asking if you are uncertain.

---

### Post by jonnyboysmithy on 2011-10-18
The /windows mount option means that it automatically mounts the partition, and gives it the label "windows" and if you choose /dos the the label is dos.


You could try making a liveusb again but this time with a big persistance file so that it has a place to store the apps you install  and other things etc... > The problem with LiveUSB is that if you ever try to update your USB, it  will download all the updates and instead of updating, reinstall the  updates into the persistence space while keeping the old files intact. It will keep the old files. It will take up more space. Thats okay if you have plenty space. 
Edit: I think this is the easiest method.

---

