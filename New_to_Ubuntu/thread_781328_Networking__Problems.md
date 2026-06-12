---
title: "Networking  Problems"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by kurt295 on 2008-05-04
Okay, so I've installed Ubuntu 8.04 Hardy Heron. Great right? Now all I need to do is network my WinXP box to my Linux box so I can tranfer my WinXP files over and Burn them at will. Right now, if I go into:

Places > Network > MSHOME > computername 

It gives me 3 options. C, Print$, and SharedDocs. But every time I try to open one of the folders it says, "Unable to mount location Failed to Mount Windows share."

I've already tried installing SAMBA through the Add/Remove applet but it crashes everytime I try to run it with an error that says:

"Warning: Some lines couldn't be understood while reading the configuration file /etc/samba/smb.conf. These may be unknown configuration directives for Samba plugins but could also be configuration errors.

49:  enable spoolss = yes    

So I'm at kind of a loss on what to do. I've only been using Linux for about ...... 19 hours and while I love it, it's really confusing.

---

### Post by superprash2003 on 2008-05-04
try smb://(computer name or ip)

---

### Post by kurt295 on 2008-05-04
I don't really know what that means, or where I'd be typing it or looking for it >_<  This is the very first time I've tried to do anything technical with Linux. My other time was spent customising the desktop and Opera. #-o

---

### Post by drsox1899 on 2008-05-04
Try this easy HowTo.  Works well.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

Luck

PS Having a static IP address is not needed, but ensure that you tell the system that you don't.

See in the HowTo :

"    ....    -> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS.   ....  "

---

### Post by kurt295 on 2008-05-04
Ok, thanks a lot. It seems to be working now. I'm porting over about 30Gbs of info now. :guitar: Sweetness ^_^ But what happens when I'm ready to format my WinXP box? After a reinstallation of Windows, I know I'll have to reset the Sharing system on there, but will I have to remodify the Samba config file to match whatever I happen to rename the workgroup .etc? Also, if I do have to modify it, will I have to stop SAMBA and restart it after the modifications to the config file have been made?

---

### Post by drsox1899 on 2008-05-04
> **kurt295 said:**
> Ok, thanks a lot. It seems to be working now. I'm porting over about 30Gbs of info now. :guitar: Sweetness ^_^ But what happens when I'm ready to format my WinXP box? After a reinstallation of Windows, I know I'll have to reset the Sharing system on there, but will I have to remodify the Samba config file to match whatever I happen to rename the workgroup .etc? Also, if I do have to modify it, will I have to stop SAMBA and restart it after the modifications to the config file have been made?

No need to rename the workgroup unless you want to.

Yes and yes if you do.

---

