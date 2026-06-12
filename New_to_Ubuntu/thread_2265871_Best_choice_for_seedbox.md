---
title: "Best choice for seedbox"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by ja-finn on 2015-02-18
Hi

I want to set up a linux seebox VM running VPN and share the downloaded files with the host which in turn will distribute the finished files on my network. I don't have much experience with linux but am a fast learner. The reason why I two machines is that then I can separate the torrent traffic over the VPN and the distribution of finished files over a non VPN network (due to speed).

What I'm wondering here is if anyone has any suggestions to what distros to choose for each of the machines? Pros/cons?


I'm thinking running Ubuntu on the host and Ubuntu server on the VM with OpenVPN and uTorrent/Azureus (due to support of labeling which makes it easy to script how to handle the files when finished)

---

### Post by bapoumba on 2015-02-18
How big are your files, and which type ?

---

### Post by ja-finn on 2015-02-18
> **bapoumba said:**
> How big are your files, and which type ?

Do you mean for the torrent files? Ranging from 100 MB to 10 GB, various types. I realize that seedbox might have been a poor choice of words but I am not looking for an online service.

---

### Post by sandyd on 2015-02-18
> **ja-finn said:**
> Do you mean for the torrent files? Ranging from 100 MB to 10 GB, various types. I realize that seedbox might have been a poor choice of words but I am not looking for an online service.
No need for VMs

1. Create two sets of folders. One will hold downloading files, and one will hold downloaded files.
2. Bind torrent client to the VPN interface
3. Use a torrent client with support for placing different files in different folders based on tag. I suggest rtorrent or deluge.
4. Create a script to copy files from the 'downloading' folder to the 'downloaded' folder. Some torrent clients can do this.
3. Then, use a sync tool such as btsync or syncthing to distribute the 'downloaded' folder. In syncthing, disable lan sync, and traffic will be forced to pass through public interface. You can bind to the public interface with syncthing as well

---

### Post by ja-finn on 2015-02-18
Ok, that sounds simple enough, but I thought that the VPN forced all the traffic through the same interface. Maybe that's just a Windows thing.

How would this be with regards to DNS leaks and such? 

I would have thought that the simplest thing would be to block all traffic if the VPN goes down? The host is not at my house so with a VM I would still be able to remotely log on to the host and restart the VPN.

---

### Post by sandyd on 2015-02-18
> **ja-finn said:**
> Ok, that sounds simple enough, but I thought that the VPN forced all the traffic through the same interface. Maybe that's just a Windows thing.

How would this be with regards to DNS leaks and such? 

I would have thought that the simplest thing would be to block all traffic if the VPN goes down? The host is not at my house so with a VM I would still be able to remotely log on to the host and restart the VPN.

Depends on how much work you are willing to do, might be easier with VM or without. Its a personal preference.

With VM, create one VM, with one interface

Setup VPN in VM along with torrent client

Setup syncthing in the VM, get it to bind to the internal interface ip (not the VPN one)

Setup syncthing on host. Syncthing on host will automatically sync with Syncthing on VM. You can then add additional Syncthing nodes outside of the server and the Syncthing server on the host will distribute files

---

