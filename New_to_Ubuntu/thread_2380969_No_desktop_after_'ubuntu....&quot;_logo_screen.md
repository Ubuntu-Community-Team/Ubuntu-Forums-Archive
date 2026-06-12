---
title: "No desktop after 'ubuntu....&quot; logo screen"
date: 2017-12-24
forum: New to Ubuntu
---

### Post by wrongusername2 on 2017-12-24
Hi,
           I am new to Ubuntu. 3 days ago I moved my primary machine to Ubuntu. It ran well for two days. This morning I am having boot problem.

[B]Problem
[/B]1) This is not DUALboot. just has Ubuntu 16.04
1) Last night I did a grace full shutdown
2) Today I turn on the machine. GRUB menu came up, and then I chose "Ubuntu" 
3) Showed purple logo screen. All the white dots become SOLID red.
    This stayed for several minutes
4) Then I pressed CRT+ALT+DEL. Machine restarted, now I get purple screen but **no word "Ubuntu"**
     Purple screen stays for ever. Keys are responding so it is not hung

**Grub output**
I went to Grub menu typed ls
    
```
    grub> ls
                            .........(hd2) failed to read sector......
```
[B]
mSata is hd2
[/B]I have 3 physical hard disks. Hd2 is unused. It had NTFS reserved partition. Last night I deleted the reserved partition, so it became un allocated partition.


Is the problem because of hd2?
Can I disable the drive hd2 from Grub?
I can also physically remove the mSATA. 

Please let me know how to proceed..

---

### Post by wrongusername2 on 2017-12-24
I removed the mSATA disk, then booted. No use. OS stops in purple screen, does not reach the login screen.

---

### Post by wrongusername2 on 2017-12-24
This got solved. I had to comment out following line in fstab. In order to do that, I had to connect the hard disk to another system.
#windows ext drive
#UUID=9A8C91E08C91B76B  /media/extsun  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0

---

