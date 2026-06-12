---
title: "Installed Ubuntu but can no longer access it with dual boot."
date: 2012-08-06
forum: New to Ubuntu
---

### Post by mrtn474 on 2012-08-06
Hello!

I'm totally new at this, just fyi. 

I did a dual install with Windows and Ubuntu 12.04 on my HP Mini-110. Like any other HP laptop, it already had four partitions on my hard drive, so I had to delete the HP Tools partition and shrink the main C drive to leave 29 GB of space for Ubuntu (I had picked 30GB but it turned out to be 29 somehow). 

I successfully installed Ubuntu in that free space. I used it for a bit. I hated that Unity interface, so I tried to get Gnome (which I think is the window manager that 10.10 used). I had to restart the computer to let some updates complete. But when I tried to use Ubuntu, I could not access it. 

Using Windows' Disk Management, I noticed that the free space where Ubuntu was in had no letter label. It only says "free space." So I deleted everything that was in that partition. 

Could this be it? That it has no letter label? There's also some 103MB of unallocated space that couldn't figure out how to merge with the other free space. It's very little memory so I just left it alone. 

Thank you for your time! :D

PS: I took a screen shot of my Disk Management window so you could see what I see.

---

### Post by z3nhakr on 2012-08-06
ubuntu installs on an ext4 partition which is not supported by windows. how did you install gnome?

---

### Post by mrtn474 on 2012-08-07
I installed gnome by just looking it up with the software that came with ubuntu. I forgot what it's called, but I looked it up and downloaded it. It installs on it's own, doesn't it? I tried logging out so that I could switch window manager, since that's how it worked with 10.10. But it didn't let me. That's when I shut down and couldn't boot Ubuntu again. 

But Gnome is irrelevant, isn't it? Did that have to do anything with it?

Then how am I supposed to install Linux from the state that my hard drive is already in? 

Thank you for replying.

---

### Post by oldfred on 2012-08-07
Windows cannot read the ext4 or any Linux formats. So the Windows partition tools do not work for Linux. Only use the Windows partition tool to shrink Windows and use Linux tools to create or modify all other partitions.

If you used Windows to clear the space it did not see, you deleleted the Ubuntu install.

I think you wanted gnome-panel which is almost like the older gnome2.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by mrtn474 on 2012-08-14
Well, the installation worked perfectly this time around. I've had no problems in the past two hours since I installed it. 

> **oldfred said:**
> Windows cannot read the ext4 or any Linux formats. So the Windows partition tools do not work for Linux. Only use the Windows partition tool to shrink Windows and use Linux tools to create or modify all other partitions.

If you used Windows to clear the space it did not see, you deleleted the Ubuntu install.

I think you wanted gnome-panel which is almost like the older gnome2.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

I used GParted to format the unallocated space that I had, as an ext4 partition by using a live USB. It was the same USB that I used afterwards to insall Ubuntu. Then, Ubuntu seemed to do it's own thing. It asked me to partition that same logical partition into two parts. I let it do it, and continued the installation. As I said, it was successful, but I'm doubting that what I did with Gparted had anything to do with it. 

Also, will this version of gnome let me use ccsm? (Edit: I found a "The Gnome Desktop Environment with Extra Components" on the Ubuntu Software Center. Is that the same?) Sorry for being a little out of topic.

---

### Post by oldfred on 2012-08-14
I do not normally use the Software Center. If you click on Gnome Desktop and the more info it will show most of the apps are the installed ones or that is the standard.

If you want gnome-panel it is under gnome shell and fallback session. The 4 or 5 apps under that, I show all as installed.

---

### Post by mrtn474 on 2012-08-14
Thank you so much for the replies. I downloaded "The Gnome Desktop Environment with Extra Components" through the software center and i got what i wanted.

---

