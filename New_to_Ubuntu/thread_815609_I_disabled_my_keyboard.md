---
title: "I disabled my keyboard???"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Brenegars on 2008-06-01
I'm running Hardy (8.04) on a Dell XPS 1530, dual booted with vista. I am completely new to linux, just trying it out. I was editing the xorg.conf file, trying to configure it for gsynaptics so i could use my touch pad.(i backed up xorg.conf first) I've read several places that you need to save the file with an extra line of code in order for gsynaptics to work. (is this even the right thing to do?)

I put this line at the end of the section for the Synaptics Touchpad. 

Option      "SHMConfig"       "true"

 I saved the file, restarted my computer, and for some reason my keyboard no longer works in Ubuntu. Everything works fine in my Vista partition, but the keyboard doesn't respond in Ubuntu. I have no idea what to do, this is my 3rd day ever using Linux.

Any Help would be appreciated!

---

### Post by NT4usB on 2008-06-02
There should be a five second interval before Ubuntu boots where you could hit Esc to pause the boot and select another boot option (recovery mode?) or something... I've never had to do it but I've read about it.
Or, couldn't you boot to vista, edit the xorg.conf (it's just a textfile) or just rename and switch back to your backup copy, then boot Ubuntu?
Then, there's always boot to the Ubuntu Live CD, mount the drive, and edit xorg.

---

