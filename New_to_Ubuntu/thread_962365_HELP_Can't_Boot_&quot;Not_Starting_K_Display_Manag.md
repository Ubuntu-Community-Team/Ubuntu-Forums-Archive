---
title: "HELP: Can't Boot: &quot;Not Starting K Display Manager (kdm-kde4)"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Matt86 on 2008-10-29
OK,

I'm running Kubuntu 8.10 on a HP compaq nx7010 laptop.

When booting I now get the message:

grep: /user/lib/kde4/etc/kde4/kdm/kdmrc: no such file or directory
Not starting K Display Manager (kdm-kde4); it is not the default display manager

I can only guess that this is attributed to me installing an ATI driver in the previous session. I was having issues with Kubuntu not shuting down, restarting, or logging off (just a black screen with the cursor showing) and found some information suggesting it might be attributed to ATI graphic cards.

I have an ATI mobility radeon 9200 so I installed an ATI driver from adept (as there was no ATI folder in /etc and hardware drivers didn't detect any driver).

Following this, I got the afore mentioned error - so I cannot enter Kubuntu. 

I tried entering recovery mode and using:
sudo dpkg-reconfigure xserver-xorg 

However, after setting up the keyboard for configuration I get a prompt from xserver saying that it may override existing configuration and it is making a backup, and then nothing happens.

If anyone knows anything that might help me resolve the situation I'd be greatly appreciative - I really don't want to have to reinstall merely because of my incompetency without a GUI.

Thanks,
Matt

---

### Post by Borgond on 2008-10-30
Hi Matt, 

first of all I think your guess is right. I ran into exact same problem with my upgrade to 8.10 some hours ago.

I am not fully able to reproduce my steps because I tried a lot of things but you could try the following:

Go to a console Ctrl-Alt-F1, login and add 

```
Driver      "vesa"
```  

to your xorg.conf in /etc/X11/xorg.conf in the "Device" section

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "vesa"
EndSection
```

Then I installed gdm (maybe not necessary) and selected it as the default Display Manager.

Killing the X Server on display (Ctrl-Alt-F7) and Ctrl-Alt-Backspace should now restart X with unaccelerated graphics drivers and a login manager. Select your Session from the bottom left (KDE) ... log in.

Logging into KDE a popup notified me that there are restricted drivers that would enhance my performance ... Click it, Install and activate the restricted drivers.

Reboot 

This worked for me - maybe it works for you as well.

Oh - and I switched back to KDM using

```
sudo dpkg-reconfigure gdm
```

Cheers, 

   Borgond


References:
[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/")
[http://www.michaellarabel.com/index.php?k=blog&i=114]("http://www.michaellarabel.com/index.php?k=blog&i=114")

---

### Post by Matt86 on 2008-10-31
Thanks for offering your help, glad to know I wasn't the only one with this issue!

I ended up doing a fresh install with the official release of 8.10 - I hadn't been using my system for very long, so it wasn't a huge loss, just a pain.

I couldn't actually get xserver to start, and without finding a solution (this was before your post) I caved in to my frustration.

Thanks anyway!

---

### Post by stephan0h on 2008-11-17
just for the record: had the same problem - and a "sudo dpkg-reconfigure xserver-xorg" solved it for me.

cheers,
stephan

---

