---
title: "Need help with WD MYCLOUD drive."
date: 2015-03-27
forum: New to Ubuntu
---

### Post by bcavotta on 2015-03-27
Hello, I'm using an ACER Aspire 5100 with ubuntu 14.04 installed. I recently installed a WD Mycloud on our home network. I installed the Mycloud software on the laptop using wine and everything seems to be working fine with one exception. I cannot upload any files from the laptop to the Mycloud. When I try to upload files it begins the process and stops stating that problems were found, but no info on what the problem was. I have windows machines and mobile devices that can upload to the Mycloud fine. I'm sure this is a newbie issue and any help is greatly appreciated.

Bill

---

### Post by pfeiffep on 2015-03-27
> **bcavotta said:**
> Hello, I'm using an ACER Aspire 5100 with ubuntu 14.04 installed. I recently installed a WD Mycloud on our home network. I installed the Mycloud software on the laptop using wine and everything seems to be working fine with one exception. I cannot upload any files from the laptop to the Mycloud. When I try to upload files it begins the process and stops stating that problems were found, but no info on what the problem was. I have windows machines and mobile devices that can upload to the Mycloud fine. I'm sure this is a newbie issue and any help is greatly appreciated.

BillI have a WD My Cloud and found that it easily can be accessed using Ubuntu.    Here are the steps I used when installing mine which was purchased for a single point backup for household:
 
[LIST]
[*]installed     10/100/1000 switch to connect computers and My Cloud directly 
[*]disabled UPnP     on my router 
[*]upgraded My     Cloud firmware (I think this is actually a Debian kernel) 
[*]ignored all WD     suggestions for installing their software 
[*]used Firefox on     Ubuntu to access and configure my device 
[/LIST]
[INDENT=2]        probably 192.168.1.XX where XX is your router supplied ip
[/INDENT]

[LIST]
[*]disabled cloud     access 
[*]set up my     userid password 
[*]rebooted my     device 
[*]used nautilus     to find my device (I named my kincaidpeters) 
[*]created     nautilus bookmarks to shares found 
[*]tested drag and     drop method to copy / move files 
[*]set up ubuntu     backup to target kincaidpeters 
[/LIST]
[INDENT=2]Server            kincaidpeters[/INDENT]
[INDENT=2]Storage     Location    Windows Share
[/INDENT]
[INDENT=2]Folder            /my_book_1144_2/hp_ub_backup
[/INDENT]
 
[LIST]
[*]setup Mac Book     Pro Timemachine to use kincaidpeters as backup device 
[*]installed and     configured WD Smartware on Windows 7 and tested 
[/LIST]
 
 I found little functionality offered in WD's suggested software for Windows; however I did finally install some of it to actually discover how I really didn't need it!
 
 _**Be aware that the time set in Dashboard is NOT reflected in the device's kernel. In my case the local time is EDT and the notifications are stamped in PDT**_

---

### Post by DuckHook on 2015-03-27
MyCloud has NFS support. It is usually better to use native Linux technology over Windows kludges, so if I were you, I would avoid Samba and connect all local Linux machines to your MyCloud with NFS.

Also, stick to the browser-based setup rather than the Windows app running in WINE. Apps in WINE are not very reliable, especially apps used for admin and config purposes.

Make sure NFS support is turned on in your MyCloud server. Then follow [these]("https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client") instructions to connect your Linux machines.

---

### Post by pfeiffep on 2015-03-28
> **DuckHook said:**
> MyCloud has NFS support. It is usually better to use native Linux technology over Windows kludges, so if I were you, I would avoid Samba and connect all local Linux machines to your MyCloud with NFS.

Also, stick to the browser-based setup rather than the Windows app running in WINE. Apps in WINE are not very reliable, especially apps used for admin and config purposes.

Make sure NFS support is turned on in your MyCloud server. Then follow [these]("https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client") instructions to connect your Linux machines. Enabling NFS on My Cloud requires SSH to also be enabled; by enabling SSH one's WD warranty is voided.

WD enables SMB and AFP by default so the product line is compatible with both Windows and Mac OSes. IMO it's probably best to use the product as designed. AFP on Ubuntu 14.04.2 is fully capable of accessing My Cloud. Additionally I had not problems using Backups (Deja dup) to the default Windows share on My Cloud.

---

### Post by DuckHook on 2015-03-28
> **pfeiffep said:**
> ...enabling SSH one's WD warranty is voided.I automatically enable SSH on all my devices whenever I can, but had forgotten that it voids the warranty. Thanks for the reminder.> ...it's probably best to use the product as designed.+1 for new users.

I feel compelled to hack any original piece of kit and make it do more than intended, but that's just me. For people who just want it to work, you are right&#8213;best to leave well enough alone.

---

### Post by pfeiffep on 2015-03-28
> **DuckHook said:**
> I automatically enable SSH on all my devices whenever I can, but had forgotten that it voids the warranty. Thanks for the reminder.+1 for new users.

I feel compelled to hack any original piece of kit and make it do more than intended, but that's just me. For people who just want it to work, you are right&#8213;best to leave well enough alone.I'm certainly not inhibited by SSH, but I am somewhat inhibited by a new to me product and voiding a warranty. I generally use your [COLOR=#800080]*"hack any original piece of kit and make it do more than intended"*[/COLOR] by extending the life of older equipment - for instance my Dell Laptop from the XP boneyard is still running just fine on Ubuntu 14.04 32 bit albeit I installed gnome flashback because 3d was WAY too much for the dinosaur;)

Since I purchased WD refurbished it came with only a 6 month warranty so I'll probably try SSH and enabling NFS. 

BTW is NFS that far superior to AFP or SMB?

---

### Post by DuckHook on 2015-03-28
> **pfeiffep said:**
> ...is NFS that far superior to AFP or SMB?Good question. If you read the forums and Google around, you find tons of anecdotal experiences and little by way of reliable stats. Moreover, network file system performance is very dependant on fine tuning. A well-tuned SMB share will be much faster than a poorly-tuned NFS and vice versa. However, NFS is a leaner protocol, and for that reason, on really lean installations&#8213;for example, those running minimal installs on *my* dinosaurs&#8213;it's the only network file system that I have. So, I leave myself no choice but to activate it on my NAS appliances. I've also learned how to tune my clients to maximize NFS throughput on my network, but each network is unique and I'll be the first to admit that my settings won't be of much use to others.

In my case, since I stopped running any Windows boxes at all years ago, SMB is superfluous. Haven't touched it for years. This means that I'm just more familiar and comfortable with NFS than anything else, so my preference is also very subjective.

Attempting to be at least somewhat objective, here are what I think are the pros and cons:

Pros:
1. Native permissioning and ownership functionality. It's Linux. I don't have to install or configure kludges to make it coexist with the remote file structure.
2. I can tune the thing by simply adding parameters when I invoke it.
3. My experience is that it's really fast. I could never get my SMB throughput to match my NFS (back in the day when I still played with SMB).
4. Proven stability and fault tolerance. I've never lost a file over NFS. Lost a fair share of files using SMB. But this was years ago and I may not have known how to configure SMB reliably.

Cons:
1. It's not secure. Everything is transmitted unencrypted in the clear, so it has to be used behind a firewall that you have absolute confidence in, and in a network environment that you completely trust.
2. It suffers from the usual Command Line obscurity that intimidates new users. Not a lot of graphical tools exist to administer it and the few that exist are dated, of limited functionality and not very good.
3. Not a champ when it must be scaled, clustered or otherwise dressed up and made over.

BTW, CIFS has largely replaced SMB, although many of us old-timers still use SMB when we really mean CIFS. I take it that you are referring to CIFS as well. I have absolutely no knowledge of AFP, nor do I trust Apple on anything infrastructure-related, so I can't comment there.

---

### Post by pfeiffep on 2015-03-28
Thanks DuckHook for your synopsis! I'm not entirely certain about CIFS or SMB ... I do know that I can connect to the server with either smb:// or afp:// and nfs is denied.  I need to do some more research on CIFS to throw out some of my ignorance and replace it with knowledge.

---

### Post by DuckHook on 2015-03-28
> **pfeiffep said:**
> ...I can connect to the server with either smb:// or afp:// and nfs is denied.You were quite right in your initial observation that NFS requires you to dig into the OS through ssh.> ...more research on CIFS...[This]("http://unix.stackexchange.com/questions/34742/cifs-vs-samba-what-are-the-differences") might help.

---

### Post by bab1 on 2015-03-28
> **DuckHook said:**
> [This]("http://unix.stackexchange.com/questions/34742/cifs-vs-samba-what-are-the-differences") might help.

That information is very out of date.  

The keeper of the protocol is Microsoft and they have gone from naming it SMB to CIFS and back to SMB with SMB3.  

Here is the latest Samba take on the state of [SMB/CIFS/SMB2/SMB3]("https://wiki.samba.org/index.php/Samba3/SMB2")

Edit:  Here is more from Wikipedia on [SMB/CIFS/et all]("http://en.wikipedia.org/wiki/Server_Message_Block")

---

### Post by DuckHook on 2015-03-29
> **bab1 said:**
> That information is very out of date.Thanks for update and correction. Tells you how long it's been since I've had anything to do with it.

---

### Post by bab1 on 2015-03-29
> **DuckHook said:**
> Thanks for update and correction. Tells you how long it's been since I've had anything to do with it.

And it is changing pretty fast right now.  I don't need Samba for enterprise so I haven't followed the developments like I used to.  

One interesting development is that you can't use a SambaV4 install for both AD - DC (users and group management) and file sharing.  You need to have either 2 hosts or a host with a VM for file sharing.  The *samba* daemon doesn't play well with *smbd* and *nmbd*.

---

### Post by pfeiffep on 2015-03-29
> **bab1 said:**
> That information is very out of date.  

The keeper of the protocol is Microsoft and they have gone from naming it SMB to CIFS and back to SMB with SMB3.  

Here is the latest Samba take on the state of [SMB/CIFS/SMB2/SMB3]("https://wiki.samba.org/index.php/Samba3/SMB2")

Edit:  Here is more from Wikipedia on [SMB/CIFS/et all]("http://en.wikipedia.org/wiki/Server_Message_Block")Thank you for the update 
Sooooo ... for the home user who:
[LIST]
[*]doesn't enable "cloud access" 
[*]has control of physical access to networked devices 
[*]is primarily using WD My Cloud as backup solution 
[/LIST]
It makes little or no difference which protocol is used from a functionality perspective. 
If DNLA, iTunes, and other media streaming start to get bogged down then one might look at the different methods.

---

### Post by DuckHook on 2015-03-29
> **pfeiffep said:**
> Thank you for the update 
Sooooo ... for the home user who:
[LIST]
[*]doesn't enable "cloud access" 
[*]has control of physical access to networked devices 
[*]is primarily using WD My Cloud as backup solution 
[/LIST]
It makes little or no difference which protocol is used from a functionality perspective. 
If DNLA, iTunes, and other media streaming start to get bogged down then one might look at the different methods.From a bare functionality perspective, I'd say you have summarized it quite accurately.

Scratch the surface and a whole host of issues come up: issues like security, simplicity of maintenance, efficiency, throughput, etc. But since we've hijacked the thread from the OP already, I won't get any further into them here. For most users, I'd say that you've pretty much summed it up.

---

