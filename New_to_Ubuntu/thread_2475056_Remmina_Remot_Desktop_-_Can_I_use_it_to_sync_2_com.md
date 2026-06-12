---
title: "Remmina Remot Desktop - Can I use it to sync 2 computers"
date: 2022-05-15
forum: New to Ubuntu
---

### Post by jonfisher on 2022-05-15
I just noticed Remmina Remot Desktop in 22.04 lts - Can I use it to sync 2 computers?  I'd love a program that would Sync *everything* on my desktop and laptop, regardless of which was used last, to simply sync all files from one to the other...

If not Remmina, then what could do it?  Especially for someone that can't code and predominately uses the GUI

Addendum:  Actually, I would be very pleased if I could simply sync one folder between the 2 computers.  Ultimately, it would be great if the sync"ing" program could automatically recognize the latest used, or saved, file/folder(s) within that folder and sync it to the other computer, regardless of which computer was used last....

Addendum 2:  I came across some reading, that *perhaps* one of these programs could pull it off.  Anyone that has experience with any of these, please do comment.  Also, please note that I have no server of my own, I just own a desktop and a laptop    

Copy and pasted from the web:


[LIST]
[*][Unison]("http://www.cis.upenn.edu/~bcpierce/unison/")  - as mentioned by others, this is run manually, but is very fast,  reliable and effective. Requires both machines being synchronised to be  on at the same time. It has a nice user interface to allow you to deal  with the almost inevitable conflicts, and tracks and propagates  deletions correctly. The graphical app/package is called unison-gtk.
[*][OwnCloud]("http://owncloud.org/") -  Cloud storage run on your own server. You'll need a machine to leave on.   Requires a reasonable amount of setup. Runs a full Apache 2 webserver  and an SqlLite or MySQL database on the server. Works similar to Dropbox  with a desktop client, but the server is under your control. edit :  OwnCloud has recently gone through some changes in how the project is  run, and now has a new fully open source (ie no closed source  'enterprise' edition) under the guise of [NextCloud]("https://nextcloud.com/"), (see this [youtube interview]("https://www.youtube.com/watch?v=iMfokaX2r8g") with the original OwnCloud developer for more details).
[*][SparkleShare]("http://sparkleshare.org/")  - uses git to keep files in sync. According to the homepage: good for  many smaller files, not good for lots of large files such as music or  photo collection.
[*][Seafile]("http://seafile.com/en/home/") - Provides a server component you can install on a local machine. Seafile uses a data model [similar to git]("http://manual.seafile.com/develop/data_model.html")  for tracking changes. Provides sync clients for desktops, tablets and  smartphones. A blog post describing setup can be found at [http://openswitch.org/blog/2013/07/18/installing-and-configuring-seafile-on-ubuntu-12-dot-04/](http://openswitch.org/blog/2013/07/18/installing-and-configuring-seafile-on-ubuntu-12-dot-04/)
[*][Osync]("http://www.netpower.fr/osync")  - "... bidirectional file synchronization tool written in bash and  based on rsync. It works on local and / or remote directories via ssh  tunnels. It's mainly targeted to be launched as cron task" (text from  the website)
[*][PowerFolder]("http://sourceforge.net/projects/powerfolder-/") - java based GPL v2 project. Main website pushes commercial offerings so it's not clear how to use the provided .jar file.
[*][Rsync]("https://rsync.samba.org/") -  fast and effective and been around for decades, however it doesn't keep a  history so you have to choose a direction to decide whether a file is  new or deleted. Graphical tools are available such as [gwRsync]("http://www.opbyte.it/grsync/screenshot.html").
[*][Lsyncd]("https://github.com/axkibe/lsyncd") - monitors folders/files to trigger rsync replication
[*][dvcs-autosync]("https://www.mayrhofer.eu.org/dvcs-autosync") - written in python, uses git to store and share changes between machines, and XMPP to communicate changes.
[*][git-annex]("http://git-annex.branchable.com/") - command line tool for shunting files around, based on git. There's an illustrative walkthrough here: [http://git-annex.branchable.com/walkthrough/](http://git-annex.branchable.com/walkthrough/)
[*][Tonido]("http://www.tonido.com/") -  freeware. Provides a desktop app that will share files to other devices.  Also provide commercial cloud offerings, and the TonidoPlug plug  computer.
[*][BitTorrent Sync]("http://www.bittorrent.com/sync")  (freeware) - peer-to-peer file sync based on BitTorrent. I don't know  much about this as I won't be using it due to it not being open source  and not trusting it to keep my data within my LAN, feel free to edit  this answer with better information / real experiences.
[*][SyncThing]("http://syncthing.net/") -  Developed as an open source alternative to BitTorrent Sync. It currently  lacks some of the advanced features of BitTorrent Sync, such as  untrusted peers. It is under active development.
[*]Commercial hosted services such as dropbox, ubuntu one, google  drive, apple iCloud are all quick cheap and convenient, however they all  require trusting a company with all your data, and need a reasonably  fast internet connection.
[*][Git]("http://www.git-scm.com/") / [subversion]("https://subversion.apache.org/")  - Use a source control system directly. Completely manual and can be a  little complex but popular approach with some users familiar with these  systems from using them as programming tools.
[*][CloudFS]("http://cloudfs.org/") - syncronise a whole filesystem, cluster technology based
[*]NFS mount - basically your home lives on one machine and you  access it over the network, no good for laptops you take with you. More  info: [http://www.linuxjournal.com/article/4880](http://www.linuxjournal.com/article/4880)
[/LIST]

I'm already guessing that this may be darn near impossible for someone, like me, that has no programming/coding knowledge...

  [HR][/HR]

---

### Post by TheFu on 2022-05-16
I use **rsync**.  **grsync** is the GUI.  You can't sync everything, since they are different machines, but you can push the newer file from A-->B and from B-->A.
rsync is how I push my keepassxc database and TODO lists to many different systems every night.

I my mind, my "desktop" is the system of record. The sync happens a little after midnight (local time), so if I've made any changes on any other platform, I need to push those changes to the "desktop" system before midnight .... or if I'm traveling with the laptop, then my laptop won't get updates on the desktop (there won't be any - I'm gone), so when I return home, if I've made any changes, I need to push that file to the desktop before midnight that day or they will be lost.  Well, not really lost, since I have daily, versioned, backups, but ... nobody likes to go through backup sets to get a file that was corrupted/lost.

osync is interesting, but I've not used it. Same for lsyncd. I've not used it.  Immediate sync seems like a good idea if you are always connected, but by definition, your laptop won't always be connected. That can lead to strange situations.

These tools don't merge the differences in files, if the file is changed on both the target and destination. That's a different tool and a non-trivial problem to handle for hundreds of non-text files.

Lots of people use SyncThing.  I looked at it and decided that rsync already did what I needed.

Be careful using any git/dvcs tools. Those are really meant for text files, not documents. Programmers use them.

Seafile, Owncloud, Nextcloud are all home-server things.  If you have a Raspberry pi v2 or newer, any of them could be used as a central server. If you leave your desktop on almost all the time, it can be a server too.  I've been running a nextcloud server for 4-6+ yrs. The desktop Linux integration sorta sucks.  On Android, it works better than other options I've used.  I use my nextcloud server from android to pull/refresh music files, ebooks, and audiobooks when I know I'll be stuck somewhere with my tablet.  Had jury duty a few months ago.  Loaded up the tablet because jury duty is mostly sitting around in a room, waiting to be called before any trials happen.  Since I can pick out a guilty person in a snap, I'm seldom picked for a jury. Still, 1-2 full days sitting around a courthouse means I need music and reading materials or podcasts. Those are available through my nextcloud instance - when I'm at home. We keep shopping lists, by store, in nextcloud as a note file.

If the files you plan to sync aren't sensitive - you'd be happy to share them on twitter - then you can use any of the cloudy storage providers - like dropbox (or whatever MSFT/Google/Apple/etc... have).  Beware that almost all of these aren't secure, so if you want security, then you'll need to add it yourself. Don't trust their client that claims to encrypt stuff and definitely don't trust any browser addon that claims to encrypt files as they are put in the cloud.  Even filenames without access to the content breaks our privacy.

There are lots of tutorials for using rsync.  You can create two 1-line scripts to be run from the laptop to push and pull the files as you choose.  Rsync is one of the top 5 Unix tools that I think everyone should learn to intermediate level. ssh, bash, vi, are the main others.  

The command to copy **newer** ~/Documents FROM the desktop TO the laptop, replacing any files that have a newer timestamp on the desktop, is:
Run this from the laptop, after you have ssh setup from the laptop to the desktop.
```
$ rsync     -avz     --progress      xx.xx.xx.xx:~/Documents/      ~/Documents/
```
[LIST]
[*]xx.xx.xx.xx is the IP address for the desktop. It would be best if that were a static IP, not DHCP.
[*]I've assumed the username on both systems is identical.
[*]I've assumed that the laptop can ssh into the desktop. That is mandatory. It is just 2 commands, not including the package installation on both systems.
[/LIST]

To copy the any **newer** files from the laptop back to the desktop, use
```
$ rsync      -avz   --progress      ~/Documents/      xx.xx.xx.xx:~/Documents/
```

Files will be replaced if they have the same name and are newer.  Files that don't exist on the target will be created.

rsync has many options to get the behavior you could use. Many, many, options.
There is also a --dry-run option to see what would happen, without doing anything.

grsync is basically the same, just with a GUI. I think you'd probably like that, but you still need to setup ssh on both the laptop and desktop first.

---

### Post by jonfisher on 2022-05-17
Thank you so much for your time in typing up that tutorial.  It is easy to understand and just what I want.
I really do appreciate you taking your valuable time to help me!

---

### Post by TheFu on 2022-05-18
> **jonfisher said:**
> Thank you so much for your time in typing up that tutorial.  It is easy to understand and just what I want.
I really do appreciate you taking your valuable time to help me!

Well, I saw that you'd done some research and that the research was very reasonable. It made me want to be as helpful as possible.

I should have said that I've never used grsync either.  I'd rather have a 1-5 line script for stuff like this, so it can be automated easier.  GUI programs don't automate easily.  Stuff like rsync does.

---

### Post by kurt18947 on 2022-05-19
There is at least one other GUI front end for rsync that seems pretty straightforward, it's called "Lucky Backup" found in the repositories. Don't be afraid of the name:), it has been reliable for me. It will either sync two folders or create a folder of backed up data within another folder on a second machine. I used the sync function, I don't know if it has any sort of differential backup. I found it very simple to use. I've used Grsync as well, they seem pretty similar.

---

