---
title: "GRUB2 customization questions..."
date: 2012-10-15
forum: New to Ubuntu
---

### Post by pandacookie on 2012-10-15
I actually have two questions. The first is about customizing the border that surrounds the menu options on the GRUB2 menu. How would I make that area smaller? Or even get rid of the border altogether? I have a splash image and the border goes right through it. It looks messy.
 
Also, if I were to upgrade to 12.10 in a few days (I am on 12.04 now), would I have to do the edits to the GRUB2 menu all over again? Or will the edits remain as they are? 
 
Thanks in advance for any help.

---

### Post by oldfred on 2012-10-15
Moved thread. You were in Tutorials & tips.

Do not know about grub menu configuration. There may be some info here:
Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)


If you upgrade your settings will remain in most cases. Sometimes system settings which include grub are totally rewritten or it may give a choice on whether to keep your settings or change to the maintainers settings. So anything I maintain in /etc or system I make a separate backup of into /home so my regular backups of /home include any customization.

If you do not accept the maintainers version, it may not work. And sometimes you make customizations to fix something and the new version does not even need that fix anymore.  But I keep the copy just in case I need to add custom settings again.

---

