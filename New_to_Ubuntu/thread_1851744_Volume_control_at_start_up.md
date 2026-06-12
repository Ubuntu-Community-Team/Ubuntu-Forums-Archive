---
title: "Volume control at start up?"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-09-28
This is probably an unusual inquiry... I have a Dell Inspiron 9400 laptop, running Ubuntu v10.04 LTS 32-bit. My problem is that when the computer boots up, the volume seems to be set at its maximum. I really like the default sound themes in Ubuntu (the bongos & the Gnome start-up sound), but when the computer plays them, they're LOUD! I don't want to change them; I just want them played softer. Like, maybe 1/4 or 1/8 of the default volume. As it is, I have to remember to plug in headphones before booting, in order to not get my ears blasted. I'd never want to turn this on in a public place, the way it is now! Is there any way to adjust the volume of those start-up theme sounds? And if not, then how can they be disabled?

---

### Post by Frogs Hair on 2011-09-28
Go into sound preferences and try turning down the alert volume .

---

### Post by scruffyeagle on 2011-09-28
> **Frogs Hair said:**
> Go into sound preferences and try turning down the alert volume .

Thanks for the reply.

The alert volume was already at its minimum setting, all the way to the left end of the slider.

---

### Post by fooman on 2011-09-28
whatever volume it is set to when you turn it off....should be the same when turned back on (at least that has always been the case for me on numerous laptops/netbooks/or desktops).

in other words,  if you turn the volume down low before turning it off,  it should stay low when restarted.  or if you mute the volume before turning off,  it should stay muted when rebooted!

---

### Post by scruffyeagle on 2011-10-14
> **fooman said:**
> whatever volume it is set to when you turn it off....should be the same when turned back on (at least that has always been the case for me on numerous laptops/netbooks/or desktops).

in other words,  if you turn the volume down low before turning it off,  it should stay low when restarted.  or if you mute the volume before turning off,  it should stay muted when rebooted!

Nope. It doesn't work that way on this machine. I don't know if it's a quirk of the OS, or the way the OS interacts with this machine, but on power-up and during start-up of Gnome, the volume of the decorative sounds is always at full blast maximum volume.

---

### Post by tomasijeaux on 2011-11-01
I am having the same issue after upgrading to Oneiric. It's really annoying, back in Natty volume after start used to be adjusted to the level before turning off. Someone please help

---

### Post by pqwoerituytrueiwoq on 2011-11-01
one way would be to replace the login sound startup entry with a script that alters the volume before playing you may be able to do this with the rc.local file
```
pacmd set-sink-volume 0 3500
```that is the volume command 3500 is volume (3500 is low for me)

copy paste solution:

replace startup entry:
```
echo "[Desktop Entry]" > ~/.config/autostart/libcanberra-login-sound.desktop
echo "Type=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Name=GNOME Login Sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Comment=Plays a sound whenever you log in" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Exec=/opt/sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "OnlyShowIn=GNOME;" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "AutostartCondition=GNOME /desktop/gnome/sound/event_sounds" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "X-GNOME-Autostart-Phase=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "X-GNOME-Provides=login-sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
```create startup script
```
sudo -su
echo "#\!/bin/sh" > /opt/sound
echo "pacmd set-sink-volume 0 3500" >> /opt/sound
echo "/usr/bin/canberra-gtk-play --id=\"desktop-login\" --description=\"GNOME Login\"" >> /opt/sound
echo "exit 0" >> /opt/sound
chmod +x /opt/sound
exit
```

---

### Post by scruffyeagle on 2011-11-04
> **pqwoerituytrueiwoq said:**
> one way would be to replace the login sound startup entry with a script that alters the volume before playing you may be able to do this with the rc.local file
```
pacmd set-sink-volume 0 3500
```that is the volume command 3500 is volume (3500 is low for me)

copy paste solution:

replace startup entry:
```
echo "[Desktop Entry]" > ~/.config/autostart/libcanberra-login-sound.desktop
echo "Type=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Name=GNOME Login Sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Comment=Plays a sound whenever you log in" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Exec=/opt/sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "OnlyShowIn=GNOME;" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "AutostartCondition=GNOME /desktop/gnome/sound/event_sounds" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "X-GNOME-Autostart-Phase=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "X-GNOME-Provides=login-sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
```create startup script
```
sudo -su
echo "#\!/bin/sh" > /opt/sound
echo "pacmd set-sink-volume 0 3500" >> /opt/sound
echo "/usr/bin/canberra-gtk-play --id=\"desktop-login\" --description=\"GNOME Login\"" >> /opt/sound
echo "exit 0" >> /opt/sound
chmod +x /opt/sound
exit
```

Thank you for your reply. I haven't tried what you posted yet, but at least now there's something to try (to deal with one part of the problem), if I can't find the solution I need. I don't think I was clear enough, in my description of the problem I'm trying to solve. It's not just the Gnome login sound that's a problem. It's also the pre-login sound that Ubuntu makes. When the machine first powers up and presents the screen where you can select username & enter password, the bongos sound is also at full blast.

If the volume prior to login can't be fixed by script, then one other possible method of solving the problem would be to do sound editing on the soundfiles themselves; ie., doing a diminishment of decibel level of the sound in the file, then saving it that way. Does anyone know the names of the soundfiles being used for the bongos sound and the Gnome desktop presentation sound? And, of course, the necessary info re. where they're being stored in the filing system.

---

### Post by pqwoerituytrueiwoq on 2011-11-04
/usr/share/sounds/ubuntu/stereo
is where the sounds are 
try opening up /etc/rc.local and setting the volume with this line
pacmd set-sink-volume 0 3500should be before exit
i think i have had issues with it like that running before the volume can be set
the login screen is a short sound i can tolerate the volume for under 1 second



the login ready is opened with and make it run a script that sets the volume  then play the sound
/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop

open it with nano/gedit/leafepad/mouepad/geany
and use the same trick as i posted with the other login sound

---

### Post by scruffyeagle on 2011-11-04
> **pqwoerituytrueiwoq said:**
> /usr/share/sounds/ubuntu/stereo
is where the sounds are 
try opening up /etc/rc.local and setting the volume with this line
pacmd set-sink-volume 0 3500should be before exit
i think i have had issues with it like that running before the volume can be set
the login screen is a short sound i can tolerate the volume for under 1 second



the login ready is opened with and make it run a script that sets the volume  then play the sound
/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop

open it with nano/gedit/leafepad/mouepad/geany
and use the same trick as i posted with the other login sound

I'm still here, but I was a little sluggish in my response to your reply because I was trying to figure out how to change file permissions to make stuff writeable. I finally came up with ```
chmod u+w *filename*
```

Is that correct?

---

### Post by pqwoerituytrueiwoq on 2011-11-04
open it with root access
sudo nano /usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop
or 
gksudo gedit /usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop

sudo for terminal apps, gksudo for gui apps

---

### Post by scruffyeagle on 2011-11-09
> **pqwoerituytrueiwoq said:**
> one way would be to replace the login sound startup entry with a script that alters the volume before playing you may be able to do this with the rc.local file
```
pacmd set-sink-volume 0 3500
```that is the volume command 3500 is volume (3500 is low for me)

copy paste solution:

replace startup entry:
```
echo "[Desktop Entry]" > ~/.config/autostart/libcanberra-login-sound.desktop
echo "Type=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Name=GNOME Login Sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Comment=Plays a sound whenever you log in" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "Exec=/opt/sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "OnlyShowIn=GNOME;" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "AutostartCondition=GNOME /desktop/gnome/sound/event_sounds" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "X-GNOME-Autostart-Phase=Application" >> ~/.config/autostart/libcanberra-login-sound.desktop
echo "X-GNOME-Provides=login-sound" >> ~/.config/autostart/libcanberra-login-sound.desktop
```create startup script
```
sudo -su
echo "#\!/bin/sh" > /opt/sound
echo "pacmd set-sink-volume 0 3500" >> /opt/sound
echo "/usr/bin/canberra-gtk-play --id=\"desktop-login\" --description=\"GNOME Login\"" >> /opt/sound
echo "exit 0" >> /opt/sound
chmod +x /opt/sound
exit
```

I managed to get through the first of these two, but ran into problems in the second one. I figured out about entering my logged-in user name after "-su", but when I tried to enter the 2nd line of code to create /opt/sound, it told me "bash: /opt/sound: Permission denied". I didn't know how to get around that, so that was the end of my attempt for the evening. Just to be on the safe side, I removed the file I'd made in the first section. I didn't want the OS getting hung up when the first file called the second, and the second not existing. Any ideas why I'm getting the Bash error?

---

