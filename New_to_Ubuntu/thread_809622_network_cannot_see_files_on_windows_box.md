---
title: "network cannot see files on windows box"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-05-27
Running Hardy on desktop.  Laptop still has Vista.  From Ubuntu on desktop if I click on the "Network" icon I can see the windows machine but I cannot see any of the many shared files it has (that I could see before I converted the desktop to dual boot).

What should the network settings be?

I have already mapped the Ubuntu sharing folder as a drive to my windows machine and I can read and write to it from the windows machine without problems.  Just need to be able to see the shared files on the windows machine from within Ubuntu.

Thanks

---

### Post by sayakb on 2008-05-27
Do you have samba installed?
```
sudo apt-get install samba
```
This would display and access all machines within the Windows Network.

---

### Post by raymondvillain on 2008-05-27
Yes!  Samba installed yesterday.  Before Samba, there was no network (but I could connect to the internet).

I set up the smb.conf file by using the "How To" posted on these forums:


[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Otherwise I wouldn't be this far along.

---

### Post by KingTermite on 2008-05-27
I'm certainly no expert, but I'm pretty sure LinuxIsInnovation is correct. I've always heard you must have Samba installed to see files with a windows computer over the network.

---

### Post by sayakb on 2008-05-27
> **raymondvillain said:**
> Yes!  Samba installed yesterday.  Before Samba, there was no network (but I could connect to the internet).

I set up the smb.conf file by using the "How To" posted on these forums:


[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Otherwise I wouldn't be this far along.

Do you have Firestarter or an equivalent firewall running?

---

### Post by raymondvillain on 2008-05-27
I don't think so.  How would I find out?  I installed "firesort" for sorting Mozilla bookmarks.

Are the firewall settings on the "System" tab on the top panel?

Thanks

---

### Post by sayakb on 2008-05-27
No, I mean any gnome firewall configuration? Seems like something is blocking your inbound/outbound traffic.

---

