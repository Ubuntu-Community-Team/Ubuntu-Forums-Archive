---
title: "Installing new Ubuntu on existing dual boot"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by malevolent-decadent on 2014-05-02
I currently have Vista dual booting with Ubuntu 12.04. However, I managed to break the GUI on my ubuntu installation some time ago and gave up trying to fix it. Is there a way I can SAFELY install 14.04 over that partition without destroying my dual boot setup in GRUB?
Any help would be appreciated

---

### Post by oldfred on 2014-05-02
First backup both Windows and any data in Ubuntu that you want to save.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Is /home a separate partition? Then you can reuse / (root) and reformat it, but DO NOT reformat the /home partition. You use the Something Else option.

I think all settings will ve overwritten with standard settings so best to backup up anything you think you may want to save.
      
 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

This is what I backup, but from my working system:
      
 Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541
[/URL]
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834
      [/URL]
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

    
Attached shows me over installing on a partition on sdc that had an old install using change, since I was not adding partitions.


[URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

---

