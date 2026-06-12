---
title: "Can't see Ubuntu shares from WinXP"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by TerryP on 2008-11-08
Hi,

I installed samba and can access windows xp shared files from Ubuntu, but the Ubuntu shared folders don't appear in Windows although I can see the Ubuntu PC itself under WORKGROUP.  Any help would be appreaciated.

---

### Post by medic2000 on 2008-11-08
Hmm you have to configure samba for this. Please look or search the Tutorials-Tips sections. There are guides for Samba.

---

### Post by chrisod on 2008-11-08
What is the file system on the share? If it's ext2 or 3 I don't think Windows will be able to read it. There are freeware apps for Windows available that will enable you to access data on ext2 or 3 from Windows. I don't remember the exact names, I'm sure Google will turn them up if you look.

---

### Post by TerryP on 2008-11-08
The file system on the XP Laptop is NTFS, the Ubuntu laptop is using ext3.  These are two laptops, one with Ubuntu Hardy 8.04, the other with WinXP Home.  Like I said, the Ubuntu laptop shows up in Windows, but I don't see any folders.  I enabled sharing on the Ubuntu Laptop for several folders in the home directory.  I can access all the shared folder/files on the XP laptop from Ubuntu, but can't access anything from the XP laptop.

I've used several tutorials to setup file sharing already.  It must be something simple.  I just haven't figured it out yet.

---

### Post by foxmulder881 on 2008-11-09
I'm having a very similar issue myself and can't for the life of me figure out what the heck is causing it.

I originally posted this is another forums but thought it would be worth posting here too.

Original post reads...
> This has been driving me crazy all evening and I'm at my wits end with my flatmates XP laptop being stubborn.

I can see my linux system on the network (both systems are on workgroup MSHOME) and my shared directory called share_dir. I can't see hers on the network.

And on her laptop, I can't see my machine either, only her own shared folder.

There seems to be a connection problem somewhere that's preventing the machines from seeing each other. I can't ping her machine either.

What could possibly be the cause? 

---

### Post by TerryP on 2008-11-09
Foxmulder, your issue sounds similar to mine; however, I can ping from either laptop successfully (XP to Ubuntu and vice versa).  I just don't see any shares from the XP machine although I can see the Ubuntu laptop listed within WORKGROUP. :confused:

---

### Post by _sAm_ on 2008-11-09
Just an suggestion: 

My father could not see my samba shares from his XP, but thanks to google I did find the two problems. 

1. NetBIOS Over TCP/IP was turned of on XP. Guide to turn on here; [http://www.practicallynetworked.com/sharing/troubleshoot/netbt.htm](http://www.practicallynetworked.com/sharing/troubleshoot/netbt.htm)

2. His firewall(Zonealarm) blocked it without telling him about it, when I turned it off the shares worked fine.

If that dos not help you I would check samba. On Ubuntu running Samba you can run a command to see what other pc on the LAN(that work) should see when browsing the server:
smbclient -L [hostname for XP pc] -U% -[samba username]

---

### Post by TerryP on 2008-11-09
sAm,

Thanks for your response.  However:

After I enabled NetBIOS Over TCP/IP on XP, ALL shares disappeared except for those on the host PC but came back after a few minutes.

The firewall has been turned off the whole time on the XP machine.

When using the smbclient commands I get the following error if I enter the XP machine host name - Error NT_STATUS_BAD_NETWORK_NAME.

At this point, nothing changed

Thanks

---

### Post by Iowan on 2008-11-09
Will it work if you use IP address instead of hostname?

---

### Post by TerryP on 2008-11-09
No, doesn't work.  I have attached the error message.

---

### Post by _sAm_ on 2008-11-10
Are you sure if your path to the shares are correct in the Samba settings?

---

### Post by jonandrews on 2008-11-10
I've put a series of simple step-by-step guides about networking and printing between Ubuntu & Windows pc's on a website:

[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

By the way, the file systems used on the PC's is definitely irrelevant to networking between them. All writing to a disk is controlled only by the operating system of the pc in which the disk is installed.

---

### Post by Efros on 2008-11-10
You could try using webmin, it has a section that alows you to interactively configure samba shares, very easy to use.

[http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html](http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html)

---

### Post by TerryP on 2008-11-10
I did some more troubleshooting:

My third laptop running crunchbang linux can ping the Ubuntu laptop at 50% loss and the XP laptop with 0% packet loss.  

At the XP laptop I can ping the crunchbang machine with 0% loss and the Ubuntu machine with 25-50% packet loss.  

At the Ubuntu machine I can ping the crunchbang with 0% loss and the XP machine with 50% packet loss.


I've had a lot of trouble with wireless drivers for the NIC on the Ubuntu machine (Broadcom BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)) and recently installed the Broadcom STA drivers using Synaptic.  I was using the Broadcom drivers and NDISWrapper, but these drivers were flakey

Anyway, I'm using wireless on all the laptops connected through a wireless router.  All the laptop connections to the internet work.  Could this problem be related to the NIC?

BTW, I followed jonandrews how to and it didn't work. On Efros's suggestion I downloaded/installed webmin 1.43 and it has goobs of options.  Very well organized app but it will take awhile for me to figure it all out.

---

### Post by TerryP on 2008-11-10
Wow!  I'm really impressed with Webmin.  Still haven't fixed the problem yet though.

---

### Post by Coreigh on 2008-11-10
I have had some hair pulling experiences with shared folders on XP, especially when XP is fully updated. It seems that XP security locks down shared folders pretty tight. You need to make sure the everybody permissions are enabled on the XP side in BOTH the file permissions AND the share permissions. Right-click the shared folder and look at security and check that everyone has read/write permission. Then the Shares tab and permissions button and make sure that everybody has read/write permission. These settings and properties may be obscured or hidden especially in the Home version of XP. You'll have to google for how-to's on enabling them.

---

### Post by TerryP on 2008-11-10
I installed the MS Security Tool and it now displays the security tab for folders.  Permissions were already enabled though.

---

### Post by foxmulder881 on 2008-11-10
Sorry that you fellas are still having issues. But I figured out why mine wasn't working at least. My flatmate connects to another router in her bedroom. So essentially we're running a network with 2 routers (and a switch) resulting in the nasty that is double NAT.

---

### Post by TerryP on 2008-11-11
foxmulder,

Wish my problems were as simple.  I think I'll try editing the smb.conf file next, after saving the original of course.

---

