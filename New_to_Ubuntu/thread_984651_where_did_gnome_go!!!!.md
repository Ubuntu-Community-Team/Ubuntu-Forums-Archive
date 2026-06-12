---
title: "where did gnome go?!?!?!?!"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Maximusmaximus on 2008-11-16
i booted up my computer today and it did its usual start up sequence and after the Ubuntu loadning screen it sent me to a balnk screen with only this written:


starting up...
loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-vvid/83cdc2b3-fe2d-4320-9754-b63b2087cc0f) = sda(8,5)
kinit: no resume image, doing normal boot...

ubuntu 8.04.1 kev-desktop tty1

kev-desktop login:



does anywhere know where gnome went? if it helps i had a compiz-fusion desktop run by an Nvidia 7800 series with the latest drivers all working perfectly.

---

### Post by cariboo on 2008-11-16
You might want to start in recovery mode, and when you get to the menu try **xfix**, when it is done select continue booting.

If that doesn't start you in at least lowres safe graphics mode, then your problems are a little bit bigger.

Jim

---

### Post by Maximusmaximus on 2008-11-16
how do i restart the computer in recovery mode>?

---

### Post by OutOfReach on 2008-11-16
```

reboot

```

---

### Post by 73ckn797 on 2008-11-16
> **Maximusmaximus said:**
> how do i restart the computer in recovery mode>?


If pressing the "escape" key does not display the boot menu with the second option of recovery mode, then you do have a problem. You will have to do this after the initial post screen displays on boot-up. You may see a count-down occurring which gives you the time to press escape to enter the grub options menu.

---

### Post by Maximusmaximus on 2008-11-16
all of the above worked going through Xfix, but it only sent me back to square one. what could the problem be?

---

### Post by SunnyRabbiera on 2008-11-16
uncertain, perhaps an update broke gnome or something.
But dont worry if you still need a gui try sudo apt-get install kubuntu-desktop if you can only do terminal right now

---

### Post by redjoel on 2008-11-17
Try this
[ubuntu white death screen]("http://travel567.890m.com/2008/09/resolving-ubuntu-white-death-screen.rdj")
sorry giving u just a link, because i online using operamini

---

### Post by Maximusmaximus on 2008-11-17
> **SunnyRabbiera said:**
> uncertain, perhaps an update broke gnome or something.
But dont worry if you still need a gui try sudo apt-get install kubuntu-desktop if you can only do terminal right now

ok.. its telling me its an invalid operation

---

### Post by qjmoss on 2008-11-17
This happened to me once, what you might have done is installed and app. from a different distro.  If so, find that app. and uninstall. I didn't really read your whole post. But i found the same error awhile ago for me. 

Who knows.

---

### Post by Maximusmaximus on 2008-11-17
> **Maximusmaximus said:**
> ok.. its telling me its an invalid operation

dont worry about that i type it in wrong

---

### Post by matmarroba on 2008-11-18
> **SunnyRabbiera said:**
> uncertain, perhaps an update broke gnome or something.


I have the exact same problem. And it was because of upgrading firefox-3.0! Some other packages were also being upgraded, but I noticed right before rebooting that I couldn't restart firefox after the upgrade. So I reboot and this kinit thing shows up, followed by "\nUbuntu 8.04.1 name tty1\n\nname login: "

I uninstalled firefox (sudo apt-get remove firefox-3.0) and rebooted, but it doesn't solve it. I don't know how to access some kind of upgrade-log or aptget-log so I could perhaps see what other packages was in that upgrade manager-batch.

This is a real serious problem, guys! Help!

---

### Post by matmarroba on 2008-11-19
*bump*

---

