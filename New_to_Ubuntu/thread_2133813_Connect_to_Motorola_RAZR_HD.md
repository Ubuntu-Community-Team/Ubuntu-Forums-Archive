---
title: "Connect to Motorola RAZR HD?"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by nycap on 2013-04-09
I am having trouble connecting my new driod (Moto RAZR HD with Jelly Bean) to Ubuntu 12.10 with the USB.   When I connect the device it is not recognized properly, its recognized as device manager. I ran the installer  and it seemed to install but no program shows up in Dash.  Searched Google and got nothing.  I dont know what I am doing wrong here; Has anyone delt with this?

---

### Post by 3rdalbum on 2013-04-09
Android 3 and Android 4 devices don't mount on Ubuntu 12.10 and below without some hacking around.

I couldn't get it to work even with the hacking around. Installing Windows software in Wine will not help.

In the end, I downloaded a program onto the Nexus that sets up an FTP server. I connected my Nexus to my wifi network, and used the Ubuntu computer to access the FTP server running on the Nexus (File > Connect to Server... in Nautilus). This works pretty well.

Alternatively, I've heard that Ubuntu 13.04 fixes the problems with MTP support and will mount Android 3.x and 4.x devices out-of-the-box.

---

### Post by cortman on 2013-04-09
> **3rdalbum said:**
> 
Alternatively, I've heard that Ubuntu 13.04 fixes the problems with MTP support and will mount Android 3.x and 4.x devices out-of-the-box.

Hopefully this is an upstream improvement as well... I have tried many, many times to get my Android phone to mount in numerous Linux systems with zero success.

---

### Post by thenoodler on 2013-05-24
At this point in time, it is impossible to connect the Motorola RAZR HD / HD MAXX to Linux via USB.  The reason is that Motorola does not provide drivers for these models in linux. I have contacted them about this, and they said they do not plan to provide drivers for linux in the future, either - which a dirty shame... especially, considering the android is linux-based.  For now, our options are to use Windows or Mac, or (as **[COLOR=#000000][3rdalb]("http://ubuntuforums.org/member.php?u=61044")um, [/COLOR]**[COLOR=#000000]suggested, using an ftp client to copy files. [/COLOR]

---

### Post by nonneg on 2013-07-12
I've accidentally found a way to connect my razr m (xt905) to ubuntu 13/04 !:guitar: 
After reading this topic I tried to connect via VirtualBox. 
Razr appear to OS like two USB devices, and when I added one of them to VBox permissions, the other popped up in Ubuntu =) I can browse both of phone's SD's 

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)
*"Devices Mounted in Guest OS will likely be unavailable in Host OS"*

So you have to block someway the first device to get access to SD

Proof pic included

[ATTACH=CONFIG]244662[/ATTACH]

---

### Post by Gnub_Daemon on 2013-09-11
I know this is a few months old but all you need to do is put your phone into usb debugging mode.

---

### Post by hydro123 on 2013-10-14
Hello everyone, I realize this is an old thread. With OSs previous to 13.04 without MTP support for individuals that are looking for a way to down load images from their Droids this worked very well. First thing is get a new micro USB charge/sync cable. I have many and found bad contacts to be a major problem. On multiple previous versions, 10.04, 10.10 and on when you mount your droid via USB, there a pop up stating "Media Device", meaning MTP. Change connect as on droid to Camera (PTP), drag sreen down on droid to see USB connect appt, touch and you can change connection from MTP to PTP, and open with Gwenview. List will start with "camera:>USB PTP Class Camera" this brings up a folder "store_00010001" open and string will be "camera:>USB PTP Class Camera>USB PTP Class Camera" open DCIM file and then camera and all images should be available. This, at least, syncs the gallory from the droid.

---

