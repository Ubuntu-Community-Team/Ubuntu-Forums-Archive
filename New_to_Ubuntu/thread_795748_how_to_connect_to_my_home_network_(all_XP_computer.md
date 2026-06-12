---
title: "how to connect to my home network (all XP computers)"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by franky_88 on 2008-05-15
Hello everyone,


I just installed the new version of Ubuntu 8.04 on my HP pavillion dv 6568. Everything works fine, except this. I have a networked HDD with a lot of Tv shows that I want to watch, the only problem is when I go to Network I only see Windows network but not the other computers on my network. I can connect through the internet fine via a wired connection. I just don`t know how to connect to my network with all the other computers being windows XP.


Thank you for your help,


Franck

---

### Post by bswilson on 2008-05-15
> **franky_88 said:**
> I have a networked HDD with a lot of Tv shows that I want to watch, the only problem is when I go to Network I only see Windows network but not the other computers on my network.

What is a `networked HDD`?  Do you mean a hard drive that is installed in a networked Windows XP computer?  Also, do you have file and folder sharing enabled on these XP systems?  If not, you'll never see them from the Ubuntu system.

---

### Post by franky_88 on 2008-05-16
Yes it is a Hard drive on an XP computer. All the other computers have sharing enabled. I used to access them via Windows Vista but I just changed completly to Ubuntu 8.04.



Thank You,


Frank

---

### Post by housam on 2008-05-16
Install [COLOR="Red"]_samba_[/COLOR] from synaptic or from [[COLOR="Purple"]_here_[/COLOR]]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id341745")

---

### Post by Golem XIV on 2008-05-16
The process should go like this (please point out where does your problem appear):

From the main menu, open Places -> Network
(shows all detected networks)
Double-click on Windows Network
(shows all Windows domains/workgroups detected)
Double-click on the workgroup that you want to access
(shows all computers on that domain/workgroup)
Double-click on the computer you want to connect to
(shows all shared resources - folders, printers, etc.)

I am personally having problems with the last part, but I get around it by typing directly into the nautilus address bar **smb://computername/sharename** where **computername** is the name of the Windows system you want to access and **sharename** is the folder/printer name you want to access.

At this point, you should get the username/password prompt to access the Windows resource.

To make it simpler, you can create a launcher on your desktop ("Shortcut" in Windowspeak) to access the resource directly.

---

### Post by franky_88 on 2008-05-16
Okay so I installed Samba and now I can see my home network, but can`t access the other computers. I also have another network called MSHOME. I click it and it directs me to my laptop. I think that this my be due to the fact that I just switched from Vista to Ubuntu. Thank you all for your help, and I will post any progress in here. If I see the network that I want to connect do I need to configure smb.conf??


Thank you,


Frank

---

### Post by mrmoon31 on 2008-05-20
I have the same problem.

Recently upgraded from 7.10 to 8.04.


In Places->Network->Windows Network,
does not show workgroups at all.

Internet is working fine.

---

### Post by mapes12 on 2008-05-20
I couldn't get sharing to work at all across my home LAN therefore I gave up on network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

---

### Post by Iowan on 2008-05-20
On Gutsy, I have better luck with Places>"Connect to Server". Another question would be whether the Windows boxes have the firewall enabled.

---

### Post by lisati on 2008-05-20
> **franky_88 said:**
> Okay so I installed Samba and now I can see my home network, but can`t access the other computers. I also have another network called MSHOME. I click it and it directs me to my laptop. I think that this my be due to the fact that I just switched from Vista to Ubuntu. Thank you all for your help, and I will post any progress in here. If I see the network that I want to connect do I need to configure smb.conf??


Thank you,


Frank

MSHOME is WindowSpeak for a home network, and can have different names according to how your system is set up. It's one way that Windows organizes PCs into what it calls workgroups. XP on my laptop and my desktop identify themselves as part of MSHOME. My neighbour's laptop, which I allow to connect to the internet through my wireless setup, runs NT and identifies itself as being part of HOME instead of MSHOME. When my old WIN98SE machine was working, it grouped itself with MSHOME as well.

---

### Post by pistos on 2008-05-20
Try this... Install samba as suggested by others (I thought I read somewhere that samba is actually installed by default under 8.04, but whatever). Then, "share" a directory of yours on the Ubuntu computer. Verify that XP computers can see your Ubuntu computer. And, see if you are now able to connect to the XP computers.

A friend of mine was having a similar problem. He was not able to connect as a client to any samba shares on the network. Then, he shared a directory of his, and all of the sudden he was able to connect to others on the network. Once that initial connection was made and the addition setup files were installed/initialized he was able to then stop sharing his Ubuntu folder, but was able to continue to connect to the XP boxes.

It also helps if you have all machines in the same "workgroup" especially with Windows XP-Home Edition, since it has crippled networking compared to XP-Pro.

---

### Post by Dani Filth on 2008-05-20
Samba worked smoothly in previous versions (7.04 & 7.10) but ever since I upgraded to 8.04, an annoying problem occured that whenever you want to access your Windows shares, you **have to** type in the full path of the share (e.g "smb://LAN_IP/SharePath" instead of "smb://LAN_IP" like it was in 7.10) which, till now, doesn't seem to have a proper solution for it. (You can search the forum for similar threads)

For those who use LAN & Windows share a lot, this is indeed annoying.

---

### Post by pistos on 2008-05-21
> **Dani Filth said:**
> Samba worked smoothly in previous versions (7.04 & 7.10) but ever since I upgraded to 8.04, an annoying problem occured that whenever you want to access your Windows shares, you **have to** type in the full path of the share (e.g "smb://LAN_IP/SharePath" instead of "smb://LAN_IP" like it was in 7.10) which, till now, doesn't seem to have a proper solution for it. (You can search the forum for similar threads)

For those who use LAN & Windows share a lot, this is indeed annoying.

I don't want to hijack this thread, but my experience with 8.04 is much better than it was with 7.04 or 7.10 in regards to Windows shares. It is very reliable now for me. I create bookmarks of server directories and they stick, working every time.

---

### Post by franky_88 on 2008-06-22
Heelo everyone,


So after several weeks and a lot of work I finally solved my problem. I read trough forums after forums. One day I decided to just uninstall and reinstall Samba. I did it and it worked. I can now see and access windows shares trough my home network.


Thank all of you for your help,

Franck

---

### Post by westdale on 2008-06-25
May be useful to cross-refer to the thread 
[http://ubuntuforums.org/showthread.php?p=5261631&posted=1#post5261631](http://ubuntuforums.org/showthread.php?p=5261631&posted=1#post5261631)

For me Heron worked fine accessing MSHOME and other Windows XP network areas but (possibly) a recent update has affected it?

I shall give the re-install of Samba a go !

---

### Post by Jerm93 on 2009-03-15
Ok, I'm trying to get shares/LAN gaming to work with my vista and my intrepid machines, so far none of the games will connect together and i have gotten the ubuntu desktop to see the vista ("LIVINGROOM") but it just says unable to mount, note i still cant get the windows to see the ubuntu tower. looking for some help!

Map of what network would be

LIVINGROOM--><--Belkin wireless N Router--><--HP Ubuntu machine

(note: im connecting with a wired connection not wireless)

---

### Post by pistos on 2009-03-15
I know this is not a lot of help, but I have not had much success networking any OS with Vista. Ubuntu has been problematic, and even Windows XP has been problematic. So, I will be watching this thread for help too.

---

