---
title: "Entry level Linux – server or desktop?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-07-13
(Here is the essence of my question: Can I effectively run Samba and LAMP services on Ubuntu Desktop or do I need to run the Server version? And if I *can* run them on Desktop, is it going to be more trouble than it’s worth? The below provides detailed background in case something in there makes a difference, and in case this question is nonsensical.)

I should have known better than to look Linux directly in the eyes. 

Long story short: I had some issues with a Linksys NAS200. I use it in my home office as a file server in RAID(1), and needed to find a way to read the drives if something happens to the device (it runs Linux). I tried not looking too closely – I actually found a solution by running a Knoppix live CD on an old laptop and using an external enclosure. I really really tried not looking too closely. But... but ... I couldn’t help myself. The Linksys box doesn’t run Gigabit Ethernet, and its RAID service is software based. Backing it up is a bit cumbersome. A custom Linux server started looking more and more attractive. I knew I shouldn’t have looked to closely!

The end result is that I cobbled together some old parts out of the graveyard, and now have a PIII system with 512 MB, an 80 GB drive, DVD ROM, etc. I’ve installed Knoppix and Ubuntu Desktop and Server (one at a time, of course), and it runs them fine. Once I learn how to set things up and run them smoothly, I’ll be upgrading the hardware (e.g., something with a hardware RAID), so a puppy version (is that the right term?) isn’t necessary – I’ll buy hardware to match the version’s needs. 

The primary machines run WinXP (Pro and Home) and Mac OSX (Leopard and Jaguar) connected together via a router. Because of clients’ software requirements, we can’t change these over, and have to keep them as our main workhorses. We also have a WinXP box in the parlor connected to the intranet to play NAS-stored files (e.g., MP3s, SHNs, WAVs) on the stereo. 

There are the few things I want to do with it: 

File serving/sharing:
The main purpose is for it to serve as our NAS device. Mrs. Dvl and I frequently work on/need access to the same files. Because of this, all of our files are stored on the Linksys. This, I believe, is where SAMBA comes in. 

Web testing: 
If I understand this correctly, I can install Apache Web Server, then point Dreamweaver to use the local Linux box as the test server (as opposed to our or our client’s hosts). Right now, whenever we want to see the results of changes to a PHP page, we have to upload them to a remote host. This is not problematic per se, but there is a noticeable delay and occasional timeouts. If I’m not mistaken, testing them here over our LAN will be *much* faster. I understand there may be some synchronization problems (e.g., different versions of PHP), but the effort in adjusting for that seems worth it. 

MySQL testing:
Basically the same as above. Many clients ask us to create databases for their pages, and the testing process can get a bit cumbersome. 

(On preview, I thought to add—most of our work is editorial and design consultation. Adjusting/creating Web pages is a necessary, but very small part of what we do. We’re decidedly *not* “real” programmers.)

Backing up:
I want to run regular backups of our files and send them to the repurposed Linksys device. Something that will only back up files that have changed. I imagine there is a slew of Linux software that does this, but since I want to run it, I thought to mention it. 

Security
I’m not sure about this, but it just feels *wrong* not to take some security into account. The box will be sitting behind a NAT (in the router), and I don’t have any intention to make it visible to the net. It won’t be used to surf the net, and once it’s up and running I can’t see installing any software I don’t trust. One area of possible concern would be macro- or other viruses embedded in a file saved to it from one of our desktops. But since we both have on-access scanning running resident on our machines, is this really an issue?

I think that’s it. We’ll never run our own publicly-accessible Web site from the server, nor connect to it remotely. I’ll probably be installing Linux on other machines in the future (i.e., the parlor-laptop), but right now I think I’m only interested in the above. Of course, suggestions are welcome!

So which version should I run?

I currently have Ubuntu Server installed, and have spent several days becoming familiar with command line functions (takes me back to pre-Windows DOS days). But I am much more comfortable in a GUI environment, and if I can get the Desktop version to do all of the above, I think I’d prefer that. I realize I’ll likely need to use the command line for a host of configuration tasks, but my intuition says that the learning curve for the Desktop version will be easier. 

I’m a complete newbie to Linux, but I am slightly technologically inclined. Over the past few years I’ve taught myself enough PHP and MySql to create such things as surveys and document libraries, both with public and administrative interfaces (e.g., search for documents, add and remove them, adjust their criteria). But since I’ve still got a lot of learning to do on that front, the quicker I can get Linux up and running the above, the better it will be. For example, I can navigate withy cd, ls, etc., but if I’m looking at a GUI file tree, maneuvering will be that much easier. 

Is speed an issue? Since a hardware upgrade is in the works regardless, I assume that a new board with RAID capability and a basic no-frills CPU will still be able to handle basic file sharing and Web testing without a noticeable difference. And with RAM being relatively cheap, a couple GIG should also make a difference. There is only my wife and I in the office, so there will never be more than two of us hitting it at the same time – and even then only to load/save a document or test a page, and we’d rarely do it simultaneously.  

So, is accomplishing the above even possible on Desktop? By trying to make things “easier” for myself, am I actually making things more complicated? 

Sorry if this is too long. I tried to provide all information I thought would be relevant, and hope it wasn’t overkill. I also took the time to read a slew of relevant threads and Web sites, but am still unsure if I can do the above on Desktop, and if it would be worth it to do so.  

Thank you very much for any help or guidance you can share!

Rhythm

---

### Post by sdennie on 2008-07-13
If you are just learning Ubuntu and would be more comfortable doing things with a GUI, it's fairly straightforward to do this.  Simply install the server version and, when you initially login (it should be command line), you can simply run:

```

sudo apt-get install ubuntu-desktop

```

That will download and install what you would normally get with a desktop install onto a server install.

The other option is to go in the opposite direction and install the desktop edition and then install the server components later.  All the software from both Server and Desktop editions comes from the same place so, really, the only difference between the two is the initial packages installed.  It's very easy to convert a Server install into something that resembles a Desktop install and vice-versa.

---

### Post by Rhythmdvl on 2008-07-13
Wow, thanks, I had no idea this could be so easy -- so much for typing out all of the above! 

I&#8217;ve been watching everything install, and lots of things, while nice, aren&#8217;t necessarily useful to what I&#8217;ll be using it for (e.g., OpenOffice). But it&#8217;s probably easier to get everything than determine which elements I really need. Assuming a modern board, at least 2 GB of RAM, and ample drive space, and assuming I don&#8217;t have OpenOffice/FireFox et all running in the background, is it safe to assume that the server won&#8217;t take any significant performance hit with the extra goodies installed? 

After rebooting, I have a slight video problem. The box I have it on has a 3dFx Voodoo 3500 card with an obnoxiously large &#8220;pod&#8221; of sorts to connect display connections. While I was running the Server edition, I had the S-Video cable plugged in (S-Video and VGA wouldn&#8217;t run simultaneously). I used the S-Vid connection because my display allows picture-in-picture via a TV-like signal, but won&#8217;t do it with VGA. P-I-P makes things MUCH easier, as switching between inputs is cumbersome to say the least. 

[deleted question about sound due to idiocy. Hey, I said I was technically inclined, not smart!] 

Thanks!

Rhythm

---

### Post by philinux on 2008-07-13
You could try this for sound.

system>prefs>sound

Change to alsa and then test each item see if that works.

---

### Post by Rhythmdvl on 2008-07-13
> **philinux said:**
> You could try this for sound.

system>prefs>sound

Change to alsa and then test each item see if that works.

Thanks for the direction -- it turned out the PCM slider was set to zero. Pandora is now keeping me company in my travels :)

---

### Post by KamakazieX on 2008-12-04
All the desktop version is, is the Server version with the ubuntu-desktop package installed. You get sick of the gui just apt-get remove ubuntu-desktop and them apt-get autoclean or clean

---

### Post by hyper_ch on 2008-12-04
running a desktop won't help you really for running servers/daemons

---

### Post by muut on 2010-12-26
> **sdennie said:**
> If you are just learning Ubuntu and would be more comfortable doing things with a GUI,...The other option is to go in the opposite direction and install the desktop edition and then install the server components later.  All the software from both Server and Desktop editions comes from the same place so, really, the only difference between the two is the initial packages installed.  It's very easy to convert a Server install into something that resembles a Desktop install and vice-versa.

Easy for you to say ;)

Well, I am VERY new but want to learn. So, I have the Desktop edition (10.04) installed. Can you (or anyone) give me some guidance on how to get Server components installed? I am looking to have a box that can act as a Server/network storage device and be able to allow workstations  *to boot* remotely via [I]PXE, map a drive to the Server, etc... 

Thanks in advance for any help...
[/I]

---

