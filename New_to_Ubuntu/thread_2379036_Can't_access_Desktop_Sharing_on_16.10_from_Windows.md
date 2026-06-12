---
title: "Can't access Desktop Sharing on 16.10 from Windows 10"
date: 2017-11-30
forum: New to Ubuntu
---

### Post by ianmanning on 2017-11-30
I want to get remote desktop access to my Ubuntu machine from Windows 10 on another machine on my LAN. I've just installed Ubuntu 16.10 and have Desktop Sharing configured to "Allow other users to view your desktop" and "Allow other users to control your desktop". I also have the option selected to "Automatically configure UPnP router to open and forward ports". 

I am trying to connect to my Ubuntu host from a Windows 10 machine using a RealVNC client downloaded from realvnc.com. When I try to connect I get this:

"Unable to connect to VNC Server using your chosen security setting.
Either upgrade VNC Server to a more recent version from RealVNC, or
select a weaker level of encryption."

Prior to this I had tried installing x11vnc and tightvncserver, but each time I tried to connect using a VNC client from my Windows 10 machine I got "connection refused".

Can anyone help?

---

### Post by howefield on 2017-11-30
Your first step should really be to get on to a supported release of Ubuntu. 16.10 has reached its end of life.

---

### Post by ianmanning on 2017-11-30
> **howefield said:**
> Your first step should really be to get on to a supported release of Ubuntu. 16.10 has reached its end of life.

Is Desktop Sharing supported on Ubuntu 17.04 - for access using VNC from Windows 10?

---

### Post by howefield on 2017-11-30
> **ianmanning said:**
> Is Desktop Sharing supported on Ubuntu 17.04 - for access using VNC from Windows 10?

Yes, you can do the same with 17.04 as you can with 17.10. Just to make sure that you are aware, Ubuntu release a new version every 6 months, they are supported for nine months except for the April release in the even numbered years, ie April 2016 is the current LTS, 18.04 will be the next one. A long winded way of saying that support for 17.04 will end in January.

I'd suggest either using the last LTS 16.04 or the latest 17.10, both of which can be directly upgraded to the next LTS.

---

### Post by ianmanning on 2017-11-30
> **howefield said:**
> Yes, you can do the same with 17.04 as you can with 17.10. Just to make sure that you are aware, Ubuntu release a new version every 6 months, they are supported for nine months except for the April release in the even numbered years, ie April 2016 is the current LTS, 18.04 will be the next one. A long winded way of saying that support for 17.04 will end in January.

I'd suggest either using the last LTS 16.04 or the latest 17.10, both of which can be directly upgraded to the next LTS.

I've gone for the upgrade which was offered in the "Software & Updates" section - 17.10. Fingers crossed I'll have more luck with remote desktop on that version...

---

### Post by ianmanning on 2017-11-30
Hmmm...so that was not so surprising...I've upgraded to 17.04 and get exactly the same error when I try to connect
???

---

### Post by cariboo on 2017-12-01
Are you using Unity as a desktop environment? I'd suggest using a different manager.

---

