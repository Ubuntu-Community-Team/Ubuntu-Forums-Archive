---
title: "Cannot access any files in  Ubuntu 12.04"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Norman Thom on 2012-04-26
I have just upgraded Ubuntu 11.10 to 12.04
What a mess!
It boots more or less
shows my desktop with my chosen background but no menu bar on top
or on the left side
I am asked to enter my password to unlock keyring but the window will not accept input from my keyboard.  I have one file folder on my desktop but when I open it it has no header. Perhaps if I could reconfigure x I could repair this but I have no way of doing this.  Does anyone have any ideas without my losing all my files.  It should be notices that when I first upgraded all was fine. This seemed to happen after I was asked to install drivers for the nvidia video card.  I chose the recommended driver and reboot when told and this is when the problems started

---

### Post by cryptotheslow on 2012-04-26
If you can get a Terminal to open (Ctrl-Alt-T from the desktop) you could try running:

```
jockey-gtk
```

to get the Additional Drivers dialog to open where you can remove the nVidia driver.

Alternatively you could try the Unity 2D environment by clicking on the cog next to your name before logging in.

If really stuck you should be able to get to a command prompt login by using Ctrl-Alt-F1 (or even Recovery Mode from the GRUB menu if necessary) and from there amend whatever configuration files need to be. Sorry, I've no specific guidance on how to uninstall or deactivate the nVidia driver from the command line. Hopefully someone will be a long soon who does.

---

### Post by Norman Thom on 2012-04-26
Thanks Crypto:

Will do. Hope someone tells me when I'll be able to install the appropriate drivers.

You've been a big help

---

### Post by cryptotheslow on 2012-04-26
What nVidia card or chipset do you have?

There were some nVidia related glitches during the testing cycle - knowing what card you have may mean someone who worked through them can help you more.

---

