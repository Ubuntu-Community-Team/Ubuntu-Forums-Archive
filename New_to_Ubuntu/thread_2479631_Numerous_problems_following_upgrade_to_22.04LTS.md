---
title: "Numerous problems following upgrade to 22.04LTS"
date: 2022-09-30
forum: New to Ubuntu
---

### Post by kbarber3 on 2022-09-30
Sorry this is such a long post.  I'm not sure what is relevant and what isn't (or perhaps how many different problems I have).

**My level of experience**
More-or-less rank beginner.  (*e.g.* I don't even know where to look for system logs etc if anyone needs information from them.)  But I'm not afraid of the command line and if someone holds my hand for a while I can probably start to work out some of the simpler things for myself.  Anything complicated will need spelling out, preferably in words of one syllable.

**Where it all started**
A couple of months ago I upgraded from 20.04 to 22.04; didn't really intend to but clicked the wrong button in a dialogue at the end of a long day so decided to let it run.  20.04 was itself an upgrade from 18.04 pre-installed when PC delivered late 2019 and had given no problems (original installation and 20.04 used Budgie desktop which was dropped for 22.04).

None of the subsequent problems have been permanent showstoppers.  Some have taken considerable time to sort out; these all recur, seemingly randomly.  Some have never been sorted but not necessary for my work so I've left them.

**Problems**
In no particular order:
Sometimes machine fails to boot, requests boot media be inserted.  This has so far been overcome by changing boot order, sometimes several times; each of the available options has been used and all have worked at various times (I'll post details of the options I have if requested, if you know a way of finding them without rebooting the machine please say so).

If the system is left running overnight with several pieces of software open, one (Evolution email program) will usually have closed itself by the morning.  When this happens, attempting to open one of the others (usually Firefox or LibreOffice Writer) results in that, too, shutting down.  Attempting to open anything at that point results in a hamster wheel that runs for a while, but nothing opens; only solution is to reboot the machine.

Some of the programs listed in the 'Activities' option don't open at all; a particular example is Drawing.  Some work for the most part but occasionally fail (one such is pCloud).  Some I could open now fail (Synaptic is one, I seem to recall Drawing is also in that category).

Software installer seems to misbehave: I was able to use it to install software but it won't list installed software and when I try to check updates I get this error
   Unable to download updates: E:[http://dl.bintray.com/aluxian/deb](http://dl.bintray.com/aluxian/deb) stable InRelease is not (yet) available (Connection failed [IP: 3.121.3.67 80])

Shutdown or reboot is hit or miss.  Sometimes behaves perfectly.  Sometimes goes to black screen which then fills with message below (sometimes via the shutdown dialogue and sometimes not) -
   [  ] systemd-journald[477]. Failed to write entry (yy items, zzz bytes), ignoring: Read-only file system.
This will occasionally finish in a reasonable time, other times it will run as long as I let it (but usually comes to an end and machine shuts down if left overnight).  I have found various references to similar messages here, for 18.04 or earlier and with suggestions that don't seem to work when I try them - commands don't seem to be recognised by the terminal (unless I'm trying to input them in the wrong place - definite possibility, see above re my level of knowledge).

Occasionally while shutting down the system will pause, sometimes for rather a long time, showing the message -
   Unattended-upgrade in progress during shutdown, please don't turn off the computer
Again this may sometimes be very quick or sometimes needs leaving to finish overnight.  I wouldn't include it, except that there have been times when the Software Updater has failed, referencing 'unattended-upgr'.  That now seems to have ceased, but the Software Updater now fails to download repository information.  (Settings are default.)

Today I had the machine drop out to a black screen without trying to reboot, with the following series of messages appearing -
   [  ] FAT-fs (nvme0n1p2): unable to read boot sector to mark fs as dirty
   [  ] EXT4-fs error(device dm-1):_ _ ext4-find.entry:1612: inode #5513292: comm snapd: reading directory 1 block 0
   [  ] Buffer I/O error on dev dm-1 logical block 0, lost sync page write
   [  ] EXT4-fs (dm-1) I/O error while writing superblock
The last 3 lines were repeated after a while and it looked as if that would continue, but I needed the machine for the afternoon's work so forced a power-down.

Whenever the black screen appears, I have found that forcing a power-down resolves things (sometimes via the boot media request etc when I switch on again) so I can continue working.

Apologies again for such a long post, I have no idea what is strictly relevant and what isn't so please help me to narrow it down.  Also please be aware I use the computer for my work and have a very full schedule, with several 12 hour days each week, so it may be some time before I can respond to requests or suggestions.

Any assistance would be most welcome.

---

### Post by tea for one on 2022-10-01
First, have you backed up your personal data?
> **kbarber3 said:**
> Today I had the machine drop out to a black screen without trying to reboot, with the following series of messages appearing -
[ ] FAT-fs (nvme0n1p2): unable to read boot sector to mark [COLOR="#0000FF"]fs as dirty[/COLOR]
[ ] [COLOR="#0000FF"]EXT4-fs error[/COLOR](device dm-1):_ _ ext4-find.entry:1612: inode #5513292: comm snapd: reading directory 1 block 0
[ ] Buffer I/O error on dev dm-1 logical block 0, lost sync page write
[ ] EXT4-fs (dm-1) [COLOR="#0000FF"]I/O error [/COLOR]while writing superblock
The last 3 lines were repeated after a while and it looked as if that would continue, but I needed the machine for the afternoon's work so forced a power-down.
Forced power down will often lead to file system damage.
Are you familiar with repairing file systems via a live Ubuntu session?

My instinct tells me that a clean install and restore backup may be quicker than repairing file systems and chasing down the other problems.

---

### Post by Impavidus on 2022-10-01
That's a long and somewhat diffuse list of problems. It's unlikely to have a single cause, unless it's a hardware problem. The filesystem errors and the read-only filesystem point to possible hard drive failure. Make sure you've got good backups of your important files.

Maybe the smart status of your drive has some interesting bits: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools). It looks like your drive is called /dev/nvme0n1, not /dev/sda as in the examples.

---

### Post by kbarber3 on 2022-10-01
Thanks for this, though I fear it's not the good news I hoped for.

> **tea for one said:**
> First, have you backed up your personal data?

I have all my data synced with pCloud, except the last week's worth of client confidential (that is done using their crypto facility, which doesn't work automatically, and the last update failed).  I suspect you may be telling me that's insufficient?

> **tea for one said:**
> Forced power down will often lead to file system damage.
Are you familiar with repairing file systems via a live Ubuntu session?
Not at all I'm afraid.

> **tea for one said:**
> My instinct tells me that a clean install and restore backup may be quicker than repairing file systems and chasing down the other problems.

That's what I was afraid of.  Including that - from what you're saying - I have multiple problems here.

Any idea how much time I should allow for clean install?  I imagine I'll find instructions somewhere here?  If it's going to be a long job it may need to wait until I've a weekend when I'm at home without scheduled meetings...

---

### Post by kbarber3 on 2022-10-01
Hmm... installing smartmontools seems to fail... smartctl comes up as command not found.

I have a nasty suspicion it has to do with these lines in the output when I tried to install smartmontools -
```
dpkg: error: duplicate file trigger interest for filename '/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders' and package 'libgdk-pixbuf-2.0-0:i386'
E: Sub-process dpkg --set-selections returned an error code (2)
E: Couldn't record the approved state changes as dpkg selection states
```

Looks like another session with Mr Google, unless anyone can offer a shortcut.

---

### Post by tea for one on 2022-10-01
> **kbarber3 said:**
> 
Any idea how much time I should allow for clean install?
Well, that will very much depend on your PC, your internet speed and your experience with installations.
For example:-
Download ISO = 15 minutes
Prepare USB installer = 10-15 minutes
Boot and Try Ubuntu = User choice, although I usually spend 30 minutes looking at the new features.
Install = 20-30 minutes
Restore backup = Depends on how much data.

if you haven't done this often, then the time will be increased due to unfamiliar procedures.

---

### Post by kbarber3 on 2022-10-01
Thank you... not as bad as I thought.  Hopefully time taken to backup will give some kind of indication how long restore might take (please don't feel that's a request to respond, unless you want to save me from getting this seriously round my neck).  I guess another google session will tell me what I need about the various stages.

Very grateful for help so far - from you and from Impavidus.  Hopefully I'll be able to leave you in peace before too long...

---

### Post by Impavidus on 2022-10-01
Checking the health of your hard drive can also be done during the live session ("Try Ubuntu"), just before installing, or after your fresh install. There's no point in fixing package management now if you're going for a fresh install anyway.

Occasionally checking hard drive health is a good idea. Keep the reports somewhere safe, so that you can monitor changes over time.

---

### Post by kbarber3 on 2022-10-04
Thank you both, I think I know where I need to go with this now.  Looks like a clean install for one thing.  My caseload being what it is, that's not going to be before Friday afternoon (London time), but it does give me time to do a bit of homework (at my level that's basic instructions on how to do it); if either of you have really good hints and tips for the process, I'm all ears.

Hopefully that will allow me to install smartmontools and check the hard drive.  I'm hoping that doesn't take me into even worse places...

I hope it'll be OK if I leave this thread open until after the new install is up & running, so I can pick your brains again if needs be?  Sorry to be a pain (and I suspect some of my questions are pretty basic), but a combination of having too much on and it being a *long* time since I messed about in the innards of a system are making it quite hard for me to fit in the work I need to do.

---

### Post by kbarber3 on 2022-10-04
Me again, I'm afraid.

Trying to get the .iso file set up ready for the install.  Can't find 'Startup disk creator' on my machine (wonder if that was one of the failures when it upgraded a few weeks ago).  Tried to install UNetbootin as a recommended alternative.  The first command I used, as recommended, was 
```
sudo add-apt-repository ppa:gezakovacs/ppa
```; 
partway down the output I got 
```
Err:12 https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release    
  404  Not Found [IP: 185.125.190.52 443]
```
 which led to the last few lines looking like [
```
Reading package lists... Done                 
E: The repository 'https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Err... help?!!

---

### Post by tea for one on 2022-10-04
mkusb is a splendid utility for USB devices.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
The developer of this software is a regular contributor to these forum pages.

---

### Post by kbarber3 on 2022-10-05
Thanks yet again... not sure I'll have much time today but will certainly take a look when I get a chance.

---

### Post by Impavidus on 2022-10-05
And if that doesn't work, you can directly use the low-level tools that mkusb uses behind the scene. That means dd, or any other command line file copy tool. The tricky part is not to wipe the wrong drive clean.

---

### Post by kbarber3 on 2022-10-05
Again I get the gezakovacs not found issue as in my post #10 above, and the subsequent 'does not have a Release file...' etc results.  Mkkusb seems not to install - certainly I get a 'command not found' response when I try to use it and a filesearch gets no results.  Interestingly, the errors after trying the 'sudo apt install mkusb command' goes back to the duplicate file trigger error as in post #5.  There must be something (obvious?) I'm not doing but this is where I really do run up against my own ignorance.

---

### Post by kbarber3 on 2022-10-05
Had a client cancel so there was time to do some digging.  And every  time I think I'm getting somewhere, I seem to meet another block.   Chasing up the 'doesn't have a release file' issue leads to a suggestion  of removing the cdrom entry from the /etc/apt/sources.list file.   But I can't see such an entry in my sources.list - and in any case I  couldn't do it because I'm shown as not the owner, therefore unable to  change the permissions.

Looking into it further, there's a  suggestion to remove (a) PPA(s), but that's for a 14.04 problem and  frankly if I'm getting into that region I don't know where to start;  this is where, if I'm to start making changes to things, I suspect I  really will need my hand holding.

---

### Post by Holger_Gehrke on 2022-10-05
The file 'Release' in a repository is part of the basic structure of a repository. If there is no 'Release' file in a PPA for a specific release of Ubuntu, then that PPA doesn't have packages for that release. If you look at the page [https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa](https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa) you'll see that the newest release for which there are packages is 'Groovy'. The last time packages were built for that PPA is 99 weeks - almost two years - ago. That page also has various links, including a github page were you can download a (non-distribution specific) binary.

Holger

---

### Post by tea for one on 2022-10-05
> **kbarber3 said:**
>   Mkkusb seems not to install - certainly I get a 'command not found' response when I try to use it and a filesearch gets no results. 
Can you open a terminal and run these commands one at a time:-
```
sudo add-apt-repository ppa:mkusb/ppa
sudo apt update
sudo apt install mkusb
```
As soon as you see an error message, please post the command and full terminal output within code tags so we can see what is happening.

---

### Post by kbarber3 on 2022-10-05
Fell at the first hurdle.
```
sudo add-apt-repository ppa:mkusb/ppa
```
gave output
```
Repository: 'deb https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/ jammy main'
More info: https://launchpad.net/~mkusb/+archive/ubuntu/ppa
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Found existing deb entry in /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Adding deb entry to /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Found existing deb-src entry in /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Adding key to /etc/apt/trusted.gpg.d/mkusb-ubuntu-ppa.gpg with fingerprint 29D76ADA2D15A87BF4C68B823729827454B8C8AC
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://mirrors.tuxedocomputers.com/ubuntu/mirror/security.ubuntu.com/ubuntu focal-security InRelease
Ign:3 https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy InRelease   
Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]      
Hit:5 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Hit:6 https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu jammy InRelease        
Err:7 https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release     
  404  Not Found [IP: 185.125.190.52 443]
Get:8 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]        
Get:9 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7,453 B]
Get:10 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,452 B]
Get:11 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]     
Get:12 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]
Get:14 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [613 kB]
Get:15 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [327 kB]
Get:16 http://archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [279 kB]
Get:17 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [426 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [2,127 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [728 kB]
Get:20 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [962 kB]
Get:21 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [694 kB]
Reading package lists... Done                              
E: The repository 'https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Hoping that's useful.

I have searched on 'See apt-secure(8) manpage', which was where I got the suggestion to remove the (nonexistent) cdrom entry.  But as you can probably see I'm well out of my depth.

---

### Post by tea for one on 2022-10-05
> **kbarber3 said:**
> Fell at the first hurdle.
```
sudo add-apt-repository ppa:mkusb/ppa
```
```
Found existing deb entry in /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Adding deb entry to /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Found existing deb-src entry in /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/mkusb-ubuntu-ppa-jammy.list
Adding key to /etc/apt/trusted.gpg.d/mkusb-ubuntu-ppa.gpg with fingerprint 29D76ADA2D15A87BF4C68B823729827454B8C8AC

```

mkusb repository hasn't failed, it has been added to your sources list
The failure (mentioned by Holger in post 16) is:-
Err:7 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release     
404  Not Found [IP: 185.125.190.52 443]

What is the output from:-
```
sudo apt update
```

---

### Post by kbarber3 on 2022-10-05
Wow, that was quick.

sudo apt update
gives 
```
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Ign:3 https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy InRelease   
Hit:4 http://mirrors.tuxedocomputers.com/ubuntu/mirror/security.ubuntu.com/ubuntu focal-security InRelease
Get:5 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Get:6 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7,453 B]
Hit:7 https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu jammy InRelease        
Get:8 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,452 B]
Hit:9 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Err:10 https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release    
  404  Not Found [IP: 185.125.190.52 443]
Get:11 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]
Reading package lists... Done       
E: The repository 'https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Sudden thought that I might help by giving the whole story rather than one command at a time. So
```
sudo apt install mkusb
```
gives
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  dialog dus exfatprogs expect guidus libtcl8.6 mkusb-common mkusb-nox
  mkusb-plug pv tcl-expect tcl8.6 usb-pack-efi
Suggested packages:
  tk8.6 doc-base tcl-tclreadline
Recommended packages:
  exfat-utils
The following packages will be REMOVED
  exfat-utils
The following NEW packages will be installed
  dialog dus exfatprogs expect guidus libtcl8.6 mkusb mkusb-common mkusb-nox
  mkusb-plug pv tcl-expect tcl8.6 usb-pack-efi
0 to upgrade, 14 to newly install, 1 to remove and 2525 not to upgrade.
72 not fully installed or removed.
Need to get 0 B/25.5 MB of archives.
After this operation, 35.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
dpkg: error: duplicate file trigger interest for filename '/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders' and package 'libgdk-pixbuf-2.0-0:i386'
E: Sub-process dpkg --set-selections returned an error code (2)
E: Couldn't record the approved state changes as dpkg selection states
```

After that, 
```
mkusb
```
gives, as before, 
```
bash: mkusb: command not found
```

---

### Post by tea for one on 2022-10-05
```
dpkg: error: duplicate file trigger interest for filename '/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders' and package 'libgdk-pixbuf-2.0-0:i386'
E: Sub-process dpkg --set-selections returned an error code (2)
E: Couldn't record the approved state changes as dpkg selection states
```
This isn't going very well yet.
Unfortunately, I have no idea what that error message means nor how to fix it.
As you are going to re-install, it probably isn't worth pursuing a solution.

You still only need an application to create a USB install device, so there are some alternatives which may help:-

Use the terminal command dd (mentioned in post 13)
It is not particularly intuitive if you are unfamiliar with it, although plenty of online info.
You have to be very careful with the selection of the target device!

Have a look at [https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
You only have to download an installation package via a web browser and then follow the installation instructions.

---

### Post by kbarber3 on 2022-10-05
Trust me!  Never do anything simple if I can cause trouble!

Thanks for this so far.  Clients for the rest of the evening, but I've a gap tomorrow morning so I'll look at your link then.

---

### Post by Holger_Gehrke on 2022-10-05
The dpkg error (which you already had when trying to install the smartmontools) shows that there's something wrong in your package management. That's why I mentioned the downloadable binary for unetbootin. Just download it, open a terminal, change into the directory you downloaded it into and call it with 'sudo QT_X11_NO_MITSHM=1 ./unetbootin-linux-702.bin'.

Holger

---

### Post by kbarber3 on 2022-10-06
So far so good... it looks as if I have a bootable USB stick.  Quite an achievement today as I have a nasty cold and am having trouble installing myself in a chair!  I did try it out to be sure and, booting to safe graphics, got the error 'mtd device must be supplied (device name is empty)', but it seemed to continue OK after sitting there for a while so I'm hoping it won't be too much of a problem.  If anyone knows different, please shout before I do something very silly.

Holger: Thank you for your help.  I did have a look where you suggested and followed through a bit, but to be honest I couldn't work out quite what I had to do (this is where my lack of knowledge becomes a serious problem).  You may have guessed that, as 'tea for one' suggested upthread, I'm going to go for a clean install in any case... the nuclear option, but at least I should end up with something that doesn't then need huge amounts of chasing yet more faults down.  I hope!

Install will be tomorrow afternoon, when my week's work has finished and I have time to do it without too much pressure.  Hoping the backup will do what's necessary; the first one I tried failed but I suspect that may have been because I had several applications (and probably some data files) open at the time.  Hope so anyway; again, if anyone thinks I'm going to make a complete ass of myself, please shout.

I'll be back tomorrow afternoon, all being well, either with results or to ask for yet more help.

Wish me luck...

---

### Post by Impavidus on 2022-10-07
> **kbarber3 said:**
> ... got the error 'mtd device must be supplied (device name is empty)', ...
That's a known "issue" with 22.04. It's not really an issue, just a spurious notification. It has been fixed for installed systems, but the live disk will only be updated in January (unless some alarming bug appears).

> Hoping the backup will do what's necessary; the first one I tried failed but I suspect that may have been because I had several applications (and probably some data files) open at the time.
I don't know the details of your backups. You do, I hope. The important bit is that you can get to your files after you wiped your hard drive, so you must have a copy on some external drive or in the cloud. Sensitive data shouldn't be uploaded to the cloud (and certainly not to free cloud services), unless encrypted before upload. And make sure you store the encryption key on an external drive, or on paper.

---

### Post by kbarber3 on 2022-10-08
So far so good(ish).

First, huge thanks to 'tea for one', Impavidus and Holger_Gehrke for all the help so far.  I now have 22.04 working, seemingly all OK.  Reason it's taken me so long to surface is that ensuring I had everything backed up took over 8 hours!

There are one or two little wrinkles I still have to sort out, like some applications that don't seem to want to install.  Perhaps someone with better knowledge of etiquette than me can say whether I'd do better to continue this thread (presumably others may come across the same issue having re-installed) or start new threads for each of the issues that arise?

---

### Post by tea for one on 2022-10-08
It would be better to start a new thread with each problem.
If you mention in the title the application causing an issue, then members with knowledge of the app will certainly jump in with advice/suggestions.
You can always provide a link to a certain post in this thread if you think it is pertinent.
Glad that progress has been made.

---

### Post by kbarber3 on 2022-10-10
Thanks, I'll do that.  Grateful (again) for all your help, doubtless we'll be in touch again as I come up against my own ignorance!

---

