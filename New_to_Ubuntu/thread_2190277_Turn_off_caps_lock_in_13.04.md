---
title: "Turn off caps lock in 13.04"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by bob brazie on 2013-11-26
How can I permanently turn off the caps lock key in 13.04?

Other versions I could find this in keyboards under options but can't find it in 13.04.

I keep turning on cap's locks by accident and end up typing it all over again.

dconfig possibly?

I have done a Google search and find nothing about this concerning 13.04

Thanks in advance. Bob.

---

### Post by Jonor on 2013-11-27
Speaking for the Gnome Desktop it can be disabled through System Settings > Region and Language > Layouts > Options > Caps Lock Behaviour.

---

### Post by bob brazie on 2013-11-27
Thanks but in the Ubuntu 13.04 Language there is no "options" choice.

There was in previous versions but I think it was under "keyboard". But there is no "option" choice in either.

Bob.

---

### Post by Jonor on 2013-11-27
Layouts is in my Region And Language, not Language Support, in case you are looking there (for 13.04).

---

### Post by bob brazie on 2013-11-27
All I find in my 13.04 install is Language Support. No Region and Language.

Bob.

---

### Post by Jonor on 2013-11-28
So now a search is needed to find why Region and Language is missing from your System Settings.
This is my System Settings :

[[IMG]http://i.minus.com/jbo8eFhpk7J4se.png[/IMG]](http://minus.com/i/bo8eFhpk7J4se)

---

### Post by bob brazie on 2013-12-01
I did a search in Ubuntu 13.04 and it returns only the "Language Support" icon in the system settings which has no "options" to select.

---

### Post by Jonor on 2013-12-01
Here is a screenshot of the packages that are installed on my (Gnome) box using the synaptic package manager when searching using the terms "system settings".

[[IMG]http://i.minus.com/jlAPOv8pVAqpD.png[/IMG]]("[URL=http://minus.com/i/lAPOv8pVAqpD)"][[IMG]http://i.minus.com/jlAPOv8pVAqpD.png[/IMG]](http://minus.com/i/lAPOv8pVAqpD)[/URL]

It might be worth comparing with what you have installed. See what you find. 
If i were you i would not make any changes without mentioning it on here first and making backups.
On a side note a non-tech solution for my keyboard is to put some small solid object like a piece of wood under the Caps Lock key if they are easy to remove which they are.

---

### Post by bob brazie on 2013-12-01
I just checked a copy of 12.04LTS and it only has "Language Support" in system settings and no "options" button available.

I remember that was not the case in other versions. Maybe an "update" removed what I am looking for.

I can't find a setting in dconf that would allow me to turn off cap's lock either.

Thanks. Bob.

---

### Post by Jonor on 2013-12-02
I noticed Gnome have changed around the arrangement of system settings with regard to options, layout and key behaviour quite a lot in the last few years since i change mine to other languages sometimes.
If you started with a 12.04 install from a disc image and then upgraded to 13.04, i would suspect, as you appear to think, that a package was lost in the upgrade. Here is another synaptic installed packages screen cap for "layout" :

[[IMG]http://i.minus.com/jcJf6LTFRkBVe.png[/IMG]]("[URL=http://minus.com/i/cJf6LTFRkBVe)"][[IMG]http://i.minus.com/jcJf6LTFRkBVe.png[/IMG]](http://minus.com/i/cJf6LTFRkBVe)[/URL]

---

### Post by heir4c on 2013-12-02
You can install the gnome-tweak-tool
Via Terminal:
```
sudo apt-get install gnome-tweak-tool
```

Or you use the UbuntuSoftwareCenter or Synaptic.

Then you must look via the Dash (UbuntuLogo): Tweak Tool (NOT gnome-tweak-tool)
Choose in the left menu: "Typing"
On the right you see the button for the Capslock (see screenshot)
Here you choose for "Capslock is disabled"
(The term "disabled" on the button is just to say that it is not yet set)
Also here you can set the Ctrl+Alt+Backspace to reload the xserver.

[IMG]http://i.imgur.com/TIEulVD.png[/IMG]

---

### Post by bob brazie on 2013-12-02
Thanks, that utility did the job!

Still wonder why that isn't in dconfig. Or I if it is I can't find it. <g>

Thanks. Bob.

---

### Post by vitalii-zdanevich on 2014-05-03
Lubuntu 13.04 - not working :(

---

### Post by bapoumba on 2014-05-03
> **vitalii-zdanevich said:**
> Lubuntu 13.04 - not working :(

May be here ?
[http://ubuntuforums.org/showthread.php?t=1782212](http://ubuntuforums.org/showthread.php?t=1782212)
[https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003185.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003185.html)

---

