---
title: "Problem with Samba instruction"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by PeteClimbs on 2011-11-26
I installed ubuntu 11.10 and then samba 4.0, including system-config-samba.  The instructions then say to "open GUI samba server configuration by going to System-->Administration-->Samba".  I do not have an Administration icon in the System "folder".  How do I invoke the samba server configuration application?

The instructions are at [http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-)

TIA
Pete

---

### Post by bluexrider on 2011-11-26
Did you install SWAT also. Its the administration tool.

---

### Post by PunkLV on 2011-11-26
Have you tried ALT+F2 gksudo system-config-samba ?

---

### Post by PeteClimbs on 2011-11-27
[SIZE=3]With Alt+F2 I get prompted for my password, then nothing.  When I type the command in a terminal window, I get (among other things) "ImportError: No module named glade".  Do I need to install glade?
[/SIZE]
BTW, I tried to install SWAT and it gave me:
"ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it"
I removed /etc/samba/smb.conf and tried to install SWAT again.  Same error.

---

### Post by Morbius1 on 2011-11-27
> I installed ubuntu 11.10 and then samba 4.0,....Just out of curiosity did you install Samba4 out of the sheer joy and exhilaration of using alpha level experimental software. From Synaptic:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production.


---

### Post by PunkLV on 2011-11-27
Not to be a jerk, but it is amazingly easier just to write your own smb.conf in case you intend to share files/printers at home. And using samba3, which is stable and everything.

See /etc/samba/smb.conf
Way below there will be some examples for typical home-netwok filesharing. Read the comments, uncomment/edit what you see fit and run sudo service samba restart

---

### Post by Morbius1 on 2011-11-28
It's even more "amazingly easier" to open Nautilus, right click on a file you own, select "Sharing Options", select 2 or 3 options, and then hit "create share" ;)

It even avoids the Samba3 - Samba4 problem. If you don't have Samba installed when you select "Sharing Options", it automatically prompts you if you want to install it and then does so with the "correct" version of Samba.

---

### Post by Paqman on 2011-11-28
PeteClimbs: What is it you're actually trying to achieve by installing Samba? You'd normally only need to install the whole of Samba if you wanted to set your machine up as a Samba server, which would be a bit unusual for a desktop machine. Let us know what you're trying to do as it's likely the solution is much simpler than what you're trying to do.

---

### Post by Morbius1 on 2011-11-28
> **Paqman said:**
> PeteClimbs: What is it you're actually trying to achieve by installing Samba? You'd normally only need to install the whole of Samba if you wanted to set your machine up as a Samba server, which would be a bit unusual for a desktop machine. 
Your use of the phrase "Samba server" in the context of the sentence you wrote it in implies an enterprise level file and print server with a thousand seats all running Windows clients.

If bob wants to share a folder with edna he will have to install Samba. Well, he's not limited to Samba of course but whatever he may choose ( ssh, nfs, ... ) he will have to install and configure a "server".

---

### Post by Paqman on 2011-11-28
> **Morbius1 said:**
> 
If bob wants to share a folder with edna he will have to install Samba. Well, he's not limited to Samba of course but whatever he may choose ( ssh, nfs, ... ) he will have to install and configure a "server".

My point is that Ubuntu includes enough of the Samba client packages by default that you can connect to a Windows share. Likewise sharing your own folders doesn't require installing the whole of Samba. Since it's a bit unlikely that PeteClimbs really does need to be installing Samba, it would be useful to find out what he's trying to achieve.

---

### Post by Morbius1 on 2011-11-28
> Likewise sharing your own folders doesn't require installing the whole of Samba
That statement is incorrect but in the interest of clarity please explain what parts of samba he does not need to install.

---

### Post by Paqman on 2011-11-28
> **Morbius1 said:**
> That statement is incorrect but in the interest of clarity please explain what parts of samba he does not need to install.

Look, let's wait for him to get back and tell us what he actually needs. He may not need Samba at all (ie: SSH, NFS, etc), or the client packages that are already installed might be enough. There's no point in us discussing Samba in depth if it's no use to the OP.

---

### Post by Morbius1 on 2011-11-28
Well, he's installed Samba ( the wrong version but ... ), he installed system-config-samba to managed Samba, and he referenced a HowTo on the care and feeding of a Samba server so I just assumed he was trying to to use Samba to share folders on his system to someone else on his network.

But you're right let's see if he gets back to us with what he's attempting to do.

---

