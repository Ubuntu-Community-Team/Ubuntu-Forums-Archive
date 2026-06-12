---
title: "Unable to boot ASUS Vivomini from USB"
date: 2017-05-25
forum: New to Ubuntu
---

### Post by anders.ostling on 2017-05-25
I have recently bought a ASUS MiniVivo UN42. It came preinstalled with Windows 10, but I want to run Ubuntu instead.

[https://www.asus.com/us/Mini-PCs/VivoMini_UN42/](https://www.asus.com/us/Mini-PCs/VivoMini_UN42/)

I created a bootable USB stick with Ubuntu 16.04 yesterday. I downloaded from Windows on that box, and a got the AMD64 version. Hope that this is correct.

Modified the ASUS BIOS to enable USB boot, and selected the Sandisk stick as primary boot. There is also an option called "Secure boot" that I am unable to change for some reason (I have set an administrator password in bios since a forum post mentioned that, but it makes no difference).
Anyway, while booting the box, I never got to a "Select boot device" prompt, and Windows starts by default.

There is also a boot option where I can select "Windows UEFI secure boot" or "Other OS". I have selected the Other OS, also without any effect.

The USB stick in inserted in a port directly on the computer, not in an USB hub.

Any ideas? I would love to get Ubuntu up and running on this little beauty!

Anders

Edit: I had to delete the "secure boot keys" in bios in order to disable fast/secure boot. Now it works fine!

---

### Post by KenUBF on 2017-06-01
Hi anders. I also have a ASUS computer...a Vivobook, so I'm hoping that the steps I took will help you. I've attached pictures of my BIOS so you can compare. 



[ATTACH=CONFIG]275394[/ATTACH]


First I disable secure boot and fast boot. Secure boot should be under the Security tab.


[ATTACH=CONFIG]275395[/ATTACH]


Then I go to the Boot option and make sure the drive I want to boot is selected. 

[ATTACH=CONFIG]275396[/ATTACH]

Then I go to Save and Exit and choose my desired boot device again and hit enter and it should hopefully boot for you. 

[ATTACH=CONFIG]275397[/ATTACH]

In this case I looked at the new Bodhi Linux distro.....

[ATTACH=CONFIG]275398[/ATTACH]

Good luck!

---

### Post by KenUBF on 2017-06-01
Oops. I didn't see your edit. I'm glad it works! I'll leave these pics up for anyone else who might have a similar issue.

---

