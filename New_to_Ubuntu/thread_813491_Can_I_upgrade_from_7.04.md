---
title: "Can I upgrade from 7.04?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-05-30
I saw on the main page ([www.ubuntu.com](www.ubuntu.com)) that you can upgrade from 7.10 to 8.04. Can I upgrade from 7.04 (which I have installed on this laptop) to 8.04? Is there instructions somewhere on how to update your OS without having to use a disk? Thanks for any and all help.

---

### Post by bumanie on 2008-05-30
If you upgrade through update manager, you have to update to 7.10 before you can update to 8.04. You cannot update and skip any distros in between. You could always download the 8.04 .iso and do a fresh install.

---

### Post by redfox1160 on 2008-05-30
can i upgrade to 7.10 from the update manager?

---

### Post by bumanie on 2008-05-30
I believe you can still update from 7.04 to 7.10 and then upgrade to 8.04 once 7.10 has been upgraded. Open the update manager and check - it will tell you at the top of the window. It should say upgrade available to 7.10 (or something similar).

---

### Post by wolfen69 on 2008-05-30
if possible, back your stuff up and do a fresh install.(less chance of problems) since this is a long term support release that will be supported for 3 years, wouldnt it be nice to start fresh? just my opinion, as ive never done upgrades. i love that new OS smell.

---

### Post by Exsecrabilus on 2008-05-30
Two Internet updates in a row are not recommended.

If you generally want a more secure way of installation, just burn a copy of 8.04.
It'll be kinda faster and you'll notably see more features

Internet updates can always break and things can happen.

---

### Post by redfox1160 on 2008-05-30
> **wolfen69 said:**
> if possible, back your stuff up and do a fresh install.(less chance of problems) since this is a long term support release that will be supported for 3 years, wouldnt it be nice to start fresh? just my opinion, as ive never done upgrades. i love that new OS smell.

I don't have anything important (that i need to back up) on here. Is there any sites you could point me to that would tell me how to do a clean install. Could i just download the .iso to the desktop, then do something from there? thanks.

---

### Post by Joeb454 on 2008-05-30
You would need to download the .iso to your desktop, and burn it to a CD :) Then you boot from the CD and install it over your existing install (you said you didn't have anything that needed backing up)

---

### Post by Exsecrabilus on 2008-05-30
Download the .iso file.

```
cd ~/Desktop
```
Or wherever you downloaded the .iso file to.
~ represents: /home/<your username>/

```
md5sum <iso file name>.iso
```
This will take a few minutes; it's supposed to.
When the results come out, go here:
[http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS)
Compare the hashes you got to the type you downloaded.
If the hashes are exactly the same, you win.

Right-click on the .iso file and click **Write to Disc...**.
Change the **Write Speed** to the lowest possible.
Now press **Write** and let it.....write!

After it's done and the disc is popped out, put it back in.
Restart the computer and follow the steps.

---

### Post by Joeb454 on 2008-05-30
Ah thanks for reminding me about that! You should always burn an install disc (for a Linux distro etc.) at a slow speed (between 1-4x).

Oh and don't forget to change the boot options to boot from the CD before the Hard Drive ;)

---

