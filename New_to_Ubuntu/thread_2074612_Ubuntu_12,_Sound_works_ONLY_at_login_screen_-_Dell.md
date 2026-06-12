---
title: "Ubuntu 12, Sound works ONLY at login screen - Dell Mini9"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by xle0nx on 2012-10-22
hello, everyone...

Dell Mini 9
12.04 LTS

Sound works at  startup and at login screen. I hear the drum-roll loud and clear and I  can adjust the volume with the slider controls at the top of the screen.  After I log in, the sound/controls appear to become non-existent (I  can't adjust the volume (it's locked)) and no devices show up when I go  into "Sound Settings".

When I open AlsaMixer:
Card: HDA Intel
Chip: Realtek ALC268

Everything is on including "Beep".
Auto-Mute is disabled. (enabling this did not change result)
no MMs across any of the controls

I've performed the steps shown [here]("http://grabag-linux.blogspot.com/2009/05/enabling-audio-in-debian-on-mini-9.html") in hopes of getting it to work. Still nothing. Well, now i have a file in /etc/modprobe.d/**sound.conf** with the following contents:
[B]alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 model=dell[/B]

I also ran the following lines, per the instructions:
# rmmod snd_hda_intel
# modprobe snd_hda_intel

I upgraded to 12.04 from Lucid Lynx with  hopes of having sound and a power issue worked out. The power works  perfectly now, but I kind of want sound too :)

Thank you in advance,
leon

---

### Post by newb85 on 2012-10-22
Try issuing the command
```
pulseaudio --kill
```
and see if that changes anything.

---

### Post by NikTh on 2012-10-22
Hi , 

try this 

```
killall pulseaudio 
rm -r ~/.pulse/ 
sudo alsa force-reload
```Also check the alsamixer , from terminal give 
```
alsamixer
```navigate with arrow keys (left-right) and see if any channel is muted [MM]. You can unmute channels with 'M' key in your keyboard and increase - decrease volume with up-down arrow keys. [ESC] to exit.

---

### Post by xle0nx on 2012-10-22
ran: pulseaudio --kill
result: Failed to kill daemon: No such process

ran: killall pulseaudio
result: no process found

thanks for the quick replies and info so far. any more suggestions?

edit: peeked at alsamixer again and everything looks fine. no mutes (MMs) anywhere.
snapshot (note volume control icon on taskbar):
[IMG]https://lh3.googleusercontent.com/-IQhtmNpusZ0/UIVRd3ZFoNI/AAAAAAAABFc/MJ5MRJIBALU/s582/Screenshot+from+2012-10-22+08%3A56%3A52.png[/IMG]

---

### Post by pqwoerituytrueiwoq on 2012-10-22
make sure [FONT=Courier New]pluseaudio --start[/FONT] is is your startup applications
```
rm -rf ~/.pulse
```
logout then login

---

### Post by xle0nx on 2012-10-22
> **pqwoerituytrueiwoq said:**
> make sure [FONT=Courier New]pulseaudio --start[/FONT] is is your startup applications

wow. that fixed it. i added that to the "Startup Applications Preferences" and restarted.

> **pqwoerituytrueiwoq said:**
> ```
rm -rf ~/.pulse
```logout then login

what's this part for? should i do anything else or just leave it as it is, now that it is working?

thanks again, everyone...

---

### Post by pqwoerituytrueiwoq on 2012-10-22
that was for if the startup option was not the issue
it would reset your sound config
what does this give you?
this is what is supposed to start the audio

cat /etc/xdg/autostart/pulseaudio.desktop | grep Exec

---

### Post by xle0nx on 2012-10-22
^^ oh, ok. 

i didn't run that (**cat /etc/xdg/autostart/pulseaudio.desktop | grep Exec**). i'll run it later on when i'm on break. it won't change anything, will it?

honestly, it's way over my current linux comprehension :)

but, to reiterate, it's working now thanks to your first suggestion.

---

### Post by pqwoerituytrueiwoq on 2012-10-22
will not alter anything
just wondering if your system has that file and if so what command is being run

---

### Post by xle0nx on 2012-10-22
sounds cool. i'll let you know...

---

### Post by xle0nx on 2012-10-22
ok. it outputs the following: **Exec=start-pulseaudio-x11**

oh, and i deleted the "**pulseaudio --start**" entry from the startup applications dialog, you know, just to see if it would change the above output. it didn't change. but you probably knew that already, but i wanted to see, heh heh...

i had to add it back to the startup applications to get sound again.

---

### Post by pqwoerituytrueiwoq on 2012-10-22
```
sudo sed -i 's/start-pulseaudio-x11/pulseaudio --start/' /etc/xdg/autostart/pulseaudio.desktop
```
try that and see if you can delete your new startup item and still have sound

here is the undo command
```
sudo sed -i 's/pulseaudio --start/start-pulseaudio-x11/' /etc/xdg/autostart/pulseaudio.desktop
```

---

### Post by xle0nx on 2012-10-22
^^ that makes it not work again. (after restart)

also, when i ran: **cat /etc/xdg/autostart/pulseaudio.desktop | grep Exec**
it returned: [B]Exec=pulseaudio --start

[/B]also, i didn't run the "undo" command yet...

---

### Post by pqwoerituytrueiwoq on 2012-10-23
```
cat ~/.config/autostart/pulseaudio.desktop
```
do you get file not found? if not that will override **/etc/xdg/autostart/pulseaudio.desktop**

---

### Post by xle0nx on 2012-10-23
no errors or messages.

it just acts like it did before. drum roll (sound) at the login screen and disabled once i'm logged in.

i think i'll just keep that entry in the startup box. at least i know what to look out for on the next upgrade.

---

### Post by xle0nx on 2012-10-24
ran: [B] cat ~/.config/autostart/pulseaudio.desktop
[/B]
[Desktop Entry]
Type=Application
Exec=pulseaudio --start
Hidden=true
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=pulseaudio
Name=pulseaudio
Comment[en_US]=
Comment=


^^ that's what happened. rebooting now...

edit: after reboot. still no sound.

---

### Post by xle0nx on 2012-12-21
just as an update to this thread; formatted and installed 12.10 today and everything works without having to add any parameters to the startup sequence. this is truly the first ubuntu distribution that has worked 'out of the box' for me and the mini9...

---

