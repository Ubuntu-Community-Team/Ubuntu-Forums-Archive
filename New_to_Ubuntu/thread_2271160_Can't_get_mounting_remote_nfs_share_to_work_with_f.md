---
title: "Can't get mounting remote nfs share to work with fstab"
date: 2015-03-27
forum: New to Ubuntu
---

### Post by MikeyTT on 2015-03-27
Hi
I'm friarly new to linux in its entirety, but I'm learning. However I have a real problem I cannot seem to solve. I was using the Hyper-V box as an nfs file share, but I kept getting odd issues, so I thought I would just serve these files up via a linux box. BTW references to reddwarf are the old server name, so will eventually be replaced once I get it working.

I have a virtual machine running on Hyper-V, which has a passthrough drive attached, so I get a 2nd hdd in linux.

In my fstab file I have the usual entries, and one I have added myself to add in the NTFS formatted 2nd hdd:
```
UUID=CC94999A9499881A /mnt/mediadrive ntfs-3g uid=1000,gid=1000,dmask=000,fmask=000,sync,rw 0 0
```

This I've then shared over nfs having followed some other great guide out there:
```
/mnt/mediadrive        192.168.0.0/24(rw,sync,insecure,no_subtree_check)
/mnt/multimedia        192.168.0.0/24(rw,sync,insecure,no_subtree_check)
```


Due to an issue with having mount commands in fstab, and a timing issue with the main mount, I read a post that suggested these go into a mount-bind.conf file in /etc/init. So I have this mapping the Multimedia folder on the drive to a folder in /mnt. I know it's not absolutely necessary, but I wanted to access it via a different share.
```
description "bind"

start on stopped mountall
script
  mount --bind /mnt/mediadrive/Multimedia /mnt/multimedia
end script
```

All this appears to be working fine and I can manually bind from one of the other linux machines, and also my Win 8.1 box.

What I can't seem to fathom though is how to configure the fstab on the client side to automatically map the share. I have tried a few, but they all fail to map/bind:
```

#original cifs mapping
//192.168.0.200/Multimedia    /mnt/reddwarf_multimedia        cifs    username=xxx,password=xxx,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

#nfs mappings I've tried
//192.168.0.55:/mnt/multimedia     /mnt/reddwarf_multimedia nfs auto,noatime,nolock,bg,intr,tcp,actimeo=1800 0 0
//192.168.0.55:/mnt/multimedia     /mnt/reddwarf_multimedia   nfs defaults 0 0
//192.168.0.55:/mnt/multimedia     /mnt/reddwarf_multimedia nfs rw,hard,intr 0 0
```

I've been banging my head against this for a few hours now, and I'm really at the point where I need a pointer or tow from you more advanced linux peeps out there.

---

### Post by nerdtron on 2015-03-28
So you have  no problems mounting it manually? only in fstab?

You need to add "_netdev" as the first option on mount options of your share since the nfs should wait for the network first before mounting the share.

---

### Post by DuckHook on 2015-03-28
> **nerdtron said:**
> ...You need to add "_netdev" as the first option on mount options of your share since the nfs should wait for the network first before mounting the share.This used to drive me crazy because occasionally even *_netdev* would not work. Sometimes, the system hung at boot due to (I'm guessing) two cross-dependant processes waiting for the other to complete. Most other times, the NFS call would time out after four minutes thus allowing the system to proceed with the rest of its boot process, but even then, the failed initial NFS call had already hooked the /mnt directory such that *sudo mountall* would subsequently fail. I tried many different suggestions from this and other forums before discovering a much better solution: *autofs*. Haven't used *fstab* since.

@OP

*autofs* is a mount-as-needed filesystem service. So, at boot, none of your NFS shares are mounted and therefore won't get in the way of your boot-up. However, upon calling a remote file, the NFS share is automounted then and only then, and the file is served as normal. If all files are closed, no connection is open, and no further activity is noted to the share for 10 minutes, then *autofs* also automatically unmounts the share. This has the added advantage of allowing your server to go back to sleep when not in actual use (if you have it set up that way). Saves tons of wear and tear on your server HDD and your electrical bill. Most of all, you never have to deal with the chicken-or-egg problem of mounting an NFS share at boot before the network is ready. Instructions for *autofs* [here]("https://help.ubuntu.com/community/Autofs").

---

### Post by MikeyTT on 2015-03-28
I am now so happy and so annoyed it's quite staggering.

After calling it a night and looking afresh this morning, I've just found the problem in about 2 minutes.

I had tried these commands which were based on the cifs entry I had originally.
```
#original cifs mapping
//192.168.0.200/Multimedia    /mnt/reddwarf_multimedia        cifs    username=xxx,password=xxx,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0


#nfs mappings I've tried
//192.168.0.55:/mnt/multimedia     /mnt/reddwarf_multimedia nfs auto,noatime,nolock,bg,intr,tcp,actimeo=1800 0 0
//192.168.0.55:/mnt/multimedia     /mnt/reddwarf_multimedia   nfs defaults 0 0
//192.168.0.55:/mnt/multimedia     /mnt/reddwarf_multimedia nfs rw,hard,intr 0 0
```

This is the problem: "**//**" at the start.

These belong in front of a windows based cifs share, as I understand it, but not a linux based nfs share. As soon as I removed these from the start of the line the top mapping with the many parameters worked first time. 

Thanks for the pointers and I will look into autofs, but for now I'm as pleased as can be, just a shame I spent several hours mashing my head against the wall :-)

---

### Post by DuckHook on 2015-03-28
> **MikeyTT said:**
> ...This is the problem: "**//**" at the start...I'm rather annoyed at myself too. So intent on singing the praises of *autofs* that I didn't even bother looking at that. Seems obvious once you catch it.

Good Luck and Happy Ubuntuing!

---

