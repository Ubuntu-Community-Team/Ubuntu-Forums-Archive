---
title: "Bring back Ubuntu! Please!"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by karlo on 2008-08-29
I have Ubuntu Hardy Heron, and I have no installer, just upgraded my Gutsy to Hardy. I installed XP SP3 ... then of course my Ubuntu is gone because my pc will now boot to XP. Still, I haven't touched the linux partitions. Is there a possibility that I can boot with Ubuntu as well as XP again?:lolflag:and please make it easy bec. I only have one laptop, if you'll give me complicatede command line thingy, it's really hard to remember....

Or do you think I have to use a Boot Manager?

---

### Post by Joeb454 on 2008-08-29
I think this is the link you want :)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by kk0sse54 on 2008-08-29
You might have to reinstall GRUB. Try popping in a live CD first though and starting Gparted to check that your linux partitions are still intact. What probably happened was that when you installed XP you probably wiped your MBR.

---

### Post by L1nchp1N on 2008-08-29
Yeah, it's more than likely rest the MBR.  I had this happen when I had to reinstall Windows.  Reinstalling GRUB should resolve it.

---

### Post by crispy_420 on 2008-08-29
I third the motion of the master boot record needs to be repaired/replaced.

To understand you correctly, you installed Windows all over again and this was just a service pack upgrade? By that I mean a clean install of XP. 

If that is the case, Windows has the habit of believing that there is no need to have anying but windows on your drive. It wipes out all other boot loaders but will let you select other versions of windows from its boot loader. God forbid you choose anything but a MS product.

---

