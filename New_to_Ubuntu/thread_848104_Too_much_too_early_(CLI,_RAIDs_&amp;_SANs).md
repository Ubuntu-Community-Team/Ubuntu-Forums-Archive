---
title: "Too much too early?? (CLI, RAIDs &amp; SANs)"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Toyan on 2008-07-03
Hello people of Ubuntuness!!

First off... I am brand new at this *Nix thing.  I work desktop support, but everything is windows based, so it's all new and weird to me...

The bosses where I work have tasked me with installing the CLI of Ubuntu, get a RAID setup in the server (about 8 SCSI HDDs) and set it up so that the Windows SAN can see the extra space on this ancient PoS.

Bearing in mind, the last time I used a CLI 'properly' was back in the days of Win95, and even then it only got used for when Windows broke.  It gets used regularly ping and ipconfig commands, but that's about as much as i do.

What I'm hoping to find is some kind of documentation on setting up RAIDs from within the CLI.  (I've got some stuff about common commands and such, but as to know where to look from there...)

Apparantly we're not allowed the GUI of Ubuntu as using the terminal from there doesn't allow full access to the kernal, which, according to the guy who has tasked me with it says.  (I've been told the kernal will need 'tweaking')

It's all a bit over the top of my tiny little Windows mind, and I was hoping for a bit of point in the right direction, not necessaraly a complete answer.  (I do need to learn after all!!)

Thanks in advance folks, and apologies for the bad spelling!!

Andy

---

### Post by hyper_ch on 2008-07-03
Not sure what you're looking for but try that:  [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=raid&titlesearch=Titel](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=raid&titlesearch=Titel)

---

### Post by Toyan on 2008-07-03
Thanks for the info, I'll have a little gander and see what I can get.

I'll also have a play with search to see what else i can dig up...

Thanks again.

---

### Post by avtolle on 2008-07-03
Take a look at [https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid) and see if this gives you some help.

---

### Post by ilrudie on 2008-07-03
Why Ubuntu for this?  CentOS (recompiled RedHat Enterprise) has very good support for RAID (both soft and hard), LVM (Logical Volume Manager), Samba (Windows File Shares) and LDAP/Kerberos (Windows authentication).  It also supports iSCSI and Fibre Channel if you are serious about connecting it to a SAN.  It may be wrong to suggest it but CentOS is probably a better place to start looking into this.

Furthermore building, administering and maintaining this may actually be a little over your head if you are used to supporting desktop Windows.  If your company has a Unix Team they should be the ones  who own this even if the file shares will be used exclusivly for desktops running windows.  If you don't have a Unix Team and your boss really wants to push forward with this you can always post back to Ubuntu Forums and get answers.

Regarding the terminal:  The terminal does allow full access to the kernel but your user does not have permissions.  Traditionally only root(UID=0) has full access to the computer.  Ubuntu breaks from traditional POSIX security model by disabling root and instead relying on sudo to grant access to things that normally root would do.  To learn more about sudo type ```
man sudo
```If you want more help or better advice post back with a better description of what your boss wants and I will try to assist you.  Things like what kind of hardware, what kind of RAID (hard or soft, mirror, concatination, stripe, parity, dual parity?), and does he really mean SAN (Storage Area Network) or does he mean NAS (Network Attached Storage) because these are different.  If he means SAN what kind of SAN do you have (iSCSI, direct Fibre, switched Fibre)?  If he means NAS does he want a Samba file server?  Does he require Active Directory integration?

Finally if they want you to be a full time windows desktop admin and a part time Linux Systems/Storage admin you should be asking for a nice raise and maybe a cool new title or something.

Sorry this is so long but there is a lot you need to consider.

---

### Post by hyper_ch on 2008-07-03
why CentOS and not Debian? ^^

---

### Post by ilrudie on 2008-07-03
> **hyper_ch said:**
> why CentOS and not Debian? ^^  Debian is of course quality.  I work in a Unix (Solaris/AIX) shop with some CentOS/Redhat ES so I know it works well with all sorts of the possibilities the OP might encounter in his project.  I just don't have the Debian experience is all.  Don't count my post as anti-Debian just pro CentOS.

---

### Post by hyper_ch on 2008-07-03
Debian Server is like Ubuntu - just a bit older packages (and IMHO more stable)

---

### Post by Toyan on 2008-07-03
> **ilrudie said:**
> Why Ubuntu for this?  

The boss said so... 

> **ilrudie said:**
> Furthermore building, administering and maintaining this may actually be a little over your head if you are used to supporting desktop Windows.  If your company has a Unix Team they should be the ones  who own this even if the file shares will be used exclusivly for desktops running windows.

I agree, I believe it may be over my head, and I've tried explaining that, but as we are only a 3 man team (2 of us desktop support guys, and 1 'super brainiac'/'boss') you guys here will be my first port of call!!

If I had my way, i'd just stick to Windows because I know it, and can do it as it's what I've done for years (Windows Support that is... No offence intended..)

> **ilrudie said:**
> Regarding the terminal:  The terminal does allow full access to the kernel but your user does not have permissions.  Traditionally only root(UID=0) has full access to the computer.  Ubuntu breaks from traditional POSIX security model by disabling root and instead relying on sudo to grant access to things that normally root would do.

I've been reading about that, and using sudo on the VM I've been using to practice on.

> **ilrudie said:**
> Things like what kind of hardware, what kind of RAID (hard or soft, mirror, concatination, stripe, parity, dual parity?), and does he really mean SAN (Storage Area Network) or does he mean NAS (Network Attached Storage) because these are different.  If he means SAN what kind of SAN do you have (iSCSI, direct Fibre, switched Fibre)?  If he means NAS does he want a Samba file server?  Does he require Active Directory integration?

Thanks for the offer, I may be taking you up on that.  As for the other info, the hardware is an old Acer F650PE server. (I believe it's discontinued, and both Google and the Acer website turn up chuff all...

The RAID is to be mirrored, and he does indeed mean a SAN (As long as thats the one that can scan and find empty storage space).  I've no idea on the type of SAN, apart from when using the Windows machine with it on, (which I've not actually played with) it seems to be fine.  (As in, the Windows application scanned the machines it was told to scan, came back with a report of what was available, and thus the space became assigned as useable or whatever the terminology is.)

As for AD intergration, it's not been mentioned, i think the plan is just to get this old machine setup with it's SCSI drives, and use it as a file storage machine.  So I would doubt AD setups would be needed.

> **ilrudie said:**
> Finally if they want you to be a full time windows desktop admin and a part time Linux Systems/Storage admin you should be asking for a nice raise and maybe a cool new title or something.

I can only dream and hope... although if I do get it sussed, I'm sure it will look pretty upon my CV...

> **ilrudie said:**
> Sorry this is so long but there is a lot you need to consider.

No apology needed, really useful info to consider in there.  I'll be stealing quotes from you and mailing them to the boss very shortly!!  Thank you!

---

### Post by ilrudie on 2008-07-03
He probably means NAS:

The difference between SAN and NAS is that each piece of SAN space assigned to a server shows up to the OS as a physical device.  A server or cluster "owns" it in the same way it "owns" local disks.  The server doesn't just read and write files to it but can actually use it as a disk.  SAN space can be formatted, mirrored, striped, concatenated all by the server that owns it.  NAS space is really just a file share.  The space is owned an managed by the NAS Device and read/write permissions are given to the clients.  Both will be able to find empty storage space and resizing/reclaiming/repurposing/repartitioning that space is generally more a function of the File System and Volume Manager.  

If you want to build your own SAN Attached Disk Array I'm not sure Ubuntu/Debian/Redhat/CentOS or any other Distro is the proper way to go. You will probably be cooking your own disto up because I can't think of any that are built for this (could be wrong).  If thats really what he wants he should be talking to a Vendor(NetAPP, EMC, Hitachi...) not an employee.

---

