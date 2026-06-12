---
title: "Windows doesn't boot from grub"
date: 2015-05-23
forum: New to Ubuntu
---

### Post by Hemil on 2015-05-23
Hi,
I have a HP-Envy dv6 which came with Windows 8 pre-installed. I installed ubuntu14.04 on it and it was all working fine.
Then I tried out the new Elementary OS after removing Ubuntu. It didn't work out as there was a lot of heating so I removed Elementary and installed Ubuntu 15.04.
Now, I can boot into Ubuntu, but there is no option for windows.
I tried formatting the Ubuntu partition and re-installing it, to no avail.
I tried Boot repair, but there wasn't any change after this either. 
here's the pastebin link:
[http://paste.ubuntu.com/11303053/](http://paste.ubuntu.com/11303053/)

When I boot, this is what I see a lot of options (line 26-43):
but windows bootmanager doesn't run.



Any help will be appreciated.

---

### Post by grahammechanical on 2015-05-23
This is what I see

> The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting),

Windows 8 reduces boot loading times by going into hibernation instead of a proper shut down. Try turning off Fast Startup and then loading Ubuntu and running

```
sudo update-grub
```

and see if the Windows 8 boot loader is detected.

Regards.

---

### Post by Hemil on 2015-05-23
hey,
I'm currently in Ubuntu and am unable to boot into Windows, so turning it off from the Power buttons isn't possible.
I tried to find it in the BIOS, but couldn't find it. I don't think its the same as SecureBoot, is it?
Is there a way to do it?

---

### Post by Geoffrey_Arndt on 2015-05-23
So, when someone has the good fortune (luck) to succeed in installing a dual boot (ubuntu & win8) . . . maybe best not to experiment with other installs/uninstalls, but instead to use a Live USB or DVD to explore other distros?:confused::confused:

These settings (hibernation, etc.) are often available also in the control center of windows, buried in one the higher level settings group.    Might be best to do a search Youtube for visual example.

[https://www.youtube.com/watch?v=OlFWw-Qb3qA](https://www.youtube.com/watch?v=OlFWw-Qb3qA)

---

### Post by oldfred on 2015-05-23
Since UEFI, you should be able to directly boot Windows from UEFI boot menu or one time boot key often f10 or f12, but varies.

Grub will not boot Windows with fast startup on.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

