---
title: "Ubuntu Tweak - Resets on Reboot"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by julian2 on 2013-09-03
Hey, so i have redirected my user folders to my internal 1tb but everytime i reboot they rest and i have to reapply the change...?

Help?

---

### Post by Crusty Old Fart on 2013-09-03
I'm not exactly sure what you're asking. Perhaps you could word it a little differently or provide a little more detail.
Did you do something like move your user folders to your internal drive, and subsequently made symlinks to them in your home directory?
What do you mean by "redirected my user folders"?

---

### Post by AFriendlyNerd on 2013-10-19
I had this problem and it came down to a technical glitch with how, and then where, my partition was mounted. It may have been excacerbated by the fact I chose an NTFS partition, so I could share it with the many OS' and devices in my home. First, I learned how to mount my drives using fstab: [#201]("http://ubuntuforums.org/showthread.php?t=293513&p=9769731#post9769731") 

Then I found out that due to the way recent Ubuntu builds treat certain folders, the folders were in a bad place. Specifically, my partition was mounted inside /media/username, meaning only username could own that mount. I moved it one level above, (umount drive, mkdir, edit fstab, mount -a), to /media/, and now everything works great. [#40]("http://ubuntuforums.org/showthread.php?t=2171268&p=12775886#post12775886")

I'm a complete n00b so all please forgive if I'm giving bad answer. But I learned it here! ;)

---

