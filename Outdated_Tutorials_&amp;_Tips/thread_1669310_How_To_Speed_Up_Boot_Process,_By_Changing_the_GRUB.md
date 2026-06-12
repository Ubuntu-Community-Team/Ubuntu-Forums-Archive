---
title: "How To Speed Up Boot Process, By Changing the GRUB Menu Timeout.( EASY )"
date: 2011-01-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Bazzi313 on 2011-01-17
When your Ubuntu system boots, you will see the GRUB menu if you hit the Esc key, or if you’ve enabled the menu to [show by default]("http://www.howtogeek.com/howto/ubuntu/show-the-grub-menu-by-default-on-ubuntu/").  The only issue with this is that the default timeout is only 3 seconds.  You may want to increase this amount… or you may even want to decrease  it. Either one is simple.
 Open up the /boot/grub/menu.lst file in your favorite text editor. I’m using gedit:
 [INDENT]sudo gedit /boot/grub/menu.lst
 [/INDENT] Now find the section that looks like this:
 [INDENT]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3
 [/INDENT] The timeout value is in seconds. Save the file, and when you reboot  you will have that many seconds to choose the menu item you want.

---

