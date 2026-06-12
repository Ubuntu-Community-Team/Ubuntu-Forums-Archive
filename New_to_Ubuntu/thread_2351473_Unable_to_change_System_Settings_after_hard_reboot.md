---
title: "Unable to change System Settings after hard reboot -- Unity seems &quot;broken&quot;"
date: 2017-02-03
forum: New to Ubuntu
---

### Post by Grace_Palazzolo on 2017-02-03
I'm running Ubuntu 14.04 LTS. It locked up on me, and I did a hard reboot. (I had to reboot by physically holding down the power button.)

What happens now, is my wallpaper, my icons in the Launcher, my theme -- it is all gone. I am also missing stuff in my Launcher that was there, and there are icons there that I didn't have there before (or that I had removed when I started customizing). I am back to the default Unity theme.

But it's more than just a missing theme. As I say, the items I had in my Launcher are missing too. Some of these are a
real problem because I installed them through the Software Center, and so I do not know the Terminal command for them. And customizations like auto-hiding the launcher are gone, too. International keyboards that I had installed are gone.

Ubuntu now ignores any setting I try to make with unity-tweak-tool. I mean completely ignores. I am also unable to change theme or any other aspect of appearance using System Settings

When I try to auto-hide the Launcher using System Settings, it will not let me slide the swtich from "on" to "off". If I try to enable workspaces, the little checkmark next to "Enable workspaces" disappears as soon as I let go of the mouse. Same applies to "Add show desktop icon to deskbar".

And there is one more piece of weirdness. In the login screen, I have my wallpaper, custom icons, etc. (but not the keyboards). Once I log in, then it there are the problems that I have described. 

I am open for any suggestions on how to resolve this.

---

### Post by mc4man on 2017-02-03
If your dconf user file is corrupted then maybe just start fresh. To do that reboot. (or just do from current orig. user session.
At the login screen go ctrl+alt+F3 to go to  tty3
Login  in the tty console then run
```
mv .config/dconf/user .config/dconf/user.bak
```
Follow that with ```
sudo reboot
```
This will set you back with a fresh dconf user file

For app look in /usr/share/applications, add as desired to launcher by either DnD to the launcher or d. click & pin icon to launcher with a right click on.

---

### Post by cariboo on 2017-02-04
You may want to start in recovery mode, and run fsck on your /home partition if you have a separate one, or on / if you have everything in one partition. Use the following command:

```
fsck /dev/sdxX
```

where /dev/sdxX is the partition you want to run fsck on

---

### Post by Grace_Palazzolo on 2017-02-23
> **mc4man said:**
> 

For app look in /usr/share/applications, add as desired to launcher by either DnD to the launcher or d. click & pin icon to launcher with a right click on.

I didn't quite follow this part. What exactly I am looking for in this directory?

---

