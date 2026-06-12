---
title: "Upgrade woes-NFS/VMware"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by longboneslinger on 2008-05-02
I just upgraded my lappy. Its an Acer Aspire 5315-2153. It was working flawlessly. Note the word was.

I had filesharing, nfs and vnc set up to transfer files from the lappy to my desktop. The desktop is still using 7.10 and I'm now very hesitant to 'upgrade'. I can't touch the desktop and the desktop shortcut on my lappy is gone. When I try to log on in nfs, vnc or remote desktop it's unable to resolve or find the disk. I havent been able to mount the remote folder. It reports that that the addy isn't in fstab. I checked and it's still the same.
As far as I can tell, all my settings in /etc/fstab and /etc/networking/interfaces and everywhere else are unchanged. I just cant connect. It took me a week to get it all up and one upgrade to kill it all.

Here's fstab:
> # /etc/fstab: static file system information.

Huge TIA,
bone
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1bdb4430-518c-4d9a-81fb-ad7824c7cfd5 /               ext3    defaults,erro$
# /dev/sda5
UUID=4e2a1203-d4b6-4b0a-8e8f-1c4573c775f1 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/home/bone      192.168.1.101/255.255.255.0 nfs (rw,async,no_root_squash,subtree_check)



Here's /etc/exports

>   GNU nano 2.0.7             File: /etc/exports                                 

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/home/bone      192.168.1.101/255.255.255.0(rw,no_root_squash,async)



I forget off hand what else I had to edit but but all appears to be the same. I was functional before the upgrade and now not. Someone please help the gnoob.

---

### Post by longboneslinger on 2008-05-02
Here's a little extra info. this is the output of rpcinfo:

>   program vers proto   port
    100000    2   tcp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  52703  nlockmgr
    100021    3   udp  52703  nlockmgr
    100021    4   udp  52703  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  36860  nlockmgr
    100021    3   tcp  36860  nlockmgr
    100021    4   tcp  36860  nlockmgr
    100005    1   udp  45024  mountd
    100005    1   tcp  56712  mountd
    100005    2   udp  45024  mountd
    100005    2   tcp  56712  mountd
    100005    3   udp  45024  mountd
    100005    3   tcp  56712  mountd
    100000    2   udp    111  portmapper
    100024    1   udp  55376  status
    100024    1   tcp  47561  status


maybe this'll help.

---

### Post by Xiong Chiamiov on 2008-05-02
I'm a little puzzled by this line in your fstab:
```

/home/bone 192.168.1.101/255.255.255.0 nfs (rw,async,no_root_squash,subtree_check)

```
Shouldn't the address it's getting it from be something along the lines of 192.168.1.101:/home/bone2 or something?  At least, that's the way I have things working for mounting nfs shares off my fileserver.  Have you taken a look at [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo")?

Assuming you're trying to mount the remote folder /home/bone2 to the local folder /home/bone, what happens when you do
```

sudo mount 192.168.1.101:/home/bone2 /home/bone

```
?
Also, is your lappy for sure still using the IP 192.168.1.101? (you can find it in ifconfig)

---

### Post by longboneslinger on 2008-05-02
Actually, my lap is 192.168.1.100 the 101 is the comp in my office. Like I said, up until I upgraded everything was cool. I had a short cut on my lap-top that allowed me to browse the files on my desk-top comp. I was experimenting with VNCServer so I could access my father-in-laws comp to fix his winblows machine and it worked fine. I even had remote desktop working. Now it's all dead.
fstab on the other comp is the same, with 1.100 being 1.101 but otherwise the same. 
both machines are not listing the remote folders as mounted (using the mount command). If I try to mount it, both comps reply:

> mount.nfs: unrecognized mount point 192.168.1.101/255.255.255.0

the desk-top comp just has 1.100 as a dif. I tried switching the IPs (swapping 1.100 for 101 and vice-versa on both machines with no dif. I put them back)
As an interim attempt at fixing this mess, I'm presently upgrading my desk-top to Hearty Heron as I write this. Maybe that'll fix it.:confused:

Maybe. Anywho, thanks for the response. I know the gurus here can help me if anyone can. Being able to get friendly help is one major reason I switched to linux to begin with. That and the sheer stability and security of this OS.
Thax again and TIA to all who help!!
bone

---

### Post by longboneslinger on 2008-05-04
Update. Upgrading the main comp to 8.04 made no dif. I really didn't expect it to but hope springs eternal.
I've played around with vncviewer and if I use the login it gives for the desktop it can't resolve the host. If use the IP addy it pops up the password screen. When I input the pw in it says 'authorization failed'. I triple checked the password on the main box so it's not an improper password. since remote desktop relies on vnc I get the same message there as well. This is a bummer. 
I had a wreck a few weeks ago and I can't really get around to much and I'm using the main comp for entertainment. I have a lot of movies and MP3s on it since it has 4 times the storage space my lap has. Watching movies, videos and listening to Casting Crowns over the network has been a Gods send. So please help an old invalid get his network up and running again. 
TIA to all who post. I really appreciate your taking the time.
bone

---

### Post by longboneslinger on 2008-05-07
Just a gentle bump.

---

### Post by longboneslinger on 2008-05-09
Just another update. I got VNC working but NFS is still dead. 
When I use the mount command I get "cannot find 192.168.1.101 in /etc/fstab or /etc/mtab" (or 100 on main comp). It's in there. I checked both comps. I went back over the NFS install tutorial here and at czarism.com and triple checked my install and it's all the same. So what changed from 7.10 to 8.04?? This is really confusing and annoying me. It worked fine till the upgrade. So far, besides my two fav FF add-ons, this is the only thing that died. 

Can someone please take pity on an old man and toss some help?
Once again, TIA to all who take the time to help!
bone

---

### Post by longboneslinger on 2008-05-14
Yet another bump/slash update. I got ticked off and re-installed 8.04. So it's clean. NFS still doesn't work. I redid czarism eazy-peazy nfs but nada. My main comp/server responds to the mount command with 192.168.1.102 does not exist. Same with the lapy. I am lost.

The only changes are my main comps (bone) IP is now 192,168,1,102 and the lappy (lilbone) switched to 103. I've made the changes in /etc/exports and /etc/fstab. Hardy just doesn't care.


Xiong
It gives the same message. 
> mount.nfs: mount point /home/bone does not exist


In case someone wonders, I am able to ping both comps. So what's the hang up?
bone

---

### Post by longboneslinger on 2008-05-17
Yet another gentle bump.

---

