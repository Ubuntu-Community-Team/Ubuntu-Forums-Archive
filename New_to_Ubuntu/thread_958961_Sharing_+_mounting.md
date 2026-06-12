---
title: "Sharing + mounting"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by timcee42 on 2008-10-25
Few questions.1st- how do i share folders, both to other linux and windows machines, have set up Samba but permissions are screwing it all up. Whenever i go to do this i get =
net usershare' returned error 255
Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

have looked around and tried a few things but not helping. All these drives are NTFS format.

Also i have one drive that i have to keep on mounting on startup, where/how do i stop this from recurring.

Cheers

---

### Post by Little Girl on 2009-10-27
> **timcee42 said:**
> 
net usershare' returned error 255
Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.


This page might help: [http://ubuntuforums.org/showthread.php?t=772706]("http://ubuntuforums.org/showthread.php?t=772706")

> **timcee42 said:**
> Also i have one drive that i have to keep on mounting on startup, where/how do i stop this from recurring.

To automatically mount a drive, you'll need to add its information to the /etc/fstab file. This page should help: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by mapes12 on 2009-10-27
I gave up on Samba to access my XP box because of all the configuration required. Instead, I now use PyNeighborhood which I find much easier. This is how I set it up:

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

---

