---
title: "Permanent shares - seems impossible in Ubuntu for a newbie?"
date: 2022-11-01
forum: New to Ubuntu
---

### Post by anderson9876 on 2022-11-01
Hi all
Have been struggling for a few weeks with this, as yet, can't figure it out. If some kind person can point me at a tutorial that works (the Ubuntu wiki for example doesn't work), that would be most welcome.

The problem - I have a Synology NAS box and I'd like to do like Windows does, and share the contents of the NAS to my Ubuntu devices. 
Synology is a closed system so although I can SSH to the box, I can't really tinker with the underlying setup other than what they provide. 
 
So far I've been trying to use SMB and NFC to share drives. SMB is a dead loss, Dolphin can see the NAS box SMB but as soon as I go to it, it insists on appending '.local' to the NAS name so fails with 'folder does not exist'.  
If I try and map shares directly to SMB in fstab, similar lack of success, permission denied (the mounts and so forth are correctly setup as far as I can see, but can't be). 

With NFC, I've got as far as mapping the drives successfully on the fly, but as soon as I transfer into fstab, I'm toast, and the mappings don't work. So, am thinking, maybe the only way of doing this is to write a script to run on startup to map the drives under NFC and leave it at that?

thanks in advance!

---

### Post by oldfred on 2022-11-01
You say NFC, do you mean NFS?

I use NFS, but as temp mounts to transfer data between systems. Others have told me it would just be easier to use SSH.
But I had already created scripts to create & mount partitions. And my new install scripts installs NFS & updated NFS settings in  /etc/exports with default paths to use.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)
[https://saywebsolutions.com/blog/mounting_synology_nas_shared_folder_nfs_ubuntu_16_10](https://saywebsolutions.com/blog/mounting_synology_nas_shared_folder_nfs_ubuntu_16_10)

---

