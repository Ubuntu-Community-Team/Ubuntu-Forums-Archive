---
title: "RAID 1+0 on 4 Seagate GoFlex 2TB drives?"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by AlpharettaTom on 2012-03-04
I am so new to Linux I still have to pause and think when I go to spell it. I know Windows but want to move away from it.

My setup: HP small form factor dc7700 w/ dual core 1.8
          4 gig of RAM
          main drive for OS is 160GB SATA drive
          4 (USB 3) Seagate GoFlex 2TB hard drives
          plugged into a SiiG 4-port USB 3 card

The Goal: 1) setup a fileserver for dishing out mp3 files, movies, and recorded television (SAMBA?)to various computers in the house and to my iPhone. 2) I also would like to set up my own personal "cloud" to access from anywhere. 3) I would also like to back up the 8-10 computers to this.

I know the next Ubuntu Server LTS version is coming out next month (April 2012) but for now I am trying to setup Lucid Server (aka version 10.4 LTS). I have Lucid installed with desktop. I have been trying to RAID the 4 drives but I cannot for the life of me figure out how to get mdadm installed. I open a terminal window and do a:
sudo apt-get install mdadm
but it comes to a page "postfix configuration" that asks me to choose a type of setup but there is NO WAY that I can see to make a choice. There is no place for me to type anything. It looks like a picture of a page of options with no active selecting method. I have been fighting getting these 4 drives RAIDed 1+0 and LVM for a week now and I finally have to ask for help. I think I have read almost everything on the internet but I am missing something for sure.

I am wide open for suggestions. I have even thought about just using rsync between 2 sets of 2 drives which would give me a backup of all of my data but not the best way to do this, I don't think. Please let me know if I have left out any required detail that would allow you to better answer my question. 

Given my current hardware, is there a better way to accomplish my goal?

Thanks in advance for your help!

---

### Post by Lisiano on 2012-03-04
0) I'm guessing you never dealt with a ncurses menu. Basically you navigate that menu using Tab, arrow keys and space/enter. Just scroll down this page using the arrow keys and read up on what option does what, then tab so OK is highlighted and press space/enter. Rinse and repeat.

1) For your fileserver, you might want to try doing it via the GUI since it is easier. Here is a guide on how to set up Samba if you want to do it via CLI [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)
For GUI, right click the folder you wish to share -> Properties -> Share.

2) For the "cloud", I think installing a SSH server and port forwarding it will be good enough. You can use SSH for virtually anything, including file transfers, administration, proxy, you name it.

3) I think DejaDup can help with that.

4) For the RAID, you can also set it up quite easily using the GUI tools, just look under System -> Administration -> Disk Utility, then File -> Create Raid Array.

---

