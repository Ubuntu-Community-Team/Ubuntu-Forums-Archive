---
title: "[SOLVED] Networking my two home pc's"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by RoyHobbs on 2008-08-25
Hi

Dumb question time, but how do I network my two pcs and printer?  I have one pc connected to my (wireless) router with an ethernet card and I have the printer connected to this pc via usb cable.  My second pc is connected to the router via a wireless usb stick.  Internet connection on both is fine, however I can't "see" either pc?  Any advice would be appreciated.  Thanks

---

### Post by wolfen69 on 2008-08-25
first, go to synaptic and make sure you have samba, samba client, nfs server, and nautilus share installed.

---

### Post by Threbus5 on 2008-08-25
Well, before adding application or services, could you please provide some detail? For example what operating systems are the PCs using? Both Windows (let us hope not), both Ubuntu Linux, or a mixture?

A mixed network will succeed with Samba sharing.
Two Ubuntu machines have other options.

As far as being able to see either PC from the other, that requires making sure that they are on the same Workgroup. Sometimes just sharing the same gateway (which may be how your network interface [probably router] is configured - as the default gateway) may be insufficient.

You might want to try the suggestions from here: [http://ubuntuforums.org/showthread.php?t=897326&highlight=howto+network](http://ubuntuforums.org/showthread.php?t=897326&highlight=howto+network)

Good luck.

---

### Post by RoyHobbs on 2008-08-25
> **Threbus5 said:**
> Well, before adding application or services, could you please provide some detail? For example what operating systems are the PCs using? Both Windows (let us hope not), both Ubuntu Linux, or a mixture?

A mixed network will succeed with Samba sharing.
Two Ubuntu machines have other options.

As far as being able to see either PC from the other, that requires making sure that they are on the same Workgroup. Sometimes just sharing the same gateway (which may be how your network interface [probably router] is configured - as the default gateway) may be insufficient.

You might want to try the suggestions from here: [http://ubuntuforums.org/showthread.php?t=897326&highlight=howto+network](http://ubuntuforums.org/showthread.php?t=897326&highlight=howto+network)

Good luck.

Hi, both are dual boot.  One is XP / Ubuntu (wireless), the other is Vista / Ubuntu (ethernet).  When I was describing not being able to see them, I was referring to when both are in Ubuntu 8.04.  Thanks

---

### Post by crispy_420 on 2008-08-25
What do you want to accomplish? File sharing or print, maybe both?

As far as file sharing and/or printing, you can't beat samba. NFS is good as well but will take a little more work.

---

### Post by RoyHobbs on 2008-08-26
> **wolfen69 said:**
> first, go to synaptic and make sure you have samba, samba client, nfs server, and nautilus share installed.

Thanks for your help, Samba has been fantastic, far easeir than windows!  My only problem now is that I have a external harddrive connected to the wireless pc that I cannont acces from the second pc.  I can see the external drive from the other pc, I just can't access it (failed to mount Windows Share?).  I haven't had any problems with the external drive before.

---

### Post by RoyHobbs on 2008-08-27
Bump

---

### Post by RoyHobbs on 2008-08-27
Any help on the "failed to mount Windows Share" error would be greatly appreciated

---

### Post by crispy_420 on 2008-08-28
When you have the external connected to the PC, are you using Windows or Linux?

---

### Post by RoyHobbs on 2008-08-28
> **crispy_420 said:**
> When you have the external connected to the PC, are you using Windows or Linux?

Linux - Ubuntu 8.04

---

### Post by wdaniels on 2008-08-28
Note that while you can certainly use Samba to network two Linux machines, this is basically an open-source implementation of the various Microsoft networking services, and is better reserved for compatibility with Windows machines IMHO.

A simple way to get Ubuntu to show other machines on your network in the file browser, without Samba, is to use avahi services (avahi is an open-source ZeroConf). Nautilus should recognise sFTP services advertised by avahi under the Network bookmark the same way as it does when using Samba if you do the following (on each machine):

```
sudo cp /usr/share/doc/avahi-daemon/examples/ssh.service /etc/avahi/services
cat /etc/avahi/services/ssh.service | sed 's/ssh/sftp-ssh/' | sudo tee /etc/avahi/services/sftp.service
sudo /etc/init.d/avahi-daemon restart
```

All this does is tells avahi to advertise two services on the machine; sFTP and SSH. Note that you can also use avahi to resolve IP addresses (instead of winbind in Samba) by using the host name with a ".local" domain suffix (e.g. myotherpc.local) and this is enabled in Ubuntu by default.

---

### Post by leezx10 on 2008-08-30
Seem like you have the same problem I had a while ago, was your external hard drive connected to a windows box. If so the problem is with NTFS.

Ubuntu will not let you plug an external hard drive directly to it's USB ports without it being properly terminated from NTFS. What you have to do is plug it back in to Windows, right click and do a safe removal of the external hard drive from Windows then plug it into Ubuntu's USB ports.

Hope that helped...

---

### Post by RoyHobbs on 2008-09-03
> **leezx10 said:**
> Seem like you have the same problem I had a while ago, was your external hard drive connected to a windows box. If so the problem is with NTFS.

Ubuntu will not let you plug an external hard drive directly to it's USB ports without it being properly terminated from NTFS. What you have to do is plug it back in to Windows, right click and do a safe removal of the external hard drive from Windows then plug it into Ubuntu's USB ports.

Hope that helped...

Hi

I got Samba working (I think), however now I only have one PC that I can view.  When I click on it I get an error - UNABLE TO MOUNT LOCATION Connection refused by server.  I am getting really lost here!

---

### Post by RoyHobbs on 2008-09-03
bump

---

### Post by redbob on 2008-09-03
If you wanna open ubuntu smaba hosts, it's a good idea to install at least a samba user[QUOTE]sudo smbpasswd -a <username>/QUOTE]

---

### Post by RoyHobbs on 2008-09-17
Hi

I have Samaba working (sporadically) however when I try to access the external drive connected by wireless network to my second pc I get a pop up screen asking me for a username, domain and password.  I have not set up any passwords or users on this drive as it is set up the same as the harddrive on the pc it is connected to.  When I cancel out of this pop up I get the error "Unable to Mount Location.  Failed to mount Windows Share"

Any advice???

TIA

---

### Post by TVAbuntu on 2008-09-17
I set up a similar network, but used ssh. Pretty easy. Just "connect to server" in "places". Can see dual boot files via NTFS shares.

This did lead me to wonder, am I opening a security hole by doing this. I am behind a NAT router and ShieldsUp says I'm fully "stealthed", but can I still be brute force hacked on port 22?

---

### Post by RoyHobbs on 2008-09-17
> **TVAbuntu said:**
> I set up a similar network, but used ssh. Pretty easy. Just "connect to server" in "places". Can see dual boot files via NTFS shares.

This did lead me to wonder, am I opening a security hole by doing this. I am behind a NAT router and ShieldsUp says I'm fully "stealthed", but can I still be brute force hacked on port 22?

What is the best way to install this?  Please keep in mind, I am a NEWBIE!  Thanks :)

---

### Post by TVAbuntu on 2008-09-18
go to "places"
find "connect to server" This opens a dialogue box. You can then pick ssh. All you need is the IP address of the computer you want to connect to. You can find this by looking in network manager or running "ifconfig" in terminal (in the computer to be connected). It should then prompt you for your login name and password.
If this doesn't work you may have to make sure that both client and server ssh are installed (can be done via synaptic). There are a number of more detailed guides posted that are easy to google (here is a useful link [http://www.linux.com/feature/119744](http://www.linux.com/feature/119744)). I'm no expert here either, so I have confidence that if I can do it, you can too (hardware allowing)

---

### Post by RoyHobbs on 2008-09-19
> **TVAbuntu said:**
> go to "places"
find "connect to server" This opens a dialogue box. You can then pick ssh. All you need is the IP address of the computer you want to connect to. You can find this by looking in network manager or running "ifconfig" in terminal (in the computer to be connected). It should then prompt you for your login name and password.
If this doesn't work you may have to make sure that both client and server ssh are installed (can be done via synaptic). There are a number of more detailed guides posted that are easy to google (here is a useful link [http://www.linux.com/feature/119744](http://www.linux.com/feature/119744)). I'm no expert here either, so I have confidence that if I can do it, you can too (hardware allowing)

THANKYOU THANKYOU THANKYOU!!!  This seems (touch wood) to be working fine, if not a bit slowly?

---

### Post by wdaniels on 2008-09-21
> **TVAbuntu said:**
> I am behind a NAT router and ShieldsUp says I'm fully "stealthed", but can I still be brute force hacked on port 22?

No, not unless your router is configured to forward port 22 to one of the machines within your private network, which should not happen under any normal default configuration.

---

