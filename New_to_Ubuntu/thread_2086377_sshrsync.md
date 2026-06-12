---
title: "ssh/rsync"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by Judemarg on 2012-11-20
Hi

Hope someone can help.
I'm running Ubuntu 12.04 and I have a netgear readynas Ultra 2. I have a local network to which the readynas is attached.  I would like to back up my files on my laptop to the readynas over the network using rsync.

I'm using lucky backup and feel I have the settings correct and openssh is definitely installed but it just won't connect.  When I run rsync I get this message:

ssh: connect to host nas-8A-EE-E2 port 22: Connection timed out 

rsync: connection unexpectedly closed (0 bytes received so far) [sender] rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9] 

Underneath it says 
trying to send an email
       . . .
The specified command is probably not installed

command:   
exit code: 0
output:    No such file or directory

I've tried to mount the share and browse so I can backup locally instead but that doesn't work either.

Thanks in advance

---

### Post by papibe on 2012-11-20
Hi Judemarg.

> **Judemarg said:**
> ssh: connect to host nas-8A-EE-E2 port 22: Connection timed out
It looks like ssh is not actually enable on the ReadyNAS

AFAIK, the Netgear ReadyNAS Ultra 2 does not support officially rsync over ssh as an standard feature (read [this]("http://www.readynas.com/forum/viewtopic.php?f=124&t=52914")). It may require more tweaking to enable it, if possible at all.

> **Judemarg said:**
> I've tried to mount the share and browse so I can backup locally instead but that doesn't work either.
That should be more easy to accomplish. Are they smb share or nfs exports?

Regards.

---

### Post by Judemarg on 2012-11-21
Phew glad its not me being completely stupid and changing stuff on the Readynas looks a bit too scary for my liking.

So I guess I need to work on getting it mounted and use it as a local backup.

When I look at the properties of the share it says smb.
When I right click and click mount it seems to do something but I can't browse to it as if its a local folder.  I've read about changing /etc/fstab/ to get a nas mounted but I'm not 100% certain how to go about that.
The helpfile on the nas also talks about NFS and describes doing this -  mount ipaddr:/Sharename /mountdir but what is my mountdir? Is that /etc/fstab/?

Any advice gratefully received.
Judith

---

### Post by papibe on 2012-11-21
If the ReadyNAS supports it, I would recommend using NFS.

Then get the share (or exports) available from your machine by doing:
```
showmount -a server
```
(replace server with your server's hostname or LAN IP).

The results should look something like:
```
All mount points on server:
192.168.1.101:/path/to/dir1
192.168.1.101:/path/to/dir2
```
In this instance, /path/to/dir1 would be a 'sharename'.

The term 'mountpoint' basically refers to a directory which main use is to mount the share on it. In practice, just create a directory.

If you want it to share with all users, you could create it closer to the root directory:
```
sudo mkdir -p /nfs/dir1
```
Or for just personal use, in your own home:
```
mkdir ~/dir1
```
Then I would try to mount it manually in order to check if everything is OK:
```
sudo mount -t nfs  server:/path/to/dir1  /nfs/dir1
```
Once that is working properly, you are ready to create a permanent mount point on your /etc/fstab

Let us know how it goes.
Regards.

---

### Post by Judemarg on 2012-11-25
Hi
When I input "showmount -a server" it didn't give me anything but then I've done the second thing you said and created a directory for the server to mount to and that seems to work.  

Now I get 
All mount points on 192.168.1.75:
192.168.1.64:/c/backup
192.168.1.64:/c/media

I then went onto manually mount backup and then I've done a test run on rsync which seems to work.  I have files on the NAS and I can access them directly through the network.
So that all seems to work.

So the backup share is what it sounds like; to backup our laptops (once I get this configured on my husbands as well)
But I will also be using the media folder to store music which will be accessed by a squeezebox.
Is it possible to mount the folders in two different places at the same time?  If I want to mount different folders I wonder if I want it mounting automatically at start up? 
Am I making things too complicated now?

Judith

PS I've just unmounted and I've gone back to look at the NAS media folder and I got this error 
DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

So now I'm confused

---

