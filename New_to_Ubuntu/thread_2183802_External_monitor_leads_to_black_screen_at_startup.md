---
title: "External monitor leads to black screen at startup"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by frame0 on 2013-10-26
Hello,

I nearly have no experience with Linux. I have installed Ubuntu 12.04.3 LTS on my laptop (IBM lenovo X220 4291-37G). I've configured it and installed several further software which I require for work. And everything works fine as long as I do not use an external monitor.

The first time I connected an external monitor with VGA it was correclty detected and the screen was cloned on both monitors. Then I adjusted the settings (via the GUI) to extend the desktop on both monitors. And everything still worked fine. But then I have rebooted. During the start both monitors showed the Ubuntu scrren with the animated dots under the logo. When the login screen should be displayed, both monitors showed only a black screen with a blinking white underscore in the left upper corner. I typed in my passphrase because I would have done this if the log in screed would have been displayed. The entered passphrase was not shown and when pressing the enter key. Then I saw on my laptop screen an Ubuntu image which was splitted into four mixed up parts. Thereafter, the normal desktop was shown. It was extended on both screens.

Then Ubuntu seems to work normally. But when I am away from keyboard for some time both screens become black. When I move the mouse nothing happens. When I press a key the reaction differs each time the displays become black. Sometimes, the external monitor shows its part of the desktop again and the monitor of the laptop stays completely black or the other way round. Or both displays keep black and show the white blinking underscore in th left upper corner. But when I enter my passphrase nothing happens and I have to reboot.

If I use the laptop without the external monitor everything works fine.

I have searched the interet for this problem. But I found only some similar problems with Nividia graphic cards which I don't have. Here some information of my laptop which might help to give an answer. If some further information are required please tell me because I do not have any experience on how to find the cause of an error in Linux.

The command ```
lspci -v | perl '/VGA/../^$/ and /VGA|Kern/ and print'
``` produces the following output:
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
                Kernel driver in use: i915
                Kernel modules: i915
```

The command ```
lsb_release -a
``` produces the output:
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:         12.04
Codename:     precise
```

Best regards
frame

---

