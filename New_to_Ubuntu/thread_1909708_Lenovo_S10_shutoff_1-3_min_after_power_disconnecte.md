---
title: "Lenovo S10 shutoff 1-3 min after power disconnected"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by leinadsreiem on 2012-01-15
I have a Lenovo S10 laptop that i've been having power issues with. Power management says the battery is fully charged but when it's disconnected from the charging cable it shuts off shortly thereafter. I was wondering if anyone else has experienced this issue.

---

### Post by corrytonapple on 2012-01-15
Your laptop, like mine, have similar issues.  The power manager hibernates your computer, thinking that your battery is low, even if it is not.  Just turn it back on, and if it doesn't, then we'll have to go deeper.

---

### Post by leinadsreiem on 2012-01-16
I turn it back on it doesn't even make to BIOS splash screen. When you attempt to turn it back on after this the battery indicator light on the front of the computer flashes yellow three times. At this stage the computer either repeats this or turns on but doesn't make it to the the BIOS splash. The only way to boot successfully is with power cord attached. I don't know if this will make a difference but Jupiter 0.0.53 is installed on this machine.

---

### Post by corrytonapple on 2012-01-16
I doubt if it has anything to do with Jupiter.
Try looking up how to "Step Charge" your battery.  How old is your computer?
Also, you can report this as a bug.  Just google "ubuntu power manager bug" and report it as a bug.  They try to solve it ASAP.

---

### Post by saneearth on 2012-01-16
If it is merely hibernating there will not be a boot splash. If it is completely shutting off, it will also not come back up, but it will boot and there will be a splash screen. Either way is seems as if there are some power issues.

---

### Post by tcallahan1982 on 2012-01-21
I'm running 11.10 in Gnome 3 on a Viewsonic Viewpad, and having the same issues. Once I unplug the cord, it shoots a low battery warning, even if the charge indicator says 100%. Within a short span, it shuts down, and will not restart.

I loaded the new kernel today, and it got worse. If I'm live and unplug, 5 min. If I boot unplugged, 20 min.

---

### Post by corrytonapple on 2012-01-24
There is a risky method of going about this.  I personally use it myself in Debian Wheezy, what 12.04 will be based on.  It will work with 10.04 and up as well.
**Note:  This completely disables hibernate.  If you like to use it, you won't be able to.  Also, when the battery is truely dead, your laptop will just shut off, and your battery will be drained as far as it will go while powering your laptop.  If you have anything open, and it shuts down suddenly without something being saved, then you lose that data.**
I highly recommend doing this while doing something simple, so you don't lose data and you can figure out how long the battery will last.  Once you get that figure, always shut down about ten minutes before then.  You can push to only five minutes, but it is riskier.  Why?  Well, web browsing doesn't need your fan to move as much, nor you HDD.  So if you're doing something more system intensive, such as gaming or loading 10,000px images in GIMP (Like me :D), then your system uses more battery.  Thus, it could shut down sooner.
Now that you understand the risks and what it does, just do this:
Go to your system preferences and tell the system to hibernate on low battery.  GNOME 3 users, click on your username in the top right hand corner, then click System Settings.  Click "Power Manager" or something like that, and then tell it to hibernate only on low battery.  Unity users, just click that Ubuntu logo, and search for "power".  Click the one that says something about "power settings" or "power manager".  I don't use Unity, so IDK exactly what it is.
Now open up a Terminal.  GNOME 3 users, search for "Terminal".  Unity users, search for "Terminal" as well.  Open it.  Then type:
```
sudo nautilus /etc/polkit-1/localauthority/50-local.d
```
Type in your password.  It will not show up.
When nautilus opens with that window, go to **File > Create New Document > Empty Document**
That will open gedit.  Put in the code below.
```

[Disable hibernate]
Identity=unix-user:yourusernamehere
Action=org.freedesktop.upower.hibernate
ResultAny=no
ResultActive=no
ResultInctive=no
```
Where "yourusernamehere" is, put your username.  If you have additional users of the laptop, then you can *TRY* putting a comma, then another username.  I have not tried adding additional users like that, so I do not know if it will work.
Save the file as "disable.pkla", without the quotes.
Reboot and enjoy!

---

