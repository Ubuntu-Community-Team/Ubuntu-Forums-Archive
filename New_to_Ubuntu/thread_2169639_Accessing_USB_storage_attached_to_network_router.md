---
title: "Accessing USB storage attached to network router"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by CyberPotato on 2013-08-22
I have a Western Digital My Net N900 router.  Attached to it via USB is a Seagate Free Agent GoFlex hard drive.  I have the hard drive set up in the router to be accessible as a shared drive or via FTP.  I am running Ubuntu 13.04.  I am able to access the storage using my browser, via FTP.  I would like to be able to access it as a shared drive using my file manager, but it does not show up under "Browse Network", even though the router itself does show up there.  I understand from reading some older posts that I should be able to mount the drive, but I have been unable to figure out how to do this.  One thing I have tried, based upon a couple of posts I read, is:

sudo mount -t cifs //192.168.1.1/Seagate_FreeAgent_GoFlex_33 /media/public -o rw,uid=dave

which yields:

Unable to find suitable address.

The address I am using, (which I assume is being referred to as unsuitable) //192.168.1.1/Seagate_FreeAgent_GoFlex_33, I obtained from using my browser to FTP to //192.168.1.1, so I assume it is correct, but I'm very rusty at this stuff, so am not so sure.

Any help would be much appreciated.

---

### Post by texaswriter on 2013-08-22
If you could check with this link, see if this helps you any bit. 

[http://askubuntu.com/questions/109505/how-do-i-access-an-external-hard-drive-plugged-into-my-router](http://askubuntu.com/questions/109505/how-do-i-access-an-external-hard-drive-plugged-into-my-router)

---

### Post by kurt18947 on 2013-08-23
I recently bought a WD N600.  Filezilla works perfectly.  I'm using a USB flash drive for storage though I'd experimented with a H.D. in an enclosure as well.  I'm still playing with connecting via Nautilus or Nemo.  The Nautilus version in 13.04 doesn't seem to have a "connect to server" option, it's back in 13.10

---

### Post by CyberPotato on 2013-08-24
Thanks for the comments.

Ok, finally got this to work.  After much playing around, I defined a server name in /etc/hosts

192.168.1.1    [I]servername
[/I]
then added the following line to /etc/fstab

//*servername*/seagate_freeagent_goflex_33     /media/public  cifs    uid=1000,guest,iocharset=utf8  0       0

and the drive mounts now when I boot.

The same line in /etc/fstab using the IP address in place of the servername did not work.  Maybe someone knows why?

I do get an odd error message at boot:

Aug 24 11:29:15 Spud kernel: [   25.286154] CIFS VFS: Error connecting to socket. Aborting operation
Aug 24 11:29:15 Spud kernel: [   25.286242] CIFS VFS: cifs_mount failed w/return code = -101

I understand from doing a bit of reading in various forums that this is likely due to the mount being attempted before the network is connected.  It doesn't appear to cause a problem, other than flashing an error message during boot-up.  Still, if anyone knows how to correct this, it would make things a bit neater. :)

---

### Post by jiss2 on 2013-09-10
i am also using ubuntu 13.04 and have a WD750 with a Seagate FreeAgent 1TB drive connected to it .
This can be achieved in 3 simple steps via Nautilus UI  

1) Open Files menu (top left corner)
2) Click Connect to server option 
3) in the Server Address field enter "smb://<yourrouteripaddress>"  (eg: smb://192.168.0.1) and click connect 

you should be able to see your shared folder in the file manager now
I think many of us will look to right click the network share icon and expect to find the "Connect to server" in right click menu there (i did that too) which is not there

---

### Post by CyberPotato on 2013-09-10
> **jiss2 said:**
> i am also using ubuntu 13.04 and have a WD750 with a Seagate FreeAgent 1TB drive connected to it .
This can be achieved in 3 simple steps via Nautilus UI  

1) Open Files menu (top left corner)
2) Click Connect to server option 
3) in the Server Address field enter "smb://<yourrouteripaddress>"  (eg: smb://192.168.0.1) and click connect 

you should be able to see your shared folder in the file manager now
I think many of us will look to right click the network share icon and expect to find the "Connect to server" in right click menu there (i did that too) which is not there

Thanks for the reply. I found a way to automatically mount the drive when I boot up, as noted in my last post.  It's a bit easier than having to manually mount, so you might check it out, if you like.

---

