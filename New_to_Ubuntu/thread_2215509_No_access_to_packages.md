---
title: "No access to packages"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by emy.amstein on 2014-04-07
Hi all,  as the section says: absolute beginner...  I've been trying to use Ubuntu 10.10 with my MacBook 4,1. The OS runs all right, but I can't seem to contact any packages server. I've tried to install the Broadcom STA Wireless driver for the wireless hardware in the MacBook to no avail.

Trying to install a manually downloaded version of the driver: OS refuses the file as "unstrusted".
Trying to install from software center: OS cannot fetch files.

Both problems seem to be a staple since Google has lots about them, but nothing really helped. Is there no simple way?  NOTE: I'm not behind a proxy.

---

### Post by carl4926 on 2014-04-07
10.10?
Old and unsupported

Try a up to date version

---

### Post by emy.amstein on 2014-04-07
OK then, I guess I can forget about Ubuntu, because [this page]("https://help.ubuntu.com/community/MacBook") seems to explain that the most recent version I can install on a MacBook 4,1 is 10.10.

Arrgh... I killed a partition with a fully updated Windows install to make the switch... :(

---

### Post by squakie on 2014-04-07
Did you check the links on the right side of that page?   Here's something from those that may be of interest to you since you said yours came back as MacBook type 4,1

[https://help.ubuntu.com/community/MacBook4-1/Raring](https://help.ubuntu.com/community/MacBook4-1/Raring)

Note that the post is talking about installing Ubuntu 13.04.  In the text is what has to be a mis-type:  it says to insert the 10.xx disk - I'm sure that was just a carry over from another older page and you should use the 13.04 disk.

---

### Post by squakie on 2014-04-07
About the wireless - are you sure you have a wireless adapter that requires that driver?

Post back the output of:

lscpi

I know it will be a rather long list, so if you can find your wireless adapter just copy the info for it and post it back here.

---

### Post by emy.amstein on 2014-04-07
> **squakie said:**
> Did you check the links on the right side of that page?

Heyyyyy thanks!... I only scrolled down to the 4,1 section of the list. Anyway I had no clue what "Raring" meant (really an insider info; I'd rather put version numbers there so beginners get the point immediately).

In the meantime I've downloaded, burnt and started the install of 12.04. We'll see, but since you gave me this great link, I guess I'll go for the 13.04 update afterwards.

I'll post back: the output of lscpi if the problem goes on / a thank you message if everything runs all right.

---

### Post by emy.amstein on 2014-04-07
Thanks, everything works fine now. Still in 12.04. Might go for the update to 13.04 in the future.

PS: you're lucky, I wish I could disguise my cat. He'll simply shred my face to bits if I only try to.

---

### Post by Impavidus on 2014-04-07
Don't upgrade to 13.04 if 12.04 works. In contrast to 12.04, 13.04 is unsupported. 12.04 will be supported for three more years. You could at some point try 14.04.

Could you mark the thread as solved? Thread tools (top of the page)&#8594;mark as solved.

---

### Post by squakie on 2014-04-07
+1 on 12.04.  I only posted that 13.xx link since it shows you could go to a higher release than 10.xx.  12.04 is the latest long term support release until later this month when 14.04 will be released.  However, I would be in no hurry to update - if you've got things working I stay as-is for now.

Glad I could help!  Enjoy Ubuntu!

BTW - the cat didn't mind the reighdeer antlers for some reason, but went beserk - I mean REALLY crazy, bouncing off walls, running like a mad man - when I put the matching collar with bells on him.  Took 10 minutes to catch him and he back to normal once the collar was removed and he moved and noticed he wasn't "dinging" anymore. ;)

---

