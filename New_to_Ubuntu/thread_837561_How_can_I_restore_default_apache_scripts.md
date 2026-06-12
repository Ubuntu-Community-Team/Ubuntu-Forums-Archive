---
title: "How can I restore default apache scripts?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by JiminSD on 2008-06-22
Hi, I managed to corrupt my apache installation and it no longer starts (the startup script ends in [FAIL]).

I've been going through and fixing the reported errors, but would like to know if there is just an easy way to go back to the default scripts that cam with Ubuntu as I think this would be cleaner in the long run. I've been trying to learn apache and things are a bit hacked up. Yeah, I know I should have made a backup.

Any help is appreciated.
Thanks,
Jim

---

### Post by scott_g on 2008-06-23
I'd try two things; first, try simply removing the configuration file (/etc/apache2/apache2.conf), and re-starting apache ```
sudo /etc/init.d/apache2 restart
```.  If that doesn't work, backup your /var/www folder, and remove apache by using the 'Mark for Complete Removal' in the Synaptic Package Manger (this'll remove all configuration files with the removal), then install it again.

Scott

---

