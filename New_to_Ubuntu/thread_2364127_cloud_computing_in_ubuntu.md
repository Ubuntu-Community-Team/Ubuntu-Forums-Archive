---
title: "cloud computing in ubuntu"
date: 2017-06-19
forum: New to Ubuntu
---

### Post by linuxprj on 2017-06-19
what is cloud computing in Ubuntu ?
how it work application of it?

---

### Post by TheFu on 2017-06-19
It depends. What do you want to accomplish?  Running your own cloud services? Consuming services from other-people's-computers?
Server? Client? Desktop? 
Have you done any prior reading on the subject? There are thousands of articles about each of these things.

Ubuntu MAAS: [https://docs.ubuntu.com/maas/2.1/en/](https://docs.ubuntu.com/maas/2.1/en/)
[https://www.ubuntu.com/cloud](https://www.ubuntu.com/cloud)
[https://www.ubuntu.com/cloud/openstack](https://www.ubuntu.com/cloud/openstack)
[https://askubuntu.com/questions/78876/how-to-set-up-my-own-cloud-server](https://askubuntu.com/questions/78876/how-to-set-up-my-own-cloud-server) - I use a mix of self-hosted, private, cloud services. Including:
* Nextcloud (plus news addon)
* Zimbra (MS-Exchange replacement + much more)
* email gateway
* Plex Media Server
* Wallabag
* NX remote desktops
* openVPN (both clients and server)

Also use KVM + virt-manager + libvirt to host many virtual machines across a few physical devices.

Since I don't use centralized, public, free, services, I cannot say how any of those work (or don't work) from Ubuntu.  Nextcloud works well from Ubuntu and Android clients. Same for Wallabag, Zimbra, Plex.  Plus much of my normal, daily, use is through ssh services like ssh, scp, sftp, sshfs, and ssh-SOCKS proxy.

So ... what part of "cloud" interests you?

---

