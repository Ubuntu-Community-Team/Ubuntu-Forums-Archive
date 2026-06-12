---
title: "setup home network"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by PoopyTheJ on 2008-04-28
Ok, so I've looked around at setting up a home network with either windows or ubuntu pc's. I currently have a main desktop dual booting Ubuntu and Windows XP. I want to have it be a print and file server, I want to also be able to pull files to it from other PC's connected to the network. I've checked out some tutorials but they all seem to assume a level of *nix competency I haven't achieved yet. Do I need to do a network setup similiar to XP where I set workgroup names then the machines will see each other? If so where is that tool? If not how do I go about setting this up? I'm currently using NTFS as my file system on the drive with shared documents as geting a nix file system readable and writable in XP seems like way too big of a headache. In short it total moronic newb talk how do I setup or start to setup file and print sharing so when my desktop is running ubuntu I can share files and printers and when it's running XP I can do the same. I'm looking to fully emigrate from XP eventually but right now I still need things which I can only get or do in windows (due to my knowledge level and not some inherent flaw in ubuntu I know).

---

### Post by The Cog on 2008-04-28
There are loads of guides out there. See the link below.

Basically, install samba, create users in samba's user database, and share the appropriate folders. 

I did it once just to see, and I found a GUI configuration program called gsambad very useful.

[http://www.google.co.uk/search?hl=en&q=ubuntu+share+files&meta=&btnG=Google+Search](http://www.google.co.uk/search?hl=en&q=ubuntu+share+files&meta=&btnG=Google+Search)

---

### Post by PoopyTheJ on 2008-04-28
Will I need to setup Samba on both my main desktop, ie the file and print server or do I just set it up on the peripheral machines?

---

### Post by martyssweb07 on 2008-04-28
Not 100% sure I'm following but...

Honestly, Why do you want your desktop to be your gateway, This is just inherently a bad idea.  first for security reasons but moreover, it means if you reboot, or crash... whatever, the rest of your network goes down.

I would suggest setting up a machine as a gateway box, and a seperate box for your NAS. This way your more secure, and it doesn't matter if your desktop goes down.  

If you do choose to go this route, theres alot of great gateway software which will give you much better throughput than eith xp or ubuntu. I know shorewall is easy to setup, and reasonably secure (though not open source). 

let me know your thoughts, and I can help more.

---

### Post by PoopyTheJ on 2008-04-28
Ok, I'll have to build a box to accomplish that. I was actually considering something along those lines but I wanted to set it up with my desktop as the file and print server until I got around to rebuilding the other box to be a gateway. I've got the parts, I think to accomplish it, just not the time. What will probably happen ideally is I want a machine for serving UT2004, print serving and file serving possibly as a mumble server as well. I have a laptop and two other desktops, one which needs to be builtto be the server. I want to install a *nix distro, perhaps debian as the server. In the meantime though I just want files available on my laptop available on my desktop and vice versa. Both machines are directly connected to the internet through my router. Soon to have two more desktops connected. If I'm unclear let me know as I'd really like to figure this out and I'm not the strongest at communicating in type.

---

### Post by brucewagner on 2008-04-28
Those guides seem to be out-of-date.... a year old...  and written for version 7.10.

I tried (using Hardy Heron 8.04) simply right-clicking on the folder I want to Share, and there is a new automatic tool.

Right-click...  Then, "Sharing Options".

Unfortunately, I get an error on the "File Manager - Folder Sharing" window...

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Perhaps this is a bug?

---

### Post by BLTicklemonster on 2008-04-28
My opinion, and it's just mine, is: if you want to network, stick with windows. I don't care what anybody says, networking in linux is just plain twisted and dementedly unpleasant to attempt for the average Joe. AND not worth the effort, in my opinion. I'm behind a hardware firewall, so I don't give a flying rat's pattotie about the security aspect of it all, and I'd never use a computer for anything sensitive, regardless of whether it's linux or windows I use, because in my opinion, that's just plain asking for trouble.

Otherwise try the link in my sig.

---

### Post by bodhi.zazen on 2008-04-28
This guide will help set up samba, including printer sharing. It is working on 8.04.

Samba works out of the box and for the most part is point and click. Follow the graphical configuration sections.

The manual configuration may be needed if the automatic, default settings do not work.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by martyssweb07 on 2008-04-28
Ok if you already have a router, then there is no need for what i mentioned earlier as the router is actually your gateway. 

So as I'm getting this you simply want to share files back and forth from desktop to laptop?

---

### Post by PoopyTheJ on 2008-04-28
yes, although as mentioned I would in time like to have a seperate computer setup as the repository for everything and to run a mumble, UT2004 server so I can just run the clients on the desktop. In short I want a windows type workgroup setup, but I really have no desire to run windows. I just like the ease of sharing files and printers.

---

### Post by brucewagner on 2008-04-28
I have no idea what a "mumble UT2004 server" is...

But what about running Ubuntu Server on one machine?

I've been thinking of doing that.

I bought a new 1TB hard drive that I'd love to share...  so creating a file server on an Ubuntu Server box seems to make the most sense to me.

Yes?  No?

---

### Post by martyssweb07 on 2008-04-28
ok, in ubuntu heres what i'd do

sudo apt-get install samba samba-client

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf_BAK

sudo gedit /etc/samba/smb.conf 

and paste in the following

[global]

   workgroup = mygroup

   server string = laptop

   dns proxy = no

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   security = user

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   invalid users = root

   load printers = yes

   printing = cups
   printcap name = cups

   socket options = TCP_NODELAY


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
   write list = root, @ntadmin


[share]
path = /media/share
available = yes
browsable = yes
public = yes
writable = yes

change workgroup and server string to whatever you like
save the file and close gedit

then do 

sudo mkdir /media/share
sudo chmod -R 777 /media/share
sudo chown -R myusername:myusername /media/share

do the following where your_system_username is your ubuntu login and network_username is your windows username (best if their the same)

sudo smbpasswd -a your_system_username
gksudo gedit /etc/samba/smbusers
Insert the following line into the new file 
your_system_username = "network_username"

sudo /etc/init.d/samba restart

Now this is a quick and dirty, so security may be an issue, but, if you just want to share files behind a firewall it's ok. 

Alternately, you can use sshfs (sshfs is great because it copies files encrypted over ssh) this way the only port you need to open is ssh. (this is great if your laptop is linux) if it's windows, I imagine you'll need to pay for some shareware thing to make sshfs work.
If you want sshfs instructions let me know

---

### Post by BLTicklemonster on 2008-04-28
By the way, I've been able to get XP to networking Ubuntu working on occasion, but never gotten Ubuntu to Ubuntu networking to work. 

Must be holding my teeth wrong or something.


You want a UT2k4 server running in Linux? That would be cool. Our UT server is linux.

---

### Post by bodhi.zazen on 2008-04-28
> **BLTicklemonster said:**
> By the way, I've been able to get XP to networking Ubuntu working on occasion, but never gotten Ubuntu to Ubuntu networking to work. 

Must be holding my teeth wrong or something.


You want a UT2k4 server running in Linux? That would be cool. Our UT server is linux.

LOL, Samba is working for me out to the box, Ubuntu server (manual and GUI configuration), with minimal effort. Both file shares and printers, althoug printers sometimes take a little more work. Multiple working clients including Windows XP, Slackware, Ubuntu (all version), and Fedora (7,8, and 9 preview).

Take a look at the samba wiki page and post questions / problems.

---

### Post by martyssweb07 on 2008-04-28
> By the way, I've been able to get XP to networking Ubuntu working on occasion, but never gotten Ubuntu to Ubuntu networking to work.

have you tried to use sshfs, works awesome for sharing files between machines and the bonus is it does it over ssh, so as long as you have a ssh port open at home you can network over the internet and encrypted at that.

---

### Post by pmenefee on 2008-04-28
I have a home network that I get to work most of the time.  I have XP on my home desktop and Ubuntu on my workshop computer.  The cable connects to a router and broadcasts the signal.  The range extender picks up the router signal and rebroadcasts in my shop.

Every time I turn on the shop computer I have to go through some strange routine.  I go into network and change to ascii for my network, and it usually works, although sometimes I have to change to one of the other options under properties and maybe even back again.  Once it gets a signal it stays connected.

martyssweb07, thanks for the detailed instructions, but at least for me, I couldn't do all that.  Computers are something I work with, not on, and until Linux works without all this coding, it's hard for most to get it working on a network.

I have no idea what ss?? is.

---

### Post by bodhi.zazen on 2008-04-28
ssh

[uwiki]SSHHOwto[/uwiki]

and sshfs mounts directories over ssh

[uwiki]SSHFS[/uwiki]

---

### Post by martyssweb07 on 2008-04-28
pmenefee actually there is a much easier way to do it.  in this post however there is some question as to why the basic way isn't working.  The instructions I gave are simply the "hard way"  the easy way goes like system=>preferences>"personal file sharing" and turn it on.

---

### Post by pmenefee on 2008-04-29
Thanks for the help, but when I go to system.....preferences.........there is nothing entitled "personal file sharing".  Using 8.04.

---

### Post by martyssweb07 on 2008-04-29
Do you have samba and samba-client installed?

---

### Post by pmenefee on 2008-04-29
No, sorry I don't have a clue what Samba is or does.  martyssweb07, thanks, and I really mean that, but I'm one of users who is probably not going to spend lots of time tweaking Ubuntu.  I like what I see, and Open Source works well.  I'm thankful that there is a whole community of people who love to work with Linux and make it better.  Guys like me benefit from what you do.  Thanks.

---

### Post by bodhi.zazen on 2008-04-29
There is a bug with samba, listed here :

[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by PoopyTheJ on 2008-05-02
MArtysweb, I had a bunch of stuff going on and had to drop this for a bit, now after running sudo apt-get install samba samba-client I get,
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
samba set to manual installed.
Package samba-client is a virtual package provided by:
  smbclient 3.0.26a-1ubuntu2.3
You should explicitly select one to install.
E: Package samba-client has no installation candidate
You asked someone if they had samba and samba client installed and go to system-preferences-file sharing, that isn't there for me. I checked there after that first step didn;t work. What's my next step?

---

### Post by PoopyTheJ on 2008-05-02
ok, actually got through the Samba config, thanks a lot for those steps, now to get to those files from my laptop, do I need to install Samba on the laptop as well, and is there something in particular I need to do to get to the files? I really appreciate the help!

---

