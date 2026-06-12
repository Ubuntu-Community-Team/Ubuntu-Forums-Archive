---
title: "What server?"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by Muttly on 2013-01-06
I regard myself as a novice having made the switch only 3 years ago. However I wish to make the steps towards an Ubuntu server. My aim is to back-up my ubuntu desktops and store music in a central location. Would a LAMP server meet these requirements? I would still like a GUI as well.

Could I also run encoding tasks on a server?

---

### Post by iponeverything on 2013-01-06
google around for ubuntu backup and file server, it is a road well travelled.

---

### Post by TheFu on 2013-01-06
> **Muttly said:**
> I regard myself as a novice having made the switch only 3 years ago. However I wish to make the steps towards an Ubuntu server. My aim is to back-up my ubuntu desktops and store music in a central location. Would a LAMP server meet these requirements? I would still like a GUI as well.

Could I also run encoding tasks on a server?

This is very easy, especially for someone with your experience.  You do not need a "server", but if you want the most efficient and stable server on your network DO NOT LOAD A GUI.  X/Windows is fairly crappy code. It crashes. Anything running under it crashes. It leaks memory and since it is always running, those memory leaks never get cleaned up until a reboot happens ... when it starts leaking memory again.  I have friends who worked on the X11 code when at MIT.  Heck, you can look at the code yourself, if you like. It is complex and that makes it hard to maintain and hard to safely clean up all the memory leaks.  BTW, MS-windows leaks memory in their GUI layers too. Ask any C software developer who uses memory leak checking tools, they can confirm my statements.  I've seen leaks on all GUI platforms when running Purify.

I have a few servers.  On is for file sharing, printer server, media transcoding, and a place to put backups.  It runs Ubuntu Server amd64 10.04. I'm planning a migration to 12.04 now.  NO GUI.  Uptimes for this thing routinely go to 90+ days.  In the old days, before kernel patches every few months, I'd have uptimes over a year on most Linux servers ... provided there wasn't any X/Windows clients or servers running.

Ok, I'm off the soap box now.
Steps:
* You can load any Linux OS that you like. Desktop, server, whatever. All of them will stay up at least 2 weeks, so if you reboot every 2 weeks or monthly, then all that desktop code leaking memory won't matter at all.
* If you are Linux-only, use **NFS **to share files.  Always share files between Linux systems with NFS even if you have Windows/OSX clients too.
* If you have MS-Windows, use **samba3** (not v4) to share files. There are lots of how-tos.
* For transcoding, I like **handbrakeCLI**.  No GUI needed. Scripts are fairly easy and much more efficient than all that pointing and clicking.
* You can setup a DLNA server too, if you like.  I found DLNA to have so many issues with out of date files still being shown over the network. It didn't matter if the DLNA server was UNIX or Microsoft.  I prefer file-based streaming - NFS or Samba.

**Backups** are a more complex issue and it depends on your sophistication.  I found tools like **Bacula **to be too complex for my needs.

For Linux systems, I use **rdiff-backup **and LOVE it!  I've restored systems backed up with this technique and it works. There are plenty of other solutions that work equally well on Linux.

For Windows backups, I wanted a tool that could write to shared network storage, then use a 2-step process.  **PartImage** to create an imaged based Windows backup, then **rdiff-backup** to protect data on Windows systems and only data.  The data backups happen daily.  The image backups are manual and happen about once a quarter or whenever a large patch, like a SP, comes from MS - 1 image before and another after.  There isn't any reason that a Windows specific backup tool shouldn't be used. Even the built-in Windows7 Pro tool works.

Anyway, hope this is helpful and not too much of a rant.

---

### Post by Muttly on 2013-01-06
Thanks for your advice guys. Im going to digest whats been said before taking the plunge. The GUI less server with increased uptime does sound tempting. I have amassed 6000 photos, 200 films, and weeks worth of music now so the server solution has been on the cards for a while!

thanks again!

---

### Post by drdos2006 on 2013-01-06
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Allows your browser to connect and modify your server settings on your network, start and stop processes, change permissions etc.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.610_all.deb

Install with :
sudo dpkg -i webmin_1.610_all.deb

Add extra libraries with :
sudo apt-get -f install

```


regards

---

### Post by mysteriousdarren on 2013-01-07
If your worried about a GUI it can always be added and removed once everything has been setup and is working properly. Good Luck!

---

### Post by Muttly on 2013-01-07
Good point, though webmin looks usefull and when installed with PuTTY should allow me to setup the server. From a quick google it looks like I can run these programs off my Ubuntu laptop too!

---

### Post by TheFu on 2013-01-07
> **mysteriousdarren said:**
> If your worried about a GUI it can always be added and removed once everything has been setup and is working properly. Good Luck!

Lots of great data in this thread from different viewpoints.

The GUI doesn't seem to be as unstable as it was, so perhaps I'm overly cautious.  My desktop has been up, running X/Windows and lots of memory sucking programs, plus I do software development .... for 15 days.  I don't really worry about it crashing before a reboot is needed due to a kernel update. Still, GUIs use many more resources - especially RAM. On a server that simply is not needed.

The idea to install server, add a GUI, do your settings, remove the GUI is not a bad one if you know your way around shell enough to figure out what the GUI tools actually did inside the config files. What happens when you need to make a small tweak?  Load up the GUI stuff again, tweak, remove?  

Seems much easier to just learn the few config file settings to me. It will also force learning that will never be a waste of time for anyone interested in Linux systems.

OTOH, I am definitely NOT a fan of **webmin** and similar web front-end tools for systems administration use.  These things have been hacked before and external attackers have found ways to access them.  Honestly, if you don't know how to configure the server without one of these tools, then you probably do not have the skill to secure it either. It is like giving a 14 yr old boy a $200K Ferrari and sending him on a steep and winding road.  Anyway, if you do setup webmin, please, please, please block it from use by all external IPs.  There definitely ARE more risks in using a web front-end than using local GUI tools.

I hope the different views on this stuff is helpful to the OP and later lurkers. Nobody can decide what is best for anyone.

---

### Post by mastablasta on 2013-01-07
Openmediavault might be what you are looking for (debian based).
 
otherwise out of the box GUI file servers:
Zentyal (Ubuntu based)
ClearOS (CentOS/Redhat based)

---

### Post by p2ranger on 2013-01-07
I first took the plunge with Ubuntu when I decided I wanted to setup a server to do various things. As a life long MS Windows user, it was as steep learning curve. I decided right off the bat that I was going to do a headless server so everything was going to be done by CLI (command line interface). I compared it with writing a novel in a new language that I didn't know. I had to google every little thing I wanted to do, whether it was learning to change file permissions or how to install something. As a friend of mine accurately pointed out, Linux is only free if you don't value your time.

It was a lot of work, but I also learned a lot as well. I still don't know a whole lot, but linux is not as foreign to me as it used to be. I just last week updated from 10.04 to 12.04 Things didn't go well so I had to start all over again. The notes I had taken from the first install were incomplete and things had also changed which rendered some of them no longer useful. This time, I kept an Evernote window opened on the side and I documented every command I used and what those commands were supposed to be doing. I even had to start over again, so it made it easier to get back to the point that I had gotten back to.

If you do go the command line route, which I think is the best idea if you are going to run a headless server, make notes.

Some things I've put on mine:

[Backuppc]("http://backuppc.sourceforge.net/") - a huge pain to set up. But once its working, it is a dream for backing up your computers. 

[subsonic]("http://www.subsonic.org/pages/index.jsp") - use for streaming my music. This was an issue I first came across because I had gotten married and I needed a way to manage the merging of my wife's music library with my own. It gives you a web interface to listen to music from any computer as well as mobile apps for listening on tablets and phones.

[CUPS]("https://help.ubuntu.com/11.10/serverguide/cups.html") - use this so that my wife and I can print to the one printer in the house from any computer in the house.

[Webmin]("http://www.webmin.com/deb.html") - I mostly use this for when I want to look up something about my server. I don't use it for making changes as I've read that Webmin doesn't always work the same from distro to distro.

Just a few things I thought I would pass along. Good luck

Jason

---

