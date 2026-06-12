---
title: "Headphone jack doesnt work, only display port monitor sound does"
date: 2020-08-04
forum: New to Ubuntu
---

### Post by darinbuntu123 on 2020-08-04
I have some Z200 Logitech speakers plugged in the green port (the green one) and it does get detected in pulseaudio as:
Starship/Matisse HD Audio Controller Analog Stereo
And I get two entries:
Port: Headphones (unplugged) (where my speakers are connected to)
Port: Line Out (plugged in)

Plugging them does light them up, thats it

Typing $alsactl restore gets me

alsactl: state_lock:125: file /var/lib/alsa/asound.state lock error: File exists
alsactl: load_state:1683: Cannot open /var/lib/alsa/asound.state for reading: File exists
Found hardware: "HDA-Intel" "Nvidia GPU 99 HDMI/DP" "HDA:10de0099,103c8556,00100100" "0x103c" "0x8556"
Hardware is initialized using a generic method
Found hardware: "HDA-Intel" "Realtek ALC1220" "HDA:10ec1220,103c86d3,00100003" "0x103c" "0x86d3"
Hardware is initialized using a generic method

and then restarting does nothing

Unplugging it makes it not detect it anymore, until a reboot

I am sorry if I didnt give enough infomation, I am switching from WIndows to Linux and I am starting out

---

