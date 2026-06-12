---
title: "Ubuntu for NAS file server."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-07-03
Hey guys, I am thinking of using ubuntu for a file server in a home made nas, but I am a novice in the area. Would you recommend any good links to info? Also I am right now using one vista desktop pc as my main file repository, it's on 24/7 and I can access via lappie any file I want seeing the disk drive in my places-network area. What is the difference between this setup and the nas one. What would a server do differently than what I have now, and why would I prefer one from the other. I kinda confused reading all these fancy terms like samba/ftp etc. Do they offer anything more to the home user than my current fuss free setup?

---

### Post by computermacgyver on 2008-07-03
First a few terms:
Samba: This is the linux implementation of the windows file-sharing system. E.g. This will let you browse windows network-shares from a linux machine or make network shares available on a linux machine to a windows pc. Some information is available here:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

FTP (File Transfer Protocol): FTP is a Internet standard used for transferring files from one computer to another. An FTP Client (e.g. gftp, fireftp, etc.) sends and receives files which are stored on an FTP Server. If you would like to have access to certain files from outside of your home network (e.g. at the office), you may consider establishing an FTP Server. 

SSH: Another option for connecting from outside the home network would be an SSH server, which is a bit slower, but uses encryption to protect data.
Some information is available here:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
In addition, from the Windows side,
PuTTY and WinSCP are great client programs to connect to your network.
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)



For the average home user, there is probably little difference between your current setup and using Samba. There may be some tradeoffs in usability, speed, security, etc. but for me it will hinge on user comfort and understanding.

If you plan to connect from outside of your network, then I have personally found the tools and features of Linux to be superior. I would highly recommended looking into SSH for this purpose.

Scott

---

### Post by bluepowder7 on 2008-07-03
do a search for ubuntu server guide.  it'll step you through setting up your home file / print / whatever server quite nicely.

i have a small desktop for all my duties, and a big server box with a few hard drives and an old laser printer connected to it, stuffed somewhere far away in the house.  the server made sense when my laptop was funcional.

benefits?  your desktop pc can be small, quiet, low-power, etc.  your server can use LVM to take a random assortment of hard drives and pool it all together into one larger drive.  more storage = more drives = more heat = more fans = more noise = as far away from you as possible.

ssh makes connecting to the server easy to do the various configs on it.

i haven't played with samba yet, since i haven't needed to boot into windows since february, so right now nfs is working just fine for me.

---

### Post by Iowan on 2008-07-03
Check [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") - there are several Ubuntu server How-To's.

---

### Post by Jackfrost123 on 2008-07-03
Scott, wow, super great help. Thank you buddy.

I still don't understand that well what the potential gains might be, why would you need special software, protocols to just have the other computer see the folders and the contents and not just ubuntu? (I suppose the protocols work on top of a ubuntu installation right?)

When you say "from outside of my network" you mean for example from a remote location right?

---

### Post by Jackfrost123 on 2008-07-03
Hey Iowan thanks!

Hey bluep! Fantastic help, thinks start to clear up in my head. What you describe is the reason I would want such a set up too, and why my current setup. So in essense I am setting up a server capable of among other sings serving my files, but above all it's a server which could have other uses to, right? Ok, I get it samba = communication with windows emulating its protocol. How about interoperability with macs?

---

### Post by lazyart on 2008-07-03
If you're looking to create an "appliance" (one role only, quick configuration) take a look at [www.freenas.org](www.freenas.org) .  It's BSD based (Unix derivative) and would be quick to get going with.

---

### Post by Jackfrost123 on 2008-07-03
hey lazy, yeahp I found freenas. I wouldn't mind playing around with something a bit more advanced to tell you the truth to get the hang of it should I need something more in the future.

---

### Post by bluepowder7 on 2008-07-03
as far as i know, yeah you could have multiple users, but then you'd have to set up the file permissions (users / groups) - some files might be for one user only, others could be available to all users (so i guess the users would need to be part of the same group).  i'm a single user at home, so i haven't needed to explore that avenue.  and i've not used a mac since grade 10.  though i think that the current mac OS is a close relative on linux, so it might not need samba.

what i do like about my home file server is that i've got physical space for 11 storage hard drives (plus 1 for the OS), which means i can end up with a HUGE amount of space - and it all shows up as one block, not 11 smaller random blocks.

freenas probably works great as a file server.  don't think it has print server capability, though.

---

