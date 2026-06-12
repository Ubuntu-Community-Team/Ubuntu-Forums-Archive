---
title: "New Ubuntu installation: Basic Steps. 11.10"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by alexanderedward on 2011-11-25
Having recently upgraded to 11.10, I was dismayed by how confusing it was, and how much poring over the Forum was required to get it to a point where it does the basic things one expects of an OS. The lack of the classic console is a case in point. It may well be that linux geeks can make head or tail of the new, default, Launcher style console, but personally I think it is some bad joke. Naturally I realize that Ubuntu and others, don&#8217;t have the benefit of MS&#8217;s 10,000 paid developers, but if anyone reading this is involved with configuring what is included in the distros, then I suggest it would be a huge step forward to simply load them up with all the basic stuff. If that is not done, then it makes it very difficult for linux to gain traction beyond the world of Dungeons and Dragons lovers. Normal people need to be able to install it, and then plug things in and have them work, find the installed applications, get it running on their home network, and so on. Preferably without having to consult Ubuntuforums.
 
So for the benefit of others like me ie average users who are trying to like linux, but are more interested in using it, than being a student of it, this is what I did&#8230;.
 
 
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT]Install the classic console. This is necessary if you want to view your applications in some sensible way, access the Places menu in a sensible way and so on&#8230;
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Find Terminal in the top launcher button
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]>sudo opt-get install gnome-session-fallback
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Now log out, and relog in but when you do, click on the * next to the space for your password, and select Classic
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT]Now it is time to install a variety of software items which should have been included in the distro in the first place
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Sudo apt-get install gnome-system-tools
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT](this installs a bunch of tools, some of which are absolutely necessary for accessing a variety of things, particularly the Users and Groups ap.
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Sudo apt-get install apache2
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Sudo apt-get install libapache2-mod-dnssd
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT](these two make personal file sharing work)
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Sudo apt-get install python-glade2
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Sudo apt-get install glade-gnome
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT](no idea what these do or if you need both, but at least one of them is necessary to make Samba work)
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]sudo apt-get install samba smbfs
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT](this installs samba)
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT]Now, reboot. Maybe not necessary, but do it anyway.
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT]When logged in, select Applications>others>Main Menu
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]Select each option in the left hand column in turn, and then tick every box for each of them, in the right hand column. Why, oh, why, would they not all be ticked by default??
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT]Applications>Others>Users & Groups
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]For each user (ie only one initially .. you)
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]>Advanced>Privileges
[FONT=Courier New][SIZE=3]o[/SIZE] [/FONT]And check every box. For some stupid reason, the tick boxes which give permission to mount USB devices and others, are unchecked by default. Without checking the boxes, you get a very unhelpful &#8216;cannot mount drive xx. Unauthorised&#8217; type message when you plug in your USB camera, card reading, external HDD etc. 
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT]Comment about Personal File Sharing, and Samba. I am NOT an expert on any of this, but I have picked up that there is a lot of confusion about the relationship between these two. Answer is that there is no relationship. PFS is a mechanism for sharing files among different linux users. Samba is a mechanism for sharing Windows and Linux machines on the same network. Completely different idea.
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT]Configuring Samba.
This seems to be an ongoing problem for users, in that they can see linux on the Windows network but when they try to access it, are asked for a password or some message saying they are not authorized. The trick is that you have to go to samba configuration first..
Applications>Others>Samba 
&#8230; and set up samba users with the SAME name as the pc names on the Windows network. So when you try to access your linux machine from the windows network, the former will recognize the pc as an authorized Samba user.
 
 
No doubt there are other things, but the above steps at least got me to a point where I could use Ubuntu on my home network, and access all its functions.

---

