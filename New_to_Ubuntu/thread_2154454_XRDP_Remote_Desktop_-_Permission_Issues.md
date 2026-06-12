---
title: "XRDP Remote Desktop - Permission Issues"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by NRF19 on 2013-06-14
Hi,

I'm new to ubuntu and am setting it up on my mediaserver. I have installed Ubuntu 12.04.

My problem arises in having a number of harddrives connected to the machine, when I have this machine wired up in-front of me I can mount these drives and then my smb shares see where they've been mount e.g. '/media/TV Series' and share them to the other PC's in my house. 

My intentions are to run my server in the kitchen with just a plug and ethernet and control it remotely, for this I installed XRDP.

My problem arises when I remotely connect in the fact that the software I set to automount the drives on startup (AriOS) doesn't seem to have mounted the drives and doing so manually (in the GUI clicking the drive name) delivers the error 'Unable to mount "drive name" not authorized' I have googled a bit to try find a solution but am at a loss. When I am controlling the PC locally (Keyboard and monitor plugged into it) the drives mount on boot automatically or I can manually (as aforementioned) mount them however this way I cannot.

I'd like to point out that everything I have achieved thus far has been following step by step (copy/paste into terminal guides) and I have next to no knowledge of Ubuntu or Linux.

Edit: I forgot to mention I tried as per the recommendation of something I saw creating a blank .Xauthority document then using "touch~/.Xauthority" and "chmod 600 ~/.Xauthority" to no avail.  The drives are NTFS and named TV Series and Movies
 
Thanks in advance,
Nathan.

---

### Post by NRF19 on 2013-06-15
Problem solved after another morning of google'ing 

If anybody is interested it wouldn't let me mount to /media for some reason but by creating a root directory in media

```
sudo mkdir /media/root
```

I could then mount the required drives into there via terminal with no problems

```
sudo mount /dev/sdb1 /media/root
```

---

