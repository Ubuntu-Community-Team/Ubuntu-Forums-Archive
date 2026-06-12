---
title: "Setting up open media share. guide wanted."
date: 2021-01-12
forum: New to Ubuntu
---

### Post by DeathByDigital on 2021-01-12
Hello. After several years trying, im back at trying some more.
Every time ive tried, i always get broken by either wrong version on some software in the guide, files not where the guide sais they are, the guide assumes i know some basic Linux, or something else breaks the guide for me.
(searching Google and other gives often old and outdated guides)

This post is just asking: **Does anyone have a new updated guide to set up Ubuntu server, with samba for a Full open media share to my home network?**  
pref for win/linux -if lucky /android/smartphones too. --just a big NAS.

Ive got a HP DL380g7 2x4core 72gig ram with 2x12 storagework bays id thought id use for this.  
(Servers are on Vlan XX and  Guests have Wifi without access to internal network, so ive got no problems with open share to make it easy/work)
if we are going to make it harder, i can ofc set up private folders for family members + open share.

(got a few different disks set up in the raid) and they show when using lsblk. so everything seems ok for a fresh start.
i don't even know if i should just use one disk for Ubuntu install, and then mount the rest as media1,2,3,4 or share1,2,3,4 after install.  

Only time i got a share working from Linux was years ago with GUI Ubuntu desktop and Natilus... kinda easy klick and share, and it worked..  

Ive got another server running Proxmox where one of the nodes run Ubutnu server and Nextcloud.  But that works out of the box with gui, so i see and understand what is happening.
If there is a GUI software id assume id get that easier.... (share program AKA Nextcloud)

Still if someone have relevant and updated guides for learning old dogs new tricks, either basic how to mount disks, file system, or a "Linux for dummies" guide id appreciate it.

---

### Post by CelticWarrior on 2021-01-12
> **Does anyone have a new updated guide to set up Ubuntu server, with samba for a Full open media share to my home network?**

Not really.
Network sharing hasn't changed that much over the years.
You're making it more difficult than it needs to be. Start by NOT using Ubuntu server, use the same Ubuntu desktop. There's really not many differences except the server edition is mostly geared towards headless installation (no GUI). Unless the target computer is so underpowered to the point that having a desktop environment running makes a difference, there's no point in using "server" at home.

> [COLOR=#000000]Only time i got a share working from Linux was years ago with GUI Ubuntu desktop and Natilus... kinda easy klick and share, and it worked..[/COLOR]

Yes, of course.
In "server" the end result is indistinguishable. The difference is setting things up in command line only. And it's all there is regarding what you're asking about here. But is it the best way to serve media in the context of a home network? Probably not.
I would be using dedicated software for that, like Kodi, Emby, Plex, etc. For media you actually don't need any of the traditional folder/files network sharing. It can be used as you already know but it wasn't designed for media files (those didn't exist, in a currently recognizable form, back then when network sharing started to be used) but for collaborative networked tasks where serving files "as is" just like they were in a local drive was the goal. The thing is, for media content, serving files "as is" often isn't the best way. The aforementioned software can transcode in the fly to a compatible format for the target device, the media player. This means they will work in situations where the media player for some reason (old software, etc.) doesn't support the file format and/or codec of the original file.

---

### Post by ActionParsnip on 2021-01-12
Why not setup an NFS server rather than Samba? Its modern and will work across your devices. If the server is for video "media" then something like Plex will serve you well.

I suggest a separate drive or partition for your media. You could even be a spinny drive (Cheaper per gigabyte) to store your media and keep the OS on a small cheap SSD

---

### Post by DeathByDigital on 2021-01-12
Thank you for the reply Changan.. 
ill go to desktop and i can install RDP and OpenSSH server on it just for fun. (because i kinda like to fiddle around and learn something)
Trouble with linux is all the different variations, when you read guides and try stuff, even basic codes does change from flavors, and it gets a mess.
Ive kinda ended up with ubuntu and Mint)  
Still id like to some day understand some basic commands, figure out how "disk space" works -as of now its kinda floating with mount points and disks/diskspace...

So guides are always welcome. 
(pref those guides to help those who have been at windows and plug and play for too long :D )  
Been at it so long that i remember we used to edit Autoexec.bat and command.com -so im troubled with thinking windows way :( and i know that is wrong.

---

### Post by DeathByDigital on 2021-01-12
[[COLOR=#000000]ActionParsnip[/COLOR]]("https://ubuntuforums.org/member.php?u=1079078")[COLOR=#000000] :  ive been looking at Freenas, and other solutions,  there is also a way to install synology NAS OS on a computer. 
Ive probably made it more difficult than it needs to be. I pretty much want my disks to show up on my network. If lucky from Linux, Windows, smartphones, and smart TV's
But beeing a amateur on Network and share, i usually dont know where the chain breaks...  (say win10 and smb1 not active for an example)

So NFS is kinda what im looking for...  Did try XMBC years ago, and Kodi isnt made to be on the server side as i can figure? ofc i can Install KODI on the computer if that works easier? 
Plex might be better of what ive read. but not free?[/COLOR]

---

### Post by CelticWarrior on 2021-01-12
Plex was mentioned by me indeed but for completeness only, it wasn't an endorsement.
I prefer Emby, the free version works fine for 98% of usage scenarios. Some people may want the "pro" features though.
And Kdi can be configured as "media server", quite easily actually, but you'd need to have it running (GUI included) in the machine serving whereas Emby works as a headless server and can be managed with any web browser.

---

### Post by ActionParsnip on 2021-01-12
[https://www.tecmint.com/install-nfs-server-on-ubuntu/](https://www.tecmint.com/install-nfs-server-on-ubuntu/)

Nice and easy

---

### Post by DeathByDigital on 2021-01-12
Thanks alot for replies..  
I dont mind trying a few.. (kinda is expected as learning by doing)
Ill try the latter link from ActionParsnip and download Kodi and Emby to see what they bring.

---

### Post by SeijiSensei on 2021-01-12
If your primary application is media sharing, I suggest using minidlna. It uses the DLNA method and works with most any device you have. On Android, for instance, you can use BubbleUPnP as the DLNA client with MXPlayer. VLC includes a DLNA client and runs on most platforms including Windows and Linux. Last I looked Windows Media Player is DLNA-aware as well. Also many smart TVs have DLNA clients.

After installation, all you need to do is define the locations of the files to be shared in minidlna.conf. Here's mine:

```

# set this to the directory you want scanned.
# * if you want multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to specific content types, you
#   can prepend the types, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
#   + "PV" for pictures and video (eg. media_dir=PV,/home/jmaggard/digital_camera)
media_dir=V,/media/raid/Video
media_dir=A,/media/raid/Music
media_dir=P,/home/seiji/Pictures

```

---

