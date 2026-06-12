---
title: "Connect to server"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by ebonweaver on 2012-12-08
Ok going to try this from the absolute beginner standpoint and hope for the best.  I'll use the most similar platform as a comparison point for the issue.

On a stand alone Mac, if I want to connect to a particular server, I do Finder -> Go -> Connect to Server, and for the address put in smb://server.domain.com/Shares.  I am challenged for my name and password which I put in plainly, and it mounts the share names Shares and I see all the folder I have access to inside.

On Ubuntu 12.0.4 LTS I click the taskbar item to open my Home to activate the file manager menu, and do File -> Connect to Server.  I am presented a window with a lot more options for the connection that on the Mac.  Given the above example from the Mac, what do I put in the various fields to connect to the share?

---

### Post by steeldriver on 2012-12-08
Since it is smb/SAMBA/cifs you can select 'Windows Share' from the dropdown, then enter

Server: server.domain.com
Share: Share
Directory: /

(unless you want to open straight to a subdirectory on the share) and enter your remote username and password. I would leave the domain blank unless you log on with a domain\server combination on the remote host. The port option will be grayed out once you select Windows Share.

Alternatively you can use **Go --> Location**... instead of File --> Connect to Server, which will give you an interface much more like the MAC one you describe

---

### Post by ebonweaver on 2012-12-10
Thanks for the reply, unfortunately none of this works.

Using the Connect to Server method, it displays an alert at the top of the dialogue "Please verify your user details".  If I put in the Domain name, I get "Failed to mount Windows share"

If I use the Go -> Location method and put in the address as I would on the Mac, I get an error window: 
Could not display "smb://server.domain.com/shares/"
Error: Failed to mount Windows share
Please select another viewer and try again.

So far it seemed Ubuntu can't auth to a Windows share properly for some reason.  However, on an interesting side note, there was a Win 7 system on the same subnet that had a share on it, and I COULD connect to that with my domain credentials as expected when going through the Network browser.  That then seems to indicate Ubuntu can only connect to a Windows 7 share not a Win 2008 share, or it can't auth across subnets for some reason, or it can only connect properly when browsing as oppose to using an smb:// path.

Any thoughts what is going on here and how to resolve it?

---

### Post by ebonweaver on 2012-12-10
Solved the issue.  There are two bugs in Ubuntu 12 you have to be aware of when connecting to a server:

1. You MUST uppercase the domain name when connecting to a Windows server otherwise it fails to use all auth type properly.

2. You MUST use the IP or aname as cnames do not resolve properly.

If you account for those, everything works as expected.  When using a lower case domain name and server cname as you do on any other OS, it will fail.

---

