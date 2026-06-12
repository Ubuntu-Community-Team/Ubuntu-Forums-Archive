---
title: "Mounting NTFS with permissions, still can't chmod"
date: 2015-11-27
forum: New to Ubuntu
---

### Post by jc-szamosi on 2015-11-27
I followed the instructions in this answer:
[http://askubuntu.com/a/91054/475985](http://askubuntu.com/a/91054/475985)

using both users and permissions, as recommended. But two surprising things happened:

1) I could not mount the drive without sudo, despite having used 'users'
2) I still can't chmod on that drive.

Not having chmod available to me is super irritating. Is there anything I can do to fix it other than format the drive?

Thanks

---

### Post by Tadaen_Sylvermane on 2015-11-27
No. You have to change the filesystem if you want to control permissions. NTFS cannot understand unix permissions.

---

### Post by Habitual on 2015-11-28
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
I'm not certain format is necessary.
It can be mounted in such a way to allow full control.

chmod is useless if it doesn't mount. so save some aspirin and skip that step if it doesn't.

---

### Post by Morbius1 on 2015-11-28
>  1) I could not mount the drive without sudo, despite having used 'users'
Because the user and users option have no meaning with NTFS unless you do something silly with setuid-root.
>  2) I still can't chmod on that drive.
Consider yourself lucky.

My view is fairly simple on this:

*** If this is an ntfs partition in a dual boot with Windows don't user the permissions option. It's a far more complicated thing than just adding the option. Username  maps have to be created so that Windows and Linux can understand each  others users. Not worth the risk to your Windows install.
*** If it's an ntfs partittion on a Linux only system, Why? If you really need file specific permissions control use a linux filesystem.
*** If it's on a Linux only system and you want to change permissions across the whole ntfs partition then [COLOR=#0000cd]Habituals[/COLOR]'s link is your best bet.


THe only folks that recommend using the "permissions" option on ntfs either:
** Have done it themselves but only on an ntfs partition that is not part of a dual boot with a Windows OS.

** Have read about it but never actually used it themselves.

---

### Post by bab1 on 2015-11-28
> **Morbius1 said:**
> My view is fairly simple on this:

*** If this is an ntfs partition in a dual boot with Windows don't user the permissions option. It's a far more complicated thing than just adding the option. Username  maps have to be created so that Windows and Linux can understand each  others users. Not worth the risk to your Windows install.
*** If it's an ntfs partittion on a Linux only system, Why? If you really need file specific permissions control use a linux filesystem.
*** If it's on a Linux only system and you want to change permissions across the whole ntfs partition then [COLOR=#0000cd]Habituals[/COLOR]'s link is your best bet.


THe only folks that recommend using the "permissions" option on ntfs either:
** Have done it themselves but only on an ntfs partition that is not part of a dual boot with a Windows OS.

** Have read about it but never actually used it themselves.

+1 and amen to all of the above!  It reinforces the notion that *just because can do something doesn't mean you should do it*.

---

### Post by Tadaen_Sylvermane on 2015-11-28
Learned something. Possible however not recommended. I always thought it was impossible :/

---

### Post by jc-szamosi on 2015-11-29
> **Morbius1 said:**
> 
...
*** If it's an ntfs partittion on a Linux only system, Why? If you really need file specific permissions control use a linux filesystem.
...

THe only folks that recommend using the "permissions" option on ntfs either:
** Have done it themselves but only on an ntfs partition that is not part of a dual boot with a Windows OS.
...


This is my situation. I have no idea why this drive was set up as NTFS. It's an internal drive on a linux-only tower. I didn't set up the system; I just have to live with it. I was hoping there was a clever way to avoid backing up, formatting, and restoring the drive in order to make it properly functional, but it looks like the consensus answer is "don't do what you're trying to do" so I won't.

Thanks for the advice, folks!

---

