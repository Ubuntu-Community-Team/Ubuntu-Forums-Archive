---
title: "How to Format Hard Drive"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by tinylittle on 2008-09-22
I need to temporarily uninstall Ubuntu and reinstall Windows Vista on my Acer 3680. The hard drive had failed, was replaced and while awaiting the Acer system and recovery disks, tried Ubuntu. 

I can't just use the Acer disks to do this as I get the famous error code 0xd0000017. 

So, I need to format the hard drive, I assume, back to how it came new, and then use the Acer disks. Then I can use the Ubuntu live cd to reinstall Ubuntu.

Any help would be appreciated.

---

### Post by bumanie on 2008-09-22
From the live cd > sudo apt-get install gparted  

This will install the partition editor. Go to System --> Administration --> Partition editor. Highlight the drive and click format and choose the filesystem you want. You can pre-partition one ntfs partition and one ext3 partition at this stage if you wish. It is better to install windows first, followed by ubuntu. It is also a good idea when installing ubuntu to choose manual at the partitioning stage and make a 6-8gb / a 1-2gb swap and a separate /home as large as you want. This way if something goes wrong with ubuntu, you only have to reinstall to / and all your saved data in /home is safe.

---

### Post by tinylittle on 2008-09-22
Not sure if I did this command in the right area (the live cd does not automatically come to a terminal command window), but, I tried but got the message

Could not find kernel image: sudo

---

### Post by bumanie on 2008-09-22
Terminal is located at Applications --> Accessories --> Terminal. Click on terminal, when it is open type the code > sudo apt-get install gpartedHit enter.You will then be asked for your password. Type that in (be aware there s no visual ouput)and hit enter again. Gprted should download and then you should be able to locate it as mentioned in the original reply.

---

### Post by wolffangalchemist on 2008-09-22
he needs to reformat the hard drive so "sudo apt-get install gparted" won't work right ppl?
you just put in the live cd and use gparted(on the live cd under system>>administration>>partition editor(or possibly it says gparted idr)) to wipe all partitions from the hard drive and bingo your disk should work.

---

### Post by tinylittle on 2008-09-22
Alright, sorry I am confused. I thought you wanted me to boot to the Live Cd and do those commands. 

I have now gone started Ubuntu and gone to the terminal window and been able to install partition editor.

I do not see anywhere that allows me to format a drive. I have 3 items to hightlight: /dev/sda1, /dev/sda2 and /dev/sda5. I can highlight any of these and nothing allows me to format.

Sorry, but what am I doing wrong.

I do appreciate your assistance.

---

### Post by tinylittle on 2008-09-22
I now see Wolf's reply, but I am still a little lost. When I boot to the live cd I get the options:

Try Ubuntu....
Install Ubuntu
Check CD
Test Memory
Boot from first hard disk

How to I get to where you directed?

---

### Post by bumanie on 2008-09-22
> **tinylittle said:**
> Alright, sorry I am confused. I thought you wanted me to boot to the Live Cd and do those commands. 

I have now gone started Ubuntu and gone to the terminal window and been able to install partition editor.

I do not see anywhere that allows me to format a drive. I have 3 items to hightlight: /dev/sda1, /dev/sda2 and /dev/sda5. I can highlight any of these and nothing allows me to format.

Sorry, but what am I doing wrong.

I do appreciate your assistance.

What I said should work (I actually cut and pasted that answer from  a thread I answered earlier and the peron said it worked fine), but as you seem to be quite new, it may be easier for you to go to the gparted site and downnload the gparted live cd .iso and use that instead. It is a dedicated tool and in my opinion is lightly superior to the one on the ubuntu cd. Clicking on a partition should allow you to choose what filesystem to format to. I just tried the gparted site and it seems to be down - so try right clicking on the partitions, I think you will be offered the option of formatting. (Going on memory, haven't done it for a while).

---

### Post by tinylittle on 2008-09-22
Thanks for your help. It does not work.

Uninstalling Ubuntu should not be this difficult, even for a noobie. Perhaps this is one of the problems with Ubuntu and possibly other Linux programs. Just too NOT user friendly.

I will try to find the answer in other searches. I do appreciate your time however.

---

### Post by bumanie on 2008-09-22
Try the gparted site, it may be back up again.

---

### Post by oldos2er on 2008-09-22
> **tinylittle said:**
> Thanks for your help. It does not work.

Uninstalling Ubuntu should not be this difficult, even for a noobie. Perhaps this is one of the problems with Ubuntu and possibly other Linux programs. Just too NOT user friendly.

I will try to find the answer in other searches. I do appreciate your time however.

 Ubuntu is an operating system, not a program, so naturally its install/uninstall procedures are going to be more complex than installing or removing programs.
If you have access to another computer, you might want to look into using the Gparted live cd (see [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)), or you can use the Ubuntu Live cd (run the 'Try Ubuntu' menu choice). Once you're at the desktop, look under System, Administration, Partition Editor.

---

