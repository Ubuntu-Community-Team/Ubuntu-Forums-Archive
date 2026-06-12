---
title: "Write permissions problem, I think"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by eberndl on 2008-08-03
Hi,

I'm getting write permissions problems with Thunderbird and now Frostwire, and I need to know how to fix them.  However, that's not all that is happening.

After my Firefox updated itself sometime last week, my Thunderbird stopped working.  It told me it was already running, and it most certainly was NOT.  But, the interesting thing was that if I tried to open Firefox after getting this message on thunderbird, firefox also gave me the message, but it didn't if Firefox was opened first.

So I figured out that my prefs.js for Thunderbird was corrupted, and was able to replace it.  Thunderbird now opens just fine.  In both XP and Ubuntu.  and in XP, it can d/l new mail.  But In Ubuntu, I'm told that I don't have write access to my shared drive. I'm getting the same problem with Frostwire (my downloads also go to my shared drive).

Can anyone maybe help?

---

### Post by billgoldberg on 2008-08-03
> **eberndl said:**
> Hi,

I'm getting write permissions problems with Thunderbird and now Frostwire, and I need to know how to fix them.  However, that's not all that is happening.

After my Firefox updated itself sometime last week, my Thunderbird stopped working.  It told me it was already running, and it most certainly was NOT.  But, the interesting thing was that if I tried to open Firefox after getting this message on thunderbird, firefox also gave me the message, but it didn't if Firefox was opened first.

So I figured out that my prefs.js for Thunderbird was corrupted, and was able to replace it.  Thunderbird now opens just fine.  In both XP and Ubuntu.  and in XP, it can d/l new mail.  But In Ubuntu, I'm told that I don't have write access to my shared drive. I'm getting the same problem with Frostwire (my downloads also go to my shared drive).

Can anyone maybe help?

I don't use Thunderbird (I do use frostwire) but if you shared folder is in the /home, it should not happen.

You could always open frostwire as root (sudo frostwire) to avoid this problem, but it's not adviced to do so.

--

If you get the "firefox is still running" thing again, use

```
pkill firefox
```

And then start firefox again.

--

Sorry I can't help more.

---

### Post by eberndl on 2008-08-03
No, none of these point to the /home folder.  They point to a FAT32 drive that I use for info I want accessable regardless of if I boot in Windows or Ubuntu (currently in Windows b/c of the Fx problems).  I think that somehow the permissions for that entire drive got f*cked for Ubuntu, because I can access them (and change them) through XP.

But I will try the pkill firefox now, when I reboot in Ubuntu.

[edit]
And now it magically heals itself.  Stupid computers.
Thanks very much though billgoldberg

---

