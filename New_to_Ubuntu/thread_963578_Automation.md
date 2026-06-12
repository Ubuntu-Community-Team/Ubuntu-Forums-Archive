---
title: "Automation"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by G_Alexander on 2008-10-30
Hi

If I have gnupgc installed with and a default private key setup, then is it possible with ubuntu linux to set up some sort of script that will automatically and without interaction...


 * Encrypt the contents ...\desktop\confidential
   without asking for the private key password

 * Wipe original contents

 * Copy encrypted contents to two different hard drives connected

 * Burn encrypted contentst to DVD-R

 * Empty ...\desktop\confidential


Many thanks

Grant

---

### Post by Sarmacid on 2008-10-30
> **G_Alexander said:**
> 
 * Wipe original contents

 * Copy encrypted contents to two different hard drives connected

 * Empty ...\desktop\confidential


You can set up a cron job to do these automatically, and if the other options can be done from command line(I suppose they can, just not sure) then you can get cron to execute a script periodically.

Here's a post explaining cron [http://ubuntuforums.org/showthread.php?t=102625](http://ubuntuforums.org/showthread.php?t=102625)

---

