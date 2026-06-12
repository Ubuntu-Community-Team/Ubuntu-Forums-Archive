---
title: "[SOLVED] Confused:: Sharing files between Ubuntu &amp;amp; XP??"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Corrupt3d on 2008-06-10
Hi guys, 
I'm Hoping someone can point me in the right direction :) 
For the past 2 hours or so, I've been browsing the web trying to find the best way to Network my _Notebook_ (Ubuntu:Hardy) and a _Desktop_(XP). What I want to do is pretty simple 
1) _Share files back and forth_ & 
2) _Share a printer connected to the Desktop_.
(I dual boot my Notebook and when I run XP on it, I can connect/share with the Desktop without any problems.)

All the articles seem to recommend different steps, however most of them involve **Samba**, so I'm guessing thats my best bet. What I have done so far is: I clicked on a folder and tried to set up sharing, this prompted me to download a few packages which I accepted. I also went to Add/Remove and added Samba from there: After I checked Package Manager the following show up as being installed:

libpam-smbpass  * libsmbclient *  nautilus-share  * samba
samba-common *  smbclient *  system-config-samba

Do I need any other packages?
>>> Could someone recommend a good guide?
In Samba what exactly is a 'Network Share'? Is that simply a shared folder?

Lastly,
I can't seem to find 'Shared Folders' under System>Administration>.  :confused: or
A 'Windows Networking' Option inside of Network Setting. :confused:

---

### Post by dudude on 2008-06-11
When I tired to connect to my XP machine in the past from Ubuntu, all I had to do was go to Places->Network and all of the Windows machines showed up.

I personally use Filezilla with FTP instead of the Shared Folder system from Windows now.

---

### Post by fenian on 2008-06-11
To set up samba follow these steps.

First Go to the menu System>Administration>Users and Groups
click unlock
click properties
click the user privilages tab and and make sure the share files with network box is checked.
click ok.
Next open a terminal and enter...

> shares-admin


in the window that opens click the unlock button then click the General Properties tab and make sure the workgroup matches that of your XP box then close the window.

Next setup the smb.conf file
open a terminal and enter...

> sudo gedit /etc/samba/smb.conf

Under Share Definitions change the line...

;browseable = no
to
browseable = yes

and change the line...

;read only = yes
to
read only = no

save the file and close.

Next add a samba user open a terminal and enter (substitute username with your ubuntu username and when prompted for a SMB password use your ubuntu password)...

> sudo smbpasswd -a username

Next enable that user,in the teminal enter (again substitute username with your ubuntu username and when prompted for a SMB password use your ubuntu password)...

> sudo smbpasswd -e username

Next restart samba,in the terminal enter

> sudo /etc/init.d/samba restart 

You should now be able to share files from ubuntu to xp (you will need to use your ubuntu username/passwd when accessing from xp)

To view the windows shares on ubuntu you should be able to do this from the menu Places>Network.

To access a shared printer go to the menu System>Administration>Printing

Click server settings in the left side menu and check the Show printers shared by other computers box then click the refresh icon and the shared printer should become available (it will be listed in the left side menu)

---

### Post by Corrupt3d on 2008-06-11
I got everything working now :)
Turns out the majority of the problems where being caused by my windows box. 
It somehow manage to corrupt all the files it was supposed to share out. 
After following the guide provided by fenian and reseting my windows shared files it worked!

---

