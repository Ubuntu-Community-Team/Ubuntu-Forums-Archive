---
title: "sound when desktop opens"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by bdubawoop on 2013-06-22
10.04 used to sound a chorus when the desktop loaded.
is there a way to get 12.04 to do that or do i need to change desktops?

---

### Post by gifford on 2013-06-22
If you mean the startup sound, this link will walk you through getting it in 12.04.
[http://www.ubuntugeek.com/how-to-enable-startup-login-sound-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-enable-startup-login-sound-in-ubuntu-12-04-precise.html)

---

### Post by FStarter on 2013-06-22
Hi, in this kind of question people usually get confused about the short bongo beats that sounds when LightDM is ready and the sound after you hit enter to log in to your account
It seems you refer to the last one, so try this:
-Search in dash for "Startup Applications" and add another entry
-Name: Login sound
 Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login sound"

I already tried this in a virtual machine I have for testing stuff and it worked, so give it a try :D

edit: whoops, it seems it's the same gifford posted 2 min ago

---

### Post by bdubawoop on 2013-06-22
doesn't work
tried copy/paste & typing & removing 'sound' at the end.
did browse & canberra is there but no sound either logging out/in or rebooting.

if i browse to canberra it sez theres nithing to open it
tried the web search & install pypar2 but still wont open.
i do have sound with videos,etc.

par2 is now on there but wont play the canberra file.
is there another app that will play it manually so i can hear it?

i found the cmd on my main computer which still has 1004 (and which will stay with 1004), typed the cmd in a terinal & it played.

i figure ill do that with 1204 to test it---NO TERMINAL! in 1204. i cant believe they install the thing with no terminal icon.
when i find it in another week or so i, try & play it from the terminal-i assume its gotta be on here somewhere.

ok-found the terminal-entered the command & nothing-came back with cmd prompt-obvuosly im missng an app or something

---

### Post by FStarter on 2013-06-22
You can test the sound with the terminal, just copy this:
**/usr/bin/canberra-gtk-play --id=desktop-login** (note that there are two "-" before "id")

You should hear the sound from there, in my PC it works.
BTW the ogg file is located in /usr/share/sounds/ubuntu/stereo/desktop-login.ogg

---

### Post by Hadaka on 2013-06-23
Hi, this should give you a sound at splash screen.

```
sudo gedit /etc/default/grub
```
# Uncomment to get a beep at grub start
```
#GRUB_INIT_TUNE="480 440 1"
```
save and close gedit
then..
```
sudo update-grub
```
reboot

---

### Post by bdubawoop on 2013-06-23
ok, it is playing but at extremely low volume.
it, alone, is barely audible. all other sounds play normally, in fact, desktop-login.ogg plays loud if played manually with rythymbox.
could it be another program is being used to play it with low volume from the terminal & at login-if so, how do i find out what it is, or better yet force it to use rythymbox?

i also took the advice of another poster & installed the gnome shell which helps greatly with usability.

---

### Post by bdubawoop on 2013-06-25
got it.
had to add -V 4 parameter to end of canberra-gtk line.
found by searching canberra-gtk in forum.
intended to mark this as solved but how to do that is bigger mystery than original problem
i see nothing about solved under thread tools.

---

### Post by FStarter on 2013-06-26
Glad u make it work ;)

---

