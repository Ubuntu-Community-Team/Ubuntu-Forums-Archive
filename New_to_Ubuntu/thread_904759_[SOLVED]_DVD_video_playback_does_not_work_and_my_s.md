---
title: "[SOLVED] DVD video playback does not work and my sound is super quiet"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by roland0702 on 2008-08-29
I have a new Dell Inspiron 1525 laptop with Ubuntu 8.04 installed. My sound is super quiet at full volume. The sound is adequate with headphones, just not the speakers. Also the microphone barely records my voice when speaking through a headset.

Also, my DVD playback is simple not working. I have the Totem movie player with GStreamer.

Please help.

---

### Post by kansasnoob on 2008-08-29
Regarding sound I'd add gnome-alsamixer which is in synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in the menu under Sound & Video. Check out the toggles on mine:

[ATTACH]83277[/ATTACH]

[ATTACH]83278[/ATTACH]

---

### Post by kansasnoob on 2008-08-29
To add DVD playback capabilities look here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

As it says go to terminal and run the following commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

It's much easier to just copy & paste the commands.

---

### Post by roland0702 on 2008-08-29
> **kansasnoob said:**
> Regarding sound I'd add gnome-alsamixer which is in synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in the menu under Sound & Video. Check out the toggles on mine:

[ATTACH]83277[/ATTACH]

[ATTACH]83278[/ATTACH]


Hey, it works. Thanks man.

---

### Post by roland0702 on 2008-08-29
> **kansasnoob said:**
> To add DVD playback capabilities look here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

As it says go to terminal and run the following commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

It's much easier to just copy & paste the commands.



Hey I followed all of these instructions. My totem player still freezes...I also tried playing a DVD through VLC player, but the software quit on it's own.

---

### Post by Crafty Kisses on 2008-08-29
Try running Totem through the Terminal, do you get any errors?

---

### Post by roland0702 on 2008-08-29
> **Codename said:**
> Try running Totem through the Terminal, do you get any errors?

Sorry, I don't know how to run Totem through the Terminal; I'm a noob. I can copy and paste code.

---

### Post by spec-chum on 2008-08-29
> **roland0702 said:**
> Sorry, I don't know how to run Totem through the Terminal; I'm a noob. I can copy and paste code.

Just open a terminal (Applications->Accessories->Terminal) and type
```

totem

```

totem will then run and any errors that occur while you run it will be displayed on the terminal.

---

