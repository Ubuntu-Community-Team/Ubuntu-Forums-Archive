---
title: "Unable to change permissions"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by gunter1959 on 2012-11-17
Using 12.04 gnome no effects

On my dual boot laptop, I have the Windows NTFS partition visible and usable as "Acer". Most of my data resides there. No problems.

Now, I'd like to share "Acer" on my home network. It's visible on the other PC's, but not accessible, as the permissions for that partition are  drwx------

I tried the GUI to change the permissions - no luck. So I tried the command line, both as the owner, and the SU, like this:

gunter5253@Aspire-5253:/media$ sudo chmod g+rwx Acer

(no error messages)

But still no luck: 

gunter5253@Aspire-5253:/media$ ls -ld Acer
drwx------ 1 gunter5253 gunter5253 8192 Nov 18 14:45 Acer

What am I missing? Any help appreciated.

---

### Post by Gone fishing on 2012-11-17
ntfs doesn't support Unix permissions so the permissions are being set by whatever system you are sharing over the network. 

How are you sharing over the network? Samba, NFS? That is where you will need to set the permissions for example if you are using nfs you will need to make sure the the export is rw and the clients mount nfs as read write.

---

### Post by gunter1959 on 2012-11-18
> **Gone fishing said:**
> ntfs doesn't support Unix permissions so the permissions are being set by whatever system you are sharing over the network. ]

How are you sharing over the network? Samba, NFS? That is where you will need to set the permissions for example if you are using nfs you will need to make sure the the export is rw and the clients mount nfs as read write.


hmm. Are you saying that I can't change the NTFS permissions when running Linux?

I'm using Samba (via Nautilus). And it's this GUI that won't change the permissions either (right-clicking the partition or a sub-folder, properties-permissions)

---

### Post by Gone fishing on 2012-11-18
Yes 

When you mount an ntfs drive the options in fstab determine the permissions and you cant change the permission of the files individually. ntfs does not support UNIX permissions so these are set by fstab when the drive is mounted.

OK update it seems that you can add an option in fstab that maps POSIX to Windows permissions (you live a learn)

eg:

/dev/sda2   /mnt/excess ntfs-3g permissions,locale=en_US.utf8    0   2

[http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)

However, I would suggest mounting the ntfs drive with rw permissions and the setting the permissions you want the network users to have in samba

[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

---

### Post by Morbius1 on 2012-11-18
You have 2 choices:

[1] Mount the NTFS partition with the permissions necessary for access by remote samba users. [COLOR=Blue]*BTW, I personally would not use the "permissions" option on a drunken bet since it will most likely end up messing up your partition but that's entirely up to you. Just don't ask for Windows help in a Linux forum.*[/COLOR]

[2] Make eveyone on your network look like you when they access that share.

Edit /etc/samba/smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the share definition or in the [global] section ( right under the workgroup line ):
```
force user =  gunter5253
```Then restart samba:
```
sudo service smbd restart
```

---

### Post by gunter1959 on 2012-11-20
I'd like to thank you for your contributions so far. I did a lot of reading and tinkering, and have come up with a suitable work-around because of that, (learned a lot about users, groups, domains, permissions etc) not involving iffy permissions or installing additional software. My migration from Windoze to Ubuntu is nearly done, so Good Riddance, Mr. Gates. 

Cheers!

---

