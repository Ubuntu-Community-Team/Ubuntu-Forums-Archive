---
title: "Network Sharing problem"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by smergs on 2008-08-12
I'm trying to view a network share that is on a windows machine.  When I go to network I see the workgroup and I can even click on the pc, however none of the shares show up.  The same thing happens when I try to access a shared file on the ubuntu pc from the windows machine.

I'm running the latest ubuntu version and Windows XP SP3.

Also, to take it a little further, can I share an NTFS drive that is mounted in ubuntu?  I just want to share my music folder so I can listen to music on other computers.  So I only need read access on that share.  Actually, I only want read access on any share.  No reason for write access in my case. 

Thanks for any help anyone can provide.

---

### Post by rbc on 2008-08-12
Keep in mind, I am no expert, but here are a few tips that I have tried or heard of. Assuming you can ping the Windows machine, try typing the Windows IP address instead of the computer's name. Also, try typing the entire path to the shares. In other words, smb://nameofcomputer/sharedfolder. To take a stab at the last question, I do not think you can share the entire NTFS drive, but you can share a folder contained therein. However, unless the NTFS drive is listed in fstab, it will not auto-mount after a reboot, so the share on that drive will not be visible until you mount it.
Lastly, I read somewhere that nautilus (Ubuntu's default file browser) and samba (the application that allows shares between Unix/Linux machines and Windows machines) sometimes do not play nice together, so I installed Konqueror, which is Kubuntu's default file browser. I have had very, very few problems with Konqueror and samba

---

### Post by smergs on 2008-08-13
I installed Konqueror and was able to immediately see my windows shares.  That was the main thing I was trying to do.  I still want to get one folder on my ntfs drive shared but I'll post more about that later.

---

### Post by smergs on 2008-08-13
Ok, so I lied.  It's not exactly working.  :(
I can see my shares and see each individual file now however I can't copy the files over to the ubuntu pc.  It give me an error message saying something like "Error moving file."

Any ideas?

---

### Post by Riffer on 2008-08-13
Could be a variety of things.  How you have your shares setup, how you have samba setup, and how you have your user permissions setup.

There is a great HOWTO in tips and tutorials on setting up samba with Ubuntu and Windows

[http://ubuntuforums.org/showthread.php?t=202605&highlight=setting+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=setting+samba)

Take a look at that.

---

### Post by smergs on 2008-08-13
Thanks Riffer.  I'll take a look at it.

---

