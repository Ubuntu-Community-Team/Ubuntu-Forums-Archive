---
title: "VSFTP user Browsing problem"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by hawk007 on 2012-11-16
I have created a ftp user and added the user to the chroot list.

When i log into the user account using filezilla the user is directed to a specific folder, ie /var/www/site1folder.

The problem is that the user can back out into, www, then var, then system folders are all vizible.

How can i stop the user being able to browse other folder.

Any assistance (the easier the better) WOULD BE APPRECIATED THANKS.

---

### Post by Toriku on 2012-11-16
you want to add

chroot_local_user=YES

into your config file
:)

---

### Post by hawk007 on 2012-11-16
There are 2 chroot_local_user=YES in the config file and both are UNCOMMENTED


Thanks for the reply by the way.

---

### Post by Toriku on 2012-11-29
is the user you are using listed in the user list that bypasses chroot? I popped my username in this list to see the entire root directory of the server, but left the other users out of the list, and they can only see their own directory... I'm still a bit new to all of this, I can't remember where this list is on my machine but the default directory is in the comments.

---

### Post by Wim Sturkenboom on 2012-11-29
My solution is not to have websites in /var/www. I place them in the user's home directory, modify apache's config to read from there (e.g. using virtual hosts) and jail the user to his/her home directory in vsftpd.

---

