---
title: "Ubuntu Server not showing up in Windows Network Explorer"
date: 2018-06-11
forum: New to Ubuntu
---

### Post by farmall.dude on 2018-06-11
Greetings!
New to Ubuntu, not new to computing or networking. I decided to take a whack at running an Ubuntu 16.04LTS server. Installed Samba, et. al., created folders, shares and added content. The first few times I fired it up, everything was great (well, after some trial and error that is). I opened Windows Explorer and there were my shared folders on my Ubuntu Server. All was well until... I'm not sure what happened. I suspect a Windows Update. I'm running Windows 10 Pro, Build 1803 for X64. I have taken the latest security updates and cumulative updates. So, all of a sudden my Ubuntu server (called media-server) is not showing up in Windows Explorer or Network Explorer. Every other stupid network device I have is, but not the server. I can navigate to it by \\media-server and the expected folders and files pop right up. I know therefore, there is a valid path to the server and the network is configured correctly. It's in the right workgroup, network, subnet, etc. When I close Network Explorer or Windows Explorer and re-open, the server is gone again. I have to navigate back to it by entering \\media-server. I have also taken the latest update and upgrade (again today) for Ubuntu. Is there something I can do to keep its persistence on my Windows machines? A setting in the smb.conf file I'm missing maybe?
I'm sure you'll need more info, just not sure what. Instead of posting every config I have on the server, I'll wait for a request for specific info.
Thanks in advance,
Bruce  

By the way, I tried searching but didn't have any luck finding what I was looking for.

---

### Post by Morbius1 on 2018-06-11
I'm getting old and feeble minded so I don't remember if a recent Windows update disabled it or if I did it myself but is the SMB1 client disabled on your Win10 machine? I'm not talking about the SMB1 server component I'm talking about the client component.

Go to Control Panel > Programs > Programs and features > Turn Windows features on and off > SMB 1.0/CIFS File Sharing > SMB 1.0 / CIFS Client.

No smb1 no netbios discovery. It doesn't affect name resolution so you will be able to access the machine by name explicitly but browsing by name is gone.

If it has been disabled it's up to you if you want to enable it.

[COLOR=#0000cd]**EDIT**[/COLOR]: Found this little gem: [https://support.microsoft.com/en-us/help/4034314/smbv1-is-not-installed-by-default-in-windows](https://support.microsoft.com/en-us/help/4034314/smbv1-is-not-installed-by-default-in-windows)
> In-place upgrades and Insider flights of Windows 10 Home and Windows 10  Professional do not automatically remove SMB1 initially. If the SMBv1  client or server is not used for 15 days in total (excluding the time  during which the computer is off), they each automatically uninstall  themselves. 
*That sort of thing preys on the old and feeble minded.*

---

### Post by farmall.dude on 2018-06-11
That's Brilliant! Problem solved. Gotta love Microsoft. That was exactly what was wrong. Lot's of "undocumented features" in the Fall edition :(
Thanks Morbius1.

Cheers,
Bruce

---

