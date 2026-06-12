---
title: "Total Frustration! I can´t set folder sharing!"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by smcaro on 2008-10-30
Hi,

Thanks in advance for your help. I have now spent two weeks with this and cannot get it done...

My setup:

SMC Router /modem
Mac mini with External 500 giga HDD
Macbook
PC Pentium 4 3.0 Ghz with 10 giga HDD ( with Xp Pro), and 2 internal 200 giga HDDs, one External HDD 1 Terabyte. ( all FAT 32).

With XP running on the one Windows box, all I do is right click and set share for folders. Then both my mac automatically see those folders and everything works.

The problem is that I regularly transfer 200+ giga folders between the mac mini´s external driva and the XPs external drive. One of them being Windows, sometimes it works, sometimes it crashes, so having had Linux installed in some older Pentium II about 5 years ago with no problems, I decided to give Ubuntu a try, thinking that it would be more stable.

The XP box is hardly ever used for anything else than for storage.

Problem: There is NO NO way I can get Ubuntu file share to work. This has being going on for 2 whole weeks!!!!!

I have done fresh install a few times and the ONLY thing that works by itself is the internet connection. It automatically connects and I can surf the web and do the updates ( at least 4 times). 

I then started reading and studying and editing smb.conf, and usershares and the lot, nothing. I once managed to connect as the user in Ubuntu from my laptop, but did not have permissions to go ay further than share the screen.

Now I have finished with:

Ubuntu 7.10 server
Ubuntu 8.04 build from 2 weeks ago ( I don´t have the number because I am now using Windows sorry)
Ubuntu 8.04 latest build.

I´m sorry to say the next step would be to go for Ubuntu 8.10 and then I would have 3 Ubuntus on my box!!!

I play around every night with conf files, terminal commands, anything remotely similar to my problem I can google I have tried. One day, the SAMBA appeared in my Preferences. Aha I thought, finally. I opened it and worked for a while on right clicking and allowing shares for 7 folders on 3 different HDDs. But where are they on my network??? I cannot access them. 

And yes, I have changed the workgroup name, and have ugraded samba and and and and....

All I want is to go to bed and leave Linux Ubuntu connected to my network, or rather having my macs see and work with the Ubuntu box. As it is now, just before I go to bed, I close Ubuntu very very frustrated and launch XP, and voilá my computer appears on my macs and I can see and work the drives?

Why can I not get Ubuntu to do something so simple? I honestly do not know. It must be something stupid of me, because believe me I have spent two weeks and many many hours.

So, can someone please tell me how:

1.- Erase all the different Ubuntu versions I have in my system?
2.- Get me up and running a simple network where everyone can see, read and write everything?

Thank you...
SMC

---

### Post by Thelasko on 2008-10-30
I hate configuring samba manually.  I just install the system-config-samba package and use the nice GUI it provides.

smb.conf just gives me a headache. 

P.S. Don't forget to configure any firewalls you may have (you don't need one).

---

### Post by alphaniner on 2008-10-30
You have tried the complicated way, but have you tried the simple way?  First, see if your Ubuntu can access shares on Windows by typing 'smb://<IP>' into the Nautilus address bar.  If you are wanting to share from Ubuntu, install samba-server, set your folders to be shared, then from Windows type '//<IP>' to see if they are accessible.  I don't know how well this setup will work when it comes to browsing the network tree, but when it comes to directly accessing shared resources it has (almost) never failed me.

---

### Post by Sarmacid on 2008-10-30
I don't have access to the guide where I saw how to share folders on the network, but I did it last saturday and it still works. For some reason, sharing the files had to be done running nautilus as root, otherwise it wouldn't work. I also had to tweak the smb.conf adding a line so I could share files from my ntfs partition.

To erase all those Ubuntus, just install a new one over them, or format and resize the partitions.

---

### Post by smcaro on 2008-10-30
Many thanks for your answers.

I cannot do what is suggested however, because when I run Ubuntu I no longer have windows! My other 2 computers are macs.

I don´t want to access the macs from Linux. I want the macs to access the 3 HDD on the XP/Ubuntu machine. 

I am pretty sure I have samba server, because I have the GUI. I can set the shares but they simply don´t work! 

Maybe I can uninstall ( I don´t know how to do that in Ubuntu) samba and reinstall.

BTW NFS and Netatalk don´t work either. I tried...

Thanks
SMC

---

### Post by Kellemora on 2008-10-30
I SMC

Don't feel alone!
I think we've all pulled our hair out over this one.

As UNLIKELY as this is going to sound, just do it and you should be up and running.

I spent DAYS trying to figure it out, two identical smb.conf files, one worked one didn't ON THE SAME COMPUTER....  I joked that the only thing different was the brand of hard drive, because I was swapping a working hard drive for one that was a mirror and the network wouldn't work from it.  Until you see what I did at the end here.
Not high tech, but works!

Restore your original smb.conf file as it came packaged.
Change the WORKGROUP to the name of your Workgroup.

If Synaptic didn't load smbclient along with Samba, go ahead and install that.  Don't know what it does, but we didn't get file sharing to work until it was installed.

And here is the killer.  If the network don't work, uninstall Samba and reinstall it.  If it don't work, do it again.  They say three times a charm!

Simply by uninstalling and reinstalling Samba, our network of 8 computers are all working fine and see each other.

On occasion, if a file don't show up or a computer comes up missing, just typing either the IP or the name of that computer will sometimes bring it back up.  I like to keep the whole shared folders mounted on the desktops of the computers that use them.

What that means is after an upgrade that requires a reboot, I sometimes have to uninstall and reinstall Samba a couple times to get everything up and running again the way I like it.

Sounds stupid, sounds crazy, sounds illogical, BUT IT WORKS!

TTUL
Gary

---

### Post by Thelasko on 2008-10-30
In the samba configuration window go to Preferences>users and make sure you have a user setup.  If you don't care who accesses your shared folders just select "allow access to everyone" under the access tab under properties.

---

### Post by smcaro on 2008-10-31
Thanx Thelasko,

been there done that! Yes I have set uo all users. I have tried setting up individual users. When I do, the computer appears on the network and the macs ask for a username and password, but guess what? Ubuntu machine does not allow the connect. Hell I don´t even know how to get to root, because it sometimes doesn´t work! And when it does, you guessed, root cannot change THOSE parameters!!

Flying the space shuttle is probably easier. I am so disappointed. As I have said elsewhere, 5 years ago I went out and bought a magazine, it had a CD, I put it in an old Pentium II box and set up a file server for my 3 windows machines. That was 5 years ago and it was easy! Now 5 years down the road I am in Zimbabwe ( they don´t sell magazines in this country) and internet is slow. SO I have spent 2 weeks of my time with this Ubuntu. 

I suspect that the only way for me is back to XP. At least it works most of the time. Today I brought home a Windows laptop from work. Plugged in the Ethernet and in seconds my two Macs coould read/write, exchange files. Not so with Ubuntu I am afraid.

Kind Regards and thanx
SMC

---

### Post by Thelasko on 2008-10-31
I don't know about Macs but in Windows I always have to go to "view entire network" to access my samba shares.

---

### Post by Commander_Keen on 2008-10-31
HI SMC
  Question:  The folders that you want to share, they located on a Partition that is fat32 or NTFS?  Maybe it matters maybe it does not

---

### Post by smcaro on 2008-11-01
Commander_Keen: both actually. One of the 200 gig HDD is NTFS on two partitions. The other 200 gig HDD by now is a mixture of ext3 linux partitions. And the external Terabyte HDD USB is fat32. 

I am afraid I cannot send a copy of my smc.conf file because I reformatted the linux partitions and will try a fresh install later.

Thanks and please keep any ideas coming....

---

