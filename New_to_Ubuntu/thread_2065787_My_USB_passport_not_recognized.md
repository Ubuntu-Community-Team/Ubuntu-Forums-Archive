---
title: "My USB passport not recognized"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by gfar on 2012-10-02
OK so ubuntu will not recognize my usb passport.  Normally when I connect my usb it automatically runs its installation on to the pc then I am prompted to enter my password  to open the device and view my files. I am thinking I have some sort of firewall or restriction preventing me from successfully opening my usb .. Your help and knowledge is greatly appreciated

---

### Post by newb85 on 2012-10-02
We'll need to know more about your USB drive.  Make and Model.

---

### Post by steeldriver on 2012-10-02
If you are talking about a Western Digital My Passport drive then afaik the 'WD Unlocker' software is Windows / Mac only - you may be able to mount it if you connect it to a Windows box and turn off the encryption first

---

### Post by Mark Phelps on 2012-10-03
WD uses hardware encryption on their Passport series external drives.

When you connect those in MS Windows, and app is launched that provides a front-end for creating/changing/entering the password. Once that is done, you can then access the files.

Without that MS Windows front-end, there is literally no way to bypass the hardware encryption and access the drive.

If you can get to it in MS Windows, see if you can REMOVE the password using the login front-end.  Of course, you will need to use the current password to login to do that.

But ... once you do that, you might then be able to mount the drive in Linux.

---

### Post by gfar on 2012-10-03
Ok thanks Yes I have a Western Digital passport and I do have a laptop that runs windows where i can take my password off. After that is done how do i go about Mounting? Please be specific as I am new to Ubuntu. Thanks alot

---

### Post by Mark Phelps on 2012-10-03
I said you "might" be able to mount the drive -- since I don't have one, I have no way to verify this.

When Ubuntu is up and running, and you then connect the external drive, you should see a drive icon added to the lower left part of the navigation panel of your desktop.  When you click that, it will open Nautilus and point to the partition on the drive.

If there is no icon, it could be that it's not being mounted.

To see if Ubuntu even sees the drive, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  This will list out all the drives and all their partitions. 

If that doesn't show your external drive, it could be that the drive simply can't be accessed in Linux. Any messing around with the drive after that to remove partitions (to remove the encryption capability) runs the risk of totally corrupting the drive and rendering it useless.

---

### Post by newb85 on 2012-10-03
I don't have a Western Dig drive, either, but I suspect you could  format the drive from Windows to behave like a normal drive.

---

### Post by Mark Phelps on 2012-10-04
> **newb85 said:**
> I don't have a Western Dig drive, either, but I suspect you could  format the drive from Windows to behave like a normal drive.

Actually, I believe that WD makes that very difficult to do -- since the password front-end autolaunches when you connect the drive to an MS Windows PC.

It would probably work better reformatting the drive in Linux, since that will NOT launch the password front-end -- but, of course, that will erase everything on it -- and I got the impression that the OP wanted access to the existing data, not a way to wipe the drive.

---

### Post by newb85 on 2012-10-04
I only recommended that as a way of making the drive usable in Linux.  And I was under the impression the drive wouldn't mount in Linux, so I thought it would be easier from Windows.

---

### Post by steeldriver on 2012-10-04
I think it should mount fine once the password is removed - I have one here attached to my Win7 box and after unlocking it in Windows (using the WD Unlocker) it mounted fine as a vboxsf in a Mint VM on the same host

[I haven't tried removing the encryption altogether and mounting it on a native *nix box because it is a work drive with sensitive stuff on]

---

### Post by gfar on 2012-10-04
Ok everyone I have successfully got my USB to work now. I would like to thank all of you for assisting me. 

How I solved the problem:

1. Connected USB to windows laptop, then unlocked the device

2. Turned the password security setting off

3. Then reconnected device to my PC running Ubuntu and the usb was recognized immediately

4. Thanks AGAIN!!!!!!!!!!! :)

---

