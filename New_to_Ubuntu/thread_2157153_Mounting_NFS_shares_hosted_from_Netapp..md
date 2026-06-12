---
title: "Mounting NFS shares hosted from Netapp."
date: 2013-06-24
forum: New to Ubuntu
---

### Post by silverbullet007 on 2013-06-24
Trying to mount a few NFS shares on my workstation here.. shares are hosted from our Netapp FAS3020.  I have NFS version 2, 3 and 4 enabled on the san, and I have mirrored the NFS export config from other exports that have been working for years.  The error I'm getting says Access Denied.  Which yeah is most likely a permissions issue but my problem is that I have set 'All Hosts' to R/W access, and the two IP addresses of my workstation are specified under the Root Access part of the export config.

I do not know what else I have to do to get this going..

---

### Post by silverbullet007 on 2013-06-24
Here is the exports from the san side.  Yeah there's two 'mis' folders because I do not know if capitalization is required or not.

/vol/vol3/MIS -sec=sys,rw,root=10.2.6.53,anon=0
/vol/vol3/mis -actual=/vol/vol3/MIS,sec=sys,rw,root=10.2.6.53:10.2.6.75,anon=0

---

### Post by redmk2 on 2013-06-24
> **silverbullet007 said:**
> Here is the exports from the san side.  Yeah there's two 'mis' folders because I do not know if capitalization is required or not.

/vol/vol3/MIS -sec=sys,rw,root=10.2.6.53,anon=0
/vol/vol3/mis -actual=/vol/vol3/MIS,sec=sys,rw,root=10.2.6.53:10.2.6.75,anon=0

Show the output from the workstation of this command```

showmount -e

```

---

### Post by silverbullet007 on 2013-06-24
I get:
clnt_create: RPC: Program not registered

Odd because when I google that it seems to indicate that nfs isn't running on the 'server'.  I'm confused now.

---

### Post by silverbullet007 on 2013-06-24
Anyone?

---

### Post by silverbullet007 on 2013-06-24
Ok after installing nfs-kernel-server.. showmount -e worked but only returned this:

Export list for hostname:

Nothing.

---

### Post by redmk2 on 2013-06-24
> **silverbullet007 said:**
> Ok after installing nfs-kernel-server.. showmount -e worked but only returned this:

Export list for hostname:

Nothing.

I don't understand what you did.  Where did you install ***nfs-kernel-server***?  If you installed it on your workstation then the response is correct as there are no filesystems configured for export from your machine.  Why did you install an NFS server on your workstation?   I thought you were only client of the Netapp Filer's NFS server? 

I rather doubt you could get to the Netapp Filer to install anything.  Don't you have an admin to help you with this problem?  I can help with the Ubuntu client but not Netapp.  Is it possible that the server only hosts SMB (CIFS)?  Are all the other clients on the network Windows hosts?

---

### Post by silverbullet007 on 2013-06-25
I don't understand why this is such a hard problem.. really.  

Ok first things first, I installed the nfs-kernel-server based off some googling I was doing while awaiting someone to reply here.  It was an off beat attempt to get it working is why.  I couldn't find a thing definitive on the showmount error I posted yesterday.

Secondly I am the administrator for this site, granted I will never classify myself as an expert on a Netapp... but I can assure you there is nothing that I need to install on it.  The netapp has been hosting 8 NFS shares for years now.  FWIW this is the first Ubuntu client that has probably ever attempted to mount them, but the Engineering folks has no trouble with CentOS and Red Hat.  I want to use linux but I do not want to use either of those distros if at all possible.

All of the users workstations here are Windows, there are 4 linux-based ProE servers that talk to the netapp via NFS.  In my first post or two I explained how I created the NFS share MIS by copying the configuration of the existing NFS shares that work.  I cannot be the first person to want to mount NFS from a Netapp.

---

### Post by SeijiSensei on 2013-06-25
Have you tried posting a bug report at: [https://launchpad.net/ubuntu/+source/nfs-utils/+bugs](https://launchpad.net/ubuntu/+source/nfs-utils/+bugs)

---

### Post by silverbullet007 on 2013-06-25
Actually no.. I never would have thought it was a bug.  I assumed I was doing it wrong.. and actually I've had no one correct me of offer a correct way of mounting NFS shares in fstab.  I got this far by googling and that's never a 100% certainty.

---

### Post by SeijiSensei on 2013-06-25
Well, my /etc/fstab entries for my NFS-exported shares (on a server running CentOS 5.8) look like this:

```

server:/home  /media/homes nfs defaults,rsize=32768,wsize=32768 0 0 

```

I use a separate local /home and mount the server's /home at /media/homes.  I always increase the buffer sizes to 32768 or even 65536 for performance reasons.

On the server, /etc/exports has 
```

/home           192.168.0.0/16(rw,no_root_squash,async,insecure)

```

I use async to improve performance.  Insecure gets around a problem with clients that use a port > 1023, and no_root_squash lets me mount the share as the client's root user.

Of course the ordinary users listed in my /etc/passwd match those found in the server's /etc/passwd so that permissions are correct.

Does that help at all?  This setup is pretty vanilla.

---

### Post by redmk2 on 2013-06-25
> **silverbullet007 said:**
> Actually no.. I never would have thought it was a bug.  I assumed I was doing it wrong.. and actually I've had no one correct me of offer a correct way of mounting NFS shares in fstab.  I got this far by googling and that's never a 100% certainty.

I doubt this is a NFS server bug that could be addressed by Ubuntu launchpad as your NFS server is Netapp.  I think you should first verify what the Netapp NFS exports are.  I think we should have used the longer version of *showmount*.   I have NFS exports on all my machines so I just use *showmount -e * from the host in question.  You can explicitly show the Netapp Server with this long command ```
showmount -e <ipaddress_of_netapp_server>
```... you can use either the hostname or FQDN or IP address.  This should return something like this```

showmount -e 192.168.1.2
Export list for 192.168.1.2:
/exports/rincon/egb_data 192.168.1.0/24
/exports/rincon/rab_data 192.168.1.0/24

``` 

You can also check the server this way  ```
rpcinfo -p <ipaddress_of_netapp_server> 
```

This should return something like the following```

rpcinfo -p 192.168.1.2
   program vers proto   port  service
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  59615  status
    100024    1   tcp  39942  status
    100021    1   udp  45959  nlockmgr
    100021    3   udp  45959  nlockmgr
    100021    4   udp  45959  nlockmgr
    100021    1   tcp  50097  nlockmgr
    100021    3   tcp  50097  nlockmgr
    100021    4   tcp  50097  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  51096  mountd
    100005    1   tcp  39510  mountd
    100005    2   udp  51096  mountd
    100005    2   tcp  39510  mountd
    100005    3   udp  51096  mountd
    100005    3   tcp  39510  mountd

```...you can see the TCP ports for portmapper and nfs in the return I get for one of my NFS servers.

If the exports are correctly setup, as shown in the above showmount -e command, then you should be able to mount the NFS export with something like this```

sudo mount -t nfs <displayed_export> <mount_point>

``` ... The magic is all in the export created on the server.  The client (your workstation) only mounts whatever the server exports.

In the end we need to see if you can see the Netapp exports so you can use that with the mount command.  If you can get that to work it is easy to mount it via fstab.

[COLOR="#0000FF"]Edit:  Oops, I didn't see @SeijiSensei's reply.  Some of what I have said he provided earlier.  :) [/COLOR]

---

### Post by silverbullet007 on 2013-06-26
Guys:

here's my showmount -e results:

bhart@MI00320-1:~$ showmount -e 10.2.1.72
Export list for 10.2.1.72:
/vol/vol0/eng      (everyone)
/vol/vol0/pd       (everyone)
/vol/root          (everyone)
/vol/vol0/cnc      (everyone)
/vol/vol4/Avtec    (everyone)
/vol/vol0          (everyone)
/vol/vol1          (everyone)
/vol/vol2          (everyone)
/vol/vol3          (everyone)
/vol/vol4          (everyone)
/vol/vol3/MIS      10.2.6.0/24
/vol/vol0/web      (everyone)
/vol/vol0/custom   (everyone)
/vol/vol0/tweb     (everyone)
/vol/vol0/eweb     (everyone)
/vol/vol0/groen    (everyone)
/vol/vol4/ARCHIVE1 (everyone)
/vol/vol0/nov1     (everyone)


The export in question being the MIS one, the clients I'm trying to mount on are (verified) in that subnet.  When I first started down this road, i had 'All Hosts' enabled for  RW for this export which would've been 'everyone' like the others.  But when it didnt work I started trying other things.

---

### Post by silverbullet007 on 2013-06-26
The sudo mount -t nfs netapp:/vol/vol3/MIS /home/bhart/mounts/mis returns an 'access denied by server while mounting'

---

### Post by SeijiSensei on 2013-06-26
Does the NetApp generate logs?  Do they show anything useful?

---

### Post by silverbullet007 on 2013-06-27
Useful?  Not at all.  I've checked the Syslogs after every umount and mount.. both from fstab and manually.  And when trying to access the data (which is where the access denied message comes into play)

---

### Post by redmk2 on 2013-06-27
> **silverbullet007 said:**
> Useful?  Not at all.  I've checked the Syslogs after every umount and mount.. both from fstab and manually.  And when trying to access the data (which is where the access denied message comes into play)

Clarify please!  Before you said: *"returns an 'access denied by server **while mounting**' "*.  Now you are saying: *"And **when trying to access the data** (which is where the access denied message comes into play)*.  These are 2 different things.  Does it mount?  Do you have permission to access the file or directory.   it is possible to have success with the first and not the second item.

---

### Post by silverbullet007 on 2013-06-28
I'm sorry, I did make a change on a whim and the share mounts now.

See before I had read how in mounting an NFS share you should put server:\share and NOT put server:\path\to\share.

So what I did was change that after seeing the showmount -e display the full path, i.e. vol\vol3\MIS, so I change the line in fstab to match from netapp:\MIS to netapp:\vol\vol3\MIS

I have a thread about this going on on ExpertsExchange to so I got confused on which one I updated.  But yes the share mounts now however I get "you do not have permissions to view the contents of this folder"  The line right now is:

10.2.1.72:/vol/vol3/MIS /home/bhart/mounts/mis2 nfs     hard,rw,auto,noatime,nolock,bg,nfsvers=3,intr,tcp,rsize=32768,wsize=32768       0       0

And as you can see above everyone on the 10.2.6 subnet has R/W perms.

---

### Post by SeijiSensei on 2013-06-28
Yes, but they also need to have the proper Unix permissions on the specific directories as well.  Setting NFS to rw means that users can write to the share, but they can still only write to shares to which they have permissions as controlled by their Unix by user and group IDs.  

Does the NetApp run something like [idmapd]("http://linux.die.net/man/8/idmapd")?  I usually just maintain identical copies of /etc/passwd on the server and client, but that may not be an option for you.

The simplest solution may be to put all the users in a common Unix group and grant the group write permissions on the shared directory.

---

### Post by redmk2 on 2013-06-28
> **silverbullet007 said:**
> I'm sorry, I did make a change on a whim and the share mounts now.


That's nice to know.  It make diagnosis so much easier.   LOL
> 

See before I had read how in mounting an NFS share you should put server:\share and NOT put server:\path\to\share.

I think you are confusing Samba (SMB-CIFS) share with NFS exports.  They are not the same thing, nor are the expressed the same manner.  That's one of the reasons I don't use the term shares when talking about NFS exports.  The Samba share is //SERVER/SHARE and the NFS export is *hostname:path/to/nfs/export/directory.* 
> 

So what I did was change that after seeing the showmount -e display the full path, i.e. vol\vol3\MIS, so I change the line in fstab to match from netapp:\MIS to netapp:\vol\vol3\MIS

I have a thread about this going on on ExpertsExchange to so I got confused on which one I updated.  But yes the share mounts now however I get "you do not have permissions to view the contents of this folder"  The line right now is:

10.2.1.72:/vol/vol3/MIS /home/bhart/mounts/mis2 nfs     hard,rw,auto,noatime,nolock,bg,nfsvers=3,intr,tcp,rsize=32768,wsize=32768       0       0

And as you can see above everyone on the 10.2.6 subnet has R/W perms.

I'll let @ SeijiSensei help you sort out the file permissions and user ID's.  His description is perfectly stated.  I will make a comment though about UID's and GID's being consistent across the LAN.  It is very helpful to do that.  This way the mortal user (you)  is correctly identified no matter what host you are logged into.  I manually do that on my home network and use a common group with group inheritance.  If you have a lot of hosts that you administer then you should consider using a centralized system of user ID's.  It can be as simple as NIS.  My take on that would be that if you have a small installation go with NIS.  If you have such a large install base I would seriously consider a commercial LDAP/Kerbros/Bind9 solution.  My favorite (and the most expensive) is Novell's eDirectory.

[COLOR="#0000FF"]Edit:  Now that I think of it, you are the administrator and you have a nice shiny NetApp Filer in your network.  You must have some sort of centralized user management.  If not, I'd put in a requisition tomorrow for eDirectory and be done with it.  Or maybe you should talk to your senior IT engineer first.  What do you think? [/COLOR]

---

### Post by silverbullet007 on 2013-07-01
I'm not confusing the two (NFS and Samba) but I did toss the word 'share' between them so maybe that's part of my mistake :)

We're obviously a Windows shop mainly, thus we do have two DC's in each site including mine.  We have not, however, ever had NIS setup anywhere so maybe that's an option.  The few *nix boxes we have setup that have been utilizing these NFS exports for years all user service accounts.  I am the only 'regular' user whose trying to use the Netapps NFS exports so maybe that's also a problem/monkey wrench.

Oh and I absolutely abhor Novell.. just personal preference.

---

### Post by redmk2 on 2013-07-01
> **silverbullet007 said:**
> ... We're obviously a Windows shop mainly, thus we do have two DC's in each site including mine.  We have not, however, ever had NIS setup anywhere so maybe that's an option.  The few *nix boxes we have setup that have been utilizing these NFS exports for years all user service accounts.  I am the only 'regular' user whose trying to use the Netapps NFS exports so maybe that's also a problem/monkey wrench.
...
If you have a centralized user account system already such as AD then you don't need a second one such as NIS.  They both do the same thing.  NFS security is based only on UID and GID and the file system permissions.  It is not strictly based on whether you are a mortal user or a system user per se.

---

