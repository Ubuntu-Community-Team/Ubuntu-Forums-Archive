---
title: "Defaulting to CLI on boot"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by warm cardigan on 2012-08-04
Hello,

A very simple question regarding my Xubuntu 12.04 installation: is there any way to default to a Terminal/console interface, as opposed to booting into XFCE immediately? I would like to be able to choose to go to the GUI, but not necessarily immediately.

Thank you,

/wc

---

### Post by sisco311 on 2012-08-04
You can disable the display manager (LightDM):

```
echo "manual" | sudo tee /etc/init/lightdm.override
```

In order to re-enable the X display manager you have to delete the .override file created by the previous command.

You can start the X session with the **startx** command. Or,as root, you can start the DM:
```
sudo initctl start lightdm
```

---

### Post by dodo3773 on 2012-08-04
In GNU / Linux you are auto logged in usually in most distros by your display manager. Also known as a DM for short. In Ubuntu it is called lightdm. So, if this is not a feature you want you can just:
```

sudo apt-get remove lightdm
sudo reboot

```

Then you will be presented with a login console where you will have to type your username and password. After which you can type startx or use xinit etc.. To load your gui. 

I found this a little while back as well which may be of interest to you:

[s][http://virtual-drive.in/2012/05/20/ubuntu-12-04-text-boot/](http://virtual-drive.in/2012/05/20/ubuntu-12-04-text-boot/)[/s]

Scratch that link. This is probably all you need to do:
[http://www.techienote.com/2012/05/how-to-disable-gui-boot-in-ubuntu-12-04.html](http://www.techienote.com/2012/05/how-to-disable-gui-boot-in-ubuntu-12-04.html)

---

### Post by warm cardigan on 2012-08-05
> **sisco311 said:**
> You can disable the display manager (LightDM):

```
echo "manual" | sudo tee /etc/init.d/lightdm.override
```

In order to re-enable the X display manager you have to delete the .override file created by the previous command.

You can start the X session with the **startx** command. Or,as root, you can start the DM:
```
sudo initctl start lightdm
```

Looks like I should have done this, as opposed to having removed lightdm altogether. As things stand, I followed Dodo's advice; Terminal did mention that xfce-desktop would be removed if I removed lightdm, but I have uninstalled various things that say that they will do just that and then don't - I assumed it was just a slightly indirect way of saying, "We don't really want you to do this...", so I went ahead and uninstalled lightdm. Upon re-booting, my Xubuntu splash screen comes up, and then stays up. F11 tells me that it is hanging at "Checking battery state". This means that I can no longer boot into either a GUI or CLI interface, and my laptop is essentially useless. Do I need to reinstall Xubuntu, or is there some way to get around this and reinstall xfce-desktop?

---

### Post by dodo3773 on 2012-08-05
> **warm cardigan said:**
> Looks like I should have done this, as opposed to having removed lightdm altogether. As things stand, I followed Dodo's advice; Terminal did mention that xfce-desktop would be removed if I removed lightdm, but I have uninstalled various things that say that they will do just that and then don't - I assumed it was just a slightly indirect way of saying, "We don't really want you to do this...", so I went ahead and uninstalled lightdm. Upon re-booting, my Xubuntu splash screen comes up, and then stays up. F11 tells me that it is hanging at "Checking battery state". This means that I can no longer boot into either a GUI or CLI interface, and my laptop is essentially useless. Do I need to reinstall Xubuntu, or is there some way to get around this and reinstall xfce-desktop?

You shouldn't have to reinstall. Just install the packages that you removed (didn't know xfce-desktop had lightdm as a dependency (no clue why it does)). Can you switch to a tty (ctrl+alt+F2 (or F3,F4, etc..))? Then just follow sisco311's advice. You may still want to read the link I mentioned earlier though.

---

### Post by warm cardigan on 2012-08-05
All right, now I'm confused.

I tty'd, then just tried startx, and up came my GUI. I suppose I didn't uninstall xubuntu-desktop at all...? Anyway, three weird things are happening now.

1. I have no sound anywhere on the system. No output devices are showing in Sound Settings, only a dummy output. Same with input devices, except for the lack of a dummy output. There is also nothing under the Hardware tab.

2. I suddenly seem to have loads of settings-options that weren't showing up under Applications Menu>Settings before this. Display, Desktop, Mouse And Touchpad, and a number of others are all new. I used to be accessing those through the Settings Manager, which incidentally appears to be the same as it was previously.

3. I cannot connect to any wireless network. This is an issue that I was experiencing previous to my disastrous CLI-boot endeavor; Xubuntu seems to think "wireless is disabled by hardware switch" even though it isn't. This issue appeared entirely out of the blue one day last week.

Helllllllllp! I feel like Scooby Doo in the mysterious mansion at the moment... utterly confused and somewhat frightened :P

---

### Post by dodo3773 on 2012-08-05
Usually a display manager will load dbus sockets, consolekit sessions, etc..etc.. Sound may be a different issue entirely not sure. Post your ~/.xinitrc file.

---

### Post by warm cardigan on 2012-08-05
> **dodo3773 said:**
> Usually a display manager will load dbus sockets, consolekit sessions, etc..etc.. Sound may be a different issue entirely not sure. Post your ~/.xinitrc file.

Where do I find the .xinitrc file? I looked through the root of the file system and also through the hidden files in /home/ and /home/lawrence with no success.

---

### Post by drs305 on 2012-08-05
Another option is to add the kernel option "text" to GRUB. It will boot to a terminal login screen if that is what you are looking for.

To enable this option, open /etc/default/grub as root with a text editor and add *text * to the **GRUB_CMDLINE_LINUX_DEFAULT=** line.  Save the file and run "sudo update-grub".

If you want to test it before making the change permanent, you can press 'e' after highlighting the entry on the Grub menu during boot. Cursor to the end of the 'linux' line and add *text*, then F10 or CTRL-x to boot.

---

### Post by dodo3773 on 2012-08-05
> **warm cardigan said:**
> Where do I find the .xinitrc file? I looked through the root of the file system and also through the hidden files in /home/ and /home/lawrence with no success.

Should be in /home/lawrence. It's okay. There may not be one by default. There could be a different way Ubuntu does things. But this should work:

~/.xinitrc
```

exec ck-launch-session dbus-launch startxfce4

```


Where startxfce4 is whatever your window manager is called. May be called something else. This would work if consolekit and dbus is what you are missing for your permissions. Again, I am not sure how Ubuntu does things these days.

---

