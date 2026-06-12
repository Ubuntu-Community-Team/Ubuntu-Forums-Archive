---
title: "Windows ubuntu clock issues"
date: 2016-10-14
forum: New to Ubuntu
---

### Post by 6c45 on 2016-10-14
I know the clock issue with Windows in a dule boot has been
talked about a lot. But why can't a work around be included in
the installation to let us pick local or universal time during installation ?

---

### Post by yetimon_64 on 2016-10-14
_*[s]It is[/s]*_[s], with a checkbox on the location page of the installer whether to use UTC or not. Though not clearly marked as to what the checkbox is for maybe. A setting that can very easily be missed or wrongly set up for dual boot needs.[/s]

**Edit:** sorry OP, you seem to be correct. I just fired up the 16.04 installer and the checkbox for setting to UTC is no longer there. I am now checking if any bugs are noted for it and such.

**Edit 2:** Now I am really confused, I was remembering the older graphical installers having the checkbox, but it seems neither the 14.04 or 16.04 installer has such. Then again I used a text based installer on this install so also may be confusing it with the location settings on the text (minimal) installer, sorry for the mistake OP. It seems very strange to me that the graphical installer does not offer the option to set UTC as well.

Once installed and if the setting is wrong for your set up, then simply editing as root the file /etc/default/rcS and changing the line "UTC=yes" to "UTC=no" will fix the problem.
**Edit 3:** seems in some cases editing /etc/default/rsS can fail to change the time in newer releases [[COLOR=#0000ff]--see here--[/COLOR]]("http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/") for updated commands to do so if needed.

---

### Post by Frogs Hair on 2016-10-14
I fixed mine using the Ubuntu method @ the link.
[http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html](http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html)

---

### Post by Impavidus on 2016-10-15
I don't remember seeing a checkbox. If I remember correctly, the installer automatically chooses UTC if Linux only and local time if dual booting with Windows. So if it doesn't detect Windows during installation, like when you disconnect the Windows drive before installing Ubuntu, it will be configured incorrectly. But I'm not entirely sure, as the only computer on which I installed Ubuntu dual booting with Windows (XP), Windows had been set to use UTC.

---

### Post by Qew on 2016-10-15
> **Impavidus said:**
> I don't remember seeing a checkbox. If I remember correctly, the installer automatically chooses UTC if Linux only and local time if dual booting with Windows. 

That didn't happen in my case. My Windows was detected during installation. I then found that my Windows installation was showing UTC when it should have been showing British Summer Time (UTC+1). I fixed it using what was mentioned in the link mentioned by Frogs Hair.

I do agree with the OP that there should have been an option for this during installation to avoid this irritation, even if there are understandable reasons for setting the RTC to UTC.

---

