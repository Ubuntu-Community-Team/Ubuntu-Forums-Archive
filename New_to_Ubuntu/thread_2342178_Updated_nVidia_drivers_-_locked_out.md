---
title: "Updated nVidia drivers - locked out"
date: 2016-11-04
forum: New to Ubuntu
---

### Post by m.hoop on 2016-11-04
After having much success thanks to the message board, I decided to strike out on my own. 

Big mistake.

I used apt-get to retrieve nvidia drivers for my card (nvidia geforce 8 series). I used nvidia-367. I downloaded and installed, all looked fine. I rebooted, and now I'm stuck. I can unlock my machine and when I input my password, I get a garbled screen, the bongo sound, and it takes me right BACK to the login screen. Not sure how to proceed here. I booted in safe mode and all, and it got stuck because of a failure on nvidia braille something-or-other..

---

### Post by ajgreeny on 2016-11-04
It's generally much better, and safer, to use the nvidia drivers from Additional Drivers utility rather than downloading from nvidia direct, which is what I assume you did.

I am not sure how you uninstall the driver you have at present; was it a .deb file?  if so the command ```
sudo apt-get -remove package-name
``` should do it for you.

I suggest you do uninstall it  and then use the Additional Drivers utility from the dash to install the recommended version.

---

### Post by Autodave on 2016-11-04
You can possibly use your boot disk or stick to get into your installed ubuntu.

---

