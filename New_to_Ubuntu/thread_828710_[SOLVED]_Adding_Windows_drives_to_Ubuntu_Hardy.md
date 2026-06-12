---
title: "[SOLVED] Adding Windows drives to Ubuntu Hardy"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by freddyandrews on 2008-06-14
I recently started dual booting XP with Hardy. Am pretty happy with Hardy and found solutions to most problems I faced. ( The credit goes to ubuntu forums. You guys rock )

Now am planning to bring in my remaining drives from XP to Hardy without losing the data. How do I do that? 

I used to have 4 XP partitions c,d,e,f( XP in C drive)
I used the 4th Partition F (20G) for Ubuntu. 
I can access all partitions from Hardy without any glitches, but just want the former XP drives D and E migrated to Ubuntu. Will eliminate XP at some other point of time.

May be there is a different post discussing the same and I overlooked. Please point me to that post or suggest solutions. 

Any suggestion is welcome. Thanks in advance.

---

### Post by powerpleb on 2008-06-14
I'm not sure what you mean by emigrated to Ubuntu. Do you want to copy all the data into the Ubuntu partition and remove the others or do you just want them permanently accessible with Ubuntu?

If so..
Open a terminal and type this:```
sudo fdisk -l
```
This gives you a list of all your drives. You can then use the information to mount them. E.g if D: is /dev/sda2 in Ubuntu you can mount it by typing:
```
sudo mkdir /media/D
sudo mount /dev/sda2 /media/D
```
If you navigate to the /media/D folder on your Filesystem you should have access to the drive.
You can of course change D to whatever you want.

To have them permanently mount everytime you turn on the computer you need to put them in your /etc/fstab file.
This thread will help you do that: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by sam_delta on 2008-06-14
click on the top-right panel on places>computer, check if the drives shows there, they should be there, you just double click em and your done :p


sam

---

### Post by housam on 2008-06-14
You can create a /home partition out of the free spaces of the two partitions and then copy your data to that partition .
Here is how to make a [[COLOR="Red"]_separate /home partition _[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by freddyandrews on 2008-08-02
Excuse me for the late reply. I didn't bother to retain windows. Just gave a clean Ubuntu install on my pc. Issue solved.

Thanks guys.

---

