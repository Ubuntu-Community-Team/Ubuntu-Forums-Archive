---
title: "Bluetooth/Skype Problem"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by fdepinto on 2008-05-18
Just installed Ubuntu 8.04 and paired my bluetooth adapter and my Plantronics 520 headset.  

The problem is that Skype doesn't "see" the headset as one of the sound devices available.  

How can I get Skype to recognize my headset?

Thanks in advance.

---

### Post by PinkFloyd102489 on 2008-05-18
Open/create .asoundrc in your home directory and put this in it.

```
pcm.bluetooth {
 type bluetooth
 device "AA:BB:CC:DD:EE:FF"
 profile "auto"
}
```

Replace the device bit with the fingerprint of your headset. Then restart Skype if it's running. You may have to pair the headset again.

---

### Post by fdepinto on 2008-05-18
> **PinkFloyd102489 said:**
> Open/create .asoundrc in your home directory and put this in it.

```
pcm.bluetooth {
 type bluetooth
 device "AA:BB:CC:DD:EE:FF"
 profile "auto"
}
```

Replace the device bit with the fingerprint of your headset. Then restart Skype if it's running. You may have to pair the headset again.


Okay.  First of all, thanks for the reply, and I mean that.  But remember, this is a beginner forum.  You're talking over my head.

I know what/where the home folder is.  But, is .asoundrc a file or a folder which I need to create?

What is a device bit?

Also, what do you mean by a "fingerprint" of my headset?

Thanks again.

---

### Post by benpage26 on 2008-05-18
> **fdepinto said:**
> Okay.  First of all, thanks for the reply, and I mean that.  But remember, this is a beginner forum.  You're talking over my head.

I know what/where the home folder is.  But, is .asoundrc a file or a folder which I need to create?

What is a device bit?

Also, what do you mean by a "fingerprint" of my headset?

Thanks again.


Hi,
I can help a little bit to get you started.

.asoundrc is a file in your home drive.
All file names that start with a . [full stop] are hidden by default, so if you go to your home drive in nautilus you will not see any of these files.

The easiest way to open/create this file is to use the following command:
```
gedit ~/.asoundrc
```
gedit is a graphical text editor (like notepad in Windows), if you prefer another editor you just type the name of that one - other popular (but less pretty ones) include nano, pico, vi.  I however find gedit the easiest to use.

When gedit pops up copy paste the section PinkFloyd102489 suggested into the file, when he said the "device bit" he meant the line that starts with device.
You need to change "AA:BB:CC: DD:EE:FF" to the fingerprint of your bluetooth headset.  A fingerprint is a unique identifier.  I am not sure how to find out the fingerprint, it may be printed on the device, or you may be able to find it out from the application you used to initally pair your device.

---

### Post by fdepinto on 2008-05-18
Thanks to benpage26 and pinkfloyd.  It's working!

---

### Post by tunnelblick on 2008-05-18
Hi!
Can you please tell me how you paired your headset? Which application do you use? I tried hcitool, hidd and kbluetooth but somehow it just does not work :(

Thanks
Tunnelblick

---

### Post by PinkFloyd102489 on 2008-05-18
Blueman is a good bluetooth manager. In Blueman, all you have to do is set your device to pairing mode and hit Bond. It'll ask you for the pairing key and viola, it's paired.

---

### Post by fdepinto on 2008-05-18
> **tunnelblick said:**
> Hi!
Can you please tell me how you paired your headset? Which application do you use? I tried hcitool, hidd and kbluetooth but somehow it just does not work :(

Thanks
Tunnelblick

Keep in mind that I'm a complete Linux newbie, so I don't know how helpful I can be.  But, in my case I just clicked on system | preferences | bluetooth, and poked around there until the headset was paired.  I don't remember the exact sequence of how I did it, but that is the basic idea.  Sorry I can't be of more assistance.

By the way, the headset is paired and works with Skype, but it sounds like c**p.  Don't know if that's my fault or Skype's.

---

