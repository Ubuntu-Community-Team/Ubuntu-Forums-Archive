---
title: "Help when upgrading from gutsy gibbin to FF!"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by djowtlawz on 2008-04-24
Help when I was upgrading from gusty gibbon to the latest version feisty fawn (8.04) I ran into some errors like "Cannot Install 'xorg'" and it said that it would leave the configuration alone. (I have the exact errors but they are written on my tomboy on the OS I cannot access.)

Now that I have restarted my computer I can't even log in because of the xorg xserver I presume. When trying to dpkg-reconfigure xserver-xorg I get a message saying xserver-xorg is either missing or corrupt!

I tried reinstalling my NVIDIA drivers but nothing! Help please! A similar thing happened even during the BETA and I had to reformat and reinstall.

Thanks any response would be greatly appreciated.

---

### Post by Paqman on 2008-04-24
Can you boot into recovery mode? If so you could try and reinstall X.org from there.

---

### Post by Dark Aspect on 2008-04-24
I think you mean Hardy Heron because feisty fawn was 7.04 and not 8.04,anyway you could try to recreate the xorg file and then run dpkg-reconfigure xserver-xorg.Boot from the LiveCD and create a file called xorg.conf in your /etc/X11/ folder.Make sure its the etc folder on your computer and not the LiveCD.If that fails you could copy the xorg file from the LiveCD to you hard drive that "might" restore defaults.

Other than that one possibility,I think it would be best to reinstall.

---

### Post by ace007 on 2008-04-24
Version 8.04 has been dubbed Hardy Heron.  Version 7.04 was called Feisty Fawn.  Gutsy Gibbon is 7.10.  Have you tried
```

sudo dpkg-reconfigure -a

```

---

### Post by djowtlawz on 2008-04-25
1) No I can't boot unto recovery

2) sudo dpkg-reconfigure -a - didn't work

3) > I think you mean Hardy Heron because feisty fawn was 7.04 and not 8.04,anyway you could try to recreate the xorg file and then run dpkg-reconfigure xserver-xorg.Boot from the LiveCD and create a file called xorg.conf in your /etc/X11/ folder.Make sure its the etc folder on your computer and not the LiveCD.If that fails you could copy the xorg file from the LiveCD to you hard drive that "might" restore defaults.

Other than that one possibility,I think it would be best to reinstall.

I may have to reinstall but do you think it is best to reinstall with GUTSY again or just reinstall with Hardy Heron?

---

### Post by doorknob60 on 2008-04-25
Hardy should work fine if you're reinstalling, something weird probably happened during the upgrade that probably won't happen with a clean install.

---

