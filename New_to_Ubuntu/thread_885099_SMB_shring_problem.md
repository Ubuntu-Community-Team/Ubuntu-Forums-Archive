---
title: "SMB shring problem"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by apotter303 on 2008-08-09
Hi-

I am having trouble modifying the smb.conf file to add a line so that I can share a folder to my xbox.
I am getting the error:
'net usershare' returned error 255: net usershare add: cannot share path /media/External 750/Music as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

I don't understand why i would not have permission to chang the smb.conf file.
It says the owner of smb.conf is root in the permissions.

Could this be because I installed ubuntu within widows?

Thanks

---

### Post by pi.boy.travis on 2008-08-09
When you say "within Windows," I assume you used Wubi to install?  Wubi is intended to sort of "try out" Ubuntu.  I personally have had many bad experiences with it, and it is still sort of "experimental."  It is best to install Ubuntu in it's own dedicated partition, especially when you need it to share files in the long term.

---

### Post by bpowell2005 on 2008-08-09
> **apotter303 said:**
> Hi-

I am having trouble modifying the smb.conf file to add a line so that I can share a folder to my xbox.
I am getting the error:
'net usershare' returned error 255: net usershare add: cannot share path /media/External 750/Music as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

I don't understand why i would not have permission to chang the smb.conf file.
It says the owner of smb.conf is root in the permissions.

Could this be because I installed ubuntu within widows?

Thanks

When you edit smb.conf, you'll have to use "sudo nano smb.conf" which will edit the file as root. What I've done (as I'm trying to avoid editing conf files) is I go to terminal and run "sudo nautilus" This brings up a file explorer with root permissions, then just find the disk you want to share, right-click it and select Share. It has worked for me on a standard Ubuntu installation, haven't tried it with Wubi.

---

### Post by mjpatey on 2008-08-09
I agree with bpowell... I've used "sudo nautilus" many times when I'm in a GUI kind of workflow and don't feel like going to a terminal to "sudo" my actions individually.  It gives you root permissions while in Ubuntu's file manager.  This will give you the permission you need to right-click the drive and select "share".

The only caveat:  when you're done, close that scary sudo-powered Nautilus window!  Especially if you have little kids.  ;-)

-Mark

---

### Post by aloshbennett on 2008-08-10
I guess you are able to edit the smb.conf file, but not share a folder within xBox.

Check the permissions of the folder you are trying to share? Do you have write access?
Also, I faced a similar problem trying to share a drive which had umask set to 007 (no read access to other users). It could be somethign similar in your case too.

---

