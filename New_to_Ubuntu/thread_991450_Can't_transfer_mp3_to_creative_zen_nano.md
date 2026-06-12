---
title: "Can't transfer mp3 to creative zen nano"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by bogman on 2008-11-23
When I try to transfer mp3's to a creative zen nano plus portable music player using either Rhythmbox or the File browser I get "destination is read only". I used to use the player with a mac for a while and it worked ok for 6 months and then the mac didn't recognize it anymore.

The lsusb output is 

Bus 005 Device 006: ID 041e:4139 Creative Technology, Ltd Zen Nano Plus
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Any help would be appreciated.

---

### Post by magli on 2008-11-25
You may find this interesting:
[http://ubuntuforums.org/showthread.php?t=445201](http://ubuntuforums.org/showthread.php?t=445201)

---

### Post by Hallvor on 2008-11-25
> **bogman said:**
> When I try to transfer mp3's to a creative zen nano plus portable music player using either Rhythmbox or the File browser I get "destination is read only". I used to use the player with a mac for a while and it worked ok for 6 months and then the mac didn't recognize it anymore.

The lsusb output is 

Bus 005 Device 006: ID 041e:4139 Creative Technology, Ltd Zen Nano Plus
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Any help would be appreciated.

Try opening a terminal and type

```
gksu nautilus
``` to open the file browser in root mode. Are you able to write to the device now?

---

### Post by bogman on 2008-11-25
> **Hallvor said:**
> Try opening a terminal and type

```
gksu nautilus
``` to open the file browser in root mode. Are you able to write to the device now?

It still says "Destination is read only".  Thanks for the suggestion though.

---

