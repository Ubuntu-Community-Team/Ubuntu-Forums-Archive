---
title: "Howto Desktop sharing from/to Dapper Kubuntu"
date: 2006-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-05-07
Hi,
   Here is just a basic process to get your desktop sharing up and running. No commands in the terminal, all from gui! I have not done more than this and anyone is welcome to expand the howto. I have just briefly tested both ways on a Windows and Kubuntu PC on the same lan.

_**Desktop sharing in Dapper Kubuntu**_

If you have a couple of PC's on your own lan or intranet, you can use your PC to take control of any of the remote PC's via their desktops Kubuntu already comes with Krfb and Krfc installed and you can use TightVNC (Download for free) on the Windows PC.

_Windows PC sharing Kubuntu PC_
On the Kubuntu PC use Krfb (Desktop Sharing) and run from the menu
Create a personal invite in Krfb and note the automatic password
Run TightVNC viewer on the Windows PC and add the IP of the Ubuntu PC i.e. 192.168.0.3
Type the password that was provided on Krfb on the Kubuntu PC
And Voila, you can see the desktop of the Kubuntu PC

_Kubuntu PC sharing Windows PC_
Launch TightVNC server on Windows PC
Add your own password that you want to use from Kubuntu
Launch Krdc (Remote Desktop Connection) on the Kubuntu PC and add vnc:/192.168.0.1 (or the IP of the Windows PC).
If you have a firewall active on the Windows PC you may have to allow this connection.
Now enter the password on the Kubuntu PC when requested
And Voila, You can see the Windows PC desktop.

---

### Post by Archibaldd on 2009-05-07
Information provided is worth reading and great use to the newbies,  thanks for sharing.

---

