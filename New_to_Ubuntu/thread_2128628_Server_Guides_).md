---
title: "Server Guides :)"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by ally_uk on 2013-03-23
Hey guys I have a spare AMD dual core shuttle currently doing nothing so I am thinking of slinging ubuntu server on it and getting a few services configured.

I am a noob I am not a programmer and I am coming from a Windows world.

The initial goals I have are

Samba server sharing data to Windows machine I also want to learn about how to secure shares and create users who can access shares.

Torrent server having the ability to download torrents and serve them up via the samba shares.

Some kind of media streaming to both PS3 and Windows 7 PC

FTP what is the best FTP service to use? I need a guide that explains how to set it up how to secure and how to create users and shares.

Some easy method of backing up my samba shares

If somebody has done something similar or can point me in the direction of noob friendly guides that would be most helpful like I said before I am not a programmer or a command line genius I just want clear concise steps to get stuff configured and working

Or is this to much to ask? :)

---

### Post by Doug S on 2013-03-23
I would recommand the [Ubuntu server guide ]("https://help.ubuntu.com/12.10/serverguide/index.html")as your main reference. Myself, I prefer the [PDF]("https://help.ubuntu.com/12.10/serverguide/serverguide.pdf") version, so that I can print pages and make notes on them. It contains many links to further reference materials. The links are to the 12.10 version, but I would use that version even if installing 12.04 as some changes haven't been backported.

---

### Post by ibjsb4 on 2013-03-23
You can find a lot of information [here.]("https://help.ubuntu.com/community/NewDocs")

---

### Post by sandyd on 2013-03-23
Some stuff to point you in some sort of direction ;)
> **ally_uk said:**
> Hey guys I have a spare AMD dual core shuttle currently doing nothing so I am thinking of slinging ubuntu server on it and getting a few services configured.

I am a noob I am not a programmer and I am coming from a Windows world.

The initial goals I have are

Samba server sharing data to Windows machine I also want to learn about how to secure shares and create users who can access shares.

Torrent server having the ability to download torrents and serve them up via the samba shares. - **Deluged is pretty easy to config - after you install deluged, just see the [thinclient]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient") guide. Don't use rtorrent unless you want to work a bit**

Some kind of media streaming to both PS3 and Windows 7 PC - **[Plex]("http://www.plexapp.com/") - The app for android requires $, but is otherwise free. Some people have complained that plex and whatever torrent program they have are conflicting in ports - make sure that you set the port range in Deluged so that it does not include 3400**

FTP what is the best FTP service to use? I need a guide that explains how to set it up how to secure and how to create users and shares. - ** Depends really, theirs vsftpd, pure-ftpd, proftpd, not to mention many others... Personally, I would just use SFTP and get it over with**

Some easy method of backing up my samba shares - **rsync or rdiff-backup - where are you backing it up to?**

If somebody has done something similar or can point me in the direction of noob friendly guides that would be most helpful like I said before I am not a programmer or a command line genius I just want clear concise steps to get stuff configured and working

Or is this to much to ask? :)

---

### Post by Morbius1 on 2013-03-24
>  Samba server sharing data to Windows machine I also want to learn about  how to secure shares and create users who can access shares.
Someone above recommended the following HowTo series: [https://help.ubuntu.com/12.10/serverguide/index.html](https://help.ubuntu.com/12.10/serverguide/index.html)

I haven't gone through all of it it yet but I would caution you about the Samba specific sections:

_Samba File Server: [https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html)_

Parts of it are harmless but factually incorrect ( uncomment the "security = USER" section for example ). The biggest problem is the share it has you create will be inaccessible the instant you create another share that requires credentials to gain access. It's simple enough to fix but it really should have gone through some kind of peer review before it was published.

_Securing a Samba File and Print Server: [https://help.ubuntu.com/12.10/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/12.10/serverguide/samba-fileprint-security.html)_

There is one section about installing a package ( libpam-smbpass ). Unless this server is behind locked doors or is headless I would suggest doing just the opposite. If for some reason it's installed by default uninstall it. It's only function in life is to sync the Server's local users with the Server's Samba password database so that the usernames and passwords match. That means that all your network users can access the physical machine itself.

---

### Post by Doug S on 2013-03-24
@ Morbius1: Would you consider to enter a Launchpad bug report to detail your issues with the Ubuntu server guide samba chapter and other samba areas. There is one week left before the documentation freeze for 13.04. I think anyone that frequents these forums is well aware that you are a subject matter expert on Samba. The ubuntu server guide, is supposed to be the "official documentation", but is falling behind and is desperate for subject matter expert input.
Reference: [https://bugs.launchpad.net/serverguide](https://bugs.launchpad.net/serverguide)

@alley_uk: Sorry for the digression on your thread.

---

### Post by ally_uk on 2013-03-28
Guys I appreciate your help it really does mean alot to myself the eventual aim is to setup up a blog with Wordpress and document everything I do to give something back to people in a similar position.

I think I am going to tackle Samba first :) 

If anyone has anymore tutorials or Guides stick them in this thread I enjoy reading everyone

---

### Post by mastablasta on 2013-03-28
just a thought you can use a GUI such as Webmin to set up the server. 

or a GUI server distro such as Zentyal (Ubuntu based) or Openmediavault (debian based)

---

