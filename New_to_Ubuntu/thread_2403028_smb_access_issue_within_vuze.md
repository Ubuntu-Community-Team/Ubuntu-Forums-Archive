---
title: "smb access issue within vuze"
date: 2018-10-06
forum: New to Ubuntu
---

### Post by dalton1958 on 2018-10-06
Hi all,
I have just installed ubuntu for the first time so am completely green.  I have a laptop with ubuntu installed which I want to use solely for downloading.  At the moment all seems fine and I can access my folders shared on a freenas server via the ubuntu file manager.  The problem starts however when I install Vuze and try to setup the default file location, I want to use a location on my freenas server which is available however it does not show up using browse within vuse, I cannot see any network shares or a mounted share even though they are visible in ubuntu file manager.  I have read about and tried using sshfs but this seems somewhat complicated given my total lack of linux/ubuntu knowledge.  I would rather not return to using windows if possible but if simply accessing network shares is such a problem I may not have any choice.

My freenas server is at 192.168.0.16 and I have two users set up, root and steve, the folder I want to map to is at \\192.168.0.16\Torrents  . I have tried the sshfs route but not had any success as I get an error about not having write permissions to the folder I set up on the laptop to mount the share into which is /mnt/torrent.  Should it really be this complicated? is it an issue with Vuze? I dont mind using an alternative if it is.

Trying to master new operating systems is difficult at the best of times but when you are over 60 it becomes a lot harder so any simple step by step help or advice would be most appreciated.

Thanks in advance for any help provided.

---

### Post by him610 on 2018-10-06
Hello dalton1958 and welcome to the forums.

I have been using freenas vers 7.2 as a fileserver for eight or nine years. I set it up during initial installation, and the only time it has been down is during an occasional power outage which has been addressed with a UPS.

Which version of freenas are you running?
Is the freenas server installed on a standalone system?
What services do you have running on freenas: cifs/smb, nfs, ssh, BitTorrent, or others?
Is this a mixed system network - Windows and Ubuntu?

Linux is case-sensitive. Torrents is not the same as torrents is not the same as torrent.

Your slashes should all lean to the right "/"

Not sure what *Vuze* or *vuse* is. Maybe *fuse*?

> Trying to master new operating systems is difficult at the best of times

How right you are. You actually are attempting to master two operating systems, freenas and ubuntu.

---

### Post by dalton1958 on 2018-10-07
Hi,
thanks for taking the time to respond, because I could access the freenas shares without issue from windows systems and having just installed ubuntu I automatically assumed the issue was with ubuntu, however I later discovered that I could no longer connect to the freenas shares with Plex on the Nvidia shield. My thoughts were then directed to the freenas update done earlier in the day so created a new boot drive from the original version, imported the volumes and I could then access the shares on the shield.  I am now wondering whether the ubuntu issues could be linked to the same problem.  I have at the moment returned to the windows install but simply need to replace the hard drive with the ubuntu install on it and will try again and report back as to how I get on.  If I still have issues I will ensure that my update contains the information you requested.

Thanks again for taking the time to help.

---

### Post by dalton1958 on 2018-10-07
Hi,
tried again and still same issue so reluctantly installed a copy of win 10 lite which gives me the speed upgrade I wanted over standard windows and has the benefit of being an environment I am familiar with.  Thanks for trying to help.

---

