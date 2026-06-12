---
title: "Reinstalling Pulse or Alsa"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by aronkindi on 2014-01-09
I don't what is the difference between both drivers. I think I mess here in my notebook trying to install both drivers at the same time and the icon of sound doesnt appear anymore.
Now, I don't know which of them I have. I'm trying to uninstall all the sound drivers to install since the beginning a new  all the time that I try to uninstall running this command: [COLOR=#444444][FONT=Arial]sudo apt-get remove --purge alsa-base pulseaudio[/FONT][/COLOR]  . I get this error:
" 
Building initial module for 3.8.0-35-generic
Error! Bad return status for module build on kernel: 3.8.0-35-generic (x86_64)
Consult /var/lib/dkms/alsa-hda/0.201210261053~natty1/build/make.log for more information.
dpkg: error processing alsa-hda-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 alsa-hda-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

Any help for a noob? Thanks

---

### Post by ian-weisser on 2014-01-09
Um, you do realize that purging pulseaudio will remove huge chunks of your system, right?
A successful remove of pulseaudio should also remove most of your desktop environments (they depend upon PA), leaving you with a command-line only system.

---

