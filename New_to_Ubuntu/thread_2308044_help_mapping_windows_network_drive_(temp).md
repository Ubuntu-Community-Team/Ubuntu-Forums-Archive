---
title: "help mapping windows network drive (temp)"
date: 2015-12-30
forum: New to Ubuntu
---

### Post by cafeledavid on 2015-12-30
hi i want to map a windows network drive, now my company has different subnets but we use site to site vpn so all remote sites can communicate with each other

now that i am using linux, i would like to do the same, in windows i would just map via run line \\IP address or \\IP address\share folder name

in linux i read you can do this via fstab file but i want to do this temporarily since there are so many shares on different subnets. i tried to use

sudo mount -t cifs //Windows IP/share -o username=ak /mnt/share

i am replacing the parts like username with my domain admin account but it keeps saying no write access so it fails

any ideas?

thanks

---

### Post by bab1 on 2015-12-30
Your company's IT department should be able to help you with this issue.

---

### Post by cafeledavid on 2015-12-30
I am in IT lol I am not familiar with linux though, I am trying to learn it without schooling, we all use windows where I work but I want to implement linux on certain systems

---

### Post by bab1 on 2015-12-30
> **cafeledavid said:**
> I am in IT lol I am not familiar with [s]linux[/s] [COLOR="#0000FF"]**Linux**[/COLOR] though, I am trying to learn it without schooling, we all use windows where I work but I want to implement linux on certain systems
If you are just attempting to set up a file server (not AD-DC) you can follow [this guide]("https://www.samba.org/samba/docs/man/Samba-Guide/").  Forget all the install stuff.  You can [start here]("https://www.samba.org/samba/docs/man/Samba-Guide/ExNetworks.html").  Samba v4 uses the same processes (daemons) as Samba v3, so for the most part the file sharing is the same.  In fact some of the Samba v2 parameters are still used.  Read everything up to the PDC part.  Don't go off into the weeds regarding PDC or AD-DC.  That is a completely different thing.  Think of the default Samba install as a member server BEFORE dcpromo.

In your issue, I'll bet you have not created a Samba user and a matching Linux user.  When you authenticate to the share Samba checks both the Linux and Samba user databases.  

In some ways Linux and Windows work the same if you can get past the differences in terms.  In other ways they are very different.  Read up on Linux permissions and how they are applied.  I always add the users (adduser) and the Samba user (smbpasswd -a) first.  Then I create the data store that has the correct permissions.  After that I share the directory to those users so they can access it remotely.  If you think about it, you have the same users on all the machines in the network, but no central management.  So the user bob has to be configured on the server and the client.

Samba has lots of legacy code and was originally reverse engineered.  It can get confusing.  Start with the tutorial and come back with the questions I'm sure you will have.

---

### Post by cafeledavid on 2015-12-30
I just want to be able to map to a Windows system, doesn't have to be a server, and access the shared folder(s) on it like I would in windows

will this Samba do the same?

---

### Post by cafeledavid on 2015-12-31
i figured it out, i didnt have cifs installed, now i can map however it is only giving me read only rights even when i am logging in as a domain admin, also is there a way like in windows to map to the root of the system instead of always having a shared folder name such as //192.168.1.1 instead of //192.168.1.1/share any ideas? couldnt find anything via google for both
thanks

i am using:
sudo mount -t cifs //server/share -o username=domainadmin /home/me/tempmapping

---

### Post by bab1 on 2015-12-31
> **cafeledavid said:**
> i figured it out, i didnt have cifs installed, now i can map however it is only giving me read only rights even when i am logging in as a domain admin... 

Samba (and Linux) have no concept of "Domain Admin" users.  You are either root (uid=0) or a system (non-login) user or a normal user (interactive login and shell).  You can add read/write and user ownership at mount time.  You can see all the options by reading the man pages with this terminal command```
man mount.cifs
```
> 

also is there a way like in windows to map to the root of the system instead of always having a shared folder name such as //192.168.1.1 instead of //192.168.1.1/share any ideas? 
There is no provision for admin sharing (C$ or some such) with Samba.  You could share share the root folder of the partition.  I don't ever do that as I don't ever nest shares inside of other shares.  > 
i am using:
sudo mount -t cifs //server/share -o username=domainadmin /home/me/tempmapping
Something like this might help```

sudo mount -t cifs //server/share -o rw, uid=<your uid), gid=100 username=<user>  /home/<user>/tempmapping

```
This should mount the share with you authenticating AND with the user 1000 as the directory owner (uid) and the the group named *users * as the group-owner.  The group owner is more important than the user when multiple users have access.

You manage access with ownership and permissions.  If all of your users are in a common group (say gid=100) then they would all have access permissions based on the group permissions (rwx).

if you are going to learn Linux you will need to drop using Windows concepts.  Windows is not Linux.  I would start at the beginning with [this]("https://help.ubuntu.com/lts/serverguide/serverguide.pdf") .

---

### Post by cafeledavid on 2015-12-31
thanks i will check the pdf out but the [COLOR=#000000][FONT=Ubuntu Mono]man mount.cifs says [/FONT][/COLOR]No manual entry for mount.cifs

do i need to install something else?

---

### Post by bab1 on 2015-12-31
> **cafeledavid said:**
> ...but the man mount.cifs says No manual entry for mount.cifs

do i need to install something else?
If I understand your question correctly, the answer is, no there is nothing else to install.  The items in the  mount.cifs man page are invoked by the mount command.  You do not use mount.cifs directly.  The proper way to invoke the use of mount.cifs is```
sudo mount -t cifs
```
The -t switch is to declare the type of file system being mounted (in your case it is cifs).  As stated in the man page```
mount.cifs mounts a Linux CIFS filesystem. It is usually invoked indirectly by the
       mount(8) command when using the "-t cifs" option.
```

The mount.cifs man page is useful as it lists the options (-o) you can use with the mount command.

The man pages are a comprehensive reference of a Linux distro.  Many times the man pages include items that are not called directly.

---

### Post by cafeledavid on 2016-01-01
thanks for the info, monday i will try all this

---

### Post by cafeledavid on 2016-01-07
yeah gid doesnt work :(

still only read access..

so i can map drives fine just wish i didnt need a share folder name after the ip and could go to the root of the share like in windows.. really dumb you cant do that

---

### Post by davehenson on 2016-01-18
thank you to the thread starter. I'be been looking for this for a while and seem to only find outdated info. Now to figure out hot to automate this at boot!

---

### Post by bab1 on 2016-01-19
> **davehenson said:**
> thank you to the thread starter. I'be been looking for this for a while and seem to only find outdated info. Now to figure out hot to automate this at boot!
FWIW, I never mount a SMB (CIFS) share at boot up time.  You will have endless problems with users that forget to unmount the share before shutting down.  This hangs the system.  I've seen a lot of threads with folks reporting a perceived bug, but I assure you it is not a bug.  The CIFS file system has no provisions for knowing when the system is shut down.

The best bet is to either browse to to the share and click on the icon to mount the share or mount the share via the file browser's "Connect to Server" provision.  If you want to map (bookmark) the share for easy mounting later on you can do that.  The Ubuntu system will use the (Gnome Virtual FIle system (gvfs) mounting system to monitor the system and unmount the share as you shut down.

---

