---
title: "no sound"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by tobythedog on 2012-05-06
hi just put lubuntu on my old pc , great it flies compared to xubuntu, only prob is i dont seem to have any sound , cannot find sound preferences, could someone tell me where it is please

---

### Post by Dennis N on 2012-05-06
You have your volume control on the panel, which you can check for volume level and mute/unmute. also you have the alsamixer utility to control pcm volume and various sound inputs and outputs you might have on your machine. Alsamixer can be started from the terminal.

---

### Post by tobythedog on 2012-05-06
still no sound volume set at max not muted no sound at all how do i start alsamixer from terminal please.i cannot find any sound settings on  lubuntu, how do i find them please

---

### Post by Dennis N on 2012-05-06
> **tobythedog said:**
> still no sound volume set at max not muted no sound at all how do i start alsamixer from terminal please.i cannot find any sound settings on  lubuntu, how do i find them please

Open the terminal (its under accessories - LX Terminal).
Type **alsamixer** and press enter and it will start up. Use the arrow keys to navigate between the various devices. The initial screen should show you all the playback devices; if not press F3 to view playback devices. Up arrow will increase volume on each device.

Press ESC to close alsamixer.

---

### Post by tobythedog on 2012-05-06
ok got alsamixer running , played about with settings still no sound anyone anymore ideas please

---

### Post by Dennis N on 2012-05-06
I assume the sound worked on Xubuntu, so that is a definitely a good sign. Did you do a fresh install from the Lubuntu Live CD, and did the sound work in the Live CD? 

Test other outputs and see if they work - external speakers, headphones. Check audio cables to any external speakers? Are they plugged in the right jacks? Is volume up on external speakers?

Next, there is a Sound Troubleshooting thread in Multimedia and Video Forum. Reading and posting there may help find the solution.

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

Good Luck

---

### Post by NikTh on 2012-05-06
> **tobythedog said:**
> ok got alsamixer running , played about with settings still no sound anyone anymore ideas please
Hi , 
also in alsamixer check if something is muted[MM]. if it is , then hit "m" key to unmuted. Another thing is S/PDIF , check if its muted. if not then mute it. 


You can install pavucontrol in Lubuntu to check and configure sound devices. (GUI)
Open terminal and ```
sudo apt-get install pulseaudio pavucontrol
```I think this will work.

---

