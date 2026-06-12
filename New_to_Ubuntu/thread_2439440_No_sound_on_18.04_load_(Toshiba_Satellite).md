---
title: "No sound on 18.04 load (Toshiba Satellite)"
date: 2020-03-27
forum: New to Ubuntu
---

### Post by dcabrera72 on 2020-03-27
[]("https://askubuntu.com/posts/1220875/timeline")            Disclaimer: new Ubuntu user.  Win 10 forced update crashed my machine, so went with Ubuntu. 

Prior to  update, everything was working. Post install, things are going well,  only no sound. Speakers or headphones.

Some Steps I already took after reading a few forums and here...


  Ran alsamixer and see that a generic card is default, HDMI is not. All towers are maxed out, headphones keep going to MM and lowest level

  Checked BIOS, no sound selections there

  Installed Pavucontrol and built in audio is /not muted. Port is set  to speakers, other option is headphones (unplugged). I plug in  headphones and shows plugged in, but no sound. System Sounds are set to  100%

  
Running youtube in the background, I see sound should be playing, but nothing out of the speakers. 

  
Any recommendations? Should I install sound drivers? Is there a way to remove and detect/install?

  
TIA 
Dave

---

### Post by dino99 on 2020-03-28
Welcome to Ubuntu :P

Goto System Settings -> Sound -> Output Device : select one and click on 'test' until you find the good device

If that fails, then from a terminal, run 'journalctl -b' and glance at warning/error related to sound and/or unkown hardware

---

