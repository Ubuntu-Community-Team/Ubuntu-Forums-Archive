---
title: "Sharing files between Ubuntu 18.10 with Cinnamon and Windows 19"
date: 2018-11-24
forum: New to Ubuntu
---

### Post by jbcohen on 2018-11-24
How do I do this?

---

### Post by TheFu on 2018-11-24
Never heard of Win19 and there isn't any way we can predict what will happen in the future.

But, you can use almost any file sharing method following standards to share files from a Linux system to almost any other computing system available.
* NFS
* CIFS / Samba
* sshfs
* sftp
* scp
* rsync
* Owncloud/Nextcloud
* Seafile
* DLNA / MiniDLNA / PlexMS / and 
* 10 others

On the same LAN, most people choose to use CIFS to share files with Windows.
NFS is how Unix-to-Unix systems share files.
Over the internet, I'd push for using sftp if you don't want to setup a full VPN. Do not allow paswords, allow only ssh-keys or ssh-certs to be used for authentication.

But the choices are yours.  The GUI you are running doesn't matter at all, because using a GUI to setup sharing is almost always a bad idea that leads to security risks and terrible performance.

If you want files on Windows to be shared with Linux, that would almost certainly be CIFS.  Almost all Linux file managers can browse the network and location CIFS shares.  You might need to install some samba-client packages, but it depends no the file manager you want to use.  If you want to just mount the CIFS locations for use by anyone on the Linux machine like it was local storage (mostly), then use the smbmount tool or modify your /etc/fstab or use autofs.

Again, the choice is yours. Once you decide which method you'd like, ask and there is probably an Ubuntu-specific how-to guide available.

---

