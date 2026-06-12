---
title: "Permissions for Access to Shared Directory"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by Sam_Carpenter on 2014-06-23
Hi All,

I am new to Ubuntu and have been having some problems.

I recently rebuilt an old Dell Tower PC with Ubuntu 14.04 as it was gathering dust in the corner.  I've started to use it on my home network to backup files through creating shared directories and giving access to all on the network, my users merely drag and drop files into the shared folder.

Here comes the problem...

I recently found an old 160GB HDD amongst my things, I have reformatted it and my PC now recognises it as a shiny empty hard drive.  Having put the same permissions on the drive I put on the folder on my original hard disk, my other PC's can see the directory but no one is allowed in aaaaaaarrrrrrgggghhhh.

Thanks for any help, I will provide further details if needed.

Sam
Linux N00B

---

### Post by SeijiSensei on 2014-06-23
Are you using Samba?  If so, you need to set permissions at both the operating system level and in the share definitions in smb.conf.  You might start [here](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html).

---

### Post by Sam_Carpenter on 2014-06-24
Hi,

Thanks for replying I have looked into this but am struggling, I really don't know my way around a command line too well.

:(

I shall try my utmost to resolve this based on the info given.

Kind Regards

Sam

---

