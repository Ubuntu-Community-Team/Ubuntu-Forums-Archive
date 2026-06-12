---
title: "Short HOWTO get music from your machine through an usb bluetooth dongle to a headset"
date: 2006-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by robos on 2006-08-11
This is a short list of commands I used under ubuntu dapper to connect my bluetooth levelone MDU-0025 usb dongle to my nokia hs-37w headset. Ubuntu already comes with quite a lot of services set up but a little bit stuff is still to do. First, check that you installed bluez-btsco, bluez-pin and bluez-utils.
Now, this is a little modified version of the intro printed at bluetooth-alsa.sf.net:
1) ```
sudo modprobe snd-hwdep
```
2) ```
sudo modprobe snd-bt-sco
```
3) ```
sudo hciconfig hci0 voice 0x0060
```
4) change your headset into pairing mode (the nokia hs-37w does this after you take out and put in the battery).
5) ```
sudo hcitool inq
```
This will give you the bdaddress of the headset. Example: > hcitool inq
Inquiring ...
00:07:A4:B1:F5:82 clock offset: 0x5832 class: 0x200404
Now it becomes a little fuzzy because it didn't work and I had to try stuff, but I think this here does it...
6) ```
sudo /etc/init.d/bluez-utils restart
```
There should be a popup coming up that asks you for the pin. Enter it.
7) ```
sudo sdptool search --bdaddr 00:07:A4:B1:F5:82 HS
```
Replace with your bluetooth address. The "HS" at the end tells the sdptool to query for headset characteristics.
8) ```
sudo hciconfig hci0 revision
```
This should list something like "SCO mapping: HCI" at the end of the output.
9) ```
sudo btsco -v -s 00:07:A4:B1:F5:82
```
After this you should be connected to your headset and you can now play audio with e.g. xmms configured to use alsa and look in the configure alsa, there you should find something like "BT Headset" at the bottom of the audio device selection. Play!
My output of the last command looks something like this:
> btsco v0.4c
Device is 2:0
Voice setting: 0x0060
RFCOMM channel 1 connected
recieved AT*GNMK
speaker volume: 13 mic volume: 14
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
recieved AT+VGS=03
Sending up speaker change 3
I think that 7) and 8) aren't strictly necessary but they give nice infos.
I hope this helps someone else. If someone manages to get audio from the headset to the machine, please post it! I want to make voice calls via VoIP with this setup, so audio in is crucial :)
Cheers
Robos

---

### Post by MatBi on 2006-08-17
As soon as i issue the "sdptool search" command i get: "Failed to connect to SDP server on 00:0D:44:3A:BB:8B: Permission denied".
I tried to switch the security from auto to user and back, with no luck. I'm running Xubuntu, so "kbluetoothd" is not an option for me. 
Any idea?

---

### Post by MatBi on 2006-08-18
The problem was the dongle. Apperently, that dongle (or its drivers) does not support the headset profile.

---

### Post by stumps on 2006-09-24
Robos, you're a star!!! ... Great Thanks!!! :cool: 

Your howto works perfectly with Motorola H500 headset and DeLL Latitude D610 ...

---

### Post by Redeyes_Gambit on 2006-09-26
}{i, I tried yor steps and get this error message:

greg@ubuntu-laptop:~$ sudo btsco -v -s 00:07:A4:B1:F5:82
btsco v0.4c
Device is 1:0
Error: Failed to connect to SDP server: Host is down
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Host is down


Any idea why? In all fairness I cant get this thing to pair in windows either, but that's no surprise now is it ;) ?

---

