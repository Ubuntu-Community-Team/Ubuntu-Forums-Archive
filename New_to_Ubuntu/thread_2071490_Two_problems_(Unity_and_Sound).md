---
title: "Two problems (Unity and Sound)"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by JoshDempsey on 2012-10-15
After a few years I decided to use Ubuntu again.

So yesterday I loaded 12.10 into my machine several times for it to install, then on reboot lock up at the login screen. I tried onboard and external graphics, my memory passed memtest and the disc verified itself.

So anyway, I just installed 12.04 xubuntu with 1 minor problem (will go onto that later)

However I wanted unity from the login screen so I:

sudo apt-get install unity

It went successfully, so I re-booted only for there not to be an option. So I ran "unity" from terminal and it switched XFCE to unity. However it moved my windows to the right so the "x" to close apps etc. is not half off the screen. Very annoying.

It also doesn't have the nice purple theme that just ubuntu has. And also I'm not sure what it's called but the apps etc. don't use Ubuntu's "windows" (the gray bar and orange buttons) but they still use XFCE's.

So I need to know how to get the full unity experience while using Xubuntu, as in login from the very start.

I also need to know how to get my sound to work on this. I have the prop. graphics card drivers installed and alsa and pulse as well. I have Logitech speakers if it makes a difference.

Also note that every package has been upgraded after I updated the list of packages.

Any help would be great and I'm very greatful for the amazing community here and other places.

Thank you.

---

### Post by JoshDempsey on 2012-10-15
Bump for help. I still have the two issues.

---

### Post by MrSteve on 2012-10-15
for the sound try

menu > multimedia > pulse audio volume control

once open go to configuration tab
set built-in audio to none 
just leaving the logitech speaker entry

log out and back in speakers should work now ...

---

### Post by mikewhatever on 2012-10-15
If you wanted Unity, why did you install Xubuntu? Install Ubuntu 12.04 instead, and save yourself the trouble, ...unless of cause you actually like the trouble.

---

### Post by JoshDempsey on 2012-10-15
> **mikewhatever said:**
> If you wanted Unity, why did you install Xubuntu? Install Ubuntu 12.04 instead, and save yourself the trouble, ...unless of cause you actually like the trouble.

I know it does seem stupid, but both 12.04 and 12.10 refused to work at all. Hence why I had to go with  Xubuntu

---

### Post by audiomick on 2012-10-15
You could try using the alternate installer to install 12.04 (or 12.10 in a couple of weeks when it is officially released). It sometimes works when the standard installer doesn't.

---

### Post by JoshDempsey on 2012-10-15
> **audiomick said:**
> You could try using the alternate installer to install 12.04 (or 12.10 in a couple of weeks when it is officially released). It sometimes works when the standard installer doesn't.

Thanks but I got it installed correctly OK, however it constantly locked up at the login screen. I may try that still, however.

---

### Post by JoshDempsey on 2012-10-15
> **MrSteve said:**
> for the sound try

menu > multimedia > pulse audio volume control

once open go to configuration tab
set built-in audio to none 
just leaving the logitech speaker entry

log out and back in speakers should work now ...

This fails also. I click on "PA volume control" and nothing happens. It definitely is installed and running as a daemon though.

---

