---
title: "[SOLVED] Network printing from Vista to Ubuntu box with printer"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by iconoclast hero on 2008-07-24
I've spent about an hour and a half looking through the forums and have not really gotten anywhere.  Is there a guide or FAQ on now to do this?  I saw Samba mentioned, but I couldn't even tell if I wanted the Samba server or just SMBFS.  I would like to be able to print from a machine running Vista to my box running Ubuntu 8.04.  I installed it yesterday and have no experience with Linux.  

I would also like to be able to access files on my Linux box via file-sharing.

---

### Post by Hospadar on 2008-07-24
Can't help you with the printer, although I'm 99% sure that some form of samba is how you will eventually (if ever) get it working, although here are some guides that might help:
[http://www.petersblog.org/node/726](http://www.petersblog.org/node/726)
[http://tldp.org/HOWTO/SMB-HOWTO-9.html](http://tldp.org/HOWTO/SMB-HOWTO-9.html)

As for your remote file access, you can use samba, but I prefer ssh.  all you have to do to set it up is "sudo apt-get install ssh" and you can remotely access your machine and get files all you want (with a client like filezilla, or from the command line)

---

### Post by LowSky on 2008-07-24
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by plucky on 2008-07-24
This link might help [Network Printing with Ubuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

You need to enable printer sharing on the Ubuntu machine by going to **System > Administration > Printing** and select **Server Settings** and make sure "Share published printers connected to this system" is ticked. 


Then follow the instructions in the link for windows printers.

Good Luck

---

### Post by o.besner on 2008-07-24
1) Open Synaptic Package Manager, install samba. Restart your computer. (I'm not joking about the restart -- it helps somehow.)

2) Go in System --> Administration --> Printing and check "Show Printers Shared by Other Systems" and "Share Published Printers Connected to this System" and Voilà !

---

### Post by The Cog on 2008-07-24
You don't need samba. plucky's link is the easiest way. 
Share printers in Ubuntu, then on XP/Vista, configure an address like:
[http://1.2.3.4:631/printers/PRINTER_NAME](http://1.2.3.4:631/printers/PRINTER_NAME)
Easy.

---

### Post by iconoclast hero on 2008-07-24
Ok, I got it working; both methods worked.  I have two perfectly ruined pieces of paper with "test page" on them to prove it!

I installed Samba and went to work on dinner (trying a new [recipe]("http://www.epicurious.com/recipes/food/views/BULGUR-VEGGIE-BURGERS-WITH-LIME-MAYONNAISE-242594"))...  I came back and to my surprise, I saw my linux box in vista's Network screen.  From there I just added the printer by selecting the linux box and then the printer.  (Windows didn't care for the driver that Ubuntu picked, but that is a different matter.)

I then stopped Samba (sudo /etc/init.d/samba stop) and tried the other way.  At first I didn't notice the server settings (possibly because I'm VNCing into my box upstairs from the vista pc on my porch).  I updated the checks and balances and then was able to print a test page using [http://192.168.1.7:631](http://192.168.1.7:631)...  

**However**, for some reason, even though I named the server Mustang-Linux and that is what it says under "Location" in System -> Administration -> Printing -> Local Printers -> HP_LaserJet_2100_Series, it will only work with the IP.  Also while I can ping the ip 192.168.1.7, I cannot ping mustang-linux...but that perhaps is a topic for a different post.

Anyway, thank you for the help and hope this thread helps someone else down the line...  The link plucky gave did not cover Hardy but I think that it is the same as for Gutsy.  I think I'm going to use the Samba method and figure out how to share files.  

----------------
Now playing: [Charlie Sexton & Shannon McNally -- Burn](http://www.foxytunes.com/artist/-/track/charlie+sexton+%26+shannon+mcnally+--+burn)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by The Cog on 2008-07-25
Glad you got it going.

The problem with the name Mustang-Linux sounds like a DNS problem. You either need to get the name Mustang-Linux registered on your WINS server, or add it to the file \windows\system32\drivers\etc\hosts (from memory - its somewhere like that).

---

### Post by bobpaul on 2008-11-29
> **The Cog said:**
> You don't need samba. plucky's link is the easiest way. 
Share printers in Ubuntu, then on XP/Vista, configure an address like:
[http://1.2.3.4:631/printers/PRINTER_NAME](http://1.2.3.4:631/printers/PRINTER_NAME)
Easy.

I've been using this method for WinXP clients for years, unfortunately this doesn't appear to work on Vista Home Premium. I see that Windows Services for Unix (or whatever they call it now) is only available on the Business editions and Ultimate, so maybe that has something to do with it?

Really irritating in that it worked fine via Samba up until a week ago when I did the upgrade from 8.04 to 8.10. Grr..

---

### Post by Cato2 on 2008-11-29
In order to make hostnames work properly, you might want to try installing winbind - see my mini HOWTO at [http://ubuntuforums.org/showpost.php?p=3653772&postcount=13](http://ubuntuforums.org/showpost.php?p=3653772&postcount=13)

---

