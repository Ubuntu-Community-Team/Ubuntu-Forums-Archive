---
title: "Setting up a file server/media centre"
date: 2019-03-03
forum: New to Ubuntu
---

### Post by daleks on 2019-03-03
Hi,

I was hoping to get some advice on a little project. I have previously installed Ubuntu on old laptops to prolong their life so I'm not an absolute complete beginner, however I've never done anything at all advanced with Linux. I recently inherited an old windows tower and wanted to be a bit more adventurous with it. Before I just go and do whatever myself I thought I'd get some advice on whether what I'm doing is a good idea, and what I might want to think about when doing it.

The main thing I want the computer to do is to store all my files. Essentially I'd like to have a Google drive/OneDrive/Dropbox which doesn't hand my data over to dubious third parties. I'd like this to allow local copies of files to be worked on and re-uploaded in case I need to work offline. I would also like it to backup files off site on a regular (daily?) schedule to a friend of mine in another country. I would ideally like it to shutdown at night to save a bit of power, install updates etc. but send a warning when it does and allow this to be cancelled.

The secondary purpose I'm considering putting this computer to is mostly just for playing videos through my TV. I don't have a working aerial indoors so I've hooked the pc up to my TV with an old VGA cable. There's probably not much advice I need to do this, although an alternative way to control the desktop remotely would be nice without having to connect through VNC (e.g. can a phone be used as a remote mouse/keyboard in some clever way)?

So that's my idea. What I'd like to know is:

Is this a totally silly idea to use the one machine for these two purposes?
Should I do anything different to the standard install (e.g. are there extra partitions I should make, things I shouldn't install etc.)?
Are there any packages that I could install which would be good for doing the first task?
If there's not a good package to do this already, is there a good tutorial which explains how to set up a file server type system like this?

Your help is very much appreciated!

---

### Post by SeijiSensei on 2019-03-03
First, no you're not silly to do that at all. I've had a computer connected to my TV for years with video files stored there. Lately I moved those files to another server in my home and watch the videos over the network.

First suggestion I'd make if your TV supports it is to buy a [video card with HDMI out](https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%204017%204027&IsNodeId=1&bop=And&Order=PRICE&PageSize=36). I prefer NVIDIA.

In broad terms I have an arrangement similar to what you're looking to set up. My main server has a "[RAID-1 array](https://help.ubuntu.com/community/Installation/SoftwareRAID)," a pair of identical disks combined to look like one, where I store all my files. Everything is written to both drives simultaneously using this method. I also run a script every night that backs up the server, and files on some remote servers I manage, to a 4 TB external USB drive.

I share these files with my other Linux machines using the technology known as [NFS](https://help.ubuntu.com/community/SettingUpNFSHowTo). It allows me to treat server resources the same as if they were local to my machine. If you need to support Windows users as well, you'll need to look into [SAMBA](https://tutorials.ubuntu.com/tutorial/install-and-configure-samba).

Some devices like smart phones can stream using the DLNA protocol. I use minidlna for this purpose, but there are other DLNA servers out there.

There's a program called [KDEConnect](https://play.google.com/store/apps/details?id=org.kde.kdeconnect_tp&hl=en_US) designed to interface between Android phones and Linux computers. The Linux component is in the Ubuntu "repositories." With it I can remotely control [SMPlayer](https://www.smplayer.info/), my preferred video player which is also in the repositories.

---

### Post by CatKiller on 2019-03-03
> **daleks said:**
> The secondary purpose I'm considering putting this computer to is mostly just for playing videos through my TV. I don't have a working aerial indoors so I've hooked the pc up to my TV with an old VGA cable. There's probably not much advice I need to do this, although an alternative way to control the desktop remotely would be nice without having to connect through VNC (e.g. can a phone be used as a remote mouse/keyboard in some clever way)?

The most seamless way to do this (not necessarily for this project, because of the hardware requirements, but in the future) is to use something that has an interface suited for use at a distance, like [Kodi]("https://kodi.tv/"), controlled through [HDMI CEC]("https://en.wikipedia.org/wiki/Consumer_Electronics_Control"). CEC lets you use your normal television remote for navigation: your television receives the signal from your remote control and then turns it into commands that get sent along the HDMI cable. Kodi can also be configured as a [DLNA]("https://en.wikipedia.org/wiki/Digital_Living_Network_Alliance") UPnP client, so you can simply push media streams to it from any device connected to the network, such as phones, tablets, and so on.

You'd need to be using HDMI, and it needs to be supported by the devices at each end of the cable, and by the software. I've got a NUC connected to my TV that does this, although I needed to install a cheap accessory to enable it to properly interpret all of the available CEC commands. It works really well. My media is stored on a different [NAS]("https://en.wikipedia.org/wiki/Network-attached_storage") device, but it would work just as well with media stored on the [HTPC]("https://en.wikipedia.org/wiki/Home_theater_PC").

An alternative to using CEC is to add an infra red receiver to the computer itself, and having a specific remote control just for the computer. I believe people like using Harmony remotes for that.

As to using one machine for multiple purposes, that's fine. My NUC also runs two Minecraft servers and a Windward server, and uses Steam's In-Home Streaming to let me play games on the TV that are actually running on different machines elsewhere in the house. In your case, it's only the playing of media that requires any direct interaction: transferring files to it will be done from the other machines, and for configuration and maintenance SSH is the best option anyway.

---

### Post by mastablasta on 2019-03-04
i won't say what you should install. that's up to you. it looks like you have usage and services in mind and you didn't mention if you need a GUI or not.

there are a couple of project i would point you to, have a look at them maybe read a review or two or even try them out in virtualbox.

For server administration via web based GUI (you administer server through browser) have a look at projects like: Ajenti, Zentyal, Openmediabox, Nethserver
For file sharing have a look at: Owncloud, Nextcloud and Seafile
For media look into: Kodi and Plex

I don't think server should be shut down, unless you are off the grid and get solar power or something. server uses really low amount of power when idle. for the tasks you mentioned a RaspberryPi will do the work and i think it uses ridiculously low amount of energy. Even if you go with ye old tower, they have power management and would reduce power down to almost zero when idle. still, if BIOS is modern enough it is possible to setup the PC to shut itself down and turn itself back on at specified time.

security updates are done through "unnatended updates". these are super easy to configure. if you want it can send you an email notice. i set mine up to use gmail to do that.

Using a server you will have ports open. for that reason you need to harden it (fail2ban, monitor ports...) and use firewall. there are a couple of guides out there. here is a site with links to several good guides: [https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017](https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017)

you will also use SSH with keys and do all security updates automatically.

---

### Post by daleks on 2019-03-05
Thank you very much for your ideas and help guys, looks like I have a bit of research to do. I'll try and post back when I get a chance to try some of it out and if I have any more questions!

---

