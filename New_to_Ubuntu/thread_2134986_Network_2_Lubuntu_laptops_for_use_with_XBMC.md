---
title: "Network 2 Lubuntu laptops for use with XBMC"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by sbomb90 on 2013-04-12
I've Googled and searched and experimented a ton but this is frustrating me so I came here for help.   I'm a Lubuntu/Linux newbie so I'm looking for a solution that isn't totally over my head.  I have a 1 TB USB Western digital hard drive with a[COLOR=#444444][FONT=arial]NTFS [/FONT][/COLOR][FONT=arial][SIZE=2][COLOR=#444444]Filesytem filled with content hooked up to my Lubuntu 12.10 laptop HTPC living room setup.  I also have a Lubuntu 12.10 HTPC netbook setup in my bedroom that I would like to be able to sync up to the content on the 1TB harddrive.  My problem is that I cant seem to be able to figure out how to make it work. 

My steps so far -

1. I used Samba (version on lubuntu software center with a GUI) to set up the USB harddrive as a shared folder.  
2.  Installed xbmc Frodo to my netbook bedroom setup
3. Under Im able to use xbmc "add video source" to "browse" to the SMB->workgroup>  but it wont let me access the living room HTPCs files.
4 [/COLOR][/SIZE][/FONT][COLOR=#444444][FONT=arial]  It brings up a lock settings box and asks me for username and password.[/FONT][/COLOR][FONT=arial][SIZE=2][COLOR=#444444]
5 I input the username and password of my living room HTPC but nothing happens. 

Im not super strong on the terminal being a totally linux newbie. 

Any help would be appreciated
Thanks :)



[/COLOR][/SIZE][/FONT]

---

### Post by sbomb90 on 2013-04-12
Figured it out!!   Had to use "sudo smbpasswrd -a"
To set a sbm password

---

