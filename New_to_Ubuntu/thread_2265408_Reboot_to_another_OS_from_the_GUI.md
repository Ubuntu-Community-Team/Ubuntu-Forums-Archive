---
title: "Reboot to another OS from the GUI"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by maurice9 on 2015-02-14
Hello all.
Am used to a Mac and just installed Xubuntu on a PC which is dual booted with Windows XP.
Am wondering is there a way to switch from one OS to another in the GUI?
Since am VNCed into the machine its hard to go and look at the local monitor and select which OS to boot into after the BIOS clears.

In Mac OS X there is StartUp Disc which lets you select which boot disc to boot into and there is a restart button as well.

Any apps that let you do this in Linux?
If so then I still have to figure out how to do this from Windows I guess.

Thanks much in advance

---

### Post by maurice9 on 2015-02-20
Bump??

---

### Post by ian-weisser on 2015-02-20
[EDIT] Ooh, oldfred's answer below is way better than mine was.

---

### Post by maurice9 on 2015-02-20
Hello ian-weisser...

Thank you for the reply.
am sorry if I am misunderstanding but by "benefit of choosing the OS a few seconds earlier" you mean earlier then?????

Right now I work out of my bedroom because am disabled.
I have all my boxes in another room and while I can go to the other room and select the OS at boot up it is a bit difficult.
So that is why I had asked as with Mac OS I am used to just selecting my windows bootup disc from the system preferences and letting the system reboot and VNC stays connected and eventually refreshes with the new OS booting.

My default OS in that case is OS X so if I reboot the Windows OS it automatically takes me back to Mac OS X.

I was looking for a way to do the same with Linux as my default OS and be able to go to another OS from the GUI while logged in through VNC..

Hope that makes sense.

Thanks much

---

### Post by oldfred on 2015-02-20
Grub can have a default boot and a one time reboot. So you still default to grub and Ubuntu but from Ubuntu can set it to auto boot once into Windows. 

More info here:
[http://unix.stackexchange.com/questions/43196/how-can-i-tell-grub-i-want-to-reboot-into-windows-before-i-reboot](http://unix.stackexchange.com/questions/43196/how-can-i-tell-grub-i-want-to-reboot-into-windows-before-i-reboot)

And:

 Reboot grub to different system default
[http://ubuntuforums.org/showthread.php?t=1310463](http://ubuntuforums.org/showthread.php?t=1310463)
sudo grub-reboot 1
sudo grub-reboot "Microsoft Windows 7"
Boot non-default entry only once
The command grub-reboot is very helpful to boot another entry than the default only once. GRUB loads the entry passed in the first command line argument, when the system is rebooted the next time. Most importantly GRUB returns to loading the default entry for all future booting. Changing the configuration file or selecting an entry in the GRUB menu is not necessary.
Note: This requires GRUB_DEFAULT=saved in /etc/default/grub (and then regenerating grub.cfg) or, in case of hand-made grub.cfg, the line set default="${saved_entry}".

---

### Post by maurice9 on 2015-02-20
Hello oldfred:

That is perfect,, that way I can boot into it once and be guaranteed I come back to the default OS,,,, Very nice,,, Thank you very much...

---

