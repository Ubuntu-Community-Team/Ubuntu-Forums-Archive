---
title: "bug in additional driver"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by Jessie_James_A._At on 2014-07-11
guys, what is this ive check the binary driver version 331.89 but it says no proprietary driver in use. how to fix this?

---

### Post by Hakunka-Matata on 2014-07-12
the graphics driver you're using is (open source), not proprietary, so it states that fact

---

### Post by deadflowr on 2014-07-12
I don't understand, did you simply select the option and expect it to change to the new driver, or something?

The steps should be, select the driver you want, then click apply, let it run (it needs to download and install the driver, it'll take time)  then restart.

If after restart it is still not listed as in use, open the nvidia setting program.(something like that, it'll be in the menu/dash...)
and then in X server display configurations, go to the right side and click save x configuration
this should open a save dialog, and will default to save the xorg.conf file.
When this happens it will need your password.

After this, try restarting again.

---

### Post by Jessie_James_A._At on 2014-07-12
can i used the legacy driver 304.117? @[[COLOR=#C61919]deadflowr[/COLOR]]("http://ubuntuforums.org/member.php?u=1276577")[COLOR=#000000]  thanks, i'll try it again..[/COLOR]

---

### Post by deadflowr on 2014-07-12
LOL.
I missed the buggy part entirely.
Re-reading I notice that a few are listed, errorenously, as open source.
All nvidia binary options are proprietary. The only open source should be the xserver xorg one.
If you want to file a bug about it, the program is called jockey, or jockey-gtk.
[Good bug reporting]("http://ubuntuforums.org/showthread.php?t=1011078")
[Reporting bugs]("https://help.ubuntu.com/community/ReportingBugs")
 
FWIW

---

### Post by buzzingrobot on 2014-07-12
> **Jessie_James_A._At said:**
> can i used the legacy driver 304.117? @[[COLOR=#C61919]deadflowr[/COLOR]]("http://ubuntuforums.org/member.php?u=1276577")[COLOR=#000000]  thanks, i'll try it again..[/COLOR]

You can check at nvidia.com to see which of their drivers are compatible with your card.

---

