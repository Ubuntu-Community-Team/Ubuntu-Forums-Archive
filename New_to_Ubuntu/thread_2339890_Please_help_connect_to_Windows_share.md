---
title: "Please help connect to Windows share"
date: 2016-10-13
forum: New to Ubuntu
---

### Post by frank2222 on 2016-10-13
Hello all, im very frustrated. Im following this tutorial here. [http://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](http://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/)
 Im pretty sure my music folder is shared but i cant get the syntax of this command correct

sudo mount.cifs //WindowsPC/Share /home/geek/Desktop/Windows-Share -o user=geek

the username on my windows pc is gremlin32 and ubuntu is frank.
I want to connect to the default Music folder

Im trying sudo mount.cifs //192.168.1.129/Music /home/frank/Desktop/Windows-Share -o user=frank

Can someone please tell me whats wrong or a diffrent way to move the contents of my music folder to my ubuntu machine.

Thanx in advance

---

### Post by frank2222 on 2016-10-13
I got it to work by createing a writable samba share on ubuntu, but would still appreciate the proper syntax for that command

---

### Post by Geoffrey_Arndt on 2016-10-13
Why not just copy the files to an external USB flash-stick or hdd/ssd.    Then restart the system,  or use "sneaker-net" to walk over to the linux machine, (plug the device back in, click on it in the nautilus file manager, and copy it to your linux music directory?    Or another way, just get a cloud service (Dropbox works great in Ubuntu) . . then copy the files to your Dropbox music directory, and it will be available to both OS's if you have Dropbox (and same user ID) there also.    If the OS's are on the same machine, _but just different partitions, it's even easier_ . . .

---

### Post by frank2222 on 2016-10-18
Thank you for the reply. I needed to move close to 200 gigs of data, not just the music, making a usb impractical, and i only get 10 gigs a month of bandwith so the clouds not really feasable. It is 2 diffrent machines but the samba server was simple to set up and I can move files back and forth with ease now.
Thanx again.

Edit: Added:

just reread your reply and I will check out dropbox,

---

### Post by mastablasta on 2016-10-19
samba is the default for sharing with Windows. however if you canaccept a bit clunkier interface then sFTP (part of openssh) is good option as well. samba Works well for smaller files, but sFTP seems ot work faster and better on larger files. at least in my case. so if i had to move 200 GB i would go with sFTP protocol.

dropbox is not an option if you have limited data package. plus it's only free for a  much smaller space than you need.

---

