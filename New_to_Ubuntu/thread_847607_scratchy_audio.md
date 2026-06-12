---
title: "scratchy audio"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by asmugone on 2008-07-02
Hey gang,

The problem is that all of a sudden my sound is super scratchy and unless I turn pcm all the way up it is almost impossible to hear. I dont know what happened it just started. Also I now have to manually type in sudo dhclient everytime i start my computer to communicate with my cable modem. Problems started around the same time but I havent dont anything, strange huh.
oh aplay -l yields

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I have tried my speakers on another system and they work perfectly. Plz help.

---

### Post by asmugone on 2008-07-02
bump

---

### Post by asmugone on 2008-07-02
followed the comprehensive sound guide btw and got no love, im going to try these automated scripts. oh and in system->prefrences->sound it list my audio card via 8237 twice in the drop down menus, both sound scratch but one sounds a little less bad then the other, fyi

---

### Post by asmugone on 2008-07-02
used the autopmated scripts and those didnt work either, im going to wipe and go with a fresh install, guess no one can help me :((

---

### Post by markbuntu on 2008-07-02
Before you do that, try logging in in a different setting like xfce or gnome or gnome safe mode. This will reset a lot of defaults.

Another thing you can do is when grub comes up when you boot to choose a previous kernel and see if your things work with that.

---

### Post by asmugone on 2008-07-02
I dont have a option for alternate like that in the user login screen, I also dont have other desktops installed like that, plus this is my fathers system and im not about to throw him to the wolves by changing up like that on him lol

---

