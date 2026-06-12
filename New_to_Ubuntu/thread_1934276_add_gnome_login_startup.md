---
title: "add gnome login startup?"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by soryu on 2012-03-01
how do i add gnome login sound to start up apps?
i deleted it and my sound effects are gone. i thought it would just remove the login sound.

---

### Post by soryu on 2012-03-03
will this work on 11.10?


GNOME Login Sound
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

---

### Post by Diametric on 2012-03-04
Don't know the answer but I'd like to see if anyone else does.

---

### Post by NikTh on 2012-03-04
> **soryu said:**
> will this work on 11.10?


GNOME Login Sound
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

Go to /usr/share/gnome/autostart and create a file, name it login-sound.desktop. Then open it with gedit (sudo) and add following lines . Alternatively you can create the file at /etc/xdg/autostart . 

```
[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --file /usr/share/sounds/gnome/<YOUR .ogg FILE> 
-description="GNOME Login"
OnlyShowIn=GNOME;Unity;
AutostartCondition=GSettings org.gnome.desktop.sound event-sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound

```Be careful the line  --file /usr/share/sounds/gnome/<YOUR .ogg FILE> . You must have an .ogg sound file in there .Give the exactly path with file name if you have it somewhere else .  

save it. 
done

---

### Post by soryu on 2012-03-05
thanks for the info,but isn't there a command i could just add to start up applications to get my sound effects back.
i want to get my sound effects back. i dont know but will adding the desktop login sound also bring back my sound effects?

---

