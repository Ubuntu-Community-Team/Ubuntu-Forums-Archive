---
title: "Switch Keyboard Layouts"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by cheatos on 2012-10-20
Hi all,

I recently have bought a new keyboard with american keyboard layout and I now want to be able to switch the keyboard layouts by clicking or entering a special key-combination or whatsoever and not need to reconfigure it by using system settings.

However I only need to switch between German and American layout, so there doesn't need to be a selection menu or stuff, a simple button would be enough.
I know there is something in Windows as I sometimes accidently click that button and then I write with a different layout but I haven't found a configuration for this in lubuntu.
I have seen the Input Method Switcher but that thing crashed when I tried opening it :(

Thanks for any help!

PS: I can't switch to windows for keyboard switchgin as I want to use Kile and any LaTeX editor I tried to use under Windows wouldn't work...

---

### Post by cheatos on 2012-10-23
bump

---

### Post by NikTh on 2012-10-23
This is an example for Alt+Shift keyboard keys combo to change the layout from American to German (and vise versa)

Open lxterminal and copy-paste this command ```
echo '@setxkbmap -option grp:alt_shift_toggle "us,de"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart
```

Do not forget to right click on panel and "add/remove items"and add the Keyboard layout switcher (or something like that) so you can see the country flags . 

Logout - login and you will be able to switch between us(american) and de(german) with Alt+Shift keys combo. 

Thanks

---

### Post by Rex Bouwense on 2012-10-23
Have you looked here:
[http://lxlinux.com/#17](http://lxlinux.com/#17)
Those of us who use Lubuntu should have this great piece of work composed and maintained by seppalta bookmarked.  It is a time saver.

---

### Post by cheatos on 2012-10-25
Hey there,

I have tried copying your code but however it does give me some output but does not affect something. I even tried rebooting but there is no switch. Where should this switch e located

I havent read the website you recommended yet, because of to litle time...

Thanks for your help!

---

### Post by cheatos on 2012-11-01
bump again

---

