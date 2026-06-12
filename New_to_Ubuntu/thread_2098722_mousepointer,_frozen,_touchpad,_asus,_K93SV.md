---
title: "mousepointer, frozen, touchpad, asus, K93SV"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by aeolibus on 2012-12-27
Since yesterday the mousepointer of my user account got frozen.

Everything was fine when I went to sleep, I left the system swiitched on for the night.

No new programs were installed recently.


Note that : 
- System has been working just fine for a year;
- Over the past year the mousepointer froze a few times for no apparent reason, exiting the session and logging in again solved the matter at all occasions, but not this time; 
- Rebooting doesn't resolve the issue either; 
- The touchpad -and mousepointer - work in the login-screen, but freeze upon arriving in the user session.
- When I plug in an external USB mouse it works whilst the touchpad refuses to cooperate; 
- The touchpad and mousepointer work perfectly in a guest session!

Since the touchpad works in the login screen and in a guest session I assume - in all modesty - that it isn't a hardware related problem.

Any suggestion how I can get the touchpad working again in my user account?
Or can you help pointing my nose in the direction of a possible solution?

Th .odt in attachment is actually a html file of my 

lshw >> html

Thanks beforehand for your help and time,

Bert

---

### Post by slickymaster on 2012-12-27
There's a bug report that reports this:

[URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727"]Touchpad stops working after login
Ubuntu “xserver-xorg-input-synaptics” package Bugs Bug #549727[/URL]

Try this at a terminal window:
```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

---

### Post by aeolibus on 2012-12-27
Thanks slickymaster,

Your suggestion made the touchpad come to life again, but :   
 
[LIST]
[*]I did notice however that the touchpad settings tab (switch 	off touchpad while typing , slide scrolling and other touchpad settings) has 	disappeared from the mouse and touchpad settings  in the system 	settings menu. It now only has a tab for mouse settings.
So it 	seems the system now considers my touchpad to be a mouse and that's not really what I was looking for.

[*]The tweak doesn't survive a boot.
After rebooting the pointer is locked again.
[*]Any other suggestions as to how I could tackle this problem. Isn't there a way to 'refresh' the touchpad driver so that the system works as before?
[/LIST]

---

### Post by slickymaster on 2012-12-27
> **aeolibus said:**
> I did notice however that the touchpad settings tab (switch 	off touchpad while typing , slide scrolling and other touchpad settings) has 	disappeared from the mouse and touchpad settings  in the system 	settings menu. It now only has a tab for mouse settings.
So it 	seems the system now considers my touchpad to be a mouse and that's not really what I was looking for.

That's really strange and unexpected. 

> **aeolibus said:**
> The tweak doesn't survive a boot.
After rebooting the pointer is locked again.

Include this line of code:
```
sudo modprobe psmouse proto=imps
``` in **/etc/modprobe.d/options**.

If by any chance your system doesn't have a file called options in that path, I'm attaching an .sh file, and I changed 'sudo' to 'gksudo' so you'll get a graphical interface question for the root password instead of a commandline version. You can download it in your **/home** directory, and make it run every boot by going to System -> Preferences -> Startup Applications and click on 'Add'. Type anything in the name section, and type this command in the command section:
```
sh ~/workaround.sh
```

---

### Post by slickymaster on 2012-12-27
Another alternative is to created a file with the following command:
```
options psmouse proto=imps
```
(options instead of sudo), named it **touchpad.conf** and put it in **/etc/modprobe.d/**

Hopefully, one of these two solutions will work for you, permanently.

---

### Post by aeolibus on 2013-01-27
Sorry I didn't reply any sooner. Have been quite busy.

In the meantime I've found a command that solved the touchpad-mousepointer matter completely. 

Thinking that it must have been a system setting being wrongly set by one of the programs that I run, I started looking for ways to 'reset' or restore Ubuntu to it's initial 'out of the box' state without loosing all the program specific settings.

On of the first hits on  askubuntu.com was : 
[http://askubuntu.com/questions/72119/how-do-i-restore-default-settings-and-configuration-but-keep-local-data-instal](http://askubuntu.com/questions/72119/how-do-i-restore-default-settings-and-configuration-but-keep-local-data-instal)

Following command followed by a reboot did the trick. Everything works perfectly ever since.

rm -r ~/.config/ ~/.cache/

Haven't been able yet to determine though which program has been causing 
the problem in the first place. (I don't tweak settings myself.)

---

