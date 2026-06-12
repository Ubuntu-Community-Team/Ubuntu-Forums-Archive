---
title: "No sound after update, and other problems"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by personal-data-removed on 2008-05-31
I have done the update for the last kernel. 2.6.24-17.

After that i have some problems.

1st problem- I have no sound
I cant delete the linux-ubuntu-modules-2.6.24.12-generic, it gives a delete error at synaptic. (E: linux-ubuntu-modules-2.6.24-12-generic: subprocess post-removal script retorns exit status error 1)

The lspci return is
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 02)

I have tryed to install a lot of Alsa modules and Gstreamer plugins, but at no avail.

I also want to install totem but at add/remove programs gives a error, i have to uninstall linux-ubuntu-modules-2.6.24.12-generic first. ?!

How to uninstall this ?



2nd problem - Avant windows manager stoped working
The docking bay does not appear, its fully installed...



3rd problem - Nvidia resolution.
I have new driver installed. 
But at Ubuntu start in the password menu, i have low resolution,
and i always enter in ubuntu at 800x600, but cant save config to xorg ?!

Thanks for help

---

### Post by pawnrocket on 2008-05-31
Did you try changing your audio server? I had the same problem changing the server worked around the problem. 

System>Preferences>sound 

I switched from HDA Generic to OSS

For the Login Window resolution you can try to install "startupmanager"  and adjust the resolution from there.

---

### Post by personal-data-removed on 2008-05-31
Switching from Alsa to OSS:
Gives a error: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
I tryed the other options, all give error.

"install "startupmanager" and adjust the resolution from there"
I have it installed and the resolution there is 1024x768, dont work, i see the ubuntu login background too big and the password field to much to the right, wich indicates that a lower resolution is working.

I also cant make updates in the update manager, it gives the following error:
"Failed to lock /var/cache/apt/archives/lock"

I cant do the following updates:

jockey comon
jockey gtk
linux image generic
ubuntu modules 2.6.24-17 generic
ubuntu desktop

---

### Post by personal-data-removed on 2008-05-31
Perhaps the solution is to delete the: linux-ubuntu-modules-2.6.24.12-generic
But i cant delete this it gives an error, anyone knows how to delete this ?

---

### Post by personal-data-removed on 2008-05-31
I still cant get rid of this broken package giving synaptic errors...

How can i get rid of : linux-ubuntu-modules-2.6.24.12-generic

---

