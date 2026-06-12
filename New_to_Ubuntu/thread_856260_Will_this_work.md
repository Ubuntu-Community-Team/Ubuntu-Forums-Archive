---
title: "Will this work?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Pensfan on 2008-07-11
Greetings all total newb here )  The more I read up on Ubuntu the more I want to give it a whirl to check it out. To that end I have a quick, hopefully easy, question:

I'm thinking of buying a 250-500Gb external USB drive for my PC (Intel Quad Core with WinVista SP1) to use as a small backup device. What I'd like to do at the same time is install Ubuntu on that drive also. Anyone done this that could give me some pointers/suggestions/advice?

Thx in advance.

---

### Post by rxtx on 2008-07-11
Short answer, yes. Well, if you bios supports booting from external USB devices (most do).

Just partition the drive accordingly during setup (don't allow ubiquity to do it automatically) and you're away :) Just make sure you leave enough space for your installation. 

Don't skimp on room for /, it'll only cause problems later.

---

### Post by prismpirate on 2008-07-11
Technically, It should work. However, this is under the condition that your computer can boot from USB. This should not be a problem if your computer is new. 

Attach your removable hard drive. Unplug all existing hard drives. Now, assuming that you have downloaded and burned the live-cd, boot into the live environment. Go to 

System > Preferences > Removable Drives and Media

Uncheck 
[LIST]
[*]Mount Removable drives when hot-plugged
[*]Mount removable media when inserted
[*]Browse removable media when inserted
[/LIST]

Install Ubuntu by clicking **Install Ubuntu** Enjoy.

On a second thought, you need to change your BIOS so as to make sure the computer boots from USB first. 

Why would you install it on a removable hard drive? I'm curious. In addition, if you just want to try ubuntu, boot into it from the live cd. No harm done from doing that

---

### Post by Pensfan on 2008-07-11
Thx for the feedback all. Direct answer Prismpirate - the drives in machine now are twin 250Gb running in 500Gb RAID 0. Since I'm not all that hardware savy, except to know enough to get in trouble :), I figured I'd go with an easy PnP solution if possible. Figure worst case if I totally screw up the external drive I just reformat and start again. Not that confident in my skills to think the same about internal drives lol.

Thx again.

---

