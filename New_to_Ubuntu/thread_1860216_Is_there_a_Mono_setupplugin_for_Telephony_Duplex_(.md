---
title: "Is there a Mono setup/plugin for Telephony Duplex (HSP/"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by suomalainen on 2011-10-14
Ubunteros,

I got a Samsung Nexus S. I was having a problem with it whereby I could not hear MP3 or other audio via the bluetooth mono headset. However, a plugin from the Android market took care of that problem and now I can hear the things I need to hear over my Mono headset when connected to my handset (eg Nexus S).

In Ubuntu 10.04 LTS I can connect to the bluetooth headset but everything I hear is in static! Sypke, MP3's, recorded audio... everything.

As you can see from the pic I attached the only setting available is "Telephony Duplex (HSP/HFP)". Is there a way to add a "Mono" setting here so that I can hear things better over my headset?

Correct me if I'm wrong and not going in the right direction.

Thanks Ubunteros,

Suomalainen

---

### Post by suomalainen on 2011-10-14
Sorry. Forgot to attach the pic in original post. I did try to edit it by attaching the pic but that wasn't allowed to do. So I needed to make new post.

---

### Post by suomalainen on 2011-10-15
I discovered this document in the "Community Documentation" area:

[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

It sounds like this is a "mono" plugin that would enable me to hear sound over my Samsung Bluetooth Mono headset model HM1100. But am I correct?

When I ran the first two commands noted I got no where. E.G.

paavo@paavo-laptop:~$  sudo apt-get install bluez-btsco
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez-btsco is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
paavo@paavo-laptop:~$ sudo modprobe snd-bt-sco
FATAL: Module snd_bt_sco not found.
paavo@paavo-laptop:~$ 

What should/can I do now?

Thank you!

---

### Post by suomalainen on 2011-10-16
bump

---

