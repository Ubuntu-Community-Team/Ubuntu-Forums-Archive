---
title: "How do I mount a folder on a remote server"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Valir on 2008-05-03
Hi, 

Between two Hardy 8.04 computers: How can one mount a folder on a remote server so it shows up as a local folder in the filesystem? The folder is shared and shows up on network through samba and in places. But how does one access it from within an application, as it were a local folder, say within the /mnt folder? 

I have tried using a symlink, but I can't get it to work over network. 

This a probably a very easy thing but I can't seem to find anything that explains it. 

thx for your help

---

### Post by Paqman on 2008-05-03
You can mount remote shares a few different ways:

Nautilus
Dead simple, browse through the network and click on the share. Mounts it for the duration of that session to /media (and therefore shows up on the desktop).

Manually through the command line
Mounts it to anywhere for the duration of that session.

Add an entry to /etc/fstab
Mounts it to anywhere automatically at boot.

To access a share in an application you just point it to the folder where the share is mounted. Say you had an entry in fstab that automatically mounted your music collection to /media/chewns. You'd then tell your media player to find the music collection at /media/chewns. It would behave as if that share were a drive physically installed in your machine.

---

### Post by Valir on 2008-05-05
Hi thanks for the answer, 

1. I still can't get it on though. (btw. I have ubuntu studio Hardy). In nautilus i browse in the network and when i click on the share, it shows up in the drop-down list under network, but not on the desktop - and not either in the /media folder. 

2. How is the manaul command line (and perhaps same problem as above)

3. "Add an entry to /etc/fstab" - I tried a few things but to no avail. How would the entry look like? Say if the shared folder on other computer is called smb://othercomputer/music/ and I would like to find it on my own?

I know i am missing something real simple here, but have tried for many hours. Thanks for the help

---

### Post by tacutu on 2008-05-05
the easiest way would be to use nfs.
install on the client the nfs-common package and the nfs-server on the server.
then, on the server edit the /etc/exports line to tell it what folder to export. It should look something like:
/folder/to/share      192.168.0.2(rw,sync)
(where 192.168.0.2 is the IP address of the client)
finally, on the client you can mount the folder by issuing the following command:
sudo mount -t nfs 192.168.0.2:/folder/to/share /mnt/nfsshare
this will mount the folder under /mnt/nfsshare (which has to exist before)

Of course, you can automatically mount it at boot time by adding an entry to fstab on the client.
hope this helps.

Edit: really, i find it rather absurd to use samba to share folders between unix computers. samba was designed to permit sharing with windows machines. The nfs method is the normal protocol for sharing in unix-world.

---

### Post by Valir on 2008-05-06
Hi, 

I put in the entry in the /etc/exports in the server, and then in the clien I wrote sudo mount -t nfs 192.168.1.34:/home/huginn/Music /mnt/nfsshare

but i get the error message

mount.nfs mount to NFS server 'rpcbind' failed: RPC error: Program not registred
mount.nfs: internal error 

What is bugging me?


p.s. 

"Of course, you can automatically mount it at boot time by adding an entry to fstab on the client." How does one do that, what does the entry look like?

p.s.s. In case I would like to do the same thing from an windows machine using smb, how would that look like?

Thanks for the help guys

---

### Post by inportb on 2008-05-06
Did you say smb? You might want to use samba instead of nfs. You might also find smbfs interesting.

---

### Post by hyper_ch on 2008-05-06
if the other computer is outside your network (or if you are paranoic anway) use SSHFS instead of NFS :)

---

### Post by tacutu on 2008-05-06
yes, this is probably not secure, but if your computers are behind a firewalled router you probably don't have to worry. Plus, i don't think samba is more secure anyway.

anyway, Valir, did you _start_ the nfs service on the server? If not, try
```
sudo  /etc/init.d/nfs-kernel-server start
```
and then see if things work.

good luck.

Edit: fstab thing: on the client, add this line in /etc/fstab:
```
192.168.1.34:/home/huginn/Music	/mnt/nfsshare	nfs	defaults,rw	0 0
```
this should probably do it.

---

### Post by cwskas on 2008-05-13
> **Valir said:**
> mount.nfs mount to NFS server 'rpcbind' failed: RPC error: Program not registred
mount.nfs: internal error 


I am getting this error as well.  The server is a machine that has been serving nfs to other clients on the network for years.  I edited /etc/exports on the server to add my machine and restarted nfs.  I can mount it on the other machines on the network but not on the ubuntu machine.  Any ideas?

Willie

---

### Post by cwskas on 2008-05-13
> **cwskas said:**
> I am getting this error as well.  The server is a machine that has been serving nfs to other clients on the network for years.  I edited /etc/exports on the server to add my machine and restarted nfs.  I can mount it on the other machines on the network but not on the ubuntu machine.  Any ideas?

Willie

I rebooted both machines and now it works.   Just thought I would follow up.

Willie

---

### Post by Xiong Chiamiov on 2008-05-13
Once again, yes, NFS is for sharing between UNIX-like machines, and there's a great tutorial [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

### Post by Valir on 2008-05-14
Yes! Finally it worked.

I followed this tutorial.

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

REMEMBER!!!

What you have to remember if you followed the directions in this thread, is that, when you are in the client and you mount the shared folder, the ip number has to be the servers ip-number. (because it was confused with the clients ip-number in an above post)

On the server you export to the client ip number.
On the client you mount on the server ip number.

then it should work.


Thx for tips guys.

---

### Post by Valir on 2008-05-14
p.s. from [https://help.ubuntu.com/community/SettingUpNFSHowTo#head-a01961641dbc473cbd43f296b22fabafc6c6ee69](https://help.ubuntu.com/community/SettingUpNFSHowTo#head-a01961641dbc473cbd43f296b22fabafc6c6ee69)

To load up at boot:

"Static Mounts

Prior to setting up the mounts, make sure the directories that will act as mountpoints are already created.

In /etc/fstab, add lines for shares such as:

servername:dir /mntpoint nfs rw,hard,intr 0 0

The rw mounts it read/write. Obviously, if the server is sharing it read only, the client won't be able to mount it as anything more than that. The hard mounts the share such that if the server becomes unavailable, the program will wait until it is available. The alternative is soft. intr allows you to interrupt/kill the process. Otherwise, it will ignore you. Documentation for these can be found in the Mount options for nfs section of man mount.

The filesystems can now be mounted with mount /mountpoint, or mount -a to mount everything that should be mounted at boot."


thats: sudo gedit /etc/fstab
add something like: 192.168.1.x:/home/again/music /home/sharemusic rw,hard,intr 0 0  

where x is the server ip number

---

### Post by Valir on 2008-05-16
Hi, 

and now for the next assignment :)

I added a third machine that runs windows, so now I want to add a smb share and mount it in the fstab along with the nfs.

I can mount it manually after having installed smbfs

sudo apt-get install smbfs

share the folder on the server through smb and give it permissions on the network

and then:

sudo smbmount //192.168.1.x/folder/on/server /home/mountfolder/on/client/

voilá, works perfectly.

But now, how do I do it automatically in the fstab as we did with the NFS, how should the line be in the /etc/fstab?

thx

---

### Post by neurostu on 2008-05-16
I don't know if anybody else has mentioned this but sshfs is a great way to do this.
Its really simple to use to!
```
 
$sshfs user@host:[dir] mountpoint 

```
thats all it takes!

You might need to run:
```

sudo apt-get install sshfs

```

---

### Post by Valir on 2008-05-29
Hi, 

has anyone figured out the line for /etc/fstab if one wants to automatically mount a folder from xp with smbmount?

best regards,

---

### Post by Valir on 2008-06-03
Hi, 

this solved the matter:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently?highlight=(mount](https://help.ubuntu.com/community/MountWindowsSharesPermanently?highlight=(mount))

-------------------------------------------------------------------
smbfs, user perms

    *

      FS_TYPE=smbfs
    *

      UID=1000 # particular user's uid
    *

      don't include gid=$GID, which defaults to $UID

//apollo/install_files /path/to/mnt smbfs credentials=/path/to/.smbcredentials,uid=1000 0 0
-------------------------------------------------------------------

However I was having problem with the credential files, so I skipped it altogether, and it worked! (Does that mean my system is wide open? My computers are behind a moderately firewalled router though so I guess i'm for fall practical purposes safe.)

So the line goes in the end of /etc/fstab:

```
//[servername]/[sharedfolder] /[your]/[mount]/[folder] smbfs rw,hard,intr 0 0

```

I am not sure though what it means for security to skip the username, password credentials. But it worked for me. 

I put in the "rw, hard, intr" which i saw in another line, which i think makes it read and write, reconnects if server is restarted. I am not sure though, so somebody else could maybe tell if that is unnecessary.

best,

---

