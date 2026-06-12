---
title: "How to mount a share on other end of a VPN"
date: 2018-09-20
forum: New to Ubuntu
---

### Post by neil.down on 2018-09-20
Hi, I&#8217;m new to Ubuntu and I&#8217;d so love some help please. Ive used Windows for 20 years but for the last 5 years I&#8217;ve been trying so hard to give it up permanently and have been using Mint at home and now Ubuntu 18.04 Bionic Beaver, Win10 drives me nuts!

I&#8217;ve been using FreeFileSync, a really great copy/backup files app for a few years but I&#8217;ve never been able to get it to work properly over my network as it errors with can&#8217;t delete .tmp.  Last week I found out that I need to mount the shares on my networked Synology NAS first, then use these mounted shares to point to from FreeFileSync. When using the mounts the transfers work correctly and don&#8217;t product an error. (Just shows I&#8217;m not good with Linux, I&#8217;ve been trying to solve this problem for 2 years, doh!).

So now I want to mount a share over a VPN (OpenVPN) as I do off-site backups of photos etc to a friend&#8217;s NAS (mutual backups). I&#8217;ve tried every combination to get this working except the one that makes it work!  By the way, my network is 192.168.1.xx and his is 192.168.0.xx. 

I&#8217;ve taken the mount command that works with my network and changed the url to the IP address on the other end of the VPN.
Nautilus works fine, I just enter smb://192.168.0.5/photos/ into the &#8216;other&#8217; box and all the folders appear and I can copy and delete just fine over the VPN, but using this address with FFS doesn&#8217;t work as the &#8216;can&#8217;t delete .tmp files&#8217; error appears when I try.

I&#8217;m trying things like:
mount -cifs -o,rw, /192.168.0.5/photos/ ~/Desktop/Far_end_photos/

Am I&#8217;m right to think that the &#8220;~/Desktop/Far_end_photos/&#8220; expression is a folder on my computer?  It certainly works when accessing my networked NAS.

So I&#8217;m looking for a mount expression that will work over a VPN to a Synology DS115, Linux system, probably ext4 formatted.


Thanks so much.

I&#8217;ve tried installing autofs, but couldn&#8217;t really understand how to get that to work, and messing with fstab, but couldn&#8217;t add anything useful to make that work even those my mount commands often asked for an entry in the etc/fstab file.

---

### Post by TheFu on 2018-09-20
```
mount -cifs -o,rw, /192.168.0.5/photos/ ~/Desktop/Far_end_photos/
```
is incorrect.  Check the options. Check the remote address specification.  Don't use ~/ for the mount location. Use the full path.

I'd guess 
```
sudo mount -t cifs -o rw,async ://192.168.0.5/photos/  /home/${LOGNAME}/Desktop/Far_end_photos/
```
is what you want, but you'll also need to specify userid/groupid options. Mounting storage into a HOME directory is usually a bad idea.

Also, not all openvpn connections support browsing. I think the slower, tun device has to be used for that to work.

Honestly, CIFS should be avoided outside any LAN.  Finding a better protocol really would help.  CIFS doesn't support full permissions in the backups, so you'll need to capture that data some other way.

Or a better backup tool that has a client/server architecture and don't require mounts at all.  duplicity, rdiff-backup are two options. They work over ssh tunnels, like rsync does.  C/S backups are much safer to avoid malware issues than mounting storage in a way that malware can directly access it.

I've never heard of FreeFileSync.  I use rdiff-backup and rsync both over ssh to perform networked backups.

---

### Post by neil.down on 2018-09-21
Well, thank you much for your response. I really appreciate it.  I can see that I&#8217;ll be spending the evenings over the next few weeks trying out everything you suggest. I&#8217;ll read up on rdif-backup and give it a go.

---

### Post by neil.down on 2018-09-21
So am I right in thinking the second expression of the sudo mount instruction is pointing to a folder on my laptop and the first expression points the the url and share/folder of the NAS at the far end? In my rubbish example of a mount command I should have made it more clear and said Copy_of_far_end_folder.

I take your point about malware when setting up a mount folder, interesting, I can see how the security vulnerability occurs so I won&#8217;t be doing that in the future.

---

