---
title: "Samba share lost at boot? not the usual problem"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Huzudra on 2008-09-27
so i have a 200gb ntfs drive of old media that wont physically fit (not enough ide channels) in my main PC, which yes is a windows box (linux+nvraid=fail as of yet).

when i reboot the linux box here, and goto my windows machine the samba share is NOT accessible.  alright, i goto my linux box and open samba, open the drive, both are 'working'. check the shares properties in samba, it all looks jive there.  when i click OK, i get a message that...

"The directory /media/disk does not exist. Please specify an existing directory"

which is odd because under nautilus, the disk is still seen as media/disk!  when i used samba under 6.06 for the same purpose (with this same drive actually, different computer) i never did have this problem.


what am i doing wrong? how do i fix it?

---

### Post by Huzudra on 2008-10-10
for some reason the drive is not mounted at boot, but it is showing in the 'places' drop down.

how do i fix this? i mean as soon as i click on it it seems like its mounted.

---

### Post by bodhi.zazen on 2008-10-10
Do you need help with the server (Linux box) or client (windows box) ?

---

### Post by Huzudra on 2008-10-11
ha, right now...BOTH!

windows is doing its pissy thing where it wont see the linux box on the network after either are power cycled.  it worked 10 minutes ago until i powered down the linux box to install the gigabit nic.   i also rebooted the pc since it had been up for a week straight,  upon powerup i cant see the linux box from windows or vice versa.

:lolflag: i are screwed.  this is almost getting comical, both can access the router and modem and internet so both the network hardware does work, nics work, cables work, etc.  its a software problem going on, hardware i can deal with easily.  

in windows the linux box isnt showing on the workgroup, it was previous to the power cycle.

in linux the windows box isnt coming up, nor can i see any of its shares.

netbios is enabled in windows (random googling suggested that may help).

and now it works again, some reason or another the linux box WAS having a connectivity issue. in my near slumber i must have unticked roaming mode which for some reason made it not show up to anything on the network, ticking roaming mode got the thing working again. huzah!


**i still have the same problem as in the first post, drive not mounting at boot until i open it from 'places'  so yes this is a server problem then i suppose.**

---

### Post by bodhi.zazen on 2008-10-11
sounds as if it is working server side.

On your windows box, map a network drive and have it mount automatically at boot.

[http://www.cs.umd.edu/faq/pc/map_network_drive/map_network_drive.html](http://www.cs.umd.edu/faq/pc/map_network_drive/map_network_drive.html)

---

### Post by Huzudra on 2008-10-11
no no, the original post IS talking about the linux box.

i have to open the drive in places in LINUX on the linux box before samba can see the drive or before ANYTHING can see the drive. does fraps work in linux? i can make a video of the problem!

1. press power button on linux box
2. linux box boots to desktop (auto logon)
3. 203GB media is not on desktop
4. 203GB media is not accessible as a share to any other PC
5. open samba, click on media/disk
6. all looks the same as last time
7. click OK
8. "The directory /media/disk does not exist. Please specify an existing directory"
9. open /media/disk in nautilus from 'places' where its called 203GB Media
10. 203GB Media is now on desktop
11. go back to samba, open media/disk
12. all the same as before, click ok, pause, properties close
13. 203GB Media is now accessible to all other network PC's AND any other linux programs.

lets say i leave a media player open on the linux box when i shut down (session saves) and it was playing a file on 203GB Media, when i boot back up it will say that /media/disk/filename.avi is not accessible.  open /media/disk in nautilus from 'places' and then the file is once again accessible.

it seems to ME that its a problem with the drive not mounting at startup.




i cant have windows automatically mount the drive at boot if the linux box is not mounting it when it boots, follow me?  cant mount whats not mounted!

---

### Post by bodhi.zazen on 2008-10-11
OIC, I thought you were having problems mounting the share on Windows.

To have a drive mount automatically at boot you need to edit fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

If you added an entry for fstab, and it is not working, post it here so we can look at it.

---

### Post by Huzudra on 2008-10-11
> **bodhi.zazen said:**
> OIC, I thought you were having problems mounting the share on Windows.

To have a drive mount automatically at boot you need to edit fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

If you added an entry for fstab, and it is not working, post it here so we can look at it.

thanks!, i think thats what i did when i had it setup in 6.06 a few years back, but that was soo long ago and once i had it set i just left the box on for like 2 years straight and never really touched it again except for some updates.  as soon as i saw fstab it rung a bell. i swear i know what some of these things are, i just cant remember what they're called beyond 'that config thing for the disks' :lol:

i think pysdm is the best choice for me, 7/10 times i somehow mess up editing config files i some way that keeps the system from booting or knocks me to command line only...oh how i heart my point and click gui!

---

### Post by Huzudra on 2008-10-11
seems like pysdm did the trick for me! awesome.

---

### Post by bodhi.zazen on 2008-10-11
Woot ... :guitar: 
 
Please mark this thread as solved, it saves the time of many volunteers looking to help  
[indent]... and users looking for solutions.[/indent] 
 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

