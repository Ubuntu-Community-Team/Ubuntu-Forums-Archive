---
title: "[SOLVED] Networking problem: XP and Ubuntu in network"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Nermi on 2008-08-30
I am a total beginner in Ubuntu, but I have recently installed Hardy and I love it. 

However, I have run into a problem when trying to access my Windows network from my Ubuntu box, and although I've done an extensive research about this matter (this Forum and elsewhere), I am still unable to find a solution.

I have three computers in my Windows network, all of them XP, and the workgroup name is MAIN. First, I went to Places &#8594; Network and I did find the icon “Windows network” there. Clicking on that gave me an icon for my MAIN (windows) workgroup. But, clicking on that opened a blank page.

After some more reading, I found out that I needed to install samba. So, I did. But, although I made a little progress (now I can see my Ubuntu share from my Windows computer), I still can not connect to my windows network from Ubuntu. 

When I click on MAIN properties (Basic tab) I get 
Type: uknown, 
Contents: nothing, and 
Location: smb///  

I don't know if that's important, but I have Netgear wireless router. 

What am I doing wrong? 


Nermi

---

### Post by bangmalley on 2008-08-31
guide on setting up samba.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by bab1 on 2008-08-31
It sounds like you need to install [COLOR="Red"]*smbfs*[/COLOR],

See[http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs]("http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs")

---

### Post by Nermi on 2008-08-31
Samba was already installed. 

Now I installed smbf but it didn't change anything. 


Nermi

---

### Post by jonandrews on 2008-09-01
Hi - I've put a step - by - step guide to XP / Ubuntu networking on a website

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

This will show what need to be configured...

---

### Post by Nermi on 2008-09-01
Thank you, but... 

your tutorial deals more with setting up network so you can see your Ubuntu share from Windows. My problem is just the opposite. 

I CAN see my Ubuntu share from Windows, but I CAN NOT see computers in my Windows network (called MAIN) from Ubuntu. 

I have installed Samba, and later I even installed smbf (as someone suggested); that didn't change anything. 

Nermi

---

### Post by halitech on 2008-09-01
open nautilus (Places - Home Folder) if it is showing buttons for the locations, click the notepad to the left to change it to a text box. then type in ```
smb://IP Address/name of share
``` and hit enter. See if that connects for you

---

### Post by Nermi on 2008-09-01
Yes, it does connect me to one of shared folders on one of my windows computers. 

Does that mean that I have to do this for each particular shared folder on all three computers in my Windows network?

And, thanks by the way. 


Nermi

---

### Post by halitech on 2008-09-01
what you can do is connect to each one and then book mark it so it shows up when you open nautilus.

---

### Post by Nermi on 2008-09-01
Excellent!

Thank you very much. 



Nermi

---

### Post by halitech on 2008-09-01
welcome and glad we got it working for you :)

---

### Post by gregphil on 2008-09-01
Ah-hem

I would not call that "solved", but rather a work-around.  Browsing means browsing, it does not mean enter all known shares and then remember them for the next "browse".

I *finally* got full (Windows style) browsing to work with CentOS 5.2 and KDE (gnone never would "browse").  Centos KDE actually works as it should, it lists all the available shares on your sub-net and when you try to connect (expand the share) it requests a username and password valid on the target share.  KDE will remember the username and password if I tell it to.

Then I decided to try Ubuntu and Kubuntu.  To be brief, they broke sharing somehow.  I see various posts about version Ubuntu 8.04 changing the default settings in Samba, and it being necessary to add the the [global] section of /etc/samba/smb.conf the lines:

	client plaintext auth = yes
	client lanman auth = yes

This in itself does not seem to be quite enough.  In Ubuntu or Kubuntu after ever reboot my 'workgroup' (domain) gets cleared to blank.  Sometimes, when I notice this, and reset it to the correct workgroup, and wait 6 minutes, the shares around the network become visable.  The slow update of the browing database (a protocol issue) makes it hard to understand cause and effect here.

On my private sub-net (behind a router) I am comfortable sharing the whole disk on each machines to myself.  For reference here is part of my smb.conf that works under Centos and sometimes works under Ubuntu or Kubuntu:

[global]
	workgroup = MYGROUP
	server string = LIVING-ROOM
	netbios name = LIVING-ROOM
	interfaces = lo eth0 192.168.0.0/24
	hosts deny = ALL
	hosts allow = 127.0.0.1 192.168.0.0/24
	encrypt passwords = yes
	security = user
	passdb backend = tdbsam
	client plaintext auth = yes
	client lanman auth = yes
        |
        |
        |
[DISK]
	comment = DISK
	path = /
	public = yes
	writable = yes
	printable = no
	write list = root, myusrname
	admin users = root, myusrname
        available = yes
        browsable = yes

It is also necessary to run "smbpasswd -a usrname" for each user that you want to allow to connect.  This fills in an encrypted Samba password database for use by Samba to authorize connection requests.

One other possible setting that may be involved (some claim it is) is the gnone configuration database.  To see this get gconf-editor and run it.  Under the "smb" settings there is a "workgroup" entry that default to blank, set this to your workgroup.

If someone actually knows all the settings involved, and how to make share browsing "just work" like it does between peer-to-peer Windows boxes, please post a complete "How Too"

Thank You.

---

### Post by halitech on 2008-09-01
> **gregphil said:**
> Ah-hem

I would not call that "solved", but rather a work-around.  Browsing means browsing, it does not mean enter all known shares and then remember them for the next "browse".

I never said it was solved but it was working and he wouldn't have to remember them as he can bookmark the shares.

> I *finally* got full (Windows style) browsing to work with CentOS 5.2 and KDE (gnone never would "browse").  Centos KDE actually works as it should, it lists all the available shares on your sub-net and when you try to connect (expand the share) it requests a username and password valid on the target share.  KDE will remember the username and password if I tell it to.

Then I decided to try Ubuntu and Kubuntu.  To be brief, they broke sharing somehow.  I see various posts about version Ubuntu 8.04 changing the default settings in Samba, and it being necessary to add the the [global] section of /etc/samba/smb.conf the lines:

	client plaintext auth = yes
	client lanman auth = yes

This in itself does not seem to be quite enough.  In Ubuntu or Kubuntu after ever reboot my 'workgroup' (domain) gets cleared to blank.  Sometimes, when I notice this, and reset it to the correct workgroup, and wait 6 minutes, the shares around the network become visable.  The slow update of the browing database (a protocol issue) makes it hard to understand cause and effect here.


** SNIP **

It is also necessary to run "smbpasswd -a usrname" for each user that you want to allow to connect.  This fills in an encrypted Samba password database for use by Samba to authorize connection requests.

he has no problem with connecting to the Ubuntu box, only going out so no need to set up users on his box to allow them in.

> One other possible setting that may be involved (some claim it is) is the gnone configuration database.  To see this get gconf-editor and run it.  Under the "smb" settings there is a "workgroup" entry that default to blank, set this to your workgroup.

If someone actually knows all the settings involved, and how to make share browsing "just work" like it does between peer-to-peer Windows boxes, please post a complete "How Too"

Thank You.

checked mine and it was already set to my workgroup name

---

