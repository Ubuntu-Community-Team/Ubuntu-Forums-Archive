---
title: "Cannot remotely access Ubuntu home server from otherPC/Settop boxes"
date: 2022-08-06
forum: New to Ubuntu
---

### Post by agarwaldvk on 2022-08-06
Hi Everyone


I have had my home server running successfully for a while now on 18.04 LTS. I upgraded it to 20.04 yesterday and now I cannot remotely access it from my other windows computers or from any of my set top boxes. But I can access them using my mobile phone.

Previously it would allow read only anonymous login without password through set top box but now it doesn't. Also, it doesn't get discovered using Microsoft Remote Desktop or Real VNC or even TeamViewer.


Can anyone please suggest what I can do to be able to access it from other devices on this new OS - 20.04 LTS?

Just to let you know that I only have very rudimentary knowledge of the details of this operating system.


Best regards


Deepak

---

### Post by arraybolt3 on 2022-08-06
By "remotely access", I'm assuming you're talking about SSH? Also, what remote desktop server software is running on the server? Xrdp? Do you have any firewall software running on the server?

My first suspicion with the remote login stuff is that maybe the software you're using on Windows and your set-top boxes isn't compatible with the newer SSH server for some reason. I'd recommend using PuTTY on Windows as an SSH client and see if that fixes it.

---

### Post by agarwaldvk on 2022-08-07
Hi arraybolt3


Thanks for your response.

> By "remotely access", I'm assuming you're talking about SSH? Also, what remote desktop server software is running on the server? Xrdp? Do you have any firewall software running on the server?

My first suspicion with the remote login stuff is that maybe the software you're using on Windows and your set-top boxes isn't compatible with the newer SSH server for some reason. I'd recommend using PuTTY on Windows as an SSH client and see if that fixes it. 


No, I don't mean SSH. I can login to the server using SSH through PuTTY from another Windows machine. I am just trying to access the video files using the WDtv Live Set top box (very old now).

I followed the steps from here to install xrdp but apparently its already installed :-

[https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-20-04/]("https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-20-04/")

and when I try to connect to it through Windows Remote Desktop, I get the following error (please see attached file)

Firewall - don't know. I didn't install one myself.

Is there anything else I can do?


Edit : Added the screenshot after trying to login through Microsoft Remote Desktop - just get a blank screen.


Best regards


Deepak

---

### Post by ActionParsnip on 2022-08-07
If you are trying to access video files, why not map a drive to the Ubuntu system, then watch the video on your Windows system.... Surely that would make more sense?

---

### Post by TheFu on 2022-08-07
> **ActionParsnip said:**
> If you are trying to access video files, why not map a drive to the Ubuntu system, then watch the video on your Windows system.... Surely that would make more sense?

Because he has a WDTV Live media player. and supports mkv and h.264 playback of hidef content? It can use DLNA and, I suppose, SAMBA v1 connections.  I have one here somewhere. Not a bad device. There are 3rd part firmwares for it which support NFS, which would be the preferred (i.e. better) way to access media files on the WDTV live device.  [http://forum.wdlxtv.com/](http://forum.wdlxtv.com/) is the forum for that firmware.

In 20.04, old CIFS protocols were deprecated for a number of reasons.  They can be re-enabled, but there are security implications in doing this.  The system upgrade process DOES NOT enable deprecated protocols.  

I've gotten the $50 out of my WDTV device in the last 10 yrs.  I extended the life of mine by using it as a purely data backup storage location for a few years, but the 10/100 network speeds were just too slow for my needs. [https://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live](https://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live)   Eventually, support for other video formats drove me to use a regular computer for video playback.  A used chromebook would be a good option for this - say an Acer C720 from 2011 which can be found for around $65 still.  Load up KODI on the chromebook and it should handle playback of any 1080p or less content. It has an HDMI video output which can drive nearly any display we have these days.

For remote access over the LAN, the best protocols are ssh and sftp.  PuTTY and WinSCP are the Windows tools for that, if you don't want to pay money.  WinSCP is a drag-n-drop file manager and accepts MS-Exploder drag-n-drop as inputs or outputs.

For remote desktop from Windows, I stopped using VNC and RDP very, very, long ago after learning about NX. For NX, x2go is the tool to use. It is about 2-3x faster than either VNC or RDP.

---

