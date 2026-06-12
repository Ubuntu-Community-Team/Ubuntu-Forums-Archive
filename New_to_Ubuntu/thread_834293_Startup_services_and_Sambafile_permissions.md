---
title: "Startup services and Samba/file permissions"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-19
Hi everyone

I'm messing around with Xubuntu at the moment, setting up a small Samba/Netatalk server but I've got some questions about how these services are installed.

1) After I first installed Xubuntu, using Synaptic I chose to upgrade Samba, and a couple of smb related utils.
I also installed Netatalk and a few other packages (p7zip, archiver etc)

Where do I go in Xubuntu to edit what services are loaded on startup?
Is there a specific config file I need to edit to do this?
I want to add Samba and Netatalk to startup automatically.

2) Do these services get started up before or after the login screen?
Thanks to help on here, I've set Xubuntu to stop at the login prompt without the graphical login and loading xfce.
At that point are the services started up?
Or do I need to login on the machine to enable access to those sharing services?

3) I notice in Xubuntu xfce... Applications > System > Shared Folders
Is that just a GUI front-end to the Xubuntu Samba installation?
Can I edit the /etc/samba/smb.conf file manually without using that GUI?

4) We currently have the sharing set up in Win2000 so that anyone on our internal network can access the server without a username/password.
Is that all handled by the Samba and Netatalk configuration files?
Or is that down to the chmod/file permissions of the parent shared folders?
For this sort of sharing (guest/total access), is there a recommended chmod/owner for the shared folders?

5) When Windows and Mac users add/edit files on the shared folders, I don't want to get any permissions problems... so some users can access files but others can't.
Is there a way to prevent this happening?
Will permissions of files/folders be inherited from the parent shared folder?

Thanks in advance!
B

---

