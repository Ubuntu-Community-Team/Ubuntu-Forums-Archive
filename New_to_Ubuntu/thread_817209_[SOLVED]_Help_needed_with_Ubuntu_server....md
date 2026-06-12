---
title: "[SOLVED] Help needed with Ubuntu server..."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by PsycoGeek on 2008-06-03
I have made the decision to try to move my entire home network over to open source for the majority of our computing needs.  I'm starting with and Ubuntu server so that I can migrate all of our files (personal and ripped music) to the server first, then build the client machines one at a time and have access to them right away.

First a little background.  I have tried Ubuntu before, last year, 7.04, on the PC's.  For some really stupid reason I thought it might be a good idea to go with Vista on new PC's that we built just before Christmas... very dissapointing.  I'm ready to move back to Ubuntu, and dual-boot with v-lited Vista for the games that will not run under Ubuntu w/wine (MS Flight Simulator X for me).

My trouble is with Ubuntu server.  I can build it just fine, but I want a GUI for it, so I have been loading the Ubuntu desktop after the initial build.  I figured having the GUI would be a lot easier for me to deal with for setting up client accounts and shares given my long history with Windows (since about 1993??).

The problem is this... The system has an ATI x1900XT video card, and after loading the Ubuntu Desktop no drivers appear in the restricted drivers for me to activate.  When I tried Envy, or following other instructions for loading the drivers, I end up with a system that boots to the log in, but after I log in it goes to a white screen.  I can get back out to the command line, but nothing I do to try and repair the system works.

Is there something I am doing wrong right from the get go with loading the Ubuntu desktop?  Help me get the server up and running so I can get off of the MS wagon, please.

---

### Post by saj0577 on 2008-06-03
You running
```
sudo apt-get install ubuntu-desktop
```
for your gui?
If so then this might not be what you need.

Saj

---

### Post by jimrz on 2008-06-03
When you used Envy it should have backed up your original xorg.conf and given you the name of the backup (hope you noted it). First thing to do is restore that backup.
```
cp /etc/X11/<name of backup> /etc/X11/xorg.conf[CODE]
```[/CODE]
reboot and this should get you your gui back, as you apparently had one before running Envy. You could try other options for restricted drivers but, since this is going to be just a server for your network, why would you need restricted drivers in the first place. Are you in need of desktop effects, etc on the server? If not, the drivers originally installed should do just fine.

---

### Post by avtolle on 2008-06-03
I've a thought that the problem resides with the apparent lack of a suitable driver for you graphics card, and trying various WMs on top of the server install will not be fruitful unless we get the graphics driver issue sorted. When you were working with 7.04, did you try/were you successful in installing a GUI? If so, is there any chance that you might be able to take a look at the /etc/X11/xorg.conf file from that to compare with what might appear under 8.04 (you have installed 8.04 server, as I understand it)? Some ATI folks might be able to assist you additionally, if the information from the xorg.conf file under 7.04 and 8.04 could be obtained and posted. Sorry I cannot be of any further assistance with this.

---

### Post by MockY on 2008-06-03
Why do you need to apply the restricted drivers if it is just for a server? As far as I am aware, no 3D hungry applications are needed for a server. So if you initially get the Gnome to load fine, I think you should leave it that way.

---

### Post by PsycoGeek on 2008-06-03
> **saj0577 said:**
> You running
```
sudo apt-get install ubuntu-desktop
```
for your gui?
If so then this might not be what you need.

Saj

Yes.  This is how I was installing the Ubuntu desktop.

jimrz, MockY:  Did not look at the backup file.  I was trying to get the restricted driver installed because this "server" might get placed in the living room, and eventually hooked up to a flat screen TV and used to view downloaded video, online video (from hulu and other sources). 

avtolle:  Don't have a 7.04 machine anymore to look at.  Plus it is very different than the 7.04 install (the restricted drivers option is completely missing after loading the Ubuntu Gnome desktop as above).

A big question that I have...  If I am only using the "server" to share files, do I really need to use the server install, or can I get away with a regular Ubuntu desktop install and run the samba server on it (and eventually turn the machine into a Mythbuntu box)?  This would get me past the problem of the driver, as I think the restricted drivers would install just fine on the desktop version (they are supposed to include support for the x1900XT, or at least the 8.05 release from ATI does - looked at that last night).

Thank you to everyone so far for your input on the problem.

---

### Post by avtolle on 2008-06-03
I'm aware of the differences, but sometimes one must do some manual editing of the /etc/X11/xorg.conf file, and knowing what was there before comes in handy. 

As for your other question, I would think using a regular Ubuntu desktop install with samba ought to work. Good luck.

---

### Post by PsycoGeek on 2008-06-07
OK, seems I have the video problem worked out.  I'm going to make another post concerning it because of the amount of troubleshooting that I did to "fix" the problem.

Onwards and upward...  Tally HO !!!

Next question... for sharing folders, do I need samba on both the "server" (Ubuntu Desktop w/samba) and the client machines?  I haven't gotten far enough to check that out on my own yet as I have only gotten the "server" built so far.

---

### Post by PsycoGeek on 2008-06-21
OK... Time to revive this thread.  

The "server" is up and running and has SAMBA installed.  I have made two partitions on the 40gig hard drive and mounted them as "downloads" and "shares".  I used "gksudo nautilus" to share them, checked off 'share this folder' and 'Allow other people to write in this folder', and created a user account with 'System-Administration-Users and Groups'

I cannot access the shared folders from a client PC, booted to a live Ubuntu 8.04 CD.  I try to connect to either share as the user I created, but can't.  I can connect to them as 'Administrator' (the user on the "server").  

What do I need to do to give the user I created permission to connect to them?

---

### Post by hyper_ch on 2008-06-21
what makes you think setting up a gui will help you adminstrate your server more quickly?

---

### Post by PsycoGeek on 2008-06-21
> **hyper_ch said:**
> what makes you think setting up a gui will help you adminstrate your server more quickly?

Because a GUI is what I am most used to, coming from an ex-IT back ground of 8 years under M$ operating systems.  Also, the "server" is only serving files... no DNS, DHCP, or anything else... just files.  It may also be eventually used as a MediaPC in the living room, so I want a GUI on it.  

Now, can you help me?

---

### Post by cariboo on 2008-06-21
This is a dumb question, but have you created users on your server?

Instead of a gui on your server have you check out remote admin tools like webmin and ebox?

Jim

---

### Post by PsycoGeek on 2008-06-21
> **cariboo907 said:**
> This is a dumb question, but have you created users on your server?

Instead of a gui on your server have you check out remote admin tools like webmin and ebox?

Jim

I haven't checked those out Jim.  I'm just starting up with Ubuntu again, after a brief psychotic episode of installing Vista on my PC's for some reason.  I want to move off of my Win 2k server and onto an ubuntu one.  I figured a GUI is the fastest way for me to do it, since that is what I know.  

>edit< I also do not have a second box built with Ubuntu... I'm live booting my PC to get user log-ins straitened out before I proceed installing it on a client PC.

And, yes, I did create a user on the server with Users and Groups.  What I need to do is get that user to be able to access the shared folders of the server.  I can see them from the client PC, but can't log into them.

---

### Post by avtolle on 2008-06-21
Is the user you created included within the right group(s), e.g., the admin group?

---

### Post by PsycoGeek on 2008-06-21
> **avtolle said:**
> Is the user you created included within the right group(s), e.g., the admin group?

What groups should the user be a part of?

---

### Post by PsycoGeek on 2008-06-21
Can no one help me out?

---

### Post by hyper_ch on 2008-06-22
a gui is not needed and will actually slow you down... when sharing with samba you need to add system users to the samba server also.

---

### Post by PsycoGeek on 2008-06-22
> **hyper_ch said:**
> a gui is not needed and will actually slow you down... when sharing with samba you need to add system users to the samba server also.

OK...  I'm willing to go that route.  But the "server" is really an Ubuntu 8.04 x32 Desktop build because of needing to enable the restricted drivers for the ATI card (to eventually hook up to a flat screen TV in the living room).  I could not enable them after loading the Ubuntu Desktop after installing an actual server build.  Will I still be able to do everything on the Desktop build via command line?

Please post everything step-by-step because I am still a novice when it comes to Ubuntu and Linux in general.

---

### Post by Dedoimedo on 2008-06-22
Hello,

The whole difference between server and client is the issue of open ports. Personally, I see no reason why you should or shouldn't run just about any version you like - and then simply install needed server packages.

As to sharing, try this, see if this helps you out:

[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

[http://www.dedoimedo.com/computers/linux_commands.html#network_sharing](http://www.dedoimedo.com/computers/linux_commands.html#network_sharing)

This shows sharing via Samba. But you can also share between *NIX systems using NFS, if you like.

Cheers,
Dedoimedo

---

### Post by PsycoGeek on 2008-06-22
I can share whichever way... all I need to do is to be able to make persistent connections to the "server" when the clients boot, invisible to the users (myself, my wife- who is a typical user, no put down intended, and my son who is 12).  

When I last ran Ubuntu I used CIFS to make the persistent connections to my Win2k server, but now the game has changed.  That server is going to go away in favor of Ubuntu...

---

### Post by tootlet on 2008-06-24
Hi PGeek,
Did you set up a samba password for the client machine? I'll assume you are logging in on the Windows client with "user" and the password is "password".
On the Ubuntu server do 
sudo smbpasswd -a user 
and then type in "password" twice. Restart Samba (or reboot the server).
Then go to the Windows box and go to start, run and enter
\\whatever you named the Ubuntu box. A logon screen should appear. Put user and password in. 

Obviously you will use something other than user and password on your set up. But I've found setting up the samba password is the final and (in my case) often overlooked step. And though there seems to be a section for this in SWAT I've never used it successfully. I've always had to use the CL
I. Hope this helps.

Good luck,
T

---

### Post by PsycoGeek on 2008-06-26
The original problem with the server build has been solved.  I will open a new thread for my other problems.

---

